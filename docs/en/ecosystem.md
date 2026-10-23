# Garden Ecosystem

Status: **Canonical ecosystem authority; individual decisions retain their stated status**

Garden is a family of focused software projects for building frontend products. Its identity comes
from interoperability, consistent architectural values, and deliberate integration boundaries,
not from one mandatory dependency graph.

> Garden is an ecosystem by interoperability, not by dependency.

## Purpose

Garden aims to provide a coherent set of independently useful tools while preserving:

- product autonomy;
- composability and replaceability;
- explicit public integration points;
- independent implementation and versioning;
- adoption of one project without the rest of the ecosystem.

Botanical names provide a shared identity, but each name should reinforce a real product role
rather than justify creating another repository.

The [shared project rules](project-rules.md) own engineering and contribution conventions.
This document owns product relationships; product documentation owns implemented contracts.

## Principles

### Independent by default

Every major project must remain useful on its own. Lilium must not require Protea or Aster. Protea
must not exist merely as Lilium's internal component package. Aster must not require a framework or
UI library. Flora must not become an application runtime dependency.

### Public integration boundaries

Projects integrate through documented APIs, adapters, wrappers, plugins, or serialisable
contracts. No Garden integration may depend on another project's implementation paths.

### Agnosticism with purpose

Technology-independent foundations are valuable when they support real reuse. Runtime-specific
behaviour belongs in explicit hosts or adapters. Agnosticism is not a reason to abstract an
incidental implementation detail.

### Focused ownership

Each project owns one coherent product responsibility and explicit non-goals. A new project is
justified only when it has independent value, evolution, versioning, and integration needs.

## Current projects

```text
Garden
|-- Lilium   Frontend framework
|-- Protea   UI components
|-- Aster    Portable icons
`-- Flora    Headless CLI platform
```

Lilium, Protea, and Aster are active product projects. Flora has an accepted identity and role, but
its implementation, package layout, and plugin ABI are not yet established product contracts.

Protea's product identity is the UI component library as a whole. Framework-neutral or headless
foundations are internal architectural layers, not a restriction of the product to headless UI.

## Dependency direction

The accepted dependency boundaries are shown below. Optional adapters and Flora integrations
describe permitted compositions, not evidence of implemented or published integrations.

```text
Lilium  -X-> Protea
Lilium  -X-> Aster
Aster   -X-> Protea
Aster   -X-> Lilium core runtime

Protea                ----> optional Aster public capability
Protea Lilium adapter ----> Protea public contracts + Lilium public contracts
Aster Lilium adapter  ----> Aster public contracts + Lilium public contracts
Project Flora plugin  ----> project public commands + Flora public contracts
```

An adapter depends on public contracts from the products it connects. The foundational product
must not acquire a reverse dependency merely to support an adapter.

## Integration forms

| Form | Responsibility |
| --- | --- |
| Adapter | Connects one product to a specific framework, runtime, target, or host. |
| Wrapper | Presents an existing capability through another project's native consumer model. |
| Plugin | Contributes domain commands or capabilities to an extensible host such as Flora. |
| Plan | Describes a complete host-neutral operation that a capable host may present or commit. |

Project-specific integrations should normally remain with the project whose domain they
understand. Generic host contracts remain with the host project.

## Supported compositions

Garden's architecture permits, among others, the following compositions. This is an ownership and
dependency model, not an installation or support matrix:

```text
Lilium
Protea
Aster
Flora
Lilium + Protea
Lilium + Aster
Protea + Aster
Lilium + Protea + Aster
Flora + any explicit project plugin
```

No composition is the mandatory definition of Garden.

## Repository and versioning model

Major products belong in separate repositories and may use internal monorepos for packages that
share one product boundary. The layout below models ownership; it does not establish every
repository or integration as implemented:

```text
BlueLuscious/
|-- lilium/
|-- protea/
|-- aster/
`-- flora/       when independent implementation evidence justifies extraction
```

Each product versions and releases independently. Adapters and plugins declare compatibility with
the public contracts they consume. Garden does not require synchronised ecosystem releases.

## New-project criteria

A capability becomes a separate Garden project only when it has:

1. A responsibility distinct from existing projects.
2. Meaningful use outside one implementation detail.
3. A reason to evolve and version independently.
4. Explicit integration boundaries and non-goals.
5. At least one credible implementation or consumer path.

The ecosystem must not grow merely to appear comprehensive.

## Botanical naming model

Botanical identities connect each product's role to Garden without determining its package graph
or implementation. The [Garden Botanical Registry](registry/index.md) owns the naming model,
statuses, taxonomic integrity and product species authorities. The
[Garden Genus Registry](registry/genera.md) owns product assignments, reservations and candidates,
including [Flora's accepted exception](registry/genera.md#flora).

Product species registries record the durable identities assigned within their product. For
example, the [Aster Species Registry](products/aster/species-registry.md) owns the botanical
assignment of Amellus; Aster owns the collection's membership, visual rules and product behaviour.

### Deliberate botanical exceptions

The [Garden Genus Registry](registry/genera.md#flora) records Flora's accepted exception and its
architectural rationale.
