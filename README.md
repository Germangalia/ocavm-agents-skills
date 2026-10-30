# OCVA Agents & Skills

A structured knowledge base for AI agents that design, implement, integrate, document, and validate systems using the Open Cooperative Vehicle Architecture (OCVA) protocols.

The repository covers three related protocol specifications:

- **OCAVS** — vehicle-to-server application and fleet/device management.
- **OCAVM** — short-range vehicle-to-vehicle and vehicle-to-infrastructure awareness and coordination.
- **OCAVI** — platform-to-platform service interoperability.

This repository provides reusable skills and role-based agent instructions. It contains no protocol runtime or application implementation.

## Repository structure

```text
.agents/
├── agents/       # Role-based agent instructions (AGENT.md)
└── skills/       # Reusable protocol knowledge (SKILL.md)
README.md
skills           # Symlink to .agents/skills for registry discovery
skills-lock.json # Registry lock file
```

## Protocol overview

OCVA separates vehicle/fleet management, peer coordination, and platform service exchange into distinct protocols. Choose the protocol from the operation and endpoint roles. Keep each protocol's message identifiers, data types, permissions, profiles, status codes, and lifecycle rules within that protocol.

The skills in this repository reference specification version **v0.1.0**. Resolve specification versions from the source repositories' Git release tags, and use version-pinned links when consulting normative requirements. The normative specification files are authoritative; checklists and operation-design records are planning material.

## Skills

Skills are focused knowledge units that agents can load for the relevant protocol task.

| Skill | Coverage |
| --- | --- |
| `ocva-foundation` | Scope, terminology, roles, deployment, profiles, and boundaries across OCAVS, OCAVM, and OCAVI |
| `ocva-data-types` | Canonical scalar, object, enum, time, unit, identity, and geospatial representations |
| `ocva-message-semantics` | Request/response processing, idempotency, revisions, ordering, deadlines, and lifecycles |
| `ocva-security-privacy` | Validation, authorization, privacy, secure connectivity assumptions, and external-transfer constraints |
| `ocva-spec-authoring` | Normative ownership, requirement language, examples, repository conventions, and release discipline |
| `ocavm-awareness-danger` | OCAVM peer awareness, danger alerts, freshness, validity, and safety-sensitive handling |
| `ocavm-coordination` | OCAVM maneuver, intersection, merge, and platoon coordination |
| `ocavm-infrastructure-discovery` | OCAVM infrastructure capabilities, peer discovery, zones, subscriptions, geofences, and time windows |

## Agents

Agent definitions compose skills into task-focused responsibilities and outputs.

| Agent | Role |
| --- | --- |
| `protocol-architect` | Selects protocols, roles, profiles, normative owners, and deployment boundaries |
| `state-contract-engineer` | Designs typed message contracts, validators, idempotency, ordering, and state transitions |
| `security-privacy-engineer` | Reviews validation, authorization, privacy, and sensitive-data handling |
| `ocavm-coordination-developer` | Implements and reviews OCAVM awareness, coordination, and infrastructure-discovery behavior |
| `integration-specialist` | Designs and troubleshoots handoffs across OCAVS, OCAVM, and OCAVI |
| `conformance-test-engineer` | Builds traceable positive, negative, lifecycle, security, and recovery conformance cases |
| `documentation-release-writer` | Authors and reviews protocol documentation, examples, and release materials |

## Use the knowledge base

1. Identify the protocol, operation, endpoint roles, profile, and specification version relevant to the task.
2. Load the matching agent instructions from `.agents/agents/` when a role is useful.
3. Load the relevant skills from `.agents/skills/`; use shared foundation, data-type, message-semantics, and security guidance as applicable.
4. Follow the operation and type definitions in the selected protocol's version-pinned normative specification.
5. Preserve protocol boundaries and report gaps rather than inventing behavior that the specification does not define.

For OCAVM tasks, select the awareness/danger, coordination, or infrastructure-discovery skill for the feature area. For cross-protocol work, begin with `ocva-foundation` and consult the applicable shared skills.

## Installation and local usage

The root `skills` path is a symlink to `.agents/skills`, so registry tools can discover the skills while the project keeps its agent-oriented directory structure. To install the skills with the Skills CLI, use:

```sh
npx skills add Germangalia/ocavm-agents-skills
```

To work from a local checkout:

```sh
git clone https://github.com/Germangalia/ocavm-agents-skills.git
cd ocavm-agents-skills
```

Configure your agent runtime to load skills from `.agents/skills/` and, if supported, role instructions from `.agents/agents/`.

## Design principles

- Protocol-first, with clear boundaries between vehicle/fleet, peer-coordination, and platform-service behavior.
- Modular skills that can be composed for a task.
- Version-pinned references to normative specification sources.
- Exact preservation of field names, types, status values, permissions, and lifecycle rules.
- Safety-aware handling of peer information and coordination outcomes.
- Explicit identification of unspecified behavior and cross-protocol mapping gaps.

## Current repository scope

This checkout contains the eight distinct skills and seven agents listed above. The `ocva-data-types copy/` directory duplicates `ocva-data-types`; it is not a separate skill. Some agent definitions also name additional skill identifiers that are not present in this checkout, so those references should not be treated as available local skills.

## License

No license is declared in this repository yet.
