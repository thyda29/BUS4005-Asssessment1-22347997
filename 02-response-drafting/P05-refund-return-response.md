# P05 · Refund and return response

**Section:** 02 — Response Drafting  
**Workflow step:** Step 5 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support agent for an online retail business.

Draft a professional email response to a customer asking about a refund or return.

Customer issue details:
Issue category: [ISSUE_CATEGORY]
Urgency level: [URGENCY_LEVEL]
Customer sentiment: [SENTIMENT]
Customer email:
[EMAIL_TEXT]

Policy details:
[POLICY_DETAILS]

Instructions:
- Acknowledge the customer’s request clearly
- Use a polite, empathetic, and professional tone
- Explain the relevant refund or return process using only the policy details provided
- If important details are missing, politely ask for them
- Do not promise a refund, exchange, or return approval unless the policy details clearly support it
- Do not invent policy terms
- Keep the email between 140 and 200 words

Respond as a complete email with:
- greeting
- body
- closing
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[ISSUE_CATEGORY]` | Output from P01 | Refund request |
| `[URGENCY_LEVEL]` | Output from P02 | Medium |
| `[SENTIMENT]` | Output from P02 | Frustrated |
| `[EMAIL_TEXT]` | Customer email from support inbox | "Hi, I received the wrong item and would like a refund..." |
| `[POLICY_DETAILS]` | Internal store refund/return policy summary | "Refunds are available within 30 days for unused items with proof of purchase..." |

---

## Intended Workflow or Task

This prompt supports a **specialised response path for refund and return enquiries**. After the customer’s issue has been triaged, the support team may need a more policy-specific response rather than a general first reply.

- **Trigger:** Customer email is identified as a refund or return issue
- **Actor:** Support agent
- **Timing:** After intake and triage, and after initial issue understanding
- **Next step:** The draft is reviewed by the support agent and sent to the customer, or escalated if the case falls outside standard policy

```text
P01 identifies refund/return issue → [P05 RUNS]
                                 → policy-aligned draft created
                                 → agent reviews
                                 → sent to customer or escalated
```

---

## Problem Being Solved

Refund and return requests are among the most common and repetitive customer support tasks in online retail. Staff often need to explain the same policy conditions, request the same missing details, and use the same tone of reassurance. Writing these replies from scratch is time-consuming and can lead to inconsistency in how policy is communicated.

This creates risk because one support agent may explain the policy accurately while another may unintentionally overpromise, omit an important condition, or give unclear instructions. These inconsistencies can frustrate customers and increase unnecessary back-and-forth.

**Pain points addressed:**
- repetitive drafting of refund and return replies
- inconsistent explanation of store policy
- risk of agents overpromising outcomes
- slower handling of routine policy-based enquiries

---

## Automation Potential

**Level:** High

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | Very high — refund and return requests are common in online retail |
| Data availability | High — customer email and policy details are usually available |
| Human judgment needed | Moderate — staff still need to confirm policy fit and exceptions |
| Integration possibility | High — can be integrated into a helpdesk workflow using internal policy summaries |
| Estimated time saving | ~75–85% compared with writing policy responses manually |

**Human-in-the-loop role:** The support agent should review the draft before sending to ensure that the policy has been applied correctly and that no unsupported approval or exception has been implied.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Draft promises a refund or return outcome that has not been approved | High | Prompt explicitly forbids promising approval unless policy details clearly support it |
| Model invents policy terms not included in the source text | High | Prompt requires the reply to use only the provided policy details |
| Draft sounds too rigid or policy-heavy | Medium | Include empathy and professionalism instructions, then review before sending |
| Policy summary provided to the prompt is incomplete or outdated | Medium | Ensure policy details are current and validated before use |

**Overall risk rating:** MEDIUM — useful for standardising routine policy communication, but all customer-facing policy replies should still be reviewed by staff.

---

## Version History

### v1.0 — Initial draft
**Date:** 12 March 2025  
**Prompt:** `Write a reply to this customer asking for a refund: [EMAIL_TEXT]`  
**Output:** The model produced a polite response, but it sometimes assumed the refund would be approved and did not reference any actual store policy.  
**Observed effect:** The draft was too risky to use because it could mislead the customer about their entitlement.  
**Lesson learned:** Refund and return prompts must be grounded in actual policy details, not just general customer service language.

---

### v1.1 — Added policy context
**Date:** 16 March 2025  
**Change:** Added internal policy details and instructed the model to explain the process.  
**Output:** The draft became more useful, but sometimes still sounded too confident about outcomes.  
**Observed effect:** Policy alignment improved, but the response still needed stronger limits on promises and approvals.  
**Lesson learned:** It is not enough to add policy context; the prompt must also restrict what the model is allowed to promise.

---

### v1.2 — Added approval limits and tighter instructions ✅ Current
**Date:** 21 March 2025  
**Change:** Added instruction not to promise refund, return, or exchange approval unless the policy details clearly support it, plus a stronger word limit and structured format.  
**Output:** The draft became more controlled, clearer, and easier to review before sending.  
**Observed effect:** Responses were more consistent and less likely to create policy risk.  
**Lesson learned:** In policy-sensitive prompts, constraints are just as important as tone.

---

## A/B Test Results

**Test date:** 22 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Policy alignment | 1.5/5 | 4.5/5 |
| Tone appropriateness | 3/5 | 4.5/5 |
| Risk control | 1.5/5 | 4.5/5 |
| Overall usefulness | 2/5 | 4.5/5 |

---

## Related Prompts

- **Previous in chain:** [P04 — First response draft](P04-first-response-draft.md)
- **Alternative related prompt:** [P06 — Delivery delay response](P06-delivery-delay-response.md)
- **Parent section:** [02 — Response Drafting Workflow](README.md)
- **Library index:** [Main README](../README.md)
