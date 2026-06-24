# App Structure

## Principle

Keep it light. This is a lab, not a framework. Structure should make experiments easy to add and easy to browse — nothing more. Resist building taxonomy or shared infrastructure before there are real experiments to justify it.

## Shape

A single Xcode project with one app target. No Swift package, for now — that boundary exists to serve external consumers, and there aren't any. Add one later only if sharing becomes a real need.

```
SwiftUILab/
├── README.md
├── SwiftUILab.xcodeproj
├── App/
│   ├── SwiftUILabApp.swift       // entry point
│   ├── CatalogView.swift         // the browsable list of experiments
│   └── ExperimentRegistry.swift  // registers experiments for the catalog
├── Experiments/
│   ├── LiquidGlassActiveState/
│   │   ├── LiquidGlassActiveState.swift
│   │   └── NOTES.md
│   ├── ProminentTab/
│   │   ├── ProminentTab.swift
│   │   └── NOTES.md
│   └── ...
├── Shared/                       // only what's genuinely reused
└── Docs/
    ├── GOAL.md
    ├── APP_STRUCTURE.md
    └── EXPERIMENT_TEMPLATE.md
```

## An experiment

One folder under `Experiments/`, containing:

- One or more Swift files with the SwiftUI views.
- A `NOTES.md` (copy from `Docs/EXPERIMENT_TEMPLATE.md`) recording what it tests, minimum OS, status, and what was learned.

Each experiment exposes a single entry view through a small protocol so the catalog can list and present it:

```swift
protocol Experiment {
    static var title: String { get }
    static var minimumOS: String { get }
    associatedtype Body: View
    @ViewBuilder static func makeView() -> Body
}
```

Treat that protocol as a draft. Refine it once the first two or three experiments exist — don't lock the shape before real experiments show what it needs.

## The catalog

`CatalogView` lists registered experiments: searchable, and grouped by category only once there are enough to warrant grouping. Where practical, an experiment screen shows the live result and its source side by side. That pairing is what makes this a showcase rather than a folder of files.

## À la carte vs shared

Decide this per experiment and record it in the experiment's notes:

- **Standalone** — the experiment duplicates anything small it needs, so the whole folder copies cleanly. Default for small UI tricks.
- **Shared** — the experiment depends on helpers in `Shared/`. Fine for substantial work, but the copy unit becomes "the experiment plus its dependencies."

Don't move a helper into `Shared/` until a second experiment actually needs it. Premature sharing turns standalone experiments into a tangle.

## Order of work

Build the first experiment fully — view, notes, and a hardcoded catalog entry — before generalizing anything. Let the registry, the protocol, and any categories fall out of two or three real experiments. Building the shell, navigation, and theming before there's content is the most likely way to stall this project.