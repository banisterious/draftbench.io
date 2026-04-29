---
title: "Features"
description: "Inside Draft Bench: the Manuscript view, versioned drafts, and the compile flow. Each section pairs a short walk-through with a motion loop captured from a real vault."
showTableOfContents: true
---

A walk-through of Draft Bench in action. Each section pairs a short factual description with a captured motion loop from a real vault. The plugin handles the manuscript spine — projects, chapters, scenes, drafts, and compile — and stays out of plotting, entity management, and analytics.

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
