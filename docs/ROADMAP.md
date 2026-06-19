# Public Roadmap

This is a public summary of direction, not the full internal implementation plan.

Nova Station is still in architecture and early prototype work. Dates are intentionally not promised yet.

## Current: Station Core Runtime Baseline

The immediate target is a headless runtime proof.

- Typed Object descriptors and reflection metadata.
- ProgramObject invocation contracts.
- Station Runtime node and execution capability descriptors.
- Execution placement matcher.
- Asynchronous invocation/task lifecycle events.
- Role, capability, and outlet descriptors.
- Delivery routing matcher and graceful fallback.
- Event envelope and in-memory event log.
- Artifact references and initial in-memory store.
- Immutable reducer and deterministic projection tests.
- Stub agent selector.
- Pure text-transform demo.
- Effectful shell-command demo with recorded outputs.
- Text, log, error, and debug outlets.

The first executor may be local. The contracts should already support a future remote executor.

## Next: Durable Local Project

- Filesystem-backed event log and artifacts.
- Snapshots and restore.
- Project descriptors, settings, and routing policy.
- Task cancellation, timeout, retry, and progress projections.
- Permission and provenance boundaries.
- Source events beyond direct user input.
- Agent observation over Project events.

## Then: Presentations And Compatibility

- Attach a terminal/log presentation to Core projections.
- Prototype Board for large displays and pointer/keyboard input.
- Prototype Stack for phones and small touch screens.
- Explore voice/audio-only Project presentation.
- Attach Wayland compositor hosting as a visual compatibility outlet.
- Keep visual rendering behind Scene/DisplayList and backend-neutral commands.

## Then: Nodes, Sync, And Appliances

- Real multi-node transport and identity.
- Capability advertisement and remote execution placement.
- Shared state, object-reference, and artifact synchronization.
- Network-first restore with local offline fallback.
- Versioned outlet and connector repositories.
- Local Appliance Profile prototype.
- English Tutor voice-only node.
- Trusted external compute experiments.

## Ongoing

- Maintain concrete product stories as architecture constraints.
- Publish meaningful announcements rather than raw development logs.
- Gather feedback and reality checks.
- Test with varied hardware, outlets, and constrained devices.
- Keep compatibility work subordinate to the project-first product model.

## Not Goals Right Now

- A production-ready general-purpose OS.
- Replacing the Linux kernel.
- Polishing a classic desktop or window manager for its own sake.
- Rewriting every existing application.
- Streaming one desktop to every device as the primary model.
- Unrestricted autonomous agents.
- Premature cloud, package-manager, or graphics-backend complexity before the core proof.

Read the [Core Runtime](CORE_RUNTIME.md), [Vision](VISION.md), [Stories](STORIES.md), or [How To Help](HOW_TO_HELP.md).
