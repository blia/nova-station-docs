# Public Vision

Nova Station is a project-first AI operating environment.

Not just a workstation.

The product model is a Station: one project context, many devices, many outlets, coordinated through state, agents, and routing policy.

The central idea:

```text
Station -> Command Center -> Project -> Presentation -> Outlets / Widgets / Agents
```

## Core Ideas

- Project is the first-class citizen.
- Presentation is modality-agnostic: GUI, phone stack, voice/audio, command surface, or other outlet-driven interfaces.
- Agents are native system participants, not a side chat.
- Programs are executable Typed Objects.
- Many classic app shells should dissolve into service connectors, Typed Objects, agents, and system outlets.
- Outlets handle delivery and presentation by role.
- State is event-sourced for replay, restore, explanation, and sync.
- Classic applications still matter as compatibility surfaces.

## What Is Different

Traditional systems start from desktops, apps, windows, and tabs.

Nova Station starts from project state and routes work through agents, Typed Objects, and outlets.

This changes the role of applications.

The goal is not to run the same app silos inside prettier windows. The goal is to move common human-facing capabilities into system outlets and let services expose typed capabilities through connectors.

Examples:

- media services route videos to media/feed/control outlets;
- source-hosting services route code, issues, checks, files, and notifications to code/status/log/notification outlets;
- IDE-like tools split into code editor outlets, language/tool connectors, build/test/log/status outlets, Git/source-hosting connectors, terminal/command outlets, and AI agents;
- chat services route conversations, media references, notifications, and agent summaries to shared chat/media/notification outlets.

Benefits:

- less duplicated UI code;
- less duplicated runtime overhead;
- easier multi-device presentation;
- cleaner agent access to project context;
- fewer app-specific silos.

Missing outlets are handled as routing states, not crashes. If a connector returns a media reference but no media outlet exists, Station can keep the object and offer text summary, audio-only playback, queue-for-later, or compatibility-surface alternatives.

The system should adapt the project to the device:

- large monitor: board;
- phone: stack/control surface;
- audio-only node: voice/audio presentation;
- future devices: any capable Station Runtime node.

## Beyond Workstations

Nova Station is project-first, not desktop-first. That makes the model useful beyond normal computers.

Potential device classes:

- laptops/desktops;
- phones/tablets;
- cars;
- smart homes;
- entertainment systems;
- voice-only devices;
- embedded nodes and appliances.

The same account can coordinate many Station Runtime nodes. The active Project defines context, outlets, and routing policy.

Example Project contexts:

- Work Project: code, logs, terminals, agents, browser compatibility surfaces.
- Home Project: lights, sensors, cameras, routines, family notifications.
- Entertainment Project: movies, YouTube-like connectors, short-form feeds, speakers, TV outlets.
- Car Project: navigation, audio, calls, warnings, route context, voice interaction.
- Presentation Project: slides, notes, timer, audience display, media output.

If the active Project lacks a requested outlet, Station should explain the capability mismatch and offer to attach an outlet, switch Project, queue the object, or degrade to another modality.

## Rendering Direction

Visual presentations should be backend-agnostic:

```text
Project/View Projection
    -> Aura UI Engine
    -> Scene / DisplayList
    -> Render Graph Builder
    -> Backend Command Stream
    -> OpenGL ES backend now
    -> Vulkan / Metal / other backend later
```

OpenGL ES is the current baseline because the active prototype runs in an Android ARM Linux VM with virgl. The architecture should not depend on OpenGL-specific UI code.

## Status

This is early research and prototyping.

The current goal is to prove the Station Core Runtime first: Typed Objects, executable object references, event log, artifacts, routing policy, graceful outlet fallback, and then visual/audio/compatibility presentation backends.
