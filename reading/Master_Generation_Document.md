# Passage Reading Master Generation Document
_Last updated: 2026-09-01 (second pass same day, correcting the first pass's own Fishbowl/Concentric Circles
diagnosis). Four corrections stand as of this update, in order of consequence: (1) a module is 4 lessons, not 8 -
a lesson is a 2-day cycle, and "8 days worth of lessons" was originally miscounted as "8 lessons" (16 days)
instead of "4 lessons of 2 days each" (8 days); Module 1 Intermediate's already-generated Lessons 1-4 are
therefore the COMPLETE module, not half of it, and its cumulative Lessons-1-4 assessment is already the full
end-of-module assessment, not a partial one. The Module Lesson-Plan Generation Prompt and the Program
Rotation Log are both corrected to match; (2) Fishbowl and Concentric Circles were first diagnosed (v2.6,
earlier 2026-09-01) as unworkable at this program's realistic class size (roughly 8-12 students) and replaced
with a small-group default - that diagnosis was itself corrected the same day: the actual problem was a single
static discussion prompt and a passive outer circle, not the protocols themselves. The Lesson Generation Prompt
is now **v2.7** (Section 0.10 rewritten): Fishbowl and Concentric Circles are reinstated as fully valid Phase 3
choices at 8-12 students, provided Fishbowl gives every outer-circle student an explicit active task (never
passive listening) and every protocol rotates through 2-3 discussion prompts rather than running one prompt for
the full window. The Module Lesson-Plan Generation Prompt (now **v1.2**) is realigned to match. (3) the Student
Print Formatting Prompt (v1.1) is corrected against two finished packets the user supplied (Intermediate Lesson
1 "Kitchen," Advanced Lesson 1 "Sagrada Família"): it pulls its 2-3 discussion prompts directly from a source
lesson instead of inventing them, generalizes the "Read & Mark It Up" annotation key to every packet regardless
of source reading strategy, documents the word-bank dashed-rule as an intentional exception, and gains a
required base stylesheet (Section 3.5) so future packets reproduce the same fonts/colors/spacing without
needing an existing packet as a reference; (4) Module 1 Lesson 1 (Advanced)'s raw lesson doc and the full
Module 1 Advanced module plan were both previously referenced in this file but never actually saved as project
docs, or (for the plan) never actually logged to the Program Rotation Log despite claiming otherwise - both gaps
are now closed: the Lesson 1 raw doc and the plan (trimmed to the corrected 4-lesson model, with a note on its
own inaccurate claim) are saved, and the Program Rotation Log has a proper Advanced Band entry.
Prior update 2026-08-31: Student Print Formatting Prompt v1 added, a new Step 6 producing a print-ready
black-and-white student handout from a completed lesson; tested end-to-end against Module 1 Lesson 1 Advanced.
Prior update 2026-08-30: all five prompts synced to v2.5; Module Lesson-Plan now Reading-only grounded with
a reality-grounded, band-conditioned topic rule; v2.5's genre and reading-strategy banks expanded; Module 1
Intermediate plan approved and logged, Lessons 1-4 generated, homework generated for Lessons 1-4, cumulative
assessment plus 4 study guides generated; Module 1 Advanced plan approved, Lesson 1 generated.
This is a living index, not a prompt - update it whenever a doc in the family is added, renamed, or synced to a
new lesson-prompt version, so it never falls out of date the way the individual prompts did before this project
started tracking them here._

## What this document is

A single reference for everything in the Passage Reading prompt family: what each file does, whether it's in sync
with the current lesson-generation prompt, and the order to actually run them in to produce a module of lessons.
"Passage Reading" is the lesson type these prompts generate: a fixed 2-day cycle built around one shared anchor
text. A module is **4 lessons** (4 x 2-day cycles = 8 instructional days) - see the correction note above; do
not plan or expect 8 lessons per module. A second lesson type, tentatively **Novel Reading** (variable-length,
multi-chapter), is planned separately and will get its own file family and its own section in a future version of
this document; nothing here currently supports it.

