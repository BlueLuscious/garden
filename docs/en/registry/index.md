# Garden Botanical Registry

Status: **Canonical botanical naming authority**

The Botanical Registry governs the botanical identities used, reserved, or considered by Garden.
It records naming relationships and their rationale without owning package APIs, implementation
details, visual specifications, runtime behaviour, or release contracts.

## Naming Model

```text
Garden product or project       ----> botanical genus
Named internal product identity ----> species of that genus
```

### Genus level

A major Garden product should normally use a botanical genus whose meaning supports the product's
role. A genus assignment does not itself justify creating a project. Used, reserved, and candidate
genus identities belong to the [Garden Genus Registry](genera.md).

### Species level

Species belonging to an assigned genus may name meaningful internal identities within that
product. Species form a semantic namespace; they are not a requirement to rename every package,
class, component, or implementation detail.

A species is assigned only when the concept belongs clearly to the product, has durable identity,
benefits from the botanical language, and belongs to the assigned genus. Each product owns its
species registry:

| Product | Species authority |
| --- | --- |
| Aster | [Aster Species Registry](../products/aster/species-registry.md) |
| Lilium | [Lilium Species Registry](../products/lilium/species-registry.md) |
| Protea | [Protea Species Registry](../products/protea/species-registry.md) |
| Flora | [Flora Species Registry](../products/flora/species-registry.md), explicitly not applicable |

### Taxonomic integrity

Canonical assignments must preserve the taxonomic relationship represented by the name.
Historical classifications, synonyms, reclassifications, or ambiguous common names must be
documented before acceptance. Species counts are reference context, not software contracts.

### Deliberate exceptions

A botanical term outside genus rank may be accepted when its meaning has an unusually strong
architectural relationship with a product. Every exception is recorded in the
[Garden Genus Registry](genera.md). Flora is the current accepted exception.

## Status Language

| Status | Meaning |
| --- | --- |
| Used | Canonical identity assigned to an active or accepted Garden product or product concept. |
| Reserved | Held for a specific future product or domain. |
| Candidate | Considered suitable but not assigned. |
| Proposed | Candidate species assignment awaiting product-level acceptance. |
| Retired | Intentionally removed from active use. |

## Authority Boundary

The genus registry decides which botanical identities belong to Garden products. Product species
registries decide which species identify durable concepts inside their owning product. Product
documentation remains authoritative for implementation, behaviour, visual rules, membership,
packages, and releases.
