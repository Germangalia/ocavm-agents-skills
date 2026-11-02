---
name: ocavm-infrastructure-discovery
description: "OCAVM infrastructure capabilities, peer discovery, coordination status, zone/capability queries, alert subscriptions, geofences, and time windows."
---
# OCAVM Infrastructure and Discovery

## Specification Versions

This skill references **OCAVM** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when discovering nearby peers or roadside infrastructure, querying capabilities or zones, publishing coordination status, subscribing to alerts, or applying an infrastructure geofence.

## Key References

- [Infrastructure types](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-08-infrastructure.md), [time-window types](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-09-time-windows.md)
- Operations: [infrastructure](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-07-infrastructure-operations.md), [peer discovery](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-08-peer-discovery-operations.md), [coordination status](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-09-coordination-status-operations.md), [zone query](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-10-zone-query-operations.md), [capability query](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-11-capability-query-operations.md), [alert subscription](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-12-alert-subscription-operations.md), [geofence](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/04-operations/04-13-geofence-operations.md)
- [Limits and defaults](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/appendix/D-limits-defaults.md)

## Rules

- Use discovery results as time-bounded information; validate timestamps, range, participant type, and capability freshness before use.
- A capability query describes supported operations/features, not current permission or guaranteed availability.
- Apply zone/geofence geometry, validity interval, time-window, and query-limit constraints as defined.
- Keep coordination status publication separate from negotiation and execution of a coordination operation.
- Create and remove alert subscriptions using their defined lifecycle, filters, expiry, and result semantics.
- Follow the operation's empty-result and no-match behavior; do not convert a valid empty response into an error.
- Use exact OCAVM identifiers and status enums from the selected specification version.

## Common Pitfalls

- Treating a discovered peer as permanently reachable or capable.
- Confusing a zone query response with permission to enter or use the zone.
- Ignoring subscription expiry or sending alerts outside the requested filter.
- Applying stale infrastructure capability data to a safety-critical decision.
- Reusing similarly named service discovery behavior from OCAVI.
