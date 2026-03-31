# P06 · Delivery delay response

**Section:** 02 — Response Drafting  
**Workflow step:** Step 6 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support agent for an online retail business.

Draft a professional email response to a customer reporting a delayed delivery.

Customer issue details:
Issue category: [ISSUE_CATEGORY]
Urgency level: [URGENCY_LEVEL]
Customer sentiment: [SENTIMENT]
Customer email:
[EMAIL_TEXT]

Available delivery information:
[DELIVERY_DETAILS]

Instructions:
- Acknowledge the delay and the inconvenience caused
- Use an empathetic, calm, and professional tone
- Explain the next step using only the delivery information provided
- If the delivery status is unclear, state that the team will investigate
- Do not promise compensation, refunds, or delivery dates unless clearly supported by the delivery information
- Do not invent courier updates or tracking events
- Keep the email between 140 and 200 words

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
| `[EMAIL_TEXT]` | Customer email from support inbox | "Hi, my order still hasn’t arrived and the tracking hasn’t updated in days..." |
| `[DELIVERY_DETAILS]` | Tracking or courier status available to support staff | "Tracking last updated 3 days ago. Parcel marked in transit. No confirmed delivery exception yet." |

---

## Intended Workflow or Task

This prompt supports a **specialised response path for delayed delivery enquiries**. When the customer’s issue has been classified as a delivery problem, the support team needs a reply that is empathetic, accurate, and aligned with the latest delivery information available.

- **Trigger:** Customer email is identified as a delivery issue
- **Actor:** Support agent
- **Timing:** After intake and triage, when delivery-related information is available
- **Next step:** The draft is reviewed and sent to the customer, or escalated if the delay appears severe, repeated, or high-risk

```text
P01 identifies delivery issue → [P06 RUNS]
                            → delivery response draft created
                            → agent reviews delivery details
                            → sent to customer or escalated
```

---

## Problem Being Solved

Delayed delivery complaints are common in online retail, especially during high-demand periods, courier disruptions, or peak seasons. Support agents often need to send very similar replies: acknowledge the inconvenience, explain what is currently known, and outline the next step. Writing these responses from scratch is repetitive and time-consuming.

There is also a service-risk issue. If staff guess at delivery updates or overpromise arrival dates, customer frustration may increase when expectations are not met. Consistency is important because the tone of these replies directly affects customer satisfaction and trust.

**Pain points addressed:**
- repetitive drafting of delayed-delivery replies
- inconsistent tone and reassurance across staff
- risk of overpromising based on incomplete tracking information
- slower response times during periods of high complaint volume

---

## Automation Potential

**Level:** High

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | Very high — delayed-delivery enquiries are frequent in online retail |
| Data availability | High — customer email and tracking details are usually available |
| Human judgment needed | Moderate — staff still need to verify tracking and decide if escalation is needed |
| Integration possibility | High — can be integrated with CRM and courier-tracking workflows |
| Estimated time saving | ~75–85% compared with fully manual drafting of delivery updates |

**Human-in-the-loop role:** Support staff should verify the tracking details and ensure the message does not promise unsupported delivery dates, compensation, or outcomes before sending it to the customer.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Draft promises a delivery date or update that is not confirmed | High | Prompt explicitly says not to promise dates or courier updates unless clearly supported |
| Model invents tracking information | High | Prompt requires the response to use only the delivery information provided |
| Draft sounds too generic and does not reassure the customer properly | Medium | Empathy and tone instructions included; human review before sending |
| Staff use outdated tracking information in the prompt | Medium | Delivery details should be checked before prompt use |

**Overall risk rating:** MEDIUM — strong support for routine delivery enquiries, but replies should still be reviewed before sending.

---

## Version History

### v1.0 — Initial draft
**Date:** 13 March 2025  
**Prompt:** `Write a reply to this customer about their delayed order: [EMAIL_TEXT]`  
**Output:** The model produced a polite response, but sometimes guessed what had happened to the parcel or implied that delivery would happen soon.  
**Observed effect:** The draft was too risky because it could create false expectations.  
**Lesson learned:** Delivery-response prompts must be grounded in verified delivery data, not assumptions.

---

### v1.1 — Added delivery information input
**Date:** 17 March 2025  
**Change:** Added delivery details and instructed the model to explain what is currently known.  
**Output:** The draft became more relevant, but still sometimes used language that sounded too confident about likely outcomes.  
**Observed effect:** Accuracy improved, but the prompt still needed stronger controls around promises and unsupported updates.  
**Lesson learned:** When customer frustration is high, the prompt must balance empathy with factual restraint.

---

### v1.2 — Added stronger factual limits and escalation-safe wording ✅ Current
**Date:** 22 March 2025  
**Change:** Added instructions not to promise compensation, refunds, or delivery dates unless clearly supported, and to state that the team will investigate if the status is unclear.  
**Output:** The response became more controlled, realistic, and easier for support staff to approve.  
**Observed effect:** The draft now provides a better balance between reassurance and factual accuracy.  
**Lesson learned:** Delivery prompts perform better when they explicitly separate confirmed information from uncertain status.

---

## A/B Test Results

**Test date:** 23 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Accuracy of delivery messaging | 2/5 | 4.5/5 |
| Tone appropriateness | 3/5 | 4.5/5 |
| Risk control | 2/5 | 4.5/5 |
| Overall usefulness | 2.5/5 | 4.5/5 |

---

## Related Prompts

- **Previous in chain:** [P04 — First response draft](P04-first-response-draft.md)
- **Alternative related prompt:** [P05 — Refund and return response](P05-refund-return-response.md)
- **Next possible escalation:** [P08 — Escalation summary](../03-escalation-insights/P08-escalation-summary.md)
- **Parent section:** [02 — Response Drafting Workflow](README.md)
- **Library index:** [Main README](../README.md)
