# P07 · Complaint recovery response

**Section:** 02 — Response Drafting  
**Workflow step:** Step 7 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support agent for an online retail business.

Draft a professional complaint recovery email for a customer who has had a poor experience.

Customer issue details:
Issue category: [ISSUE_CATEGORY]
Urgency level: [URGENCY_LEVEL]
Customer sentiment: [SENTIMENT]
Customer email:
[EMAIL_TEXT]

Available case notes:
[CASE_NOTES]

Instructions:
- Acknowledge the customer’s frustration or dissatisfaction clearly
- Use an empathetic, calm, and professional tone
- Apologise for the customer’s experience without admitting unverified fault
- Summarise the next step the business will take
- If the case needs further review, say that it is being investigated
- Do not promise compensation, refunds, or outcomes unless clearly supported by the case notes
- Do not invent facts or policy terms
- Keep the email between 140 and 220 words

Respond as a complete email with:
- greeting
- body
- closing
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[ISSUE_CATEGORY]` | Output from P01 | General complaint |
| `[URGENCY_LEVEL]` | Output from P02 | High |
| `[SENTIMENT]` | Output from P02 | Angry |
| `[EMAIL_TEXT]` | Customer complaint email | "I have contacted your team twice already and still have no solution..." |
| `[CASE_NOTES]` | Internal support notes or known case details | "Previous contact logged 2 days ago. Refund not yet approved. Supervisor review pending." |

---

## Intended Workflow or Task

This prompt supports a **specialised complaint recovery path** for cases where a customer has had a poor experience and the business needs to respond carefully. These complaints may involve repeated service failure, emotionally charged language, or dissatisfaction that goes beyond a simple routine request.

- **Trigger:** Customer email is identified as a complaint or service recovery case
- **Actor:** Support agent or supervisor
- **Timing:** After intake and triage, and after the case has been recognised as requiring a more sensitive response
- **Next step:** The draft is reviewed by support staff and either sent to the customer or escalated further if the complaint involves serious risk

```text
P01 identifies complaint case → [P07 RUNS]
                            → complaint recovery draft created
                            → reviewed by support agent or supervisor
                            → sent to customer or escalated further
```

---

## Problem Being Solved

Complaint recovery emails are more sensitive than routine customer support responses. Staff need to acknowledge the customer’s dissatisfaction, show empathy, explain the next step, and avoid making unsupported promises. Writing these messages from scratch takes time and requires careful judgement, especially when the customer is already frustrated.

Without a structured approach, different support agents may respond inconsistently. Some replies may sound too defensive, too generic, or too casual, while others may unintentionally admit fault or promise outcomes that have not been approved. This creates reputational risk and can worsen the customer experience.

**Pain points addressed:**
- repetitive drafting of emotionally sensitive complaint responses
- inconsistent complaint-handling tone across agents
- risk of overpromising or admitting unverified fault
- slower handling of escalated customer dissatisfaction

---

## Automation Potential

**Level:** Medium

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | Medium to high — complaint responses follow recurring patterns but require more care |
| Data availability | Medium to high — customer email and case notes are usually available |
| Human judgment needed | High — complaint tone, risk level, and next steps still require review |
| Integration possibility | Medium — useful inside support workflows but not suitable for unattended sending |
| Estimated time saving | ~50–65% compared with drafting complaint recovery emails manually |

**Human-in-the-loop role:** A support agent or supervisor should always review the draft before it is sent. This is especially important when the customer mentions repeated unresolved issues, legal action, discrimination, or requests for compensation.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Draft admits fault that has not been confirmed | High | Prompt instructs the model to apologise for the experience without admitting unverified fault |
| Draft promises compensation or resolution not yet approved | High | Prompt explicitly forbids unsupported promises |
| Tone sounds too generic or not empathetic enough | Medium | Tone guidance plus human review before sending |
| Model invents details not contained in the email or case notes | High | Prompt requires use of provided information only |

**Overall risk rating:** HIGH — useful for drafting support, but complaint recovery responses should always be reviewed by a human before being sent.

---

## Version History

### v1.0 — Initial draft
**Date:** 14 March 2025  
**Prompt:** `Write a response to this unhappy customer: [EMAIL_TEXT]`  
**Output:** The model produced a polite message, but it was too generic and sometimes apologised too broadly without clear next steps.  
**Observed effect:** The draft did not feel strong enough for a real complaint-handling context.  
**Lesson learned:** Complaint responses need more structure, clearer boundaries, and better guidance on how to apologise safely.

---

### v1.1 — Added empathy and next-step structure
**Date:** 18 March 2025  
**Change:** Added instructions to acknowledge dissatisfaction, apologise, and explain the next step.  
**Output:** The draft became more appropriate, but it sometimes sounded too confident about what the business would do next.  
**Observed effect:** The response quality improved, but risk remained around unsupported promises and assumptions.  
**Lesson learned:** Complaint recovery prompts need strict controls on what can and cannot be promised.

---

### v1.2 — Added case notes and stronger risk controls ✅ Current
**Date:** 23 March 2025  
**Change:** Added internal case notes, instruction not to admit unverified fault, and restrictions on unsupported outcomes or compensation promises.  
**Output:** The model now produces more balanced complaint responses that are empathetic while remaining operationally safe.  
**Observed effect:** Drafts became more usable for supervisor review and less risky in sensitive situations.  
**Lesson learned:** In complaint-handling workflows, empathy must be balanced with factual and policy control.

---

## A/B Test Results

**Test date:** 24 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Empathy and tone | 3/5 | 4.5/5 |
| Clarity of next step | 2/5 | 4.5/5 |
| Risk control | 2/5 | 4.5/5 |
| Overall usefulness | 2.5/5 | 4.5/5 |

---

## Related Prompts

- **Previous in chain:** [P04 — First response draft](P04-first-response-draft.md)
- **Next possible escalation:** [P08 — Escalation summary](../03-escalation-insights/P08-escalation-summary.md)
- **Parent section:** [02 — Response Drafting Workflow](README.md)
- **Library index:** [Main README](../README.md)
