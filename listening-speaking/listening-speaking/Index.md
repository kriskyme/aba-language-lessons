# Listening/Speaking Index

_This is the Listening/Speaking counterpart to Passage Reading's `Index.md` - same purpose (a living index of the file
family, sync status, and run order), same living-document rule (update it whenever a doc in this family is added,
renamed, or revised). Both index docs describe sibling prompt families that share `learningobjectives.csv` and
the same 8-Module skill taxonomy, but each family's lesson type and workflow are otherwise independent. Version
history lives in `Changelog.md`._

## What this document is

A single reference for everything in the Listening/Speaking prompt family: what each file does, whether it's in
sync with the current lesson-generation prompt, and the order to run them in to produce a module of lessons.
"Listening/Speaking" is the lesson type these prompts generate: a fixed 2-day cycle built around one shared,
real (not invented) audio or video source, differentiated into band-scoped task Levels across a Listening half
(Day 1) and a Speaking half (Day 2).

## How this differs from Passage Reading, and why

The Listening Speaking Content Sample (a real textbook unit) that grounded this design is far richer than a single
Passage Reading anchor text: one vocabulary set, three listening passes, a listening-skill lesson, a note-taking
lesson, a speaking-skill lesson, a pronunciation lesson, and a group presentation, all built around one class
discussion recording alone, before a second (video) source and synthesis project even start. Four decisions came
out of scoping this against that sample:

1. **The source is real, always found via search, never invented.** Unlike Passage Reading's original anchor
   texts, a Listening/Speaking lesson points to an actual existing recording (a TED Talk, a news segment, a
   podcast clip) with a genuine transcript, cited in full so the teacher can play it. See the Lesson prompt's
   Section 0.3 for the sourcing and fair-use rules this requires that Passage Reading never needed.
2. **One source per lesson,** matching Passage Reading's one-anchor-text-per-lesson simplicity. The sample's
   second (video) source plus its synthesis/group-presentation project is scoped as a planned, separate,
   optional extension on top of a completed core lesson (see Pending work below) - not part of every cycle.
3. **The cycle builds toward two performances in two days, not one in one.** `learningobjectives.csv` pairs a
   Listening can-do with a Speaking can-do at every Level, so one lesson has to build toward two performances,
   and a found real source (rather than a written-to-length one) still carries the sample's full skill set:
   listening comprehension, a named listening strategy, note-taking, critical thinking, a speaking skill modeled
   on the real speaker's own language, and pronunciation, before any oral output protocol - all compressed into
   one real 75-minute period per half rather than spread across four. Day 1 builds the Listening half; Day 2
   builds the Speaking half; see the Lesson prompt's Unit Architecture.
4. **A module holds 4 lessons,** matching Passage Reading's own module size now that the cycle lengths actually
   match (2 days each). Total instructional days per module (4 lessons x 2 days = 8 days) is the same footprint
   as Passage Reading's per-module length.

## File index

