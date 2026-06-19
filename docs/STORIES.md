# Nova Station Stories

Nova Station is an abstract operating-system idea. These stories show what it is meant to change in practice.

They are not product demos or promises that every feature already exists. They are concrete scenarios used to shape the architecture and test whether the project-first model is coherent.

## Switch The Project, Not The Tabs

Imagine working on an API and a frontend at the same time.

The terminal has tabs for both. The browser has tabs for both. Logs, tasks, source code, chats, and agents are scattered across separate tools. To change context, you reconstruct it manually from windows and memory.

In Nova Station, API and frontend can be separate Projects. Selecting the API Project restores its code, logs, browser content, tasks, agents, status, and presentation. Selecting the frontend Project restores another coherent context.

The user chooses the work. The system restores the environment around it.

## Ask On A Phone, Execute On A Workstation

You ask Nova Station from a phone to generate an image.

The phone is the interaction point, but it is not forced to perform the expensive work. Station sees a trusted workstation with a suitable GPU and model, places the task there, tracks progress, accepts the resulting image artifact into Project state, and returns a preview to the phone.

The full image can then appear on a tablet, TV, or media outlet.

The source device, execution device, and output device can all be different.

## The Video Exists Even Without A Video Outlet

You ask for the latest video from a channel you follow. An agent uses a video-service connector and receives a media reference.

If the current Project has a media outlet, the video plays. If it does not, the request has not failed. Station can keep the reference and offer a text summary, audio-only playback, queue for later, temporary media outlet, Project switch, or compatibility surface.

Failure to present is not failure to fetch, compute, store, or understand.

## A Voice-Only English Tutor

A Raspberry Pi has only a microphone and speaker. It boots directly into an English Learning Project with a tutor agent, voice/audio outlet, and audiobook or dictionary connectors.

The Project remembers playback position, questions, corrections, vocabulary progress, and lesson history. The same Project can later continue on a laptop or phone with a different presentation.

Nova Station does not require every useful computer to have a desktop.

## Restore Work On Another Machine

Your computer or development VM is lost. On another machine, Station authenticates the same account and reconstructs Projects from snapshots, ordered events, and artifacts.

It does not restore live Linux process memory. It restores the durable logical state that Nova Station owns: Project history, accepted outputs, configuration, agent memory, object references, and restore points.

If the network is unavailable, cached local work can continue in a degraded mode and synchronize later.

## One Project, Different Device Roles

A laptop displays the main Project Board. A second monitor becomes a media outlet. A phone becomes a virtual keyboard, approval surface, or remote control. A speaker handles voice input and audio output.

The devices do not all stream the same screen. Each Station Runtime node advertises capabilities and receives roles appropriate to the active Project.

The Project is shared. Its presentations are different.

## The IDE Becomes Smaller

Modern editors repeatedly grow into heavy IDEs because each one absorbs project context, terminal, Git, tests, debugger, logs, packages, notifications, AI, and layout management.

Nova Station moves that environment into the Project. The code editor can focus on editing. Language tools, build/test status, Git hosting, terminal commands, logs, and agents become focused connectors and outlets around shared Project state.

The editor edits code. The Project is the environment.

## Add New Hardware Once

A developer creates a new controller or unusual hardware device. Instead of integrating it separately into every application, they implement one Station outlet describing its capabilities and semantic roles.

Programs that already understand those roles can use the device without knowing its brand or custom protocol.

The outlet model turns hardware support into a reusable system capability.

## More Scenarios

The current private architecture catalog also tracks car, smart-home, entertainment, presentation, VR, Time Machine, proactive-agent, parallel-execution, compatibility, and replay scenarios. They will move into public documentation as they become concrete enough to explain responsibly.

Return to the [project overview](../README.md), read the [Vision](VISION.md), or follow [Announcements](ANNOUNCEMENTS.md).
