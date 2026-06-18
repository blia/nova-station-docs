# Public Vision

Nova Station is a project-first AI workstation.

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
- chat services route conversations, media references, notifications, and agent summaries to shared chat/media/notification outlets.

Benefits:

- less duplicated UI code;
- less duplicated runtime overhead;
- easier multi-device presentation;
- cleaner agent access to project context;
- fewer app-specific silos.

The system should adapt the project to the device:

- large monitor: board;
- phone: stack/control surface;
- audio-only node: voice/audio presentation;
- future devices: any capable Station Runtime node.

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

The current goal is to prove the compositor, project model, presentation model, and agent-readable architecture step by step.
