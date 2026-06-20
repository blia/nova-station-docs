# Nova Station

Project-first agentic operating environment.

Be focused.

## The Project Is Missing From The Operating System

People do not work on windows, tabs, or applications. They work on Projects.

Yet the operating system does not really know that.

When someone works on an API and a frontend in parallel, both contexts are scattered across terminal tabs, browser tabs, editor windows, logs, tasks, chats, and agent/model sessions. The person remembers what belongs together and rebuilds the context every time attention moves.

Modern computers are powerful, but the operating model still makes the human carry the Project.

That operating model is learned behavior, not a natural law. Nova Station aims to establish a new cognitive path: the person operates intention and Project context while Station coordinates capabilities and returns results into durable context. “New neural pathways” is a product metaphor for learning that interaction, not a claim that Station literally simulates the brain.

Nova Station starts somewhere else:

```text
not apps first
not windows first
not screens first

projects first
state first
agents first
outlets by role
```

## Project Becomes First-Class

A Project is not a folder, repository, workspace, or group of windows.

It is a durable living context:

- state and history;
- agents and permissions;
- connectors and typed objects;
- code, media, logs, tasks, and notifications;
- device and outlet roles;
- accepted outputs and restore points.

The user enters a Command Center, chooses a Project, and continues from its actual state.

API and frontend can be separate Projects even when they reuse the same editor, browser, terminal, and services. The tools no longer own the context. They participate in it.

## Agents Belong Inside The System

A Station agent should not have to infer the Project from a pile of unrelated windows.

In Nova Station, agents participate at Station, Command Center, Project, task, routing, and outlet levels. They can observe permitted events, understand typed results, propose actions, request approval, invoke capabilities, and explain what happened.

Agent-first does not mean every interaction starts in chat. Work may begin with a user request, schedule, repository event, sync event, hardware signal, or another Project event.

The agent is a system participant, not a chat panel beside the system.

## One Project Can Use Many Computers

Suppose the user asks from a phone to generate an image.

The phone is the interaction point. Station can place execution on a trusted workstation with a suitable GPU, track the asynchronous task, accept the resulting artifact into Project state, and return a preview to the phone.

The full image may be delivered to a tablet, TV, or media outlet.

```text
source node != executor node != delivery outlet
```

There is no required primary host. Devices can contribute display, input, voice, media, approval, control, sensor, or compute roles according to their capabilities.

This is not remote desktop. Nova Station synchronizes owned state, object references, artifacts, and events instead of streaming one screen everywhere.

## Presentation Is Not The Project

The same Project can become:

- a Board on a large monitor;
- a focused Stack on a phone;
- a voice-only session on a Raspberry Pi;
- a car interface centered on navigation, warnings, audio, and voice;
- a smart-home context for sensors, routines, media, and notifications;
- separate presenter and audience views;
- a compatibility surface for existing applications.

The Project remains durable. Presentation adapts to available outlets and context.

## Applications Become Smaller

Most applications bundle service access, data, editing, playback, search, notifications, layout, settings, and device handling into separate UI universes.

Nova Station separates those responsibilities.

A YouTube-like service can expose media references, search, channels, and playback controls. Station routes the result to media, audio, phone-control, queue, or fallback outlets.

A GitHub-like service can expose repositories, files, issues, checks, actions, and notifications. Station routes them to code, task, status, log, notification, and agent workflows.

An IDE can become:

```text
focused code editor
language and debugger connectors
build/test/log/status outlets
Git/source-hosting connector
terminal/command outlet
agents and optional model providers
Project state
```

The editor edits code. The Project is the environment.

## Missing Presentation Is Not Total Failure

The user asks for the latest video from a channel they follow. A connector successfully returns a media reference, but the current Work Project has no video outlet.

The object remains valid. Station can offer a summary, audio-only playback, queue for later, temporary outlet, Project switch, or compatibility surface.

Failure to present is not failure to fetch, compute, store, or understand.

## The System Remembers Work

Nova Station-owned state is reconstructed from:

```text
snapshot + ordered event log + artifacts
```

That enables restore, replay, explanation, branching, and future synchronization across machines.

Outputs marked as recorded-result-required are stored when accepted. Replay restores those results instead of asking a model again or repeating an external action.

If one machine is lost, another machine can reconstruct the durable Project context. Nova Station does not claim to restore live Linux process memory; it restores the state that belongs to the Station.

## Compatibility Without Surrendering The Model

Firefox, terminals, editors, GTK/Qt applications, and other existing software still matter.

They can run as compatibility surfaces inside Project Presentations while native connectors and outlets evolve around them.

The compositor is important infrastructure. It is not the product metaphor.

## Where The Project Is Now

Nova Station is very early and not yet a usable operating system.

The current priority is a headless Station Core Runtime proof: Typed Objects, ProgramObjects, events, artifacts, execution placement, asynchronous task lifecycle, immutable Project state, routing, and graceful fallback.

Visual, voice, appliance, and compatibility presentations should attach to that core rather than define it.

If the thesis works, the result is not a cleaner desktop.

It is an operating environment where Projects are durable, agents are native, devices have roles, applications become focused capabilities, and work can continue across machines without losing its meaning.

Read the [concrete Stories](STORIES.md), the complete [Vision](VISION.md), or [How To Help](HOW_TO_HELP.md).
