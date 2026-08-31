# SK-06 — Duplicate Detection

**Skill ID:** SK-06
**Workflow Steps:** Step 6a
**Trigger:** SK-05 complete — deal summary generated, ready for CRM entry

---

## Purpose

Search Affinity CRM for existing Company records that match the extracted data before any record creation occurs. This prevents duplicate records from accumulating in Godspeed's Affinity instance.

---

## Behavior

1. Search Affinity for existing Company record by extracted Company Name
2. If match found: capture existing org ID and use update path
3. If no match found: proceed with create path
4. If search fails: flag as Warning, proceed with create path, note that duplicate check could not be completed

---

## MCP Tool Call

**Tool:** `search_companies_top_matches`
**Parameter:** name = extracted Company Name

---

## Match Handling

| Result | Action |
|---|---|
| Exact match found | Capture org ID — use update path for all field writes |
| Partial / low confidence match | Flag for analyst review — do not auto-merge — pause CRM entry pending analyst decision |
| No match found | Proceed with create path |
| Search call fails | Log Warning — proceed with create path — flag in confirmation report that duplicate check could not be completed |

---

## Governing Rules

- Duplicate check is mandatory — it is never skipped
- Always search before any create_organization call
- Never auto-merge records on a low confidence match — always surface to analyst
- If search fails, do not halt the workflow — proceed with create path and flag the gap
- Capture and store the org ID from any match found — it is required for all subsequent field write calls

---

## Notes

- This is the only duplicate check in v1.0 — Person record duplicate detection is deferred to v1.1
- Low confidence matches are flagged in the confirmation report for analyst resolution
- The org ID captured here is passed to SK-07 for all field write operations