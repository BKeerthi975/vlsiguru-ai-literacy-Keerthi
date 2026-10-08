# Week 01 AI Assistant Comparison

## Common question

In Verilog, what is the difference between blocking (`=`) and non-blocking (`<=`) assignments, and when is each typically used?

## Tool 1

Name: ChatGPT (version not recorded)

Answer summary: Blocking assignments update immediately; non-blocking assignments evaluate the right side now and update the left side later in the same time step. Blocking is typical for combinational logic and non-blocking for clocked logic. It gave two short examples.

Strengths: Short, clear, correct on the main idea.

Weaknesses: Did not mention race conditions or the rule against mixing the two styles in one block. No sources.

## Tool 2

Name: Gemini (Flash)

Answer summary: Same core idea, plus a comparison table, scheduler regions (Active vs NBA), a shift-register example, and a list of six guidelines attributed to Clifford Cummings.

Strengths: More detailed and better structured; covered mixing styles and assigning one variable from several always blocks.

Weaknesses: One listed guideline (blocking assignments inside `assign` statements) is not in the Cummings paper. The "single wire" statement is wrong; the paper says a single register (flip-flop).

Note: Both Gemini answers (Verilog and 301 vs 302) were asked in the same Gemini chat, so earlier messages in that chat were available to it as context.

## Verification source

Clifford Cummings, "Nonblocking Assignments in Verilog Synthesis, Coding Styles That Kill!" (SNUG San Jose 2000): https://rfsoc.mit.edu/6S965/_static/F24/lectures/CummingsSNUG2000SJ_NBA.pdf

## Final comparison

- Accuracy: ChatGPT was correct but less complete. Gemini was mostly correct with two problems.
- Traceability: Neither gave links. Gemini named a source, but one item in its list did not match that source.
- Explanation quality: Gemini was more thorough; ChatGPT was simpler and easier to read quickly.
- Ease of verification: ChatGPT made fewer claims, so it was easier to check. Gemini made more claims, so there was more to verify.
- Which claims required correction or qualification? The `assign` statement guideline and the "single wire" claim.

## Lesson

A more detailed answer is not automatically a more reliable one. The errors were hidden among many correct statements, and attaching a famous name to a list made it look trustworthy. I should check each item against the source, not just my overall impression.
