# P02 · Urgency and sentiment detection

**Section:** 01 — Intake and Triage  
**Workflow step:** Step 2 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support triage assistant for an online retail business.

Review the following customer email and assess:

1. Urgency level: Low, Medium, or High
2. Customer sentiment: Positive, Neutral, Frustrated, or Angry

Use these urgency rules:
- High: the email mentions legal action, discrimination, safety concerns, repeated unresolved issues, or a highly time-sensitive event
- Medium: the customer is clearly dissatisfied, inconvenienced, or facing a service delay, but the issue does not involve major risk
- Low: the issue is routine, low-impact, or informational

Customer email:
[EMAIL_TEXT]

Rules:
- Base your judgement only on the email content
- Do not invent facts or exaggerate urgency
- If the customer sounds upset but the business risk is low, keep urgency and sentiment separate

Respond in JSON only using this format:

{
  "urgency": "[Low / Medium / High]",
  "sentiment": "[Positive / Neutral / Frustrated / Angry]",
  "reason": "[one short sentence explaining the assessment]"
}
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[EMAIL_TEXT]` | Customer email from support inbox or web form | "Hi, I’m disappointed that my parcel still hasn’t arrived and I need it before this weekend..." |

---

## Intended Workflow or Task

This prompt supports the **second step of the intake and triage workflow**. After the email has been classified into a main issue category, the next task is to assess how urgent the case is and what tone the customer is expressing.

- **Trigger:** Customer email has already been classified by P01
- **Actor:** Support agent, team lead, or automated triage system
- **Timing:** Immediately after issue classification
- **Next step:** Output helps prioritise the case for response drafting and identifies whether escalation or supervisor review may be needed

```text
Customer email received → P01 classifies issue → [P02 RUNS]
                                           → urgency and sentiment assessed
                                           → case prioritised for next workflow step
```

---

## Problem Being Solved

Not all customer emails should be handled in the same order. Some are routine service enquiries, while others involve strong dissatisfaction, repeated unresolved problems, or high-risk concerns that need faster attention. In a busy support environment, agents may not always identify urgency consistently, especially when many messages arrive close together.

This creates operational problems because a serious case may sit too long in the queue, while a low-priority case may receive unnecessary attention. It can also lead to inconsistent service recovery decisions, especially when different staff interpret customer tone differently.

**Pain points addressed:**
- inconsistent judgement of urgency across staff
- delayed response to serious or time-sensitive issues
- poor visibility of emotionally charged customer messages
- inefficient prioritisation of customer support workload

---

## Automation Potential

**Level:** High

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | High — every incoming email can be assessed for urgency and sentiment |
| Data availability | High — the necessary input is contained in the email text |
| Human judgment needed | Moderate — routine cases can be supported well, but high-risk cases still need review |
| Integration possibility | High — output can support queue prioritisation, SLA monitoring, or escalation alerts |
| Estimated time saving | ~70–80% for initial urgency review compared with full manual assessment |

**Human-in-the-loop role:** Staff should review any case marked High urgency, especially where legal threats, repeated service failure, safety concerns, or sensitive complaints are involved. Human review is also important where the model may confuse emotional tone with actual business risk.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Model confuses frustration with true business urgency | Medium | Add explicit urgency criteria and require staff review for High urgency outputs |
| Model underestimates a serious complaint | High | Escalate all High-risk keywords such as legal action, discrimination, safety concerns, or repeated unresolved issues |
| Sentiment labels oversimplify the customer’s tone | Low | Use broad sentiment categories and treat them as support signals, not exact emotional analysis |
| Staff rely too heavily on the model’s urgency decision | Medium | Treat output as triage support only and keep human oversight for escalations |

**Overall risk rating:** MEDIUM — useful for prioritisation support, but high-urgency outputs should always be reviewed by a human.

---

## Version History

### v1.0 — Initial draft
**Date:** 9 March 2025  
**Prompt:** `Read this email and say how urgent it is: [EMAIL_TEXT]`  
**Output:** The model gave a general opinion, but urgency labels were inconsistent and sentiment was not considered separately.  
**Observed effect:** The output was too loose to support reliable prioritisation in a workflow.  
**Lesson learned:** The prompt needed defined urgency criteria and a more structured output format.

---

### v1.1 — Added urgency scale and sentiment label
**Date:** 13 March 2025  
**Change:** Added Low/Medium/High urgency and separate sentiment categories.  
**Output:** The model became more consistent, but sometimes treated an annoyed tone as automatically High urgency.  
**Observed effect:** Better structure, but business risk and customer emotion were still being mixed together.  
**Lesson learned:** The prompt needed stronger rules to separate urgency from sentiment.

---

### v1.2 — Added explicit urgency rules and JSON output ✅ Current
**Date:** 18 March 2025  
**Change:** Added clear urgency definitions, instruction to separate urgency from sentiment, and JSON-only output.  
**Output:** The model now produces clearer and more consistent urgency and sentiment assessments that are easier to use in triage.  
**Observed effect:** Outputs became more reliable for queue prioritisation, with fewer exaggerated urgency ratings.  
**Lesson learned:** AI performs better in support workflows when emotional tone and operational risk are defined separately.

---

## A/B Test Results

**Test date:** 19 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Consistency of urgency rating | 2/5 | 4.5/5 |
| Separation of urgency and sentiment | 1/5 | 4.5/5 |
| Ease of use in workflow | 2/5 | 4/5 |
| Overall usefulness | 2/5 | 4.5/5 |

---

## 🔗 Related Prompts

- **Previous in chain:** [P01 — Email classification](P01-email-classification.md)
- **Next in chain:** [P03 — Missing information checker](P03-missing-information-checker.md)
- **Parent section:** [01 — Intake and Triage Workflow](README.md)
- **Library index:** [Main README](../README.md)
