# Station Core Runtime

Nova Station is moving core-first.

The first serious proof is not another shell screen or window effect. It is a headless runtime that can understand a Project, invoke a capability, track asynchronous work, record accepted results, and route them to available outlets.

The compositor remains important visual and compatibility infrastructure. It is not the state or execution core.

## Canonical Flow

```text
source event
    -> Station Runtime
    -> Project context
    -> optional agent interpretation
    -> ProgramObject selection
    -> execution placement
    -> asynchronous invocation lifecycle
    -> Typed Objects / artifacts / progress / errors
    -> Station validation and acceptance
    -> event log
    -> reducer and projection
    -> delivery routing
    -> compatible outlet or graceful fallback
```

A flow can begin with user input, schedule, repository change, synchronization, network event, hardware signal, system startup, or agent observation.

Agent interpretation is optional. State acceptance and routing remain Station responsibilities.

## Runtime Contracts

### Project State

Project state is immutable and changes through accepted events or patches.

The runtime must be able to reconstruct it from a snapshot, ordered event log, and referenced artifacts.

### Typed Object

A Typed Object is a clean value or reference plus Station-owned metadata:

- type and version;
- semantic roles;
- capabilities and methods;
- provenance;
- permissions;
- agent-readable description;
- replay and storage behavior.

Examples include code blocks, media references, messages, notifications, command results, artifacts, patch proposals, outlet descriptors, and executable program references.

### ProgramObject

A ProgramObject is an executable Typed Object reference. It declares:

- accepted input types;
- emitted output types;
- execution requirements;
- permissions;
- effect mode, determinism, and replay behavior;
- timeout, cancellation, and replay behavior.

Programs do not directly mutate Project state. They return results for Station to validate and accept.

Execution metadata uses separate axes:

- effect mode: `pure` or `effectful`;
- determinism: `deterministic` or `non_deterministic` with pinned version, inputs, and context;
- replay behavior: `recompute_allowed` or `recorded_result_required`.

Model-backed is provider metadata, not an execution class. Agentic behavior may be deterministic or model-backed.

### Station Runtime Node

A node advertises capabilities relevant to execution and outlets:

- available ProgramObjects and connectors;
- models, CPU, GPU, memory, and hardware;
- physical and software outlets;
- load and availability;
- trust, permissions, and policy constraints;
- network and locality context.

There is no required primary host.

### Outlet

An outlet is a focused endpoint or adapter with semantic roles and capabilities.

Physical examples include displays, keyboards, microphones, speakers, touch screens, sensors, and controllers.

Software examples include code editor, media player, log presenter, notification handler, voice/audio adapter, command surface, and legacy application host.

## Execution Placement Is Separate From Delivery

Consider image generation requested from a phone.

```text
phone
    -> InvocationRequested
    -> Station selects trusted GPU workstation
    -> workstation generates image artifact
    -> Station validates and accepts result
    -> preview delivered to phone
    -> full image delivered to tablet or TV
```

The phone is the source node. The workstation is the executor. The phone, tablet, or TV may be delivery outlets.

Placement policy considers capability, permissions, trust, load, cost, locality, network conditions, and Project policy.

Delivery policy considers object roles, outlet capabilities, user context, Project configuration, and fallback options.

The two decisions must not collapse into one.

## Asynchronous Invocation Lifecycle

Program execution is not modeled as a blocking product-level function call.

```text
InvocationRequested
    -> InvocationAccepted / InvocationRejected
    -> ExecutionPlaced
    -> ExecutionStarted
    -> Progress / OutputChunk / ArtifactCreated / LogEmitted
    -> ExecutionSucceeded / ExecutionFailed / ExecutionCanceled / ExecutionTimedOut
    -> ResultAccepted
```

Durable state stores invocation ID, source and executor nodes, lifecycle status, provenance, progress, timeout, cancellation, accepted outputs, and artifact references.

This allows immediate tasks, long-running model work, streaming commands, remote queues, retries, parallel execution, and late completion to use one model.

## Events, Artifacts, And Replay

The first durable event log is planned as inspectable JSON Lines.

Payload storage is hybrid:

- reducer and routing metadata stays inline;
- small values may stay inline when useful;
- large outputs become content-addressed artifact references with hashes, metadata, and previews.

Pure deterministic work may be recomputed only with pinned versions and inputs.

Work marked `recorded_result_required` is stored. Replay restores accepted stdout, stderr, exit code, media, model output, or other artifacts instead of repeating the external action.

This is necessary for restore, explanation, Time Machine, synchronization, and agent accountability.

## Graceful Routing Failure

A valid object can exist without a currently compatible outlet.

For example, a connector can return a `MediaRef` while the active Project has no video outlet.

Station retains the object and may offer:

- text summary;
- audio-only playback;
- queue for later;
- temporary outlet attachment;
- Project switch;
- compatibility surface.

Unhandled presentation is a modeled routing state, not a crash and not permission to discard the result.

## First Headless Prototype

The first implementation should stay local and in-memory where practical while preserving distributed contracts.

It should include:

- Typed Object descriptors;
- ProgramObject execution contracts;
- Station Runtime node and execution capability descriptors;
- execution placement matcher;
- invocation/task descriptors and lifecycle events;
- role, capability, and outlet descriptors;
- delivery routing matcher;
- event envelope and in-memory event log;
- deterministic reducer and projection;
- stub agent selector;
- pure text transform program;
- effectful shell-command program;
- text, log, error, and debug outlets.

## Acceptance Checks

The prototype is meaningful when it can prove all of the following without GUI dependencies:

1. A source event selects and invokes a ProgramObject through Station.
2. Placement policy chooses a compatible executor descriptor, even if the first executor is local.
3. Invocation lifecycle events are recorded in order.
4. Program output cannot mutate Project state directly.
5. Accepted output creates deterministic reduced state and outlet projections.
6. Replay reconstructs the same state.
7. Replay does not repeat the effectful shell command.
8. Missing outlets produce an explainable fallback state.
9. The same contracts can later attach visual, voice, appliance, or compatibility presentations.

## Not In The First Proof

- production cloud synchronization;
- real multi-node transport;
- full agent provider integration;
- final package and outlet repositories;
- production security sandboxing;
- complete Board or Stack UI;
- production compositor integration;
- final artifact persistence.

The first proof is intentionally small. Its job is to validate the operating model before presentation complexity grows around it.

Read the [Vision](VISION.md), [Stories](STORIES.md), [Appliance Profiles](APPLIANCE_PROFILES.md), or [Public Roadmap](ROADMAP.md).
