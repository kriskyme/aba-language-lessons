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

A modality can hold more than one **lesson type** — a fixed generation format
with its own prompt family, rotation log, and lessons — so every modality
folder is one level of grouping above that:

```
<modality>/
├── Index.md                 # thin: lists this modality's lesson type(s), points into each
└── <lesson-type>/           # one subfolder per lesson type this modality generates
    ├── Index.md              # living index: what each file does, sync status, pending work
    ├── Changelog.md          # dated version history for this lesson type's prompt family
    ├── Rotation_Log.md       # tracks every generated lesson (topic/skill rotation, avoids repeats)
    ├── lessons/{beginner,intermediate,advanced,proficient}/
    ├── prompts/              # versioned generation prompts
    └── source/               # raw reference material (see note below)
```

`source/` holds raw text pasted in from outside sources (textbook excerpts,
sample transcripts) as generation reference material — not lesson output, and
not something to read by default. Each modality's `source/` currently holds
one large file (1,000+ lines). Open it only when a task specifically calls
for consulting the source material (e.g. checking a prompt's claims against
it), not as part of general repo work.

Worked example: `reading/passage-reading/` (Reading's one active lesson
type today; `reading/novel-reading/` is planned as a sibling once real work
on it starts — see `reading/Index.md`). `listening-speaking/` and `writing/`
currently have exactly one lesson type each, so they each hold exactly one
such subfolder (`listening-speaking/listening-speaking/`,
`writing/academic-writing/`) — the lesson-type folder is named after what the
docs call that lesson type, not forced to match the modality name, so
Listening/Speaking's repeats the modality name (it has no more specific name
yet) while Writing's doesn't (its one lesson type has always been called
"Academic Writing").

No modality or lesson-type prefix on the three per-lesson-type filenames —
the folder path already says which lesson type it is. When referring to one
from a *different* lesson type's doc, name the lesson type in prose instead
(e.g. "Passage Reading's `Index.md`"), since "Index.md" alone is ambiguous
across folders.

Each lesson type's actual cycle differs by design:

- **Passage Reading** (`reading/passage-reading/`) — 2-day lesson / 4-lesson
  module, built around one shared anchor text with lettered
  `[STOP & CHECK]` checkpoints.
- **Novel Reading** (planned, `reading/novel-reading/`) — not yet started;
  expected to be variable-length/multi-chapter, a different enough shape
  (e.g. an 8-day format spanning what Passage Reading treats as two modules)
  that it can't share Passage Reading's prompt family.
