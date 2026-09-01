# System Prompt Changelog
# Godspeed Deal Intake Agent
# Godspeed Capital Partners

---

## Version 1.3 — 2026-08-30
**Changed by:** IT Solutions Consultant

### Changes
- Clarified People / Team note in Step 2 — explicitly states no People data is written to Affinity in this workflow version
- All People data delivered to analyst in Claude chat confirmation report only

---
### Changes
- Added Step 4 — Screen Against Investment Thesis to workflow
- Updated investment criteria to confirmed Godspeed targets:
  - LTM Revenue: Under $200M
  - LTM EBITDA: Between $3M and $30M
  - Employees: Fewer than 500
  - HQ Location: United States
  - Ownership: Not already PE-backed
- Removed Market Position, Revenue Quality, and Profitability criteria — deferred to future version
- Renumbered all steps — Steps 4 through 6 shifted to Steps 5 through 7
- Added thesis screening results table to Deal Summary (Step 5) and Confirmation Report (Step 7)
- Added Leverage row to Confirmation Report summary table
- Fixed People / Team format to Name | Title | Email | Phone throughout
- Added EBITDA Margin to Governing Rules as display only — not written to Affinity
- Replaced closing placeholder line with correct version footer

---

## Version 1.1 — 2026-08-30
**Changed by:** IT Solutions Consultant

### Changes
- Removed Transaction Type and Deal Source fields from extraction and CRM entry
- Removed Opportunity record creation from v1.0 scope — deferred to future phase
- Removed Contact / Person record creation from v1.0 scope — deferred to v1.1
- Removed CRM Notes — all output delivered to analyst in Claude chat only
- Confirmed and embedded Affinity field IDs for LTM Revenue (field-5276952), LTM EBITDA (field-5276953), Net Debt (field-5276956)
- Confirmed affinity-data- slug IDs for Description, Industry, Location, Number of Employees, Year Founded
- Removed Adj. prefix — standardized to LTM EBITDA throughout
- Removed Leverage as computed field — Affinity calculates automatically from Net Debt and LTM EBITDA
- Simplified currency rule — flag non-USD for analyst review, no conversion logic
- Clarified EBITDA Margin as display only — not written to any Affinity field
- Moved financial period rule to Note format in Step 3
- Updated People / Team to Name | Title structured text format
- Added Governing Rules section

---

## Version 1.0 — 2026-08-25
**Changed by:** IT Solutions Consultant

### Changes
- Initial production system prompt created
- 6 workflow steps defined
- Full field extraction list established
- Affinity MCP tool call sequence defined
- Investment thesis screening criteria defined
- Deal summary template created
- Confirmation report template created
- Exception handling rules defined

---

*This changelog must be updated every time system_prompt.md is modified. Include the date, version number, who made the change, and what was changed.*