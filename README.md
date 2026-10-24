# API Test Case Generator — Custom Skill homework

This repository contains a custom AI skill for producing reviewable API test scenarios from a documented OpenAPI/Swagger contract.

## Submission files
- [`api-test-case-generator/SKILL.md`](api-test-case-generator/SKILL.md) — trigger description and agent workflow
- [`api-test-case-generator/references/coverage-guidelines.md`](api-test-case-generator/references/coverage-guidelines.md) — coverage guide
- [`api-test-case-generator/assets/test-case-template.md`](api-test-case-generator/assets/test-case-template.md) — Markdown output template
- [`ANALYSIS_AND_REFLECTION.md`](ANALYSIS_AND_REFLECTION.md) — one-page analysis and short reflection

## Example user prompt
> Use the api-test-case-generator skill to draft API test cases from the attached OpenAPI YAML for POST /users. Clearly mark behavior that is not defined in the contract.

## Safety and scope
The skill does not make network requests or claim tests were executed. Human review is required before automation.
