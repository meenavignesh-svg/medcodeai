# MedCodeAI

AI-assisted CPC medical coding workbench prototype.

This static browser app supports clinical note review, draft code suggestions, evidence signals, audit checks, and a searchable code catalog. The catalog can be expanded by importing JSON or CSV records with:

```text
system,code,description,terms,confidence,source
```

It is coder-assist software only and requires human validation against current official coding guidance, payer policy, and source documentation.

Open `index.html` in a browser to try it.

## Code Set Integration

- ICD-10-CM and ICD-10-PCS: load current CMS public files into the catalog.
- HCPCS Level II: load current CMS public quarterly update files into the catalog.
- CPT: do not ship full CPT content without an AMA license. Use licensed CPT data from AMA or an authorized distributor before production use.

See `docs/code-set-integration.md` for source and compliance notes.