| File                                                                 | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Sync status                                                                                                                                                                                                         |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Listening Speaking Lesson Generation Prompt v1.md`                  | Generates one lesson (a 2-day cycle: Day 1 Listening, Day 2 Speaking): sources a real audio/video text, builds tiered listening and speaking tasks around it. Carries five addenda, including the day-count/Unit Architecture correction and balanced-duration item counts.                                                                                                                                                                                                                                                                                                                                                                              | Current (v1 + five addenda); six real lessons generated against it (Intermediate 1-4, Advanced 1-2), all six on the current 2-day cycle                                                        |
| `Listening Speaking Module Lesson-Plan Generation Prompt v1.md`      | Plans one Set (4 lessons by default, matching the 2-day cycle) for a given Module/Band - topic directions, content-format/strategy/skill rotation, task-Level-to-objective mapping - before any lesson content is generated. A Module/Band can hold more than one Set over time (a fresh rotation for a retaught semester); lesson numbering stays global across Sets. Listening/Speaking-modality objectives only.                                                                                                                                                                                                                                                       | Current (v1 + Sets correction); Module 1 Intermediate and Advanced retroactively relabeled as Set 1 + Set 2 - see progress sections below |
| `Rotation_Log.md`                                                     | Running record of every approved Set's format/strategy/skill/hook/protocol/vocabulary/topic choices, one subsection per Set under each Module/Band's section. Read before planning a new Set; appended to after approval.                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Two Module/Band sections (Intermediate, Advanced), each split into Set 1/Set 2                                                 |
| `Changelog.md`                                                        | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | N/A (data, not a prompt)                                                                                                                                                                                            |
| `Listening Speaking Student Print Formatting Prompt v1.md`           | Takes one completed lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML), mirroring Passage Reading's print prompt (same base stylesheet, same star-rating system), adapted for a real-source lesson: a plain citation box instead of a printed passage, a fillable Listening Notes organizer instead of an annotation key, two parts (Unit \_A Listening / Unit \_B Speaking) instead of Unit \_A/\_B by calendar day.                                                                                                                                                                                                       | Current (v1); six packets generated (Intermediate 1-4, Advanced 1-2), all six current against this prompt's conventions                                                                            |
| `Listening Speaking Assessment Generation Prompt v1.md`              | Generates the assessment layer on top of a taught Set, both parts run every Set: Part A, an individual Listening assessment (new unseen source, task-Level-tiered items, in-class, same period length as a lesson's Day 1); Part B, a Speaking assessment whose mechanism splits by band - Beginner/Intermediate scored via a Teams Speaking Progress solo recording (the recording IS the assessment); Advanced/Proficient default to a live solo/group presentation, with a same-task, same-rubric Teams-recording version always also generated as a standing scored alternate. | Current (v1); one assessment generated (Intermediate Set 1) - not yet run for Advanced, field-testing pending                                                                                                       |
| `learningobjectives.csv` (project file, shared with Passage Reading) | Source of truth for every Learning Objective, including the Listening/Speaking modality rows this family pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | N/A (data)                                                                                                                                                                                                          |

Not yet started for this family: a homework-generation prompt and the Part-2/presentation-project extension
described above. See Pending work.

## Module 1 progress, Intermediate Band (Describing, Intermediate)

Plan approved and logged: `Listening Speaking Module 1 (Intermediate) - Lesson Plan.md`. Task
Levels 2, 3, 4, 5 (Intermediate band). **Set 1 complete:** Lessons 1-4 fill one full rotation's
8-day allocation.

| File                                                                                               | Lesson # | Real source                                                                                              | Status                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Listening Speaking Module 1, Lesson 1 (Intermediate) - New Bakery, Old Baking Method.md`          | 1        | "New Bakery, Old Baking Method," VOA Learning English (Jonathan Bethony, Seylou Bakery, Washington D.C.) | Current (source is audio, not video; item counts balanced)                                                                        |
| `Listening Speaking Module 1, Lesson 2 (Intermediate) - A Food Tour Through Porto's Old Market.md` | 2        | "Porto Food Tour," Rick Steves Classroom Europe (guide Andre, Taste Porto Food Tours)                    | Current                                                                                                                                                                    |
| `Listening Speaking Module 1, Lesson 3 (Intermediate) - How to Choose a Backpack.md`               | 3        | "How to Choose a Backpack," REI Co-op Expert Advice (article + embedded video)                           | Current. Flagged deviations: source register not simplified for learners (draws only from simpler sections); module alignment reasoned through (Describing vs. Instructing)                                       |
| `Listening Speaking Module 1, Lesson 4 (Intermediate) - Great-Grandmother Learns English.md`       | 4        | "Great-Grandmother Proves It Is Never Too Late to Learn," VOA Learning English (Setsuko Takamizawa)      | Current. Flagged deviations: vocabulary-theme mismatch (family-relationship words vs. planned "personality & character traits"); Speaking Skill grounded in source context rather than a directly quoted exchange |

**Set 2 (Lessons 5-8: Nature description, Craft-studio tour, Museum/exhibit-guide description, Atelier/workshop
profile) is planned only, not yet generated** - a second full rotation of topics for whenever this module is
retaught with fresh material, per the Lesson Plan's Sets note. Not needed to complete this module; Set 1 already
does that on its own.

