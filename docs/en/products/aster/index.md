# Aster

Status: **Active project; public packages published; source development continues**

Aster is Garden's portable icon platform. It owns portable icon and collection definitions,
curated artwork, standalone SVG rendering and explicit catalogue workflows. Optional source
adoption remains a private capability.

The [Aster package documentation](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages)
owns implemented APIs, package boundaries and workflows. Its
[source and published-version guidance](https://github.com/BlueLuscious/aster/blob/develop/docs/en/index.md#source-and-published-versions)
distinguishes current guides from released behaviour; later source changes must not be attributed
automatically to a registry installation.

## Responsibility

Aster owns:

- portable, target-independent icon and collection definitions;
- immutable construction, validation and domain identity;
- canonical TypeScript-first artwork and collection membership;
- standalone framework-independent SVG rendering;
- optional private adoption of acquired external sources;
- host-neutral command composition and a standalone CLI.

## Current package boundary

| Package | Ecosystem responsibility | Distribution |
| --- | --- | --- |
| [`@luscious-garden/aster-core`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/core) | Portable definitions and construction. | Public; published. |
| [`@luscious-garden/aster-icons`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/icons) | Canonical artwork and discovery. | Public; published. |
| [`@luscious-garden/aster-svg`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/svg) | Standalone SVG rendering. | Public; published. |
| [`@luscious-garden/aster-cli`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/cli) | Command composition and standalone hosting. | Public; published. |
| [`@luscious-garden/aster-import`](https://github.com/BlueLuscious/aster/tree/develop/docs/en/packages/import) | Adoption of acquired external sources. | Private workspace package. |

Aster's [12 October 2026 publication record](https://github.com/BlueLuscious/aster/blob/08dca1d50cf48bfe68795e300fc054c4a8c86b66/docs/en/project/publications/2026-10-12.md)
records the stable public-package combination verified on that date. Package histories and
publication records own released versions, migrations and registry evidence; the current-source
guides may describe later changes. Private Import is not part of that published combination.

## Current visual baseline

Amellus is Aster's active foundational collection. Its
[collection authority](https://github.com/BlueLuscious/aster/tree/develop/docs/en/collections/amellus)
owns curatorial identity, provenance, visual rules and acceptance, and links the product-owned
membership and distribution authorities. Collection lifecycle is separate from package publication.

## Authoring and rendering

Portable definitions remain usable without the CLI, ingestion services or a Garden framework.
The product-owned package guides linked above own authoring, rendering and adoption workflows,
as well as the internal dependency graph.

## Lilium and Protea relationships

A future Lilium adapter belongs to Aster and depends on public contracts from both products:

```text
Future Aster Lilium adapter ----> Aster public contracts
                           `---> Lilium public contracts
Protea ------------------------> optional Aster public capability
Aster -X-> Protea
```

The adapter does not make portable Aster definitions depend on Lilium. Protea decides whether and
how to accept icons; Aster remains usable independently and owns no Protea-specific semantics.

## Flora relationship

Aster separates host-neutral command composition from its private standalone Node shell within
`@luscious-garden/aster-cli`. Its `aster` executable remains independently usable.

[Command-set extraction and Flora integration](https://github.com/BlueLuscious/aster/blob/develop/docs/en/future-capabilities.md#command-set-extraction-and-flora-integration)
remain a product-owned conditional proposal. Command-set extraction requires a real independent
consumer. A Flora adapter additionally requires a stable public plugin boundary and a demonstrated
integration. Neither the separate command package nor the Flora adapter is implemented.

A standalone host or future Flora host would present or publish Aster plans through explicit
capabilities. Process and filesystem authority remain outside the command domain. Aster's
[Shell guide](https://github.com/BlueLuscious/aster/blob/develop/docs/en/packages/cli/shell/index.md)
owns current invocation syntax; Garden does not establish a composed Flora command contract.

## Versioning

Aster versions independently from Lilium, Protea and Flora. Future adapters declare compatibility
with the public contracts they consume. Artwork additions, package changes and framework releases
do not require synchronised Garden versions.

## Botanical collection identity

The [Garden Genus Registry](../../registry/genera.md#aster) owns the product assignment; the
[Aster Species Registry](species-registry.md) owns its botanical collection assignments. Botanical
assignment does not define collection visuals, membership or package behaviour.
