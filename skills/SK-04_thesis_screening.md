# SK-04 — Thesis Screening

**Skill ID:** SK-04
**Workflow Steps:** Step 3 (screening portion)
**Trigger:** SK-03 complete — normalized data set ready

---

## Purpose

Apply Godspeed Capital Partners' investment criteria to the normalized deal data and produce a thesis fit rating. This gives the analyst an immediate signal on whether the opportunity warrants further attention.

---

## Behavior

1. Apply each investment criterion to the normalized data set
2. Rate each criterion individually: Met / Partial / Not Met / Unknown
3. Compute overall thesis fit rating based on individual assessments
4. Flag criteria that cannot be assessed due to missing data

---

## Investment Criteria

| Criterion | Target | Met | Partial | Not Met | Unknown |
|---|---|---|---|---|---|
| LTM Revenue | Between $10M and $200M | In range | Slightly outside range | Below $10M or above $200M | Not found |
| EBITDA Margin | Greater than 10% | >10% | 5%–10% | <5% | Not calculable |
| Profitability | Profitable or clear path | Currently profitable | Clear path documented | Not profitable, no path | Insufficient data |
| Market Position | Defensible position | Clearly defensible | Some differentiation | No evidence | Insufficient data |
| Revenue Quality | Recurring or contracted | Majority recurring | Mixed recurring/transactional | Primarily transactional | Not described |
| Geography | U.S. or North America | U.S./North American | Primarily international with U.S. presence | No U.S. presence | Not found |

---

## Overall Thesis Fit Rating

| Rating | Condition |
|---|---|
| Strong Fit | 4 or more criteria rated Met |
| Possible Fit | 2 to 3 criteria rated Met or Partial |
| Does Not Fit | Fewer than 2 criteria rated Met |
| Insufficient Data | More than 3 criteria are Unknown |

---

## Governing Rules

- Never rate a criterion Met without supporting data in the document
- If a criterion cannot be assessed due to missing data: always rate Unknown — never assume
- Insufficient Data rating does not mean the deal is declined — analyst makes final determination
- Does Not Fit rating does not auto-decline the opportunity — surface to analyst for review

---

## Notes

- Thesis screening is advisory only — final decision always rests with the analyst
- All Unknown criteria are listed in the data gaps section of the confirmation report
- Criteria thresholds are defined in config/investment_criteria.json
- If Godspeed updates their criteria, both this file and the system prompt must be updated together