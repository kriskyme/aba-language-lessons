# Academic Writing Index

_This is the Writing-modality counterpart to Passage Reading's `Index.md`: a living index for the Academic Writing
prompt family, tracked the same way from day one instead of being added after the fact. Update it whenever a
doc in this family is added, renamed, or synced to a new lesson-prompt version. Version history lives in
`Changelog.md`._

## What this document is

A single reference for everything in the Academic Writing prompt family: what each file does, whether it's in sync
with the current lesson-generation prompt, and the order to run them in. "Academic Writing" is the lesson type
these prompts generate: a fixed **2-day cycle**, 4 lessons per Set (matching Reading and Listening/Speaking - see
`shared/Program_Conventions.md` §C; corrected 2026-09-08 from an original 8-day/1-lesson-per-Set model), built
around one shared writing Scenario, differentiated into band-scoped task Levels that each produce their own
written output. For Intermediate, Advanced, and Proficient, that one Scenario now spans **two** consecutive Sets
- a **Module Pair** - rather than being confined to one Set: see "Module Pairs" below. Beginner is exempt and
keeps the single-Set, 4-lesson arc. It is the Writing-modality sibling of Passage Reading and shares the same
Band/Level-1-8 scale and the same `learningobjectives.csv`, but is structured differently where the two
modalities actually differ. See `Generate_Lesson_Prompt_v5.md`, Section 0.1, for the specific reason: a Reading
task Level can share one anchor text because the text itself doesn't change, while a Writing task Level's
_output form_ changes across the Level scale (a spelled word in a frame at Level 1-3 versus an independently
authored multi-paragraph piece at Level 7-8), so each task Level gets its own Mentor Text (a Leveled Mentor
Ladder) rather than one shared anchor.

A **Set** (see `shared/Program_Conventions.md` §C) is 4 lessons, same as Reading and Listening/Speaking, and its
own numbering/folder/version-code shape is completely unaffected by Module Pairing - see "Sets" below for the one
genuine structural difference that survives (a shared Scenario across the whole Set, now sometimes across two
Sets). "Leveled Mentor Ladder" (above) is an unrelated, older term - one Mentor Text per task Level within a
single lesson - renamed 2026-09-06 from "Leveled Mentor Set" specifically to free up "Set" for this
Module-rotation concept; see `Changelog.md`.

## File index

