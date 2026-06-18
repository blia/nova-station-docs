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

The goal is a Station: one project context, many devices, many outlets, all coordinated through state.

## Why

Classic operating systems still start from desktops, apps, windows, and tabs.

That model scatters project context across browsers, terminals, chats, logs, agents, devices, and app-specific interfaces.

It also wastes enormous effort. Every app rebuilds its own media viewer, chat panel, notifications, search, settings, layout, feed, editor shell, and device assumptions.

AI makes this worse, not better, if we only bolt agents onto the old model. Agents need structured project state, not a pile of windows.

## The Shift

Nova Station starts from the Project.

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

The same Project can be presented differently:

- large monitor: board;
- phone: focused stack and controls;
- car: audio, navigation, warnings, voice;
- home: sensors, routines, media, notifications;
- audio-only node: voice agents.

The Project is the same. The presentation changes.

## Apps Dissolve

Many traditional apps should become smaller than apps.

YouTube-like services can expose media references and playback controls. Station routes them to media outlets, feed outlets, phone controls, speakers, or queues.

GitHub-like services can expose repositories, files, issues, checks, notifications, and actions. Station routes them to code outlets, logs, status, agents, and notifications.

IDE-like apps can split into:

```text
code editor outlet
language/tool connectors
build/test/log/status outlets
Git/source-hosting connector
terminal/command outlet
AI agents
Project state
```

The editor edits code. The Project is the environment.

## Typed Objects And Outlets

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

If an outlet is missing, the system should not break. A video reference without a media outlet can become a text summary, audio-only playback, queued item, or compatibility surface.

The object remains valid. Only the current presentation route is unavailable.

## One Account, Many Devices

Nova Station is not only for laptops.

One account can coordinate many Station Runtime nodes:

- laptop;
- phone;
- tablet;
- car;
- TV;
- smart home hub;
- speaker;
- server;
- embedded device.

This is not remote desktop. Devices do not need to stream one screen everywhere.

They share Station-owned state and object references. Each device presents or controls the parts it is good at.

## Memory And Replay

Nova Station state is event-sourced:

```text
snapshot + ordered event log = deterministic state
```

That enables restore, replay, explanation, branching from previous state, and future sync across machines.

AI and other non-deterministic results are recorded as events/artifacts. Replay restores accepted results instead of asking a model again.

## Compatibility

Classic apps still matter.

Firefox, terminals, editors, GTK/Qt apps, and old windows become compatibility surfaces inside Project Presentations.

The compositor is important infrastructure.

It is not the product metaphor.

## Why It Matters

The desktop was built for apps.

Nova Station is being built for projects, agents, devices, and continuity.

If this works, the upside is not a cleaner desktop.

The upside is a new category of operating environment where:

- Projects are durable;
- agents are native;
- devices are outlets;
- apps dissolve into connectors and focused capabilities;
- state can be replayed and restored;
- the system remembers how work happened.
