
# Prompt Library — Retail Customer Support Workflow

> **Assessment 1 | Generative AI for Business**  
> Student: Monythyda Chea (22347997) 
> Business Field: Online Retail Customer Support  
> Topic: **AI Prompt Library for Automating Customer Email Support in an Online Retail Business**  
> Model tested on: [ChatGPT / GPT-4o]  
> Last updated: [March 31,2026]

---

## What This Library Does

This prompt library supports workflow automation in **online retail customer support**. It is designed for a **mid-sized online retail business** that receives a high volume of customer emails relating to delivery issues, refunds, returns, damaged items, wrong orders, product quality concerns, and general complaints.

The library contains **10 documented, tested, and iterated prompts** that improve the speed, consistency, and quality of customer email handling. These prompts are organised around the key stages of the workflow: **intake and triage, response drafting, and escalation and service insights**.

Each prompt entry includes:
- the exact prompt text
- the workflow task it supports
- the problem being solved
- automation potential
- risks and limitations
- version history showing iterative improvement

---

## Business Problem

Customer support teams in online retail often handle repetitive email enquiries manually. This creates several operational problems:

- slow response times during peak periods
- inconsistent tone and quality across agents
- misclassification of issues
- delays in escalating serious complaints
- repetitive drafting work for common issues such as refunds and delivery delays

These problems affect both **operational efficiency** and **customer experience**. A prompt library can help reduce manual effort while keeping human oversight in place for sensitive or high-risk cases.

---

## Folder Structure

```text
prompt-library/
│
├── README.md
│
├── 01-intake-triage/
│   ├── README.md
│   ├── P01-email-classification.md
│   ├── P02-urgency-sentiment.md
│   └── P03-missing-information-checker.md
│
├── 02-response-drafting/
│   ├── README.md
│   ├── P04-first-response-draft.md
│   ├── P05-refund-return-response.md
│   ├── P06-delivery-delay-response.md
│   └── P07-complaint-recovery-response.md
│
├── 03-escalation-insights/
│   ├── README.md
│   ├── P08-escalation-summary.md
│   ├── P09-faq-answer-generator.md
│   └── P10-weekly-support-summary.md
│
└── README.md
```

--- 

## Library Summary Table

| ID | Prompt Name | Workflow | Automation Level | Risk Level | Status |
|----|-------------|----------|------------------|------------|--------|
| P01 | Email classification | Intake and triage | Very High | Medium | ✅ Tested |
| P02 | Urgency and sentiment detection | Intake and triage | High | Medium | ✅ Tested |
| P03 | Missing information checker | Intake and triage | High | Low | ✅ Tested |
| P04 | First response email draft | Response drafting | High | Medium | ✅ Tested |
| P05 | Refund and return response | Response drafting | High | Medium | ✅ Tested |
| P06 | Delivery delay response | Response drafting | High | Medium | ✅ Tested |
| P07 | Complaint recovery response | Response drafting | Medium | High | ✅ Tested |
| P08 | Escalation summary | Escalation and review | Medium | High | ✅ Tested |
| P09 | FAQ answer generator | Knowledge support | Medium | Low | ✅ Tested |
| P10 | Weekly support insights summary | Reporting and improvement | Medium | Medium | ✅ Tested |

**Automation levels:** Very High / High / Medium / Low  
**Risk levels:** High (always needs human review) / Medium (human review recommended) / Low (limited oversight needed)

---

## Prompt Chaining Map

Some prompts in this library are designed to work together as a connected workflow rather than as standalone prompts.

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
P04 · First response draft
        │
        ├── If refund/return issue → P05
        ├── If delivery issue → P06
        ├── If complaint or service recovery case → P07
        │
        ▼
P08 · Escalation summary (if high urgency / legal risk / unresolved)
        │
        ▼
P09 · FAQ answer generator for repeated enquiries
        │
        ▼
