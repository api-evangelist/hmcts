---
name: hmcts-run-applications-register-report
description: Start an asynchronous Applications Register report job, poll it, and download the CSV.
api: openapi/hmcts-applications-register-openapi.yml
operations: [createFeesReport, createWorkloadReport, createDurationReport, getJobStatusById, downloadReport]
---
# Run an Applications Register report

1. Start a job, e.g. `createFeesReport`, `createWorkloadReport` or `createDurationReport`; keep the returned job id.
2. Poll `getJobStatusById` until the job reaches `completed`.
3. `downloadReport` streams the CSV — it only works once the job is `completed`.
