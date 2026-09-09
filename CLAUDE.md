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
Beginner / Intermediate / Advanced / Proficient. See
[`shared/Program_Conventions.md`](shared/Program_Conventions.md) §A/§B for the
full canonical version — including the Band/CEFR and Task-Levels-by-Band
tables — that lesson-generation prompts paste in directly.

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
    ├── Rotation_Log.md       # overview: purpose + links to each Band's log
    ├── Rotation_Log_<Band>.md  # one per Band with generated content; created lazily on that Band's first lesson
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

Outside the three modality folders, one more top-level folder holds facts
that don't belong to any single modality:

```
shared/
├── Program_Conventions.md          # cross-modality facts: taxonomy, Sets, Rotation Log mechanics
├── Generation_Quality_Standards.md # modality-neutral pedagogical/item-quality rules + shared self-check
├── Student_Packet_Style_Guide.md   # everything about printed output: CSS, translations, star/Task rules, packet self-check
└── Changelog.md                    # version history for the three files above
```

Every lesson type's prompts and `Index.md` point here for this content rather
than restating it — see the "Cross-modality conventions live in one shared
file" bullet below for what that means in practice.

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
- **Academic Writing** (`writing/academic-writing/`) — 2-day lesson (matching
  Reading and Listening/Speaking), 4 lessons per Set, built around a shared
  "Scenario" plus a **Leveled Mentor Ladder** (one exemplar per task Level)
  instead of a single shared anchor text, with a Focus A/Focus B grammar
  pairing structure. The one place a Writing Set still differs from Reading's:
  all 4 lessons in a Set share **one** Scenario carried from grammar input
  (Lessons 1-2) through drafting (Lesson 3) to a finished, published piece
  (Lesson 4), rather than each lesson getting its own independent anchor text.
  The Scenario names two of the student's own belongings: a **practice
  object** for Lessons 1-2's grammar work and Mentor Ladder, and a **draft
  object** introduced at Lesson 2 Day 2's prewriting that Lessons 3-4 (and a
  Module Pair's second Module) write about, so the draft transfers the
  grammar to a fresh object; a Module Pair's piece is built in parts, each
  Module drafting only the part its own form fits (`shared/Program_Conventions.md` §C).
  (Corrected 2026-09-08 from an original 8-day/1-lesson-per-Set model — see
  `shared/Program_Conventions.md` §C.)

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
- **Lessons nest by Set.** See
  [`shared/Program_Conventions.md`](shared/Program_Conventions.md) §C/§D for
  what a Set is and the `lessons/<band>/Set_<N>/Lesson_<N>_<Slug>/` folder
  shape — canonical there, not restated here. Institutional history specific
  to this repo (not duplicated in the shared file): Listening/Speaking
  adopted the convention first (2026-09-03, after correcting an early
  miscount that had inflated its module size); Reading followed for parity
  (2026-09-06), physically migrating its already-generated lessons into the
  nested shape; Academic Writing adopted it for real 2026-09-08, once its own
  8-day/1-lesson-per-Set sizing was corrected to match Reading and
  Listening/Speaking's 2-day/4-lessons-per-Set model (see
  `shared/Program_Conventions.md` §C). As of the 2026-09-08 shared-layer restructure, every
  Lesson, Assessment, and Module Lesson-Plan prompt points to
  `shared/Program_Conventions.md` §D for where its output saves.
- **Cross-modality conventions live in one shared file, not restated per
  lesson type.** Facts that are true program-wide (the Level/Band taxonomy,
  what a Set is, the Set/Lesson folder-nesting shape, the CBI/TBLT
  framework, Rotation Log mechanics) belong in
  [`shared/Program_Conventions.md`](shared/Program_Conventions.md);
  modality-neutral pedagogical and item-quality rules plus the shared
  output self-check belong in
  [`shared/Generation_Quality_Standards.md`](shared/Generation_Quality_Standards.md);
  everything about printed output (CSS, teacher-to-student translations,
  star and lettered-Task rules, the packet-is-a-regeneration rule, the
  shared packet self-check) belongs in
  `shared/Student_Packet_Style_Guide.md`. A lesson type's own `Index.md`,
  `Changelog.md`, and prompts point there rather than restate it — this
  applies to Novel Reading and any future lesson type too, from the start
  rather than as a later cleanup.
- **Fix modality-neutral bugs in `shared/` first.** Before editing a
  modality's prompt to fix a quality problem, ask whether the rule stays
  true when "text" is swapped for "clip" or "scenario." If yes, it goes in
  `Generation_Quality_Standards.md` or the Style Guide, is logged once in
  `shared/Changelog.md`, and each modality's own `Changelog.md` gets at most
  a one-line pointer to that entry, not a restated copy. This is what stops
  a fix landing in one modality and the same bug resurfacing in another.
- **No prose cross-references between modalities.** A prompt may point at a
  `shared/` section, never at another modality's prompt ("same as Passage
  Reading 2.12"). Such a pointer has no mechanical link, so a change on one
  side never reaches the other.
- **Prompt bodies carry no version stamps.** No `(new in v2.2)`,
  `(corrected in v1.5)`, dated parentheticals, or "this was the failure in
  Lesson 2" narration inside a prompt's rules. Rationale and history live in
  `Changelog.md`; the prompt states only the current rule.
