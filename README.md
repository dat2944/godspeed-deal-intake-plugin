# godspeed-deal-intake-plugin

> AI-powered deal intake automation for Godspeed Capital Partners — Claude AI and Affinity CRM.

---

## What This Is

This repository contains the complete configuration, prompt engineering, and documentation for the **Godspeed Deal Intake Agent** — an AI-powered workflow that eliminates manual analyst effort when processing inbound investment opportunities.

When an analyst uploads a PDF deal document (teaser, CIM, pitch deck, or company overview) into Claude, the agent automatically:

1. Extracts all relevant company, financial, and transaction data
2. Validates and normalizes the extracted data
3. Screens the opportunity against Godspeed's investment thesis
4. Generates a structured deal intake summary
5. Creates or updates Company, Contact, and Opportunity records in Affinity CRM
6. Attaches deal notes and data gap logs to the Opportunity record
7. Delivers a full confirmation report to the analyst

---

## Repository Structure

godspeed-deal-intake-plugin/
│
├── README.md ← This file
├── prompt/
│ ├── system_prompt.md ← Production system prompt (main artifact)
│ └── system_prompt_changelog.md ← Version log of every prompt change
├── config/
│ ├── field_mapping.json ← Affinity field-{number} IDs mapped to field names
│ ├── investment_criteria.json ← Godspeed's investment thesis criteria and thresholds
│ └── pipeline_config.json ← Affinity list IDs, stage names, and stage IDs
├── skills/
│ ├── SK-01_document_ingestion.md
│ ├── SK-02_data_extraction.md
│ ├── SK-03_normalization.md
│ ├── SK-04_thesis_screening.md
│ ├── SK-05_deal_summary.md
│ ├── SK-06_duplicate_detection.md
│ ├── SK-07_record_writing.md
│ ├── SK-08_note_authoring.md
│ └── SK-09_confirmation_report.md
├── docs/
│ ├── Task_2.01_Plugin_Scope.docx
│ ├── Phase2_Plugin_Specification.docx
│ └── Phase1_MCP_Assessment.docx
├── testing/
│ ├── test_cases.md
│ ├── sample_documents/
│ └── test_results/
└── .github/
└── CHANGELOG.md
---

## How to Use the Plugin

### Prerequisites
- Access to Claude.ai (Pro, Team, or Enterprise plan)
- Affinity CRM account with MCP Server access enabled
- Affinity MCP Server connected in Claude.ai Settings → Integrations

### Analyst Workflow
1. Open a new Claude conversation
2. Copy the full contents of `prompt/system_prompt.md`
3. Paste the system prompt as your first message
4. Upload the PDF deal document
5. Type: **"Process this deal document."**
6. Claude executes the full workflow automatically
7. Review the confirmation report and verify Affinity records

---

## Configuration

### Affinity Field IDs
All custom field writes use confirmed `field-{number}` IDs specific to Godspeed's Affinity org instance. These are defined in `config/field_mapping.json`. Never reference fields by name — IDs are the only stable identifier.

### Investment Criteria
Godspeed's thesis screening criteria are defined in `config/investment_criteria.json`. Update this file and the system prompt together whenever criteria change.

### Pipeline Configuration
The Deal Pipeline list ID and stage definitions are in `config/pipeline_config.json`.

---

## Important Constraints

- **Never write Dealroom fields** — editing these breaks Dealroom sync
- **Never write the Leverage field** — calculated Smart Field, absent from MCP schema
- **Never use schema mutation tools** in production
- **Always search before create** — duplicate detection is mandatory
- **Always use field-{number} IDs** — never reference fields by name

---

## Version History

See `prompt/system_prompt_changelog.md` for prompt version history and `.github/CHANGELOG.md` for release notes.
