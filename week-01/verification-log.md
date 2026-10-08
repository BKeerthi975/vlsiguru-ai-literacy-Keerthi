# Week 01 Verification Log

| Date | Question / claim | AI tool | Claim checked | Verification source / experiment | Result |
|---|---|---|---|---|---|
| Oct 5, 2026 | Q1/Q2 - Generative AI definition | AI assistant | Google Cloud's generative AI page defines generative AI | IBM Research: https://research.ibm.com/blog/what-is-generative-AI | Original source was not suitable; replaced with IBM Research and verified the definition. |
| Oct 5, 2026 | Q2 - ML vs traditional programming | AI assistant | Google's ML introduction page | Google for Developers: https://developers.google.com/machine-learning/intro-to-ml | Original URL was outdated; replaced it with the current Google ML page. |
| Oct 5, 2026 | Q3 - Next-token prediction | AI assistant | LLMs predict the next token | Hugging Face LLM Course: https://huggingface.co/learn/llm-course/chapter1 | Verified the concept using the LLM course and removed the weaker source. |
| Oct 6, 2026 | Q4 - Blocking vs non-blocking | ChatGPT | `=` is blocking and `<=` is non-blocking; non-blocking assignments update later in the simulation time step | Cummings SNUG paper: https://csg.csail.mit.edu/6.375/6_375_2009_www/papers/cummings-nonblocking-snug99.pdf | Core explanation was correct but incomplete because it did not mention race conditions and other coding guidelines. |
| Oct 6, 2026 | Q4 - Cummings guidelines | Gemini | Gemini claimed six guidelines were from Cummings | Cummings SNUG paper: https://csg.csail.mit.edu/6.375/6_375_2009_www/papers/cummings-nonblocking-snug99.pdf | Five matched the paper; one claimed guideline was not found in the paper. |
| Oct 6, 2026 | Q4 - Clocked blocking assignment | Gemini | Blocking assignment in a clocked block synthesizes into a single wire | Cummings SNUG paper, Example 5: https://csg.csail.mit.edu/6.375/6_375_2009_www/papers/cummings-nonblocking-snug99.pdf | Incorrect wording. The paper describes a single register/flip-flop, not a wire. |
| Oct 7, 2026 | Q5 - HTTP 301 vs 302 | Gemini | 302 is "Found (Temporary Redirect)" | RFC 9110: https://www.rfc-editor.org/rfc/rfc9110.html | Corrected: 302 is "Found"; 307 is "Temporary Redirect." |
| Oct 7, 2026 | Q5 - 301 link equity | Gemini | 301 passes about 90–99% link equity | RFC 9110: https://www.rfc-editor.org/rfc/rfc9110.html; additional SEO sources | Unsupported. RFC 9110 does not give an SEO percentage and web sources disagreed. |
| Oct 7, 2026 | Q7 - Mata v. Avianca | AI assistant | Lawyers were sanctioned for fake ChatGPT citations | U.S. District Court decision: https://www.nysd.uscourts.gov/sites/default/files/2023-08/Mata%20v.%20Avianca%20-%20Sanctions%20Decision.pdf | Confirmed. |
| Oct 7, 2026 | Q8 - Gmail spam source | AI assistant | Gmail spam information and source link | Google Gmail Help: https://support.google.com/mail/answer/1366858 | Verified the official Gmail Help page. |
| Oct 8, 2026 | Q8 - Microwave and price-alert examples | ChatGPT / Gemini | Claimed manuals/specifications supported the examples | Web search for the claimed documents | Could not find reliable, checkable sources; unsupported sources were removed. |
| Oct 8, 2026 | Q8 - Microwave auto-defrost | None | Whether the internal operation is rule-based | Web search | No reliable public source found; conclusion left unresolved. |
| Oct 8, 2026 | Q9 - Churn classification | ChatGPT / Gemini | Whether "cancel/stay" is classification | Google for Developers: https://developers.google.com/machine-learning/crash-course/classification | Confirmed as binary classification because the output is a category such as "cancel" or "stay." It can also broadly be called churn prediction. |
| Oct 8, 2026 | Q9 - Next-token prediction source | AI assistant | Claimed paper titled "Unreasonable Effectiveness of Autoregressive Language Modeling" by Sutskever | Web search | Could not find a reliable source for the claimed paper; citation was removed. |
| Oct 8, 2026 | Q10 - AWG resistance values | AI assistant | 12, 10 and 8 AWG copper resistance at 20°C | HyperPhysics: https://hyperphysics.gsu.edu/hbase/Tables/wirega.html | Confirmed: 12 AWG = 1.588 Ω/1000 ft, 10 AWG = 0.9989 Ω/1000 ft, 8 AWG = 0.6282 Ω/1000 ft. |
| Oct 8, 2026 | Q10 - NEC Table 8 source | AI assistant | Claimed values came from NEC Chapter 9 Table 8 | Compared the claim with the verified AWG table | Source could not be confirmed; HyperPhysics was used instead. |
| Oct 8, 2026 | Q10 - NASA standards claim | AI assistant | "NASA standards dictate" the calculation | Web search | Could not verify the wording; claim was removed. |
| Oct 8, 2026 | Q10 - Voltage-drop calculation | AI assistant | 5.95%, 3.74%, 2.35% | Recalculated using verified resistance values | Corrected to 5.96%, 3.75%, and 2.36% due to rounding. |

## Notes

- **What did the AI get right?** The core concepts, including blocking vs non-blocking assignments, HTTP 301 vs 302 meanings, AWG resistance values, and the overall structure of the answers.
- **What did it get wrong or leave unsupported?** Some links were outdated or incorrect, some citations could not be found, one guideline was incorrectly attributed to a named paper, and some precise numerical claims did not have reliable sources.
- **What did I learn about verification?** I learned that I should open every important link myself and check whether the source actually supports the claim. A detailed answer with a citation can still contain errors.
