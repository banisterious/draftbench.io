---
title: "Features"
description: "Inside Draft Bench: new projects, the Manuscript view, versioned drafts, compile, Bases discovery, integrity, and theming — each section pairs a short walk-through with media captured from a real vault."
showTableOfContents: true
---

A walk-through of Draft Bench in action. Each section pairs a short factual description with media captured from a real vault — five motion loops showing flows in real time, plus stills for state and configuration. The plugin handles the manuscript spine — projects, chapters, scenes, drafts, and compile — and stays out of plotting, entity management, and analytics.

---

## New project

The Create Project command opens a modal that collects a title and shape (chapter-based or single-scene). The project folder lands in the file explorer with stamped frontmatter on the project note (`dbench-type: project`, `dbench-id`, `dbench-status`), and the Manuscript view auto-reveals on the right ready to fill in.

<video autoplay muted loop playsinline preload="metadata"
       src="/img/dbench-create-project.webm"
       aria-label="Creating a new Draft Bench project from an empty Obsidian vault: the command palette opens, the New Project modal collects a title and shape, the project folder appears in the file explorer, and the Manuscript view auto-reveals with the project's frontmatter visible."></video>

---

## Write

The Manuscript view docks in the sidebar as a workspace leaf. Chapter cards expand to reveal scene rows. Scene titles open in new tabs via Cmd-click. The Reorder Scenes modal handles structural moves without dragging files around in the explorer. Word counts roll up live per chapter and per project as prose is added.

<video autoplay muted loop playsinline preload="metadata"
       src="/img/dbench-manuscript-view.webm"
       aria-label="The Manuscript view in action: a chapter card expands smoothly, a scene title opens in a new tab via Cmd-click, scene order is updated via the Reorder Scenes modal, and word counts tick live as prose is added."></video>

---

## Versioned drafts

A draft is a `dbench-type: draft` note — a snapshot of a scene, chapter, or single-scene project at a point in time. Captured via right-click → New draft of this scene, with a preview modal confirming the target path before the snapshot is taken. The resulting note opens with stamped frontmatter (`dbench-scene`, `dbench-draft-number`, and related properties), and the draft count surfaces back in the Manuscript view as a badge on the source scene.

<video autoplay muted loop playsinline preload="metadata"
       src="/img/dbench-new-draft.webm"
       aria-label="Taking a new draft of a scene: the right-click context menu opens, the New draft of this scene action is selected, a preview modal confirms the snapshot path, and the new draft note opens with stamped frontmatter."></video>

---

## Compile

The Compile CTA in the Manuscript view opens the Manuscript Builder modal. Each preset is itself a `dbench-type: compile-preset` note with content-handling rules — frontmatter strip, heading scope, footnote renumbering, embed handling, dinkus normalization — editable in the Properties panel or the Compile tab. Run compile, and the resulting markdown manuscript opens in the active leaf.

<video autoplay muted loop playsinline preload="metadata"
       src="/img/dbench-compile-flow.webm"
       aria-label="The compile flow: clicking Compile in the Manuscript view opens the Manuscript Builder modal, the Run compile action runs the preset, and the resulting markdown manuscript opens in the vault."></video>

<figure>
  <img src="/img/dbench-compile-preset-properties.png" alt="Compile preset note's Properties panel showing dbench-compile rules for frontmatter, heading scope, footnote renumbering, embed handling, and dinkus normalization" loading="lazy">
  <figcaption>Compile presets are notes. Their content-handling rules live in the Properties panel — editable like any other frontmatter, queryable via Bases.</figcaption>
</figure>

---

## Bases-native discovery

Starter `.base` views ship for projects, scenes, and drafts. Filter, group, and surface your manuscript with the same Bases setup you use for everything else in your vault — no plugin-specific query language, no parallel data store.

<figure>
  <img src="/img/dbench-bases-projects.png" alt="Starter Bases view for Draft Bench projects, showing a table of project notes with title, status, and word-count columns" loading="lazy">
  <figcaption>Starter Bases views for projects, scenes, and drafts ship with the plugin.</figcaption>
</figure>

---

## Integrity

The plugin maintains stable IDs and reverse-link arrays as the vault changes. When state drifts — a renamed scene, a deleted chapter, an out-of-band frontmatter edit — the Repair project links modal scans for inconsistencies and lists each issue with auto-repairable and manual-review counts. Auto-repairs run in batch on click; the leaf carrying the project is forward-ref-driven and reflects the repaired state once the modal closes.

<video autoplay muted loop playsinline preload="metadata"
       src="/img/dbench-repair-integrity.webm"
       aria-label="The Repair project links modal scans a project for inconsistencies, lists detected issues with auto-repairable and manual-review counts, applies the auto-repairs on click, and confirms the repaired state."></video>

---

## Theming

Class hooks and minimum defaults; Style Settings exposes per-component variables for opt-in customization. The plugin doesn't impose chrome on writers who customize their vault's appearance.

<figure>
  <img src="/img/dbench-style-settings.png" alt="Obsidian Style Settings panel showing exposed Draft Bench variables for spacing, typography, and color overrides" loading="lazy">
  <figcaption>Per-component variables exposed via Style Settings — adjust without writing CSS overrides.</figcaption>
</figure>
