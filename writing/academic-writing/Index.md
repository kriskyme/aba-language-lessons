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
modalities actually differ. See `Generate_Lesson_Prompt_v6.11.md`, Section 0.1, for the specific reason: a Reading
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
| `Generate_Lesson_Prompt_v6.11.md` | Generates one **2-day lesson**: for Beginner, one of a Set's 4 fixed positions; for Intermediate/Advanced/Proficient, one of a Module Pair's 8 positions ("THE MODULE PAIR" section), each run producing one lesson at the named position against the approved plan. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; states only what is true of a writing lesson (the three-regime model and Scenario/Mentor Ladder in 0.1, per-Level output ceilings and required features in 0.2, the Grammar and Essay Focus banks and row-selection rules in 0.4/0.4c, self-revision evidence in 0.4a, content-volume minimums in 0.4b, checklists and Peer Editing timing in 0.6, the Module-to-form mapping in 0.9, the Module Pair arc and the per-lesson flow) and points to the shared files for everything modality-neutral. Section 0.3's self-check is the shared Quality Standards §F list plus 16 Writing-only items. Section 0 now uses `Lesson N, Day M` numbering throughout. | Current (v6.11); all four Intermediate Set 1 lessons regenerated against v6 2026-09-08 and Lessons 2-4 revised under v6.2's practice/draft-object split and v6.3's self-contained/concrete-prompt rules the same day (1.1.1.6, 1.1.2.8, 1.1.3.12, 1.1.4.13; see "First run" below); the Advanced Set's four lessons were generated under v4/v4.1 and retrofitted under v5 |
| `Generate_Module_Lesson_Plan_Prompt_v4.4.md` | Plans a full **Set** (Beginner) or **Module Pair** (Intermediate/Advanced/Proficient) in one pass: Scenario, genre, each Module's Focus A/B pairing, Essay Focus direction, the Module N+1 CSV-coverage task, Mentor Ladder direction, and the position table. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; general Rotation Log mechanics point to Conventions §F and the prompt keeps only Writing's cross-Band and within-pair rules. Writing objectives only. | Current (v4.4) |
| `Generate_Homework_Prompt_v4.2.md` | Generates one homework assignment (grammar focus in production plus skill practice) from a lesson's content so far, at any of the timing checkpoints (Beginner: after Lesson 1-4; others: after Pair position 1-8), one section per task Level keyed to its composition regime. Run with the two shared files pasted alongside; Section 3 is Quality Standards §F plus 6 Writing items. | Current (v4.2); not yet run against a real lesson |
| `Generate_Assessment_Prompt_v4.1.md` | Generates a Set's (Beginner) or Module Pair's Grammar & Mechanics Check (Part A) and Writing Task (Part B). Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; keeps what is Writing-specific (new example sentences, Focus A/B and Essay Focus coverage, objective-only Part A formats, a new Scenario matched in shape to the original, target lengths from 0.2, regime-dependent sittings, the 3-point rubric) and points to Quality Standards §C for item quality, which is where Writing's assessments now pick up the distractor, padded-bank, and requires-the-centerpiece rules they never had. Self-checks are Quality Standards §F plus 4 Part A and 6 Part B items. | Current (v4); not yet run against a real Set or Pair |
| `Generate_Assessment_Student_Packet_Prompt_v4.md` | Takes a completed Assessment and produces the student handout: Grammar Check pages per Level under lettered Tasks, Writing Task cards with the rubric's Meets column as a `.checklist` (Style Guide §H.4), no answer keys or rubric tables. Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; Section 5 is Style Guide §I plus 4 items. Its stale `.ans-line-tiny` mention is gone. | Current (v4); not yet run |
| `Rotation_Log.md`                                                                 | Overview only: purpose, this log's history (why it used to be flat, corrected 2026-09-08 to nest by Module/Set like Reading's), the cross-Set check, and the version-number note, plus links to each Band's own log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Intermediate.md`                                                    | Module 1's Set 1: four lessons (Intermediate 1-4), nested `## Module 1` → `### Set 1`, matching Reading's/Listening-Speaking's per-Band log shape (restructured 2026-09-08 from a flat single-row table). Lesson 4 retrofitted 2026-09-08 (v1.1.4.0 -> 1.1.4.1) as Part 1 of Module Pair 1-2, then regenerated against v6 (-> 1.1.4.2); one dated addendum per regenerated lesson. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Advanced.md`                                                        | Same, for the Advanced Band (Module 1's Set 1, Advanced 1-4, also retrofitted as Part 1 of Module Pair 1-2). A new Band's file is created lazily the first time a Set in that Band is generated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Changelog.md`                                                                    | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | N/A (data, not a prompt)                                                                        |
| `lessons/intermediate/Module_1/Module1_Intermediate_Lesson_Plan.md`       | Output of `Generate_Module_Lesson_Plan_Prompt_v1.md`, run retroactively against the already-approved Intermediate Set 1 (predates the planning prompt) - reconstructs its Scenario, Grammar Focus A/B, Mentor Ladder direction, and self-check from that Set's own content. 2026-09-08 addendum notes the "Intermediate 1" single-lesson framing is now Set 1's four lessons (Intermediate 1-4). Second 2026-09-08 addendum notes this Set is now Part 1 of Module Pair 1-2, pending Module 2. | N/A (data, reconstructed from an existing Set) |
| `lessons/advanced/Module_1/Module1_Advanced_Lesson_Plan.md`               | Same, for the already-approved Advanced Set 1, including a note on the v3.1 Grammar Focus A/B row-selection correction that Set required. 2026-09-08 addendum notes the "Advanced 1" single-lesson framing is now Set 1's four lessons (Advanced 1-4). Second 2026-09-08 addendum notes this Set is now Part 1 of Module Pair 1-2, pending Module 2. | N/A (data, reconstructed from an existing Set) |
| `learningobjectives.csv` (project file, shared with Reading)                      | Source of truth for every Learning Objective, including the Writing modality's 64 rows (8 Levels x 8 Modules) this prompt pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | N/A (data)                                                                                      |
| `Writing Content Sample` (project doc)                                            | The user-supplied sample grounding Levels 1-5: two full grammar-in-context chapters from an academic ESL writing textbook (simple present / articles / simple and compound sentences; simple past / adverbs of manner / complex sentences with time clauses), each ending in a guided paragraph and peer edit. Structural reference only; the sample's own grammar sequence is not reproduced lesson-for-lesson.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                                                                                 |
| `Academic Writing Essay Content Sample.md` (new for v3)                           | The user-supplied sample grounding Levels 6-8: a full essay-writing textbook chapter (essay structure, hook types, direct/indirect thesis statements, topic sentences and outlining, combining sentences, six model essays with analysis activities across five essay types). Structural reference only, same convention as the paragraph-level sample: generated essays are original, not lifted from this chapter's own model essays.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | N/A (reference)                                                                                 |
| `Generate_Student_Packet_Prompt_v3.14.md` | Takes one completed 2-day lesson and produces its one-file, two-masthead-section packet (self-contained HTML). Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; states only what is specific to a Writing packet (Set-position Unit numbering and Scenario self-containment, the Task-label line rule, Grammar and essay-structure box translation, the Mentor Ladder as star-labeled examples, the hand-off-vs-finale closing check, Check Your Own Work / Trade and Check, Writing's own translation rows) and points to the Style Guide for the translation table, star and lettered-Task rules (including one-star-per-letter and no-star-in-a-callout, both originally Writing-only), the regeneration rule, the delta CSS (§H.3, recorded from the existing packets), and the shared packet self-check. Section 5 is Style Guide §I plus 10 Writing items. | Current (v3.14); all four Intermediate Set 1 packets regenerated against v3.x 2026-09-08 alongside their lessons; the Advanced Set's four packets were generated against v2-v2.5 and hand-corrected in earlier passes (see `Changelog.md`) |

## Generation workflow (current)

As of 2026-09-08, all four companion prompts exist alongside the Lesson prompt (TOEFL-track extensions are
explicitly out of scope for Writing for now - see `CLAUDE.md`'s Known Issues), and the whole family plans and
generates by **Set** (Beginner, 4 lessons) or by **Module Pair** (Intermediate/Advanced/Proficient, two Sets/8
lessons together), matching Reading's/Listening-Speaking's Set-planning workflow shape and extending it for three
of the four Bands. None of the three newer companions (Homework, Assessment, Assessment print) has been run
against a real Set or Pair yet; treat the step order below as the intended workflow, not a proven one.

**Step 1 - Plan the Set or Module Pair.** Run `Generate_Module_Lesson_Plan_Prompt_v4.4.md` against a Band (naming
one Module for Beginner, or a Module Pair like "Modules 1-2" for Intermediate/Advanced/Proficient) to decide the
shared Scenario, each Module's own Grammar Focus A/B pairing (and Essay Focus A/B direction, where applicable),
and Leveled Mentor Ladder direction before writing any lesson content, checked against the Rotation Log for
adjacency to the Band's own immediately preceding Set/Pair and, for a Pair, within-pair non-repetition between
its two Modules. Review and approve the plan, then append its Rotation Log entries (4 rows for Beginner, 8 split
across the two Modules' own sections for a Pair).

**Step 2 - Generate the lessons, one at a time.** Run `Generate_Lesson_Prompt_v6.11.md` (pasted with
`shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`) four times (Beginner) or eight
times (Intermediate/Advanced/Proficient) against the approved plan, once per Set/Pair position. It reads
`Rotation_Log.md` plus that Band's own `Rotation_Log_<Band>.md` first (per Section 0.9) for the arc's first
lesson; every later position continues what came before it directly rather than re-deriving it - including
position 5 (Module N+1's Lesson 1), which introduces Module N+1's own Focus A but does not re-derive the
Scenario. Pulls the Writing-modality CSV row for every task Level in the band, builds the Leveled Mentor Ladder,
and runs its own Section 0.3 self-check before each lesson is finalized. As with Reading, review and approve each
generated lesson before treating it as final. Once approved, the corresponding Rotation Log row (already appended
in Step 1) reflects that lesson.

**Optional - Student print handout.** Run `Generate_Student_Packet_Prompt_v3.14.md` against any completed lesson to
produce that lesson's one-file, two-masthead-section packet. Independent of the rotation-log step; can run any
time after that lesson is finalized, one lesson at a time (not once per Set/Pair).

**Optional - Homework.** Run `Generate_Homework_Prompt_v4.2.md` against a lesson's content so far, at any of the
timing checkpoints (Beginner: after Lesson 1/2/3/4; Intermediate/Advanced/Proficient: after Pair position 1-8)
that prompt's Section 0.2 defines.

**Optional - Assessment.** Run `Generate_Assessment_Prompt_v4.1.md` against a completed Set (Beginner, all 4
lessons) or Module Pair (Intermediate/Advanced/Proficient, all 8 lessons) to produce Part A (Grammar & Mechanics
Check) and Part B (Writing Task), then `Generate_Assessment_Student_Packet_Prompt_v4.md` in the same session to
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
"Key differences" above). Since 2026-09-08 the Scenario names two of the student's own belongings: a **practice
object** for Lessons 1-2's grammar work and Mentor Ladder, and a **draft object** introduced at Lesson 2 Day 2's
prewriting that Lessons 3-4 and the Pair's second Module write about (`shared/Program_Conventions.md` §C; Lesson
prompt 0.1a).

As of 2026-09-08, `lessons/<band>/Module_1/Set_1/Lesson_{1-4}_<Slug>/` folders exist on disk for both the
Intermediate and Advanced Bands, each lesson folder holding its own 2-day Markdown doc plus a print packet - one
file, two masthead sections (v2.5-era for most; Intermediate Lesson 3's was regenerated 2026-09-08 under
`Generate_Student_Packet_Prompt_v3.14.md` alongside its Markdown's v6 regeneration, 1.1.3.1). The slug names
the object that lesson writes about (unlike Reading, where each lesson folder gets its own topic slug): the
practice object's slug on Lessons 1-2, the draft object's slug on Lessons 3-4 and on a Pair's second Module. Sets
generated before the 2026-09-08 practice/draft split carry one slug across all four folders:

- `lessons/intermediate/Module_1/Set_1/Lesson_1_MyPhoneCase/` and `Lesson_2_MyPhoneCase/` - `Lesson{1-2}_MyPhoneCase.md`, `MyPhoneCase_Intermediate_L{1-2}_Packet.html` (Intermediate 1-2, practice object); `Lesson_3_MyClothing/` and `Lesson_4_MyClothing/` - `Lesson{3-4}_MyClothing.md`, `MyClothing_Intermediate_L{3-4}_Packet.html` (Intermediate 3-4, draft object: one piece of the student's clothing from a printed list)
- `lessons/advanced/Module_1/Set_1/Lesson_1_TwoApartments/` through `Lesson_4_TwoApartments/` - `Lesson{1-4}_TwoApartments.md`, `TwoApartments_Advanced_L{1-4}_Packet.html` (Advanced 1-4)

Both Sets were originally generated as a single 8-day document (2026-08-30/31) and reorganized into this 4-lesson
shape 2026-09-08, with no change to the underlying pedagogical content - only the framing, metadata, and
day-numbering changed (each lesson's own Markdown doc has a "reorganized from" note; see `Changelog.md`'s
2026-09-08 entry for the full account, including why: the user noticed `writing 1.md`/`writing 2.md`, text
extracted from the packets actually taught, each covered 2 days, not 4). Lessons 1-2's packet text was kept
close to that actually-taught wording per the user's request; Lessons 3-4 continued the same Scenario using the
already-written drafting/revision content, rather than new topics, until the 2026-09-08 practice/draft split
moved their draft to the student's own jacket (see "First run" below). Lesson 4 was retrofitted a second time,
same day, into Module Pair 1-2's Part 1 (see "Module Pairs" below). Intermediate Lesson 1's packet was hand-corrected
2026-09-08 for duplicate tasks (Unit 1A Task C/D, Unit 1B Task D/E - each pair merged to one task at the lower star
rating) and picture references with no picture in the packet (Unit 1A's frame tasks reworded to use the student's
own phone case; the "See How It's Done" section removed entirely) - see `Changelog.md`'s 2026-09-08
hand-correction entry. All 8 packets are first-pass generations per
the print prompt's own Section 4.1 ("iterate before finalizing") - review them against a real print/classroom
pass before treating them as final. A Module Lesson-Plan prompt now exists
(`Generate_Module_Lesson_Plan_Prompt_v4.4.md`) but has not yet been run before-the-fact against a new Set/Pair, so
treat the folder shape above as a manually-applied convention for this retrofitted Set, not evidence that
Set-aware planning has been exercised from scratch yet.

## Module Pairs

For Intermediate, Advanced, and Proficient (Beginner is exempt - see `shared/Program_Conventions.md` §C's Module
Pair addendum and `Generate_Lesson_Prompt_v6.11.md`'s "THE MODULE PAIR"), two consecutive Modules pair into one
essay: odd with the next even (1-2, 3-4, 5-6, 7-8). Each Module keeps its own ordinary `Module_<N>/Set_<N>/`
folder, numbering, and version codes (§C/§D/§G are unaffected) - Module Pairing is a continuity layer above Set,
recorded via a new wrapping planning artifact rather than any change to Set mechanics:

```
lessons/<band>/
└── ModulePair_{N}-{N+1}/
    └── ModulePair_{N}-{N+1}_{Band}_Lesson_Plan.md
```

This doc (produced by `Generate_Module_Lesson_Plan_Prompt_v4.4.md`) plans both Modules together in one pass:
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

## First run against the shared-layer prompts (2026-09-08)

Intermediate Module 1 Set 1 Lesson 1 (`Lesson_1_MyPhoneCase/`) was regenerated against `Generate_Lesson_Prompt_v6.11.md`
plus the two shared files, and its packet against `Generate_Student_Packet_Prompt_v3.14.md` plus the Style Guide;
version `1.1.1.0` -> `1.1.1.1`. This is the dry run the restructure called for: the lesson's own self-check now
records both the shared §F items and the Writing items, and the shared item-quality rules caught three real gaps
in the previous version (Level 5 had no task of its own, the choose-the-form drill had throwaway distractors, the
Level 5 Mentor Text was under its sentence target). Lesson 2 (`Lesson_2_MyPhoneCase/`) was regenerated the same day in a
parallel session (`1.1.2.0` -> `1.1.2.1`), continuing the new Lesson 1 directly; see its `Changelog.md` row for what
changed. Lessons 3 and 4 followed (`1.1.3.1`, `1.1.4.2`), so the whole Intermediate Set now sits at v6
content; the Advanced Set is still at its pre-v6 content. See `Rotation_Log_Intermediate.md`'s per-lesson addenda
and `Changelog.md`'s per-lesson rows.

Later the same day the self-contained rule (Quality Standards §D8) took Lesson 1 to `1.1.1.2` and Lesson 3 to
`1.1.3.2`: every student works from their own phone case, and no picture is provided or shown by the teacher.
The four packets' Word Bank markup, which had come out three different ways, was then normalized to the Style
Guide's §F "Word banks" form (markup only; version codes unchanged).

Then, at the user's direction that four lessons on one phone case was too much of one object, the Scenario was
split into a practice object and a draft object (Conventions §C v1.9; Lesson prompt v6.2): Lesson 2's Day 2
prewriting now introduces the student's own jacket (`1.1.2.2`), and Lessons 3-4 were regenerated on it
(`1.1.3.3`, `1.1.4.3`) with their folders renamed `Lesson_3_MyJacket/` and `Lesson_4_MyJacket/`. Module 2's Set
continues the jacket draft. A last review of Lesson 3's packet then produced Quality Standards §D9 (a lesson
needs nothing a student made earlier except the carried draft) and §E6 (concrete prompts, no reflection questions,
at Beginner/Intermediate): Lesson 3 now opens with "pick one of these things to write about" and a three-word
plan (`1.1.3.4`), Lesson 2's prewriting is rehearsal (`1.1.2.3`), and Lesson 4's hand-off note is concrete
(`1.1.4.4`; the note was later cut altogether, `1.1.4.14`). A further review dropped Lesson 3's drawing box and "Finished early?" add-ons and split both
lessons' self-checks into one Task per star (Style Guide v2.4; `1.1.3.5`, `1.1.4.5`). Lessons 3-4 were then
renamed "My Clothing" (`Lesson_{3,4}_MyClothing/`) with an eight-item choice list, and the packets stripped of
object logistics, word ranges, and pacing lines (Style Guide v2.5; `1.1.2.4`, `1.1.3.6`, `1.1.4.6`). A final
review made the object a subject rather than a prop (no look-at or point-to anywhere; Quality Standards v1.3) and
turned Lesson 3's Day 2 into check-and-improve with no finish-your-piece task (Lesson prompt v6.5; `1.1.2.5`, `1.1.3.7`,
`1.1.4.7`), then merged each unit's check and fix into one Task per star (Style Guide v2.7; `1.1.3.8`,
`1.1.4.8`), renamed it "Check and Improve Your Writing" with every multi-step Task as numbered steps and no
wrap-up line (Style Guide v2.8; `1.1.3.9`, `1.1.4.9`). Because Lesson 3 Day 2 now checks and improves, Lesson 4
was regenerated to revise for effect instead of repeating the checklist (Lesson prompt v6.6; `1.1.4.10`).
Finally Lesson 1's packet dropped its "See How It's Done" section: the Mentor Ladder is teacher-presented and
never printed (packet prompt v3.10; `1.1.1.3`). Then every objective became the one skill sentence for every
student, with no object and no "some of you" (Quality Standards v1.4; `1.1.1.4`, `1.1.2.6`, `1.1.3.10`,
`1.1.4.11`). Last, the objective became a student can-do, "I can describe something of my own..." (Style Guide
v2.10; `1.1.1.5`, `1.1.2.7`, `1.1.3.11`, `1.1.4.12`). Then Levels 2-3's frame rounds were rotated into the 0.4d shapes so the frame is
completed once per lesson at most (Quality Standards v1.5 §D10; `1.1.1.6`, `1.1.2.8`, `1.1.3.12`, `1.1.4.13`). Last, Lesson 4's hand-off note section was cut and its Day 2 re-timed
(Lesson prompt v6.11, packet prompt v3.14; `1.1.4.14`, with one Lesson 3 overview line at `1.1.3.13`).

## Pending work

- **Self-contained rule (Quality Standards §D8, 2026-09-08):** the Intermediate My Phone Case Set is retrofitted
  (Lessons 1 and 3 revised; 2 and 4 needed nothing). The Advanced Two Apartments Set has not been checked against
  §D8 yet; grep its four lessons for "picture" or "provided" before the next regeneration.
- **Practice object vs draft object (Conventions §C v1.9, 2026-09-08):** applied to the Intermediate Set (phone
  case, then jacket). Module 2's Intermediate Set must continue the jacket draft, not the phone case. The Advanced
  Two Apartments Set predates the split and drafts on its practice subject; apply the split (a second, draft
  place) when that Set is next regenerated.
- **Self-contained across lessons / concrete prompts (Quality Standards §D9/§E6, 2026-09-08):** applied to the
  Intermediate Set. The Advanced Two Apartments Set still has Lesson 3's "Look back at your planning from Lesson
  2" (a §D9 violation); fix by building the plan inside Lesson 3's packet when that Set is next regenerated.
- **Objective wording (Quality Standards v1.4, 2026-09-08):** the Advanced Two Apartments packets' objectives
  name the Scenario ("compare two apartments for a friend"), say "Some of you will build...", and open "You
  will"; rewrite as the one "I can ..." skill sentence (Style Guide v2.10) at that Set's next regeneration.
- **No hand-off note (packet prompt v3.14, 2026-09-08):** the Advanced Two Apartments Lesson 4 packet still prints a
  "Before It Moves On" section; drop it for the one hand-off line under Final Copy at that Set's next regeneration.
- **Mentor Ladder not printed (packet prompt v3.10, 2026-09-08):** the Advanced Two Apartments Lesson 1 packet
  still prints its ladder as "See How It's Done"; remove at that Set's next regeneration.
- **Self-check Tasks (Style Guide v2.4 §F, 2026-09-08):** the Advanced Two Apartments Lesson 4 packet still puts
  two star tags on one self-check line and stars individual items; split into one Task per star when that Set
  is next regenerated.

- **First real, before-the-fact run of the prompt family against a brand-new Set or Module Pair.** Every prompt
  in this family (Module Lesson-Plan, Lesson, Homework, Assessment, Assessment print) has so far only been run
  either retroactively (Module Lesson-Plan, against the already-approved Set 1) or not at all (Homework,
  Assessment, Assessment print) - every number in them (item counts, timing checkpoints, essay-regime time
  budgets) is a first-pass estimate, the same status the Lesson prompt's own v1 numbers had before real-classroom
  correction. Expect addenda once each has actually been used to plan and generate a new Set/Pair from scratch.
- **Module 2 for Module Pair 1-2 (Intermediate and Advanced) has not been planned or generated.** Module 1's
  Lesson 4 has been retrofitted into a hand-off (see "Module Pairs" above), but the piece it hands off is not
  actually completed until Module 2's Set 1 is planned (via `Generate_Module_Lesson_Plan_Prompt_v4.4.md`, naming
  the Module Pair) and generated. This is the most load-bearing gap left by the Module Pair redesign - until it
  closes, both existing Sets end mid-arc.
- **Grammar/Essay Focus Bank "Alternate" rows are not yet authored.** `Generate_Lesson_Prompt_v6.11.md`'s Section
  0.4/0.4c gives exactly one Focus A/B per native Level; a Module Pair's second Module needs genuinely different
  content at the same native row (Section 0.9's within-pair non-repetition rule), which the Bank does not yet
  have a dedicated column for. Until authored, Module N+1's Focus A/B must be hand-selected and checked for
  distinctness each time a Pair is planned - a real content-authoring task, not a structural one.
- **Real-classroom calibration pass.** Section 0.2 length targets and the Section 0.4 grammar bank are
  first-draft estimates (see above); revise them once real lessons have been generated and taught, the same way
  Reading's prompt matured from v1 through v2.5.
