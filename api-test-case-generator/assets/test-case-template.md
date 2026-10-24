# API Test Scenarios — {service_or_feature}

**Contract/source:** {source_document}
**Scope:** {paths_and_methods}
**Draft status:** Requires human review

| ID | Endpoint | Category | Priority (proposed) | Preconditions | Test data / request | Steps | Expected result | Source | Review status |
|---|---|---|---|---|---|---|---|---|---|
| API-TC-001 | `{METHOD} {PATH}` | Positive | P1 | {preconditions} | {input} | 1. Prepare data; 2. Send request; 3. Inspect response | {documented behavior} | {document section} | READY_FOR_REVIEW |
| API-TC-002 | `{METHOD} {PATH}` | Negative | P2 | {preconditions} | {invalid input} | 1. Prepare invalid request; 2. Send; 3. Inspect response | {expected behavior — confirmation if undocumented} | {document section} | NEEDS_CONFIRMATION |

## Coverage summary
- Operations covered: {count}
- Positive/negative/boundary/security scenarios: {counts}
- Contract gaps: {items}

## Required human decisions
- {Expected status or message to confirm}
- {Test priority and automation scope approval}
