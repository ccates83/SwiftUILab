# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A personal lab for experimenting with the newest SwiftUI APIs and practicing polished UI craft. It is a single demo app — **not** a library, package, or dependency. There is no API stability, no semver, no backward compatibility. Read `Docs/GOAL.md`, `Docs/APP-STRUCTURE.md`, and `Docs/EXPERIMENT-TEMPLATE.md` before doing substantial work; they are the source of truth for intent and conventions.

## Working philosophy (read before generating code)

This repo has an unusual constraint that overrides normal "just write the code" behavior:

- **The first working version of every experiment is written by hand, not generated.** The point of the lab is to keep the user's SwiftUI skills sharp. Do not author the initial implementation of an experiment for the user. Help with scaffolding, notes, debugging, review, and refactoring of *existing* hand-written code — but let the user write the first pass themselves unless they explicitly ask otherwise.
- **"Build it wrong first" is intentional.** Experiments often deliberately hit a sharp edge before fixing it. Don't pre-emptively "correct" a naive approach the user is working through — the friction is the lesson.
- **Resist premature structure.** Don't build shared infrastructure, registries, theming, or taxonomy before real experiments justify them. See `Docs/APP-STRUCTURE.md` ("Order of work").

## Current state vs. planned structure

The repo currently contains only the default Xcode template (`ContentView.swift`, `SwiftUILabApp.swift`) — no experiments exist yet. The `App/`, `Experiments/`, and `Shared/` folders described in `Docs/APP-STRUCTURE.md` are **aspirational**; they fall out of real work, not up front. Build the first experiment fully (view + `NOTES.md` + a hardcoded catalog entry) before generalizing the registry or the `Experiment` protocol.

When adding an experiment: one folder under `Experiments/`, containing the Swift view file(s) plus a `NOTES.md` copied from `Docs/EXPERIMENT-TEMPLATE.md`. Default to **standalone** (the folder copies cleanly); only depend on `Shared/` for substantial work, and never promote a helper to `Shared/` until a second experiment actually needs it.

## Project layout note

The Xcode project lives one level down: the git repo root is `SwiftUILab/`, and the Xcode project is at `SwiftUILab/SwiftUILab.xcodeproj`. Run `xcodebuild` from the `SwiftUILab/` subdirectory (the one containing `.xcodeproj`).

## Build, run, test

Scheme: `SwiftUILab`. Tests use **Swift Testing** (`import Testing`, `@Test`, `#expect`) — not XCTest — except the UI test target which uses XCTest.

```bash
cd SwiftUILab   # the dir containing SwiftUILab.xcodeproj

# Build for simulator
xcodebuild -project SwiftUILab.xcodeproj -scheme SwiftUILab \
  -destination 'platform=iOS Simulator,name=iPhone 16' build

# Run all tests
xcodebuild -project SwiftUILab.xcodeproj -scheme SwiftUILab \
  -destination 'platform=iOS Simulator,name=iPhone 16' test

# Run a single Swift Testing test by name
xcodebuild -project SwiftUILab.xcodeproj -scheme SwiftUILab \
  -destination 'platform=iOS Simulator,name=iPhone 16' \
  test -only-testing:SwiftUILabTests/SwiftUILabTests/example
```

Most day-to-day iteration happens in Xcode itself (build/run with ⌘R, SwiftUI previews via `#Preview`). Prefer previews for fast UI iteration.

## Project facts

- Deployment target: iOS 26.5 (the project file's actual setting; the README aspirationally references iOS 27 / WWDC26 / Xcode 27).
- Bundle ID: `com.cc.SwiftUILab`. Swift 5.0 language mode.

## Keeping experiments honest

Every experiment's `NOTES.md` records minimum OS and a status: `current`, `superseded`, or `deprecated`. After a major OS release, sweep experiments and re-mark anything a native API has replaced. Treat that sweep as part of the work — it's how the lab avoids leaving obsolete workarounds lying around.
