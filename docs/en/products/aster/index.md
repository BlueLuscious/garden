# Aster

Status: **Active project; pre-release packages implemented**

Aster is Garden's portable icon platform. It owns immutable target-independent icon definitions,
canonical icon and collection modules, standalone SVG rendering, optional SVG ingestion services,
and command-line discovery and export workflows.

Implemented package behaviour is documented by the
[Aster package documentation](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages), which remains authoritative over this
ecosystem summary.

## Responsibility

Aster owns:

- a portable serialisable icon and collection model;
- immutable construction, validation, identity, metadata, geometry, and presentation contracts;
- canonical TypeScript-first icons and collections;
- framework-independent SVG markup rendering;
- an optional private SVG and metadata ingestion domain;
- host-neutral catalogue commands and a standalone Node CLI;
- future target and framework adapters when real consumers justify them.

## Current package boundary

| Package | Current responsibility | Status |
| --- | --- | --- |
| [`@aster/core`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/core) | Portable definitions, contracts, construction, and validation. | Hardened pre-release foundation. |
| [`@aster/icons`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/icons) | Canonical TypeScript icon modules and explicit collection membership. | Experimental pilot collection. |
| [`@aster/svg`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/svg) | Deterministic standalone SVG markup rendering. | Hardened pre-release target. |
| [`@aster/import`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/import) | Private external-source inspection, adoption diagnostics, normalisation, and editable TypeScript emission. | Implemented narrow adoption boundary. |
| [`@aster/cli`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/cli) | Host-neutral catalogue commands, SVG export planning, and standalone Node effects. | Hardened pre-release. |

These packages depend only in their documented direction. Core does not depend on a target,
collection, framework, CLI, or Import implementation.

## Current visual baseline

The pilot Aster collection currently uses:

- a `24 x 24` view box;
- `1.5` view-box units as its authored default stroke width;
- round line caps and joins;
- `currentColor` as the standard SVG paint inheritance keyword;
- explicit collection membership over independent icon definitions.

These are current collection authorities, not universal constraints imposed by `@aster/core` on
all third-party definitions.

## Authoring and rendering

Aster is TypeScript-first. Canonical icon definitions are authored as immutable Core data and can
be consumed without SVG, Lilium, Protea, or the CLI. `@aster/svg` interprets those definitions as
standalone markup. `@aster/import` provides an optional path from explicit external SVG and
reviewed Core metadata to editable portable definitions and is not required for ordinary icon
consumption or export.

The portable definition schema and renderer are implemented contracts, not illustrative future
ideas. Framework components and generated named wrappers remain deferred target integrations.

## Lilium and Protea relationships

```text
Aster portable definitions ----> future Aster Lilium adapter ----> Lilium
Protea --------------------------> optional Aster public capability
Aster -X-> Protea
```

Aster must remain usable without either project. A future Lilium adapter belongs to Aster and may
depend only on public Lilium contracts. Protea decides whether and how to accept icons; Aster does
not contain Protea-specific semantics.

## Flora relationship

Aster already separates host-neutral command execution from its private standalone Node shell.
If Flora defines a stable plugin ABI and a real integration demonstrates reuse, Aster may evolve
towards:

```text
@aster/commands   host-neutral Aster command domain
@aster/cli        standalone Aster executable and default catalogue composition
@aster/flora      optional adapter to @flora/core
```

`@aster/commands` and `@aster/flora` do not exist yet and must not be created merely to reorganise
the repository. Flora must not know how Aster definitions, collections, renderers, or ingestion
services work internally.

The intended user forms are:

```text
aster search camera
aster export icon aster/camera
flora aster search camera
flora aster export icon aster/camera
```

The standalone and Flora hosts may present or publish immutable Aster plans through their own
capabilities without moving process or filesystem authority into the command domain.

## Versioning

Aster versions independently from Lilium, Protea, and Flora. Future adapters declare compatible
public contract ranges. Icon additions, corrections, package hardening, and framework releases do
not require synchronised Garden versions.

## Botanical collection identity

Aster follows Garden's genus-and-species naming model. **Aster** is the product identity and
botanical genus. Official Aster icon collections may use species belonging to the genus *Aster* as
their collection identities:

```text
Aster                         product and genus
`-- Aster <species>           official icon collection identity
```

The species identifies the collection; visual properties remain separate collection metadata and
contracts. This model applies to official named collections and does not require every icon or
third-party collection to receive a species name.

The [Garden Genus Registry](../../registry/genera.md) owns the *Aster* product assignment. Species
must be recorded in the [Aster Species Registry](species-registry.md) before becoming canonical
Garden identities. Aster package and collection documentation remain authoritative for
implemented membership, schemas, visual baselines, rendering, and package behaviour.
