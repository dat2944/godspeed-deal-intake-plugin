# SK-01 — Document Ingestion & Readability Check

**Skill ID:** SK-01
**Workflow Steps:** Step 1
**Trigger:** Analyst uploads a PDF and sends trigger prompt

---

## Purpose

Receive the uploaded PDF and confirm it is machine-readable before any extraction begins. This is the gate that prevents the agent from attempting to process an unusable document.

---

## Behavior

1. Confirm a file is attached to the conversation
2. Confirm the file type is PDF
3. Confirm the document contains extractable text content

---

## Governing Rules

- Accept PDF only — no Word, Excel, or image files without a PDF wrapper
- If no file is attached: halt and notify analyst
- If file is not a PDF: halt, state the file type received, and request a PDF
- If the PDF contains zero extractable text (scanned image only): halt and notify analyst — do not attempt OCR
- Do not proceed to SK-02 until this check passes

---

## Failure Responses

| Condition | Response to Analyst |
|---|---|
| No file attached | "No document detected. Please attach a PDF deal document and resubmit." |
| Wrong file type | "The uploaded file appears to be a [file type]. Please attach a PDF and resubmit." |
| Scanned image PDF | "This document appears to be a scanned image. Text extraction is not possible. Please provide a text-based PDF." |

---

## Notes

- This skill is a hard gate — no downstream steps run until SK-01 passes
- Scanned documents must be handled manually by the analyst outside of this workflow
- Future versions may support OCR via a separate pre-processing step