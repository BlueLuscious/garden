# Flora

Status: **Accepted product direction; implementation and ABI proposed**

Flora is Garden's prospective headless multi-ecosystem CLI platform. It should provide generic
command hosting and explicit capabilities while Lilium, Protea, Aster, and future projects retain
their own domain commands through plugins or adapters.

Flora's identity and ecosystem role are accepted. Its repository, package layout, plugin ABI,
runtime contracts, and implementation remain uncommitted until real consumers provide evidence.

The [Garden Genus Registry](../../registry/genera.md) records Flora's deliberate non-genus
exception. The [Flora Species Registry](species-registry.md) explains why species assignments are
not applicable.

## Purpose

Flora exists to prevent every Garden project from rebuilding generic CLI infrastructure while
preserving independent product executables and ownership.

The same domain command implementation should eventually support both forms:

```text
aster export icon aster/camera
flora aster export icon aster/camera
```

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
Aster repository -----> @aster/flora adapter
Flora repository -----> generic contracts, hosts, and optional capabilities
```

Flora must not depend on Lilium, Protea, or Aster. A project adapter may depend on Flora's public
plugin contract and its own project's public command boundary.

## Aster integration

Aster provides the first concrete architecture for host-neutral command reuse, but its current
`@aster/cli` remains a complete standalone product. A future split is conditional:

```text
@aster/commands ----> Aster structured commands and immutable plans
@aster/cli ---------> @aster/commands + default catalogue + standalone Node host
@aster/flora -------> @aster/commands + @flora/core adapter
```

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
- non-interactive, CI, and structured output guarantees;
- plugin compatibility and version negotiation;
- package loading, installation, discovery, and trust policy;
- the evidence threshold for independent extraction.
