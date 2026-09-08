# Passage Reading Index
_This is a living index, not a prompt - update it whenever a doc in the family is added, renamed, or synced to a
new lesson-prompt version, so it never falls out of date the way the individual prompts did before this project
started tracking them here. Version history lives in `Changelog.md`._

## What this document is

A single reference for everything in the Passage Reading prompt family: what each file does, whether it's in sync
with the current lesson-generation prompt, and the order to actually run them in to produce a Set of lessons.
"Passage Reading" is the lesson type these prompts generate: a fixed 2-day cycle built around one shared anchor
text. See `shared/Program_Conventions.md` §C for what a Set is; today that's **4 lessons** (4 x 2-day cycles),
since a Passage Reading lesson is a 2-day cycle - do not plan or expect 8 lessons per Set. Since Set size and
module size are numerically identical today, every Module/Band planned so far is that Module/Band's Set 1 - see
"Module 1 progress" below. A second lesson type, **Novel Reading**
(variable-length, multi-chapter), is planned as a sibling `../novel-reading/` folder with its own file family,
prompts, and rotation log - see `../Index.md` for the modality-level list of lesson types. Nothing here
currently supports it.

## File index

| File                                                              | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Sync status                        |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| `Generate_Lesson_Prompt_v2.8.md` | Generates one 2-day lesson: anchor text, tiered tasks, comprehension work. The current version. Section 0.10: all five Phase 3 protocols - Town Hall Role-Play, Fishbowl, Concentric Circles, Jigsaw Expert Panels, small-group discussion carousel - are valid at this program's actual class size (8-12 students), provided the lesson supplies 2-3 rotated discussion prompts (not one static prompt for the full window) and, for Fishbowl, an explicit active task for every outer-circle student (Section 0.10) - never passive listening. v2.8 adds a required `**Version:**` field (`shared/Program_Conventions.md` §G) to the opening metadata line.                                     | Current                            |
| `Generate_Module_Lesson_Plan_Prompt_v1.3.md`      | Plans **one Set** (4 lessons by default: topics, genres, strategy rotation, vocabulary themes, task-Level-to-objective mapping) before any lesson content is generated. A Module/Band can hold more than one Set over time; lesson numbering is global across Sets. Reading-modality objectives only (Writing/Listening-Speaking out of scope); topics for Intermediate and up must be grounded in a real, verifiable referent, with a guardrail against fabricating quotes attributed to real named individuals. | Synced to v2.7 (v1.3)              |
| `Rotation_Log.md`                                                  | Overview only as of the per-Band split: purpose, notes that apply across every Band (the miscount correction, the Sets-concept introduction), and links to each Band's own log. | N/A (data, not a prompt)           |
| `Rotation_Log_Intermediate.md`                                     | Running record of every approved Intermediate-Band Set's genre/strategy/hook/protocol/vocabulary/topic choices, one row per lesson, nested by Set. Read before planning a new Set; appended to after a plan is approved. | N/A (data, not a prompt)           |
| `Rotation_Log_Advanced.md`                                         | Same, for the Advanced Band. A new Band's file is created lazily the first time a lesson in that Band is generated. | N/A (data, not a prompt)           |
| `Changelog.md`                                                     | Version history for this prompt family. Not a prompt itself. | N/A (data, not a prompt)           |
| `Generate_Homework_Prompt_v1.md`                | Generates one homework assignment (vocabulary/idiom production + skill practice) from a single completed 2-day lesson, general track only. Does not reference Phase 3 protocol mechanics.                                                                                                                                                                                                       | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Generate_TOEFL_Extension_Prompt_v1.md`              | Generates an optional TOEFL iBT Reading task packet from a completed Advanced/Proficient lesson. Works from the shared anchor text and Phase 1 vocabulary only.                                                                                                                                                                                                                                                        | Synced to v2.5 (v2.7-compatible, unchanged) |
| `Generate_Assessment_Prompt_v4.2.md`              | Builds a differentiated assessment (one section per task Level, plus study guides) from a completed Set of lessons (or an explicitly-scoped checkpoint/multi-Set span). Every item now carries a Source-lesson tag and a Tests tag citing the specific CSV objective it verifies; Section 1.1 restructured around one new passage per lesson organized into lesson-blocks, with an explicit skip-a-lesson procedure (1.1a) so a lesson's items, passage, and scoring rows can be removed as a self-contained unit. Takes a Set number as input and, for a full-Set assessment, saves alongside that Set's lesson folders as `Set{N}_{Band}_Assessment.md`. v4.2 updates its two `lessons/<band>/Set_<N>/` path mentions to `lessons/<band>/Module_<N>/Set_<N>/`, matching the new Module-level folder (`shared/Program_Conventions.md` §D). | Synced to v2.7 (v4.2)              |
| `Generate_Student_Packet_Prompt_v1.9.md`           | Takes one completed 2-day lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML) with every teacher-facing pedagogical term translated to plain instructions. Pulls its 2-3 discussion prompts directly from a source lesson, generalizes the annotation key to every packet, documents the word-bank dashed-rule exception, and reuses the required base stylesheet in `shared/Student_Packet_Style_Guide.md`. Section 2.9's rationale for rendering Fishbowl/Concentric Circles as simultaneous groups reflects a print-medium constraint (a static page can't run a live timed rotation), not a claim that a well-scaffolded live Fishbowl is passive. As of v1.6, a lesson with 2 or more idioms to gloss (no single spotlight idiom) renders "Idioms to Know" as a numbered table (`.idiom-list`/`.irow`), mirroring "Words to Know"'s `.vocab-list` treatment, instead of stacked plain paragraphs. As of v1.7, the opening masthead carries a top-right `.masthead-meta` stack of two tags - "Reading," then Band and version code combined as one string - per `shared/Student_Packet_Style_Guide.md` §B (corrected from a same-day three-line version). As of v1.8, §2.13's `.ans-line-sm` line begins on its own line below its question rather than packing inline (fixed at the shared CSS layer, `shared/Student_Packet_Style_Guide.md` v1.7), and §2.12 requires a word bank sit before the question/sentence frame it supplies words for. As of v1.9, §2.13's `.ans-line-sm` is full-width like `.ans-line` (its `max-width: 320px` cap dropped at the shared CSS layer, `shared/Student_Packet_Style_Guide.md` v1.8), distinguished from `.ans-line` only by its shorter height. Student version only; a teacher-facing formatted version is a possible future companion, not yet started. | Current (v1.9); every packet across all three modalities that embeds `.ans-line-sm` was hand-corrected for the v1.9 width fix in the same pass (see `shared/Changelog.md`), not just this modality's. Existing packets under `lessons/` predate the `.masthead-meta` stack and don't have it yet. `SagradaFamilia_Advanced_L1` and `ForgeAtDawn_Advanced_L2` also predate the v1.6 idiom-table rule and still show their 2-idiom lists as plain paragraphs; not yet swept |
| `Generate_Assessment_Student_Packet_Prompt_v1.md`  | New (2026-09-08). Takes one completed Assessment `.md` and produces a single, print-ready, black-and-white student handout: four self-contained Task-Level sections (each with `page-break-before: always` for selective printing), source-lesson/Tests tags and the entire Scoring Guide (point values, rubrics) stripped, a per-Level plain objective statement translated from the CSV grounding quote, and no self-check-checklist substitute for rubric-scored items (they print as plain answer-line questions, matching how the Student Print Formatting Prompt already treats extended-response items). No Reading-specific delta CSS - reuses the base stylesheet and classes the lesson packet prompt already established. Mirrors Listening/Speaking's `Generate_Assessment_Student_Packet_Prompt_v1.md` and Writing's `Generate_Assessment_Student_Packet_Prompt_v2.md`, closing the gap noted in Pending work below. | Current (v1); first run produced `Module_1/Set_1/Set1_Intermediate_Assessment_Packet.html` the same session |
| `learningobjectives.csv` (project file)                           | Source of truth for every Learning Objective: 192 rows across 8 Levels x 3 Modalities x 8 Modules (Describing, Narrating, Explaining, Instructing, Evaluating, Arguing, Transacting, Socializing). Every prompt above pulls from this, never from an invented difficulty curve.                                                                                                                                                                                | N/A (data)                         |
| `TOEFL Reading.pdf` (project file)                                | Reference material for the TOEFL extension prompt.                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                    |

## Module 1 progress, Intermediate Band (Describing, Intermediate) - Set 1 COMPLETE

Plan approved and logged to the Rotation Log as Set 1. **All 4 lessons of this Set are generated** - this is
the complete Set, not half of an 8-lesson plan:

| File                                                                      | Lesson # | Topic                                                                         | Status                       |
| -------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------ | ----------------------------- |
| `Module_1/Set_1/Lesson_1_Kitchen/Lesson1_Kitchen.md`               | 1        | A traditional wood-fired kitchen in a trullo home in Puglia, southern Italy   | Generated, self-check passed |
| `Module_1/Set_1/Lesson_2_YoyogiPark/Lesson2_YoyogiPark.md`         | 2        | A newly renovated section of Yoyogi Park in Tokyo                             | Generated, self-check passed |
| `Module_1/Set_1/Lesson_3_RunningShoes/Lesson3_RunningShoes.md`     | 3        | What podiatrists and running-shop staff recommend when choosing running shoes | Generated, self-check passed |
| `Module_1/Set_1/Lesson_4_WynwoodWalls/Lesson4_WynwoodWalls.md`     | 4        | A street artist describes painting a mural in Wynwood Walls, Miami            | Generated, self-check passed |

**Homework (Step 3), general track, one per lesson, all 4 complete:**

| File                                              | For lesson | Status                                           |
| -------------------------------------------------- | ---------- | ------------------------------------------------- |
| `Module 1 Homework - Lesson 1 (Kitchen).md`       | Lesson 1   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 2 (Park).md`          | Lesson 2   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 3 (Running Shoes).md` | Lesson 3   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 4 (Mural).md`         | Lesson 4   | Generated, self-check passed, after-Day-1 timing |

