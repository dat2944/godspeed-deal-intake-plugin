# SK-02 — Structured Data Extraction

**Skill ID:** SK-02
**Workflow Steps:** Step 2
**Trigger:** SK-01 passes — PDF confirmed readable

---

## Purpose

Read the entire document and extract all defined data fields into a structured format for normalization and CRM entry. This skill is the core extraction engine of the workflow.

---

## Behavior

1. Read the full document from start to finish — not just headings or executive summaries
2. Extract every defined field listed in Step 2 of the system prompt
3. For each field: record the extracted value or mark as Not Found
4. Capture all executives and contacts found anywhere in the document
5. Note the source context for all financial figures (period, currency)

---

## Fields Extracted

**Company Information**
- Company Name
- Company Website / Domain
- Description
- Industry
- Location
- Number of Employees
- Year Founded

**People / Team**
- All executives and key contacts found in document
- Format: Name | Title | Email | Phone

**Financial Information**
- LTM Revenue (most recent Actual FY only)
- LTM EBITDA (most recent Actual FY only)
- EBITDA Margin (extracted from document or computed)
- Net Debt

---

## Governing Rules

- Never infer, estimate, or fabricate field values
- Never use Estimate (E) figures for Revenue or EBITDA — Actual (A) only
- LTM and TTM are equivalent period labels — both are acceptable
- If only Estimate figures are available: extract but flag clearly as "Estimate — not confirmed Actual"
- Extract the most recently stated Actual figure when multiple years are present
- Record period context alongside every financial figure (e.g., FY2022A, LTM 2022)
- Extract all named executives and contacts regardless of where they appear in the document

---

## Notes

- Extraction is exhaustive — the agent reads the entire document
- People data is text only in this workflow version — no Person records created in Affinity
- All Not Found fields are carried forward and surfaced in the confirmation report