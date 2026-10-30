# Open-Source VLSI Tool: Verilator (DV track)

Official docs: https://verilator.org/guide/latest/  
Tested with: Verilator 5.020 on Ubuntu

## What problem does it solve?
Verilator translates Verilog/SystemVerilog into optimized C++ (or SystemC) that is compiled
into a fast simulation executable. It is used for fast RTL simulation and for linting
(width mismatches, unused signals, latches, etc.) before simulation or synthesis.

## Inputs and outputs
| Inputs | Outputs |
|--------|---------|
| RTL (`.v` / `.sv`) | Generated C++ model and build files in `obj_dir/` |
| Testbench (SV with `--binary --timing`, or a C++ wrapper) | Simulation executable (`obj_dir/V<top>`) |
| Flags (`--lint-only`, `-Wall`, `--trace`) | Lint warnings, waveform files (`.vcd`/`.fst`) |

## What I tried
**Design (`counter.sv`)**
```systemverilog
module counter (
  input  logic       clk, rst_n,
  output logic [3:0] count
);
  always_ff @(posedge clk or negedge rst_n)
    if (!rst_n) count <= 4'd0;
    else        count <= count + 4'd1;
endmodule
```

**Testbench (`tb.sv`)**
```systemverilog
module tb;
  logic clk = 0, rst_n = 0;
  logic [3:0] count;

  counter dut (.*);

  always #5 clk = ~clk;

  initial begin
    #12 rst_n = 1;
    repeat (20) @(posedge clk);
    $display("Final count = %0d", count);
    $finish;
  end

  initial $monitor("t=%0t count=%0d", $time, count);
endmodule
```

**Commands**
```bash
verilator --lint-only -Wall counter.sv
verilator --binary --timing --top-module tb tb.sv counter.sv
./obj_dir/Vtb
```

**Results**
- Lint: no warnings (exit code 0).
- Build: succeeded and produced `obj_dir/Vtb`.
- Run output (trimmed):
```
t=0 count=0
t=5 count=0
t=15 count=1
...
t=155 count=15
t=165 count=0      <- 4-bit counter wraps from 15 to 0
...
t=195 count=3
Final count = 3
- tb.sv:13: Verilog $finish
```
- Observations: the counter held 0 during reset, started counting after reset released
  at t=12, and wrapped around after 15 as expected. The last `$monitor` line (t=205) printed
  after `$finish` because the final timestep still completes, which is a small simulation-semantics detail.

**Second experiment: X handling.** `a = 4'bxxxx; $display("a = %b", a);` printed `a = 0000`,
confirming default 2-state behaviour. The official docs explain that an assigned X becomes a constant
chosen by the `--x-assign` option (see `ai_tools_exploration.md`).

## Where could AI/ML help?
- Suggesting testbench stimulus and tests that close coverage holes
- Explaining and triaging lint warnings and simulation failures
- Predicting which tests are most likely to find bugs (test prioritization)
- Drafting assertions from spec text (always human-reviewed)

## Limitations I found
- Default 2-state simulation: X/Z are not represented, so X-propagation and
  uninitialized-register bugs can be hidden (tested above). Four-state support is
  new and partial.
- The docs describe Verilator's class support as limited but in active development.
- Constrained randomization, central to UVM-style verification, has historically not
  been fully supported. A 2025 DVCon paper describes recent progress in Verilator's randomization
  features, so I treat UVM support as improving but not equal to commercial simulators.
  Source: https://dvcon-proceedings.org/wp-content/uploads/DVConEU_2025_paper_107.pdf
