# Що відбувається з Nova Station

Nova Station - це спроба переосмислити операційне середовище навколо проєктів, стану, агентів і ролей пристроїв.

Це не ще один desktop environment.

Це не window manager.

Це не launcher.

І це не чат-бот, приклеєний збоку до старих застосунків.

Основна ідея проста:

```text
not apps first
not windows first
not screens first

projects first
state first
agents first
outlets by role
```

Сучасні системи змушують людину тримати проєкт у голові: вікна, вкладки, термінали, редактори, браузери, чати, логи, повідомлення, AI-агенти, файли й device-local sessions живуть окремо.

Nova Station починає не з порожнього робочого столу.

Вона починає з Project.

Project - це живий контекст:

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

Один і той самий Project може бути представлений по-різному:

- як board на великому екрані;
- як stack на телефоні;
- як voice/audio session на пристрої без дисплея;
- як media surface на TV;
- як control/approval surface на телефоні;
- як compatibility surface для старих застосунків.

Тобто Presentation не означає обов'язково GUI.

## Чому це важливо

Класична модель ставить у центр apps і windows.

Nova Station ставить у центр Project state.

Programs у цій моделі не мають бути великими GUI-застосунками. Вони мають приймати й повертати Typed Objects: код, media refs, command results, notifications, logs, patch proposals, streams, documents, agent tasks тощо.

Station дивиться на ці об'єкти, їхні roles/capabilities/provenance, і вирішує:

- яку програму викликати;
- де її виконати;
- які events записати;
- куди доставити результат;
- який outlet може це показати, проговорити, програти, зберегти або поставити в queue.

У перспективі багато класичних apps можуть розчинитися в:

```text
connectors
    -> Typed Objects
    -> agents
    -> routing policy
    -> shared system outlets
```

Наприклад, YouTube-like сервіс не обов'язково має приносити з собою весь свій GUI. Він може дати `MediaRef`, а Nova Station вже вирішить, де це програти: на TV, телефоні, speaker, media outlet або пізніше з queue.

GitHub-like сервіс може давати repositories, issues, files, checks, notifications. Station маршрутизує це в code outlets, log outlets, status outlets, agents і notifications.

## Поточний фокус

Зараз Nova Station рухається core-first.

Compositor і visual shell залишаються важливими, але вони не є центром продукту. Вони є presentation / compatibility infrastructure.

Найважливіший наступний шар - Station Core Runtime:

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

Цей core має працювати без GUI.

Після цього visual board, phone stack, voice/audio presentation, appliance profiles і compatibility surfaces будуть різними способами представити той самий Project state.

Це ще дуже ранній етап.

Але напрям уже чіткий: Nova Station - це project-first AI operating environment.

Be focused.

