# AI Tools Exploration

I ran the same prompts in two different AI tools, **ChatGPT** and **Gemini**, and compared them.
I also used Claude to help structure these notes and web search to find primary sources.

## 1. Tools I used
| Tool | What I used it for | Observation |
|------|--------------------|-------------|
| ChatGPT | UVM explanation, driver-vs-monitor comparison, Verilator X/Z claim, UVM quiz | Personalised answers (used my name and my learning path), ALU worked examples, followed the quiz instructions exactly |
| Gemini | Same prompts | Shorter, more generic answers; gave a direct link to the Verilator docs; produced an interactive quiz card (hints, correct/incorrect counter) when I asked for all questions at once |
| Claude | Structuring notes, checking claims against sources | Helpful for organising, but I still checked key facts myself |

## 2. Prompt refinement
**Version 1 (vague):** `Explain UVM.`
- ChatGPT: very long (about 10 sections), included a learning roadmap and a phases table.
  Useful, but far more than I asked for.
- Gemini: a generic textbook answer (benefits, components, phases, factory, config_db) with no
  tailoring to my level.

**Version 2 (context + constraints + format):**
> I'm a final-year ECE student learning design verification. I know basic Verilog and
> SystemVerilog. Explain UVM in beginner-friendly language in under 200 words. Use an analogy,
> then list the main components (driver, monitor, sequencer, scoreboard) in a table with one line each.

- Both tools respected the limit and the format: short, an analogy, a four-row table.
- ChatGPT used a factory-testing-team analogy tied to an ALU example. Gemini used a self-driving-car
  test-track analogy. Both answers were much easier to scan than Version 1.

**Version 3 (quiz mode):**
> Now quiz me with 5 questions on these components, one at a time. Wait for my answer before giving feedback.
- ChatGPT asked Question 1 only and waited for my answer, as instructed.
- Gemini: I asked it for all five questions at once instead. It produced an interactive quiz card with answer buttons, a hint option and a correct/incorrect counter, which is a nice format for self-testing.
- My result: 4 _/5. Gaps the quiz showed: I got the scoreboard question wrong because I mixed it up with the monitor. The monitor only observes signals, and the scoreboard is the one that compares actual and expected output.

**Key takeaway:** Adding my background, a word limit and an output format made the answers shorter and
more useful. Telling the tool how I want to be quizzed (one at a time vs all at once) changed the format, and each tool handled it well in its own way.

**Prompt I refined during the Verilator work:**
- Before: "Does Verilator support X and Z?"
- After: "Does Verilator's default simulation mode represent X and Z values? Answer yes/no first, then cite the
  official docs, and tell me how to test it myself."
- The second version forced a direct answer, a source and a test I could run.

## 3. Comparison: same question, two tools
**Question:** What is the difference between a UVM driver and a monitor?

| | ChatGPT | Gemini |
|---|---|---|
| Clarity | Table plus a worked ALU example (5 + 3 = 8) | Table plus a "closer look" section |
| Depth | Added an interview-ready one-sentence answer | Added virtual interface and analysis port details |
| Analogy | Followed the ALU thread | Video game: driver = player, monitor = replay camera |
| Sources given? | No | No |
| Errors? | None found | None found |

**Observation:** Both were correct and said the same core thing: the driver actively drives DUT
inputs from sequencer transactions, while the monitor only observes and rebuilds transactions.
ChatGPT was better for exam/interview wording; Gemini added slightly more UVM detail.

## 4. Claim I verified
**Question to both tools:** "Does Verilator simulate X and Z values the same way QuestaSim does?"
**Both answered: No.**
- ChatGPT: Verilator is traditionally two-state; an X assignment is replaced by a value chosen by `--x-assign`;
  it also said four-state work was announced in July 2026.
- Gemini: Verilator is mainly a two-state compiler; X/Z assignments become 0 or 1 (or random with `--x-initial`);
  tri-state is converted to enable signals; `===` against X behaves differently. It linked the Verilator docs.

**How I checked:**
1. *Official documentation:* Verilator's "Language Limitations" page, section "Unknown States" and
   "Tri/Inout": https://verilator.org/guide/latest/languages.html
2. *My own test:* in Verilator 5.020, `a = 4'bxxxx; $display("a = %b", a);` printed `a = 0000`.
3. *Date of the four-state news:* Antmicro's article is dated 30 April 2026
   (https://antmicro.com/blog/2026/04/initial-support-for-four-state-logic-in-verilator);
   CHIPS Alliance republished it on 22 July 2026
   (https://www.chipsalliance.org/news/initial-implementation-verilator/).

**What the sources established:**
- The docs call Verilator "mostly a two-state simulator". Assigning X gives a constant value chosen by
  `--x-assign`, and variables are initialised according to `--x-initial`. So both tools were right on these points.
- The docs say an `===` comparison against X is always false, so Verilog code that tests for uninitialised
  values will not fire. Gemini's `===` point is correct.
- The docs describe converting simple tri-state structures to two-state enable and output signals. Gemini was right.
- ChatGPT's "July 2026" is only partly right: the original announcement was in April 2026, and July is
  when CHIPS Alliance republished it. This is a small error that I only caught by checking.

**Conclusion:** Both tools were correct on the main claim. Gemini's answer was easier to check because it
linked the docs. ChatGPT mentioned newer developments but got a detail wrong. Four-state support is new and
experimental, so the answer depends on the Verilator version and flags.

**Why it matters for a DV engineer:** a 2-state simulator can hide X-related bugs such as uninitialised
registers or reset problems, so I should not rely on it alone for reset and initialisation checks.