All four Set 1 lessons' student packets (`.html`) are current against the Student Print Formatting Prompt
standard (Good to Know at the top, citebox at the point of watching, compact inline multiple-choice, real
picture placeholders, word banks positioned before their items, universal question numbering, full-width answer
lines, the `.match-row`/`.qitem`/`.num` consistency fixes) - see that prompt's own changelog for the complete
list. Not yet reviewed against a printed page.

**Set 1's Listening/Speaking Assessment:** `claude/Listening Speaking Module 1
(Intermediate) - Set 1 Assessment.md`. Part A (Listening) uses a new, verified real source - "Visitors Laugh
Away Troubles at the HaHaHouse Museum" (VOA Learning English, a real laughter museum in Zagreb, Croatia) -
distinct from all 4 taught sources, with tiered items covering all four of the Set's listening strategies (Main
Ideas/Gist, Recognize Examples, Sequence Markers, Predict from Context). Part B (Speaking) is a Teams Speaking
Progress solo recording (Intermediate's default mechanism), emphasizing Making Comparisons and Sequencing
Language, with the same-task live-delivery option noted per the current prompt. This is the first assessment
ever generated against this prompt - not yet given to a real class, so treat every number in it (period length,
item counts, target recording lengths) as a reasoned starting point pending real classroom feedback, per the
prompt's own open items.

## Module 1 progress, Advanced Band (Describing, Advanced)

Plan approved and logged: `Listening Speaking Module 1 (Advanced) - Lesson Plan.md`. Task Levels
4, 5, 6, 7 (Advanced band). Level 7's Listening objective needs two real sources on the same subject (compare
rhetorical framing) - flagged per lesson with a suggested angle in the plan. **Set 1 (Lessons 1-4, 2 of 4 generated)** and **Set 2 (Lessons 5-8, planned only)**:

| File                                                                                                    | Lesson # | Real source(s)                                                                                                                                                                         | Status                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Listening Speaking Module 1, Lesson 1 (Advanced) - The Lost Kitchen.md`                                | 1        | Primary: PBS NewsHour feature on Erin French/The Lost Kitchen (Freedom, Maine). Secondary (Level 7 excerpt only): Radio Cherry Bombe podcast interview with Erin French.               | Current, per the Lesson prompt's fifth-addendum mapping table. No task, quote, vocabulary item, or differentiated activity was cut, only reorganized |
| `Listening Speaking Module 1, Lesson 2 (Advanced) - Living Textbooks Preserving Mid-Century Phoenix.md` | 2        | Primary: PBS NewsHour Weekend feature on Phoenix mid-century modern preservation. Secondary (Level 7 excerpt only): Modern Phoenix's Beadle Archive page on the White Gates Residence. | Current, same treatment as Lesson 1                                                                                                                    |

Both lessons above follow the current Day 1 (Unit A)/Day 2 (Unit B) architecture, and their student packets
match the current Student Print Formatting Prompt conventions (Good to Know at the top, citebox at the point of
watching, compact inline multiple-choice, real picture placeholders, word banks positioned before their items,
multi-source Task D layout for Level 7, upside-down Closing Transfer Check script) - see the Rotation Log's
Advanced Band section for the full note.

