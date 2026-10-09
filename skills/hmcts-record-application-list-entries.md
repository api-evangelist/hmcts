---
name: hmcts-record-application-list-entries
description: Create an Applications Register list, add entries using reference data, and record results.
api: openapi/hmcts-applications-register-openapi.yml
operations: [getCourtLocations, getApplicationCodes, getResultCodes, getApplicationLists, createApplicationList, createApplicationListEntry, getApplicationListEntries, createApplicationListEntryResult]
---
# Record application list entries and results

1. Resolve reference data: `getCourtLocations`, `getApplicationCodes`, `getResultCodes` (all paginated and filterable).
2. `getApplicationLists` to find an existing list, or `createApplicationList`.
3. `createApplicationListEntry` for each application on the list; `getApplicationListEntries` to confirm.
4. `createApplicationListEntryResult` to record the outcome against an entry.

Rules: list endpoints are paginated — iterate pages rather than assuming one response. The spec declares no security scheme and a relative server (`/`).
