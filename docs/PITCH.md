# Nova Station

Project-first AI workstation.

Be focused.

Nova Station is an attempt to define the next major step in operating systems.

Not a nicer desktop.
Not another Linux shell.
Not an AI chatbot bolted onto old windows.

A new workstation model for the AI era.

## The Problem

Computers still start from the wrong abstraction.

We boot into a desktop, open apps, stack windows, lose context across tabs, terminals, browsers, chats, logs, agents, and devices.

Then we call that a workspace.

It is not a workspace. It is a pile of windows.

Modern mainstream operating systems are powerful universal app and entertainment platforms. But they are optimized for launching and juggling apps, not for preserving deep project focus.

## The Shift

Nova Station starts from projects:

```text
project -> state -> agents -> presentations -> outlets
```

A project is not a folder, repository, or group of windows.

It is a living work context: state, agents, logs, tools, history, devices, presentations, and continuity.

## Presentation Is Not Just GUI

On a workstation monitor, a project can be a board.

On a phone, the same project can be a stack.

On a Raspberry Pi with only a microphone and speaker, the same project can be voice/audio:

```text
agent listens -> agent acts -> agent reports
```

The project is the same. Only the presentation changes.

## Agent-First

Nova Station is not a chat window next to your desktop.

Agents are system participants.

They can observe project state, logs, outputs, events, and presentations. They can summarize, propose actions, request approval, and route results to the right outlet.

## Typed Objects And Outlets

Programs become executable Typed Objects.

They describe what they accept, emit, can do, require, and whether they are deterministic.

Programs produce meaningful objects:

```text
CodeBlock
MediaRef
ChatMessage
Alert
MetricSample
CommandResult
StatePatchProposal
```

Nova Station decides where those objects go: board, phone, speaker, agent summary, or several places at once.

## Time Machine

Nova Station state is event-sourced:

```text
snapshot + ordered event log = deterministic state
```

That enables restore, replay, branching from previous state, explanation, and eventually sync across machines.

AI outputs are not blindly recomputed during replay. Accepted non-deterministic results are recorded as events/artifacts.

## Why It Matters

The next workstation is not a better desktop.

It is a project-first, agent-first station for work.

If it works, apps no longer need to own every interface, projects no longer dissolve into windows and tabs, agents no longer operate from a side-channel, and state no longer disappears into live process memory.

The upside is not a marginally cleaner desktop.

The upside is a new category: an AI-native workstation where projects are durable, agents are native, devices are outlets, and the system remembers how work happened.
