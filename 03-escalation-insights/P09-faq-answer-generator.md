# P09 · FAQ answer generator

**Section:** 03 — Escalation and Insights  
**Workflow step:** Step 9 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support knowledge assistant for an online retail business.

Using the repeated customer enquiry example below, generate a clear FAQ-style answer that can be reused by support staff or adapted for a knowledge base.

Repeated enquiry type:
[ENQUIRY_TYPE]

Example customer question:
[EXAMPLE_QUESTION]

Approved business guidance:
[APPROVED_GUIDANCE]

Instructions:
- Write a concise and easy-to-understand answer
- Use only the approved business guidance provided
- Do not invent policy details, exceptions, or promises
- Keep the tone professional, helpful, and customer-friendly
- Keep the response between 80 and 140 words

Respond using this format:

FAQ question:
[write a clear reusable FAQ question]

FAQ answer:
[write the reusable answer]
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[ENQUIRY_TYPE]` | Repeated support issue identified by team | Delivery delay |
| `[EXAMPLE_QUESTION]` | Sample recurring customer question | "Why is my parcel taking longer than expected to arrive?" |
| `[APPROVED_GUIDANCE]` | Internal approved support guidance or policy notes | "Delivery delays may occur during peak periods..." |

---

## Intended Workflow or Task

This prompt supports the **knowledge support stage** of the workflow. When the team notices repeated enquiry types, they can use this prompt to turn those issues into reusable FAQ-style responses that improve consistency and reduce repetitive drafting.

- **Trigger:** A recurring enquiry type is identified
- **Actor:** Support lead, knowledge manager, or support agent
- **Timing:** After repeated cases have been observed
- **Next step:** FAQ answer is reviewed and added to internal support guidance or adapted for external help content

```text
Repeated enquiry identified → [P09 RUNS]
                          → reusable FAQ answer created
                          → reviewed by support lead
                          → added to knowledge base or agent guidance
```

---

## Problem Being Solved

Support teams often answer the same types of customer questions again and again. Without reusable knowledge content, agents keep rewriting similar responses, which wastes time and increases inconsistency.

This problem becomes larger as enquiry volume increases. Some agents may explain the issue clearly, while others may omit key details or use different wording. Turning repeated enquiries into FAQ-style answers helps standardise guidance and reduce avoidable effort.

**Pain points addressed:**
- repetitive drafting of the same answers
- inconsistent wording across staff
- lack of reusable support knowledge
- unnecessary time spent rewriting routine explanations

---

## Automation Potential

**Level:** Medium

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | High — repeated enquiry patterns are common |
| Data availability | Medium to high — recurring questions and approved guidance must be available |
| Human judgment needed | Moderate — final approval of reusable guidance is still needed |
| Integration possibility | Medium — can support internal knowledge bases and help-centre drafting |
| Estimated time saving | ~60–75% compared with writing FAQ content from scratch |

**Human-in-the-loop role:** A support lead or policy owner should review the FAQ before it is reused widely, especially if it may be shown to customers or embedded in a public help centre.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| FAQ answer includes policy details not actually approved | High | Prompt requires use of approved guidance only |
| Answer is too generic to be genuinely useful | Medium | Use a specific enquiry type and example question as input |
| FAQ oversimplifies exceptions or edge cases | Medium | Human review required before publishing |
| Staff reuse outdated FAQ content | Medium | Approved guidance should be reviewed regularly |

**Overall risk rating:** MEDIUM — useful for drafting reusable knowledge content, but final approval remains necessary.

---

## Version History

### v1.0 — Initial draft
**Date:** 16 March 2025  
**Prompt:** `Write an FAQ answer about delivery delays.`  
**Output:** The model produced a reasonable answer, but it was generic and not clearly tied to approved business guidance.  
**Observed effect:** The result was too risky to use as official reusable content.  
**Lesson learned:** FAQ prompts need approved source guidance, not open-ended generation.

---

### v1.1 — Added approved guidance input
**Date:** 20 March 2025  
**Change:** Added internal approved guidance as a source for the answer.  
**Output:** The response became more aligned with the business, but the question-and-answer format was still inconsistent.  
**Observed effect:** Content quality improved, but it was not yet easy to reuse directly in a knowledge base.  
**Lesson learned:** Reusable support content works better when the output structure is fixed.

---

### v1.2 — Added reusable FAQ structure and tighter limits ✅ Current
**Date:** 25 March 2025  
**Change:** Added fixed FAQ question-and-answer format, shorter length, and instruction not to invent details or exceptions.  
**Output:** The result became clearer, more reusable, and easier to review for knowledge-base use.  
**Observed effect:** Drafting effort dropped and consistency improved across repeated support topics.  
**Lesson learned:** Structured outputs are especially useful for internal knowledge content.

---

## A/B Test Results

**Test date:** 26 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Reusability | 2/5 | 4.5/5 |
| Alignment with approved guidance | 2/5 | 4.5/5 |
| Clarity for staff use | 2.5/5 | 4.5/5 |
| Overall usefulness | 2.5/5 | 4.5/5 |

---

## Related Prompts

- **Related input source:** [P10 — Weekly support insights summary](P10-weekly-support-summary.md)
- **Parent section:** [03 — Escalation and Insights Workflow](README.md)
- **Library index:** [Main README](../README.md)
