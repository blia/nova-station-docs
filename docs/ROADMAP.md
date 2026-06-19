# Public Roadmap

This is a public summary, not the full internal roadmap.

## Current Focus

- Station Core Runtime design.
- Typed Object and ProgramObject contracts.
- Event log, artifact, routing, and replay model.
- Headless first runtime flow before visual integration.
- Project-first architecture documentation.
- Public communication and feedback loop.

## Near-Term

- Prototype the headless core runtime.
- Add pure replay-safe ProgramObject demo.
- Add effectful shell-command ProgramObject demo.
- Route stdout, stderr, and debug objects to compatible outlets.
- Define Project model.
- Define event store and projections.
- Define Project Presentation model.
- Continue Wayland/compositor work as visual compatibility surface infrastructure.
- Move visual UI toward Scene/DisplayList.
- Keep rendering backend-agnostic.
- Prototype Board and Stack presentations.
- Explore Voice/Audio presentation.
- Prototype local appliance profiles and outlet repository manifests.
- Build an English Tutor profile demo for a voice/audio-only Station node.

## Later

- Sync/restore backend.
- Multi-node Station Runtime.
- Versioned outlet/connector repositories.
- Purpose-built Station appliance profiles.
- Agent observation over event streams.
- Public announcements and changelog.
- Vulkan/other rendering backend when platform support is realistic.

## Non-Goals Right Now

- General-purpose production OS.
- Replacing Linux kernel.
- Polishing a classic desktop/window manager for its own sake.
- Rewriting every app.
- Streaming one desktop to every device as the main model.
