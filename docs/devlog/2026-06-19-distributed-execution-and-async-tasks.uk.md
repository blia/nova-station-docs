# Distributed Execution та асинхронні задачі

Сьогодні зафіксували два важливі архітектурні рішення для Nova Station.

Nova Station ще далі відходить від класичної моделі "один комп'ютер, один робочий стіл, одне місце, де все виконується".

У Nova Station немає головної машини-хоста.

Є Station Runtime nodes:

- телефон;
- ноутбук;
- робоча станція;
- сервер;
- Raspberry Pi;
- VM;
- voice-only пристрій;
- embedded node;
- будь-який інший достатньо capable комп'ютер.

Будь-який з них може бути місцем, де користувач починає взаємодію. Але це не означає, що саме цей node має виконувати задачу або показувати результат.

## Execution Routing

Перше рішення: Nova Station розділяє **execution routing** і **delivery routing**.

Система окремо вирішує:

1. де запускати ProgramObject;
2. куди доставити результат.

Приклад:

```text
phone voice request
    -> "згенеруй картинку"
    -> Station вибирає image generation ProgramObject
    -> Station бачить workstation з GPU/model capability
    -> workstation виконує задачу
    -> ImageObject / ArtifactRef потрапляє в Project state
    -> Station маршрутизує preview на телефон
    -> Station маршрутизує повне зображення на tablet, TV або media outlet
```

Телефон тут є source node.

Workstation є executor node.

Tablet або TV можуть бути output outlet.

Це можуть бути три різні пристрої.

Це важливо, бо Nova Station не є remote desktop. Ми не намагаємося стрімити один екран всюди. Ми хочемо, щоб пристрої синхронізували state, object refs, artifacts і events.

Пристрій не є просто монітором до головного комп'ютера. Він може бути input node, output node, audio node, approval device, media outlet, compute node, model execution node, sensor node або hardware control node.

## Async Invocation Lifecycle

Друге рішення: ProgramObject execution має бути асинхронним на рівні самої Station-моделі.

Реальні задачі не завершуються миттєво.

AI-модель може думати.

Генерація зображення займає час.

Build або test suite можуть бігти хвилинами.

Rendering і media processing можуть давати progress.

Remote execution може чекати в queue, падати, retry-итись або повертати результат пізніше.

Тому Nova Station не має моделювати execution як blocking function call.

Замість цього execution стає task lifecycle:

```text
InvocationRequested
    -> InvocationAccepted / InvocationRejected
    -> ExecutionPlaced
    -> ExecutionStarted
    -> Progress / OutputChunk / ArtifactCreated / LogEmitted
    -> ExecutionSucceeded / ExecutionFailed / ExecutionCanceled / ExecutionTimedOut
    -> ResultAccepted
    -> reducer/projection
    -> delivery routing
```

Навіть якщо перший prototype буде локальним і завершуватиме задачу одразу, модель уже має підходити для long-running work, streaming output, cancellation, timeouts, retries, parallel execution і remote execution.

## Rust Detail

У Rust найближча річ до JavaScript-style promise - це `Future`.

`async fn` повертає `Future`.

`Future` є lazy: вона рухається вперед тільки тоді, коли async runtime її poll-ить.

Стандартна бібліотека Rust визначає `Future` trait, але повний async runtime зазвичай приходить з crates на кшталт Tokio, async-std або smol.

Для Nova Station тут важливе розділення:

- Rust `Future`;
- `JoinHandle`;
- async channels;
- process handles;
- sockets;
- GPU handles;

це локальні runtime implementation details.

Вони не мають ставати durable Station state.

Durable Station state має зберігати:

- invocation/task id;
- lifecycle events;
- executor node;
- source node;
- progress;
- provenance;
- accepted Typed Objects;
- artifact references;
- replay policy.

## Why It Matters

Nova Station є event-sourced системою.

Це означає, що replay має відновлювати state з events і artifacts. Replay не має заново запускати AI-модель або shell command просто тому, що ми відновлюємо state.

Для effectful і AI execution ми записуємо accepted output. Replay відновлює цей accepted output.

Оновлений core flow тепер виглядає так:

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

Це не desktop-first архітектура.

Це state-first, project-first, agents-first infrastructure для distributed operating environment.

