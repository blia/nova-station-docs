# Nova Station

Project-first agentic operating environment.

Be focused.

Nova Station is an attempt to rethink the operating environment around Projects, durable state, native agents, and devices with explicit roles.

It is not a nicer desktop and not a chatbot attached to old applications.

## The Problem

Imagine working on an API and a frontend at the same time.

The terminal has tabs for both. The browser has tabs for both. Code, logs, tasks, chats, agents, and model-backed assistants are scattered across tools. To switch context, you reconstruct the Project manually from windows and memory.

Modern operating systems make the person carry the Project.

Nova Station asks the system to carry it instead.

## A Different Starting Point

```text
not apps first
not windows first
not screens first

projects first
state first
agents first
outlets by role
```

A Project is not a folder, repository, workspace, or group of windows. It is a durable context containing state, history, agents, connectors, typed objects, tasks, code, media, logs, device roles, and restore points.

The user enters a Command Center, chooses a Project, and continues from the real state of that work.

```text
Station -> Command Center -> Project -> Presentation -> Outlets
                         Agents alongside every level
```

## What This Enables

- **Switch Projects, not tabs.** API and frontend can restore separate code, browser, terminal, logs, agents, and status contexts.
- **Ask on one device, execute on another.** A phone can request an image while Station routes generation to a trusted GPU workstation and delivers the result to the best media outlet.
- **Use the same Project without a screen.** A Raspberry Pi with a microphone and speaker can run a voice-only English Learning Project.
- **Keep valid results when presentation is unavailable.** A video reference without a media outlet can become a summary, audio playback, queued item, temporary outlet request, or compatibility surface.
- **Restore work on another machine.** Snapshots, ordered events, and artifacts reconstruct Station-owned Project state without pretending to restore live process memory.
- **Make applications smaller.** Editors, source hosting, media services, and chat systems can expose focused capabilities while Station owns Project context and delivery policy.

Read the fuller [Stories](docs/STORIES.md) or [Історії українською](docs/STORIES.uk.md).

## One Project, Many Presentations

The same Project can appear as:

- a Board on a large display;
- a focused Stack on a phone;
- a voice/audio session without GUI;
- a presenter view plus a separate audience display;
- a media experience across TV, phone controls, and speakers;
- a compatibility surface for Firefox, terminals, editors, or other existing applications.

Devices do not need to stream one desktop everywhere. Each Station Runtime node advertises capabilities and can become an input, output, execution, approval, media, voice, or control node.

The Project is shared. The presentation changes.

## Current Status

Nova Station is very early. It is not yet a usable operating system.

Current work includes:

- an accepted Station Core Runtime design;
- contracts for Typed Objects, ProgramObjects, events, artifacts, routing, execution placement, and asynchronous tasks;
- early visual shell and nested Wayland compositor experiments;
- first compatibility-surface hosting experiments;
- public stories and announcements used to test whether the product model is coherent.

The immediate priority is a headless core proof before deeper visual integration. The compositor remains important presentation and compatibility infrastructure, but it is not the product center.

## Read Next

- [Stories](docs/STORIES.md) / [Історії](docs/STORIES.uk.md): concrete scenarios first.
- [Pitch](docs/PITCH.md) / [Пітч українською](docs/PITCH.uk.md): the argument for Nova Station.
- [Vision](docs/VISION.md): the complete public product model.
- [Station Core Runtime](docs/CORE_RUNTIME.md): how the first technical proof fits together.
- [Station Appliance Profiles](docs/APPLIANCE_PROFILES.md): purpose-built devices from the same runtime.
- [Public Roadmap](docs/ROADMAP.md): current direction and non-goals.
- [Announcements](docs/ANNOUNCEMENTS.md): major public updates.
- [Telegram channel](https://t.me/nova_station_channel): Ukrainian announcements.
- [How To Help](docs/HOW_TO_HELP.md): feedback, hardware, compute, and practical support.
- [Changelog](CHANGELOG.md): curated documentation changes.

## Help The Project

The most useful support right now is attention, honest feedback, hardware, compute, audio/video equipment, sharing, and sponsorship.

Start with [How To Help](docs/HOW_TO_HELP.md).
