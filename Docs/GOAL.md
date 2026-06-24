# Goals

## Why this exists

Two skills, kept sharp by hand:

1. **Staying current with new SwiftUI.** SwiftUI changes every year. This lab tracks the newest APIs — currently those from WWDC26 — by building real things with them early, beta rough edges included.

2. **Building beautiful UI.** Mostly independent of which APIs exist: spacing, motion, restraint, polish. This is craft, and craft only improves with deliberate practice.

The deeper goal is staying sharp as a developer in an era when AI can generate most code on demand. The way to keep a skill is to use it. So in this lab:

- The first working version of every experiment is written by hand, not generated.
- Where it helps, build it **wrong first** — hit the sharp edge directly — then fix it. The friction is the point, not a problem to optimize away.

## Non-goals

- **Not a package or dependency.** No API stability, no semver, no consumers to protect.
- **Not production code.** Beta APIs, incomplete probes, and throwaway experiments are all fine here.
- **Not backward compatibility.** Most WWDC26 SwiftUI APIs don't offer it, and this lab doesn't work around that.
- **Not completeness.** A focused probe that teaches one thing beats an exhaustive tutorial.

## Keeping it honest

SwiftUI moves fast. A clever workaround from one release is often dead — or now native — in the next. To avoid leaving misinformation lying around for future-me or anyone who copies from here:

- Every experiment records its minimum OS and a status: `current`, `superseded`, or `deprecated`.
- After each major OS release, sweep the experiments and re-mark anything replaced by a native API.

That sweep is part of the work, not overhead. It's how the knowledge stays worth keeping.