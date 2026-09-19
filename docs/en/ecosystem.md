# Garden Ecosystem

Status: **Proposed ecosystem authority**

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

The current ecosystem rules are:

```text
Lilium  -X-> Protea
Lilium  -X-> Aster
Aster   -X-> Protea
Aster   -X-> Lilium core runtime

Protea   ----> optional Aster integration
Protea   ----> optional Lilium adapter
Aster   ----> optional Lilium adapter
Projects ----> optional Flora plugin adapters
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

Garden should permit, among others:

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
share one product boundary:

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

Garden uses botanical nomenclature as an architectural identity system, not merely as a visual
theme.

```text
Garden product or project       ----> botanical genus
Named internal product identity ----> species of that genus
```

A genus normally identifies a major Garden product when its botanical meaning reinforces the
product role. Species belonging to that genus form a reserved naming space for meaningful and
durable identities within the product.

Species names are not mandatory for every package, class, component, or implementation detail.
Each product decides which internal concept maps naturally to species and assigns a species only
when that concept has enough stability and semantic value to benefit from a botanical identity.
Aster provides the first explicit application: official icon collections may use species of the
genus *Aster*.

The [Garden Botanical Registry](registry/index.md) is authoritative for botanical names,
taxonomic status, reservations, candidates, species assignments, and deliberate exceptions.

### Deliberate botanical exceptions

A Garden product should normally use a botanical genus, but another botanical term may be
accepted when its meaning has a stronger architectural relationship with the product. Every
exception must be explicit in the Botanical Registry and does not weaken the default convention.

**Flora** is the current deliberate exception. *Flora* is a collective botanical term rather than
a genus, and its meaning fits shared CLI infrastructure that can host and compose tooling across
Garden.