- **Rotation Log splits by Band.** `Rotation_Log.md` is a short overview
  (purpose, any note that applies across every Band, links to each Band's
  file) rather than one growing file with every Band nested inside it. Each
  Band gets its own `Rotation_Log_<Band>.md` the first time a lesson is
  generated in that Band — created lazily, the same way `Set_<N>/` folders
  are — holding just that Band's Set/lesson tables and its own
  append-template. A note or correction that applies across every Band (a
  miscount fix, a Sets-concept introduction) stays in the overview; never
  duplicate it into every Band file. Applies to Novel Reading and any future
  lesson type too, from the start.
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

- **Self-contained rule backlog (added 2026-09-08).** `shared/Generation_Quality_Standards.md` §D8 now forbids
  any dependency on teacher-prepared media (props, picture cards, photos to find, "your teacher will show
  you," empty picture boxes in a packet). Twelve already-generated lessons and one assessment packet across
  all three modalities predate the rule and still carry such a dependency (Reading Intermediate Set 1 Lessons 1, 2, 4 resolved 2026-09-09); each modality's `Index.md` Pending
  work lists them. Fix each by embedding a real image or redesigning around the student's own object when it
  is next touched; do not generate new content with the old pattern. The same file's §D9 (no dependence on a
  student's work from an earlier lesson except the carried draft) and §E6 (concrete prompts, no reflection
  questions, at Beginner/Intermediate) have one known violation, Writing Advanced Lesson 3's "Look back at your
  planning from Lesson 2," logged in Academic Writing's `Index.md`, which also logs that Set's Lesson 4 packet
  for the Style Guide v2.4 rule that a self-check is one lettered Task per star, never a combined-star list.

- **Resolved 2026-09-08**: `writing/academic-writing/lessons/`'s two
  documented lessons (Intermediate 1 "my phone case," Advanced 1 "Two
  apartments... for Sam") were recovered and are now organized under the
  canonical `Module_1/Set_1/Lesson_1_<Slug>/` structure
  (`lessons/intermediate/Module_1/Set_1/Lesson_1_MyPhoneCase/`,
  `lessons/advanced/Module_1/Set_1/Lesson_1_MyRoom/`, the Advanced Set having
  been regenerated 2026-09-08 as "Two Places to Study"), each holding its
  Markdown doc plus a reconstructed pre-v1.2 Unit 1/Unit 2 print-packet pair.
  Current-convention (v1.6, Lesson Introduction Page + Units 1-8) packets
  still need to be built for both — tracked in
  `writing/academic-writing/Index.md`'s Pending work.
- **Resolved 2026-09-08**: every filename cited in all three lesson types'
  `Index.md` files (and this file) was checked against disk in the
  shared-layer restructure pass; no mismatches remain. Passage Reading's
  `Index.md` had cited `Generate_Student_Packet_Prompt_v1.11.md` for a file
  that was already `_v1.12.md`; that and the older mismatches noted here
  before are fixed.
- **Resolved 2026-09-08**: Academic Writing now has a full prompt family
  matching Reading's and Listening/Speaking's (Module Lesson-Plan, Homework,
  Assessment, plus an Assessment Student Packet prompt — split from day one
  rather than retrofitted later, since Reading itself has flagged that split
  as still-pending work). TOEFL-track prompts/content remain out of scope for
  Writing, to be handled separately. None of the four new prompts has been
  run against a real lesson yet — see
  `writing/academic-writing/Index.md`'s Pending work.

## Working notes for future sessions

- There's nothing to build, run, lint, or test — "verification" here means
  checking that a lesson type's `Index.md` and `Rotation_Log.md` actually
  match the files present in its `lessons/` and `prompts/` folders, and that
  a lesson's HTML packet stays structurally/stylistically consistent with its
  Markdown source and with other lesson types' packets.
- **How to use these docs, in order:** this file for repo-wide orientation →
  the relevant lesson type's own `Index.md` for its file inventory and
  "Generation workflow" section (what order to run that lesson type's prompts
  in) → `shared/Program_Conventions.md` for any cross-modality fact the
  workflow needs (taxonomy, Sets, Rotation Log mechanics). Don't re-derive
  any of that from scratch each session — it's already written down.
- **Update as you go, not as a later cleanup:** once you generate, rename, or
  sync any doc in a lesson type's family, update that lesson type's `Index.md`
  (file table, sync status, and its "Module/Band progress" section) and
  append to the right `Rotation_Log_<Band>.md` in the same pass — this is
  what each Index.md's own opening line already means by "living index."
  Leaving that for later is exactly how the mismatches under Known Issues
  above happened.
- When adding or renaming lesson files, follow the canonical conventions
  above rather than matching whatever scheme is already in that lesson
  type's folder — the point of this repo is to converge on one scheme.
- Adding a new lesson type (e.g. Novel Reading) means creating a new
  `<modality>/<lesson-type>/` subfolder with its own `Index.md`,
  `Changelog.md`, `Rotation_Log.md`, `prompts/`, `lessons/`, `source/` — and
  adding it to that modality's thin top-level `Index.md`. Never add a second
  lesson type's content directly into an existing lesson-type folder.
