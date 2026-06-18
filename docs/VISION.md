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
- Outlets handle delivery and presentation by role.
- State is event-sourced for replay, restore, explanation, and sync.
- Classic applications still matter as compatibility surfaces.

## What Is Different

Traditional systems start from desktops, apps, windows, and tabs.

Nova Station starts from project state and routes work through agents, Typed Objects, and outlets.

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
