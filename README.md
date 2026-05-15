# ISMS Templates

Official document templates for [isms.sh](https://isms.sh). 887 markdown documents across 11 standards.

## Available Templates

| Template | Standard | Docs | Description |
|----------|----------|------|-------------|
| `iso27001` | ISO/IEC 27001:2022 | 113 | Information security management |
| `nist-800-53` | NIST SP 800-53 Rev 5 | 152 | Security and privacy controls |
| `pci-dss` | PCI DSS v4.0.1 | 115 | Payment card data security |
| `soc2` | SOC 2 Type II | 98 | Service organization controls |
| `dora` | DORA | 77 | Digital operational resilience (EU) |
| `hipaa` | HIPAA Security Rule | 64 | Healthcare information security |
| `nist-csf` | NIST CSF 2.0 | 60 | Cybersecurity risk management |
| `iso42001` | ISO/IEC 42001:2023 | 56 | AI management |
| `iso9001` | ISO 9001:2015 | 54 | Quality management |
| `nis2` | NIS2 Directive | 54 | Network and information security (EU) |
| `iso14001` | ISO 14001:2015 | 44 | Environmental management |

## How Templates Work

Templates are scaffolded into an organization's git repository. After scaffolding, the org owns the content — templates are not referenced again at runtime.

```
isms init --template iso27001
# or via web UI: Admin → Templates → Add
```

## Template Structure

Each template is a directory of markdown files with YAML frontmatter:

```
iso27001/
├── meta.yaml                              # Template identity
├── clauses/
│   ├── .title                             # Folder display name ("Clauses")
│   ├── 04-context-of-the-organisation/
│   │   ├── .title                         # "Context of the Organisation"
│   │   ├── 4.01-external-and-internal-issues.md
│   │   ├── 4.02-needs-and-expectations.md
│   │   └── ...
│   └── ...
└── controls/
    ├── .title                             # "Controls"
    ├── a.05-organizational-controls/
    │   ├── .title                         # "Organizational Controls"
    │   ├── a.5.01-policies-for-information-security.md
    │   └── ...
    └── ...
```

### meta.yaml

Required. Identifies the template:

```yaml
id: "iso27001"
name: "ISO/IEC 27001:2022"
description: "Information security management based on ISO/IEC 27001:2022"
version: "1.0"
maintainer: "isms.sh <team@isms.sh>"
```

### Document Files (*.md)

Each markdown file is a document with YAML frontmatter:

```yaml
---
document_id: "iso27001-a-8-2"
title: "A.8.2 Privileged Access Rights"
status: "draft"
---

# Privileged access rights

Restrict and manage the allocation and use of privileged access rights...
```

- `document_id` — unique, lowercase, hyphenated. Used for linking and URL routing.
- `title` — human-readable document name.
- `status` — starts as `draft`. Managed by the review workflow.

### .title Files

Optional. Provide display names for folders in the web UI:

```
Controls
```

Without a `.title` file, the folder's directory name is shown.

### Naming Conventions

- **Directories**: zero-padded for sorting (`04-context-of-the-organisation`)
- **Files**: section number + slug (`4.01-external-and-internal-issues.md`)
- **Document IDs**: template prefix + section (`iso27001-4-1`, `iso27001-a-5-1`)

## Creating Your Own Template

1. Create a directory with your template ID (lowercase, no spaces)
2. Add `meta.yaml` with id, name, description, version, maintainer
3. Create subdirectories for document groups
4. Add `.title` files for display names
5. Add markdown files with `document_id`, `title`, `status` frontmatter
6. Set `ISMS_TEMPLATE_PATH` to the parent directory

The platform discovers templates automatically — any directory with a valid `meta.yaml` becomes available.

## Contributing

Contributions welcome. To add or improve a template:

1. Fork this repository
2. Add or modify template files
3. Ensure all documents have valid `document_id` and `title` frontmatter
4. Bump the `version` in `meta.yaml`
5. Submit a pull request

## License

Apache License 2.0 — see [LICENSE](LICENSE).

Copyright 2026 [UniDoc ehf.](https://unidoc.io) — [isms.sh](https://isms.sh)
