# Nova Station

Project-first agentic operating environment.

Be focused.

## Операційна система не бачить Project

Люди працюють не над вікнами, вкладками чи застосунками. Вони працюють над Projects.

Але операційна система цього майже не розуміє.

Коли я паралельно працюю над API та frontend, обидва контексти розкидані між вкладками термінала, браузером, редактором, логами, задачами, чатами й agent/model sessions. Я сам пам'ятаю, що до чого належить, і щоразу заново збираю контекст, коли перемикаю увагу.

Сучасні комп'ютери дуже потужні, але стара модель досі змушує людину нести Project у власній голові.

Ця модель — learned behavior, а не natural law. Nova Station формує інший cognitive path: людина оперує intention і Project context, а Station координує capabilities та повертає результат у durable context. «Нові нейронні зв'язки» — метафора навчання такій взаємодії, а не твердження, що Station буквально симулює мозок.

Nova Station починає з іншої точки:

```text
not apps first
not windows first
not screens first

projects first
state first
agents first
outlets by role
```

## Project стає first-class

Project - це не папка, репозиторій, workspace або група вікон.

Це довговічний живий контекст:

- state та history;
- agents і permissions;
- connectors і typed objects;
- code, media, logs, tasks та notifications;
- ролі пристроїв і outlets;
- accepted outputs і restore points.

Користувач входить у Command Center, обирає Project і продовжує роботу з його реального стану.

API та frontend можуть бути окремими Projects, навіть якщо використовують ті самі editor, browser, terminal і сервіси. Інструменти більше не володіють контекстом. Вони беруть у ньому участь.

## Agents мають бути всередині системи

Station agent не повинен вгадувати Project із купи випадкових вікон.

У Nova Station agents беруть участь на рівні Station, Command Center, Project, задач, routing та outlets. Вони можуть спостерігати дозволені events, розуміти typed results, пропонувати дії, просити підтвердження, запускати capabilities і пояснювати, що відбулося.

Agent-first не означає, що кожна взаємодія починається в чаті. Робота може стартувати із запиту людини, schedule, repository event, sync event, hardware signal або іншої події Project.

Agent є учасником системи, а не chat panel збоку.

## Один Project може використовувати багато комп'ютерів

Уявімо, що я прошу Nova Station із телефона згенерувати зображення.

Телефон є точкою взаємодії. Station може запустити задачу на довіреній workstation із відповідною GPU, відстежувати асинхронне виконання, прийняти готовий artifact у Project state і повернути preview на телефон.

Повне зображення може бути доставлене на планшет, TV або media outlet.

```text
source node != executor node != delivery outlet
```

Обов'язкової головної машини немає. Пристрої можуть виконувати display, input, voice, media, approval, control, sensor або compute ролі відповідно до своїх capabilities.

Це не remote desktop. Nova Station синхронізує власний state, object references, artifacts та events, а не стрімить один екран усюди.

## Presentation не є Project

Той самий Project може бути представлений як:

- Board на великому моніторі;
- focused Stack на телефоні;
- voice-only session на Raspberry Pi;
- car interface навколо navigation, warnings, audio та voice;
- smart-home context для sensors, routines, media та notifications;
- окремі presenter та audience views;
- compatibility surface для наявних застосунків.

Project залишається довговічним. Presentation адаптується до доступних outlets і контексту.

## Застосунки стають меншими

Більшість застосунків збирає service access, data, editing, playback, search, notifications, layout, settings і device handling в окремі UI-всесвіти.

Nova Station розділяє ці відповідальності.

YouTube-like сервіс може віддавати media references, search, channels та playback controls. Station маршрутизує результат у media, audio, phone-control, queue або fallback outlets.

GitHub-like сервіс може віддавати repositories, files, issues, checks, actions та notifications. Station маршрутизує їх у code, task, status, log, notification та agent workflows.

IDE може розкластися на:

```text
focused code editor
language і debugger connectors
build/test/log/status outlets
Git/source-hosting connector
terminal/command outlet
agents і optional model providers
Project state
```

Editor редагує code. Project є environment.

## Відсутня presentation не означає повний failure

Я прошу останнє відео з каналу, який дивлюся. Connector успішно повертає media reference, але в поточному Work Project немає video outlet.

Object залишається валідним. Station може запропонувати summary, audio-only playback, queue на потім, тимчасовий outlet, перехід в інший Project або compatibility surface.

Неможливість показати результат не означає неможливість його отримати, обчислити, зберегти або зрозуміти.

## Система пам'ятає роботу

State, яким володіє Nova Station, відновлюється з:

```text
snapshot + ordered event log + artifacts
```

Це дає restore, replay, explanation, branching і майбутню синхронізацію між машинами.

Outputs із `recorded_result_required` записуються після прийняття. Replay відновлює ці результати, а не питає model знову й не повторює зовнішню дію.

Якщо одну машину втрачено, інша може відновити довговічний контекст Project. Nova Station не обіцяє відновити живу пам'ять Linux-процесів; вона відновлює state, який належить Station.

## Compatibility без відмови від нової моделі

Firefox, terminals, editors, GTK/Qt applications та інше наявне software досі потрібні.

Вони можуть працювати як compatibility surfaces усередині Project Presentations, поки навколо них розвиваються native connectors та outlets.

Compositor є важливою infrastructure. Але це не product metaphor.

## Де проєкт зараз

Nova Station перебуває на дуже ранній стадії й поки не є готовою операційною системою.

Поточний пріоритет - headless proof Station Core Runtime: Typed Objects, ProgramObjects, events, artifacts, execution placement, async task lifecycle, immutable Project state, routing і graceful fallback.

Visual, voice, appliance та compatibility presentations мають підключатися до цього core, а не визначати його.

Якщо thesis спрацює, результатом буде не чистіший desktop.

Це буде operating environment, де Projects довговічні, agents native, пристрої мають ролі, застосунки стають focused capabilities, а робота може продовжуватися між машинами, не втрачаючи свого сенсу.

Читайте конкретні [Історії](STORIES.uk.md), повну [Vision](VISION.md) або [Як допомогти](HOW_TO_HELP.md).
