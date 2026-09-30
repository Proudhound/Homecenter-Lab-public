# AGENTS.md

## Purpose

This file defines the operating rules for AI agents and coding assistants working in **HomeCenter Lab Public**.

**This repository is PUBLIC. Treat every file, commit, issue, pull request and generated artifact as if it will be immediately visible on the public internet.**

Do not treat this file as a replacement for the project documentation. It is a routing and safety layer that tells agents what to read and which rules take precedence.

---

## Required reading

Before making changes, read the relevant project guidance.

### Always read

1. `README.md` – project scope and public/private separation
2. `SECURITY.md` – publication and security rules
3. `CONTRIBUTING.md` – contribution and review workflow

### Read when making project or product decisions

4. `ROADMAP.md` – current direction and planned work
5. `docs/product/PRODUCT_VISION.md` – product goals and architectural principles
6. `docs/product/FAMILY_VALUE_GATE.md` – value test for new hardware, features and integrations
7. `docs/product/MVP_V0_1.md` – current MVP scope

### Read when relevant

- `SPONSORING.md` – sponsored, supplied, loaned or discounted hardware/services; commercial relationships
- `CODE_OF_CONDUCT.md` – community interaction and moderation
- `SUPPORT.md` – support boundaries
- `LICENSE` and `LICENSE-DOCS` – licensing
- relevant files below `docs/` for the subsystem being changed

---

## Rule priority

When instructions conflict, apply this order:

1. Protect people, credentials and private infrastructure.
2. `SECURITY.md` and the Publication Security Gate.
3. Applicable repository licenses.
4. `CONTRIBUTING.md`.
5. Product principles and `PRODUCT_VISION.md`.
6. `ROADMAP.md` and MVP scope.
7. Subsystem documentation.
8. Convenience or implementation preference.

**Security and privacy take precedence over completeness.**

When in doubt, do not publish the information.

---

## Public repository boundary

HomeCenter Lab Public is a sanitized publication layer of a separately maintained private HomeCenter environment.

Never assume information is safe to publish merely because an agent can access it.

### Never copy directly from private sources without review

Content originating from a private repository, local machine, configuration export, screenshot, log, connected service or other private source must be actively sanitized before being added here.

Do not publish:

- passwords
- API keys
- access tokens
- cookies or session information
- private/public VPN key material
- SSH private keys
- recovery secrets
- real private-network IP addresses
- MAC addresses
- serial numbers
- unique device identifiers
- internal/private hostnames or DNS names
- Wi-Fi credentials
- private URLs containing identifiers or tokens
- personal filesystem paths when they identify a person or environment
- exact private security-device placement
- camera footage or snapshots
- precise household security topology
- personal household, family or location information
- logs containing any of the above

This list is not exhaustive.

---

## Sanitization

Preserve the technical lesson while removing identifying infrastructure data.

Prefer documentation-safe examples such as:

- IPv4: `192.0.2.0/24`, `198.51.100.0/24`, `203.0.113.0/24`
- IPv6: `2001:db8::/32`
- hosts: `SERVER-01`, `HA-VM`, `NAS-01`, `CLIENT-01`
- users: `example-user`
- domains: `example.com`

Do not merely redact one obvious secret while leaving enough surrounding information to reconstruct private infrastructure.

---

## Publication Security Gate

Before creating or modifying public content, check the proposed diff for:

- credentials and secrets
- IP and MAC addresses
- serial numbers and device IDs
- internal hostnames
- personal names or identifiers not intentionally public
- private paths
- location information
- camera/security details
- account identifiers
- hidden metadata copied from private sources
- commercially confidential information

Perform this check again after generating documentation from logs, screenshots, exports or private repository content.

If uncertain, stop and request human review rather than publishing.

---

## Product decision rules

New features, hardware and integrations should support a real HomeCenter use case.

Apply the principles in `docs/product/FAMILY_VALUE_GATE.md`.

Prefer:

- measurable everyday value
- local-first operation where practical
- integration before replacement
- reuse of existing hardware
- simple family-facing interfaces
- graceful degradation
- manual fallback for important home functions
- vendor-neutral abstractions
- reproducible documentation

Avoid adding complexity solely because a technology is interesting.

Experimental work is welcome, but it should be clearly separated from family-critical infrastructure.

---

## Safety-critical automation

Do not make an LLM, cloud AI service or experimental component the sole decision-maker for safety-critical functions.

Heating protection, access control, water, electrical safety, alarms and similar functions require explicit deterministic rules, limits and appropriate manual fallback.

---

## Hardware

Before recommending or adding hardware:

1. Define the use case.
2. Apply the Family Value Gate.
3. Check whether existing hardware can satisfy the requirement.
4. Consider power consumption, lifecycle cost and maintenance.
5. Document important compatibility limitations.
6. Disclose commercial relationships where applicable.

Do not publish private serial numbers, MAC addresses or inventory identifiers.

---

## Sponsoring and commercial relationships

When a change involves a manufacturer, retailer, affiliate relationship, sponsored product, free sample, loan unit, discount or paid collaboration, read `SPONSORING.md` first.

Never:

- promise positive coverage
- suppress relevant criticism
- alter technical conclusions because of sponsorship
- give sponsors access to private infrastructure
- imply that supplied hardware was independently purchased

Relevant relationships must be disclosed.

---

## Documentation

Documentation should be understandable without access to the private HomeCenter environment.

Prefer:

- clear prerequisites
- copyable commands
- explicit assumptions
- relevant version information
- distinction between tested and proposed behavior
- generic diagrams
- reproducible examples
- links between related project documents

German is the preferred project language. English contributions are welcome. Core public documentation should gradually be available in both languages, but a contribution does not need to provide both languages unless the task specifically requires it.

---

## Changes and pull requests

Keep changes focused.

For substantial features, architecture changes, new integrations, security/privacy changes or major restructuring, follow the issue-first workflow described in `CONTRIBUTING.md`.

Before completion:

1. Review the diff.
2. Run the Publication Security Gate.
3. Check relevant documentation.
4. Update documentation when behavior changes.
5. State what was tested and what remains untested.
6. Ensure commercial relationships are disclosed.
7. Ensure the change remains within project scope.

Do not claim something was tested when it was only inferred or generated.

---

## Private-to-public workflow

When asked to transfer material from the private HomeCenter project into this repository:

1. Identify the technical information that provides public value.
2. Remove information that identifies the real household, people or infrastructure.
3. Replace private values with documentation-safe examples.
4. Remove unnecessary operational detail.
5. Preserve useful reasoning, architecture decisions and lessons learned.
6. Review the sanitized result against `SECURITY.md`.
7. Only then publish it.

**Never perform a blind repository mirror or bulk copy from private HomeCenter into HomeCenter Lab Public.**

---

## Agent behavior

Agents should:

- prefer existing project conventions over inventing parallel structures
- update existing documentation rather than creating duplicates
- explain meaningful architectural decisions
- flag uncertainty instead of inventing facts
- avoid unnecessary dependencies
- preserve manual and recovery paths
- keep public examples generic and reproducible
- leave security-sensitive decisions for human review when uncertain

Agents should not:

- weaken publication safeguards for convenience
- expose private information to make documentation more complete
- turn experimental components into hidden critical dependencies
- create marketing claims unsupported by evidence
- present sponsorship as technical validation

---

## Final check

Before considering a task complete, ask:

> Would I be comfortable publishing this exact diff, including metadata and examples, to anyone on the internet?

If the answer is not clearly **yes**, do not publish it without human review.
