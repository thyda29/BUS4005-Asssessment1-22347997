# P04 · First response draft

**Section:** 02 — Response Drafting  
**Workflow step:** Step 4 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support agent for an online retail business.

Draft a professional first response email to the customer based on the issue details below.

Issue category: [ISSUE_CATEGORY]
Urgency level: [URGENCY_LEVEL]
Customer sentiment: [SENTIMENT]
Customer email:
[EMAIL_TEXT]

Instructions:
- Acknowledge the customer’s issue clearly
- Use an empathetic and professional tone
- Avoid admitting fault unless it is confirmed
- Explain the next step the support team will take
- If key information is missing, politely request it
- Keep the response between 120 and 180 words
- Do not invent order details, refund approvals, or delivery updates that are not provided

Respond as a complete email with:
- greeting
- body
- closing
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[ISSUE_CATEGORY]` | Output from P01 | Delivery issue |
| `[URGENCY_LEVEL]` | Output from P02 | Medium |
| `[SENTIMENT]` | Output from P02 | Frustrated |
| `[EMAIL_TEXT]` | Customer email from support inbox | "Hi, I ordered a jacket two weeks ago and it still hasn’t arrived..." |

---

## Intended Workflow or Task

This prompt supports the **first drafting step in the response workflow**. Once the customer email has been classified, checked for urgency, and reviewed for missing information, the support team needs a clear first reply that acknowledges the issue and sets expectations for the customer.

- **Trigger:** Intake and triage workflow completed
- **Actor:** Support agent
- **Timing:** Before any specialised response path such as refund, return, or delivery-specific handling
- **Next step:** Output is reviewed by the agent and either sent directly or used as the base for a more specific draft such as P05, P06, or P07

```text
P01–P03 completed → [P04 RUNS] → first response draft created
                                 → reviewed by support agent
                                 → sent to customer or adapted into specialist draft
```

---

## Problem Being Solved

Customer support agents often spend significant time writing first replies to routine customer emails. Even when the issue is straightforward, the agent still needs to acknowledge the problem, sound empathetic, avoid overpromising, and explain what will happen next. Writing these responses from scratch is repetitive and can slow down service during busy periods.

This also creates inconsistency. Different agents may use different tones, omit key reassurance, or forget to request missing information. That leads to uneven customer experience and more editing by senior team members.

**Pain points addressed:**
- repetitive drafting of standard first-response emails
- inconsistent tone and structure across support staff
- missing next-step information in customer replies
- slower response times during high-volume periods

---

## Automation Potential

**Level:** High

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | High — most support emails require an initial response |
| Data availability | High — triage outputs and customer email are already available |
| Human judgment needed | Moderate — final review still needed for accuracy and tone |
| Integration possibility | High — can be embedded into a helpdesk workflow or CRM drafting tool |
| Estimated time saving | ~70–80% compared with writing initial replies from scratch |

**Human-in-the-loop role:** The support agent should review the draft before sending, especially to confirm that no unsupported promises, policy statements, or inaccurate assumptions have been included.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Draft includes assumptions not stated in the customer email | Medium | Prompt explicitly says not to invent order details, refund approvals, or delivery updates |
| Tone feels too generic or robotic | Medium | Use empathy and professionalism constraints, with agent review before sending |
| Draft fails to request important missing information | Medium | Combine this prompt with P03 so the agent knows what information still needs to be requested |
| Staff rely on AI draft without checking policy fit | Medium | Human review remains mandatory before customer-facing use |

**Overall risk rating:** MEDIUM — strong drafting support for routine cases, but customer-facing replies still require staff review.

---

## Version History

### v1.0 — Initial draft
**Date:** 11 March 2025  
**Prompt:** `Write a response to this customer email: [EMAIL_TEXT]`  
**Output:** The model produced a polite response, but it was too broad and sometimes overexplained the issue without giving a clear next step.  
**Observed effect:** The draft still needed substantial editing before it could be used.  
**Lesson learned:** The prompt needed stronger structure, role framing, and clearer instructions about tone and next steps.

---

### v1.1 — Added role and response instructions
**Date:** 15 March 2025  
**Change:** Added customer support role, empathy instruction, and a requirement to explain the next step.  
**Output:** The model produced a better reply, but sometimes included assumptions about the order or service outcome.  
**Observed effect:** Draft quality improved, but factual control was still weak.  
**Lesson learned:** The prompt needed a stronger constraint against unsupported assumptions.

---

### v1.2 — Added constraints, word limit, and structured email format ✅ Current
**Date:** 20 March 2025  
**Change:** Added instructions not to invent details, included word limit, and required greeting/body/closing structure.  
**Output:** The model now generates more consistent first replies that are easier to review and closer to send-ready quality.  
**Observed effect:** Editing time decreased and the drafts became more usable across routine customer enquiries.  
**Lesson learned:** First-response prompts work best when empathy, structure, and factual limits are all made explicit.

---

## A/B Test Results

**Test date:** 21 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Tone appropriateness | 3/5 | 4.5/5 |
| Clarity of next step | 2/5 | 4.5/5 |
| Factual control | 2/5 | 4/5 |
| Overall usefulness | 2.5/5 | 4.5/5 |

---

## Related Prompts

- **Previous in chain:** [P03 — Missing information checker](../01-intake-triage/P03-missing-information-checker.md)
- **Next in chain:** [P05 — Refund and return response](P05-refund-return-response.md)
- **Alternative next prompts:** [P06 — Delivery delay response](P06-delivery-delay-response.md), [P07 — Complaint recovery response](P07-complaint-recovery-response.md)
- **Parent section:** [02 — Response Drafting Workflow](README.md)
- **Library index:** [Main README](../README.md)
