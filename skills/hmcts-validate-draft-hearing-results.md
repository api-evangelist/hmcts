---
name: hmcts-validate-draft-hearing-results
description: Check draft crime hearing results against the HMCTS Results Validation Service rules before submission.
api: openapi/hmcts-results-validation-service-openapi.yml
operations: [listValidationRules, getValidationRuleById, validateDraftResults, updateValidationRule]
---
# Validate draft hearing results

1. `listValidationRules` — see which rules exist and are enabled; `getValidationRuleById` for detail.
2. `validateDraftResults` — POST the draft results; validates against all enabled validators and returns a unified response of errors and warnings (400 on malformed input).
3. Fix errors, re-run step 2; warnings are advisory.
4. `updateValidationRule` (PATCH) enables or disables a rule — an administrative action, do not call it from an end-user flow.

Rules: the spec declares no security scheme and no servers block; the deployment base URL is not published.
