# 01 — Intake and Triage Workflow

**Business function:** Customer Support / Customer Experience  
**Trigger:** Customer email received through support inbox or web contact form  
**Prompts in this section:** P01, P02, P03

---

## Section Purpose

This section supports the **front-end assessment of incoming customer emails** in an online retail business. Before a support agent can respond, the business needs to identify what the customer is asking about, how urgent the issue is, and whether any key information is missing.

These prompts are designed to improve the speed, consistency, and accuracy of the intake stage. Instead of asking staff to manually read and sort every email from scratch, the prompts help structure the first stage of the workflow in a way that is faster and more scalable.

---

## Why This Section Matters

In online retail, customer support teams often receive large volumes of similar enquiries every day. These messages may relate to refunds, returns, delayed delivery, damaged products, wrong items, or general complaints. If these emails are not assessed properly at the start, the rest of the workflow becomes inefficient.

Common problems at this stage include:

- incorrect classification of the issue
- delayed identification of urgent complaints
- missing order details or customer information
- wasted time from agents manually checking routine issues
- inconsistent handling across different support staff

By improving intake and triage, the business can route cases more accurately, reduce avoidable delays, and prepare better-quality responses in the next workflow stage.

---

## Chain Diagram

```text
Customer email received
        │
        ▼
P01 · Email classification
        │
        ▼
P02 · Urgency and sentiment detection
        │
        ▼
P03 · Missing information checker
        │
        ▼
Output passed to response drafting workflow
```

---

## Human-in-the-Loop Points

| Step | Human action required |
|------|-----------------------|
| P01 output | Support agent or team lead checks that the issue category is appropriate before relying on it for routing |
| P02 output | High-urgency cases are reviewed by a supervisor or senior support staff member |
| P03 output | Agent confirms whether the missing information identified by the model is actually required before contacting the customer |

This means the prompts assist intake and triage decisions, but final judgement remains with human staff.

---

## Prompts

| File | Prompt | Status |
|------|--------|--------|
| [P01-email-classification.md](P01-email-classification.md) | Classifies the customer email into a single main issue type | ✅ Tested |
| [P02-urgency-sentiment.md](P02-urgency-sentiment.md) | Detects urgency level and customer sentiment | ✅ Tested |
| [P03-missing-information-checker.md](P03-missing-information-checker.md) | Identifies what information is missing before a reply is drafted | ✅ Tested |

---

## Expected Operational Value

This section is expected to create business value by improving the quality of the first stage of customer support handling.

Key expected benefits include:

- faster intake processing for incoming emails
- more accurate routing of issues to the correct response pathway
- earlier identification of high-risk or sensitive complaints
- less time wasted by agents chasing obvious missing details later in the process
- improved consistency across different team members and shifts

In practical terms, better triage supports faster downstream responses and a more efficient overall support workflow.

---

## Risk Notes

Although intake and triage tasks are highly repetitive, they still involve some important risks.

The main risks in this section include:

- misclassifying the customer’s real issue
- underestimating urgency in a serious complaint
- overestimating urgency and creating unnecessary escalations
- identifying the wrong missing information
- over-reliance on AI output without staff review

For this reason, outputs from this section should be treated as **workflow support tools**, not as final decisions. Human review remains important, especially for complaints involving strong emotion, repeated service failure, or potential legal risk.

---

## Related Workflow Sections

- **Next section:** [02 — Response Drafting Workflow](../02-response-drafting/README.md)
- **Library index:** [Main README](../README.md)
