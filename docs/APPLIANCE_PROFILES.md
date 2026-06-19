# Station Appliance Profiles

Nova Station should be able to power focused devices without creating a separate application platform for each one.

An Appliance Profile is a declarative composition of the general Station model:

```text
Station Core Runtime
    -> profile configuration
    -> default Project template
    -> physical and software outlets
    -> connectors and ProgramObjects
    -> agents and model configuration
    -> routing and permission policy
```

The device can be narrow and purpose-built while its Project state remains portable.

## English Tutor Story

A Raspberry Pi has a microphone and speaker but no display.

The user wants a dedicated English-learning device that starts ready for conversation rather than booting into a generic desktop.

The profile declares:

- default `English Learning` Project;
- microphone and speaker physical outlets;
- voice/audio software outlet;
- English tutor agent;
- model configuration;
- audiobook, dictionary, translation, and audio connectors;
- routing from speech to tutor and audio to speaker;
- permission and confirmation policy.

The Project can remember:

- audiobooks and playback position;
- questions and answers;
- corrections;
- vocabulary progress;
- lesson history;
- accepted tutor outputs and provenance.

The same English Learning Project can later continue on a laptop, phone, car, or another Station node. Its presentation changes with available outlets.

## Why A Profile Instead Of A New App

The tutor does not need a custom operating-system shell, account model, state engine, device discovery layer, event log, or sync architecture.

Those belong to Station.

The profile contributes only what makes the device specific:

- Project template;
- outlets;
- connectors;
- agents and models;
- policy.

This pattern can also support a media node, presentation controller, workshop device, voice terminal, home hub, accessibility device, or custom hardware interface.

## Same Core, Different Device

A profile changes the capabilities and default experience, not the underlying product model.

Projects, Typed Objects, ProgramObjects, tasks, events, artifacts, routing, permissions, and agents remain governed by Station Core.

That keeps purpose-built hardware compatible with the wider Station account and Project history.

## Early Prototype Scope

The first profile proof does not need a package manager or image builder.

A local manifest and registry can prove:

- profile parsing;
- outlet and connector registration;
- default Project creation;
- permission and routing configuration;
- voice/audio-only presentation;
- persistent learning events and projections.

Security, signed packages, remote repositories, updates, hardware provisioning, and production appliance images come later.

Read the [English Tutor story](STORIES.md#a-voice-only-english-tutor), [Core Runtime](CORE_RUNTIME.md), or [Roadmap](ROADMAP.md).
