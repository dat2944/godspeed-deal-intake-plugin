# SK-09 — Confirmation Report

**Skill ID:** SK-09
**Workflow Steps:** Step 6
**Trigger:** All prior steps complete or on any Critical failure

---

## Purpose

Deliver a structured confirmation report to the analyst in the Claude chat window at the conclusion of every workflow run. This is the primary output the analyst receives and acts on. It provides full auditability of every action taken during the workflow.

---

## Behavior

1. Compile outcomes of all workflow steps
2. List all Affinity records created or updated with IDs
3. Report fields written vs. fields skipped or rejected
4. Surface all data gaps requiring analyst follow-up
5. Deliver the full deal intake summary
6. Provide a recommended next step

---

## Confirmation Report Template

---

**DEAL INTAKE CONFIRMATION REPORT**
**Company:** [Company Name]
**Run Status:** Complete / Partial / Failed

**Records Created / Updated**

| Record Type | Action | Affinity ID | Name |
|---|---|---|---|
| Company | Created / Updated | [ID] | [Name] |

**Fields Written:** X of 8 fields successfully written

**Failed Actions**
- (list any failed MCP calls with error detail and recommended
  remediation — if none, write "None")

**Deal Intake Summary**

| Field | Value |
|---|---|
| Industry | |
| Location | |
| Year Founded | |
| Employees | |
| LTM Revenue | $XM (FY20XXA) |
| LTM EBITDA | $XM (Margin: X% of Net Revenue) |
| Net Debt | $XM |
| Leverage | Xx (calculated by Affinity) |
| Description | |

**People / Team**

| Name | Title | Email | Phone |
|---|---|---|---|
| | | | |

**Data Gaps Requiring Analyst Follow-Up**
- (prioritized list of Not Found fields and flagged issues — if none, write "None")

**Recommended Next Step:** Pass to IC / Request More Info / Analyst Review Required

---

## Run Status Definitions

| Status | Definition |
|---|---|
| Complete | All workflow steps executed successfully — all fields written — no Critical errors |
| Partial | One or more Warning level exceptions occurred — workflow completed with noted gaps |
| Failed | One or more Critical errors halted the workflow — CRM writes may be incomplete |

---

## Governing Rules

- Confirmation report is always delivered regardless of run status
- Even on Critical failure the analyst receives a report explaining exactly what happened
- Never silently continue past a failure — always surface errors with specific detail
- Report must include every Affinity record ID created or updated during the run
- All data gaps must be listed and prioritized by impact to deal assessment
- Recommended next step must always be included

---

## Notes

- This is the only output the analyst receives — no emails, no Slack, no CRM Notes in v1.0
- The analyst uses this report to verify Affinity records and determine next steps
- All output stays within the Claude chat window