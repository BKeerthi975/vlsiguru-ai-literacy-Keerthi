# Week 01 Verification Log

| Date | Question / claim | AI tool | Claim checked | Verification source / experiment | Result |
|---|---|---|---|---|---|
| Oct 5, 2026 | Q1/Q2 - source for the definition of generative AI | AI assistant | Google Cloud's generative AI page defines it | Opened the link | The link now redirects to a product page with no definition; replaced with IBM Research "What is generative AI?" |
| Oct 5, 2026 | Q2 - source on ML vs traditional programming | AI assistant | Google's `crash-course/ml-intro` page | Searched for the page | Outdated address; replaced with `developers.google.com/machine-learning/intro-to-ml` |
| Oct 5, 2026 | Q3 - source on next-token prediction | AI assistant | A blog post as the second source | Looked for a stronger source | Replaced with the Hugging Face LLM course, chapter 1 |
| Oct 6, 2026 | Q4 - blocking vs non-blocking | ChatGPT | `=` for combinational, `<=` for sequential; `<=` updates later in the time step | Cummings, SNUG 2000 | Correct but incomplete (no race conditions, no rule against mixing styles) |
| Oct 6, 2026 | Q4 - blocking vs non-blocking | Gemini | Six "Cummings guidelines" | Cummings, SNUG 2000, section 5.0 (eight guidelines) | Five of six match; the item about blocking assignments inside `assign` statements is not in the paper |
| Oct 6, 2026 | Q4 - blocking vs non-blocking | Gemini | Clocked block with blocking assignments "synthesizes into a single wire" | Cummings, SNUG 2000, section 8.0, Example 5 | Partly wrong: the paper says a single register (flip-flop), not a wire |
| Oct 7, 2026 | Q5 - HTTP 301 vs 302 | Gemini | 302 is named "Found (Temporary Redirect)" | RFC 9110, section 15.4.3 | Imprecise: 302 is "Found"; "Temporary Redirect" is 307 |
| Oct 7, 2026 | Q5 - HTTP 301 vs 302 | Gemini | 301 passes about 90-99% link equity | RFC 9110 (silent on SEO); three web sources | Unsupported; web sources disagree |
| Oct 7, 2026 | Q5 - HTTP 301 vs 302 | Web search results | Whether a 302 passes link value | Three SEO web pages | Sources contradict each other; unresolved |
| Oct 7, 2026 | Q7 - Mata v. Avianca | AI assistant | Lawyers were sanctioned $5,000 for fake ChatGPT citations | LawNext article | Confirmed |
| Oct 7, 2026 | Q8 - source links | AI assistant | Links for Gmail spam and YouTube paper | Searched for the pages and opened them | Two links were wrong; replaced with working URLs |
| Oct 8, 2026 | Q8 - microwave and price-alert examples | ChatGPT / Gemini | "User manuals" and "Retail Tech Architecture Specs" as evidence | Searched for them | Could not find real, checkable sources; removed |
| Oct 8, 2026 | Q8 - microwave auto-defrost internals | None | Is it rule-based? | No public source found | Not enough public evidence to conclude |
| Oct 8, 2026 | Q8 - all six links | None | Each page supports the claim in my table | Opened every link | Confirmed |
| Oct 8, 2026 | Q9 - source for next-token prediction | AI assistant | A paper titled "Unreasonable Effectiveness of Autoregressive Language Modeling" by Sutskever | Web search | Could not find it; removed |
| Oct 8, 2026 | Q9 - classification vs prediction for churn | ChatGPT / Gemini | Is churn classification or prediction? | The output is a label ("cancel" or "stay") | Classified as classification, with a caveat |
| Oct 8, 2026 | Q10 - wire resistance values | AI assistant | 12, 10 and 8 AWG copper resistance at 20 C | HyperPhysics AWG table; Wikipedia AWG | Confirmed (1.588, 0.9989, 0.6282 ohm per 1000 ft) |
| Oct 8, 2026 | Q10 - NEC Table 8 as the source | AI assistant | Resistance values come from NEC Chapter 9 Table 8 | Compared with the standard 20 C AWG tables | Source not confirmed; replaced with HyperPhysics |
| Oct 8, 2026 | Q10 - NASA handbook claim | AI assistant | "NASA standards dictate" independent verification | Could not confirm wording | Removed |
| Oct 8, 2026 | Q10 - voltage drop numbers | AI assistant | 5.95%, 3.74%, 2.35% | Recalculated | Corrected to 5.96%, 3.75%, 2.36% (rounding) |

## Notes

- **What did the AI get right?** The core concepts: blocking vs non-blocking, 301 vs 302 meanings, the wire-resistance values, and the overall structure of my answers.
- **What did it get wrong or leave unsupported?** Exact links, citations that do not exist, a guideline attributed to a named paper, and precise-looking numbers with no source.
- **What did I learn about verification?** Open every link yourself. A named source is not proof that the source says what the AI claims. Detailed, well-formatted answers can hide the errors.

- **What did I learn about verification?** Open every link yourself. A named source is not proof that the source says what the AI claims. Detailed, well-formatted answers can hide the errors.
