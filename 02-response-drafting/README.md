# 02 — Response Drafting Workflow

**Business function:** Customer Support / Customer Experience  
**Trigger:** Customer email has been assessed and triaged through the intake workflow  
**Prompts in this section:** P04, P05, P06, P07

---

## Section Purpose

This section supports the **drafting of customer-facing email responses** in an online retail business. After an incoming email has been classified, checked for urgency, and reviewed for missing information, the next step is to prepare a response that is clear, professional, and aligned with company policy.

These prompts are designed to reduce the amount of time agents spend writing repetitive emails from scratch. They also help improve consistency in tone, structure, and service quality across the support team.

---

## Why This Section Matters

In online retail, many customer enquiries follow familiar patterns. Customers often ask for refunds, request returns, complain about delayed deliveries, or express dissatisfaction with damaged products or poor service. Although these responses are common, they still need to be handled carefully because the way a business communicates can directly affect customer trust and brand reputation.

Common problems at this stage include:

- inconsistent tone across different agents
- slow response drafting during busy periods
- replies that miss key policy information
- messages that sound too generic or unempathetic
- unnecessary time spent rewriting standard responses

By improving response drafting, the business can reply faster while maintaining a more consistent and professional customer experience.

---

## Chain Diagram

```text
Intake and triage workflow completed
        │
        ▼
P04 · First response draft
        │
        ├── If refund or return issue → P05 · Refund and return response
        ├── If delivery issue → P06 · Delivery delay response
        └── If complaint or service recovery case → P07 · Complaint recovery response
        │
        ▼
Reviewed by support agent
        │
        ▼
Sent to customer or escalated if needed
```

---

## Human-in-the-Loop Points

| Step | Human action required |
|------|-----------------------|
| P04 output | Support agent reviews the first draft to ensure it matches the customer’s issue and business policy |
| P05 output | Agent confirms refund or return eligibility before sending |
| P06 output | Agent checks tracking information or courier notes before sending the delivery response |
| P07 output | Supervisor or experienced support agent reviews sensitive complaint responses before they are sent |

These prompts support faster drafting, but the final message should still be checked by staff before it is sent to a customer.

---

## Prompts

| File | Prompt | Status |
|------|--------|--------|
| [P04-first-response-draft.md](P04-first-response-draft.md) | Drafts the first customer support reply after triage | 🔄 In progress |
| [P05-refund-return-response.md](P05-refund-return-response.md) | Drafts a response for refund and return enquiries | 🔄 In progress |
| [P06-delivery-delay-response.md](P06-delivery-delay-response.md) | Drafts a response for delayed delivery issues | 🔄 In progress |
| [P07-complaint-recovery-response.md](P07-complaint-recovery-response.md) | Drafts an empathetic response for complaints and service recovery cases | 🔄 In progress |

---

## Expected Operational Value

This section is expected to create business value by improving the speed and consistency of customer communication.

Key expected benefits include:

- shorter drafting time for common replies
- more consistent tone across the support team
- reduced rewriting of repetitive responses
- better alignment with refund, return, and delivery policies
- improved customer experience through clearer and more empathetic communication

In practical terms, stronger response drafting helps the business handle larger support volumes more efficiently without lowering service quality.

---

## Risk Notes

Although response drafting is highly suitable for AI assistance, there are still important risks in this workflow stage.

The main risks in this section include:

- inaccurate or misleading information in customer replies
- responses that do not match business policy
- tone mismatch in sensitive complaints
- overly generic responses that frustrate customers
- over-reliance on AI drafting without proper review

For this reason, outputs from this section should be treated as **draft emails**, not final approved messages. Human review is especially important where refund eligibility, delivery liability, customer compensation, or complaint recovery is involved.

---

## Related Workflow Sections

- **Previous section:** [01 — Intake and Triage Workflow](../01-intake-triage/README.md)
- **Next section:** [03 — Escalation and Insights Workflow](../03-escalation-insights/README.md)
- **Library index:** [Main README](../README.md)
