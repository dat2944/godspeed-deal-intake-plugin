# SK-07 — Affinity Record Writing

**Skill ID:** SK-07
**Workflow Steps:** Step 6b
**Trigger:** SK-06 complete — duplicate check done, org ID captured or create path confirmed

---

## Purpose

Write all extracted and normalized company data to Affinity CRM using the confirmed MCP tool sequence and field IDs. This is the core CRM write operation of the workflow.

---

## Behavior

1. Determine path — create new record or update existing based on SK-06 outcome
2. Create or confirm Company record exists
3. Write all company fields in defined order using confirmed field IDs
4. Confirm each write before proceeding to the next
5. Stop and report if any write operation fails

---

## MCP Tool Call Sequence

### New Record Path
Call `create_organization`
- Parameters: name = Company Name, domain = Company Website

### Existing Record Path
Use captured org ID from SK-06 — skip create_organization

### Field Writes — call `upsert_entity_field_values` for each field

| Field | Field ID | Format |
|---|---|---|
| Description | `affinity-data-description` | Text |
| Industry | `affinity-data-industry` | Text |
| Location | `affinity-data-location` | Text — City, State, Country |
| Number of Employees | `affinity-data-number-of-employees` | Numeric |
| Year Founded | `affinity-data-year-founded` | Numeric |
| LTM Revenue | `field-5276952` | Numeric USD millions |
| LTM EBITDA | `field-5276953` | Numeric USD millions |
| Net Debt | `field-5276956` | Numeric USD millions |

---

## Fields Explicitly Excluded

| Field | Reason |
|---|---|
| Leverage | Calculated Smart Field — Affinity computes automatically — absent from MCP schema |
| EBITDA Margin | Display only — not written to any Affinity field |
| People / Team | Text output in confirmation report only — no Person records in v1.0 |
| Any dealroom- prefixed field | Writing breaks Dealroom sync — never write |

---

## Governing Rules

- Always use field-{number} IDs for custom fields — never reference by name
- Always use affinity-data- slug IDs for native enrichment fields — never use dealroom- versions
- Confirm each MCP write before proceeding to the next field
- If any write call returns a Critical error: stop all further MCP writes immediately and report to analyst
- If a single field write is rejected: log the rejection, continue writing remaining fields, include in confirmation report
- Never write to Dealroom fields — this breaks Dealroom sync and cannot be easily reversed
- Never use schema mutation tools (create_field, delete_field) in production

---

## Notes

- Write order follows the field table above — top to bottom
- Field rejections are Warning level — they do not halt the entire workflow
- All write outcomes (success or failure) are reported in the SK-09 confirmation report
- Person record creation is deferred to v1.1