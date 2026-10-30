---
description: "OCAVM peer awareness and danger-alert data, message validity, freshness, and safety-sensitive handling. Load for short-range situational-awareness or hazard workflows."
---
# OCAVM Awareness and Danger Alerts

## Specification Versions

This skill references **OCAVM** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when implementing peer awareness broadcasts, danger alerts, alert interpretation, freshness/expiry checks, or related conformance cases.

## Key References

- [General types](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-01-general.md), [awareness types](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-02-awareness.md), [danger types](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-03-danger.md)
- [Awareness operations](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-01-awareness-operations.md), [danger-alert operations](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-02-danger-alert-operations.md)
- [Message semantics](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/01-architecture/01-02-message-semantics.md), [state-machine conformance](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/06-compliance/06-03-state-machine-conformance.md)

## Rules

- Treat awareness and danger messages as short-range peer information, not as fleet missions or platform service requests.
- Validate the exact message type, required fields, enum values, spatial/temporal bounds, source identity context, and message validity rules.
- Apply the specified freshness and validity windows before using received information. Stale data must not be treated as current.
- Preserve the distinction between routine awareness, a standardized danger alert, and a coordination request.
- Follow broadcast/notification semantics and the defined duplicate, ordering, and processing outcomes for the operation.
- Use only the recognized alert categories and meanings in the selected specification version; do not invent severity mappings.
- Respect local safety policy and do not present a peer alert as a direct vehicle-control command.

## Common Pitfalls

- Acting on expired or out-of-range peer information.
- Treating a broadcast receipt as agreement to a cooperative maneuver.
- Translating a danger category into a response that the specification does not define.
- Reusing a CAV fleet or platform role in peer authorization logic.
- Assuming every awareness message is a request/response exchange.