## File index

| File                                                              | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Sync status                        |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| `Passage Reading Lesson Generation Prompt v2.7 BandCalibrated.md` | Generates one 2-day lesson: anchor text, tiered tasks, comprehension work. The current version. Section 0.10 (corrected in v2.7): all five Phase 3 protocols - Town Hall Role-Play, Fishbowl, Concentric Circles, Jigsaw Expert Panels, small-group discussion carousel - are valid at this program's actual class size (8-12 students), provided the lesson supplies 2-3 rotated discussion prompts (not one static prompt for the full window) and, for Fishbowl, an explicit active task for every outer-circle student (Section 0.10) - never passive listening.                                     | Current                            |
| `Passage Reading Lesson Generation Prompt v2.6 BandCalibrated.md` | Same, intermediate Phase 3 model (small groups as the default, Fishbowl/Concentric Circles reserved for 16+ students) - this diagnosis was itself corrected the same day it was written. Superseded by v2.7.                                                                                                                                                                                                                                                | Superseded - kept for history only |
| `Passage Reading Lesson Generation Prompt v2.5 BandCalibrated.md` | Same, earlier Phase 3 model (Fishbowl/Concentric Circles as defaults, only one discussion prompt authored, no outer-circle task). Superseded by v2.6/v2.7.                                                                                                                                                                                                                                                                                                    | Superseded - kept for history only |
| `Passage Reading Lesson Generation Prompt v2.4 BandCalibrated.md` | Same, previous tier model (fixed three-tier Level A/B/C). Superseded by v2.5.                                                                                                                                                                                                                                                                                                                                                                                  | Superseded - kept for history only |
| `Passage Reading Module Lesson-Plan Generation Prompt v1.md`      | Plans one module's **4 lessons** (topics, genres, strategy rotation, vocabulary themes, task-Level-to-objective mapping) before any lesson content is generated. Now v1.2: corrected from an 8-lesson default to 4, and its Phase 3 protocol guidance realigned twice - first to v2.6's small-group default, then to v2.7's "all five protocols valid once scaffolded" model. Reading-modality objectives only (Writing/Listening-Speaking out of scope); topics for Intermediate and up must be grounded in a real, verifiable referent, with a guardrail against fabricating quotes attributed to real named individuals. | Synced to v2.7 (v1.2)              |
| `Passage Reading Program Rotation Log.md`                         | Running record of every approved module plan's genre/strategy/hook/protocol/vocabulary/topic choices, one row per lesson. Read before planning a new module; appended to after a plan is approved. Corrected 2026-09-01: Module 1 Intermediate's entry trimmed from 8 rows to 4 (rows 5-8 were planned but never generated, out of scope under the 4-lesson correction); its Fishbowl/Concentric Circles note corrected to match v2.7 (scaffold, don't replace); a Module 1 Advanced Band section added (previously missing entirely), also trimmed to 4 rows. Not a prompt itself. | N/A (data, not a prompt)           |
| `Passage Reading Homework Generation Prompt v1.md`                | Generates one homework assignment (vocabulary/idiom production + skill practice) from a single completed 2-day lesson, general track only. Does not reference Phase 3 protocol mechanics, so the v2.6/v2.7 Phase 3 changes do not require any edit here.                                                                                                                                                                                                       | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Passage Reading TOEFL Track Extension Prompt v1.md`              | Generates an optional TOEFL iBT Reading task packet from a completed Advanced/Proficient lesson. Works from the shared anchor text and Phase 1 vocabulary only, so v2.7 does not require any edit here.                                                                                                                                                                                                                                                        | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Passage Reading Assessment Generation Prompt v4.md`              | Builds a differentiated assessment (one section per task Level, plus study guides) from a set of completed lessons. Every item now carries a Source-lesson tag and a Tests tag citing the specific CSV objective it verifies; Section 1.1 restructured around one new passage per lesson organized into lesson-blocks, with an explicit skip-a-lesson procedure (1.1a) so a lesson's items, passage, and scoring rows can be removed as a self-contained unit. Task-Level grounding is unaffected by the Phase 3 changes, so no edit needed here. | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Passage Reading Student Print Formatting Prompt v1.md`           | Takes one completed 2-day lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML) with every teacher-facing pedagogical term translated to plain instructions. Now v1.2: pulls its 2-3 discussion prompts directly from a source lesson, generalizes the annotation key to every packet, documents the word-bank dashed-rule exception, embeds a required base stylesheet (Section 3.5) drawn from the settled Kitchen/Sagrada Família packets, and (v1.2) rewords Section 2.9's rationale for rendering Fishbowl/Concentric Circles as simultaneous groups - it's a print-medium constraint (a static page can't run a live timed rotation), not a claim that a well-scaffolded live Fishbowl is passive; no output changed, only the stated reason. Student version only; a teacher-facing formatted version is a possible future companion, not yet started. | Current (v1.2)                     |
| `learningobjectives.csv` (project file)                           | Source of truth for every Learning Objective: 192 rows across 8 Levels x 3 Modalities x 8 Modules (Describing, Narrating, Explaining, Instructing, Evaluating, Arguing, Transacting, Socializing). Every prompt above pulls from this, never from an invented difficulty curve.                                                                                                                                                                                | N/A (data)                         |
| `TOEFL Reading.pdf` (project file)                                | Reference material for the TOEFL extension prompt.                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                    |

