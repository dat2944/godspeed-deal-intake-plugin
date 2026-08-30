# SK-05 — Deal Summary Generation

**Skill ID:** SK-05
**Workflow Steps:** Step 4
**Trigger:** SK-04 complete — normalized and screened data set ready

---

## Purpose

Produce a structured, human-readable deal intake summary that captures all key data points in a consistent format. The summary is delivered to the analyst in the Claude chat window as part of the confirmation report.

---

## Behavior

1. Compile all extracted and normalized data into the defined summary template
2. Compute and include EBITDA Margin and Leverage where data is available
3. List all People / Team members in structured text format
4. List all data gaps clearly
5. Provide a recommended next step based on available data

---

## Summary Template

**[COMPANY NAME] — Deal Intake Summary**

| Field | Value |
|---|---|
| Industry | |
| Location | |
| Year Founded | |
| Employees | |
| LTM Revenue | $XM (FY20XXA) |
| LTM EBITDA | $XM (Margin: X% of Net Revenue) |
| Net Debt | $XM |
| Leverage | Xx (display only — calculated by Affinity) |
| Description | |

**People / Team**

| Name | Title | Email | Phone |
|---|---|---|---|
| | | | |

**Data Gaps**
- (list every field marked Not Found or flagged during normalization)

**Recommended Next Step**
- Pass to IC / Request More Info / Analyst Review Required

---

## Governing Rules

- Always follow the defined summary template exactly — no freeform formatting
- Clearly separate confirmed data from flagged or uncertain data
- Always include a Recommended Next Step
- Summary must be self-contained — readable without reference to the source PDF
- Never include fabricated or inferred data in the summary
- EBITDA Margin and Leverage are display only — note they are not written to Affinity

---

## Recommended Next Step Logic

| Condition | Recommended Next Step |
|---|---|
| Strong Fit | Pass to IC |
| Possible Fit | Request More Info or Analyst Review Required |
| Does Not Fit | Analyst Review Required |
| Insufficient Data | Request More Info |

---

## Notes

- The deal summary is delivered as part of the Step 6 confirmation report in Claude chat
- No notes are written to Affinity CRM — all output stays in the Claude chat window
- This summary becomes the primary reference for the analyst after intake is complete