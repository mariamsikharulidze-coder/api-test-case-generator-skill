# API test-case coverage guidelines

## Extract only verified contract facts
- Path, HTTP method, operationId, tags
- Path/query/header parameters: required flag, type, format, constraints
- Request body: required properties, schema constraints, examples
- Responses: documented HTTP status codes, response schemas and error shapes
- Security: schemes declared for the operation; scopes if specified

## Candidate checks
| Category | When to consider | Evidence requirement |
|---|---|---|
| Positive | Success response documented | Use only documented success status/body |
| Missing required field | Field marked required | Error status only if documented |
| Invalid type/format | Field type or format defined | Do not invent exact message |
| Boundary | Min/max/length constraints defined | Test values just inside/outside constraints; status may need confirmation |
| Unauthorized | Security requirement documented | Documented status or NEEDS_CONFIRMATION |
| Forbidden | Role/scope requirement documented | Documented status or NEEDS_CONFIRMATION |
| Not found | Documented missing-resource response | Do not assume all ID endpoints return 404 |
| Conflict | Contract or rule defines collision case | Do not assume uniqueness unless specified |

## Test data practices
Use placeholders like `{valid_token}`, `{user_id}`, `{unique_email}`. Mark test data setup and cleanup requirements; never put secrets or real customer data in a test case.

## Priority suggestions
P1: contract's central supported workflow; P2: common invalid input; P3: edge-case constraints. Priorities are proposals requiring tester review.

## Final consistency checks
- Unique sequential scenario IDs
- Clear source for each expected result
- Explicit `NEEDS_CONFIRMATION` on unsupported expectations
- No invented selectors, statuses, response fields, roles or execution results
