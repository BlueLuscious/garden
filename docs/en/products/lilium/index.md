# Lilium

Status: **Active project; architecture evolving**

Lilium is Garden's frontend framework. It owns the foundational mechanisms required to build
frontend applications while remaining independent from optional Garden UI, icon, motion, and
tooling products.

The [Garden Genus Registry](../../registry/genera.md#lilium) owns the *Lilium* product assignment
and its architectural rationale. Any future internal species identity belongs to the
[Lilium Species Registry](species-registry.md).

## Responsibility

Lilium may own framework-level concerns such as:

- reactivity and ownership;
- component and template composition;
- rendering targets and scheduling;
- compiler and source-language support;
- application lifecycle and context;
- routing and framework-specific development capabilities when implemented.

Its package structure must follow real implementation boundaries rather than a predetermined
framework checklist.

## Non-goals

Lilium is not:

- a UI component library;
- an icon collection;
- a design system;
- a mandatory container for every Garden project;
- the owner of project-specific adapters supplied by Protea or Aster.

In particular:

```text
Lilium -X-> Protea
Lilium -X-> Aster
```

Applications must be able to use Lilium without installing either product.

## Integration boundary

Lilium should expose intentional public extension contracts that permit third-party and Garden
integrations without implementation-path imports.

```text
Future Protea Lilium adapter ----> Protea public contracts
                            `---> Lilium public contracts
Future Aster Lilium adapter -----> Aster public contracts
                            `---> Lilium public contracts
```

The adapter belongs to the integrating product. Lilium remains independent and does not privilege
Garden integrations by making them mandatory.

## Flora relationship

Lilium may provide a Flora plugin containing Lilium-specific commands such as project creation,
development, build, generation, diagnostics, or upgrade workflows. Flora must own generic command
hosting; the plugin must own Lilium domain knowledge.

The same command implementation should eventually support both:

```text
lilium build
flora lilium build
```

These illustrate a future composition, not established executable or command contracts.

Flora may be incubated beside a first consumer, but co-location does not transfer ownership of the
generic platform to Lilium. Extraction requires reuse by another real project and a stable plugin
boundary.

## Versioning

Lilium versions independently from Protea, Aster, and Flora. Integrations declare supported public
contract ranges and cannot force synchronised Garden releases.
