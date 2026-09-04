# aba-language-lessons

## What this repo is

A **content repo, not a software project** — there is no application code, no
`package.json`/`requirements.txt`, no build or test commands. It holds the
generation pipeline and output for ESL (English as a Second Language) lessons
across three modalities: **Reading**, **Listening/Speaking**, and **Writing**.

The "pipeline" is manual: long Markdown prompt documents get pasted into an AI
chat tool (Claude, and others historically) to generate lesson content, which
comes back as Markdown lesson docs plus self-contained, inline-styled HTML
"student packet" printables.

Each modality was originally developed independently (in different AI tools,
at different times) and is now being **consolidated into this repo** as the
single source of truth. That consolidation is in progress and is why the three
modalities currently look and are organized differently — see Known Issues
below. Prior working location before consolidation: `~/Desktop/ESL Content/`.

## Shared taxonomy

All three modalities key off the same skill taxonomy defined in
[`learningobjectives.csv`](learningobjectives.csv): **8 Levels × 8 Modules**
(Module 1: Describing … Module 8: Socializing), banded into
Beginner / Intermediate / Advanced / Proficient.

## Repo layout

Each modality folder is intended to have this shape:

```
<modality>/
├── Master_Generation_Document.md   # living index: prompt versions, sync status, pending work
├── Program_Rotation_Log.md         # tracks every generated lesson (topic/skill rotation, avoids repeats)
├── lessons/{beginner,intermediate,advanced,proficient}/
├── prompts/                        # versioned generation prompts
└── source/
```

Each modality's actual lesson cycle differs by design:

- **`reading/`** — 2-day lesson / 4-lesson module, built around one shared
  anchor text with lettered `[STOP & CHECK]` checkpoints.
- **`listening-speaking/`** — 2-day lesson (Day 1 Listening / Day 2 Speaking),
  built around one real, sourced audio/video clip (URL, speaker, platform,
  runtime, glossary pulled from the source's own captions) — no printed
  passage.
- **`writing/`** — 8-day lesson built around a shared "Scenario" plus a
  **Leveled Mentor Set** (one exemplar per task Level) instead of a single
  shared anchor text, with a Focus A/Focus B grammar pairing structure. No
  module concept yet — lessons are generated one at a time against a flat
  rotation log.

## Canonical conventions (apply going forward)

These reconcile inconsistencies found during consolidation. When generating
or renaming content, use these — don't propagate the older mismatched styles
noted in Known Issues.

- **Master docs**: name as `<Modality>_Master_Generation_Document.md` and
  `<Modality>_Program_Rotation_Log.md` for every modality (e.g.
  `Reading_Master_Generation_Document.md`). Reading's current generic
  `Master_Generation_Document.md` / `Program_Rotation_Log.md` are the
  outliers to rename.
- **Lesson files**: one naming scheme repo-wide — Reading's terse slug style
  is the target (`Lesson<N>_<TopicSlug>.md`,
  `<TopicSlug>_<Level>_L<N>_Packet.html`). Listening/Speaking currently has
  two divergent long-form styles (underscore-heavy vs. spaces/commas) that
  should migrate to this.
- **Master Generation Documents must only reference filenames that actually
  exist on disk.** Several currently describe files/content that were never
  saved, or that were saved under different names — treat any such mismatch
  as a bug to fix (either regenerate the missing content or correct the doc).
- **HTML student packets**: keep the shared CSS custom-property tokens
  (`--ink`, `--paper`, `--rule`, etc.) as the single source of truth for
  print styling across modalities; normalize generated-markup formatting
  (indentation, self-closing tags) so packets don't visibly differ by which
  session/tool produced them.

## Known issues / pending consolidation work

- `writing/lessons/` is **empty**, but `writing/Academic Writing Program
  Rotation Log.md` describes two fully generated, multiply-revised lessons
  (Intermediate 1 "my phone case," Advanced 1 "Two apartments... for Sam") as
  current/synced. That content appears to have never been saved into this
  repo and needs to be regenerated or recovered.
- `listening-speaking/lessons/intermediate/Listening_Speaking_Module_1__Intermediate__-_Set_1_Assessment.md`
  is a 1-line corrupted stub (a mangled filename string, not content), while
  the master doc claims this assessment was generated with real content
  (Part A/Part B, real source) — likely lost during consolidation and needs
  regenerating.
- Reading's `Master_Generation_Document.md` and `Program_Rotation_Log.md`
  reference filenames that don't match what's actually on disk, e.g. doc says
  `Passage Reading Lesson Generation Prompt v2.7 BandCalibrated.md` /
  `Module 1 Lesson 1 - A Grandmother's Kitchen.md`, but the real files are
  `Lesson_Generation_Prompt_v2.7_CURRENT.md` / `Lesson1_Kitchen.md`. Needs
  reconciling (fix the docs to match reality, not the other way around).
- Writing has no Module-Lesson-Plan, Homework, or Assessment prompt yet (only
  a Lesson Generation prompt and a Student Print Formatting prompt) — flagged
  as pending in its own master doc.
- Within Listening/Speaking itself, intermediate lessons use
  `Listening_Speaking_Module_1__Lesson_1__Intermediate__-_....md` while
  advanced lessons use `Listening Speaking Module 1, Lesson 1 (Advanced) -
  ....md` — two schemes in one modality; migrate both to the canonical slug
  style above.

## Working notes for future sessions

- There's nothing to build, run, lint, or test — "verification" here means
  checking that a modality's Master Generation Document and Rotation Log
  actually match the files present in its `lessons/` and `prompts/` folders,
  and that a lesson's HTML packet stays structurally/stylistically
  consistent with its Markdown source and with other modalities' packets.
- When adding or renaming lesson files, follow the canonical conventions
  above rather than matching whatever scheme is already in that modality's
  folder — the point of this repo is to converge on one scheme.
