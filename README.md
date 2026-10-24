# API Test Case Generator — Custom Skill homework

This repository contains a custom AI skill for producing reviewable API test scenarios from a documented OpenAPI/Swagger contract.

## Submission files
- [`.agents/skills/api-test-case-generator/SKILL.md`](.agents/skills/api-test-case-generator/SKILL.md) — trigger description and agent workflow
- [`.agents/skills/api-test-case-generator/references/coverage-guidelines.md`](.agents/skills/api-test-case-generator/references/coverage-guidelines.md) — coverage guide
- [`.agents/skills/api-test-case-generator/assets/test-case-template.md`](.agents/skills/api-test-case-generator/assets/test-case-template.md) — Markdown output template
- [`ANALYSIS_AND_REFLECTION.md`](ANALYSIS_AND_REFLECTION.md) — one-page analysis and short reflection

## Example user prompt
> Use the api-test-case-generator skill to draft API test cases from the attached OpenAPI YAML for POST /users. Clearly mark behavior that is not defined in the contract.

## Safety and scope
The skill does not make network requests or claim tests were executed. Human review is required before automation.
