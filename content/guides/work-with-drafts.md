---
title: "I want to work with drafts of a scene"
description: Snapshot a scene's current state as an archived draft, then continue revising in the source. Each draft is a real markdown file you can revisit, link, or compile.
difficulty: easy
time_estimate: ~5-10 min
last_reviewed: 2026-05-10
relevant_releases: 0.5.x
weight: 30
sitemap:
  priority: 0.7
---

You've written a scene and you want to revise it without losing what's there. A draft in Draft Bench is an archived snapshot of the scene's current state, written to its own markdown file. The source scene note carries the prose forward; you keep revising, the snapshot stays put. By the end of this you'll have created a draft of a scene, found it in the vault, and confirmed the source scene is ready for the next pass.

## What you'll need

- A Draft Bench project with at least one scene that has body content (a draft of an empty scene snapshots an empty file - works, but not useful).

## Steps

### 1. Snapshot the scene as a draft

Open the scene you want to draft. Three ways to invoke the snapshot:

- Command palette: **Draft Bench: New draft of this scene**.
- The Manuscript view toolbar (when the scene is selected).
- Right-click the scene note in the file explorer or Manuscript view -> **New draft of this scene**.

A confirmation modal previews the new draft's path (typically `Drafts/<Scene> - Draft N (YYYYMMDD).md` - the exact path depends on your **Drafts folder placement** setting). Confirm.

Draft Bench:

- Writes the new draft as a markdown file with the scene's current body.
- Stamps the draft's frontmatter: `dbench-type: draft`, `dbench-scene: [[<Scene>]]`, `dbench-draft-number: N`, `dbench-created-at: YYYY-MM-DD`.
- Auto-numbers the draft (you never manage `N` manually).
- **Carries the prose forward** in the source scene note; you continue revising there, not starting blank.

### 2. Verify the draft exists

Open your file explorer (or run a search for the draft's filename). The draft is a real markdown file at the configured path. You can:

- Open it in a split pane to read alongside the revised scene.
- Link to it via `[[<Scene> - Draft N (YYYYMMDD)]]` from anywhere.
- Open it in another tool (it's plain markdown with YAML frontmatter).

The source scene's frontmatter now has reverse-link arrays - `dbench-drafts` and `dbench-draft-ids` - listing every draft that points at it. Open the scene note and you'll see them in the properties panel.

### 3. Continue revising

The scene body stayed in place; revise as you would normally. When you reach the next milestone worth archiving, run **Draft Bench: New draft of this scene** again. The new draft auto-numbers (Draft 2, Draft 3, ...) and the reverse-link array on the scene grows.

## Variations

- **If you want drafts of a chapter** (the chapter note as a whole, not its scenes): run **Draft Bench: New draft of this chapter** while the chapter note is open. The snapshot includes the chapter's accumulated body. Same pattern as scene drafts - separate command, separate folder convention.

- **If you want drafts of a sub-scene**: run **Draft Bench: New draft of this sub-scene**. Sub-scenes have their own draft history independent of the parent scene.

- **If your single-scene-shape project needs drafts**: a single-scene project IS the scene; running **New draft of this scene** on the project note works the same way. (Created via the **Single scene** Shape option in the new-project modal - see [start-a-writing-project](/guides/start-a-writing-project/).)

- **If you want drafts in a different location**: change the **Drafts folder placement** setting (Settings -> Draft Bench). Three placements available: per-scene sibling folder (default), project-local (one `Drafts/` under each project), or vault-wide root (one shared `Drafts/` at the vault root). Future drafts honor the new placement; existing drafts stay where they were.

- **If you want a draft included or excluded from a compile**: drafts can be referenced from compile presets the same as scenes. See [compile-your-manuscript](/guides/compile-your-manuscript/) for how presets pick which files to include.

## Related guides

- [I want to start a writing project from scratch](/guides/start-a-writing-project/) - prerequisite if you don't have a project / scene yet.
- [I want to compile my manuscript](/guides/compile-your-manuscript/) - drafts can feed into compiles selectively.
- [I want to view my project in a Bases table](/guides/view-project-in-bases/) - the Drafts.base includes a "history for current scene" view that surfaces all drafts of the active scene.

## Reference

- Wiki: [Drafts and versioning](https://github.com/banisterious/obsidian-draft-bench/wiki/Drafts-And-Versioning) - full reference including chapter/sub-scene drafts, the auto-numbering rule, and the comparison vs Longform's parallel-tree model.

---

*Found something wrong or unclear? [Suggest an edit][issue-link] - opens a pre-filled issue with the `guides` label.*

[issue-link]: https://github.com/banisterious/obsidian-draft-bench/issues/new?labels=guides&title=%5BGuides%5D+work-with-drafts%3A+