## Module 1 progress, Intermediate Band (Describing, Intermediate) - COMPLETE

Plan approved and logged to the Program Rotation Log on 2026-08-30 (originally 8 rows; corrected to 4 on
2026-09-01 - see the top-of-document correction note). Under the corrected 4-lesson-per-module model, **all 4
lessons of this module are generated** - this is the complete module, not half of an 8-lesson plan:

| File                                               | Lesson # | Topic                                                                         | Status                       |
| -------------------------------------------------- | -------- | ------------------------------------------------------------------------------ | ----------------------------- |
| `Module 1 Lesson 1 - A Grandmother's Kitchen.md`   | 1        | A traditional wood-fired kitchen in a trullo home in Puglia, southern Italy   | Generated, self-check passed |
| `Module 1 Lesson 2 - New Corner of Yoyogi Park.md` | 2        | A newly renovated section of Yoyogi Park in Tokyo                             | Generated, self-check passed |
| `Module 1 Lesson 3 - Choosing Running Shoes.md`    | 3        | What podiatrists and running-shop staff recommend when choosing running shoes | Generated, self-check passed |
| `Module 1 Lesson 4 - Painting Wynwood Walls.md`    | 4        | A street artist describes painting a mural in Wynwood Walls, Miami            | Generated, self-check passed |

**Homework (Step 3), general track, one per lesson, all 4 complete:**

