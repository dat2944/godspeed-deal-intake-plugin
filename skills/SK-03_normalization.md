# SK-03 — Data Normalization

**Skill ID:** SK-03
**Workflow Steps:** Step 3
**Trigger:** SK-02 complete — raw extracted data set ready

---

## Purpose

Transform raw extracted data into standardized formats required for Affinity field entry and accurate deal assessment. Ensures all data written to Affinity is clean, consistent, and correctly formatted.

---

## Behavior

1. Apply normalization rules to all extracted financial figures
2. Compute EBITDA Margin if not stated in document
3. Compute Leverage if both Net Debt and LTM EBITDA are available
4. Normalize location to standard format
5. Flag any value that cannot be confidently normalized

---

## Normalization Rules

**LTM Revenue / LTM EBITDA**
- Convert to numeric USD millions
- Strip currency symbols and text
- Examples: "$45M" → 45, "$45,000,000" → 45
- If figures are in non-USD currency: flag for analyst review — do not convert

**EBITDA Margin**
- Extract directly from document if stated
- If not stated: compute as (LTM EBITDA / LTM Revenue) × 100
- If either value is Not Found: record as Not Calculated
- Note: EBITDA Margin is not written to any Affinity field — displayed in confirmation report only

**Net Debt**
- Convert to numeric USD millions using same rules as Revenue / EBITDA
- If non-USD: flag for analyst review

**Leverage**
- Affinity calculates automatically from Net Debt and LTM EBITDA once both fields are written
- Do not compute or write Leverage to any Affinity field
- Display computed value in confirmation report only (e.g., 3.2x)

**Location**
- Normalize to "City, State, Country" format
- Examples: "Atlanta-based" → "Atlanta, GA, USA"
- Partial locations accepted but flagged

**Financial Period**
- Every Revenue and EBITDA figure must include period context (e.g., FY2022A, LTM 2022)
- If period is absent: flag the figure and record period as Not Found

---

## Governing Rules

- Never guess or infer a normalized value — flag and move on
- Never convert non-USD currency — flag for analyst review only
- Leverage is never written to Affinity — it is a computed display value only
- EBITDA Margin is never written to Affinity — display only in confirmation report

---

## Notes

- All flagged values are carried forward and listed in the confirmation report data gaps section
- Normalization failures do not halt the workflow unless Company Name is missing