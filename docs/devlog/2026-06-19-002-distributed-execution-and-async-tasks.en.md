# Distributed Execution And Async Tasks

Today we fixed two important architectural decisions for Nova Station.

Nova Station is moving further away from the classic model of one computer, one desktop, one place where everything runs.

In Nova Station there is no primary host machine.

There are Station Runtime nodes:

- phone;
- laptop;
- workstation;
- server;
- Raspberry Pi;
- VM;
- voice-only device;
- embedded node;
- any other capable computer.

Any of them can be the place where the user starts an interaction. But that does not mean the same node must execute the task or show the result.

## Execution Routing

The first decision: Nova Station separates **execution routing** from **delivery routing**.

The system decides separately:

1. where to run a ProgramObject;
2. where to deliver the result.

Example:

```text
phone voice request
    -> "generate an image"
    -> Station selects an image generation ProgramObject
    -> Station sees that a workstation has GPU/model capability
    -> the workstation executes the task
    -> ImageObject / ArtifactRef enters Project state
    -> Station routes preview to the phone
    -> Station routes the full image to a tablet, TV, or media outlet
```

The phone is the source node.

The workstation is the executor node.

The tablet or TV can be the output outlet.

These can be three different devices.

This matters because Nova Station is not remote desktop. We are not trying to stream one screen everywhere. We want devices to synchronize state, object references, artifacts, and events.

A device is not just a monitor attached to a main computer. It can be an input node, output node, audio node, approval device, media outlet, compute node, model execution node, sensor node, or hardware control node.

## Async Invocation Lifecycle

The second decision: ProgramObject execution is asynchronous at the Station model level.

Real tasks do not all finish immediately.

AI models take time.

Image generation takes time.

Builds and tests can run for minutes.

Rendering and media processing can produce progress.

Remote execution can queue, fail, retry, or return late.

So Nova Station should not model execution as a blocking function call.

Instead, execution becomes a task lifecycle:

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

Even if the first prototype runs locally and completes immediately, the model should already fit long-running work, streaming output, cancellation, timeouts, retries, parallel execution, and remote execution.

## Rust Detail

In Rust, the closest primitive to a JavaScript-style promise is `Future`.

An `async fn` returns a `Future`.

A `Future` is lazy: it only progresses when an async runtime polls it.

Rust's standard library defines the `Future` trait, but a full async runtime usually comes from crates such as Tokio, async-std, or smol.

For Nova Station, this distinction is important:

- Rust `Future`;
- `JoinHandle`;
- async channels;
- process handles;
- sockets;
- GPU handles;

are local runtime implementation details.

They should not become durable Station state.

Durable Station state should store:

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

Nova Station is event-sourced.

That means replay should reconstruct state from events and artifacts. Replay must not rerun an AI model or shell command just because we are restoring state.

For effectful and AI execution, the accepted output is recorded. Replay restores that accepted output.

The updated core flow now looks like this:

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

This is not a desktop-first architecture.

It is state-first, project-first, agents-first infrastructure for a distributed operating environment.

