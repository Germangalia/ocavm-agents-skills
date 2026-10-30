---
description: "OCAVM cooperative maneuvers, intersection and merge coordination, and platoon formation/lifecycle. Load when implementing negotiated peer coordination."
---
# OCAVM Cooperative Coordination

## Specification Versions

This skill references **OCAVM** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load for maneuver negotiation, intersection reservation/coordination, merge sequencing, platoon formation or membership, and peer state transition handling.

## Key References

- Types: [maneuver](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-04-maneuver.md), [intersection](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-05-intersection.md), [merge](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-06-merge.md), [platoon](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-07-platoon.md)
- Operations: [maneuver coordination](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-03-cooperative-maneuver-operations.md), [intersection](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-04-intersection-coordination-operations.md), [merge](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-05-merge-coordination-operations.md), [platoon](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-06-platoon-coordination-operations.md)
- [Application behavior](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/05-application/05-01-application-behavior.md), [state-machine conformance](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/06-compliance/06-03-state-machine-conformance.md)

## Coordination Rules

- Model each coordination type using its own request, response, role, resource, and lifecycle definitions.
- Check participant capabilities and operation preconditions before negotiation.
- Apply time windows, expiry, sequence, idempotency, and revision constraints from the relevant operation.
- Treat proposal, acceptance, commitment, execution/status, and termination as distinct states where defined.
- Reject prohibited transitions and stale or conflicting state according to the operation's status rules.
- A coordination outcome describes peer agreement; it does not replace onboard safety validation or directly actuate the vehicle.
- Keep maneuver, intersection, merge, and platoon state separate even when a deployment combines them.

## Common Pitfalls

- Assuming a proposal is an accepted commitment.
- Applying intersection rules to merge or platoon state because the message patterns look similar.
- Ignoring the time window or proceeding after an offer expires.
- Letting duplicate requests create multiple reservations or coordination objects.
- Treating a peer agreement as authorization to bypass local safety constraints.
