# SK-08 — Note Authoring

**Skill ID:** SK-08
**Workflow Steps:** Step 6 (post record write)
**Trigger:** SK-07 complete — Company record written successfully

---

## Purpose

This skill is retired in v1.0. Originally designed to write Notes to Affinity CRM records, this functionality was descoped in favor of delivering all output directly to the analyst in the Claude chat window via SK-09.

---

## Descope Decision

**Date:** 2026-08-30
**Reason:** Adding Notes to Affinity CRM creates unnecessary clutter in the CRM record. All deal intake output — including the deal summary, people data, and data gaps — is delivered directly to the analyst in the Claude chat confirmation report. This keeps Affinity clean and the analyst workflow contained within Claude.

---

## Future Consideration

If Godspeed determines in a future phase that CRM Notes are valuable for audit trail or team visibility purposes, this skill can be reactivated. Potential Note types for future consideration:

- Deal intake summary Note on Company record
- People / Team structured text Note on Company record
- Data gap log Note on Company record

---

## Current Status

- **v1.0:** Retired — no Notes written to Affinity
- **v1.1+:** To be evaluated based on client feedback after production use

---

## Notes

- No MCP tool calls are made by this skill in v1.0
- All output is handled by SK-09 confirmation report