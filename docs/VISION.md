# Nova Station Vision

Project-first AI operating environment.

Be focused.

Nova Station is not a nicer desktop and not a chatbot attached to old windows.

It is a different operating-system thesis:

```text
not apps first
not windows first
not screens first

projects first
state first
agents first
outlets by role
```

The product model is a Station: one project context, many devices, many outlets, coordinated through state.

## The Shift

Classic systems start from desktops, applications, windows, tabs, and device-local sessions.

Nova Station starts from Projects.

A Project is not a folder or group of windows. It is a living context:

- state;
- history;
- agents;
- connectors;
- typed objects;
- outlets;
- device roles;
- logs;
- media;
- code;
- notifications;
- restore points.

The user should not boot into an empty desktop. The user should enter a Command Center, choose a Project, and continue from the real state of that work.

## Presentation Is Not GUI

GUI is one presentation mode, not the system itself.

The same Project can be presented as:

- a board on a large monitor;
- a focused stack on a phone;
- audio and voice in a car;
- sensors, media, and routines in a smart home;
- a voice-only session on a small device;
- compatibility surfaces for old apps.

The Project is the same. The presentation changes according to available outlets.

## Applications Dissolve

Many traditional apps are too large because they bundle unrelated responsibilities:

```text
service access
data fetching
editing
media playback
chat
notifications
search
layout
settings
device handling
```

Nova Station separates those responsibilities.

The system should provide shared outlets for common human-facing roles:

- media;
- short-form feeds;
- chat;
- AI conversation;
- code viewing;
- code editing;
- documents;
- notifications;
- logs/status;
- commands;
- voice/audio.

External services become connectors or descriptors. They expose typed capabilities instead of bringing a full GUI shell.

YouTube-like services return media references and playback controls.

GitHub-like services return repositories, issues, files, checks, notifications, and actions.

IDE-like tools split into code editor outlets, language/tool connectors, build/test/log/status outlets, Git/source-hosting connectors, terminal/command outlets, agents, and Project state.

The editor edits code. The Project is the environment.

## Typed Objects And Routing

Programs and connectors emit Typed Objects:

```text
CodeBlock
MediaRef
ChatMessage
Notification
CommandResult
StatePatchProposal
```

Station decides where those objects go.

The app does not own every interface. Station owns delivery policy.

If an outlet is missing, the system should not break. A video reference without a media outlet can become a text summary, audio-only playback, queued item, temporary outlet request, project switch, or compatibility surface.

The object remains valid. Only the current presentation route is unavailable.

## One Account, Many Devices

Nova Station is not remote desktop.

Devices should not stream one screen everywhere.

Each Station Runtime node can sync state/object references, advertise outlets, and take roles.

Examples:

- laptop: main board and keyboard/touchpad input;
- phone: controls, approvals, virtual keyboard, secondary viewer;
- TV: media outlet;
- speaker: audio output and voice input;
- car: navigation, warnings, audio, calls;
- smart home hub: sensors, routines, media, notifications.

The same account and Project can coordinate all of them.

## Appliance Profiles

Some Station nodes can be purpose-built.

Instead of installing a generic desktop, a device can be assembled from:

```text
core runtime binary
    -> profile config
    -> outlet repository
    -> connectors
    -> models/agents
    -> default Project template
```

Example: an English Tutor device on Raspberry Pi.

It may have only a microphone and speaker. Its profile installs a voice/audio outlet, English tutor agent, audio/audiobook connectors, and an `English Learning` Project.

It can remember audiobooks, playback position, questions, corrections, vocabulary progress, and lesson history.

The same Project can later be presented on a laptop, phone, car, or other Station node if suitable outlets exist.

## Memory And Replay

Nova Station state is event-sourced:

```text
snapshot + ordered event log + artifacts = reconstructed state
```

That enables restore, replay, explanation, branching, and future sync across machines.

Pure deterministic work can be replayed.

Effectful work records outputs.

AI results are recorded as accepted artifacts/events instead of being recomputed during replay.

## Compatibility

Classic applications still matter.

Firefox, terminals, editors, GTK/Qt apps, and legacy windows become compatibility surfaces inside Project Presentations.

The compositor is important infrastructure.

It is not the product metaphor.

## Rendering Direction

Visual rendering should be backend-agnostic:

```text
Project/View Projection
    -> UI Engine
    -> Scene / DisplayList
    -> Render Graph Builder
    -> Backend Command Stream
    -> OpenGL ES backend now
    -> Vulkan / Metal / other backend later
```

The current prototype uses OpenGL ES because the development environment is an Android ARM Linux VM with virgl.

The architecture should not depend on OpenGL-specific UI code.

## Current Technical Priority

Nova Station should move core-first, not compositor-first.

The next proof point is Station Core Runtime:

- Typed Objects;
- executable object references;
- reflection metadata;
- event log;
- artifact store;
- immutable state patches;
- routing policy;
- pure/effectful/AI execution classes;
- graceful outlet fallback;
- headless runtime flow;
- visual/audio/compatibility projections.

The compositor remains important, but it should serve presentation and compatibility.

The core system must also work without GUI.

## Why It Matters

The desktop was built for apps.

Nova Station is being built for projects, agents, devices, and continuity.

If this works, the result is not a cleaner desktop.

It is a new category of operating environment where:

- Projects are durable;
- agents are native;
- devices are outlets;
- apps dissolve into connectors and focused capabilities;
- state can be replayed and restored;
- the system remembers how work happened.