| File                                                                              | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Sync status                                                                                     |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `Generate_Lesson_Prompt_v5.md`        | Generates one **2-day lesson**: for Beginner, one of a Set's 4 fixed positions (unchanged from v4.1); for Intermediate/Advanced/Proficient, one of a **Module Pair's** 8 fixed positions spanning two Modules' Sets - see the prompt's own "THE MODULE PAIR" section. v5 introduces the Module Pair mechanic (`shared/Program_Conventions.md` §C): one Scenario/essay now spans 8 lessons for those three Bands, each Module contributing its own Grammar/Essay Focus, hard self-revision required at both Pair position 4 (hand-off) and Pair position 8 (publish), and Pair position 8's Closing Transfer Check adding a separate task for Module N+1's own CSV verb. Section 0's other pedagogical content (Band Calibration, Grammar/Essay Focus Banks, self-check) is unchanged from v4.1 except where marked. | Current (v5) |
| `Generate_Module_Lesson_Plan_Prompt_v3.md` | Plans a full **4-lesson Set** (Beginner) or a full **Module Pair - two Sets together** (Intermediate/Advanced/Proficient) in one pass: the shared Scenario, each Module's own Grammar Focus A/B pairing (and Essay Focus A/B direction, where the Band reaches Essay Composition), Leveled Mentor Ladder direction, the CSV-objective-coverage check for a Pair's second Module, and a lesson-position table mapping every position to its fixed content role - checked against the Rotation Log for adjacency to the immediately preceding Set/Pair in the same Band and, for a Pair, within-pair non-repetition between its two Modules' Focus choices. v3 rescopes from planning one Module's Set to planning a full Module Pair for three of the four Bands. | Current (v3); v2 was run retroactively 2026-09-08 against both existing Sets (see `Module1_Intermediate_Lesson_Plan.md` / `Module1_Advanced_Lesson_Plan.md` below) - v3 itself, and the Module Pair mechanic, has not yet been run before-the-fact against a new Set/Pair |
| `Generate_Homework_Prompt_v3.md` | Generates one homework assignment from a lesson's content so far, gated at four timing checkpoints (Beginner: after Lesson 1/2/3/4) or eight (Intermediate/Advanced/Proficient: after Pair position 1-8) rather than Reading's single Day-1-vs-full-lesson split. Per-task-Level design is keyed to that Level's own composition regime (frame/paragraph/essay), not just its position in the Band's range. v3 extends the checkpoint table to eight positions for a Module Pair, with Pair position 4 explicitly not implying a finished/published piece. | Current (v3); not yet run against a real lesson |
| `Generate_Assessment_Prompt_v3.md` | Generates the assessment layer for a completed **Set** (Beginner, all 4 lessons) or **Module Pair** (Intermediate/Advanced/Proficient, all 8 lessons across both Modules), split into Part A (Grammar & Mechanics Check - objectively gradable items on both Modules' Focus A/B where a Pair applies, and the taught confusable pair) and Part B (Writing Task - a new Scenario, rubric-scored Not yet/Developing/Meets), matching Reading's once-per-Set cadence for Beginner. v3 moves the Intermediate/Advanced/Proficient cadence to once-per-Module-Pair, since the piece only reaches a finished, gradable state at Pair position 8; no separate study guide document (follows Listening/Speaking's simpler precedent). | Current (v3); not yet run against a real Set or Pair |
| `Generate_Assessment_Student_Packet_Prompt_v3.md` | Translates a completed Assessment `.md` into a student-facing printable HTML handout: strips Part A's answer keys/point values and Part B's rubric, keeping only a self-check checklist derived from the rubric's Meets column. v3 follows its companion's cadence move to once-per-Module-Pair for Intermediate/Advanced/Proficient - both Modules' Grammar Check items and the Writing Task's checklist may now reflect two Modules' worth of taught content. | Current (v3); not yet run against a real assessment |
| `Rotation_Log.md`                                                                 | Overview only: purpose, this log's history (why it used to be flat, corrected 2026-09-08 to nest by Module/Set like Reading's), the cross-Set check, and the version-number note, plus links to each Band's own log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Intermediate.md`                                                    | Module 1's Set 1: four lessons (Intermediate 1-4), nested `## Module 1` → `### Set 1`, matching Reading's/Listening-Speaking's per-Band log shape (restructured 2026-09-08 from a flat single-row table). Lesson 4 retrofitted 2026-09-08 (v1.1.4.0 -> 1.1.4.1) as Part 1 of Module Pair 1-2 - see its 2026-09-08 addendum. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Advanced.md`                                                        | Same, for the Advanced Band (Module 1's Set 1, Advanced 1-4, also retrofitted as Part 1 of Module Pair 1-2). A new Band's file is created lazily the first time a Set in that Band is generated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Changelog.md`                                                                    | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | N/A (data, not a prompt)                                                                        |
| `lessons/intermediate/Module_1/Module1_Intermediate_Lesson_Plan.md`       | Output of `Generate_Module_Lesson_Plan_Prompt_v1.md`, run retroactively against the already-approved Intermediate Set 1 (predates the planning prompt) - reconstructs its Scenario, Grammar Focus A/B, Mentor Ladder direction, and self-check from that Set's own content. 2026-09-08 addendum notes the "Intermediate 1" single-lesson framing is now Set 1's four lessons (Intermediate 1-4). Second 2026-09-08 addendum notes this Set is now Part 1 of Module Pair 1-2, pending Module 2. | N/A (data, reconstructed from an existing Set) |
| `lessons/advanced/Module_1/Module1_Advanced_Lesson_Plan.md`               | Same, for the already-approved Advanced Set 1, including a note on the v3.1 Grammar Focus A/B row-selection correction that Set required. 2026-09-08 addendum notes the "Advanced 1" single-lesson framing is now Set 1's four lessons (Advanced 1-4). Second 2026-09-08 addendum notes this Set is now Part 1 of Module Pair 1-2, pending Module 2. | N/A (data, reconstructed from an existing Set) |
| `learningobjectives.csv` (project file, shared with Reading)                      | Source of truth for every Learning Objective, including the Writing modality's 64 rows (8 Levels x 8 Modules) this prompt pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | N/A (data)                                                                                      |
| `Writing Content Sample` (project doc)                                            | The user-supplied sample grounding Levels 1-5: two full grammar-in-context chapters from an academic ESL writing textbook (simple present / articles / simple and compound sentences; simple past / adverbs of manner / complex sentences with time clauses), each ending in a guided paragraph and peer edit. Structural reference only; the sample's own grammar sequence is not reproduced lesson-for-lesson.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                                                                                 |
| `Academic Writing Essay Content Sample.md` (new for v3)                           | The user-supplied sample grounding Levels 6-8: a full essay-writing textbook chapter (essay structure, hook types, direct/indirect thesis statements, topic sentences and outlining, combining sentences, six model essays with analysis activities across five essay types). Structural reference only, same convention as the paragraph-level sample: generated essays are original, not lifted from this chapter's own model essays.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | N/A (reference)                                                                                 |
| `Generate_Student_Packet_Prompt_v2.5.md` | Takes one completed **2-day lesson** and produces one self-contained, black-and-white, print-ready student HTML file: two masthead sections in one document (`Unit {N}A` for Day 1, `Unit {N}B` for Day 2, `N` = the lesson's 1-4 Set position), matching Reading's own one-file/two-masthead packet shape exactly. v2 retires the "Lesson Introduction Page" concept (a 2-day lesson is short enough not to need a roadmap page) and adopts the two-masthead shape in its place - the translation-layer rules (Section 1), star ratings, callout conventions, and self-check are otherwise unchanged from v1.6. v2.1 requires the bold `Objective:` label on the objective paragraph. v2.2 makes two corrections found by direct review: no teaching-content callout (Grammar box, essay-structure box) may carry a star tag anywhere inside it, title or body - genuinely tier-specific content inside one becomes plain bullets, not star-tagged or worded-tiered lines; and a lettered Task never carries more than one star tag - a task ladder that combines two task Levels under one letter must split into two consecutive letters instead, relettering the rest of that Day. Reprints whatever shared Scenario reference material a lesson's own days need, so each lesson's packet stays self-contained even though the Scenario itself was established in Lesson 1. v2.3's §2.12 `.ans-line-sm` is now full-width like `.ans-line` (its `max-width: 320px` cap dropped at the shared CSS layer, `shared/Student_Packet_Style_Guide.md` v1.8), distinguished from `.ans-line` only by its shorter height. v2.4 updates the masthead version-code construction to the new `<Module>.<Set>.<Lesson>.<Version>` shape (dropping the old `S<Set>.<Lesson>.<Iteration>` letter prefix). v2.5 updates the Lesson 4/Day 2 closing-activity translation to check hand-off (Module Pair position 4, not finished) versus true finale (position 8, or Beginner's Lesson 4) before defaulting to "finished, published" language. | Current (v2.5); Set 1 packets rebuilt against v2 2026-09-08 for both Bands (Advanced 1-4, Intermediate 1-4), then patched same-day to v2.1 (objective label) and v2.2 (callout/Task-letter star fixes) - see "Sets" section. Every packet across all three modalities that embeds `.ans-line-sm` was hand-corrected for the v2.3 width fix in the same pass (see `shared/Changelog.md`), not just this modality's. Both Bands' Lesson 4 packets hand-corrected 2026-09-08 for the v2.5 hand-off framing as part of the Module Pair retrofit. |

## Generation workflow (current)

As of 2026-09-08, all four companion prompts exist alongside the Lesson prompt (TOEFL-track extensions are
explicitly out of scope for Writing for now - see `CLAUDE.md`'s Known Issues), and the whole family plans and
generates by **Set** (Beginner, 4 lessons) or by **Module Pair** (Intermediate/Advanced/Proficient, two Sets/8
lessons together), matching Reading's/Listening-Speaking's Set-planning workflow shape and extending it for three
of the four Bands. None of the three newer companions (Homework, Assessment, Assessment print) has been run
against a real Set or Pair yet; treat the step order below as the intended workflow, not a proven one.

**Step 1 - Plan the Set or Module Pair.** Run `Generate_Module_Lesson_Plan_Prompt_v3.md` against a Band (naming
one Module for Beginner, or a Module Pair like "Modules 1-2" for Intermediate/Advanced/Proficient) to decide the
shared Scenario, each Module's own Grammar Focus A/B pairing (and Essay Focus A/B direction, where applicable),
and Leveled Mentor Ladder direction before writing any lesson content, checked against the Rotation Log for
adjacency to the Band's own immediately preceding Set/Pair and, for a Pair, within-pair non-repetition between
its two Modules. Review and approve the plan, then append its Rotation Log entries (4 rows for Beginner, 8 split
across the two Modules' own sections for a Pair).

**Step 2 - Generate the lessons, one at a time.** Run `Generate_Lesson_Prompt_v5.md` four times (Beginner) or
eight times (Intermediate/Advanced/Proficient) against the approved plan, once per Set/Pair position. It reads
`Rotation_Log.md` plus that Band's own `Rotation_Log_<Band>.md` first (per Section 0.9) for the arc's first
lesson; every later position continues what came before it directly rather than re-deriving it - including
position 5 (Module N+1's Lesson 1), which introduces Module N+1's own Focus A but does not re-derive the
Scenario. Pulls the Writing-modality CSV row for every task Level in the band, builds the Leveled Mentor Ladder,
and runs its own Section 0.3 self-check before each lesson is finalized. As with Reading, review and approve each
generated lesson before treating it as final. Once approved, the corresponding Rotation Log row (already appended
in Step 1) reflects that lesson.

**Optional - Student print handout.** Run `Generate_Student_Packet_Prompt_v2.5.md` against any completed lesson to
produce that lesson's one-file, two-masthead-section packet. Independent of the rotation-log step; can run any
time after that lesson is finalized, one lesson at a time (not once per Set/Pair).

**Optional - Homework.** Run `Generate_Homework_Prompt_v3.md` against a lesson's content so far, at any of the
timing checkpoints (Beginner: after Lesson 1/2/3/4; Intermediate/Advanced/Proficient: after Pair position 1-8)
that prompt's Section 0.2 defines.

**Optional - Assessment.** Run `Generate_Assessment_Prompt_v3.md` against a completed Set (Beginner, all 4
lessons) or Module Pair (Intermediate/Advanced/Proficient, all 8 lessons) to produce Part A (Grammar & Mechanics
Check) and Part B (Writing Task), then `Generate_Assessment_Student_Packet_Prompt_v3.md` in the same session to
produce the student-facing printable version.

## Key differences from Passage Reading (read before assuming parity)

- **One shared Scenario per Set, not 4 independent anchor texts.** This is the one place a Writing Set still
  differs structurally from a Reading Set now that both use 2-day lessons, 4 per Set. A Reading Set's 4 lessons
  each get their own anchor text; a Writing Set's 4 lessons all write about the *same* Scenario, carried from
  grammar input (Lessons 1-2) through drafting (Lesson 3) toward a complete draft (Lesson 4) - closer to one
  continuous project than four independent lessons that happen to share a Module/Band.
- **For Intermediate/Advanced/Proficient, that one Scenario now spans two Sets, not one - a Module Pair.** See
  "Module Pairs" below. Reading has no equivalent: a Reading Set is always self-contained within one Module. This
  is Writing's second, larger structural difference from Reading, layered on top of the shared-Scenario-per-Set
  difference above rather than replacing it.
- **Two grammar focuses per Set, not one per lesson.** Section 0.4 requires a deliberate Focus A (core form,
  Lesson 1) plus Focus B (sentence variety, Lesson 2) pairing every Set, matching how the sample textbook's
  chapters actually work.
- **A Leveled Mentor Ladder, not one shared anchor text.** See the note under "What this document is" above.
- **A frame-composition/independent-composition regime boundary at Levels 3/4.** This falls inside the
  Intermediate band's own task-Level span (2, 3, 4, 5), making Intermediate the one band that has to hold both
  regimes across its Set. Beginner sits entirely below the boundary; Advanced and Proficient sit entirely
  above it.
- **No word-count ceiling corpus yet.** Reading's Section 0.2 is anchored to real published B1-C1 reading
  materials. Writing's Section 0.2 output-length targets are a first-pass estimate built from the CSV's own
  worked examples; expect these to need correction once real generated lessons and real student output exist to
  check them against, the same way Reading's own Level 3 ceiling was corrected twice.
- **Self-revision is a graded feature at Levels 7-8, recommended at Levels 4-6 (Level 5 especially), with its own
  mechanism (Section 0.4a)**, since "revise your work" alone produces no checkable evidence, the same problem
  Reading's original thumbs-up closing check had before v2.3 replaced it with a demonstration.
- **Three regimes, not two.** Levels 1-3 (frame), 4-5 (single paragraph), 6-8 (full essay: hook, thesis,
  topic-sentence-led body paragraphs, conclusion). Reading has no equivalent of this second regime boundary; a
  Reading task Level always produces the same kind of response (an answer, a short synthesis), just more of it at
  higher Levels, whereas Writing's Level 5-to-6 jump changes the _shape_ of the output, not just its depth, the
  same way the Level 3-to-4 frame/paragraph jump already did.
- **Grammar Focus A/B anchors at a band's native row, not its lowest.** A band's lowest Paragraph
  Composition Level is sometimes native to it (Intermediate: Level 4) and sometimes an accommodation on loan from
  a neighboring band (Advanced: Level 4 belongs to Intermediate; Advanced's own native floor is Level 5). Reading
  has no exact equivalent, since its task Levels differentiate depth of engagement with one shared text rather
  than which grammar point anchors a shared centerpiece.
- **Level 5 gets a receptive essay-structure bridge into the essay regime.** In any band that reaches
  both Paragraph Composition and Essay Composition (Advanced, Proficient), Level 5 previously had zero exposure to
  essay structure before Level 6 suddenly required a full five-paragraph essay. Section 0.4c now gives Level 5 a
  light, receptive activity (e.g. find and underline one topic sentence) on the same shared model essay the
  essay-writing Levels analyze, without raising Level 5's own output requirement past a single paragraph. Reading
  has no equivalent regime boundary for this to bridge (see the "Three regimes" bullet above).
- **Teaching-content ordering and paired tiers are explicit checks.** Two self-check items: every piece of
  teaching content (a Grammar table, an Essay Focus explanation) must appear earlier in the lesson's own
  day-by-day sequence than any practice that depends on it, not just be present somewhere in the lesson; and
  single-audience activities are checked for a natural lighter (receptive) or heavier (combining) tier for the
  Level immediately adjacent, built only from already-taught content.

## Sets

See `shared/Program_Conventions.md` §C/§D for what a Set is and the general folder shape - canonical there, not
restated here. **Corrected 2026-09-08:** a Writing Set is **4 lessons**, matching Reading and Listening/Speaking
(the original "a Writing lesson is an 8-day cycle, so a Writing Set is 1 lesson" model was a miscount - see
`shared/Program_Conventions.md` §C and `Changelog.md`'s 2026-09-08 entry). The one fact still specific to Writing:
a Set's 4 lessons all share **one** Scenario - for Beginner, carried through to a finished, published piece
within that one Set; for Intermediate/Advanced/Proficient, carried into a complete draft handed off to a second
Set (see "Module Pairs" below) - rather than 4 independent anchor texts the way a Reading Set's lessons work (see
"Key differences" above).

As of 2026-09-08, `lessons/<band>/Module_1/Set_1/Lesson_{1-4}_<Slug>/` folders exist on disk for both the
Intermediate and Advanced Bands, each lesson folder holding its own 2-day Markdown doc plus a current-convention
(v2.5) print packet - one file, two masthead sections (`Generate_Student_Packet_Prompt_v2.5.md`). The same slug
repeats across all 4 lesson folders in a Set (unlike Reading, where each lesson folder gets its own topic slug),
since all 4 lessons share one Scenario:

- `lessons/intermediate/Module_1/Set_1/Lesson_1_MyPhoneCase/` through `Lesson_4_MyPhoneCase/` - `Lesson{1-4}_MyPhoneCase.md`, `MyPhoneCase_Intermediate_L{1-4}_Packet.html` (Intermediate 1-4)
- `lessons/advanced/Module_1/Set_1/Lesson_1_TwoApartments/` through `Lesson_4_TwoApartments/` - `Lesson{1-4}_TwoApartments.md`, `TwoApartments_Advanced_L{1-4}_Packet.html` (Advanced 1-4)

Both Sets were originally generated as a single 8-day document (2026-08-30/31) and reorganized into this 4-lesson
shape 2026-09-08, with no change to the underlying pedagogical content - only the framing, metadata, and
day-numbering changed (each lesson's own Markdown doc has a "reorganized from" note; see `Changelog.md`'s
2026-09-08 entry for the full account, including why: the user noticed `writing 1.md`/`writing 2.md`, text
extracted from the packets actually taught, each covered 2 days, not 4). Lessons 1-2's packet text was kept
close to that actually-taught wording per the user's request; Lessons 3-4 continue the same Scenario using the
already-written drafting/revision content, rather than new topics. Lesson 4 was retrofitted a second time,
same day, into Module Pair 1-2's Part 1 (see "Module Pairs" below). All 8 packets are first-pass generations per
the print prompt's own Section 4.1 ("iterate before finalizing") - review them against a real print/classroom
pass before treating them as final. A Module Lesson-Plan prompt now exists
(`Generate_Module_Lesson_Plan_Prompt_v3.md`) but has not yet been run before-the-fact against a new Set/Pair, so
treat the folder shape above as a manually-applied convention for this retrofitted Set, not evidence that
Set-aware planning has been exercised from scratch yet.

## Module Pairs

For Intermediate, Advanced, and Proficient (Beginner is exempt - see `shared/Program_Conventions.md` §C's Module
Pair addendum and `Generate_Lesson_Prompt_v5.md`'s "THE MODULE PAIR"), two consecutive Modules pair into one
essay: odd with the next even (1-2, 3-4, 5-6, 7-8). Each Module keeps its own ordinary `Module_<N>/Set_<N>/`
folder, numbering, and version codes (§C/§D/§G are unaffected) - Module Pairing is a continuity layer above Set,
recorded via a new wrapping planning artifact rather than any change to Set mechanics:

```
lessons/<band>/
└── ModulePair_{N}-{N+1}/
    └── ModulePair_{N}-{N+1}_{Band}_Lesson_Plan.md
```

This doc (produced by `Generate_Module_Lesson_Plan_Prompt_v3.md`) plans both Modules together in one pass:
Scenario/genre (fixed once, by Module N's own mapping), each Module's own Grammar/Essay Focus A/B (checked for
within-pair non-repetition), the full 8-lesson content-role table, and the CSV-objective-coverage check for
Module N+1's own verb (see the Lesson prompt's own "THE MODULE PAIR" section for what that check resolves). It
supersedes having two separate `Module{N}_{Band}_Lesson_Plan.md` docs for a paired Module going forward.

**Module Pair 1-2, both Bands: Part 1 only.** Module 1's existing Set 1 (both Intermediate and Advanced, see
"Sets" above) was retrofitted 2026-09-08 into Part 1 of Module Pair 1-2: Lesson 4 no longer ends in a published,
finished piece, but in a complete, self-revised draft handed off to Module 2's Set. **Module 2 has not yet been
planned or generated for either Band**, and no `ModulePair_1-2_<Band>_Lesson_Plan.md` exists yet either - see
Pending work below. Until Module 2 exists, treat Module Pair 1-2 as an intentionally incomplete arc, the same
status as this family's other "not yet run before-the-fact" gaps.

## Pending work

- **First real, before-the-fact run of the prompt family against a brand-new Set or Module Pair.** Every prompt
  in this family (Module Lesson-Plan, Lesson, Homework, Assessment, Assessment print) has so far only been run
  either retroactively (Module Lesson-Plan, against the already-approved Set 1) or not at all (Homework,
  Assessment, Assessment print) - every number in them (item counts, timing checkpoints, essay-regime time
  budgets) is a first-pass estimate, the same status the Lesson prompt's own v1 numbers had before real-classroom
  correction. Expect addenda once each has actually been used to plan and generate a new Set/Pair from scratch.
- **Module 2 for Module Pair 1-2 (Intermediate and Advanced) has not been planned or generated.** Module 1's
  Lesson 4 has been retrofitted into a hand-off (see "Module Pairs" above), but the piece it hands off is not
  actually completed until Module 2's Set 1 is planned (via `Generate_Module_Lesson_Plan_Prompt_v3.md`, naming
  the Module Pair) and generated. This is the most load-bearing gap left by the Module Pair redesign - until it
  closes, both existing Sets end mid-arc.
- **Grammar/Essay Focus Bank "Alternate" rows are not yet authored.** `Generate_Lesson_Prompt_v5.md`'s Section
  0.4/0.4c gives exactly one Focus A/B per native Level; a Module Pair's second Module needs genuinely different
  content at the same native row (Section 0.9's within-pair non-repetition rule), which the Bank does not yet
  have a dedicated column for. Until authored, Module N+1's Focus A/B must be hand-selected and checked for
  distinctness each time a Pair is planned - a real content-authoring task, not a structural one.
- **Real-classroom calibration pass.** Section 0.2 length targets and the Section 0.4 grammar bank are
  first-draft estimates (see above); revise them once real lessons have been generated and taught, the same way
  Reading's prompt matured from v1 through v2.5.
