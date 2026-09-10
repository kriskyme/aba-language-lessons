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
modalities actually differ. See `Generate_Lesson_Prompt_v6.16.md`, Section 0.1, for the specific reason: a Reading
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
| `Generate_Lesson_Prompt_v6.16.md` | Generates one **2-day lesson**: for Beginner, one of a Set's 4 fixed positions; for Intermediate/Advanced/Proficient, one of a Module Pair's 8 positions ("THE MODULE PAIR" section), each run producing one lesson at the named position against the approved plan. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; states only what is true of a writing lesson (the three-regime model and Scenario/Mentor Ladder in 0.1, per-Level output ceilings and required features in 0.2, the Grammar and Essay Focus banks and row-selection rules in 0.4/0.4c, self-revision evidence in 0.4a, content-volume minimums in 0.4b, checklists and Peer Editing timing in 0.6, the Module-to-form mapping in 0.9, the Module Pair arc and the per-lesson flow) and points to the shared files for everything modality-neutral. Section 0.3's self-check is the shared Quality Standards §F list plus 16 Writing-only items. Section 0 now uses `Lesson N, Day M` numbering throughout. | Current (v6.15, 2026-09-09: activity keys on `Answer note:` lines, never inside an item - see `Changelog.md`); all four Intermediate Set 1 lessons regenerated against v6 2026-09-08 and Lessons 2-4 revised under v6.2's practice/draft-object split and v6.3's self-contained/concrete-prompt rules the same day (1.1.1.6, 1.1.2.8, 1.1.3.12, 1.1.4.13; see "First run" below); the Advanced Set's four lessons were generated under v4/v4.1 and retrofitted under v5 |
| `Generate_Module_Lesson_Plan_Prompt_v4.5.md` | Plans a full **Set** (Beginner) or **Module Pair** (Intermediate/Advanced/Proficient) in one pass: Scenario, genre, each Module's Focus A/B pairing, Essay Focus direction, the Module N+1 CSV-coverage task, Mentor Ladder direction, and the position table. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; general Rotation Log mechanics point to Conventions §F and the prompt keeps only Writing's cross-Band and within-pair rules. Writing objectives only. | Current (v4.5) |
| `Generate_Homework_Prompt_v4.4.md` | Generates one homework assignment (grammar focus in production plus skill practice) from a lesson's content so far, at any of the timing checkpoints (Beginner: after Lesson 1-4; others: after Pair position 1-8), one section per task Level keyed to its composition regime. Run with the two shared files pasted alongside; Section 3 is Quality Standards §F plus 6 Writing items. | Current (v4.4, 2026-09-09: any exemplar on an `Answer note:` line, never in the item - see `Changelog.md`); not yet run against a real lesson |
| `Generate_Assessment_Prompt_v4.2.md` | Generates a Set's (Beginner) or Module Pair's Grammar & Mechanics Check (Part A) and Writing Task (Part B). Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; keeps what is Writing-specific (new example sentences, Focus A/B and Essay Focus coverage, objective-only Part A formats, a new Scenario matched in shape to the original, target lengths from 0.2, regime-dependent sittings, the 3-point rubric) and points to Quality Standards §C for item quality, which is where Writing's assessments now pick up the distractor, padded-bank, and requires-the-centerpiece rules they never had. Self-checks are Quality Standards §F plus 4 Part A and 6 Part B items. | Current (v4); not yet run against a real Set or Pair |
| `Generate_Assessment_Student_Packet_Prompt_v4.md` | Takes a completed Assessment and produces the student handout: Grammar Check pages per Level under lettered Tasks, Writing Task cards with the rubric's Meets column as a `.checklist` (Style Guide §H.4), no answer keys or rubric tables. Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; Section 5 is Style Guide §I plus 4 items. Its stale `.ans-line-tiny` mention is gone. | Current (v4); not yet run |
| `Rotation_Log.md`                                                                 | Overview only: purpose, this log's history (why it used to be flat, corrected 2026-09-08 to nest by Module/Set like Reading's), the cross-Set check, and the version-number note, plus links to each Band's own log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Intermediate.md`                                                    | Module 1's Set 1 (Intermediate 1-4, `1.1.x`) and Module 2's Set 1 (Intermediate 1-4 again, `2.1.x.0`, generated 2026-09-09), nested `## Module N` → `### Set 1`, cross-referenced as Parts 1 and 2 of Module Pair 1-2; one dated addendum per regenerated Module 1 lesson. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Rotation_Log_Advanced.md`                                                        | Same, for the Advanced Band (Module 1's Set 1, Advanced 1-4, Part 1 of Module Pair 1-2, regenerated 2026-09-08 as Two Places to Study). A new Band's file is created lazily the first time a Set in that Band is generated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A (data, not a prompt)                                                                        |
| `Changelog.md`                                                                    | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | N/A (data, not a prompt)                                                                        |
| `lessons/intermediate/ModulePair_1-2/ModulePair_1-2_Intermediate_Lesson_Plan.md` | Plan 1.0 (2026-09-09), the single plan for the whole Intermediate Pair, generated against `Generate_Module_Lesson_Plan_Prompt_v4.5.md` before Module 2's lessons were written (the family's first before-the-fact Pair plan). Restates Module 1's fixed decisions, adds Module 2's hand-selected Focus A/B (simple past + time connectors / time clauses; then / than), the built-in-parts position table, the Lesson 8 Module 2 verb task ("this morning"), the Mentor Ladder second-look direction, and per-lesson activity shapes. Supersedes the Module 1 plan below. | N/A (data, a plan) |
| `lessons/intermediate/Module_1/Module1_Intermediate_Lesson_Plan.md`       | Output of `Generate_Module_Lesson_Plan_Prompt_v1.md`, run retroactively against the already-approved Intermediate Set 1 (predates the planning prompt) - reconstructs its Scenario, Grammar Focus A/B, Mentor Ladder direction, and self-check from that Set's own content, with ten dated addenda. **Superseded 2026-09-09** by the Pair plan above; kept for its history. | N/A (data, superseded) |
| `lessons/advanced/Module_1/Module1_Advanced_Lesson_Plan.md`               | Plan 2.0 (2026-09-08), regenerated against `Generate_Module_Lesson_Plan_Prompt_v4.5.md`: Scenario Two Places to Study (practice object my room; draft object the student's home vs. one place from a printed list, for Dana, who needs quiet), Focus A/B at Level 5's row, Essay Focus A/B at Level 6's, per-lesson activity shapes, and a History block holding the Two Apartments plan and its two addenda. Module 2's Set is still unplanned; a Pair plan will supersede this file. | N/A (data, reconstructed from an existing Set) |
| `learningobjectives.csv` (project file, shared with Reading)                      | Source of truth for every Learning Objective, including the Writing modality's 64 rows (8 Levels x 8 Modules) this prompt pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | N/A (data)                                                                                      |
| `Writing Content Sample` (project doc)                                            | The user-supplied sample grounding Levels 1-5: two full grammar-in-context chapters from an academic ESL writing textbook (simple present / articles / simple and compound sentences; simple past / adverbs of manner / complex sentences with time clauses), each ending in a guided paragraph and peer edit. Structural reference only; the sample's own grammar sequence is not reproduced lesson-for-lesson.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                                                                                 |
| `Academic Writing Essay Content Sample.md` (new for v3)                           | The user-supplied sample grounding Levels 6-8: a full essay-writing textbook chapter (essay structure, hook types, direct/indirect thesis statements, topic sentences and outlining, combining sentences, six model essays with analysis activities across five essay types). Structural reference only, same convention as the paragraph-level sample: generated essays are original, not lifted from this chapter's own model essays.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | N/A (reference)                                                                                 |
| `Generate_Student_Packet_Prompt_v3.17.md` | Takes one completed 2-day lesson and produces its one-file, two-masthead-section packet (self-contained HTML). Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; states only what is specific to a Writing packet (Set-position Unit numbering and Scenario self-containment, the Task-label line rule, Grammar and essay-structure box translation, the Mentor Ladder as star-labeled examples, the hand-off-vs-finale closing check, Check Your Own Work / Trade and Check, Writing's own translation rows) and points to the Style Guide for the translation table, star and lettered-Task rules (including one-star-per-letter and no-star-in-a-callout, both originally Writing-only), the regeneration rule, the delta CSS (§H.3, recorded from the existing packets), and the shared packet self-check. Section 5 is Style Guide §I plus 10 Writing items. | Current (v3.17, 2026-09-09: both masthead sections carry the meta stack; v3.16, same day: Answer notes and error keys stripped, stems carried without answer-stating parentheticals - see `Changelog.md`); all four Intermediate Set 1 packets regenerated against v3.x 2026-09-08 alongside their lessons; the Advanced Set's four packets were generated against v2-v2.5 and hand-corrected in earlier passes (see `Changelog.md`); all 12 carry the two-line `.masthead-meta` stack (modality `·` Module name, then Band and version code) on both mastheads as of 2026-09-09 |

## Generation workflow (current)

As of 2026-09-08, all four companion prompts exist alongside the Lesson prompt (TOEFL-track extensions are
explicitly out of scope for Writing for now - see `CLAUDE.md`'s Known Issues), and the whole family plans and
generates by **Set** (Beginner, 4 lessons) or by **Module Pair** (Intermediate/Advanced/Proficient, two Sets/8
lessons together), matching Reading's/Listening-Speaking's Set-planning workflow shape and extending it for three
of the four Bands. None of the three newer companions (Homework, Assessment, Assessment print) has been run
against a real Set or Pair yet; treat the step order below as the intended workflow, not a proven one.

**Step 1 - Plan the Set or Module Pair.** Run `Generate_Module_Lesson_Plan_Prompt_v4.5.md` against a Band (naming
one Module for Beginner, or a Module Pair like "Modules 1-2" for Intermediate/Advanced/Proficient) to decide the
shared Scenario, each Module's own Grammar Focus A/B pairing (and Essay Focus A/B direction, where applicable),
and Leveled Mentor Ladder direction before writing any lesson content, checked against the Rotation Log for
adjacency to the Band's own immediately preceding Set/Pair and, for a Pair, within-pair non-repetition between
its two Modules. Review and approve the plan, then append its Rotation Log entries (4 rows for Beginner, 8 split
across the two Modules' own sections for a Pair).

**Step 2 - Generate the lessons, one at a time.** Run `Generate_Lesson_Prompt_v6.16.md` (pasted with
`shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`, fetching and citing any image a lesson
needs in this same step per `shared/Program_Conventions.md` §I) four times (Beginner) or eight
times (Intermediate/Advanced/Proficient) against the approved plan, once per Set/Pair position. It reads
`Rotation_Log.md` plus that Band's own `Rotation_Log_<Band>.md` first (per Section 0.9) for the arc's first
lesson; every later position continues what came before it directly rather than re-deriving it - including
position 5 (Module N+1's Lesson 1), which introduces Module N+1's own Focus A but does not re-derive the
Scenario. Pulls the Writing-modality CSV row for every task Level in the band, builds the Leveled Mentor Ladder,
and runs its own Section 0.3 self-check before each lesson is finalized. As with Reading, review and approve each
generated lesson before treating it as final. Once approved, the corresponding Rotation Log row (already appended
in Step 1) reflects that lesson.

**Optional - Student print handout.** Run `Generate_Student_Packet_Prompt_v3.17.md` against any completed lesson to
produce that lesson's one-file, two-masthead-section packet. Independent of the rotation-log step; can run any
time after that lesson is finalized, one lesson at a time (not once per Set/Pair).

**Optional - Homework.** Run `Generate_Homework_Prompt_v4.4.md` against a lesson's content so far, at any of the
timing checkpoints (Beginner: after Lesson 1/2/3/4; Intermediate/Advanced/Proficient: after Pair position 1-8)
that prompt's Section 0.2 defines.

**Optional - Assessment.** Run `Generate_Assessment_Prompt_v4.2.md` against a completed Set (Beginner, all 4
lessons) or Module Pair (Intermediate/Advanced/Proficient, all 8 lessons) to produce Part A (Grammar & Mechanics
Check) and Part B (Writing Task), then `Generate_Assessment_Student_Packet_Prompt_v4.md` in the same session to
produce the student-facing printable version.

## Key differences from Passage Reading (read before assuming parity)

- **One shared Scenario per Set, not 4 independent anchor texts.** This is the one place a Writing Set still
  differs structurally from a Reading Set now that both use 2-day lessons, 4 per Set. A Reading Set's 4 lessons
  each get their own anchor text; a Writing Set's 4 lessons all write about the *same* Scenario, carried from
  grammar input (Lessons 1-2) through drafting (Lesson 3) toward the Module's finished part of the piece (Lesson
  4) - closer to one continuous project than four independent lessons that happen to share a Module/Band.
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
within that one Set; for Intermediate/Advanced/Proficient, carried as the Module's part of a piece built across
two Sets (see "Module Pairs" below) - rather than 4 independent anchor texts the way a Reading Set's lessons work (see
"Key differences" above). Since 2026-09-08 the Scenario names two of the student's own belongings: a **practice
object** for Lessons 1-2's grammar work and Mentor Ladder, and a **draft object** introduced at Lesson 2 Day 2's
prewriting that Lessons 3-4 and the Pair's second Module write about (`shared/Program_Conventions.md` §C; Lesson
prompt 0.1a).

As of 2026-09-08, `lessons/<band>/Module_1/Set_1/Lesson_{1-4}_<Slug>/` folders exist on disk for both the
Intermediate and Advanced Bands, each lesson folder holding its own 2-day Markdown doc plus a print packet - one
file, two masthead sections (v2.5-era for most; Intermediate Lesson 3's was regenerated 2026-09-08 under
`Generate_Student_Packet_Prompt_v3.17.md` alongside its Markdown's v6 regeneration, 1.1.3.1). The slug names
the object that lesson writes about (unlike Reading, where each lesson folder gets its own topic slug): the
practice object's slug on Lessons 1-2, the draft object's slug on Lessons 3-4 and on a Pair's second Module. Sets
generated before the 2026-09-08 practice/draft split carry one slug across all four folders:

- `lessons/intermediate/Module_1/Set_1/Lesson_1_MyPhoneCase/` and `Lesson_2_MyPhoneCase/` - `Lesson{1-2}_MyPhoneCase.md`, `MyPhoneCase_Intermediate_L{1-2}_Packet.html` (Intermediate 1-2, practice object); `Lesson_3_MyClothing/` and `Lesson_4_MyClothing/` - `Lesson{3-4}_MyClothing.md`, `MyClothing_Intermediate_L{3-4}_Packet.html` (Intermediate 3-4, draft object: one piece of the student's clothing from a printed list)
- `lessons/intermediate/Module_2/Set_1/Lesson_{1,2,3,4}_MyClothing/` - `Lesson{1-4}_MyClothing.md`, `MyClothing_Intermediate_L{1-4}_Packet.html` (Module 2's Intermediate 1-4, `2.1.1.0` to `2.1.4.0`, generated 2026-09-09; all four on the draft object, Pair positions 5-8)
- `lessons/advanced/Module_1/Set_1/Lesson_1_MyRoom/`, `Lesson_2_MyRoom/` (`Lesson{1,2}_MyRoom.md`, `MyRoom_Advanced_L{1,2}_Packet.html`) and `Lesson_3_TwoPlacesToStudy/`, `Lesson_4_TwoPlacesToStudy/` (`Lesson{3,4}_TwoPlacesToStudy.md`, `TwoPlacesToStudy_Advanced_L{3,4}_Packet.html`) (Advanced 1-4; regenerated 2026-09-08 as Two Places to Study)

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
(`Generate_Module_Lesson_Plan_Prompt_v4.5.md`) but has not yet been run before-the-fact against a new Set/Pair, so
treat the folder shape above as a manually-applied convention for this retrofitted Set, not evidence that
Set-aware planning has been exercised from scratch yet.

## Module Pairs

For Intermediate, Advanced, and Proficient (Beginner is exempt - see `shared/Program_Conventions.md` §C's Module
Pair addendum and `Generate_Lesson_Prompt_v6.16.md`'s "THE MODULE PAIR"), two consecutive Modules pair into one
essay: odd with the next even (1-2, 3-4, 5-6, 7-8), **built in parts** (Conventions §C v1.10): the first Module
drafts the body paragraphs under a working thesis (essay Levels) or its one paragraph (paragraph Levels), the
second Module drafts the introduction and conclusion or its own second paragraph, and position 8 assembles,
peer-edits, and publishes; neither Module drafts a complete piece. Each Module keeps its own ordinary `Module_<N>/Set_<N>/`
folder, numbering, and version codes (§C/§D/§G are unaffected) - Module Pairing is a continuity layer above Set,
recorded via a new wrapping planning artifact rather than any change to Set mechanics:

```
lessons/<band>/
└── ModulePair_{N}-{N+1}/
    └── ModulePair_{N}-{N+1}_{Band}_Lesson_Plan.md
```

This doc (produced by `Generate_Module_Lesson_Plan_Prompt_v4.5.md`) plans both Modules together in one pass:
Scenario/genre (fixed once, by Module N's own mapping), each Module's own Grammar/Essay Focus A/B (checked for
within-pair non-repetition), the full 8-lesson content-role table, and the CSV-objective-coverage check for
Module N+1's own verb (see the Lesson prompt's own "THE MODULE PAIR" section for what that check resolves). It
supersedes having two separate `Module{N}_{Band}_Lesson_Plan.md` docs for a paired Module going forward.

**Module Pair 1-2, Intermediate: complete (2026-09-09).** Module 1's Set 1 was retrofitted 2026-09-08 into Part
1 (Lesson 4 ends in a kept, self-revised paragraph, not a published piece), and Module 2's Set 1 was planned
by `lessons/intermediate/ModulePair_1-2/ModulePair_1-2_Intermediate_Lesson_Plan.md` and generated the next day
as Part 2: Lesson 5 re-engages the kept paragraph and teaches the simple past with time connectors, Lesson 6
time clauses and then / than with a plan against the kept paragraph, Lesson 7 drafts the story paragraph and
runs the merged checklist over both, and Lesson 8 assembles the two paragraphs under one title, peer-edits,
revises for effect, publishes by gallery walk, and closes with the two Transfer Checks. **Module Pair 1-2,
Advanced: Part 1 only.** Advanced Module 1 Set 1 is retrofitted the same way, but Module 2 has not been
planned or generated for Advanced and no `ModulePair_1-2_Advanced_Lesson_Plan.md` exists yet - see Pending work
below.

## First run against the shared-layer prompts (2026-09-08)

Intermediate Module 1 Set 1 Lesson 1 (`Lesson_1_MyPhoneCase/`) was regenerated against `Generate_Lesson_Prompt_v6.13.md`
plus the two shared files, and its packet against `Generate_Student_Packet_Prompt_v3.17.md` plus the Style Guide;
version `1.1.1.0` -> `1.1.1.1`. This is the dry run the restructure called for: the lesson's own self-check now
records both the shared §F items and the Writing items, and the shared item-quality rules caught three real gaps
in the previous version (Level 5 had no task of its own, the choose-the-form drill had throwaway distractors, the
Level 5 Mentor Text was under its sentence target). Lesson 2 (`Lesson_2_MyPhoneCase/`) was regenerated the same day in a
parallel session (`1.1.2.0` -> `1.1.2.1`), continuing the new Lesson 1 directly; see its `Changelog.md` row for what
changed. Lessons 3 and 4 followed (`1.1.3.1`, `1.1.4.2`), so the whole Intermediate Set now sits at v6
content, and the Advanced Set was regenerated in full 2026-09-08 as Two Places to Study against v6.12 (`1.1.1.1`, `1.1.2.1`, `1.1.3.1`, `1.1.4.2`), then revised for the built-in-parts Pair model under v6.13 (`1.1.1.2`, `1.1.2.2`, `1.1.3.2`, `1.1.4.3`; Intermediate Lesson 4 `1.1.4.15`). See `Rotation_Log_Intermediate.md`'s per-lesson addenda
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

**First before-the-fact run (2026-09-09).** Intermediate Module 2 Set 1 is the first Set in this family planned
before its lessons existed: `Generate_Module_Lesson_Plan_Prompt_v4.5.md` produced the Pair plan (Module 2's
Focus A/B hand-selected at Level 4's row, the Lesson 8 verb task named, the position table filled), then
`Generate_Lesson_Prompt_v6.13.md` ran four times at Pair positions 5-8 against it (`2.1.1.0` to `2.1.4.0`) and
`Generate_Student_Packet_Prompt_v3.17.md` once per lesson. Two judgment calls the prompts left open, recorded in
the plan: Lessons 5-8's grammar practice and frame shapes all sit on the draft object (Lesson prompt 0.1a's
"every later position writes about the draft object only"), with the practice object returning only in the
Mentor Ladder second look; and the Level 2-3 past frames carry the item as their object ("I ___-ed it.") so the
frame stays on the draft object. One prompt gap found: Lesson prompt 0.4's Level 4 row gives "the comma after an
opening reason clause" but says nothing about a comma after a short opening time phrase, so Module 2's Lesson 1
states it as optional and Lesson 2 teaches the required comma after an opening time clause.

## Pending work

- **Room-neutral backlog (Quality Standards §D11, 2026-09-09):** Intermediate
  `Module_2/Set_1/Lesson_4_MyClothing/` publishes the finished piece as a gallery walk (Day 2 phase table, the
  publish step, and self-check items 16-17 all name it). Replace with a read-aloud to two partners in turn, or
  copies passed around, keeping the per-Level card task the gallery walk currently carries, when the lesson is
  next touched. The Lesson prompt no longer offers the option as of v6.16. Do not generate new content with the
  old pattern.

- **Self-contained rule (Quality Standards §D8, 2026-09-08):** applied to both Sets (the Intermediate Set
  retrofitted; the Advanced Set regenerated).
- **Practice object vs draft object (Conventions §C v1.9, 2026-09-08):** applied to both Sets. Module 2's
  Intermediate Set must continue the clothing draft, not the phone case; Module 2's Advanced Set must continue
  the two-places-to-study draft, not the room.
- **Self-contained across lessons / concrete prompts (Quality Standards §D9/§E6), objective wording, the
  hand-off note, the printed Mentor Ladder, and self-check Tasks:** all applied to both Sets as of 2026-09-08
  (the Advanced Set by regeneration). No packet backlog remains for either Set.

- **First real, before-the-fact run: done for the Module Lesson-Plan, Lesson, and packet prompts (Intermediate
  Module 2, 2026-09-09; see "First before-the-fact run" above); not yet for Homework, Assessment, or Assessment
  print.** Those three have never been run against a real Set or Pair, so every number in them (item counts,
  timing checkpoints, essay-regime time budgets) is still a first-pass estimate. The completed Intermediate Pair
  is the natural first target for all three.
- **Module 2 for Module Pair 1-2, Advanced, has not been planned or generated.** (Intermediate's closed
  2026-09-09; see "Module Pairs" above.) Advanced Module 1's Lesson 4 hands off the body paragraphs under a
  working thesis, and that piece is not completed until Advanced Module 2's Set 1 is planned (via
  `Generate_Module_Lesson_Plan_Prompt_v4.5.md`, naming the Module Pair, saved as
  `lessons/advanced/ModulePair_1-2/ModulePair_1-2_Advanced_Lesson_Plan.md`) and generated at Pair positions 5-8
  with Essay Focus A (the introduction and conclusion). The Intermediate Pair is the worked model for that run.
- **Intermediate Module 2 Set 1 is untaught.** Its four lessons and packets (`2.1.x.0`) are first-pass
  generations; review them against a real print and classroom pass before treating them as final, the same way
  Module 1's Set was revised through fourteen versions.
- **Grammar Focus Bank, Level 4 Alternate row: a candidate exists.** The pair hand-selected for Intermediate
  Module 2 (Focus A: simple past forms with the -ed spelling rules, an irregular list, and time connectors;
  Focus B: complex sentences with a time clause, comma after an opening clause; confusable pair then / than;
  Level 5 extension: past-continuous background and adverbs of manner) fits a Narrating Module at the Level 4
  row and could be authored into the bank as its first Alternate entry once taught.
- **Grammar/Essay Focus Bank "Alternate" rows are not yet authored.** `Generate_Lesson_Prompt_v6.16.md`'s Section
  0.4/0.4c gives exactly one Focus A/B per native Level; a Module Pair's second Module needs genuinely different
  content at the same native row (Section 0.9's within-pair non-repetition rule), which the Bank does not yet
  have a dedicated column for. Until authored, Module N+1's Focus A/B must be hand-selected and checked for
  distinctness each time a Pair is planned - a real content-authoring task, not a structural one.
- **Real-classroom calibration pass.** Section 0.2 length targets and the Section 0.4 grammar bank are
  first-draft estimates (see above); revise them once real lessons have been generated and taught, the same way
  Reading's prompt matured from v1 through v2.5.
