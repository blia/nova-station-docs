# Station Core Runtime

Nova Station is moving core-first.

The compositor and visual shell are still important, but they are not the center of the system. They are visual presentation backends. The core of Nova Station is a runtime that can understand project state, invoke programs, record events, route typed results, and present work through any available outlet.

That means the same project model should eventually work through:

- a large visual board;
- a phone stack layout;
- a terminal/log outlet;
- a browser compatibility surface;
- a microphone and speaker with no GUI at all;
- a car audio/navigation interface;
- a smart home outlet graph;
- an entertainment/media device.
- a purpose-built appliance profile, such as an English tutor node with only microphone and speaker.

## Core Flow

The first runtime target is:

```text
system element / source event
    -> optional agent intent
    -> ProgramObject selection
    -> Station invocation of executable object reference
    -> Typed Object output
    -> Station validation/event
    -> reducer/projection
    -> routing to compatible outlets
    -> presentation through any available modality
```

This is deliberately not a desktop/window-manager flow.

It also does not have to start from user input. A runtime flow can start from system startup, sync, schedule, repository changes, network events, hardware events, agent observations, or user input.

## Typed Objects

Nova Station treats work as typed objects.

A Typed Object is not just a blob of text and not necessarily a GUI widget. It is a clean value plus Station-owned reflection metadata.

Example object value:

```json
{
  "text": "fn main() {}",
  "language": "rust"
}
```

Station can know, separately:

- what type it is;
- what roles it has;
- which programs can accept it;
- which outlets can present it;
- how agents should describe it;
- where it came from;
- whether it is safe to replay or recompute.

This keeps programs simple while the system handles routing, state, replay, and presentation.

## ProgramObjects

Programs are not primarily GUI apps in this model.

A ProgramObject is an executable typed object. It declares what it accepts, what it emits, and whether it is safe to replay.

Because object values stay clean, execution is invoked by Station through object references and reflection metadata. Conceptually:

```text
exec_object_ref(object_ref, invocation, context)
```

The executable behavior is not embedded directly into the clean payload.

Initial execution classes:

- `pure`: same input and version always produce the same output;
- `deterministic`: same pinned input, version, and context produce the same output;
- `effectful`: uses filesystem, shell, network, time, or environment;
- `ai`: model-backed or agentic execution.

Effectful and AI outputs must be recorded. Replay should restore accepted results, not re-run a shell command or ask a model again.

## Event Log And Artifacts

Nova Station state should be reconstructable from events and snapshots.

The first local durable event format is planned as JSON Lines because it is easy to inspect, search, debug, and share during early development.

Payload strategy is hybrid:

- important routing/reducer metadata stays inline;
- small payloads can be inline when that helps speed;
- large outputs become artifact references with hashes and previews.

The first artifact store can be in-memory for tests, then move to filesystem-backed artifacts.

## First Prototype Target

The first core prototype should not depend on Wayland, OpenGL, Smithay, or the visual shell.

It should prove:

```text
input text
    -> stub agent
    -> selected ProgramObject
    -> Station invocation of executable object reference
    -> typed output
    -> event
    -> reducer
    -> routed outlet projection
```

The demo will likely include:

- a pure text transform program for replay-safe tests;
- an effectful shell command program that records stdout, stderr, and exit code;
- text/error/debug outlets.

## Appliance Profile Target

The same core should eventually boot a purpose-built Station node from a declarative profile:

```text
profile
    -> default Project
    -> physical outlets
    -> software outlets
    -> connectors
    -> agents/models
    -> routing policy
```

Example:

```text
English Tutor
    -> microphone + speaker
    -> voice/audio outlet
    -> English tutor agent
    -> audiobook/audio connector
    -> English Learning Project
```

This proves that Nova Station is not only a visual computer shell. It can also become a small dedicated device while using the same Project state, event log, Typed Objects, routing, and outlet model.

## Graceful Missing Outlets

Missing outlets should not break the system.

Example:

```text
User: "I want to watch the latest episode from a channel I follow"
    -> agent selects a video-service connector
    -> connector returns a MediaRef
    -> Station tries to route it to a media outlet
```

If a media outlet is available, the video plays there.

If no media outlet is available, the object is still valid. Station can keep the media reference and offer alternatives:

- summarize the video through text;
- play or extract audio through an audio outlet;
- queue it until a media outlet appears;
- open it through a compatibility surface if allowed.

The connector did not fail. The media object did not vanish. Only the current presentation route is unavailable.

This is a core rule: failure to present is not failure to compute, fetch, store, or understand.

The same rule applies across Project contexts. If a Work Project has no media outlet, Station can explain the capability mismatch and offer to temporarily attach a media outlet, switch to an Entertainment/Home Project, queue the media, or degrade to audio/text.

Why this matters:

Nova Station is not trying to polish windows first. It is trying to build the execution/state kernel that can later power visual boards, voice-only operation, multi-device workflows, agents, and compatibility apps.
