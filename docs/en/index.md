# Garden Architecture Book

Status: **Canonical ecosystem authority; individual decisions retain their stated status**

Garden is an ecosystem of independent software projects that share an interoperability philosophy
without requiring one another. This Architecture Book records project identity, ecosystem
relationships, and cross-project dependency direction. It is not an API reference and does not
replace the canonical documentation owned by each project.

The [shared project rules](project-rules.md) own accepted engineering and contribution policy,
including language-specific profiles, shared CLI presentation and the procedure for product exceptions.
Policy acceptance is distinct from product adoption and automated enforcement.

## Projects

| Project | Role | Current architectural status |
| --- | --- | --- |
| [Lilium](products/lilium/index.md) | Frontend framework | Active project with evolving architecture. |
| [Protea](products/protea/index.md) | UI component library | Active product direction with evolving architecture. |
| [Aster](products/aster/index.md) | Portable icon platform | Active project with published Core, Icons, SVG and CLI packages, plus private Import. |
| [Flora](products/flora/index.md) | Headless multi-ecosystem CLI platform | Accepted product direction; implementation and plugin ABI remain future work. |

The [Garden ecosystem](ecosystem.md) defines the principles shared by these projects.

## Repository automation

[Repository automation](automation.md) documents Garden's Discord notification workflow, event
coverage and secret configuration. Notifications do not replace documentary verification or
product-owned CI.

## Authority boundary

This book may state:

- why a Garden project exists;
- what broad responsibility it owns;
- which dependencies and integrations are allowed;
- which project owns an adapter or plugin;
- which cross-project decisions are accepted, provisional, or deferred.

Shared engineering and contribution requirements belong to the [project rules](project-rules.md).
Product repositories reference that authority and retain their compatible additions and approved
exceptions at the owning product; reciprocal links preserve each subject's owner.

This book must not duplicate package contracts, installation instructions, runtime workflows,
diagnostic tables, release procedures, or source-level implementation details. Those belong to
the relevant project and package documentation. Aster's
[package documentation](https://github.com/BlueLuscious/aster/tree/master/docs/en/packages)
remains authoritative for implemented Aster behaviour.

## Status language

| Status | Meaning |
| --- | --- |
| Accepted | The identity or boundary is an active architectural constraint. |
| Proposed | The direction is useful but still requires implementation or consumer evidence. |
| Provisional | A likely name or package boundary that may change without compatibility impact. |
| Deferred | Work intentionally postponed until an explicit trigger exists. |

Project identity can be accepted while its package layout, ABI, or implementation remains
proposed. Flora currently uses this distinction.

## Botanical naming authority

The [Garden Botanical Registry](registry/index.md) is the canonical cross-project authority for
Garden's botanical identity system. Its genus registry owns product assignments, deliberate
exceptions, reserved names, and candidates. Each product owns its species assignments through the
registry linked from its product documentation.

This Architecture Book may explain how a botanical identity affects an architectural boundary,
but it must not duplicate botanical registries. Conversely, those registries do not own package
APIs, implementation details, visual specifications, or runtime behaviour.
