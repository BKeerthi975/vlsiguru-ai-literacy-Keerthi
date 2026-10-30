# Reflection

**Most useful AI tool, and for what?**
ChatGPT was most useful for learning concepts, since it tailored explanations to my level and quizzed me one question at a time. Gemini was most useful for verification and practice, since it linked the official docs and gave an interactive quiz card with hints. I used both and checked key claims against the Verilator documentation.

**Which prompt change helped most?**
Adding my background, a word limit and an output format. The vague prompt "Explain UVM." produced very long,
generic answers, while the refined prompt produced short answers with an analogy and a table.
Asking for "yes/no first, then a source, then how to test it" helped most for verification.

**Claim I verified and what the source established:**
Both ChatGPT and Gemini said Verilator does not simulate X/Z like QuestaSim. Verilator's docs and my own test (`4'bxxxx`
printed as `0000`) confirmed that it is mostly two-state. I also found that one tool's "July 2026" date for
the four-state work was only the republishing date; the original announcement was in April 2026.

**What I learned about Verilator:**
It compiles RTL to C++ for fast simulation and linting, and `--binary --timing` runs SystemVerilog testbenches
directly. What surprised me is that an assigned X becomes a constant value, which can hide reset bugs unless
I use options like `--x-assign` and `--x-initial` to expose them.

**What is still unclear:**
How much of UVM (constrained randomization, factory, phasing) I can realistically run on open-source
simulators compared with QuestaSim.

**Two questions for the ML masterclass:**
1. How is ML actually used in verification today (coverage closure, test selection), and what should a DV
   engineer learn to work with it?
2. How do we tell when an ML-generated test or assertion is wrong, given that we cannot trust the output blindly?