- **Listening/Speaking** (`listening-speaking/listening-speaking/`) — 2-day
  lesson (Day 1 Listening / Day 2 Speaking), built around one real, sourced
  audio/video clip (URL, speaker, platform, runtime, glossary pulled from the
  source's own captions) — no printed passage.
- **Academic Writing** (`writing/academic-writing/`) — 8-day lesson built
  around a shared "Scenario" plus a **Leveled Mentor Set** (one exemplar per
  task Level) instead of a single shared anchor text, with a Focus A/Focus B
  grammar pairing structure. No module concept yet — lessons are generated
  one at a time against a flat rotation log.

## Canonical conventions (apply going forward)

These reconcile inconsistencies found during consolidation. When generating
or renaming content, use these — don't propagate the older mismatched styles
noted in Known Issues.

- **Nest by lesson type, not just modality.** Every modality folder holds one
  subfolder per lesson type it generates — even a modality with only one
  today (`listening-speaking/listening-speaking/`, `writing/academic-writing/`)
  — plus a thin modality-level `Index.md` that just lists the lesson type(s)
  and points into each. Don't put lesson-type content directly in the
  modality folder; a second lesson type should never require restructuring
  what's already there.
- **Per-lesson-type docs**: `Index.md`, `Changelog.md`, `Rotation_Log.md` — no
  modality or lesson-type prefix, `Title_Case_With_Underscores` for
  multi-word names. Already applied across all three modalities.
- **Lesson files**: one naming scheme repo-wide — Reading's terse slug style
  is the target (`Lesson<N>_<TopicSlug>.md`,
  `<TopicSlug>_<Level>_L<N>_Packet.html`). Listening/Speaking has migrated
  both of its former divergent long-form styles to this.
- **Listening/Speaking nests one level deeper than Reading**, since a lesson
  there belongs to a Set and its files (raw `.md`, student packet `.html`,
  later homework) travel together: `lessons/<band>/Set_<N>/Lesson_<N>_<Slug>/`
  holds one lesson's files. A Set's own assessment (one per Set, not per
  lesson) sits in `Set_<N>/` itself rather than inside any one lesson's
  folder. The Module/Band Lesson Plan spans every Set generated for that
  band so far, and sits at the band-folder root (`lessons/<band>/`), above
  the `Set_<N>/` folders. Neither the Lesson, Assessment, nor Module
  Lesson-Plan generation prompts currently specify an output location
  themselves, so this note is the convention to follow when saving newly
  generated Listening/Speaking content.
- **`Index.md` files must only reference filenames that actually exist on
  disk.** Several currently describe files/content that were never saved, or
  that were saved under different names — treat any such mismatch as a bug
  to fix (either regenerate the missing content or correct the doc).
- **HTML student packets**: keep the shared CSS custom-property tokens
  (`--ink`, `--paper`, `--rule`, etc.) as the single source of truth for
  print styling across modalities; normalize generated-markup formatting
  (indentation, self-closing tags) so packets don't visibly differ by which
  session/tool produced them.
- **Prompt preambles stay short; version history lives in `Changelog.md`.**
  A prompt file's opening section states only the current lesson-type
  description and, once there's more than one version, a pointer to that
  lesson type's `Changelog.md` for full history — not a dated "what changed
  in vX" narrative inline. That narrative belongs in `Changelog.md`, which
  exists for exactly this. Keeps prompts shorter to paste and maintain
  without losing the reasoning behind past changes.

## Known issues / pending consolidation work

- `writing/academic-writing/lessons/` is **empty**, but
  `writing/academic-writing/Rotation_Log.md` describes two fully generated,
  multiply-revised lessons (Intermediate 1 "my phone case," Advanced 1 "Two
  apartments... for Sam") as current/synced. That content appears to have
  never been saved into this repo and needs to be regenerated or recovered.
- `listening-speaking/listening-speaking/lessons/intermediate/Set_1/Set1_Intermediate_Assessment.md`
  is a 1-line corrupted stub (a mangled filename string, not content), while
  `listening-speaking/listening-speaking/Index.md` and `Rotation_Log.md`
  claim this assessment was generated with real content (Part A/Part B, real
  source) — likely lost during consolidation and needs regenerating. (The
  stale `claude/...` path prefix both docs used to cite it under has been
  corrected to this real relative path; only the content-loss part of this
  issue is still open.)
- Passage Reading's `Index.md` and `Rotation_Log.md`
  (`reading/passage-reading/`) reference filenames that don't match what's
  actually on disk, e.g. doc says `Passage Reading Lesson Generation Prompt
  v2.7 BandCalibrated.md` / `Module 1 Lesson 1 - A Grandmother's Kitchen.md`,
  but the real files are `Lesson_Generation_Prompt_v2.7_CURRENT.md` /
  `Lesson1_Kitchen.md`. Needs reconciling (fix the docs to match reality, not
  the other way around).
- Academic Writing has no Module-Lesson-Plan, Homework, or Assessment prompt
  yet (only a Lesson Generation prompt and a Student Print Formatting
  prompt) — flagged as pending in its own `Index.md`.

## Working notes for future sessions

- There's nothing to build, run, lint, or test — "verification" here means
  checking that a lesson type's `Index.md` and `Rotation_Log.md` actually
  match the files present in its `lessons/` and `prompts/` folders, and that
  a lesson's HTML packet stays structurally/stylistically consistent with its
  Markdown source and with other lesson types' packets.
- When adding or renaming lesson files, follow the canonical conventions
  above rather than matching whatever scheme is already in that lesson
  type's folder — the point of this repo is to converge on one scheme.
- Adding a new lesson type (e.g. Novel Reading) means creating a new
  `<modality>/<lesson-type>/` subfolder with its own `Index.md`,
  `Changelog.md`, `Rotation_Log.md`, `prompts/`, `lessons/`, `source/` — and
  adding it to that modality's thin top-level `Index.md`. Never add a second
  lesson type's content directly into an existing lesson-type folder.
