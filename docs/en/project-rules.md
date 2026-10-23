# Shared Project Rules

Status: **Accepted ecosystem policy**

This document owns Garden's shared engineering and contribution rules. General rules apply to
their relevant responsibilities; the TypeScript and JavaScript profile applies to those languages.
A rule does not require a repository to invent packages, directories, classes, tooling or output
modes that its product does not need.

Acceptance of a policy, adoption by a product and automated enforcement are separate facts.
Existing source and published releases must be described according to their actual evidence.

## Contents

- [Authority, adoption and exceptions](#authority-adoption-and-exceptions)
- [Responsibilities, layers and dependencies](#responsibilities-layers-and-dependencies)
- [TypeScript and JavaScript profile](#typescript-and-javascript-profile)
- [Data, validation and effects](#data-validation-and-effects)
- [Shared authorities and generated artefacts](#shared-authorities-and-generated-artefacts)
- [JSDoc, comments and language](#jsdoc-comments-and-language)
- [Tests, fixtures and temporary evidence](#tests-fixtures-and-temporary-evidence)
- [Performance evidence](#performance-evidence)
- [CLI presentation](#cli-presentation)
- [Documentation and publication](#documentation-and-publication)
- [Human control, planning and handover](#human-control-planning-and-handover)
- [Verification and enforcement](#verification-and-enforcement)

## Authority, adoption and exceptions

The [ecosystem authority](ecosystem.md) owns product relationships and dependency direction. The
[Botanical Registry](registry/index.md) owns botanical identities, assignments and exceptions.
Product repositories own their implemented APIs, packages, runtime behaviour, tooling, workflows,
tests and releases. These rules link those subjects to their owners rather than replace them.

Repository instructions must direct contributors to this authority before relevant work. Read the
applicable rules and the product authorities needed for the task. Follow cross-repository links
for their subject; do not recursively acquire every document or create circular ownership of a rule.

Products must reference shared rules instead of maintaining complete copied rulebooks. Keep
compatible product-specific additions at their narrowest canonical product owner. Garden summaries
must follow product-owned authorities for product claims. Reciprocal links do not authorise writes,
automatic prose synchronisation or a dependency on another repository's checkout.

### Exceptions

An exception to a shared rule requires explicit maintainer approval before application. Record the
affected rule, linked to its relevant section here, the scope, semantic reason and approval at the
narrowest canonical product owner. State retained guarantees and any relevant review or removal
condition. Compatible additions are not exceptions merely because they are product-specific.

A product exception cannot silently change another product's contract or an ecosystem boundary.
A contract change requires explicit approval through its owning product; an ecosystem-boundary
change requires an explicit Garden decision. An unfinished adoption is an adoption state,
not an automatically approved exception. Do not create a second complete rulebook or a competing
exception registry.

## Responsibilities, layers and dependencies

Before moving, splitting, merging or naming a piece, assess its responsibility, data, consumers,
state, effects, dependencies and reasons to change. Use consistent structural and implementation
patterns for equivalent responsibilities; justify differences by explicit semantic reasons rather
than cosmetic uniformity.

Introduce a class, facade, manager, controller, factory or additional layer only when it owns real
state, behaviour or a domain responsibility. Neither class count nor shorter files proves a better
design. Use an existing object, function or composition when it already expresses the responsibility.

Composition is a useful starting point. Inheritance is valid when genuine specialisation or an
intentional extension preserves the base contract. A presentation style alone does not justify a
new behavioural class. Do not turn a conceptual family or variant into a required inheritance tree.

### Layer boundaries

Contracts must remain independent of concrete runtime implementation classes. Express a required
capability at the narrowest appropriate boundary. Introduce an internal bridge contract only when
it supplies a missing real responsibility or capability boundary; do not add a ceremonial bridge.

Keep policy with the domain that owns its meaning. Entrypoints adapt explicit inputs, capabilities
and results to host effects; portable domain contracts must not acquire ambient filesystem,
process, terminal, clock or network authority incidentally.

### Dependencies and distribution

Declare dependencies at their real owner. Keep private contributor tooling outside production
dependencies and public product contracts. Inspect cycles, layer direction and cross-product
integration through the relevant public boundaries. Sharing must not invert dependencies or leak
private implementation paths into a public API.

Each runtime product declares its accepted runtime, module, distribution and toolchain baseline.
Do not inherit another product's target, package graph, parser, dependency allowlist, CI platform
matrix or release procedure merely because both belong to Garden.

The publication scope for Garden product packages is `@luscious-garden`. This does not establish
a package suffix, executable, visibility, version or registry availability. Verify package names,
executables, source paths, public exports and publication claims against their actual owners.
Keep hypothetical layouts explicitly conditional and their unconfirmed names provisional.

## TypeScript and JavaScript profile

### Symbols and files

Use precise domain names and semantic kebab-case filenames that reflect the principal symbol.
Maintain consistent name families within a feature; deliberate layer distinctions are valid.
Avoid tautologies and redundant markers.

| Declaration | Symbol convention | File convention |
| --- | --- | --- |
| Public interface | No prefix, such as `ValueDefinition`. | `value-definition.contract.ts` |
| Internal interface | Prefix `I`, such as `IValueReader`. | `contracts/internal/value-reader.contract.ts` |
| Public type alias | Suffix `Type`, such as `ValueKindType`. | `value-kind.type.ts` |
| Internal type alias | Prefix `T`, such as `TParsedValue`. | `types/internal/parsed-value.type.ts` |

Contracts use `*.contract.ts`; type aliases use `*.type.ts`. Do not use `.prop.ts` or `.props.ts`.
Do not include `-type` in the base of a `*.type.ts` filename. Internal contracts and types belong
in their respective internal directories, without special internal filename prefixes or suffixes.
The interface `I` is not part of the filename.

An implementation needs no role suffix when the concept is already precise. Where distinct roles
of one concept need disambiguation, use `<concept>.<role>.ts`, with a role matching the principal
symbol: `ValueReaderAdapter` becomes `value-reader.adapter.ts`. Do not repeat the role in the base.
Roles are open domain terms, not a fixed list or a reason to add a class. A product may define
additional semantic roles at its own authority.

Internal concrete classes have no mandatory symbol prefix or suffix. An internal implementation
may share its contract's name when modules and layers distinguish them and the implementation is
not part of the public API. Do not add `Manager`, `Controller` or another role merely to avoid a
cosmetic collision.

Use `*.test.ts` for TypeScript tests and the corresponding language extension for other sources.
Product-specific declaration roles do not become mandatory filename roles for every product.

### Separation and feature organisation

Keep one principal concept per file. Separate interface/contracts from type aliases, and separate
independently imported concepts or distinct responsibilities. Do not introduce empty abstraction
layers merely to obtain more files.

Organise features around their real `api/`, `contracts/`, `types/` and `runtime/` responsibilities.
Domain types belong to their feature rather than an unrelated global type directory. Use `shared/`
only for genuinely transverse pieces with real consumers. Create only directories justified by
the implementation.

### Visibility and source style

Use native `#` members for private JavaScript runtime state and behaviour. Use TypeScript
`private constructor` when construction must be restricted; use `protected` only for deliberately
defined inheritance extension points. These are distinct responsibilities, not interchangeable
privacy spellings.

Use semicolons consistently. Each product declares the rest of its concrete source-formatting
configuration and the files it owns. Use appropriate lint and formatting checks to reinforce the
accepted style, and state their actual coverage. Widening a formatter's scope requires a reviewed
baseline and generated/fixture boundaries; writing a rule does not introduce that gate.

## Data, validation and effects

### Validation and type assertions

Validate unknown or external data at its owning boundary before treating it as a narrower domain
value. Parsing is not schema validation, and a TypeScript assertion is not runtime validation.
Use appropriate guards, normalisers and contracts; do not conceal missing guarantees with casts.

Use `as const` to retain literals where appropriate; it does not freeze runtime objects. Use
`as T` only for a guarantee already established and checked that the compiler cannot express.
Keep that assertion at the narrowest boundary and cover the guarantee with meaningful tests.
Production code must not use `as any` or chained `as unknown as T` to suppress type disagreement.

Tests may use deliberate casts to construct invalid input or inspect immutability when that intent
is explicit. Review existing casts contextually: correct the disagreement between types and runtime
without weakening the API, deleting necessary validation or duplicating an established guarantee.

### Ownership and immutability

Declare what is owned, copied, borrowed, retained or exposed, and its lifecycle. Copy retained input
where the contract requires isolation; state the guarantees of snapshots and borrowed collaborators.
Do not accidentally freeze or mutate caller-owned values. Place mutable state with its real owner.

Choose immutability for the values and boundaries it protects. Do not infer a requirement for
universal deep freezing, one product's recognised-output mechanism or an immutable authoring draft.
A shared reader does not inherit its consumers' schema or freezing policy.

### Security and host effects

Give collaborators only the capabilities required for their responsibility. Keep acquisition,
validation, deterministic planning, privileged effects and result verification distinguishable.
Report failures truthfully rather than present a partially performed operation as complete.

State the limits of each protection. Lexical path containment does not resolve filesystem links
or establish a sandbox. Reading a caller-controlled object may execute getters or proxy traps.
Validation, process termination or a resource observation does not prove isolation of hostile code.
Preserve ownership, validation, isolation and security guarantees during optimisation.

## Shared authorities and generated artefacts

### Stable shared vocabularies

Centralise a closed vocabulary, schema, discriminator, policy or reusable limit only when it is
one stable semantic authority. Place it at its narrowest real owner: a feature, a genuinely shared
package responsibility or a justified foundation contract.

Derive a type from an immutable runtime vocabulary when both express the same closed set and a
runtime authority is useful. Prefer suitable literal objects and immutable collections for string
vocabularies; use an enum when runtime identity, interoperability or nominal meaning adds value.

A class singleton requires deliberately shared state, identity or lifecycle. Do not introduce
mutable global state to avoid cheap local construction. Do not centralise incidental equal
literals, local logical paths, one-owner messages, algorithm details or an external dependency's
ABI merely because their text matches. Consumers reuse the authority; different representations
need an explicit transformation or adapter.

### Producers and ownership

Never edit generated portions manually. Change their canonical source, planner, template or
generator and regenerate. Outputs must be deterministically reconstructible. Identify the true
source or producing command in generated headers, or owning metadata where the format cannot
carry a header.

Before adding generated outputs, define ownership, cleanup boundaries and verification. Ownership
may cover selected fields or regions of a partly manual file. Preserve everything outside that
boundary, check the reviewed preimage before replacement and handle concurrent or partial failure
explicitly. Partial ownership does not make the entire file disposable or imply a global transaction.

Keep read-only drift verification separate from regeneration. A successful generation or build is
not evidence of zero drift unless the owned outputs were actually compared.

## JSDoc, comments and language

The JSDoc and source-comment rules apply to TypeScript and JavaScript. British English applies
across owned content as described below.

### JSDoc requirements

Descriptive JSDoc is mandatory for production APIs, contracts, types, classes, functions,
constructors, methods, accessors, properties, module-scoped constants and domain authorities,
whether public, internal or private, subject to the implementation exclusions below. Class members
retain their own descriptive JSDoc, including private members.

- Every required descriptive block includes `@description`.
- Include `@param` for every parameter of a documented function, constructor or method.
- Include `@returns` for every documented function, accessor and method, including those returning void.
- Include `@typeParam` for every generic parameter of a documented declaration.
- Use `@remarks` for important non-obvious details, such as internal processes, failure behaviour,
  invariants, ownership, lifecycle or design context.

Describe stable behaviour, responsibilities and relationships. Link stable symbols or canonical
documentation where useful; exclude contributor-local delivery chronology and records.

### JSDoc exceptions and ordinary comments

Imports, pure re-export barrels and tests are exempt from descriptive JSDoc requirements.

Document each operation as a whole. Local variables/constants, helper functions (arrow or function
declarations), callbacks and closures that only implement that operation are covered by its owning
declaration's JSDoc, without separate descriptive blocks. Put important internal processes, failure
behaviour and other non-obvious details in the owner's `@remarks`. This also covers implementation
callbacks supplied to module-scope operations.

Distinguish implementation details from consumable surfaces by responsibility and consumers, not
syntactic location. An object or function constructed inside an implementation may expose a surface
consumed outside that operation. Its callable contract, properties and methods require documentation
available to those consumers through the canonical contract or, where appropriate, the exposed
members themselves. This includes returned or exported objects and functions, even when their types
are inferred. Do not automatically duplicate documentation already supplied by the canonical contract.

Independently declared module-level functions/constants retain their own descriptive blocks;
using a documented function as a callback does not change that requirement. Do not extract functions,
create artificial contracts or rename implementation merely to add or avoid descriptive blocks.

Retain local JSDoc needed for JavaScript type information, such as `@type`; a type annotation alone
does not require `@description`. A separately accepted testing-documentation policy may define
requirements for its own scope.

Ordinary `//` and non-JSDoc `/* ... */` comments are forbidden in handwritten implementation,
tooling, scripts and executable configuration. Keep code self-explanatory and useful explanation
in its owning JSDoc. Ordinary comments are permitted in tests, Markdown and generated files;
change generated comments through the canonical producer. Preserve legal material and resolve
any policy conflict explicitly rather than deleting it mechanically.

### British English

Use British English in owned prose, domain identifiers, code, JSDoc, diagnostics, tests, planning
records and commit metadata. Keep word families consistent, such as `normalise`, `normaliser`
and `normalisation`. Preserve exact spellings required by external APIs, standards and tools,
including `package.json#license`, SVG `currentColor` and CSS `color`.

## Tests, fixtures and temporary evidence

Each retained test must protect an observable guarantee and fail when that guarantee changes.
Test volume is not a quality target. Use these evidence roles where applicable:

| Role | Evidence |
| --- | --- |
| Contract | Accepted behaviour and exact invariants. |
| Regression | A previously observed failure with a minimal reproducer. |
| Boundary | Architecture, validation, security, ownership or effect containment. |
| Conformance | Emitted modules, declarations, exports, executables or clean consumers. |
| Workflow | Composition across independently owned boundaries. |
| Measurement | Fixture and runner semantics rather than a product speed promise. |

Use synthetic values when any valid input proves the contract. Keep exact data when its values
define the guarantee or the real data itself is under test. Do not couple unrelated tests to a
changing built-in catalogue, but reject an empty required dataset rather than silently pass.

Tests must not depend on execution order, network access, stale build output or ambient filesystem
state. Use in-process tests for domain behaviour and subprocesses when the process, installed
executable or clean-consumer boundary is the subject. Distribution and workflow checks advertised
as independently runnable must build the outputs they inspect. Other checks must declare their
actual prerequisites rather than silently depend on stale outputs.

Consolidate or remove redundant evidence only after checking its role and failure detection.
Preserve meaningful source/distribution, unit/conformance and synthetic/real-data boundaries
unless they are demonstrably equivalent. Put permanent regressions and fixtures in their owning
suites; experiments and disposable probes belong in identified system-temporary roots.

### Temporary ownership and cleanup

Filesystem tests and experiments own their temporary roots and cleanup. Before recursive deletion
or a directory move, resolve absolute targets and verify containment in the exact intended workspace
or explicitly identified temporary root. Identify ownership exactly, not through a broad name pattern.

Inspect symbolic links and junctions without following their targets; unlink owned links safely
before deleting an owned tree. Preserve unknown temporary files, installations, user data and
sibling repositories. Recheck protected sources after cleanup. Never discard work through a
destructive Git reset or checkout-based restoration.

## Performance evidence

Keep functional correctness separate from performance observations. Compare equivalent required
work and outputs at representative scales, identify source revisions and environments, retain
complete samples and use matched baseline/candidate runs with identical controls. State cache,
warm-up, instrumentation and process-startup boundaries rather than label uncontrolled work cold.

Investigate material regressions and identical-control variation before attributing a cause.
Separate latency, resource observations and functional evidence: heap pressure is not exact
allocation count, RSS is not retained object size, and a timing profile does not establish causality.

Never weaken validation, diagnostics, ordering, ownership, immutability, isolation, security or
effect guarantees to improve timing. Explain retained trade-offs and independently approve any
contract change. Sample counts and interpretation thresholds belong to the relevant measurement
owner; do not impose one product's numbers on every project or add unstable wall-clock thresholds
to functional CI by default. Do not run an entire runtime benchmark campaign for a prose-only
change without a relevant hypothesis.

Release-to-release comparisons require matched evidence against the actual relevant published
versions. Do not present an intermediate source refactor as a published baseline or include an
unsupported release performance claim.

## CLI presentation

Garden owns these shared presentation conventions. Independent product CLIs and future Flora
hosts apply them in their applicable human and JSON result modes. Each product owns implementation,
command grammar, labels, schemas, diagnostic codes, stream selection and exit statuses.

Follow the [project directory](index.md#projects) for relevant product records. For example,
[Aster's current-source Shell documentation](https://github.com/BlueLuscious/aster/blob/master/docs/en/packages/cli/shell/index.md#presentation)
owns that product's concrete presentation, stream and status contracts. Use its release authorities
for published-package behaviour; that product link does not define the shared policy here.

This policy defines no shared executable, package, plugin ABI or presentation library. Reusable
hosting code requires real consumers and separately accepted ownership. A product CLI remains
independent of Flora; accepting a convention does not implement Flora or change published bytes.

### Human results

Use headings and one sequence entry per line, with two spaces per ownership level. Indent every
line of a nested entry. Show an applicable absent optional sequence or empty array as one indented
`(none)`, while preserving their distinction in structured data.

Preserve canonical result order and declared member order, including meaningful repeated evidence.
Do not truncate or hard-wrap complete results according to terminal width. Keep scalar/count
summaries compact when they express the complete result; do not replace unbounded lists with a
lossy compact summary or invent fields and counts.

For example, product-owned labels may present a generic result as:

```text
Items:
  example/first
    Tags:
      sample
  example/second
    Tags:
      (none)
```

The example is a presentation shape, not an executable invocation or a shared result schema.

### Human data and diagnostic evidence

Quote dynamic human values containing C0/C1 controls, DEL or Unicode line/paragraph separators
using visible JSON-compatible escapes. A newline within data appears as `\n`, distinct from a
structural line break. Preserve ordinary printable Unicode and Windows path separators.

This is a display representation, not domain validation or a general spoofing defence. Human
formatting must remain deterministic under terminal width, TTY state, ANSI availability and
redirection; it must not acquire additional capabilities to improve the display.

Present diagnostic facts by their declared semantic roles. Do not infer facts from message text,
array positions or string equality, invent missing context or suppress meaningful repetition.
Supporting facts are evidence, not suggested matches. The product owns their types and labels.

### JSON, raw artefacts and effects

JSON result mode emits one compact structured result document followed by one newline. Keep
original structured values; human escaping must not rewrite the data. Preserve the product-owned
bytes of raw artefacts rather than adding human decoration, escapes or JSON framing to them.

Presentation computes complete result content before host writes and acquires no command-execution
or filesystem capabilities. Hosts own stream effects, publication evidence and process status.
Present an operation as committed only when its actual effect is verified. Each product documents
its supported modes and framing without inventing options or guarantees from another CLI.

## Documentation and publication

### Current state and subject ownership

Documentation must describe the current state of the source or authority it covers on every
branch, including before integration. Distinguish current source from published package behaviour;
a source change does not prove registry availability or retroactively alter a release.

README files introduce the repository/product, current usage and relevant links. Guides own current
contracts and implemented workflows. Versioned release notes own changes, migrations, deprecations
and qualified comparisons. Document contract/type responsibilities and relationships at their
owner; do not reconstruct an API from ecosystem summaries or hypothetical package diagrams.

Keep one canonical owner per subject. Other documents link to it instead of copying explanations,
tables, implementation details or a full rulebook. Canonical product documentation, production code,
JSDoc and commit metadata must remain understandable without contributor-local paths or delivery
records. Stable required behaviour belongs in committable contracts, tests or canonical guides.

English under `docs/en/` is canonical. Future locales preserve its relative structure. Where real
packages exist, `docs/en/packages/` documents their set and relationships, with independent guides
under `docs/en/packages/<package>/` and authored features under
`docs/en/packages/<package>/<feature>/`, reflecting the real package/feature structure. A substantial
real service/composition may have a deeper guide under its feature; do not invent implementation
layers to mirror a documentary outline.

Where contributor tooling exists, its documentation follows the actual tooling features and owns
their responsibilities, composition, commands and checks. Architecture/governance explains shared
policy and links the tooling owner for implementation details. Product-specific domain documentation
need not invent a matching source root when its authority exists independently of code layout.

### Cross-project links

Use relative links within a repository so that navigation follows the checked-out source.
Canonical links between Garden projects always target the owning repository's `master` branch.
Author the final path and fragment from the outset, including when the corresponding work is
still local, on a feature branch or in `develop`, and the destination does not yet exist in `master`.

Do not use temporary branch or commit links for canonical navigation and schedule another change
or merge merely to retarget them after integration. A temporarily unresolved cross-project target
or fragment is an accepted integration dependency; it does not by itself block the documentary
change or require a different URL. Check the intended destination against the owning source when
available and report its current availability separately, without claiming a pending target exists.

Exact commits and verified version references still identify historical records, publications,
approvals and reproducible evidence. They do not replace the current canonical navigation owner.
A `master` link alone proves neither integration of pending work, implementation, policy
conformance nor package publication. Preserve each claim's actual source and release boundary.

### Readiness and historical evidence

Prepare current guides, README files, executable examples and reviewed release/migration notes
before final source approval, packaging or publication. Do not defer routine documentation repair
until after publishing. Later publication records may add verified registry and archive evidence.

Preserve published historical evidence and legal material unless their correction is explicitly
approved. Do not assign unreleased work to an old release or invent a version to hold it. Remove
implemented opportunities from future-facing roadmaps; keep implementation evidence at its owner.

### Approval and publication evidence

Approval identifies the reviewed source, package/version/dependency scope, notes and artefacts.
Rebuilt or changed bytes need renewed review; a checked source revision does not approve every
possible archive. Keep preparation, privileged publication and readback verification distinguishable.

Passing checks, a commit title, a push or a merge is not permission to publish. A failure requires
inspection; do not silently rebuild, alter versions/tags or overwrite previously approved evidence.
Each product owns its release process, registry authority, compatibility and publication records.

## Human control, planning and handover

### Scope and permissions

Inspect instructions, worktree state and relevant authorities before editing. Preserve unrelated
or maintainer-owned changes, and stop for clarification when concurrent changes affect the work.
Ask before changing an accepted public contract, ecosystem boundary, ownership rule or decision.
Report significant unrelated findings without silently expanding scope.

Permissions are scoped to the operation and owning repository. Reading a sibling checkout or an
authority does not authorise writing there. Branch creation/switching and changes to repository
workflows require explicit authorisation; an approved name alone does not execute the operation.
Do not install dependencies or create automation, packages or a tooling framework merely to
complete documentary maintenance.

### Planning and closure

Before starting an approved delivery or phase, review its index, outstanding work and dependencies.
Complete prerequisites or obtain and record an explicit exception; report skipped decisions,
contracts or checks. Do not start a dependent phase or another delivery implicitly.

Keep each delivery record limited to its index and phase Markdown files. Use the owning
repository's declared numbering, storage and Git visibility, and archive completed deliveries
according to that convention. Record concise decisions, checks and reviewed, conserved, corrected
and pending outcomes in the owning phase, without auxiliary scripts, copied data or raw logs.

Keep statuses and checkboxes aligned with actual completion. Local verification is not integration;
integration is not publication. Agree applicable gates before execution and check exact reviewed
and integrated revisions when integration is in scope, including actual applicable CI jobs.

Once scoped work, required decisions, applicable verification and reviewed integration within the
approved scope are complete, close and archive unless an explicit hold remains. Do not request
another administrative approval solely for closure. Archival authorises no commit, branch change,
merge, publication, cross-repository work or subsequent delivery.

### Commit proposals and handover

The maintainer performs commits; agents must not execute `git commit`. Other delivery operations
remain subject to the repository's explicit permissions and prohibitions. Propose Conventional
Commit titles with an appropriate scope and a short imperative description in British English.

Present `Title` and `Description` as separate labelled `text` code blocks. Use a brief imperative
list in the description. Each commit is one coherent logical unit; separate independent documentary,
tooling and functional changes. For multiple commits, state exact file membership. Metadata must
not mention machine-local files or delivery records. Branch name proposals also use copyable
`text` blocks and the target repository's actual conventions.

State the outcome first, then relevant checks, limits and remaining work. Explain whether earlier
commit proposals still cover the retained diff. Local instructions may impose stricter execution
limits; no proposal or successful check grants delivery permission.

## Verification and enforcement

Review the complete retained diff and affected consumers. For documentary changes, check targets
and fragments, terminology, current/proposed status, authority boundaries, copied claims and
relevant files outside the canonical documentation tree, then run `git diff --check`. Check new,
untracked or local files separately where an ordinary Git diff does not include them.

An accepted rule is not proof of its enforcement. Each product must identify its actual commands,
configuration, exclusions and human-review responsibilities. A lint check does not prove domain
design, a type check does not validate unknown runtime data, and a link/hierarchy check does not
prove prose truth, completeness or publication status.

Report what passed, what was not run, what is unavailable and the limits of the audit. Never
fabricate a build, test matrix, workflow or successful integration. These rules add no checker or
CI job. If a repository has no executable suite or CI, use its agreed documentary checks rather
than treating absent checks as green. Product-owned automation and permissions remain independent.
