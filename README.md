# Nova Station

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

Nova Station starts from Projects: durable contexts with state, history, agents, connectors, typed objects, outlets, device roles, logs, media, code, notifications, and restore points.

The goal is a Station: one project context, many devices, many outlets, coordinated through state.

## Why This Matters

Mainstream operating systems are powerful universal app platforms, but they still force people to juggle windows, tabs, app silos, device-local sessions, and scattered context.

That model wastes human attention and machine resources.

It also makes AI weaker than it should be. Agents need project state, history, typed outputs, permissions, and routing policy. They do not need to guess what matters from a pile of unrelated windows.

Nova Station explores a different model:

- Projects are first-class.
- Agents are native system participants.
- Devices are runtime nodes with roles.
- Presentation is not necessarily GUI.
- Applications dissolve into connectors and focused capabilities.
- Typed Objects move through routing policy.
- State is replayable, restorable, explainable, and eventually syncable across machines.

## The Core Idea

Traditional systems:

```text
desktop -> windows -> apps -> tabs -> project context
```

Nova Station:

```text
Station -> Command Center -> Project -> Presentation -> Outlets
```

Examples:

- A laptop can show a board with code, logs, browser compatibility surfaces, agents, and status.
- A phone can become a control surface, virtual keyboard, approval device, or secondary viewer.
- A TV can become a media outlet.
- A speaker can become voice input and audio output.
- A car can expose navigation, warnings, audio, calls, and voice interaction.
- A Raspberry Pi with only microphone and speaker can still participate through audio/voice agents.

The Project is the same. The presentation changes.

## Apps Dissolve

Many things we call apps are bundles of responsibilities that should not be bundled forever:

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

YouTube-like services can expose media references and playback controls. Station routes them to media outlets, feed outlets, phone controls, speakers, queues, or fallbacks.

GitHub-like services can expose repositories, files, issues, checks, notifications, and actions. Station routes them to code outlets, logs, status, agents, and notifications.

IDE-like tools can split into code editor outlets, language/tool connectors, build/test/log/status outlets, Git/source-hosting connectors, terminal/command outlets, agents, and Project state.

The editor edits code.

The Project is the environment.

## Missing Outlets Do Not Break The Flow

If a connector returns a media reference but no media outlet exists, Station should not fail like a classic app.

It can offer:

- text summary;
- audio-only playback;
- queue for later;
- temporary outlet attachment;
- switch to another Project;
- compatibility surface.

The object remains valid. Only the current presentation route is unavailable.

## Read First

- [Pitch](docs/PITCH.md)
- [Pitch in Ukrainian](docs/PITCH.uk.md)
- [Vision](docs/VISION.md)
- [Station Core Runtime](docs/CORE_RUNTIME.md)
- [Roadmap](docs/ROADMAP.md)
- [How To Help](docs/HOW_TO_HELP.md)
- [Changelog](CHANGELOG.md)

## Status

Very early.

Current private prototype work includes:

- Rust/OpenGL visual shell experiments;
- Aura-inspired login/shell UI;
- Smithay-based nested Wayland compositor prototype;
- first Wayland client surface hosting;
- Firefox/terminal launch experiments;
- Station Core Runtime RFC for Typed Objects, ProgramObjects, event logs, artifacts, routing, and non-GUI operation.

This is not yet a usable operating system.

It is a product thesis, architecture, and working prototype path.

## How To Help

The most useful help right now is feedback, attention, hardware, compute, and reality checks.

Start here:

- [How To Help](docs/HOW_TO_HELP.md)
- [Changelog](CHANGELOG.md)

Planning and core development are currently intentionally tight and AI-first. The project still needs real people to challenge the idea, point out unclear explanations, share it with the right readers, and provide practical support.
