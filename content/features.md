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

## Compile preview, in-place

A Preview tab in the Manuscript Builder renders the current preset's compile output as continuous read-only prose, no real export file needed. Tweak settings on Build, flip to Preview, see the impact, iterate.

<figure>
  <img src="/img/dbench-manuscript-builder-preview.png" alt="The Manuscript Builder modal with the Preview tab active, showing a typography toolbar (text alignment, reading width, font-size stepper, font-family dropdown) above three chapter-style headings rendered as continuous prose." loading="lazy">
  <figcaption>The Preview tab renders the current preset's output as continuous read-only prose; the typography toolbar at the top tunes alignment, reading width, font size, and font family.</figcaption>
</figure>

Dock the Builder as a workspace tab to keep Preview pinned next to a scene you're editing. The leaf form re-renders as you save, debounced ~400ms; scroll position is preserved across re-renders so deep reading isn't reset to the top.

<figure>
  <img src="/img/dbench-manuscript-builder-leaf.png" alt="A three-pane Obsidian workspace: the Manuscript view in the left sidebar, a scene file open in source mode in the middle pane, and the Manuscript Builder docked as a workspace leaf on the right with Preview rendering the compiled prose." loading="lazy">
  <figcaption>Builder docked as a workspace leaf — Preview pinned on the right while a scene stays open and editable in the main pane.</figcaption>
</figure>

Both behaviors shipped in 0.3.x — Preview tab in 0.3.0, leaf form with file-save reactivity in 0.3.1.

---

## Importing from Scrivener

A multi-step wizard reads a Scrivener 3 project bundle from inside the vault and produces a fresh Draft Bench project. Chapters, scenes, sub-scenes, drafts, and inspector content all carry across; every mapping is reviewed in a Preview step before any file gets written.

<video autoplay muted loop playsinline preload="metadata"
       src="/img/dbench-scrivener-import.webm"
       aria-label="The Scrivener import wizard running end-to-end against a sample Scrivener 3 novel-template project: a .scriv folder is dropped onto the Source step, the Parse step renders the counts summary, the Hierarchy step shows auto-detected scene and chapter rows, the Metadata step routes statuses and custom fields, the Options step exposes the snapshot template, the Preview step shows the file tree, and the Complete step reports success."></video>

### What it does

- **Reads `.scrivx` + RTF/RTFD bodies.** Scrivener 3 binder hierarchy, document text, snapshots, and inspector content are parsed into an in-memory model.
- **Maps the binder to Draft Bench's four levels.** Auto-detection runs on parse: deepest leaves with prose -> scenes; immediate folder parents -> chapters; anything above the chapter level (Parts, Books, Volumes) becomes `scrivener-part` frontmatter on the chapters they contain; sub-sub-scenes concatenate as nested headings inside the parent sub-scene. A per-row override dropdown surfaces in the Hierarchy Mapping step for any auto-detection that doesn't fit.
- **Routes statuses, labels, and custom metadata interactively.** Scrivener statuses match against Draft Bench's status vocabulary; unmatched rows can add to the vocabulary or drop. Labels go to a writer-named frontmatter key (default `scrivener-label`). Custom metadata routes per-field with type-aware coercion: Checkbox to boolean, List to resolved option title, Date to ISO `YYYY-MM-DD`, Text to raw string.
- **Converts RTF bodies to markdown.** Italics, bold, lists, smart quotes, em-dashes, footnotes (inline + inspector), comments (rendered as Obsidian `%% %%` syntax at the original anchor), inline images (extracted to `Research/Images/`), and cross-document Scrivener Links (rewritten to wikilinks via a UUID-to-path map) all carry across. Complex RTF tables fall back to inline HTML and are flagged in the import error log.
- **Optional snapshot import.** Per-document Scrivener snapshots become `dbench-type: draft` files alongside each scene. Per-scene cap (1 / 3 / 5 / All); filename template with variables `{scene}` `{title}` `{date}` `{date_compact}` `{time}` `{n}`. Original Scrivener title preserved as `scrivener-snapshot-title` frontmatter regardless of whether `{title}` appears in the template.
- **Optional Research import.** The Research folder and any other non-manuscript top-level folders carry across with hierarchy preserved verbatim. Templates and Trash are always skipped.
- **Cross-platform.** The importer reads via Obsidian's vault adapter on every supported OS. Mobile users (Android verified; iOS / iPadOS untested) get the same wizard and the same write pass.

<figure>
  <img src="/img/dbench-scrivener-import-source.png" alt="Step 1 of the Scrivener import wizard: the Source step, where a .scriv bundle is selected from inside the vault" loading="lazy">
  <figcaption>Source — pick a `.scriv` bundle from inside the vault.</figcaption>
</figure>

<figure>
  <img src="/img/dbench-scrivener-import-parse.png" alt="Step 2 of the Scrivener import wizard: the Parse step, with a counts summary of binder items, RTF documents, snapshots, and custom metadata fields" loading="lazy">
  <figcaption>Parse — counts of binder items, documents, snapshots, and custom metadata fields surface up front.</figcaption>
</figure>

<figure>
  <img src="/img/dbench-scrivener-import-hierarchy.png" alt="Step 3 of the Scrivener import wizard: the Hierarchy Mapping step, showing auto-detected scene and chapter rows with per-row override dropdowns" loading="lazy">
  <figcaption>Hierarchy Mapping — auto-detection assigns each binder item to project / chapter / scene / sub-scene; per-row dropdowns override anything that doesn't fit.</figcaption>
</figure>

<figure>
  <img src="/img/dbench-scrivener-import-metadata.png" alt="Step 4 of the Scrivener import wizard: the Metadata step, routing Scrivener statuses, labels, and custom-metadata fields into Draft Bench's vocabulary" loading="lazy">
  <figcaption>Metadata — statuses match against the Draft Bench vocabulary, labels route to a writer-named frontmatter key, and custom metadata routes per-field with type-aware coercion.</figcaption>
</figure>

<figure>
  <img src="/img/dbench-scrivener-import-snapshots.png" alt="Step 5 of the Scrivener import wizard: the Options step, with the optional snapshot import controls — per-scene cap and filename template" loading="lazy">
  <figcaption>Options — opt into snapshot import with a per-scene cap and a filename template.</figcaption>
</figure>

<figure>
  <img src="/img/dbench-scrivener-import-preview.png" alt="Step 6 of the Scrivener import wizard: the Preview step, showing the file tree of files about to be written" loading="lazy">
  <figcaption>Preview — every file the importer is about to write, before any vault changes happen.</figcaption>
</figure>

<figure>
  <img src="/img/dbench-scrivener-import-complete.png" alt="Step 7 of the Scrivener import wizard: the Complete step, reporting a successful import with file counts" loading="lazy">
  <figcaption>Complete — successful import with file counts; any non-fatal warnings show in the import error log.</figcaption>
</figure>

### What V1 doesn't do

- **Scrivener 2 and iOS Scrivener formats.** Different schema and bundle structure. Re-add as separate parser paths post-V1 if a contributor surfaces with a project to test against.
- **Reading `.scriv` bundles from outside the vault.** Copy the bundle into the vault first. The wizard's Source step can do the copy on most platforms via drag-drop or the device picker.
- **Compile-format translation.** Scrivener compile presets don't map cleanly to Draft Bench compile presets. Build your DB presets from scratch after import.
- **DB -> Scrivener export.** No demand for the reverse direction.

Full walkthrough, mapping reference, and troubleshooting at the [wiki page](https://github.com/banisterious/obsidian-draft-bench/wiki/Importing-from-Scrivener).

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
