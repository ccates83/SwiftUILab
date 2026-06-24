# SwiftUI Lab

A personal lab for experimenting with SwiftUI, focused on the newest APIs and on building beautiful, polished UI.

This is **not** a library or a package you add as a dependency. It's a single demo app: a browsable collection of self-contained experiments, each showing one SwiftUI idea running live, with notes on how it works and where it breaks.

## What this is

- A place to learn the newest SwiftUI by building with it, by hand.
- A catalog app you can run, browse, and read the source of.
- Notes on the sharp edges — the things the documentation doesn't tell you.

## What this isn't

- **Not a dependency.** Nothing here is versioned or stable for import.
- **Not production-ready code.** Many experiments target beta APIs that ship in the 2027 OS releases and have no backward compatibility.
- **Not exhaustive tutorials.** Each experiment is a focused probe, sometimes deliberately incomplete.

## Requirements

Built against the SwiftUI APIs introduced at WWDC26. Most experiments require:

- Xcode 27 or later
- iOS 27 (or the corresponding 2027 OS releases)

Some experiments run on earlier toolchains; each one records its own minimum OS.

## Running it

1. Clone the repo.
2. Open `SwiftUILab.xcodeproj` in Xcode 27+.
3. Build and run. Browse experiments from the main catalog.

## How it's organized

Each experiment is a self-contained folder under `Experiments/`, surfaced automatically in the app's catalog. See [`Docs/APP_STRUCTURE.md`](Docs/APP_STRUCTURE.md).

## Reusing this

You're welcome to copy anything useful. Most experiments are written to stand alone — paste the folder and go. Before reusing, check the experiment's `NOTES.md` for its minimum OS and whether the API has since been replaced by something native. Because this lab tracks the newest releases, an older experiment may show a workaround that is now obsolete.

## License

This repository has no license yet, which means default copyright applies and others can't legally reuse it. Add one (MIT is a reasonable default for a public, reusable resource) if reuse is intended.