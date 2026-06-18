# Nova Station

Project-first AI operating environment.

Be focused.

Nova Station - це не красивіший desktop і не чат-бот, прикручений до старих вікон.

Це інша thesis операційної системи:

```text
не apps first
не windows first
не screens first

projects first
state first
agents first
outlets by role
```

Мета - Station: один project context, багато пристроїв, багато outlets, усе координується через state.

## Чому

Класичні ОС досі стартують з desktops, apps, windows і tabs.

Ця модель розмазує project context між browsers, terminals, chats, logs, agents, devices і app-specific interfaces.

Вона ще й витрачає купу зайвої роботи. Кожна app заново будує media viewer, chat panel, notifications, search, settings, layout, feed, editor shell і свої device assumptions.

AI робить це ще гіршим, якщо просто прикрутити agents до старої моделі. Agents потрібен structured project state, а не купа windows.

## Зсув

Nova Station починається з Project.

Project - це не folder і не group of windows. Це живий context:

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

Той самий Project може мати різну presentation:

- large monitor: board;
- phone: focused stack and controls;
- car: audio, navigation, warnings, voice;
- home: sensors, routines, media, notifications;
- audio-only node: voice agents.

Project той самий. Змінюється presentation.

## Apps розчиняються

Багато традиційних apps мають стати меншими за apps.

YouTube-like сервіси можуть давати media references і playback controls. Station маршрутизує їх у media outlets, feed outlets, phone controls, speakers або queue.

GitHub-like сервіси можуть давати repositories, files, issues, checks, notifications і actions. Station маршрутизує їх у code outlets, logs, status, agents і notifications.

IDE-like apps можуть розкластися на:

```text
code editor outlet
language/tool connectors
build/test/log/status outlets
Git/source-hosting connector
terminal/command outlet
AI agents
Project state
```

Editor редагує code. Project є environment.

## Typed Objects And Outlets

Programs і connectors повертають Typed Objects:

```text
CodeBlock
MediaRef
ChatMessage
Notification
CommandResult
StatePatchProposal
```

Station вирішує, куди ці objects доставити.

App більше не володіє кожним interface. Station володіє delivery policy.

Якщо outlet немає, система не ламається. Video reference без media outlet може стати text summary, audio-only playback, queued item або compatibility surface.

Object лишається валідним. Недоступний лише поточний presentation route.

## Один account, багато devices

Nova Station не тільки для laptops.

Один account може координувати багато Station Runtime nodes:

- laptop;
- phone;
- tablet;
- car;
- TV;
- smart home hub;
- speaker;
- server;
- embedded device.

Це не remote desktop. Devices не мають стрімити один screen всюди.

Вони ділять Station-owned state і object references. Кожен device показує або контролює те, для чого він найкращий.

## Memory And Replay

State Nova Station event-sourced:

```text
snapshot + ordered event log = deterministic state
```

Це дає restore, replay, explanation, branch з попереднього state і майбутній sync між machines.

AI та інші non-deterministic results записуються як events/artifacts. Replay відновлює accepted results, а не питає model знову.

## Compatibility

Classic apps ще потрібні.

Firefox, terminals, editors, GTK/Qt apps і старі windows стають compatibility surfaces всередині Project Presentations.

Compositor важливий.

Але це infrastructure.

Це не product metaphor.

## Чому це важливо

Desktop був створений для apps.

Nova Station створюється для projects, agents, devices і continuity.

Якщо це спрацює, upside - не чистіший desktop.

Upside - нова категорія operating environment, де:

- Projects довговічні;
- agents native;
- devices є outlets;
- apps розчиняються в connectors і focused capabilities;
- state можна replay/recover;
- система пам'ятає, як відбувалась робота.
