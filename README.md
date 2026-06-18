# Nova Station

Project-first AI workstation.

Be focused.

Nova Station is an early operating-system/workstation project exploring a different model for the AI era.

Classic systems start from desktops, apps, windows, and tabs. Nova Station starts from projects, state, agents, presentations, and outlets.

This repository is the public documentation surface. The implementation and raw internal project memory currently live in a separate private repository while the architecture is still forming.

## Why This Exists

Mainstream operating systems are extremely powerful universal app and entertainment platforms. They can do almost anything, but they are still optimized around launching apps and juggling windows.

Nova Station takes a different tradeoff: optimize the system around focused project work.

The goal is a workstation where:

- projects are first-class stateful contexts;
- agents are native system participants;
- devices become runtime nodes with roles;
- UI is only one possible presentation;
- voice/audio can be a complete interface;
- programs publish typed capabilities and outputs;
- state is replayable, restorable, and explainable.

## Read First

- [English Pitch](docs/PITCH.md)
- [Ukrainian Pitch](docs/PITCH.uk.md)
- [Public Vision](docs/VISION.md)
- [Public Roadmap](docs/ROADMAP.md)
- [Station Core Runtime](docs/CORE_RUNTIME.md)
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
- Station Core Runtime RFC for typed objects, ProgramObjects, event logs, artifacts, routing, and non-GUI operation;
- architecture and memory documents.

This is not yet a usable operating system.

It is an architectural direction with working experiments and a strong product thesis.

## What Kind Of Help Matters Now

Right now, the most valuable help is not random coding.

Useful help:

- ask hard questions;
- challenge assumptions;
- point out unclear concepts;
- compare with existing systems;
- give UX/product critique;
- help explain the idea to real people;
- sponsor time, infrastructure, or focused development later.

See [How To Help](docs/HOW_TO_HELP.md).
