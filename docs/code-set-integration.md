# Code Set Integration Notes

MedCodeAI is designed to support all major medical code systems, but the data source and licensing rules are different for each code family.

## Supported Catalog Systems

- ICD-10-CM diagnosis codes
- ICD-10-PCS inpatient procedure codes
- HCPCS Level II codes
- CPT codes, after licensing

## Current Data Sources

- CMS ICD-10 files: https://www.cms.gov/medicare/coding-billing/icd-10-codes
- CMS HCPCS quarterly update files: https://www.cms.gov/medicare/coding-billing/healthcare-common-procedure-system/quarterly-update
- AMA CPT licensing: https://www.ama-assn.org/practice-management/cpt/cpt-licensing-frequently-asked-questions-faqs

## Import Format

The browser app accepts JSON arrays or CSV files. Each record should normalize to:

```json
{
  "system": "ICD-10-CM",
  "code": "E11.9",
  "description": "Type 2 diabetes mellitus without complications",
  "terms": ["type 2 diabetes", "diabetes mellitus", "a1c"],
  "confidence": 80,
  "source": "CMS FY 2026 ICD-10-CM"
}
```

CSV headers can use `system`, `code`, `description`, `terms`, `confidence`, and `source`. Separate multiple terms with `|` or `;`.

## Production Requirements

- Refresh public code sets on their official update schedule.
- Keep CPT content behind a license-controlled ingestion path.
- Track source version, effective date, and import date for every record.
- Add payer policy, NCCI edits, LCD/NCD rules, MUEs, and modifier logic before real billing use.
- Store PHI only in HIPAA-ready systems with access controls, audit logs, retention policy, and signed business agreements.
