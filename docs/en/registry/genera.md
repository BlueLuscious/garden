# Garden Genus Registry

Status: **Canonical genus naming authority**

This registry records genus-level and exceptional botanical identities used, reserved, or
considered by Garden. The [Botanical Registry](index.md) owns the shared naming model, status
language, and relationship between this registry and product-owned species registries.

## Registered product identities

### Lilium

-   **Status:** Used
-   **Assigned Project:** Frontend framework
-   **Taxonomic Rank:** Genus
-   **Family:** Liliaceae
-   **Reference Species Count:** Approximately 100
-   **Taxonomic Reference:** [Kew Plants of the World Online](https://powo.science.kew.org/taxon/urn%3Alsid%3Aipni.org%3Anames%3A30009317-2/general-information)
-   **Meaning:** Foundation, persistence, emergence and structured growth.
-   **Suitable For:** Frontend framework, foundational application platform.
-   **Reason:** *Lilium* grows from a persistent bulb composed of overlapping
    scales, from which its above-ground shoot emerges. The identity reflects a
    frontend framework whose foundational mechanisms -- reactivity, component
    and template composition, rendering, scheduling, lifecycle, context,
    routing, and compiler or source-language capabilities when implemented --
    support the applications built above them while remaining distinct from
    those applications.
-   **Branding:** Short, scientific, memorable and appropriate for a
    software product.
-   **Species Mapping:** Available for future meaningful internal
    identities; none is currently canonical.

### Protea

-   **Status:** Used
-   **Assigned Project:** UI component library
-   **Taxonomic Rank:** Genus
-   **Family:** Proteaceae
-   **Reference Species Count:** 107 accepted species
-   **Taxonomic Reference:** [Kew Plants of the World Online](https://powo.science.kew.org/taxon/urn%3Alsid%3Aipni.org%3Anames%3A331879-2)
-   **Meaning:** Diversity of form, variation and specialised expression from a shared identity.
-   **Suitable For:** UI component libraries, reusable component systems, component families and
    variants.
-   **Reason:** *Protea* is a highly variable genus whose name refers to Proteus and his ability to
    change form. The identity fits a component architecture in which shared foundations produce
    component families, behavioural or structural variants, and multiple presentations without
    losing their common contracts.
-   **Branding:** Short, scientific, memorable and appropriate for a software product.
-   **Species Mapping:** Available for future meaningful internal identities; none is currently
    canonical.

### Aster

-   **Status:** Used
-   **Assigned Project:** Portable icon platform
-   **Taxonomic Rank:** Genus
-   **Family:** Asteraceae
-   **Reference Species Count:** 151 accepted species
-   **Taxonomic Reference:** [Kew Plants of the World Online](https://powo.science.kew.org/taxon/urn%3Alsid%3Aipni.org%3Anames%3A331068-2)
-   **Meaning:** Star, visual recognition, orientation and coherent visual language.
-   **Suitable For:** Icon systems, portable visual symbols, icon collections and visual language.
-   **Reason:** The name *Aster* derives from the Greek word for star, referring to the
    star-like appearance of its radiate flower heads. Those heads are themselves composed of
    multiple florets arranged into one immediately recognisable visual whole. The identity fits
    an icon platform in which structured geometry forms compact visual symbols used for
    recognition, communication and orientation, while related symbols can be organised into
    coherent collections.
-   **Branding:** Short, scientific, memorable and directly associated with a simple,
    recognisable visual form.
-   **Species Mapping:** Species of *Aster* may identify official Aster icon collections.

### Flora

-   **Status:** Used
-   **Assigned Project:** Shared multi-project CLI platform
-   **Taxonomic Rank:** Botanical collective term; deliberate exception
-   **Meaning:** The plant life of a place considered collectively rather than as one genus or
    species.
-   **Suitable For:** Cross-project command hosting, shared ecosystem tooling and explicit
    composition of project-owned CLI capabilities.
-   **Reason:** *Flora* names the collective botanical level rather than one individual taxon.
    That distinction matches a CLI platform whose purpose is not to own the domain of Lilium,
    Protea, Aster or any future Garden product, but to host and compose tooling contributed by
    those independent projects. The name therefore describes Flora's ecosystem-wide scope rather
    than a particular implementation technology or command set.
-   **Branding:** Short, botanical and immediately connected to Garden as a collective ecosystem.
-   **Species Mapping:** Not applicable because Flora is not a genus.
-   **Exception:** Accepted outside the default genus-to-product convention because the collective
    botanical meaning is the architectural reason for the product's identity.

## Reserved identities

### Iris

-   **Status:** Reserved
-   **Assigned Project:** Facial recognition
-   **Taxonomic Rank:** Genus
-   **Family:** Iridaceae
-   **Reference Species Count:** 320 accepted species
-   **Taxonomic Reference:** [Kew Plants of the World Online](https://powo.science.kew.org/taxon/urn%3Alsid%3Aipni.org%3Anames%3A326330-2)
-   **Meaning:** Vision, wisdom and communication.
-   **Suitable For:** Computer vision, imaging.
-   **Reason:** The iris is visually tied to recognition and sight.
-   **Branding:** Short, scientific, memorable and appropriate for a
    software product.

## Candidate identities

### Cosmos

-   **Status:** Candidate
-   **Assigned Project:** Prospective package manager
-   **Taxonomic Rank:** Genus
-   **Family:** Asteraceae
-   **Reference Species Count:** 36 accepted species
-   **Taxonomic Reference:** [Kew Plants of the World Online](https://powo.science.kew.org/taxon/urn%3Alsid%3Aipni.org%3Anames%3A8410-1)
-   **Meaning:** Order, harmony and an organised whole.
-   **Suitable For:** Package management, dependency resolution, registries, lockfiles,
    workspaces and package distribution.
-   **Reason:** The genus name derives from Greek *kosmos*, associated with order and harmonious
    arrangement. That meaning fits a package manager whose central responsibility would be to
    organise packages, versions, dependency constraints and installation state into a coherent,
    reproducible dependency graph. The assignment remains a candidate until the package manager's
    actual product scope and architecture are defined.
-   **Branding:** Short, memorable and capable of representing an ordered package universe without
    depending on a specific runtime or programming language.
-   **Species Mapping:** Deferred unless Cosmos becomes a canonical Garden product.

### Verbena

-   **Status:** Candidate
-   **Assigned Project:** Unassigned
-   **Taxonomic Rank:** Genus
-   **Family:** Verbenaceae
-   **Reference Species Count:** 69 accepted species
-   **Taxonomic Reference:** [Kew Plants of the World Online](https://powo.science.kew.org/taxon/urn%3Alsid%3Aipni.org%3Anames%3A330551-2)
-   **Meaning:** Creativity, inspiration and transformation.
-   **Suitable For:** Animations, motion, creative tooling.
-   **Reason:** Represents movement and creative expression.
-   **Branding:** Short, scientific, memorable and appropriate for a
    software product.


## Genus Naming Decisions

### Genus names for Garden products

**Decision:** Garden products should normally use botanical genera.

**Reason:** A genus gives each product an independent botanical identity and a natural species
namespace for meaningful identities within it.

**Status:** Accepted

### Flora exception

**Decision:** Flora is accepted as a Garden product identity despite not being a genus.

**Reason:** Its collective botanical meaning directly fits a shared CLI platform that composes
tooling across the ecosystem.

**Status:** Accepted

## Open Questions

- Should Cosmos become the canonical package-manager identity once that product's scope and
  architecture are defined?
- Should historical botanical synonyms remain valid aliases after a canonical genus assignment
  changes taxonomic placement?
