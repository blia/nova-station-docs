# Changelog

This changelog is curated. It is not a raw commit log.

## 2026-06-18: Station Core Runtime RFC

Today we clarified the next internal implementation target: Nova Station is moving core-first, not compositor-first.

Added public notes for the Station Core Runtime:

- Typed Objects as clean values plus Station reflection metadata;
- ProgramObjects as executable typed objects;
- source-event-driven runtime flow, not only user input;
- Station invocation of executable object references instead of embedding `exec` in clean payloads;
- execution classes: pure, deterministic, effectful, and AI;
- event-sourced state with replay rules;
- JSON Lines as the first planned local event log format;
- artifact storage for large outputs;
- routing through project configuration instead of hardcoded UI paths;
- a headless first runtime flow before deeper visual integration.

Why it matters:

The compositor and UI remain important, but they are presentation backends. The core system must also work without a GUI, which keeps the architecture aligned with project-first, agent-first, multi-device, and voice/audio use cases.

Public pitch/vision update:

We also clarified the application-dissolution thesis: many traditional app shells should become service connectors plus Typed Objects, agents, routing policy, and system outlets. This should reduce duplicated UI/runtime work and make multi-device presentation state-driven instead of desktop-stream-driven.

Added graceful fallback note: if a connector returns an object but no suitable outlet is available, Station should keep the object and offer alternative presentations instead of failing like a traditional app.

Added broader device-class note: the same project/outlet model should apply to laptops, phones, cars, smart homes, entertainment systems, voice-only devices, and embedded nodes. Projects become the organizing context across devices.

## 2026-06-18: How To Help Updated

Updated the public help page with concrete ways people can support the project now:

- clarified that planning/core development are not the main help needed right now;
- star/watch/share the repository;
- send the idea to people who may understand it;
- give feedback and reality checks;
- follow future changelog/devlog updates;
- help with video/audio equipment;
- provide financial support;
- share compute/model resources;
- share hardware/outlet test devices;
- offer relevant expertise.

Why it matters:

Nova Station needs a feedback loop with real people. At this stage, help is not only code. Attention, questions, hardware, compute, and moral support are all useful.

## 2026-06-18: Public Docs Start

Initial public documentation repository created.

Added:

- public pitch in English and Ukrainian;
- public vision summary;
- public roadmap summary;
- how-to-help page;
- public changelog.

Why it matters:

Nova Station now has a public communication surface separate from the private development brain. This makes it possible to share the idea, gather feedback, and build a small early community without exposing raw internal notes.

Open questions for readers:

- Does the project-first model make sense?
- Is "presentation is not necessarily GUI" clear?
- What is confusing in the pitch?
- What existing systems should this be compared against?
