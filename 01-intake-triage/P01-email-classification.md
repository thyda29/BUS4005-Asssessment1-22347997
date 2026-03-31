# P01 · Email classification

**Section:** 01 — Intake and Triage  
**Workflow step:** Step 1 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support triage assistant for an online retail business.

Classify the following customer email into EXACTLY ONE primary issue category from this list:

- Refund request
- Return request
- Delivery issue
- Damaged or faulty item
- Wrong item received
- Account or payment issue
- General complaint
- Product enquiry
- Other

Customer email:
[EMAIL_TEXT]

Rules:
- Choose the single best category only
- Do not invent facts that are not stated in the email
- If the issue is unclear or does not match the list, choose "Other"

Respond in JSON only using this format:

{
  "category": "[chosen category]",
  "reason": "[one short sentence explaining the classification]"
}
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[EMAIL_TEXT]` | Customer email from support inbox or web form | "Hi, I ordered a jacket two weeks ago and it still hasn’t arrived. Can you please check what’s going on?" |

---

## Intended Workflow or Task

This prompt supports the **first step of the customer email workflow**. It is used to classify incoming customer emails into one main issue category before the email moves into urgency review, missing-information checks, and response drafting.

- **Trigger:** New customer email received in the support inbox
- **Actor:** Support agent, team lead, or automated triage system
- **Timing:** Immediately after the email is received
- **Next step:** Output is used by P02 (Urgency and sentiment detection) and helps decide which response drafting path should follow later in the workflow

```text
Customer email received → [P01 RUNS] → Issue category assigned
                                      → P02 runs
                                      → Later routed to refund / delivery / complaint response path
```

---

## Problem Being Solved

Customer support teams in online retail often receive large volumes of emails every day, but not all messages are about the same issue. Staff must first read each email and determine whether it concerns a refund, return, delivery problem, damaged item, wrong item, payment issue, or complaint.

When this classification is done manually, it can be slow and inconsistent. Different agents may interpret the same message differently, which can lead to poor routing and delays in response preparation. This creates inefficiency in the workflow and increases the chance that a customer email enters the wrong process path.

**Pain points addressed:**
- repetitive manual classification of routine support emails
- inconsistent issue categorisation between staff members
- slower routing into the correct support response path
- avoidable delays during high-volume periods

---

## ⚡ Automation Potential

**Level:** Very High

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | Very high — every incoming email needs initial classification |
| Data availability | High — the email text is already available at intake |
| Human judgment needed | Low for routine cases; moderate for unclear or mixed-issue emails |
| Integration possibility | High — output can support CRM tagging, queue routing, or downstream prompt selection |
| Estimated time saving | ~80–90% for initial triage support compared with fully manual classification |

**Human-in-the-loop role:** Staff should still review categories in ambiguous or high-risk cases. Emails classified as "Other" or containing multiple issues should be checked manually before moving forward.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Email contains more than one issue, but the prompt forces only one category | Medium | Use the "single best category" rule and manually review multi-issue or unclear emails |
| Model misclassifies the email due to vague wording | Medium | Include "Other" as a fallback category and require human review for unclear cases |
| Model invents unstated facts when explaining the classification | Medium | Add constraint: "Do not invent facts that are not stated in the email" |
| Staff rely on classification without checking edge cases | Medium | Keep human oversight for unusual, emotional, or high-risk complaints |

**Overall risk rating:** MEDIUM — suitable for workflow support and partial automation, but not for fully unattended decision-making.

---

## Version History

### v1.0 — Initial draft
**Date:** 8 March 2025  
**Prompt:** `Classify this customer email: [EMAIL_TEXT]`  
**Output:** The model produced a broad explanation, but the categories were inconsistent and sometimes too vague, such as "shipping problem" or "customer dissatisfaction."  
**Observed effect:** Output was not standardised enough to support routing or consistent workflow handling.  
**Lesson learned:** The prompt needed a fixed list of categories and a more structured output format.

---

### v1.1 — Added fixed categories
**Date:** 12 March 2025  
**Change:** Added an explicit list of customer support categories and instructed the model to choose only one.  
**Output:** Category consistency improved, but the model still responded in full sentences and sometimes added extra commentary.  
**Observed effect:** Better classification quality, but outputs were still harder to use in a structured workflow.  
**Lesson learned:** A constrained output format was needed so the result could be easily reused by later workflow steps.

---

### v1.2 — Added JSON output and stricter constraints ✅ Current
**Date:** 17 March 2025  
**Change:** Added JSON-only output, the "single best category" rule, and a constraint against inventing facts.  
**Output:** The model now produces a short, structured result that is easier to review and reuse in downstream prompts.  
**Observed effect:** Classification became more consistent and usable for workflow routing, with fewer ambiguous outputs.  
**Lesson learned:** Fixed categories plus structured output make AI classification much more reliable in business workflows.

---

## A/B Test Results

**Test date:** 18 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Consistency of category labels | 2/5 | 4.5/5 |
| Ease of reuse in workflow | 1/5 | 4.5/5 |
| Clarity of output | 2/5 | 4/5 |
| Overall usefulness | 2/5 | 4.5/5 |

---

## Related Prompts

- **Next in chain:** [P02 — Urgency and sentiment detection](P02-urgency-sentiment.md)
- **Parent section:** [01 — Intake and Triage Workflow](README.md)
- **Library index:** [Main README](../README.md)
