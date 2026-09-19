# Protea

Status: **Active product direction; architecture evolving**

Protea is Garden's UI component library. It should provide reusable component models, behaviour,
interaction, accessibility, composition, and optional presentation while remaining independent
from Lilium, framework-specific runtimes, and mandatory icon or motion systems.

Protea may use a headless core and framework-neutral primitives internally, but headlessness is an
architectural foundation rather than the product identity. The product is the complete component
library: shared foundations, component families, behavioural variants, optional presentation, and
adapters for concrete consumer environments.

The [Garden Genus Registry](../../registry/genera.md) owns the *Protea* product assignment. Any
future internal species identity belongs to the [Protea Species Registry](species-registry.md).

## Responsibility

Protea may own:

- framework-neutral core primitives and shared component contracts;
- reusable component families such as buttons, sidebars, dialogs, menus, and related UI types;
- behavioural or structural variants within a component family;
- state and interaction models;
- accessibility behaviour and guarantees;
- component composition conventions;
- optional design tokens, styles, and default templates kept distinct from behavioural identity;
- framework-specific adapters and wrappers.

Its component model should preserve a clear conceptual progression:

```text
BaseComponent
`-- component type / family
    `-- behavioural or structural variant
        `-- optional presentation style
```

For example:

```text
BaseComponent
`-- SidebarComponent
    |-- StaticSidebarComponent
    `-- FloatingSidebarComponent
```

A presentation such as `Default`, `Minimal`, or `Glass` should not require a new behavioural class
merely because its visual treatment differs. Types and variants describe component identity or
behaviour; styles describe presentation unless a concrete design requirement proves otherwise.

This structure reflects Protea's botanical identity: the genus is notably variable in form while
retaining a shared identity. Protea uses that idea to describe component families that grow from
common contracts into multiple specialised forms without making any single rendering, framework,
or style the definition of the component.

## Non-goals

Protea is not:

- the Lilium component runtime;
- an icon library;
- an animation engine;
- a single mandatory visual design system;
- a reason for Lilium to require Garden UI;
- dependent on every other Garden project.

## Lilium integration

Protea remains a standalone product. A Lilium-specific adapter may make Protea components feel
native through public Lilium contracts:

```text
Protea core model ----> Protea Lilium adapter ----> Lilium public contracts
```

Lilium must not import Protea, and Protea core must not depend on Lilium implementation details.
The same boundary applies to future Svelte, React, or other framework adapters: they present Protea
through the consumer's native model without redefining Protea's component contracts.

## Aster integration

Protea may accept portable Aster definitions, a generic Aster adapter, or another compatible icon
capability. Icon support should be injectable and optional unless a concrete component contract
requires otherwise.

```text
Protea ----> optional Aster public capability
Aster -X-> Protea
```

A basic component must not acquire Aster merely because both projects belong to Garden.

## Other optional integrations

Future motion, styling, design-token, or other Garden projects may enhance Protea through explicit
public integrations. A future motion system may animate Protea components without becoming part of
their behavioural identity or a mandatory core dependency.

Core component behaviour must remain functional without animation or optional visual integrations
and should preserve accessibility, server rendering where applicable, testability, and bundle
isolation.

## Flora relationship

Protea may provide a Flora plugin for component-oriented commands such as catalogue inspection,
project integration, component generation, themes, or tokens. The plugin owns Protea semantics;
Flora owns generic command hosting and effects.

```text
protea add button
flora protea add button
```

The exact commands, package names, and integration effects remain proposed until Protea defines
their product contracts.

## Versioning

Protea versions independently from Lilium, Aster, Flora, and future Garden motion tooling.
Framework adapters and optional integrations declare their supported dependency ranges explicitly.
