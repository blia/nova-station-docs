# Nova Station

Project-first AI workstation.

Be focused.

Nova Station - це спроба зробити наступну віху в еволюції операційних систем.

Не просто красивіший desktop.
Не ще один Linux shell.
Не чат-бот, прикручений збоку до старих вікон.

Це нова модель workstation для AI-era.

## Проблема

Сучасні системи досі стартують з робочого столу.

Ми відкриваємо програми, розкладаємо вікна, губимо контекст між браузером, терміналом, логами, чатами, задачами, агентами і пристроями.

А потім називаємо це workspace.

Але це не workspace.

Це купа вікон.

Сучасні mainstream ОС - це потужні універсальні app/entertainment platforms. Але вони оптимізовані під запуск і жонглювання програмами, а не під глибокий фокус на проєкті.

Ця модель ще й витрачає купу зайвої роботи.

Кожна app приносить свій media viewer, chat panel, notifications, search, feed, settings, layout system і свої припущення про пристрої. Ми запускаємо поруч багато маленьких UI-всесвітів, а потім вручну переносимо контекст між ними.

## Зсув

Nova Station починається з проєкту:

```text
project -> state -> agents -> presentations -> outlets
```

Проєкт - це не папка, не репозиторій і не набір відкритих вікон.

Це живий контекст роботи: стан, агенти, логи, інструменти, історія, пристрої, презентації і безперервність.

## Презентація не обов'язково GUI

На великому моніторі проєкт може бути board.

На телефоні той самий проєкт може бути stack.

На Raspberry Pi з мікрофоном і динаміком той самий проєкт може бути voice/audio:

```text
агент слухає -> агент діє -> агент звітує
```

Проєкт той самий. Змінюється тільки спосіб взаємодії.

Це робить Nova Station ширшою за операційну систему для ноутбука.

Та сама project/outlet модель може працювати для:

- ноутбуків і desktop-комп'ютерів;
- телефонів і планшетів;
- автомобілів;
- smart home;
- entertainment systems;
- voice-only devices;
- embedded nodes та appliances.

Замість apps, folders і desktops Nova Station організовує контекст навколо Projects:

- Work Project;
- Home Project;
- Entertainment Project;
- Car Project;
- Presentation Project.

Кожен project може мати свої outlets і routing policies. Якщо активний Work Project не має media outlet, Station може прямо сказати це і запропонувати тимчасово додати outlet, перемкнутись в Entertainment/Home Project, поставити media в queue або перейти в audio/text.

## Agent-first

Nova Station - це не чатик збоку робочого столу.

Агенти є учасниками системи.

Вони бачать стан проєкту, події, логи, outputs і презентації. Вони можуть підсумовувати, пропонувати дії, просити підтвердження і доставляти результат туди, де він потрібен.

## Typed Objects та Outlets

Програми стають executable Typed Objects.

Вони описують, що приймають, що повертають, що вміють, які дозволи потребують і чи є deterministic.

Програми повертають meaningful objects:

```text
CodeBlock
MediaRef
ChatMessage
Alert
MetricSample
CommandResult
StatePatchProposal
```

Nova Station вирішує, куди ці об'єкти доставити: board, телефон, speaker, agent summary або кілька місць одразу.

Але багато того, що ми зараз називаємо apps, має стати меншим за apps.

YouTube-like сервіси не мають потребувати повну GUI-shell, якщо Station уже має media outlets, feed outlets, media controls, agents і connector, який дає videos та playback references.

GitHub-like сервіси не мають володіти всім developer interface, якщо Station уже має code viewers/editors, logs, status, notifications, agents і connector, який дає repositories, issues, checks, files та actions.

У цій моделі багато класичних apps розчиняються в:

```text
service connector
    + Typed Objects
    + agents
    + system outlets
    + project routing policy
```

Результат: менше дубльованого UI-коду, менше зайвої runtime-ваги і чистіша системна модель.

Це також природно паралелиться на різні пристрої: ноутбук показує board, телефон дає controls, планшет показує logs, speaker бере audio. Не треба стрімити весь desktop всюди.

Економія ресурсів тут структурна: менше дубльованих app-shells, менше дубльованих media/chat/feed/notification систем, менше desktop video streaming, менше background mini-platforms і більше reuse спільних system outlets.

Якщо потрібного outlet зараз немає, система не має ламатися. Video reference без media outlet може стати text summary, audio-only playback, queued item або compatibility surface. Об'єкт лишається валідним; змінюється тільки presentation.

## Time Machine

Стан Nova Station event-sourced:

```text
snapshot + ordered event log = deterministic state
```

Це дає restore, replay, branch з попереднього стану, пояснення змін і майбутню синхронізацію між машинами.

AI-результати не переобчислюються на replay. Прийняті non-deterministic результати записуються як events/artifacts.

## Чому це важливо

Наступна workstation - це не просто кращий desktop.

Це project-first, agent-first station для роботи.

Якщо це спрацює, apps більше не мають володіти кожним інтерфейсом, projects не розчиняються у вікнах і табах, agents не працюють через side-channel, а state не зникає у live process memory.

Багато класичних app-shells можуть просто зникнути, розчинившись у connectors та outlets.

Потенційний upside - це не "трошки зручніший desktop".

Потенційний upside - це нова категорія: AI-native workstation, де проєкти довговічні, агенти нативні, пристрої є outlets, а система пам'ятає, як саме відбувалася робота.
