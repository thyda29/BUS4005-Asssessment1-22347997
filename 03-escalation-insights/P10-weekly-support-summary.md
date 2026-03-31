# P10 · Weekly support insights summary

**Section:** 03 — Escalation and Insights  
**Workflow step:** Step 10 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support reporting analyst for an online retail business.

Review the weekly customer support notes below and generate a short internal summary for management.

Weekly support notes:
[WEEKLY_SUPPORT_NOTES]

Instructions:
- Summarise the main issue patterns observed during the week
- Identify any repeated operational problems
- Highlight any customer experience risks or escalation themes
- Suggest 2 or 3 practical follow-up actions
- Use only the information provided in the notes
- Do not invent statistics, causes, or business outcomes
- Keep the summary between 180 and 260 words
- Use a professional internal reporting tone

Respond using this structure:

Weekly support summary:
- Main issue patterns:
- Key risks:
- Recommended follow-up actions:
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[WEEKLY_SUPPORT_NOTES]` | Weekly case notes, complaint themes, or team observations | "High number of delivery-delay complaints this week..." |

---

## Intended Workflow or Task

This prompt supports the **management reporting and continuous improvement stage** of the workflow. Instead of treating customer emails only as individual cases, the business can also use support data to identify recurring patterns and service issues.

- **Trigger:** End of reporting period, such as weekly team review
- **Actor:** Support lead, reporting analyst, or operations manager
- **Timing:** Weekly or at the end of a defined support reporting cycle
- **Next step:** Summary is reviewed by management and used to inform service improvements, staffing decisions, or process changes

```text
Weekly support notes collected → [P10 RUNS]
                             → internal summary created
                             → management reviews patterns and actions
```

---

## Problem Being Solved

Customer support teams often collect useful operational insights, but these are not always turned into clear management summaries. Team leads may need to manually read many case notes to identify patterns such as repeated delivery delays, packaging complaints, or refund confusion.

This takes time and may lead to missed insights. Without structured reporting, recurring customer pain points may remain hidden, and management may not act quickly enough on developing issues.

**Pain points addressed:**
- time spent manually reviewing support notes
- poor visibility of recurring issue patterns
- inconsistent reporting quality across team leads
- missed opportunities for service improvement

---

## Automation Potential

**Level:** Medium

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | Medium — reporting is periodic rather than per case |
| Data availability | Medium to high — depends on the quality of weekly support notes |
| Human judgment needed | High — management interpretation and decision-making remain essential |
| Integration possibility | Medium — can support internal dashboards, reporting packs, or weekly review documents |
| Estimated time saving | ~50–70% compared with manual summary drafting |

**Human-in-the-loop role:** A support lead or manager should review the summary before using it in decision-making, especially to confirm that patterns and follow-up actions are genuinely supported by the source notes.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Summary overstates patterns that are weakly supported | High | Prompt explicitly forbids inventing statistics or unsupported trends |
| Recommended actions are too generic or not realistic | Medium | Human review required before management use |
| Incomplete source notes lead to weak reporting | Medium | Use the prompt only when weekly notes are reasonably complete |
| Managers rely on the summary without checking the source data | Medium | Treat output as a reporting draft, not a final analytical conclusion |

**Overall risk rating:** MEDIUM — useful for first-draft reporting, but not a substitute for managerial judgement.

---

## Version History

### v1.0 — Initial draft
**Date:** 17 March 2025  
**Prompt:** `Summarise this week’s customer support issues: [WEEKLY_SUPPORT_NOTES]`  
**Output:** The model produced a broad summary, but it mixed observations with assumptions and did not clearly separate risks from actions.  
**Observed effect:** The report sounded plausible but was not structured enough for management use.  
**Lesson learned:** Reporting prompts need explicit output sections and tighter factual limits.

---

### v1.1 — Added reporting structure
**Date:** 21 March 2025  
**Change:** Added sections for issue patterns, risks, and follow-up actions.  
**Output:** The summary became more useful, but suggested actions were sometimes generic or too broad.  
**Observed effect:** Readability improved, but the management value of the output was still uneven.  
**Lesson learned:** Reporting prompts need stronger control over what can be inferred from source notes.

---

### v1.2 — Added factual limits and practical action guidance ✅ Current
**Date:** 26 March 2025  
**Change:** Added instruction not to invent statistics, causes, or outcomes, and limited the action recommendations to practical follow-up items.  
**Output:** The summary became more balanced, more credible, and easier to use in weekly review discussions.  
**Observed effect:** Draft reporting time decreased and the summary structure became more decision-friendly.  
**Lesson learned:** AI can support management reporting well when prompts clearly separate observation from inference.

---

## A/B Test Results

**Test date:** 27 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Clarity of issue patterns | 2.5/5 | 4.5/5 |
| Usefulness for management review | 2/5 | 4.5/5 |
| Factual discipline | 2/5 | 4.5/5 |
| Overall usefulness | 2.5/5 | 4.5/5 |

---

## Related Prompts

- **Related downstream use:** [P09 — FAQ answer generator](P09-faq-answer-generator.md)
- **Parent section:** [03 — Escalation and Insights Workflow](README.md)
- **Library index:** [Main README](../README.md)
