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
modalities actually differ. See `Generate_Lesson_Prompt_v6.md`, Section 0.1, for the specific reason: a Reading
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
| `Generate_Lesson_Prompt_v6.md` | Generates one **2-day lesson**: for Beginner, one of a Set's 4 fixed positions; for Intermediate/Advanced/Proficient, one of a Module Pair's 8 positions ("THE MODULE PAIR" section), each run producing one lesson at the named position against the approved plan. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; states only what is true of a writing lesson (the three-regime model and Scenario/Mentor Ladder in 0.1, per-Level output ceilings and required features in 0.2, the Grammar and Essay Focus banks and row-selection rules in 0.4/0.4c, self-revision evidence in 0.4a, content-volume minimums in 0.4b, checklists and Peer Editing timing in 0.6, the Module-to-form mapping in 0.9, the Module Pair arc and the per-lesson flow) and points to the shared files for everything modality-neutral. Section 0.3's self-check is the shared Quality Standards §F list plus 14 Writing-only items. Section 0 now uses `Lesson N, Day M` numbering throughout. | Current (v6); no lesson generated against it yet - all 8 existing lessons were generated under v4/v4.1 and retrofitted under v5 |
| `Generate_Module_Lesson_Plan_Prompt_v4.md` | Plans a full **Set** (Beginner) or **Module Pair** (Intermediate/Advanced/Proficient) in one pass: Scenario, genre, each Module's Focus A/B pairing, Essay Focus direction, the Module N+1 CSV-coverage task, Mentor Ladder direction, and the position table. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; general Rotation Log mechanics point to Conventions §F and the prompt keeps only Writing's cross-Band and within-pair rules. Writing objectives only. | Current (v4) |
| `Generate_Homework_Prompt_v4.md` | Generates one homework assignment (grammar focus in production plus skill practice) from a lesson's content so far, at any of the timing checkpoints (Beginner: after Lesson 1-4; others: after Pair position 1-8), one section per task Level keyed to its composition regime. Run with the two shared files pasted alongside; Section 3 is Quality Standards §F plus 6 Writing items. | Current (v4); not yet run against a real lesson |
| `Generate_Assessment_Prompt_v4.md` | Generates a Set's (Beginner) or Module Pair's Grammar & Mechanics Check (Part A) and Writing Task (Part B). Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; keeps what is Writing-specific (new example sentences, Focus A/B and Essay Focus coverage, objective-only Part A formats, a new Scenario matched in shape to the original, target lengths from 0.2, regime-dependent sittings, the 3-point rubric) and points to Quality Standards §C for item quality, which is where Writing's assessments now pick up the distractor, padded-bank, and requires-the-centerpiece rules they never had. Self-checks are Quality Standards §F plus 4 Part A and 6 Part B items. | Current (v4); not yet run against a real Set or Pair |
| `Generate_Assessment_Student_Packet_Prompt_v4.md` | Takes a completed Assessment and produces the student handout: Grammar Check pages per Level under lettered Tasks, Writing Task cards with the rubric's Meets column as a `.checklist` (Style Guide §H.4), no answer keys or rubric tables. Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; Section 5 is Style Guide §I plus 4 items. Its stale `.ans-line-tiny` mention is gone. | Current (v4); not yet run |
| `Rotation_Log.md`                                                                 | Overview only: purpose, this log's history (why it used to be flat, corrected 2026-09-08 to nest by Module/Set like Reading's), the cross-Set check, and the version-number note, plus links to each Band's own log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Intermediate.md`                                                    | Module 1's Set 1: four lessons (Intermediate 1-4), nested `## Module 1` → `### Set 1`, matching Reading's/Listening-Speaking's per-Band log shape (restructured 2026-09-08 from a flat single-row table). Lesson 4 retrofitted 2026-09-08 (v1.1.4.0 -> 1.1.4.1) as Part 1 of Module Pair 1-2 - see its 2026-09-08 addendum. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Advanced.md`                                                        | Same, for the Advanced Band (Module 1's Set 1, Advanced 1-4, also retrofitted as Part 1 of Module Pair 1-2). A new Band's file is created lazily the first time a Set in that Band is generated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Changelog.md`                                                                    | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | N/A (data, not a prompt)                                                                        |
| `lessons/intermediate/Module_1/Module1_Intermediate_Lesson_Plan.md`       | Output of `Generate_Module_Lesson_Plan_Prompt_v1.md`, run retroactively against the already-approved Intermediate Set 1 (predates the planning prompt) - reconstructs its Scenario, Grammar Focus A/B, Mentor Ladder direction, and self-check from that Set's own content. 2026-09-08 addendum notes the "Intermediate 1" single-lesson framing is now Set 1's four lessons (Intermediate 1-4). Second 2026-09-08 addendum notes this Set is now Part 1 of Module Pair 1-2, pending Module 2. | N/A (data, reconstructed from an existing Set) |
| `lessons/advanced/Module_1/Module1_Advanced_Lesson_Plan.md`               | Same, for the already-approved Advanced Set 1, including a note on the v3.1 Grammar Focus A/B row-selection correction that Set required. 2026-09-08 addendum notes the "Advanced 1" single-lesson framing is now Set 1's four lessons (Advanced 1-4). Second 2026-09-08 addendum notes this Set is now Part 1 of Module Pair 1-2, pending Module 2. | N/A (data, reconstructed from an existing Set) |
| `learningobjectives.csv` (project file, shared with Reading)                      | Source of truth for every Learning Objective, including the Writing modality's 64 rows (8 Levels x 8 Modules) this prompt pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | N/A (data)                                                                                      |
| `Writing Content Sample` (project doc)                                            | The user-supplied sample grounding Levels 1-5: two full grammar-in-context chapters from an academic ESL writing textbook (simple present / articles / simple and compound sentences; simple past / adverbs of manner / complex sentences with time clauses), each ending in a guided paragraph and peer edit. Structural reference only; the sample's own grammar sequence is not reproduced lesson-for-lesson.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                                                                                 |
| `Academic Writing Essay Content Sample.md` (new for v3)                           | The user-supplied sample grounding Levels 6-8: a full essay-writing textbook chapter (essay structure, hook types, direct/indirect thesis statements, topic sentences and outlining, combining sentences, six model essays with analysis activities across five essay types). Structural reference only, same convention as the paragraph-level sample: generated essays are original, not lifted from this chapter's own model essays.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | N/A (reference)                                                                                 |
| `Generate_Student_Packet_Prompt_v3.0.md` | Takes one completed 2-day lesson and produces its one-file, two-masthead-section packet (self-contained HTML). Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; states only what is specific to a Writing packet (Set-position Unit numbering and Scenario self-containment, the Task-label line rule, Grammar and essay-structure box translation, the Mentor Ladder as star-labeled examples, the hand-off-vs-finale closing check, Check Your Own Work / Trade and Check, Writing's own translation rows) and points to the Style Guide for the translation table, star and lettered-Task rules (including one-star-per-letter and no-star-in-a-callout, both originally Writing-only), the regeneration rule, the delta CSS (§H.3, recorded from the existing packets), and the shared packet self-check. Section 5 is Style Guide §I plus 10 Writing items. | Current (v3.0); all 8 existing packets were generated against v2-v2.5 and hand-corrected in earlier passes (see `Changelog.md`) |

## Generation workflow (current)

As of 2026-09-08, all four companion prompts exist alongside the Lesson prompt (TOEFL-track extensions are
explicitly out of scope for Writing for now - see `CLAUDE.md`'s Known Issues), and the whole family plans and
generates by **Set** (Beginner, 4 lessons) or by **Module Pair** (Intermediate/Advanced/Proficient, two Sets/8
lessons together), matching Reading's/Listening-Speaking's Set-planning workflow shape and extending it for three
of the four Bands. None of the three newer companions (Homework, Assessment, Assessment print) has been run
against a real Set or Pair yet; treat the step order below as the intended workflow, not a proven one.

**Step 1 - Plan the Set or Module Pair.** Run `Generate_Module_Lesson_Plan_Prompt_v4.md` against a Band (naming
one Module for Beginner, or a Module Pair like "Modules 1-2" for Intermediate/Advanced/Proficient) to decide the
shared Scenario, each Module's own Grammar Focus A/B pairing (and Essay Focus A/B direction, where applicable),
and Leveled Mentor Ladder direction before writing any lesson content, checked against the Rotation Log for
adjacency to the Band's own immediately preceding Set/Pair and, for a Pair, within-pair non-repetition between
its two Modules. Review and approve the plan, then append its Rotation Log entries (4 rows for Beginner, 8 split
across the two Modules' own sections for a Pair).

**Step 2 - Generate the lessons, one at a time.** Run `Generate_Lesson_Prompt_v6.md` (pasted with
`shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`) four times (Beginner) or eight
times (Intermediate/Advanced/Proficient) against the approved plan, once per Set/Pair position. It reads
`Rotation_Log.md` plus that Band's own `Rotation_Log_<Band>.md` first (per Section 0.9) for the arc's first
lesson; every later position continues what came before it directly rather than re-deriving it - including
position 5 (Module N+1's Lesson 1), which introduces Module N+1's own Focus A but does not re-derive the
Scenario. Pulls the Writing-modality CSV row for every task Level in the band, builds the Leveled Mentor Ladder,
and runs its own Section 0.3 self-check before each lesson is finalized. As with Reading, review and approve each
generated lesson before treating it as final. Once approved, the corresponding Rotation Log row (already appended
in Step 1) reflects that lesson.

**Optional - Student print handout.** Run `Generate_Student_Packet_Prompt_v3.0.md` against any completed lesson to
produce that lesson's one-file, two-masthead-section packet. Independent of the rotation-log step; can run any
time after that lesson is finalized, one lesson at a time (not once per Set/Pair).

**Optional - Homework.** Run `Generate_Homework_Prompt_v4.md` against a lesson's content so far, at any of the
timing checkpoints (Beginner: after Lesson 1/2/3/4; Intermediate/Advanced/Proficient: after Pair position 1-8)
that prompt's Section 0.2 defines.

**Optional - Assessment.** Run `Generate_Assessment_Prompt_v4.md` against a completed Set (Beginner, all 4
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
"Key differences" above).

As of 2026-09-08, `lessons/<band>/Module_1/Set_1/Lesson_{1-4}_<Slug>/` folders exist on disk for both the
Intermediate and Advanced Bands, each lesson folder holding its own 2-day Markdown doc plus a current-convention
(v2.5) print packet - one file, two masthead sections (`Generate_Student_Packet_Prompt_v3.0.md`). The same slug
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
same day, into Module Pair 1-2's Part 1 (see "Module Pairs" below). Intermediate Lesson 1's packet was hand-corrected
2026-09-08 for duplicate tasks (Unit 1A Task C/D, Unit 1B Task D/E - each pair merged to one task at the lower star
rating) and picture references with no picture in the packet (Unit 1A's frame tasks reworded to use the student's
own phone case; the "See How It's Done" section removed entirely) - see `Changelog.md`'s 2026-09-08
hand-correction entry. All 8 packets are first-pass generations per
the print prompt's own Section 4.1 ("iterate before finalizing") - review them against a real print/classroom
pass before treating them as final. A Module Lesson-Plan prompt now exists
(`Generate_Module_Lesson_Plan_Prompt_v4.md`) but has not yet been run before-the-fact against a new Set/Pair, so
treat the folder shape above as a manually-applied convention for this retrofitted Set, not evidence that
Set-aware planning has been exercised from scratch yet.

## Module Pairs

For Intermediate, Advanced, and Proficient (Beginner is exempt - see `shared/Program_Conventions.md` §C's Module
Pair addendum and `Generate_Lesson_Prompt_v6.md`'s "THE MODULE PAIR"), two consecutive Modules pair into one
essay: odd with the next even (1-2, 3-4, 5-6, 7-8). Each Module keeps its own ordinary `Module_<N>/Set_<N>/`
folder, numbering, and version codes (§C/§D/§G are unaffected) - Module Pairing is a continuity layer above Set,
recorded via a new wrapping planning artifact rather than any change to Set mechanics:

```
lessons/<band>/
└── ModulePair_{N}-{N+1}/
    └── ModulePair_{N}-{N+1}_{Band}_Lesson_Plan.md
```

This doc (produced by `Generate_Module_Lesson_Plan_Prompt_v4.md`) plans both Modules together in one pass:
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
  actually completed until Module 2's Set 1 is planned (via `Generate_Module_Lesson_Plan_Prompt_v4.md`, naming
  the Module Pair) and generated. This is the most load-bearing gap left by the Module Pair redesign - until it
  closes, both existing Sets end mid-arc.
- **Grammar/Essay Focus Bank "Alternate" rows are not yet authored.** `Generate_Lesson_Prompt_v6.md`'s Section
  0.4/0.4c gives exactly one Focus A/B per native Level; a Module Pair's second Module needs genuinely different
  content at the same native row (Section 0.9's within-pair non-repetition rule), which the Bank does not yet
  have a dedicated column for. Until authored, Module N+1's Focus A/B must be hand-selected and checked for
  distinctness each time a Pair is planned - a real content-authoring task, not a structural one.
- **Real-classroom calibration pass.** Section 0.2 length targets and the Section 0.4 grammar bank are
  first-draft estimates (see above); revise them once real lessons have been generated and taught, the same way
  Reading's prompt matured from v1 through v2.5.
