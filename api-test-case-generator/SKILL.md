---
name: api-test-case-generator
description: >-
  Generate reviewable positive, negative, boundary, and authorization API test scenarios
  from a supplied OpenAPI/Swagger specification, endpoint contract, or documented HTTP request.
  Use when a user asks for API test cases, a test matrix, or test scenario drafts for
  Rest-Assured/TestNG work. Do not use to invent contracts or claim tests were executed.
---

# API Test Case Generator

## Goal
Turn a documented API contract into a concise, traceable Markdown test-case matrix suitable for human review and later Rest-Assured/TestNG automation.

## Inputs
1. OpenAPI JSON/YAML, Swagger export, or a clearly stated API endpoint contract.
2. Optional: endpoint(s) and operations to cover, authentication details, known business rules, environments and test data constraints.
3. Optional: desired output filename and priority convention.

If the contract is missing, ask for it before drafting endpoint-specific expectations. Do not infer undocumented response codes, field names, validation rules or authorization policies.

## Workflow

### 1. Read and scope
- Read the supplied specification or documentation; identify the exact path, method, operationId (if present), description, parameters, request schema and declared responses.
- If the specification is large, prioritize endpoints named by the user; otherwise offer an endpoint inventory and select a manageable first batch.
- Keep a `Source` value for each scenario (path/method and schema or document section).

### 2. Extract contract facts
- Identify required fields, types, constraints (`minLength`, `maximum`, `enum`, formats), success responses, error responses, authentication/security requirements, and stated business rules.
- Distinguish **documented** behavior from **proposed checks**. Tag proposed checks `NEEDS_CONFIRMATION` instead of assigning invented expected statuses.
- Never expose real API keys, passwords, tokens, personal records, or production secrets in the output. Use placeholders.

### 3. Generate scenarios
- Start with a happy-path test for each selected operation where the specification supports it.
- Add negative tests for documented missing/invalid fields, invalid types, bounds, and malformed payloads.
- Add authentication/authorization checks **only** if security requirements are documented; where the exact failure response is unspecified, mark it for confirmation.
- Add relevant boundary-value and resource-not-found cases when supported by the contract.
- Each scenario needs an ID (`API-TC-001`...), category, priority suggestion, precondition, request/test data, steps, expected result, source, and review status.
- Use `references/coverage-guidelines.md` for selection; use `assets/test-case-template.md` as output format.

### 4. Review gate — human decision required
- Present all `NEEDS_CONFIRMATION` cases, unverified assumptions, missing test-data rules and priority suggestions.
- Ask the tester/product owner to approve expected results and decide what to automate.
- Never silently convert an assumption into a verified API requirement.

### 5. Deliver and verify
- Produce a Markdown test matrix with clear, distinct IDs and reproducible steps.
- Recheck that the response code and body assertions are grounded in the supplied contract; if not, mark as unconfirmed.
- Check every scenario refers to a real source operation, does not contain secrets and does not claim execution.
- Summarize coverage by operation/category, coverage gaps and the human approval needed.
- Only write Java Rest-Assured/TestNG tests if explicitly requested after the expected results are approved; inspect the existing project before choosing packages/dependencies.

## Boundaries
- No running tests, API calls, database mutation, project edits or Git pushes unless separately requested and an appropriate execution tool is available.
- No assumptions about live service behavior, security rules, response codes, or database state.
- This skill generates **draft test cases**, not proof that the API works.