**Assessment (Step 5), covering all 4 lessons (Task Levels 2/3/4/5) - this is the full end-of-Set assessment,
not a partial cumulative one. Generated 2026-09-08 against `Generate_Assessment_Prompt_v4.1.md` - the first
real run of this prompt (the file names previously listed here, `Module 1 Assessment - Lessons 1-4
(Intermediate).md` plus 4 like-named study guides, never actually existed on disk; that was stale/aspirational
documentation left over from before the Set-folder migration, corrected here):**

| File                                                | Covers                         | Status                                             |
| ---------------------------------------------------- | ------------------------------- | ----------------------------------------------------- |
| `Module_1/Set_1/Set1_Intermediate_Assessment.md`             | Lessons 1-4, all 4 Task Levels | Generated, not yet given to a real class |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level2.md`      | Task Level 2                   | Generated                                          |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level3.md`      | Task Level 3                   | Generated                                          |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level4.md`      | Task Level 4                   | Generated                                          |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level5.md`      | Task Level 5                   | Generated                                          |

Every item is tagged with its source lesson and a Tests citation of the specific `learningobjectives.csv` row
it verifies, per Section 0.3. Unlike the stale table this replaces, passages are not shared/printed once - each
Task Level section is self-contained (per Section 2.1: "a visual banner or heading per section is recommended
for quick sorting when printing/distributing selectively"), so all four lesson passages are reprinted inside
each of the 4 Task-Level sections. No Foundation Support Check section - no lesson in this Set flagged a
Foundation Support student.

**Student-facing HTML packet: `Module_1/Set_1/Set1_Intermediate_Assessment_Packet.html`, generated 2026-09-08** against
the new `Generate_Assessment_Student_Packet_Prompt_v1.md` (first run of this prompt for Reading - see Pending
work, now resolved). One combined document, four Task-Level sections (★ through ★★★★), each with
`page-break-before: always` so a teacher can print one Level's pages alone; all four lesson passages reprinted
in full inside every Task-Level section, matching the source `.md`'s own self-contained-per-Level shape. Every
source-lesson/Tests tag, the item-count/scope metadata, and the entire Scoring Guide (point tables and all three
rubrics) are stripped; rubric-scored items (Level 4's comparison-and-reason items, Level 5's extended-reasoning
and cross-text synthesis items) print as plain numbered questions with answer lines sized to the expected
answer, with no self-check-checklist substitute - matching how the lesson packet already treats extended-response
items, rather than Listening/Speaking's Speaking-Task-card checklist treatment.

**Print formatting (Step 6), student version:** Lesson 1's packet (`Unit 1A`/`Unit 1B: A Grandmother's Kitchen`,
`Module_1/Set_1/Lesson_1_Kitchen/Kitchen_Intermediate_L1_Packet.html`) exists as a finished HTML file; its settled CSS
is now the base stylesheet in `shared/Student_Packet_Style_Guide.md`. Lesson 2's packet
(`Unit 2A`/`Unit 2B: New Corner of Yoyogi Park`,
`Module_1/Set_1/Lesson_2_YoyogiPark/YoyogiPark_Intermediate_L2_Packet.html`) is current against the print prompt, and its
three discussion prompts match Lesson 1 and Lesson 2's own source docs. Lesson 3's packet
(`Unit 3A`/`Unit 3B: How to Choose Running Shoes That Feel Comfortable`,
`Module_1/Set_1/Lesson_3_RunningShoes/RunningShoes_Intermediate_L3_Packet.html`) is the first packet generated
against v1.7, so it's also the first to carry the `.masthead-meta` tag stack (`Reading` /
`Intermediate S1.3.0`) on its opening masthead. Its source lesson's Town Hall section supplies only
one discussion prompt (pre-2.9-fallback case), so two additional prompts exploring different angles
of the same question were authored for the packet per Section 2.9's fallback; a Focus on the
Objective worked-model box was also added between Units 3A/3B per Section 2.7, since Day 1's tasks
don't yet test the comparison-plus-reason objective against the anchor text. Lesson 4's packet
(`Unit 4A`/`Unit 4B: Painting Wynwood Walls`,
`Module_1/Set_1/Lesson_4_WynwoodWalls/WynwoodWalls_Intermediate_L4_Packet.html`) is also current against
v1.7, carrying the `.masthead-meta` tag stack (`Reading` / `Intermediate S1.4.0`) on its opening
masthead. Its source lesson already supplies 2 discussion prompts (generated against v2.7), pulled
directly per Section 2.9 with no fallback needed; a Focus on the Objective worked-model box was
added between Units 4A/4B per Section 2.7, since Day 1's comprehension questions test the
comparison-plus-reason objective but don't yet model it worked-example style before Day 2's
independent tasks. Its annotation key carries the `!` mark, since its Level 5 (extension-up) task
asks students to identify an evaluative word choice - the first Intermediate-band packet to include
it, since Section 2.10's evaluative-language trigger is met here even though it's typically an
Advanced-and-up case.

**Phase 3 protocols (Section 0.10 compliant):** Lesson 1's Fishbowl gives the outer circle an explicit active
task (a running tally of kitchen preference plus a describing word) and rotates through three discussion
prompts. Lesson 2's Jigsaw splits three discussion questions across its mixed groups. Lesson 4's Concentric
Circles rotates through two prompts at each partner changeover and needs no outer-circle task by design (both
circles are paired and active). Word counts, task-Level mapping, vocabulary, and every other section match the
student print packets.

## Module 1 progress, Advanced Band (Describing, Advanced) - Set 1 COMPLETE

Plan approved and logged to the Rotation Log as Set 1, saved as `Module_1/Module1_Advanced_Lesson_Plan.md`. This
Set needs Lessons 1-4 total, not 1-8 (the original plan's Lessons 5-8 - Aoraki Mackenzie stargazing,
Shinkansen review, Plan Vélo bike lanes, Iron Gwazi roller coaster - are out of scope and dropped, matching how
Intermediate's Lessons 5-8 were handled). Lesson 1 was generated via `Generate_Lesson_Prompt_v2.7.md` (then at
v2.5; since renamed and updated in place). **All 4 lessons of this Set are generated:**

| File                                                                 | Lesson # | Topic                                                                              | Status                        |
| ---------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------ | ------------------------------ |
| `Module_1/Set_1/Lesson_1_SagradaFamilia/Lesson1_SagradaFamilia.md`           | 1        | La Sagrada Família, Antoni Gaudí's still-unfinished basilica in Barcelona, Spain    | Generated, self-check passed  |
| `Module_1/Set_1/Lesson_2_ForgeAtDawn/Lesson2_ForgeAtDawn.md`                 | 2        | A day inside a traditional Japanese swordsmith's forge, following the tamahagane steel-forging process | Generated against v2.7, self-check passed (18 items) |
| `Module_1/Set_1/Lesson_3_VinylComeback/Lesson3_VinylComeback.md`             | 3        | The real-world resurgence of independent vinyl record shops                       | Generated against v2.8, self-check passed (18 items) |
| `Module_1/Set_1/Lesson_4_PortlandHeadLight/Lesson4_PortlandHeadLight.md`     | 4        | A keeper's account of Portland Head Light, Maine                                  | Generated against v2.8, self-check passed (18 items) |

Anchor text calibrated to Level 5 (460 words, 6 paragraphs, B2), with task Levels 4 (extension-down), 5 and 6
(native), and 7 (extension-up, requiring the second comparison text per the plan's note). Lesson 1 used Fishbowl
as its Phase 3 protocol - a fully valid choice under v2.7, but this one has not yet been checked or patched for
the outer-circle task / multi-prompt requirements; see Pending work. Lesson 2 (450 words, 6 paragraphs) was
generated directly against v2.7, so its Jigsaw Phase 3 already carries the current Section 0.10 scaffolding
(three discussion prompts split across the mixed groups). Lesson 3 (434 words, 6 paragraphs) was generated
against the current `Generate_Lesson_Prompt_v2.8.md`, carrying the required `**Version:** S1.3.0` header field
(new as of v2.8/§G; Lessons 1-2 predate this and stay unversioned by design); its Town Hall Phase 3 rotates
through three discussion prompts across discussion tables and needs no outer-circle task under Section 0.10.
Its two board-dependent moments sit in Day 1 Phase 1 (Mystery Quote guess-and-check) and Day 2 Phase 3 (Town
Hall report-back), rotating the required slot away from Lesson 2's Phase 1 + Phase 2 pairing. Lesson 4 (454
words of dialogue, 6 turn-blocks) was generated against `Generate_Lesson_Prompt_v2.8.md`, carrying `**Version:**
S1.4.0`; it is formatted as a Reader's Theater interview script (Interviewer/Keeper speaker roles, stage
directions, rehearsal cues) rather than continuous prose, the first lesson in this Set to use a script-style
genre. Its Concentric Circles Phase 3 rotates through three discussion prompts at each partner changeover and
needs no outer-circle task under Section 0.10 (both circles are paired and active by design). Its two
board-dependent moments sit in Day 1 Phase 1 (Four-Corner Debate tally-and-check) and Day 2 Phase 2 (a live
Then/Now T-chart built from group report-backs), rotating the required slot away from Lesson 3's Phase 1 + Phase
3 pairing.

No homework, TOEFL extension, or assessment work has started yet for the Advanced band.

**Print formatting (Step 6), student version:** Lesson 1's student packet (`Unit 1A`/`Unit 1B: The Basilica That
Refuses to Be Finished`, `Module_1/Set_1/Lesson_1_SagradaFamilia/SagradaFamilia_Advanced_L1_Packet.html`) exists as an HTML
file; its CSS is the base stylesheet in `shared/Student_Packet_Style_Guide.md`. Lesson 2's student packet (`Unit 2A`/`Unit 2B: The
Forge at Dawn`, `Module_1/Set_1/Lesson_2_ForgeAtDawn/ForgeAtDawn_Advanced_L2_Packet.html`) is current against the
print prompt. Both use the 5-mark annotation key (Advanced band and up); Lesson 1 has no byline (short-story
genre), and Lesson 2's Task D (Level 7) embeds the lesson's second comparison text - a museum-placard passage
promoting swordsmithing demonstrations - inline on the page rather than as a separate handout, per the module
plan's note for this lesson's extension-up task. Lesson 2's discussion prompts (three, split across groups) came
straight from the source lesson. Lesson 2 also carries an L4 differentiated-participation tip line under the
sentence stems, mirroring the Level 4 tracking task from the lesson's own Phase 3 section; Lesson 1's packet
does not include this for its own Level 4 stem. Lesson 3's student packet (`Unit 3A`/`Unit 3B: The Vinyl Comeback
Is Real`, `Module_1/Set_1/Lesson_3_VinylComeback/VinylComeback_Advanced_L3_Packet.html`) is the first Advanced packet
generated against v1.7, so it's the first to carry the masthead `.masthead-meta` two-tag stack ("Reading",
"Advanced S1.3.0") on its opening masthead; Lessons 1-2 predate that element and don't have it yet (see Pending
work). It also uses the newer `.idiom-list`/`.irow` table treatment for its two idioms (per v1.6) rather than
Lesson 2's older stacked-paragraph idiom format, and embeds Task D's second comparison text (an industry-report
pitch for vinyl-pressing investment) inline, with an L4 differentiated-participation tip line under the sentence
stems matching its own Phase 3 tracking task. Lesson 4's student packet (`Unit 4A`/`Unit 4B: Keeping the Light`,
`Module_1/Set_1/Lesson_4_PortlandHeadLight/PortlandHeadLight_Advanced_L4_Packet.html`) carries the `.masthead-meta` tag
stack ("Reading", "Advanced S1.4.0") and the 5-mark annotation key. Its Reader's Theater script format is
translated into plain speaker labels (`.speaker` spans, a new class added for this packet only, since the base
stylesheet has no prior speaker-label element) and italic stage directions (reusing plain `<em>`-equivalent
styling via a new `.stage-direction` class), per Section 1's "state the plain action, never the pedagogical name"
rule for a strategy not explicitly listed in that section's table. Its three discussion prompts (in a
simultaneous small-group format per Section 2.9, since a print page cannot orchestrate a live Concentric Circles
rotation) came straight from the source lesson, and it carries an L4 differentiated-participation tip line under
the sentence stems, matching its own Phase 3 tracking task. Task D embeds the lesson's second comparison text (a
visitor placard promoting Portland Head Light as a tourist destination) inline, matching Lessons 2-3's pattern.

## Generation workflow (current)

This is the process for producing one Set's worth of lessons, in order (see `shared/Program_Conventions.md` §C
for what a Set is); today that's **4 lessons**.

**Step 1 - Plan the Set.** Run `Generate_Module_Lesson_Plan_Prompt_v1.3.md` for the
target Module, Band, and Set number. It reads the Rotation Log first (for cross-Set genre/strategy/vocabulary
checks against the most recent Set already planned for this Module/Band, or the previous module's last Set if
this is a new Module/Band's first Set), produces the 4-lesson plan table, and runs its self-check. Review the
plan and approve it before moving on - do not generate lesson content against an unapproved plan. Once approved,
append its Rotation Log entry to `Rotation_Log.md` per that prompt's Section 0.

**Step 2 - Generate lessons two at a time.** Run `Generate_Lesson_Prompt_v2.8.md`
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

**Step 5 - Assessment.** Run `Generate_Assessment_Prompt_v4.2.md` once a Set's lessons are complete (per its own
scope note, from a completed Set's worth of lessons, not a single one) - typically at the end of a Set (all 4
lessons), after Steps 2-4 have been run across the relevant lessons, not per lesson. Confirm scope (cumulative
vs per-lesson), the Set number, and which task Level each student/group actually completed before generating;
it produces one test section and one study guide per task Level in the band, plus a Foundation Support check
where applicable. A Set is 4 lessons, so the `Set1_Intermediate_Assessment.md` generated for Intermediate
Module 1 Set 1 (2026-09-08) is the complete end-of-Set assessment - there is no separate 8-lesson pass to run.

**Step 5a - Print formatting for the assessment.** Run `Generate_Assessment_Student_Packet_Prompt_v1.md`
immediately after Step 5's Assessment `.md` is complete, in the same session, to produce a single, print-ready,
black-and-white student handout as one self-contained HTML file - four Task-Level sections, each printable on
its own, with every source-lesson/Tests tag and the entire Scoring Guide stripped. Independent of Step 6 below
(a lesson's own print formatting), since an assessment has no taught Unit A/B to translate.

**Step 6 - Print formatting for students.** Run `Generate_Student_Packet_Prompt_v1.9.md`
against a completed 2-day lesson from Step 2 (both days, in full) to produce a single, print-ready,
black-and-white student handout as one self-contained HTML file, reusing the required base
stylesheet in `shared/Student_Packet_Style_Guide.md` and pulling its 2-3 discussion prompts directly from the source lesson. This step is
independent of Steps 3-5 and can run any time after Step 2 completes for that lesson. Deliver as an HTML
preview first; format feedback typically comes as scoped edits to that file rather than a full regeneration. No
teacher-facing formatted version exists yet - out of scope for this prompt.

## Pending work

- **Module 1 Advanced Lesson 1's Fishbowl** - not yet checked/patched against v2.7's Section 0.10 outer-circle
  task and multi-prompt requirements. Worth doing the same pass once convenient.
- **Module 1 Advanced Homework/TOEFL/Assessment** - not started; now that all 4 lessons of Set 1 are generated,
  this is the next work per Steps 3-5.
- **Print formatting for Advanced Set 1** - now complete for all 4 lessons (`SagradaFamilia_Advanced_L1_Packet.html`,
  `ForgeAtDawn_Advanced_L2_Packet.html`, `VinylComeback_Advanced_L3_Packet.html`,
  `PortlandHeadLight_Advanced_L4_Packet.html`); Set 1 Intermediate's print
  formatting is complete for all 4 lessons (`RunningShoes_Intermediate_L3_Packet.html`,
  `WynwoodWalls_Intermediate_L4_Packet.html`).
- **Teacher-facing formatted/print version** - not started; a possible future companion to the Step 6 prompt,
  noted but out of scope until requested.
- **Resolved 2026-09-08**: Reading now has an Assessment Student Packet prompt
  (`Generate_Assessment_Student_Packet_Prompt_v1.md`), matching Listening/Speaking's and Writing's own. First
  run produced `Module_1/Set_1/Set1_Intermediate_Assessment_Packet.html` from the existing
  `Set1_Intermediate_Assessment.md` the same session - see the Module 1 Intermediate section above.
- **Novel Reading lesson type** - not started. Will need its own lesson-generation prompt, its own Module
  Lesson-Plan-equivalent (or a shared one adapted to variable day-counts), and its own `../novel-reading/`
  folder (index, prompts, rotation log) rather than being folded into the tables above, since day-count is
  fixed for Passage Reading and variable for Novel Reading.
