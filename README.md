# OCVA Agents & Skills

[![skills.sh](https://skills.sh/b/Germangalia/ocavm-agents-skills)](https://skills.sh/Germangalia/ocavm-agents-skills)

A structured knowledge base for AI agents that design, implement, integrate, document, and validate systems using the **Open Cooperative Vehicle Architecture (OCVA)** protocols.

The repository covers three related protocol specifications:

- **OCAVS** — Vehicle-to-server application and fleet/device management.
- **OCAVM** — Short-range vehicle-to-vehicle and vehicle-to-infrastructure awareness and coordination.
- **OCAVI** — Platform-to-platform service interoperability.

This repository provides reusable AI agent skills and role-based agent instructions. It contains no protocol runtime or application implementation.

## Repository Structure

```text
.agents/
├── agents/       # Role-based agent instructions (AGENT.md)
└── skills/       # Skills loaded by the repo's local agent setup

agent/
└── skills/       # Registry-facing skill manifests (SKILL.md)

README.md
skills           # Symlink to agent/skills for registry discovery
skills-lock.json # Registry lock file
```

## Protocol Overview

OCVA separates vehicle/fleet management, peer coordination, and platform service exchange into distinct protocols.

Choose the protocol according to the operation being performed and the roles of the communicating endpoints. Keep each protocol's message identifiers, data types, permissions, profiles, status codes, and lifecycle rules within that protocol.

The skills in this repository reference specification version **v0.1.0**.

Resolve specification versions from the source repositories' Git release tags and use version-pinned links when consulting normative requirements. The normative specification files are authoritative; checklists and operation-design records are planning material.

## Skills

Skills are focused knowledge units that AI agents can load when performing relevant protocol tasks.

| Skill | Coverage |
|---|---|
| `ocva-foundation` | Scope, terminology, roles, deployment, profiles, and boundaries across OCAVS, OCAVM, and OCAVI |
| `ocva-data-types` | Canonical scalar, object, enum, time, unit, identity, and geospatial representations |
| `ocva-message-semantics` | Request/response processing, idempotency, revisions, ordering, deadlines, and lifecycles |
| `ocva-security-privacy` | Validation, authorization, privacy, secure-connectivity assumptions, and external-transfer constraints |
| `ocva-spec-authoring` | Normative ownership, requirement language, examples, repository conventions, and release discipline |
| `ocavm-awareness-danger` | OCAVM peer awareness, danger alerts, freshness, validity, and safety-sensitive handling |
| `ocavm-coordination` | OCAVM maneuver, intersection, merge, and platoon coordination |
| `ocavm-infrastructure-discovery` | OCAVM infrastructure capabilities, peer discovery, zones, subscriptions, geofences, and time windows |

**Total: 8 reusable skills.**

## Agents

Agent definitions compose skills into task-focused responsibilities and outputs.

| Agent | Role |
|---|---|
| `protocol-architect` | Selects protocols, roles, profiles, normative owners, and deployment boundaries |
| `state-contract-engineer` | Designs typed message contracts, validators, idempotency, ordering, and state transitions |
| `security-privacy-engineer` | Reviews validation, authorization, privacy, and sensitive-data handling |
| `ocavm-coordination-developer` | Implements and reviews OCAVM awareness, coordination, and infrastructure-discovery behavior |
| `integration-specialist` | Designs and troubleshoots handoffs across OCAVS, OCAVM, and OCAVI |
| `conformance-test-engineer` | Builds traceable positive, negative, lifecycle, security, and recovery conformance cases |
| `documentation-release-writer` | Authors and reviews protocol documentation, examples, and release materials |

**Total: 7 role-based agents.**

## Use the Knowledge Base

1. Identify the protocol, operation, endpoint roles, profile, and specification version relevant to the task.
2. Load the matching agent instructions from `.agents/agents/` when a specialized role is useful.
3. Load the relevant skills from `.agents/skills/`. Use shared foundation, data-type, message-semantics, and security guidance as applicable.
4. Follow the operation and type definitions in the selected protocol's version-pinned normative specification.
5. Preserve protocol boundaries and report gaps rather than inventing behavior that the specification does not define.

For OCAVM tasks, select the awareness/danger, coordination, or infrastructure-discovery skill according to the feature area.

For cross-protocol work, begin with `ocva-foundation` and consult the applicable shared skills.

## Installation

### Install all skills

Install the repository's available skills using the Skills CLI:

```bash
npx skills add Germangalia/ocavm-agents-skills
```

### List available skills

To inspect the available skills without installing them:

```bash
npx skills add Germangalia/ocavm-agents-skills --list
```

### Install an individual skill

To install a specific skill:

```bash
npx skills add Germangalia/ocavm-agents-skills --skill ocavm-coordination
```

Replace `ocavm-coordination` with the name of another available skill.

### Browse on skills.sh

Explore the repository and its skills:

https://skills.sh/Germangalia/ocavm-agents-skills

### Local Repository Usage

Clone the repository:

```bash
git clone https://github.com/Germangalia/ocavm-agents-skills.git
cd ocavm-agents-skills
```

Configure your agent runtime to load skills from `.agents/skills/` and, if supported, role instructions from `.agents/agents/`.

The root-level `skills` path is a symlink to `agent/skills/` so the Skills CLI discovers the registry-facing manifests. Keep those manifests in sync with the corresponding `.agents/skills/` copies used by the local agent setup.

## Design Principles

- **Protocol-first architecture:** Maintain clear boundaries between vehicle/fleet management, peer coordination, and platform-service behavior.
- **Modular knowledge:** Provide focused skills that agents can compose according to the task.
- **Version-pinned references:** Reference normative specification sources using identifiable versions.
- **Data integrity:** Preserve exact field names, types, status values, permissions, and lifecycle rules.
- **Safety awareness:** Handle peer information and coordination outcomes with appropriate safety considerations.
- **Explicit specification gaps:** Identify unspecified behavior and cross-protocol mapping gaps rather than inventing requirements.
- **Reusable agent roles:** Organize specialized agent instructions around clearly defined responsibilities and outputs.

## Current Repository Scope

This repository contains:

- **8 distinct reusable skills**
- **7 role-based agent definitions**
- **3 protocol specifications:** OCAVS, OCAVM, and OCAVI

The `ocva-data-types copy/` directory duplicates `ocva-data-types` and is not a separate skill.

Some agent definitions reference additional skill identifiers that are not present in this checkout. Those references should not be treated as available local skills or installable skills. Only the eight skills listed in this README are currently included.

## License

No license is currently declared in this repository.
