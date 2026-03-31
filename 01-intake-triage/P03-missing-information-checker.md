# P03 · Missing information checker

**Section:** 01 — Intake and Triage  
**Workflow step:** Step 3 of 10  
**Current version:** v1.2  
**Status:** ✅ Tested  
**Last updated:** March 2025

---

## Prompt Text (v1.2 — current)

```text
You are a customer support assistant for an online retail business.

Review the customer email below and identify what important information is missing that would help a support agent resolve the issue faster.

Possible missing information may include:
- order number
- product name
- date of purchase
- tracking number
- photos of damage
- description of the problem
- preferred resolution

Customer email:
[EMAIL_TEXT]

Rules:
- Only list information that is genuinely missing and relevant to the issue described
- Do not ask for information the customer has already provided
- Do not invent facts
- If the email already contains enough information for the next step, write "No major information missing"

Respond in this format:

Missing information:
- [item 1]
- [item 2]

Reason:
[one short sentence explaining why this information would help]
```

**Placeholders to fill:**

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[EMAIL_TEXT]` | Customer email from support inbox or web form | "Hi, my parcel arrived today but the shoes inside were the wrong size. Can you help?" |

---

## Intended Workflow or Task

This prompt supports the **third step of the intake and triage workflow**. After the business understands the type of issue and the likely urgency, the next step is to check whether the customer has provided enough information for the support team to act efficiently.

- **Trigger:** Customer email has already been classified and assessed for urgency
- **Actor:** Support agent or automated support workflow
- **Timing:** Before a reply is drafted
- **Next step:** Output helps the agent decide whether to ask for more details or move directly into response drafting

```text
Customer email received → P01 classifies issue → P02 checks urgency
                                           → [P03 RUNS]
                                           → missing information identified
                                           → response drafted or follow-up requested
```

---

## Problem Being Solved

Customer emails often describe a problem, but they do not always include the details needed to resolve it quickly. For example, a customer may complain about a delayed parcel without giving an order number, or may report a damaged item without including the product name or photos. This creates extra back-and-forth and slows down issue resolution.

When support staff manually check every email for missing details, the process becomes repetitive and inconsistent. Some agents may overlook gaps, while others may ask for unnecessary information. This adds delay to the workflow and reduces customer satisfaction.

**Pain points addressed:**
- repeated back-and-forth caused by missing order details
- wasted time from agents manually checking routine information gaps
- inconsistent requests for follow-up information
- slower response and resolution times

---

## Automation Potential

**Level:** High

| Dimension | Assessment |
|-----------|------------|
| Repetitiveness | High — many support emails need a basic completeness check |
| Data availability | High — the email content is already available in the workflow |
| Human judgment needed | Low to moderate — support agents still decide what is actually necessary in edge cases |
| Integration possibility | Medium to high — output can feed a response prompt or checklist before reply drafting |
| Estimated time saving | ~70–80% for the completeness-check step compared with fully manual review |

**Human-in-the-loop role:** Agents should review whether the suggested missing information is truly needed before asking the customer for more details. This is especially important to avoid unnecessary questions that may frustrate the customer.

---

## Risks and Limitations

| Risk | Level | Mitigation |
|------|-------|------------|
| Model asks for irrelevant details | Medium | Prompt explicitly says to list only information that is genuinely missing and relevant |
| Model misses a key detail needed for resolution | Medium | Agent reviews output before relying on it |
| Model repeats information already given by the customer | Medium | Prompt includes a rule not to ask for information already provided |
| Overuse creates unnecessary follow-up questions | Low | Human review ensures only useful follow-up requests are sent |

**Overall risk rating:** MEDIUM — useful for triage support, but outputs should be checked before contacting the customer for more information.

---

## Version History

### v1.0 — Initial draft
**Date:** 10 March 2025  
**Prompt:** `What information is missing from this customer email? [EMAIL_TEXT]`  
**Output:** The model sometimes listed too many possible details, including ones that were not necessary for the issue.  
**Observed effect:** Output was not focused enough and could lead to unnecessary follow-up questions.  
**Lesson learned:** The prompt needed clearer instructions about relevance and issue-specific missing information.

---

### v1.1 — Added examples of missing information
**Date:** 14 March 2025  
**Change:** Added examples such as order number, product name, tracking number, photos of damage, and preferred resolution.  
**Output:** The model became more practical, but still occasionally asked for information already mentioned in the email.  
**Observed effect:** Better usefulness, but some follow-up suggestions were repetitive.  
**Lesson learned:** The prompt needed an explicit rule not to ask for information already provided.

---

### v1.2 — Added relevance filter and fallback response ✅ Current
**Date:** 19 March 2025  
**Change:** Added rules to ask only for genuinely missing and relevant information, avoid repeating known details, and return "No major information missing" when appropriate.  
**Output:** The model now gives a more focused checklist that is easier for agents to use before drafting a response.  
**Observed effect:** Output became more practical and reduced the risk of unnecessary information requests.  
**Lesson learned:** AI is more useful in support workflows when prompts clearly distinguish between helpful missing details and optional extras.

---

## A/B Test Results

**Test date:** 20 March 2025 | **Evaluators:** 1 student tester / simulated support workflow

| Criteria | v1.0 score | v1.2 score |
|----------|------------|------------|
| Relevance of missing information | 2/5 | 4.5/5 |
| Avoids repeating existing details | 2/5 | 4/5 |
| Practical usefulness for agents | 2.5/5 | 4.5/5 |
| Overall usefulness | 2/5 | 4.5/5 |

---

## Related Prompts

- **Previous in chain:** [P02 — Urgency and sentiment detection](P02-urgency-sentiment.md)
- **Next in chain:** [P04 — First response draft](../02-response-drafting/P04-first-response-draft.md)
- **Parent section:** [01 — Intake and Triage Workflow](README.md)
- **Library index:** [Main README](../README.md)
