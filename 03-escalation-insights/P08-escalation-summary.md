# P08 · Escalation summary

**Section:** 03 — Escalation and Insights  
**Workflow step:** Step 8 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support team lead for an online retail business.

Create a concise escalation summary for a customer case that needs management or specialist review.

Customer issue details:
Issue category: [ISSUE_CATEGORY]
Urgency level: [URGENCY_LEVEL]
Customer sentiment: [SENTIMENT]
Customer email:
[EMAIL_TEXT]

Case notes:
[CASE_NOTES]

Instructions:
- Summarise the issue clearly and factually
- Identify why the case requires escalation
- Include only information provided in the email and case notes
- Do not invent facts, policy decisions, or outcomes
- Keep the summary between 120 and 180 words
- Use a professional internal business tone

Respond using this structure:

Escalation summary:
- Customer issue:
- Current status:
- Reason for escalation:
- Recommended next step:
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[ISSUE_CATEGORY]` | Output from P01 | General complaint |
| `[URGENCY_LEVEL]` | Output from P02 | High |
| `[SENTIMENT]` | Output from P02 | Angry |
| `[EMAIL_TEXT]` | Customer email from support inbox | "I have contacted your team twice and still have no solution..." |
| `[CASE_NOTES]` | Internal support notes | "Two prior contacts logged. No final resolution yet. Supervisor review requested." |

---

## Intended Workflow or Task

This prompt supports the **escalation stage of the customer support workflow**. When a case cannot be resolved through routine support handling, staff need a clear internal summary that can be passed to a supervisor, manager, or specialist team.

- **Trigger:** A customer case is marked for escalation due to urgency, unresolved status, or elevated risk
- **Actor:** Support agent or supervisor
- **Timing:** After triage and response review, when escalation is required
- **Next step:** Summary is reviewed internally and passed to the appropriate decision-maker or specialist function

```text
Customer issue reviewed → escalation needed → [P08 RUNS]
                                          → internal summary created
                                          → manager / specialist team reviews
```

---

## Problem Being Solved

When a support case needs escalation, staff often need to manually summarise the issue for a manager or another team. This is repetitive and can lead to inconsistent handovers. Important context may be missed, or the reason for escalation may not be clearly explained.

This causes delays because managers may need to go back and reread the original email thread before taking action. A structured escalation summary helps reduce that inefficiency and improves internal visibility.

**Pain points addressed:**
- inconsistent internal handover quality
- delays caused by unclear escalation notes
- repeated manual summarising of customer history
- poor visibility of why the case needs senior review

---

## Automation Potential

**Level:** Medium

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | Medium — escalations are less frequent than routine enquiries but still recurring |
| Data availability | High — relevant information is usually available from the email and case notes |
| Human judgment needed | High — escalation decisions still require human review |
| Integration possibility | Medium — can support CRM case summaries and internal handover notes |
| Estimated time saving | ~50–65% compared with manual internal case summarisation |

**Human-in-the-loop role:** A support lead or supervisor should review the escalation summary before using it for management action, especially in cases involving legal, safety, discrimination, or compensation issues.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Summary omits an important fact from the case | High | Human review required before escalation is actioned |
| Model invents reasons or outcomes not in the notes | High | Prompt explicitly says to use only information provided |
| Summary oversimplifies a complex complaint | Medium | Cases involving multiple issues should still be manually checked |
| Staff rely on summary without reading source context | Medium | Summary should support, not replace, review of the original case file |

**Overall risk rating:** HIGH — useful for drafting internal escalation notes, but should not be used without human review.

---

## Version History

### v1.0 — Initial draft
**Date:** 15 March 2025  
**Prompt:** `Summarise this complaint for escalation: [EMAIL_TEXT]`  
**Output:** The model produced a short summary, but it lacked clear structure and sometimes left out why the issue needed escalation.  
**Observed effect:** Managers would still need to read the full case to understand the handover.  
**Lesson learned:** Escalation summaries need a fixed internal structure.

---

### v1.1 — Added escalation structure
**Date:** 19 March 2025  
**Change:** Added required sections for issue, current status, and reason for escalation.  
**Output:** The summary became clearer, but sometimes included assumptions about what should happen next.  
**Observed effect:** Internal readability improved, but factual control was still weak.  
**Lesson learned:** Escalation prompts need stronger constraints against invented next steps.

---

### v1.2 — Added factual grounding and tighter internal format ✅ Current
**Date:** 24 March 2025  
**Change:** Added instruction to use only provided information and avoid inventing outcomes or decisions.  
**Output:** The summary became more reliable and easier to use in internal review.  
**Observed effect:** Handover quality improved and summaries were more consistent across test cases.  
**Lesson learned:** Internal business summaries still need strong grounding rules to remain trustworthy.

---

## A/B Test Results

**Test date:** 25 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Clarity of escalation reason | 2/5 | 4.5/5 |
| Structure and readability | 2.5/5 | 4.5/5 |
| Factual control | 2/5 | 4.5/5 |
| Overall usefulness | 2.5/5 | 4.5/5 |

---

## Related Prompts

- **Previous in chain:** [P07 — Complaint recovery response](../02-response-drafting/P07-complaint-recovery-response.md)
- **Parent section:** [03 — Escalation and Insights Workflow](README.md)
- **Library index:** [Main README](../README.md)
