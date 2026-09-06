# Passage Reading Index
_This is a living index, not a prompt - update it whenever a doc in the family is added, renamed, or synced to a
new lesson-prompt version, so it never falls out of date the way the individual prompts did before this project
started tracking them here. Version history lives in `Changelog.md`._

## What this document is

A single reference for everything in the Passage Reading prompt family: what each file does, whether it's in sync
with the current lesson-generation prompt, and the order to actually run them in to produce a module of lessons.
"Passage Reading" is the lesson type these prompts generate: a fixed 2-day cycle built around one shared anchor
text. A module is **4 lessons** (4 x 2-day cycles = 8 instructional days); do not plan or expect 8 lessons per
module. A second lesson type, **Novel Reading** (variable-length, multi-chapter), is planned as a sibling
`../novel-reading/` folder with its own file family, prompts, and rotation log - see `../Index.md` for the
modality-level list of lesson types. Nothing here currently supports it.

## File index

| File                                                              | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Sync status                        |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| `Generate_Lesson_Prompt_v2.7.md` | Generates one 2-day lesson: anchor text, tiered tasks, comprehension work. The current version. Section 0.10: all five Phase 3 protocols - Town Hall Role-Play, Fishbowl, Concentric Circles, Jigsaw Expert Panels, small-group discussion carousel - are valid at this program's actual class size (8-12 students), provided the lesson supplies 2-3 rotated discussion prompts (not one static prompt for the full window) and, for Fishbowl, an explicit active task for every outer-circle student (Section 0.10) - never passive listening.                                     | Current                            |
| `Generate_Module_Lesson_Plan_Prompt_v1.2.md`      | Plans one module's **4 lessons** (topics, genres, strategy rotation, vocabulary themes, task-Level-to-objective mapping) before any lesson content is generated. Reading-modality objectives only (Writing/Listening-Speaking out of scope); topics for Intermediate and up must be grounded in a real, verifiable referent, with a guardrail against fabricating quotes attributed to real named individuals. | Synced to v2.7 (v1.2)              |
| `Rotation_Log.md`                                                  | Running record of every approved module plan's genre/strategy/hook/protocol/vocabulary/topic choices, one row per lesson. Read before planning a new module; appended to after a plan is approved. Not a prompt itself. | N/A (data, not a prompt)           |
| `Changelog.md`                                                     | Version history for this prompt family. Not a prompt itself. | N/A (data, not a prompt)           |
| `Generate_Homework_Prompt_v1.md`                | Generates one homework assignment (vocabulary/idiom production + skill practice) from a single completed 2-day lesson, general track only. Does not reference Phase 3 protocol mechanics.                                                                                                                                                                                                       | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Generate_TOEFL_Extension_Prompt_v1.md`              | Generates an optional TOEFL iBT Reading task packet from a completed Advanced/Proficient lesson. Works from the shared anchor text and Phase 1 vocabulary only.                                                                                                                                                                                                                                                        | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Generate_Assessment_Prompt_v4.md`              | Builds a differentiated assessment (one section per task Level, plus study guides) from a set of completed lessons. Every item now carries a Source-lesson tag and a Tests tag citing the specific CSV objective it verifies; Section 1.1 restructured around one new passage per lesson organized into lesson-blocks, with an explicit skip-a-lesson procedure (1.1a) so a lesson's items, passage, and scoring rows can be removed as a self-contained unit. | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Generate_Student_Packet_Prompt_v1.2.md`           | Takes one completed 2-day lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML) with every teacher-facing pedagogical term translated to plain instructions. Pulls its 2-3 discussion prompts directly from a source lesson, generalizes the annotation key to every packet, documents the word-bank dashed-rule exception, and reuses the required base stylesheet in `shared/Student_Packet_Style_Guide.md`. Section 2.9's rationale for rendering Fishbowl/Concentric Circles as simultaneous groups reflects a print-medium constraint (a static page can't run a live timed rotation), not a claim that a well-scaffolded live Fishbowl is passive. Student version only; a teacher-facing formatted version is a possible future companion, not yet started. | Current (v1.2)                     |
| `learningobjectives.csv` (project file)                           | Source of truth for every Learning Objective: 192 rows across 8 Levels x 3 Modalities x 8 Modules (Describing, Narrating, Explaining, Instructing, Evaluating, Arguing, Transacting, Socializing). Every prompt above pulls from this, never from an invented difficulty curve.                                                                                                                                                                                | N/A (data)                         |
| `TOEFL Reading.pdf` (project file)                                | Reference material for the TOEFL extension prompt.                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                    |

## Module 1 progress, Intermediate Band (Describing, Intermediate) - COMPLETE

Plan approved and logged to the Rotation Log. **All 4 lessons of this module are generated** - this is
the complete module, not half of an 8-lesson plan:

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

**Print formatting (Step 6), student version:** Lesson 1's packet (`Unit 1A`/`Unit 1B: A Grandmother's Kitchen`,
`Module 1 Lesson 1 (Intermediate) - Kitchen Student Packet.html`) exists as a finished HTML file; its settled CSS
is now the base stylesheet in `shared/Student_Packet_Style_Guide.md`. Lesson 2's packet
(`Unit 2A`/`Unit 2B: New Corner of Yoyogi Park`, `Module 1 Lesson 2 (Intermediate) - Yoyogi Park Student
Packet.html`) is current against the print prompt, and its three discussion prompts match Lesson 1 and Lesson
2's own source docs. Lessons 3-4 have not been print-formatted yet.

**Phase 3 protocols (Section 0.10 compliant):** Lesson 1's Fishbowl gives the outer circle an explicit active
task (a running tally of kitchen preference plus a describing word) and rotates through three discussion
prompts. Lesson 2's Jigsaw splits three discussion questions across its mixed groups. Lesson 4's Concentric
Circles rotates through two prompts at each partner changeover and needs no outer-circle task by design (both
circles are paired and active). Word counts, task-Level mapping, vocabulary, and every other section match the
student print packets.

## Module 1 progress, Advanced Band (Describing, Advanced)

Plan approved and logged to the Rotation Log, saved as `Module 1 (Advanced) - Lesson Plan.md`. This
module needs Lessons 1-4 total, not 1-8 (the original plan's Lessons 5-8 - Aoraki Mackenzie stargazing,
Shinkansen review, Plan Vélo bike lanes, Iron Gwazi roller coaster - are out of scope and dropped, matching how
Intermediate's Lessons 5-8 were handled). Lesson 1 was generated via `Generate_Lesson_Prompt_v2.7.md` (then at
v2.5; since renamed and updated in place):

| File                                                          | Lesson # | Topic                                                                              | Status                        |
| --------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------ | ------------------------------ |
| `Module 1 Lesson 1 (Advanced) - La Sagrada Família.md`        | 1        | La Sagrada Família, Antoni Gaudí's still-unfinished basilica in Barcelona, Spain    | Generated, self-check passed  |
| `Module 1 Lesson 2 (Advanced) - The Forge at Dawn.md`         | 2        | A day inside a traditional Japanese swordsmith's forge, following the tamahagane steel-forging process | Generated against v2.7, self-check passed (18 items) |

Anchor text calibrated to Level 5 (460 words, 6 paragraphs, B2), with task Levels 4 (extension-down), 5 and 6
(native), and 7 (extension-up, requiring the second comparison text per the plan's note). Lesson 1 used Fishbowl
as its Phase 3 protocol - a fully valid choice under v2.7, but this one has not yet been checked or patched for
the outer-circle task / multi-prompt requirements; see Pending work. Lesson 2 (450 words, 6 paragraphs) was
generated directly against v2.7, so its Jigsaw Phase 3 already carries the current Section 0.10 scaffolding
(three discussion prompts split across the mixed groups). **Lessons 3-4 remain to be generated**: Lesson 3 (the vinyl record shop resurgence,
Think-Aloud Modeling, opinion-editorial, Town Hall) is next per the plan, against
`Generate_Lesson_Prompt_v2.7.md`, including its Section 0.10 scaffolding
requirements (2-3 rotated prompts for every lesson; an explicit outer-circle task where Fishbowl or Concentric
Circles is used - Lesson 4's plan calls for Concentric Circles).

No homework, TOEFL extension, or assessment work has started yet for the Advanced band.

**Print formatting (Step 6), student version:** Lesson 1's student packet (`Unit 1A`/`Unit 1B: The Basilica That
Refuses to Be Finished`, `Module 1 Lesson 1 (Advanced) - Sagrada Família Student Packet.html`) exists as an HTML
file; its CSS is the base stylesheet in `shared/Student_Packet_Style_Guide.md`. Lesson 2's student packet (`Unit 2A`/`Unit 2B: The
Forge at Dawn`, `Module 1 Lesson 2 (Advanced) - The Forge at Dawn Student Packet.html`) is current against the
print prompt. Both use the 5-mark annotation key (Advanced band and up); Lesson 1 has no byline (short-story
genre), and Lesson 2's Task D (Level 7) embeds the lesson's second comparison text - a museum-placard passage
promoting swordsmithing demonstrations - inline on the page rather than as a separate handout, per the module
plan's note for this lesson's extension-up task. Lesson 2's discussion prompts (three, split across groups) came
straight from the source lesson. Lesson 2 also carries an L4 differentiated-participation tip line under the
sentence stems, mirroring the Level 4 tracking task from the lesson's own Phase 3 section; Lesson 1's packet
does not include this for its own Level 4 stem. Lessons 3-4 have not been print-formatted yet (not yet
generated).

## Generation workflow (current)

This is the process for producing one module's worth of lessons, in order. A module is **4 lessons** (8
instructional days).

**Step 1 - Plan the module.** Run `Generate_Module_Lesson_Plan_Prompt_v1.2.md` for the
target Module and Band. It reads the Rotation Log first (for cross-module genre/strategy/vocabulary
checks against whatever module was planned immediately before it), produces the 4-lesson plan table, and runs
its self-check. Review the plan and approve it before moving on - do not generate lesson content against an
unapproved plan. Once approved, append its Rotation Log entry to `Rotation_Log.md` per that prompt's Section 0.

**Step 2 - Generate lessons two at a time.** Run `Generate_Lesson_Prompt_v2.7.md`
against the approved plan, generating two lessons per pass rather than one at a time or all four at once. Two at a
time keeps each pass small enough to actually check (word count, Section 0.2 band ceiling, and the plan's own
per-lesson variety requirements from Section 0.3's self-check) before moving on, while still letting adjacent-lesson
checks - no repeated genre or reading strategy between consecutive lessons - happen naturally within a pass, since
both lessons in a pair are visible at once.

Order within Step 2: Lessons 1-2, then 3-4.

**Step 3 - Generate homework per completed lesson.** Run `Generate_Homework_Prompt_v1.md`
against each completed lesson from Step 2, supplying both Day 1 and Day 2 in full. One homework assignment per
lesson, general track only; TOEFL-track students use Step 4 instead for the same cycle, never both. Default timing
is after Day 1, due at the start of Day 2 - if a class is a lesson or more ahead, homework can instead be generated
after Day 2 per that prompt's Section 0.2, but state which timing was used.

**Step 4 - TOEFL Track Extension.** Run `Generate_TOEFL_Extension_Prompt_v1.md` per completed
Advanced/Proficient-band lesson, as an optional add-on for TOEFL-interested students, replacing Step 3's
homework for that student on that cycle rather than adding to it.

**Step 5 - Assessment.** Run `Generate_Assessment_Prompt_v4.md` after a set of completed
lessons exists (per its own scope note, from a set of lessons, not a single one) - typically at the end of a module
(all 4 lessons), after Steps 2-4 have been run across the relevant lessons, not per lesson. Confirm scope
(cumulative vs per-lesson) and which task Level each student/group actually completed before generating; it
produces one test section and one study guide per task Level in the band, plus a Foundation Support check
where applicable. A module is 4 lessons, so the Lessons-1-4 assessment already generated for Intermediate
Module 1 is the complete end-of-module assessment - there is no separate 8-lesson pass to run.

**Step 6 - Print formatting for students.** Run `Generate_Student_Packet_Prompt_v1.2.md`
against a completed 2-day lesson from Step 2 (both days, in full) to produce a single, print-ready,
black-and-white student handout as one self-contained HTML file, reusing the required base
stylesheet in `shared/Student_Packet_Style_Guide.md` and pulling its 2-3 discussion prompts directly from the source lesson. This step is
independent of Steps 3-5 and can run any time after Step 2 completes for that lesson. Deliver as an HTML
preview first; format feedback typically comes as scoped edits to that file rather than a full regeneration. No
teacher-facing formatted version exists yet - out of scope for this prompt.

## Pending work

- **Module 1 Advanced Lesson 1's Fishbowl** - not yet checked/patched against v2.7's Section 0.10 outer-circle
  task and multi-prompt requirements. Worth doing the same pass once convenient.
- **Module 1 Advanced, Lessons 3-4** - not yet generated. Lesson 3 (vinyl record shop resurgence) is next,
  against `Generate_Lesson_Prompt_v2.7.md`, with Section 0.10 scaffolding
  (2-3 rotated prompts throughout; an explicit outer-circle task for Lesson 4's planned Concentric Circles at
  generation time - Concentric Circles needs the multi-prompt treatment but not a separate outer-circle task).
- **Module 1 Advanced Homework/TOEFL/Assessment** - not started; waits on Lessons 2-4 per Steps 3-5.
- **Print formatting for Lessons 3-4 (Intermediate) and Lessons 3-4 (Advanced)** - not started.
- **Teacher-facing formatted/print version** - not started; a possible future companion to the Step 6 prompt,
  noted but out of scope until requested.
- **Novel Reading lesson type** - not started. Will need its own lesson-generation prompt, its own Module
  Lesson-Plan-equivalent (or a shared one adapted to variable day-counts), and its own `../novel-reading/`
  folder (index, prompts, rotation log) rather than being folded into the tables above, since day-count is
  fixed for Passage Reading and variable for Novel Reading.
