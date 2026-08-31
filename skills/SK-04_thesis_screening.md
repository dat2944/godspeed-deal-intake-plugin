# SK-04 — Thesis Screening

**Skill ID:** SK-04
**Workflow Steps:** Step 4
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
| LTM Revenue | Under $200M | Under $200M | Slightly above $200M | Well above $200M | Not found |
| LTM EBITDA | Between $3M and $30M | In range | Slightly outside range | Below $3M or above $30M | Not found |
| Employees | Fewer than 500 | Under 500 | 500–600 | Over 600 | Not found |
| HQ Location | United States | U.S.-based | U.S. presence but HQ elsewhere | No U.S. presence | Not found |
| Ownership | Not already PE-backed | Founder/family/independent owned | Partial PE involvement | Confirmed PE-backed | Not found |

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