# What Is Happening With Nova Station

Nova Station is an attempt to rethink the operating environment around projects, state, agents, and device roles.

It is not another desktop environment.

It is not a window manager.

It is not a launcher.

And it is not a chatbot attached to old applications.

The core idea is simple:

```text
not apps first
not windows first
not screens first

projects first
state first
agents first
outlets by role
```

Modern systems force people to keep the project in their head: windows, tabs, terminals, editors, browsers, chats, logs, notifications, AI agents, files, and device-local sessions all live separately.

Nova Station does not start from an empty desktop.

It starts from a Project.

A Project is a living context:

- state;
- history;
- agents;
- connectors;
- typed objects;
- outlets;
- logs;
- media;
- code;
- notifications;
- restore points;
- device roles.

The same Project can be presented in different ways:

- as a board on a large display;
- as a stack on a phone;
- as a voice/audio session on a device with no display;
- as a media surface on a TV;
- as a control/approval surface on a phone;
- as a compatibility surface for legacy applications.

Presentation does not necessarily mean GUI.

## Why This Matters

The classic model puts apps and windows at the center.

Nova Station puts Project state at the center.

Programs in this model should not have to be large GUI applications. They should accept and emit Typed Objects: code, media refs, command results, notifications, logs, patch proposals, streams, documents, agent tasks, and so on.

Station inspects these objects, their roles, capabilities, and provenance, then decides:

- which program to invoke;
- where to execute it;
- which events to record;
- where to deliver the result;
- which outlet can show it, speak it, play it, store it, or queue it.

Over time, many classic applications can dissolve into:

```text
connectors
    -> Typed Objects
    -> agents
    -> routing policy
    -> shared system outlets
```

For example, a YouTube-like service does not necessarily need to bring its whole GUI shell. It can provide a `MediaRef`, and Nova Station decides where to play it: TV, phone, speaker, media outlet, or later from a queue.

A GitHub-like service can provide repositories, issues, files, checks, and notifications. Station routes them to code outlets, log outlets, status outlets, agents, and notifications.

## Current Focus

Nova Station is currently moving core-first.

The compositor and visual shell remain important, but they are not the product center. They are presentation and compatibility infrastructure.

The most important next layer is Station Core Runtime:

```text
source event
    -> optional agent intent
    -> ProgramObject selection
    -> execution placement routing
    -> async invocation lifecycle
    -> Typed Objects / artifacts / progress / errors
    -> Station validation
    -> event log
    -> reducer/projection
    -> delivery routing to outlets
```

This core must work without a GUI.

After that, visual board, phone stack, voice/audio presentation, appliance profiles, and compatibility surfaces become different ways to present the same Project state.

This is still very early.

But the direction is clear: Nova Station is a project-first AI operating environment.

Be focused.

