# Nova Station Vision

Project-first AI operating environment.

Be focused.

## Thesis

Nova Station is not a desktop redesign, window manager, launcher, or chatbot attached to existing applications.

It starts from a different hierarchy:

```text
not apps first
not windows first
not screens first

projects first
state first
agents first
outlets by role
```

The goal is an operating environment where the Project is the durable unit, agents are native participants, devices contribute explicit capabilities, and presentation adapts to context.

## The Human Problem

Consider parallel API and frontend work.

Both contexts are spread across terminal tabs, browser tabs, code editors, logs, tasks, chats, and agents. The operating system sees processes and windows. The user remembers which pieces form each Project and reconstructs the context manually.

Nova Station treats that missing Project context as a system responsibility.

API and frontend can be separate Projects even when they reuse the same tools. Switching Project restores the relevant code, logs, browser content, tasks, agents, status, outlet roles, and presentation.

The user chooses the work. Station restores the environment around it.

## Product Model

```text
Station -> Command Center -> Project -> Presentation -> Outlets
                         Agents alongside every level
```

**Station** coordinates identity, nodes, Projects, policies, objects, events, and global capabilities.

**Command Center** summarizes Projects and helps the user decide where attention is needed.

**Project** is an isolated living context with state, history, agents, connectors, typed objects, tasks, code, media, logs, notifications, device roles, and restore points.

**Presentation** turns Project state into a context-appropriate experience. It may be visual, audio, spatial, embedded, or mixed.

**Outlets** are role-capable endpoints. They can display, edit, speak, listen, notify, control hardware, host legacy surfaces, accept input, or perform another focused role.

Agents are cross-cutting participants. They are not a leaf node or a single chat window.

## Projects Are Not Workspaces

A Project is not defined by a directory, repository, application set, or display layout.

Those things can belong to a Project, but none of them is the Project itself.

A Project owns or references:

- durable state and ordered history;
- accepted outputs and artifacts;
- agents, permissions, and memory;
- connectors and executable capabilities;
- typed objects and tasks;
- presentation and routing policy;
- device and outlet assignments;
- restore points and synchronization state.

This makes a Project portable across presentations and machines without pretending that arbitrary process memory can be moved perfectly.

## Native Agents

Agents should understand Project state directly instead of inferring it from a screenshot or pile of windows.

An agent may:

- observe permitted Project events and task progress;
- summarize status at Command Center or Project level;
- select a connector or ProgramObject;
- propose a state change;
- request approval;
- start an allowed invocation;
- interpret and route results;
- explain provenance, failures, and uncertainty.

Work does not have to begin in chat. A source event may come from user input, system startup, schedule, repository change, synchronization, network activity, hardware, or another agent observation.

Observation does not automatically grant authority. Permissions, approval policy, invocation lifecycle, and accepted state changes remain explicit.

## Typed Objects And Programs

Programs and connectors exchange self-describing Typed Objects rather than owning every interface.

Examples include:

```text
CodeBlock
MediaRef
ChatMessage
Notification
CommandResult
ArtifactRef
StatePatchProposal
ProgramObject
```

Station knows or can restore metadata describing type, version, roles, capabilities, provenance, permissions, methods, agent-readable meaning, and replay behavior.

A ProgramObject is an executable Typed Object reference. It declares accepted inputs, emitted outputs, execution class, permissions, and requirements.

Programs do not mutate Project state directly. They return objects, artifacts, results, or patch proposals. Station validates and accepts events through the Project state boundary.

## Two Routing Decisions

Nova Station separates execution placement from result delivery.

### Execution Placement

Station decides where a ProgramObject should run based on capabilities, permissions, policy, load, network context, installed models or connectors, and availability.

The interaction device is not automatically the executor.

```text
phone request
    -> trusted GPU workstation executes image generation
    -> ImageObject / ArtifactRef enters Project state
```

Station may use the local node, a stronger remote node, a queue, degraded local execution, or several nodes in parallel.

### Delivery Routing

After output is validated and accepted, Station decides where it should go based on object roles, Project policy, current context, and outlet capabilities.

```text
accepted ImageObject
    -> preview on phone
    -> full image on tablet or TV
    -> artifact retained in Project history
```

The source node, executor node, and delivery outlet can all be different.

## Work Is Asynchronous

Real work takes time. Models think, builds run, media is processed, remote nodes queue, and several tasks may finish in a different order than they started.

Program execution is therefore an asynchronous task lifecycle at the Station level:

```text
requested
    -> accepted or rejected
    -> placed
    -> started
    -> progress / logs / output chunks / artifacts
    -> succeeded / failed / canceled / timed out
    -> result accepted
```

Durable Project state stores invocation identity, status, provenance, progress, accepted outputs, cancellation, timeout, and lifecycle events. Local runtime handles are implementation details.

This model supports immediate work, long-running work, streaming, retries, remote execution, parallel execution, and late results without turning the UI into the source of truth.

## Presentation Is Not GUI

One Project can have several presentations at the same time:

- a Board on a large monitor with multifocus and focused regions;
- a Stack on a small touch screen;
- voice/audio through microphone and speaker;
- a presenter view and a separate audience display;
- a TV media outlet with phone controls;
- a car presentation prioritizing navigation, warnings, audio, and voice;
- a smart-home context for sensors, routines, cameras, media, and notifications;
- a spatial presentation in VR;
- compatibility surfaces for existing software.

Presentation consumes stable Project projections. It does not own durable Project state.

## Devices Are Runtime Nodes With Roles

Nova Station is not remote desktop.

Each capable computer or device can run a Station Runtime node, synchronize Station-owned state and object references, advertise capabilities, and receive roles.

Examples:

- laptop: Board, keyboard, touchpad, local execution;
- phone: Stack, microphone, approval surface, virtual keyboard, controls;
- workstation: GPU or build executor;
- TV: media outlet;
- speaker: voice input and audio output;
- home hub: sensors and hardware control;
- server: durable services or compute;
- embedded node: focused hardware role.

There is no required primary host. There is only the node through which the user is interacting now, plus other nodes available to the Project.

## Applications Dissolve Into Capabilities

Many applications bundle service access, data fetching, editing, media playback, chat, notifications, search, layout, settings, and device handling into isolated UI shells.

Nova Station separates service capability from presentation.

YouTube-like services can expose media references, search, channels, recommendations, and playback controls.

GitHub-like services can expose repositories, files, issues, pull requests, checks, actions, and notifications.

Chat services can expose conversations, messages, media references, and notification events.

An IDE can decompose into a focused editor, language and debugger connectors, build/test/log/status outlets, source-hosting connector, terminal commands, agents, and Project state.

This does not mean every existing application vanishes. It means a full application shell is no longer the only way to contribute useful capability.

## Missing Outlets Degrade Gracefully

A user asks for the latest video from a channel they follow. A connector returns a valid `MediaRef`, but the current Work Project has no video outlet.

Station can keep the object and offer:

- text summary;
- audio-only playback;
- queue for later;
- temporary media outlet;
- switch to an Entertainment or Home Project;
- compatibility surface.

The connector succeeded. The object remains valid. Only the current presentation route is unavailable.

This rule generalizes: unknown or temporarily unhandled Typed Objects should remain safe, explainable, and available for later routing.

## Memory, Replay, And Sync

Nova Station-owned state is immutable and event-sourced:

```text
snapshot + ordered event log + artifacts = reconstructed state
```

This enables:

- restore on another machine;
- explanation and audit history;
- Time Machine-style rollback;
- branching from an earlier state;
- synchronization across nodes;
- agent accountability.

Pure deterministic work may be recomputed when versions and inputs are pinned.

Effectful commands, external service calls, and AI outputs are recorded as accepted events or artifacts. Replay restores the accepted result instead of repeating the effect or asking a model again.

Nova Station synchronizes state it owns. It does not promise to preserve live Linux process memory, sockets, GPU buffers, or arbitrary application internals.

The intended model is network-first and local-capable: global restore and synchronization are primary, while cached local work can continue in a degraded offline mode and synchronize later.

## Appliance Profiles

The same Station Core can power purpose-built devices through declarative profiles.

An English Tutor profile on Raspberry Pi can combine:

- microphone and speaker;
- voice/audio outlet;
- tutor agent and model configuration;
- audiobook, dictionary, and translation connectors;
- persistent English Learning Project.

The Project remembers playback position, questions, corrections, vocabulary, and lesson history. It can later continue through a laptop, phone, or car presentation.

The device is focused. The core model remains general.

## Compatibility And Rendering

Existing software remains essential during transition.

Firefox, terminals, editors, GTK/Qt applications, and other legacy surfaces can run inside Project Presentations through compositor-backed compatibility infrastructure.

The compositor hosts surfaces. It must not become the owner of Project or agent state.

Visual rendering should remain backend-agnostic:

```text
Project projection
    -> UI engine
    -> Scene / DisplayList
    -> Render Graph
    -> Backend Command Stream
    -> graphics backend
```

Non-visual presentations bypass the visual rendering path entirely.

## Current Technical Priority

The immediate goal is a headless Station Core Runtime proof before deeper visual work.

It should demonstrate:

- Typed Object descriptors and reflection metadata;
- ProgramObject invocation contracts;
- Station Runtime node and execution capability descriptors;
- execution placement policy;
- asynchronous invocation lifecycle;
- event log and artifact store;
- immutable reducer and projection;
- delivery routing and graceful fallback;
- stub agent selection;
- deterministic and effectful demo programs;
- text/log/debug outlets.

The first proof can execute locally while preserving contracts for future multi-node execution.

## Product Guardrails

Nova Station should not become:

- a classic desktop with AI decoration;
- a launcher for the same application silos;
- a window manager presented as an operating-system revolution;
- a remote-desktop product that streams one screen everywhere;
- an agent with unrestricted access and hidden side effects;
- a promise to replace the entire software ecosystem immediately.

The measure of progress is whether Projects become more durable, agents more accountable, devices more composable, execution and delivery more flexible, and human attention less fragmented.

Read the [Stories](STORIES.md), [Station Core Runtime](CORE_RUNTIME.md), [Appliance Profiles](APPLIANCE_PROFILES.md), or [Public Roadmap](ROADMAP.md).