| File                                              | For lesson | Status                                           |
| -------------------------------------------------- | ---------- | ------------------------------------------------- |
| `Module 1 Homework - Lesson 1 (Kitchen).md`       | Lesson 1   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 2 (Park).md`          | Lesson 2   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 3 (Running Shoes).md` | Lesson 3   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 4 (Mural).md`         | Lesson 4   | Generated, self-check passed, after-Day-1 timing |

**Assessment (Step 5), covering all 4 lessons (Task Levels 2/3/4/5) - this is the full end-of-module assessment,
not a partial cumulative one:**

| File                                                         | Covers                         | Status                       |
| --------------------------------------------------------------- | ------------------------------- | ----------------------------- |
| `Module 1 Assessment - Lessons 1-4 (Intermediate).md`        | Lessons 1-4, all 4 Task Levels | Generated, self-check passed |
| `Module 1 Assessment Study Guide - Level 2 (Lessons 1-4).md` | Task Level 2                   | Generated                    |
| `Module 1 Assessment Study Guide - Level 3 (Lessons 1-4).md` | Task Level 3                   | Generated                    |
| `Module 1 Assessment Study Guide - Level 4 (Lessons 1-4).md` | Task Level 4                   | Generated                    |
| `Module 1 Assessment Study Guide - Level 5 (Lessons 1-4).md` | Task Level 5                   | Generated                    |

Each Task Level's items are tagged with their source lesson and the specific `learningobjectives.csv` row they
test; the four reading passages (one per lesson) are printed once, shared, in the test's own Reading Passages
section, with a note to distribute that section alongside any single task-Level section.

**Print formatting (Step 6), student version:** Lesson 1's packet (`Unit 1A`/`Unit 1B: A Grandmother's Kitchen`)
exists as a finished HTML file; its settled CSS is now the base stylesheet embedded in the Student Print
Formatting Prompt (Section 3.5). Saved as a project doc 2026-09-01 (`Module 1 Lesson 1 (Intermediate) -
Kitchen Student Packet.html`). Lesson 2's packet (`Unit 2A`/`Unit 2B: New Corner of Yoyogi Park`) generated
2026-09-01 against the print prompt's current version (v1.2), saved as `Module 1 Lesson 2 (Intermediate) -
Yoyogi Park Student Packet.html`; it originally added two extra discussion-prompt angles per Section 2.9's
pre-v2.6 fallback, and those same three prompts are now also in Lesson 1 and Lesson 2's own source docs (see
the Phase 3 patch note above), so the packets and the source lessons agree. Lessons 3-4 have not been
print-formatted yet.

**Phase 3 protocols - patched to v2.7, 2026-09-01:** Lessons 1 (Fishbowl), 2 (Jigsaw), and 4 (Concentric
Circles) were all checked against the current Lesson Generation Prompt (v2.7, Section 0.10). Lessons 1 and 2
were patched in place: Lesson 1's Fishbowl now gives the outer circle an explicit active task (a running tally of
kitchen preference plus a describing word) and rotates through three discussion prompts instead of one; Lesson
2's Jigsaw now splits three discussion questions across its mixed groups instead of every group answering the
same one. Lesson 4 needed no change - it already rotated through two prompts at each partner changeover, and
Concentric Circles needs no outer-circle task under Section 0.10 (both circles are paired and active by design).
Only Phase 3 changed in Lessons 1 and 2; word counts, task-Level mapping, vocabulary, and every other section
are unaffected, and the patches match what the student print packets already showed (Lessons 1 and 2's print
packets had already added the extra prompts via the print prompt's own pre-v2.6 fallback rule).

## Module 1 progress, Advanced Band (Describing, Advanced)

Plan approved 2026-08-30, recovered and properly logged 2026-09-01 - saved as `Module 1 (Advanced) - Lesson
Plan.md`. (The plan text as originally drafted claimed it had already been logged to the Program Rotation Log;
it had not been - that gap, and the plan doc's own absence from the project, are both now closed.) Under the
corrected 4-lesson model, this module needs Lessons 1-4 total, not 1-8 (the original plan's Lessons 5-8 -
Aoraki Mackenzie stargazing, Shinkansen review, Plan Vélo bike lanes, Iron Gwazi roller coaster - are out of
scope and dropped, matching how Intermediate's Lessons 5-8 were handled). Lesson 1 was generated via
`Passage Reading Lesson Generation Prompt v2.5 BandCalibrated.md` (pre-dates both the v2.6 and v2.7 Phase 3
corrections):

| File                                                          | Lesson # | Topic                                                                              | Status                        |
| --------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------ | ------------------------------ |
| `Module 1 Lesson 1 (Advanced) - La Sagrada Família.md`        | 1        | La Sagrada Família, Antoni Gaudí's still-unfinished basilica in Barcelona, Spain    | Generated, self-check passed, saved as a project doc 2026-09-01  |
| `Module 1 Lesson 2 (Advanced) - The Forge at Dawn.md`         | 2        | A day inside a traditional Japanese swordsmith's forge, following the tamahagane steel-forging process | Generated 2026-09-01 against v2.7, self-check passed (18 items) |

Anchor text calibrated to Level 5 (460 words, 6 paragraphs, B2), with task Levels 4 (extension-down), 5 and 6
(native), and 7 (extension-up, requiring the second comparison text per the plan's note). Lesson 1 used Fishbowl
as its Phase 3 protocol - a fully valid choice under v2.7, but (unlike Intermediate Lessons 1 and 2, patched
2026-09-01) this one has not yet been checked or patched for the outer-circle task / multi-prompt requirements;
see Pending work. Lesson 2 (450 words, 6 paragraphs) was generated directly against v2.7, so its Jigsaw Phase 3
already carries the current Section 0.10 scaffolding (three discussion prompts split across the mixed groups) -
no later patch needed. **Lessons 3-4 remain to be generated**: Lesson 3 (the vinyl record shop resurgence,
Think-Aloud Modeling, opinion-editorial, Town Hall) is next per the plan, against
`Passage Reading Lesson Generation Prompt v2.7 BandCalibrated.md`, including its Section 0.10 scaffolding
requirements (2-3 rotated prompts for every lesson; an explicit outer-circle task where Fishbowl or Concentric
Circles is used - Lesson 4's plan calls for Concentric Circles).

No homework, TOEFL extension, or assessment work has started yet for the Advanced band.

**Print formatting (Step 6), student version:** Lesson 1's student packet (`Unit 1A`/`Unit 1B: The Basilica That
Refuses to Be Finished`) was used as the live test case for `Passage Reading Student Print Formatting Prompt`
while it was being worked out - the packet went through many rounds of direct formatting iteration before the
prompt itself was written up from the settled result, and its CSS is now the v1.1 base stylesheet (Section 3.5).
The packet exists as an HTML file, saved as a project doc 2026-09-01 (`Module 1 Lesson 1 (Advanced) - Sagrada
Família Student Packet.html`). Lesson 2's student packet (`Unit 2A`/`Unit 2B: The Forge at Dawn`) generated
2026-09-01 against the print prompt's current version (v1.2), saved as `Module 1 Lesson 2 (Advanced) - The
Forge at Dawn Student Packet.html`. Uses the 5-mark annotation key (Advanced band and up), no byline
(short-story genre, unlike Sagrada Família's magazine-article byline), and includes a Task D (Level 7) that
embeds the lesson's second comparison text - a museum-placard passage promoting swordsmithing demonstrations
- inline on the page rather than as a separate handout, per the module plan's note for this lesson's
extension-up task. Its discussion prompts (three, split across groups) came straight from the source lesson
with no fallback authoring needed, since Lesson 2 was generated fresh under v2.7. Also carries an L4
differentiated-participation tip line under the sentence stems, mirroring the Level 4 tracking task from the
lesson's own Phase 3 section - content Sagrada Família's packet had not included for its own Level 4 stem,
which this packet does not retroactively change. Lessons 3-4 have not been print-formatted yet (not yet
generated).

## Generation workflow (current)

This is the process for producing one module's worth of lessons, in order. A module is **4 lessons** (8
instructional days).

**Step 1 - Plan the module.** Run `Passage Reading Module Lesson-Plan Generation Prompt v1.md` (v1.2) for the
target Module and Band. It reads the Program Rotation Log first (for cross-module genre/strategy/vocabulary
checks against whatever module was planned immediately before it), produces the 4-lesson plan table, and runs
its self-check. Review the plan and approve it before moving on - do not generate lesson content against an
unapproved plan. Once approved, append its Program Rotation Log entry to `Passage Reading Program Rotation
Log.md` per that prompt's Section 0.

**Step 2 - Generate lessons two at a time.** Run `Passage Reading Lesson Generation Prompt v2.7 BandCalibrated.md`
against the approved plan, generating two lessons per pass rather than one at a time or all four at once. Two at a
time keeps each pass small enough to actually check (word count, Section 0.2 band ceiling, and the plan's own
per-lesson variety requirements from Section 0.3's self-check) before moving on, while still letting adjacent-lesson
checks - no repeated genre or reading strategy between consecutive lessons - happen naturally within a pass, since
both lessons in a pair are visible at once.

Order within Step 2: Lessons 1-2, then 3-4.

**Step 3 - Generate homework per completed lesson.** Run `Passage Reading Homework Generation Prompt v1.md`
against each completed lesson from Step 2, supplying both Day 1 and Day 2 in full. One homework assignment per
lesson, general track only; TOEFL-track students use Step 4 instead for the same cycle, never both. Default timing
is after Day 1, due at the start of Day 2 - if a class is a lesson or more ahead, homework can instead be generated
after Day 2 per that prompt's Section 0.2, but state which timing was used.

**Step 4 - TOEFL Track Extension.** Run `Passage Reading TOEFL Track Extension Prompt v1.md` per completed
Advanced/Proficient-band lesson, as an optional add-on for TOEFL-interested students, replacing Step 3's
homework for that student on that cycle rather than adding to it.

**Step 5 - Assessment.** Run `Passage Reading Assessment Generation Prompt v4.md` after a set of completed
lessons exists (per its own scope note, from a set of lessons, not a single one) - typically at the end of a module
(all 4 lessons), after Steps 2-4 have been run across the relevant lessons, not per lesson. Confirm scope
(cumulative vs per-lesson) and which task Level each student/group actually completed before generating; it
produces one test section and one study guide per task Level in the band, plus a Foundation Support check
where applicable. With a module now defined as 4 lessons, the Lessons-1-4 assessment already generated for
Intermediate Module 1 is the complete end-of-module assessment - there is no separate "all 8 lessons" pass to
run.

**Step 6 - Print formatting for students.** Run `Passage Reading Student Print Formatting Prompt v1.md` (v1.2)
against a completed 2-day lesson from Step 2 (both days, in full) to produce a single, print-ready,
black-and-white student handout as one self-contained HTML file, reusing the prompt's required base
stylesheet (Section 3.5) and pulling its 2-3 discussion prompts directly from the source lesson. This step is
independent of Steps 3-5 and can run any time after Step 2 completes for that lesson. Deliver as an HTML
preview first; format feedback typically comes as scoped edits to that file rather than a full regeneration. No
teacher-facing formatted version exists yet - out of scope for this prompt.

## Pending work

- **Module 1 Advanced Lesson 1's Fishbowl** - not yet checked/patched against v2.7's Section 0.10 outer-circle
  task and multi-prompt requirements, the same class of gap already fixed in Intermediate Lessons 1 and 2 on
  2026-09-01. Worth doing the same pass once convenient.
- **Module 1 Advanced, Lessons 3-4** - not yet generated. Lesson 3 (vinyl record shop resurgence) is next,
  against `Passage Reading Lesson Generation Prompt v2.7 BandCalibrated.md`, with Section 0.10 scaffolding
  (2-3 rotated prompts throughout; an explicit outer-circle task for Lesson 4's planned Concentric Circles at
  generation time - Concentric Circles needs the multi-prompt treatment but not a separate outer-circle task).
- **Module 1 Advanced Homework/TOEFL/Assessment** - not started; waits on Lessons 2-4 per Steps 3-5.
- **Print formatting for Lessons 3-4 (Intermediate) and Lessons 3-4 (Advanced)** - not started; Step 6 has now
  been run against Intermediate Lessons 1-2 and Advanced Lessons 1-2.
- **Teacher-facing formatted/print version** - not started; a possible future companion to the Step 6 prompt,
  noted but out of scope until requested.
- **Novel Reading lesson type** - not started. Will need its own lesson-generation prompt, its own Module
  Lesson-Plan-equivalent (or a shared one adapted to variable day-counts), and likely its own section in this
  document rather than being folded into the tables above, since day-count is fixed for Passage Reading and
  variable for Novel Reading.
