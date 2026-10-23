# Flora

Status: **Accepted product direction; implementation and ABI proposed**

Flora is Garden's prospective headless multi-ecosystem CLI platform. It should provide generic
command hosting and explicit capabilities while Lilium, Protea, Aster, and future projects retain
their own domain commands through plugins or adapters.

Flora's identity and ecosystem role are accepted. Its repository boundary, package layout, plugin
ABI, runtime contracts and implementation remain proposed until real consumers provide evidence.

The [Garden Genus Registry](../../registry/genera.md) records Flora's deliberate non-genus
exception. The [Flora Species Registry](species-registry.md) explains why species assignments are
not applicable.

## Purpose

Flora exists to prevent every Garden project from rebuilding generic CLI infrastructure while
preserving independent product executables and ownership.

Independent product executables and a future Flora composition should be able to invoke the same
project-owned command capability. Aster's
[CLI guide](https://github.com/BlueLuscious/aster/tree/master/docs/en/packages/cli) owns its actual
commands and invocation syntax. No composed Flora invocation is established here.

The executable identity belongs to each composition. Flora owns generic hosting; the project
plugin owns domain semantics.

## Layered boundary

Flora must not place every CLI concern in one core package. The intended responsibility split is:

```text
Flora contracts and kernel
|-- command and plugin contracts
|-- namespaced dispatch
|-- structured invocation and result boundaries
|-- diagnostics and capability contracts
`-- deterministic composition

Flora hosts
|-- argv and environment acquisition
|-- terminal streams and exit status
|-- filesystem and process implementations
`-- executable-specific presentation

Optional Flora capabilities
|-- prompts
|-- configuration
|-- templates and scaffolding
`-- testing support
```

Only contracts and deterministic orchestration belong in the host-neutral foundation. Node,
terminal, filesystem, process, clock, network, and interactive behaviour require explicit hosts or
capabilities.

Applicable CLI result modes follow Garden's [shared presentation rules](../../project-rules.md#cli-presentation).
Flora may eventually provide reusable hosting code that implements those conventions; it does not
own their ecosystem policy. Product commands and concrete result contracts remain product-owned.

## Plugin model

A Flora plugin contributes a stable project namespace, command metadata, structured command
execution, and any explicitly required capability contracts. It must not assume which executable
mounted it.

```text
Flora host
|-- lilium plugin ----> Lilium domain capabilities
|-- protea plugin -----> Protea domain capabilities
`-- aster plugin -----> Aster domain capabilities
```

The exact plugin contract remains open. Automatic discovery, third-party execution, compatibility
ranges, conflict resolution, installation, and trust policy must be designed before Flora loads
arbitrary packages.

## Project plugin ownership

Project-specific integrations should remain with their products:

```text
Lilium repository ----> Lilium Flora plugin
Protea repository -----> Protea Flora plugin
Aster repository -----> Aster Flora adapter
Flora repository -----> generic contracts, hosts, and optional capabilities
```

Flora must not depend on Lilium, Protea, or Aster. A project adapter may depend on Flora's public
plugin contract and its own project's public command boundary.

## Aster integration

Aster already provides host-neutral command composition within `@luscious-garden/aster-cli`,
alongside its standalone `aster` executable. Its
[product-owned CLI authority](https://github.com/BlueLuscious/aster/tree/master/docs/en/packages/cli)
describes its implemented boundaries. A future split is conditional:

```text
Aster structured commands ----> Aster domain operations and plans
Standalone Aster CLI ---------> structured commands + catalogue + Node host
Aster Flora adapter ----------> structured commands + Flora public contracts
```

The proposed separation does not establish additional packages. Aster's
[extraction proposal](https://github.com/BlueLuscious/aster/blob/master/docs/en/future-capabilities.md#command-set-extraction-and-flora-integration)
owns its conditional package direction. Eventual public package names use the
[Garden publication scope](../../project-rules.md#dependencies-and-distribution); suffixes and
boundaries remain provisional.

Flora would route the `aster` namespace and provide host capabilities. It would not import Aster
implementation paths or duplicate Aster command behaviour.

## Progressive implementation

1. Define one real project command set with explicit host boundaries.
2. Identify generic contracts shared by a second independent consumer.
3. Establish the smallest Flora kernel and host capability model.
4. Implement explicit project adapters without automatic package discovery.
5. Extract Flora into an independent repository when ownership, reuse, and versioning justify it.
6. Add an ecosystem executable only after namespace, compatibility, conflict, and trust semantics
   are stable.

Co-location beside an initial consumer is permitted as an incubation strategy, but it does not
make Flora part of that product's domain or public runtime.

## Non-goals

Flora is not:

- a container for project domain logic;
- a replacement for public project APIs;
- a required application runtime dependency;
- an automatic untrusted plugin loader by default;
- a reason to synchronise Garden release cycles;
- a mandatory repository before genuine cross-project reuse exists.

## Decisions still required

- the minimal plugin and command contracts;
- namespace and command-conflict rules;
- host capability ownership and lifecycle;
- product-specific non-interactive, CI and structured-output contracts within the shared
  presentation rules;
- plugin compatibility and version negotiation;
- package loading, installation, discovery, and trust policy;
- the evidence threshold for independent extraction.