P10 · Weekly support insights summary for management
```

This workflow reflects a realistic customer support process in which incoming emails are first assessed, then responded to, and finally used to support escalation handling and continuous improvement.

---

## Prompting Strategies Used

This library applies several prompting strategies to improve output quality and reliability.

### Role Prompting
Role prompting is used in response-drafting prompts so the model writes as a customer support specialist, service recovery agent, or team lead. This helps create outputs with a more professional and consistent tone.

### Structured Outputs
Structured outputs are used in prompts such as classification, escalation, and summary generation. This makes outputs easier to review, compare, and potentially integrate into support systems or CRM workflows.

### Constraints and Exclusions
Constraints and exclusions are included across the prompt library to reduce hallucination, prevent irrelevant information from being added, and ensure outputs remain aligned with customer service policies and business needs.

### Prompt Chaining
Prompt chaining is used to connect earlier workflow steps to later ones. For example, a classification output can support a drafting prompt, and a serious complaint can trigger an escalation summary prompt.

### Tone Control
Tone control is especially important in customer-facing prompts. The library uses instructions such as professional, empathetic, concise, and brand-appropriate to support a more consistent customer experience.

### Summarisation
Summarisation is used in escalation and weekly reporting prompts to improve management visibility and help identify recurring service problems.

---

## Iteration Evidence

Iterative improvement is a core part of this library. Each prompt file contains a version history that documents how the prompt developed over time.

At minimum, each prompt is designed to show:

- **v1.0** initial draft
- **v1.1** revised version
- **v1.2** improved current version

Each version history explains:

- what changed
- what effect was observed in the output
- what lesson was learned from testing

This repository structure and version documentation are intended to provide clear evidence of refinement rather than presenting a single final prompt with no development history.

---

## Expected Business Value

This prompt library is expected to create value in several ways.

### Efficiency
The library can reduce the time agents spend reading, classifying, and drafting responses to common customer enquiries.

### Consistency
The prompts support a more standard tone, format, and workflow across the support team, reducing differences in service quality between agents.

### Scalability
The library makes it easier for the business to handle larger enquiry volumes during busy periods without proportionally increasing manual workload.

### Management Visibility
Escalation summaries and weekly insights can help managers identify recurring complaint patterns, service bottlenecks, and improvement opportunities.

In business terms, the library has the potential to support faster response times, more reliable service quality, better escalation handling, and stronger continuous improvement across the customer support function.

---

## Risks and Responsible Use

Although this library creates clear automation opportunities, it also involves important risks and limitations.

The main risks include:

- hallucinated or inaccurate responses
- misclassification of customer issues
- incorrect urgency detection
- privacy concerns if sensitive customer data is entered into unsecured tools
- tone mismatch in emotionally sensitive complaints
- over-reliance on AI in cases that require human judgement

To reduce these risks, this library assumes several controls are in place:

- AI outputs should be treated as **drafts or decision-support tools**, not final decisions
- human review should remain mandatory for customer-facing replies, escalations, and sensitive complaints
- prompts should use clear constraints and avoid unnecessary personal data wherever possible
- high-risk issues, including legal threats, discrimination claims, and serious service failures, should always be escalated to qualified staff

This means the library supports **responsible augmentation**, not uncontrolled automation.

---

## References

McKinsey & Company. (2023, June 14). The economic potential of generative AI: The next productivity frontier. https://www.mckinsey.com/capabilities/tech-and-ai/our-insights/the-economic-potential-of-generative-ai-the-next-productivity-frontier 

Microsoft. (2026, February 27). Prompt engineering techniques. Microsoft Learn. https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/prompt-engineering 

National Institute of Standards and Technology. (2023). Artificial Intelligence Risk Management Framework (AI RMF 1.0) (NIST AI 100-1). https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf 

National Institute of Standards and Technology. (2024). Artificial Intelligence Risk Management Framework: Generative artificial intelligence profile (NIST AI 600-1). https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf 
 
