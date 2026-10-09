---
name: hmcts-subscribe-to-hearing-result-documents
description: Register a callback for HMCTS crime hearing result document events, verify signed callbacks, and fetch the PDF.
api: openapi/hmcts-crime-hearing-results-document-subscription-openapi.yml
operations: [GetEventTypes, createClientSubscription, getClientSubscription, updateClientSubscription, rotateClientSubscriptionSecret, getDocument, deleteClientSubscription]
---
# Subscribe to crime hearing result documents

1. `GetEventTypes` — list the valid event types you can subscribe to.
2. `createClientSubscription` — POST your `notificationEndpoint.callbackUrl` and chosen event types. The shared HMAC secret is returned once at creation: store it.
3. Verify each callback: it carries `X-Signature` (HMAC-SHA256 of the request using the subscription secret) and `X-Key-Id` (matches the keyId issued at creation). Reject anything that does not verify.
4. `getDocument` — retrieve the PDF for the documentId named in the event.
5. `getClientSubscription` / `updateClientSubscription` (strict update) to inspect or change the subscription.
6. `rotateClientSubscriptionSecret` periodically; `deleteClientSubscription` to stop.

Rules: every call needs both `bearerAuth` and `subscriptionKey` (spec-level security). Propagate `X-Correlation-Id` from responses into your logs. The spec declares no idempotency key — do not blindly retry `createClientSubscription`.
