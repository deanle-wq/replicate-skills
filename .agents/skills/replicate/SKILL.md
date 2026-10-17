---
name: replicate
description: Replicate a feature from an existing app into the user's own project. Investigate how the app does it with REA (Electron/JavaScript, native binaries, Android, .NET, websites), show the evidence, then build a clean-room version and test it. Use when the user says "replicate", "how does <app> do <feature>", "build something like <app>'s <feature>", or wants a feature from a shipped app whose source they don't have.
---

# Replicate

Turn "I like how <app> does <feature>" into a working version in the user's
project, built from observed behavior rather than copied code.

This skill is the workflow. Tool routing, setup and recovery live in the REA
guide, [reverse-engineer-anything](../reverse-engineer-anything/SKILL.md).
Read it before the first REA call in a session.

## 1. Pin down the job

Confirm three things, asking only for what the conversation doesn't already say:

- **Target**: which app, and where it is on disk (installed `.app`, ASAR, APK,
  URL). Never pick one for the user.
- **Feature**: the behavior in one sentence, as the user experiences it.
- **Destination**: the project and stack it should land in.

## 2. Investigate with REA

Follow the REA guide's routing for the target type. Electron/JavaScript is
usually the fastest route; native binaries need Hopper, Ghidra or IDA.

Start from a user-visible entry point (menu item, shortcut, UI string, IPC
channel, network call) and trace inward. Stop once the behavior is explained;
don't map the whole app.

## 3. Write the behavior spec

Before writing code, give the user a short spec:

- What the feature does: inputs, outputs, states, edge cases.
- How the app does it, citing Evidence IDs, with **observed**, **inferred** and
  **unknown** kept apart.
- What can't be seen: server-side logic, obfuscated or protected code, anything
  that never ships to the device.

## 4. Build a clean-room version

Implement it in the destination project's own style. Re-create the behavior and
algorithm, not the code: don't paste decompiled code, original strings, assets
or proprietary data. Where the spec has unknowns, make a design choice and say
so.

## 5. Verify

Test against the spec. When the original can be run safely, feed both the same
inputs and report what matches and what doesn't.

## 6. Learn

At the end, if something would make the next run faster (a tool quirk, a route
that worked, a dead end, a setup fix), propose a one-line entry for Field notes
below and add it once the user agrees.

## Boundaries

Stay within REA's
[responsible-use terms](https://github.com/morluto/rea/blob/main/DISCLAIMER.md):
no DRM, license-check or anti-cheat bypass, and no cloning proprietary code or
assets. Only analyze software the user is allowed to examine.

## Field notes

<!-- One line per lesson: what happened -> what to do next time. Newest first. -->

- (none yet)