**Still open:** Set 1 remains incomplete - only 2 of its 4 lessons exist. Lessons 3-4 (Nature/conservation,
Fine-art craft-studio, per the Rotation Log's Set 1 table) still need to be generated to complete Set 1 - Set 2
(Lessons 5-8) is not relevant until Set 1 is done; generate them the same way Lessons 1-2 were generated,
whenever Advanced Band work next resumes.

**Print formatting (student version), all current:**

- Intermediate Lesson 1: `Listening Speaking Module 1, Lesson 1 (Intermediate) - Bakery Student Packet.html`.
  Two parts (Unit 1A Listening / Unit 1B Speaking), each with its own star-rated choose-your-task block merging
  that half's differentiated day content into one block per Level, a plain citation box in place of a printed
  passage, and a fillable Listening Notes comparison table.
- Intermediate Lesson 2: `Listening Speaking Module 1, Lesson 2 (Intermediate) - Porto Food Tour Student
Packet.html`. Same two-part structure; the Four-Corner Debate hook was translated into a plain "which sounds
  most like you" print activity rather than the live corner-moving version, and the Jigsaw protocol collapsed
  into three simultaneous small-group discussion prompts, per Section 1's translation rules.
- Intermediate Lesson 3: `Listening Speaking Module 1, Lesson 3 (Intermediate) - Backpack Student Packet.html`.
- Intermediate Lesson 4: `Listening Speaking Module 1, Lesson 4 (Intermediate) - Great-Grandmother Student
Packet.html`.
- Advanced Lesson 1: `Listening Speaking Module 1, Lesson 1 (Advanced) - The Lost Kitchen Student Packet.html`.
  Same structure as the Intermediate packets, plus one
  pattern the Intermediate ones don't need: Level 7's star task (Task D, both halves) compares two real sources
  directly inside the task block, using a labeled two-part excerpt layout kept within the fair-use ceiling, per
  the Print Formatting Prompt's Section 2.7 multi-source guidance.
- Advanced Lesson 2: `Listening Speaking Module 1, Lesson 2 (Advanced) - Living Textbooks Student Packet.html`.
  Same two-part structure; Task D again uses the
  multi-source compare-pair pattern (news segment vs. an archive website), introducing the second source inline
  within the task itself per the "never name an unintroduced source" rule.
  None of the six packets has been reviewed against a printed page yet.

## Generation workflow (current)

**Step 1 - Plan the module.** Run `Listening Speaking Module Lesson-Plan Generation Prompt v1.md` for the
target Module and Band. It reads the Rotation Log first, produces the module's plan table (4 rows by
default), and runs its self-check. Review and approve the plan before
generating any lesson content. Once approved, append its Rotation Log entry to `Rotation_Log.md`.

**Step 2 - Generate lessons.** Run `Listening Speaking Lesson Generation Prompt v1.md` against the approved
plan. Because each lesson now requires finding and verifying a real source (not just writing to a word-count
ceiling), generate **one lesson at a time** for this family rather than Passage Reading's two-at-a-time pacing,
at least until the sourcing step has proven reliable enough to batch. Check each lesson's self-check
(runtime/citation/task-Level checks) before moving to the next.

**Step 3 - Assess.** Once a Set (4 lessons) is complete, run `Listening Speaking Assessment Generation Prompt
v1.md` for that Set - both Part A (Listening) and Part B (Speaking) run every Set, not staggered. Part B's
mechanism depends on the Band: Beginner/Intermediate produce a scored Teams Speaking Progress recording task
(the formal assessment itself); Advanced/Proficient produce a live presentation task plus a same-task
Teams-recording alternate for standing use (e.g. an absence). See that prompt's own scope notes (Section B.0-B.1).

**Steps 4+ - not yet built.** Homework and the Part 2/presentation-project extension remain pending (see below).

## Pending work

- **Complete Advanced Module 1 Set 1** - generate Lessons 3-4 (Nature/conservation, Fine-art craft-studio, per
  the approved plan and Rotation Log); this is the only remaining gap in Set 1.
- **Generate the Advanced Set 1 assessment** - blocked on the item above; once Set 1's 4 lessons are complete,
  run the Assessment Generation Prompt against it (live-presentation mechanism, per Part B's Advanced/Proficient
  default, plus the standing Teams-recording alternate).
- **Give the Intermediate Set 1 assessment to a real class** - not yet field-tested. Once given, expect addenda
  the same way the Lesson prompt got five.
- **Homework Generation Prompt** - not started. Will need its own rules given a homework assignment can't
  hand a student the full copyrighted transcript the way Passage Reading homework reuses the anchor text.
- **A student-facing print/submission version of the Assessment Generation Prompt's output** - not started,
  mirroring what the Student Print Formatting Prompt does for lessons. Flagged as an open item in the Assessment
  prompt itself.
- **Part 2 + Presentation Project Extension** - not started. Planned to mirror the content sample's second
  (video) source, cross-source synthesis, and group-presentation assignment, as an optional add-on after a core
  lesson is complete - analogous to how the TOEFL Track Extension sits on top of a completed Passage Reading
  lesson rather than inside it.
- **v1 is lightly field-tested, not yet classroom-reviewed** - expect the same kind of refinement for the
  Assessment prompt once it's actually run against a real Set, the way the Lesson prompt needed five addenda
  after Module 1 Intermediate surfaced real gaps.
