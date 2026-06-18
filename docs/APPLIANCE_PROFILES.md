# Station Appliance Profiles

Nova Station is not only a full-screen computer environment.

The same runtime model can build purpose-specific devices.

An appliance profile is a declarative way to assemble a Station node:

```text
core runtime binary
    -> install/profile config
    -> outlet repository
    -> connectors
    -> models/agents
    -> default Project template
```

This is similar in spirit to NixOS-style composition: small versioned blocks form a working system.

## Example: English Tutor

A user has a Raspberry Pi with a microphone and speaker.

They want it to become a dedicated English-learning device.

The profile can declare:

- physical outlets: microphone and speaker;
- software outlet: voice/audio;
- default Project: English Learning;
- agent: English tutor;
- model configuration;
- connectors: YouTube/audio, audiobooks, dictionary/translation;
- routing: speech input to tutor agent, audio media to speaker, lesson progress to Project state.

After boot, the device joins the user's Station account as a runtime node.

It can remember:

- listened audiobooks;
- playback position;
- questions asked by the user;
- corrections;
- vocabulary progress;
- lesson history;
- tutor-agent decisions.

The user can later switch to the same English Learning Project from a laptop, phone, car, or other Station node. The Project stays the same. The available outlets decide how it is presented.

## Why This Matters

This turns Nova Station from “an OS UI” into a composable runtime for user-owned devices.

A Station node can be:

- a laptop board;
- a phone control surface;
- a TV media outlet;
- a speaker voice node;
- a car assistant;
- a smart-home hub;
- a dedicated learning device;
- a custom hardware outlet.

The system model does not change.

Projects, Typed Objects, routing policy, outlets, event logs, and agents remain the same.

Only the node profile and available capabilities change.

## Early Scope

The first version does not need a full package manager or image builder.

A local manifest and local outlet registry are enough to prototype:

- profile loading;
- outlet installation;
- connector registration;
- default Project creation;
- routing into a voice/audio-only Project.
