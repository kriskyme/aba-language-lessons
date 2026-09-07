# Listening/Speaking Index

_This is the Listening/Speaking counterpart to Passage Reading's `Index.md` - same purpose (a living index of the file
family, sync status, and run order), same living-document rule (update it whenever a doc in this family is added,
renamed, or revised). Both index docs describe sibling prompt families that share `learningobjectives.csv` and
the same 8-Module skill taxonomy (see `shared/Program_Conventions.md` §A), but each family's lesson type and
workflow are otherwise independent. Version history lives in `Changelog.md`._

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
| `Generate_Lesson_Prompt_v1.1.md`                  | Generates one lesson (a 2-day cycle: Day 1 Listening, Day 2 Speaking): sources a real audio/video text, builds tiered listening and speaking tasks around it. Carries five addenda, including the day-count/Unit Architecture correction and balanced-duration item counts. v1.1 adds a required `**Band:** ... \| **Version:** ...` field (`shared/Program_Conventions.md` §G) to the opening metadata line.                                                                                                                                                                                                                                                                              | Current (v1.1 + five addenda); eight real lessons generated against it (Intermediate 1-4, Advanced 1-4), all eight on the current 2-day cycle                                                        |
| `Generate_Module_Lesson_Plan_Prompt_v1.md`      | Plans one Set (4 lessons by default, matching the 2-day cycle) for a given Module/Band - topic directions, content-format/strategy/skill rotation, task-Level-to-objective mapping - before any lesson content is generated. A Module/Band can hold more than one Set over time (a fresh rotation for a retaught semester); lesson numbering stays global across Sets. Listening/Speaking-modality objectives only.                                                                                                                                                                                                                                                       | Current (v1 + Sets correction); Module 1 Intermediate and Advanced retroactively relabeled as Set 1 + Set 2 - see progress sections below |
| `Rotation_Log.md`                                                     | Overview only as of the per-Band split: purpose, the cross-Band historical notes (day-count correction, Sets/Assessment-prompt introductions), and links to each Band's own log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | N/A (data, not a prompt) |
| `Rotation_Log_Intermediate.md`                                        | Running record of every approved Intermediate-Band Set's format/strategy/skill/hook/protocol/vocabulary/topic choices, one subsection per Set. Read before planning a new Set; appended to after approval.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1/Set 2 |
| `Rotation_Log_Advanced.md`                                            | Same, for the Advanced Band. A new Band's file is created lazily the first time a lesson in that Band is generated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1/Set 2 |
| `Rotation_Log_Proficient.md`                                          | Same, for the Proficient Band. Created 2026-09-07 - the first Band file created purely from a plan, before any lesson in the Band had been generated; Lesson 1 generated the same day.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1 (Lesson 1 of 4 generated) |
| `Rotation_Log_Beginner.md`                                            | Same, for the Beginner Band. Created 2026-09-07.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1 (Lesson 1 generated) |
| `Changelog.md`                                                        | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | N/A (data, not a prompt)                                                                                                                                                                                            |
| `Generate_Student_Packet_Prompt_v1.3.md`           | Takes one completed lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML), mirroring Passage Reading's print prompt (same shared base stylesheet, in `shared/Student_Packet_Style_Guide.md`, same star-rating system), adapted for a real-source lesson: a plain citation box instead of a printed passage, a fillable Listening Notes organizer instead of an annotation key, two parts (Unit \_A Listening / Unit \_B Speaking) instead of Unit \_A/\_B by calendar day. As of v1.3, the opening masthead carries a top-right `.masthead-meta` stack of two tags - "Listening & Speaking," then Band and version code combined as one string (corrected from a same-day three-line version). Section 2.13 ("same rules as Passage Reading 2.12-2.14") inherits that prompt's v1.5 idiom-table rule automatically: a lesson with 2 or more idioms to gloss renders "Idioms to Know" as a table (`.idiom-list`/`.irow`), matching "Words to Know," instead of stacked plain paragraphs.                                                                                                                                                                                                       | Current (v1.3); eight packets generated (Intermediate 1-4, Advanced 1-4). The two Set 1 Lesson 1 packets (NewBakery, LostKitchen) were hand-corrected 2026-09-06 to add the `.masthead-tag` and to match the shared base stylesheet exactly (idiom styling, `.task-block .instr-line` spacing, vocab-list column width, one-line `font-family` formatting) - see `shared/Changelog.md`. LostKitchen was hand-corrected again 2026-09-07: its two idioms now render as a table (`.idiom-list`/`.irow`) instead of stacked plain paragraphs, per the new idiom-table rule above, and its masthead now carries the two-tag version-stack convention. `NewBakery` was also synced 2026-09-07: its masthead now carries the `.masthead-meta` two-tag stack too, and Task A item 3's word bank was moved inline with its item (it still has only one idiom, so the idiom-table rule doesn't apply). `LivingTextbooks_Advanced_L2` was fully synced to the current spec 2026-09-07 too (masthead-meta stack, idiom-table conversion, vocab-list/task-block CSS drift, missing `.refresher` CSS) - see `Changelog.md` and `Rotation_Log_Advanced.md`. `KeyDeer_Advanced_L3` and `GlassBender_Advanced_L4` were both generated fresh 2026-09-07 directly against the current spec (masthead-meta stack, idiom-table format from the start) - neither needs later sync. `PortoFoodTour_Intermediate_L2`, `Backpack_Intermediate_L3`, and `GreatGrandmother_Intermediate_L4` were also fully synced 2026-09-07 (masthead-meta stack, `.refresher` CSS, instr-line/idiom-item CSS drift, one-line `font-family` formatting; PortoFoodTour's idiom also moved out of a spotlight-box, GreatGrandmother's vocab-list column width realigned) - see `Changelog.md` and `Rotation_Log_Intermediate.md`. Every Set 1 packet across both bands is now swept |
| `Generate_Assessment_Prompt_v1.md`              | Generates the assessment layer on top of a taught Set, both parts run every Set: Part A, an individual Listening assessment (new unseen source, task-Level-tiered items, in-class, same period length as a lesson's Day 1); Part B, a Speaking assessment whose mechanism splits by band - Beginner/Intermediate scored via a Teams Speaking Progress solo recording (the recording IS the assessment); Advanced/Proficient default to a live solo/group presentation, with a same-task, same-rubric Teams-recording version always also generated as a standing scored alternate. | Current (v1); two assessments generated (Intermediate Set 1, Advanced Set 1) - both still field-testing pending                                                                                                       |
| `Generate_Assessment_Student_Packet_Prompt_v1.md` | Takes a completed Assessment (Part A + Part B) and produces a single, print-ready student handout: a Listening Test section (one page per task Level, citation box, fillable notes organizer, that Level's items only) and a Speaking Task section (a plain instruction card per Level - topic, target length, submission info). Strips every answer key, point value, holistic pass note, and rubric - none of that is student-facing. Mirrors `Generate_Student_Packet_Prompt_v1.3.md`'s translation approach and reuses the shared base stylesheet/classes. | Current (v1); two packets generated (Intermediate Set 1, Advanced Set 1) |
| `Generate_TOEFL_LS_Extension_Prompt_v1.md` | Generates an optional TOEFL iBT Listening and Speaking practice packet from a completed Advanced/Proficient lesson - Part A (Listening: an original, faithful passage sized to a real TOEFL task format, 6-question-type item set) and Part B (Speaking: 7 original Listen and Repeat sentences, 4 original Take an Interview questions, both grounded in the lesson's real topic/vocabulary). Grounded in `source/TOEFL_Listening_extracted_text.txt` and `source/TOEFL_Speaking_extracted_text.txt`. Sibling to Passage Reading's `Generate_TOEFL_Extension_Prompt_v1.md`. | Current (v1); one packet generated (Advanced Set 1 Lesson 1, LostKitchen) |
| `learningobjectives.csv` (project file, shared with Passage Reading) | Source of truth for every Learning Objective, including the Listening/Speaking modality rows this family pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | N/A (data)                                                                                                                                                                                                          |

Not yet started for this family: a homework-generation prompt and the Part-2/presentation-project extension
described above. See Pending work.

## Module 1 progress, Beginner Band (Describing, Beginner)

Plan approved and logged: `lessons/beginner/Module1_Beginner_Lesson_Plan.md`,
`Rotation_Log_Beginner.md` (new file - the first Set ever planned for this Band). Task Levels 1, 2,
3 (Beginner band; only 3, not 4, since Level 1 is the scale's floor). Source calibrated to Level 1
(30 sec-2 min, graded-for-absolute-beginners clip). **Set 1 plan approved 2026-09-07; Lesson 1
generated:**

| File | Lesson # | Real source | Status |
| --- | --- | --- | --- |
| `Set_1/Lesson_1_WhatIsIt/Lesson1_WhatIsIt.md` | 1 | "Let's Learn English - Level 1 - Lesson 4: What Is It?", VOA Learning English (characters Anna, Pete, Marsha) | Current. Flagged deviations: runtime (~5:00 vs. the 30 sec-2 min Level 1 target; kept as Section 0.2's own named Level 1 platform); Speaking Skill (Giving Examples) grounded in source context rather than a directly quoted exchange |
| - | 2 | A simple daily routine shown step by step | Not yet sourced - planned only |
| - | 3 | A family member introduced by a child or narrator | Not yet sourced - planned only |
| - | 4 | Colors and shapes of common items, shown and named | Not yet sourced - planned only |

**Lesson 1's student packet:** `Set_1/Lesson_1_WhatIsIt/WhatIsIt_Beginner_L1_Packet.html`, generated
against `Generate_Student_Packet_Prompt_v1.3.md` - two parts (Unit 1A Listening / Unit 1B Speaking),
each with 3 star-rated task blocks (Beginner has 3 task Levels, not 4), a plain citation box, a
2-column order-and-name Listening Notes organizer (adapted from the module's usual comparison
T-chart, since this source is a sequence of named objects rather than a two-category comparison),
and the upside-down Closing Transfer Check script. Not yet reviewed against a printed page.

Next step for this Band: generate Lesson 2 against the approved plan, one lesson at a time, per the
Generation workflow below.

## Module 1 progress, Intermediate Band (Describing, Intermediate)

Plan approved and logged: `lessons/intermediate/Module1_Intermediate_Lesson_Plan.md`. Task
Levels 2, 3, 4, 5 (Intermediate band). **Set 1 complete:** Lessons 1-4 fill one full rotation's
8-day allocation. Each lesson's `.md` and student-packet `.html` now live together in their own
`Set_1/Lesson_<N>_<Slug>/` folder.

| File                                                                                               | Lesson # | Real source                                                                                              | Status                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Set_1/Lesson_1_NewBakery/Lesson1_NewBakery.md`                | 1        | "New Bakery, Old Baking Method," VOA Learning English (Jonathan Bethony, Seylou Bakery, Washington D.C.) | Current (source is audio, not video; item counts balanced)                                                                        |
| `Set_1/Lesson_2_PortoFoodTour/Lesson2_PortoFoodTour.md`        | 2        | "Porto Food Tour," Rick Steves Classroom Europe (guide Andre, Taste Porto Food Tours)                    | Current                                                                                                                                                                    |
| `Set_1/Lesson_3_Backpack/Lesson3_Backpack.md`                  | 3        | "How to Choose a Backpack," REI Co-op Expert Advice (article + embedded video)                           | Current. Flagged deviations: source register not simplified for learners (draws only from simpler sections); module alignment reasoned through (Describing vs. Instructing)                                       |
| `Set_1/Lesson_4_GreatGrandmother/Lesson4_GreatGrandmother.md` | 4        | "Great-Grandmother Proves It Is Never Too Late to Learn," VOA Learning English (Setsuko Takamizawa)      | Current. Flagged deviations: vocabulary-theme mismatch (family-relationship words vs. planned "personality & character traits"); Speaking Skill grounded in source context rather than a directly quoted exchange |

**Set 2 (Lessons 5-8: Nature description, Craft-studio tour, Museum/exhibit-guide description, Atelier/workshop
profile) is planned only, not yet generated** - a second full rotation of topics for whenever this module is
retaught with fresh material, per the Lesson Plan's Sets note. Not needed to complete this module; Set 1 already
does that on its own.

All four Set 1 lessons' student packets (`.html`) are current against the Student Print Formatting Prompt
standard (Good to Know at the top, citebox at the point of watching, compact inline multiple-choice, real
picture placeholders, word banks positioned before their items, universal question numbering, full-width answer
lines, the `.match-row`/`.qitem`/`.num` consistency fixes) - see that prompt's own changelog for the complete
list. Not yet reviewed against a printed page.

**Set 1's Listening/Speaking Assessment:** `lessons/intermediate/Set_1/Set1_Intermediate_Assessment.md`.
Part A (Listening) uses a new, verified real source - "Visitors Laugh
Away Troubles at the HaHaHouse Museum" (VOA Learning English, a real laughter museum in Zagreb, Croatia) -
distinct from all 4 taught sources, with tiered items covering all four of the Set's listening strategies (Main
Ideas/Gist, Recognize Examples, Sequence Markers, Predict from Context). Part B (Speaking) is a Teams Speaking
Progress solo recording (Intermediate's default mechanism), emphasizing Making Comparisons and Sequencing
Language, with the same-task live-delivery option noted per the current prompt. This is the first assessment
ever generated against this prompt - not yet given to a real class, so treat every number in it (period length,
item counts, target recording lengths) as a reasoned starting point pending real classroom feedback, per the
prompt's own open items.

**Student-facing packet:** `lessons/intermediate/Set_1/Set1_Intermediate_Assessment_Packet.html`, generated
against `Generate_Assessment_Student_Packet_Prompt_v1.md` - a Listening Test section (one printable page per
task Level) and a Speaking Task section (a plain instruction card per Level), with every answer key, point
value, holistic pass note, and rubric stripped. Not yet reviewed against a printed page, same as the six lesson
packets.

## Module 1 progress, Advanced Band (Describing, Advanced)

Plan approved and logged: `lessons/advanced/Module1_Advanced_Lesson_Plan.md`. Task Levels
4, 5, 6, 7 (Advanced band). Level 7's Listening objective needs two real sources on the same subject (compare
rhetorical framing) - flagged per lesson with a suggested angle in the plan. **Set 1 complete (Lessons 1-4, 4 of
4 generated)**; **Set 2 (Lessons 5-8) is planned only**:

| File                                                                                                    | Lesson # | Real source(s)                                                                                                                                                                         | Status                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Set_1/Lesson_1_LostKitchen/Lesson1_LostKitchen.md`             | 1        | Primary: PBS NewsHour feature on Erin French/The Lost Kitchen (Freedom, Maine). Secondary (Level 7 excerpt only): Radio Cherry Bombe podcast interview with Erin French.               | Current, per the Lesson prompt's fifth-addendum mapping table. No task, quote, vocabulary item, or differentiated activity was cut, only reorganized |
| `Set_1/Lesson_2_LivingTextbooks/Lesson2_LivingTextbooks.md`     | 2        | Primary: PBS NewsHour Weekend feature on Phoenix mid-century modern preservation. Secondary (Level 7 excerpt only): Modern Phoenix's Beadle Archive page on the White Gates Residence. | Current, same treatment as Lesson 1                                                                                                                    |
| `Set_1/Lesson_3_KeyDeer/Lesson3_KeyDeer.md`                     | 3        | Primary: PBS News Weekend "Saving Species" feature on the Key deer and the National Key Deer Refuge (Florida Keys). Secondary (Level 7 excerpt only): U.S. Fish & Wildlife Service's official National Key Deer Refuge pages. | Current - generated fresh against v1.1, current 2-day architecture from the start, no restructure needed |
| `Set_1/Lesson_4_GlassBender/Lesson4_GlassBender.md`             | 4        | Primary: Idaho Public Television's *createid* series, "Glass Bender: Wil Kirkman" (Rocket Neon, Boise). Secondary (Level 7 excerpt only): Boise Art Scene's written interview with Wil Kirkman. | Current - generated fresh against v1.1, current 2-day architecture from the start, no restructure needed. Completes Set 1. |

All four lessons above follow the current Day 1 (Unit A)/Day 2 (Unit B) architecture, and their student packets
match the current Student Print Formatting Prompt conventions (Good to Know at the top, citebox at the point of
watching, compact inline multiple-choice, real picture placeholders, word banks positioned before their items,
multi-source Task D layout for Level 7, upside-down Closing Transfer Check script) - see the Rotation Log's
Advanced Band section for the full note.

**Set 1 is now complete**, and its assessment has now been generated too. Set 2 (Lessons 5-8, a fresh rotation,
not yet needed to complete the module) remains the only unstarted next step for this Band.

**Set 1's Listening/Speaking Assessment:** `lessons/advanced/Set_1/Set1_Advanced_Assessment.md`. Part A
(Listening) uses a new, verified real source - "Artists with disabilities let their creativity soar at this
Utah studio" (PBS News Weekend, Ali Rogin; Jump the Moon art studio, Logan, Utah) - distinct from all 4 taught
sources, with tiered items covering all four of the Set's listening strategies (Stated vs. Implied Opinion,
Recognize Examples, Cause-and-Effect Language, Signposting/Discourse Markers). Level 7's item also draws on a
second real source (a Utah Division of Arts & Museums profile page) for the same two-source comparative-framing
task pattern this Set's own Level 7 lesson items use. Part B (Speaking) is a live solo presentation (Advanced's
default mechanism), with a same-task, same-rubric Teams-recording version generated as the standing alternate,
emphasizing Making Comparisons and Hedging an Opinion. This is the first assessment ever generated against this
prompt for the Advanced band - not yet given to a real class, so treat every number in it (period length, item
counts, target recording/live lengths, live-presentation time budget) as a reasoned starting point pending real
classroom feedback, per the prompt's own open items.

**Student-facing packet:** `lessons/advanced/Set_1/Set1_Advanced_Assessment_Packet.html`, generated against
`Generate_Assessment_Student_Packet_Prompt_v1.md` - a Listening Test section (one printable page per task Level)
and a Speaking Task section (a plain instruction card per Level), with every answer key, point value, holistic
pass note, and rubric stripped. Not yet reviewed against a printed page, same as the eight lesson packets and
the Intermediate Set 1 assessment packet.

**Lesson 1's TOEFL Practice Extension (optional add-on, new 2026-09-07):**
`Set_1/Lesson_1_LostKitchen/LostKitchen_Advanced_L1_TOEFL.md` (instructor document: Part A Listening
- an original Academic Talk passage faithful to the real PBS segment, 4 items across Main
Idea/Factual/Inference/Attitude, full answer key; Part B Speaking - 7 original Listen and Repeat
sentences and 4 original Take an Interview questions grounded in the lesson's real topic/vocabulary,
real TOEFL scoring guides, item metadata table) and
`Set_1/Lesson_1_LostKitchen/LostKitchen_Advanced_L1_TOEFL_Packet.html` (student packet - no passage
or sentence/question text shown, per the "heard, not read" rule; only instructions, Part A's
questions/answer choices, and Part B's response-time slots). Generated against the new
`Generate_TOEFL_LS_Extension_Prompt_v1.md`, this family's first worked example of that prompt. Does
not alter the base Day 1/Day 2 lesson. Not yet given to a real class.

**Print formatting (student version), all current:**

- Intermediate Lesson 1: `Set_1/Lesson_1_NewBakery/NewBakery_Intermediate_L1_Packet.html`.
  Two parts (Unit 1A Listening / Unit 1B Speaking), each with its own star-rated choose-your-task block merging
  that half's differentiated day content into one block per Level, a plain citation box in place of a printed
  passage, and a fillable Listening Notes comparison table. Hand-corrected 2026-09-06: added the
  `.masthead-tag` (Unit 1A masthead only, per the shared style guide's rule - an earlier pass had
  mistakenly also placed it on the Unit 1B masthead, now removed); moved the "mixing and matching"
  idiom out of a "Phrase Spotlight" spotlight-box into a plain "Idioms to Know" section-label block
  (matching how LostKitchen presents idioms) so it now shares Words to Know's typography instead of
  falling back to the page's default serif body font; added the `.refresher`/`.refresher-noline`
  CSS the "Check What You Heard" upside-down answer box was already using in its markup but had no
  rule for. Synced again 2026-09-07: the single `.masthead-tag` upgraded to the `.masthead-meta`
  two-tag stack (`Listening & Speaking` / `Intermediate S1.1.0`, Unit 1A masthead only, matching
  LostKitchen's retrofit); Task A item 3's word bank moved from a trailing block after the whole
  list to inline with its item, matching Task B item 2.
- Intermediate Lesson 2: `Set_1/Lesson_2_PortoFoodTour/PortoFoodTour_Intermediate_L2_Packet.html`. Same
  two-part structure; the Four-Corner Debate hook was translated into a plain "which sounds
  most like you" print activity rather than the live corner-moving version, and the Jigsaw protocol collapsed
  into three simultaneous small-group discussion prompts, per Section 1's translation rules. Fully synced
  2026-09-07 (had predated every hand-correction pass): added the `.masthead-meta` two-tag stack (`Listening &
  Speaking` / `Intermediate S1.2.0`, Unit 2A masthead only) and its CSS, including restoring `.masthead`'s
  `display: flex` layout; moved its one idiom ("in spite of") out of a `Phrase Spotlight` spotlight-box into a
  plain "Idioms to Know" block, matching NewBakery/LostKitchen; added the missing `.refresher`/`.refresher-noline`
  CSS the "Check What You Heard" upside-down box was already using in its markup; fixed `.task-block .instr-line`'s
  margin to 10px (was 4px) and restored `.idiom-item`/`.idiom-phrase`'s missing font properties; reflowed every
  multi-line `font-family` declaration onto one line.
- Intermediate Lesson 3: `Set_1/Lesson_3_Backpack/Backpack_Intermediate_L3_Packet.html`. Fully synced 2026-09-07,
  same sweep as Lesson 2: added the `.masthead-meta` two-tag stack (`Intermediate S1.3.0`, Unit 3A masthead only)
  and its CSS/`.masthead` flex layout; added the missing `.refresher`/`.refresher-noline` CSS its two upside-down
  boxes (the Mystery Quote reveal and "Check What You Heard") were already using; fixed `.task-block .instr-line`'s
  margin to 10px and restored `.idiom-item`/`.idiom-phrase`'s font properties (unused in this lesson - no idiom in
  the source - but kept in sync for stylesheet consistency); reflowed every multi-line `font-family` declaration.
- Intermediate Lesson 4: `Set_1/Lesson_4_GreatGrandmother/GreatGrandmother_Intermediate_L4_Packet.html`. Fully
  synced 2026-09-07, same sweep as Lessons 2-3: added the `.masthead-meta` two-tag stack (`Intermediate S1.4.0`,
  Unit 4A masthead only) and its CSS/`.masthead` flex layout; realigned `.vocab-list .word`'s column width to
  the shared 130px (was locally widened to 150px), the same drift LostKitchen had; added the missing
  `.refresher`/`.refresher-noline` CSS the "Check What Happens" upside-down box was already using; fixed
  `.task-block .instr-line`'s margin to 10px and restored `.idiom-item`/`.idiom-phrase`'s font properties (unused
  - no idiom in this source); reflowed every multi-line `font-family` declaration, including the lesson's own
  `.kwl-table` extension class.
- Advanced Lesson 1: `Set_1/Lesson_1_LostKitchen/LostKitchen_Advanced_L1_Packet.html`.
  Same structure as the Intermediate packets, plus one
  pattern the Intermediate ones don't need: Level 7's star task (Task D, both halves) compares two real sources
  directly inside the task block, using a labeled two-part excerpt layout kept within the fair-use ceiling, per
  the Print Formatting Prompt's Section 2.7 multi-source guidance. Hand-corrected 2026-09-06: added the
  `.masthead-tag` (Unit 1A masthead only, per the shared style guide's rule - an earlier pass had
  mistakenly also placed it on the Unit 1B masthead, now removed); realigned `.vocab-list .word`'s
  column width to the shared stylesheet's 130px (was locally widened to 150px); added the
  `.refresher`/`.refresher-noline` CSS the "Check What You Heard" upside-down answer box was
  already using in its markup but had no rule for.
- Advanced Lesson 2: `Set_1/Lesson_2_LivingTextbooks/LivingTextbooks_Advanced_L2_Packet.html`.
  Same two-part structure; Task D again uses the
  multi-source compare-pair pattern (news segment vs. an archive website), introducing the second source inline
  within the task itself per the "never name an unintroduced source" rule. Fully synced 2026-09-07 (this
  packet had predated every hand-correction pass): added the `.masthead-meta` two-tag stack (Unit 2A
  masthead only); converted its two idioms from plain `.idiom-item` paragraphs under "Phrases to Know" to
  the `.idiom-list`/`.irow` numbered table under "Idioms to Know"; realigned `.vocab-list .word`'s column
  width to 130px (was 150px); restored `.idiom-item`/`.idiom-phrase`'s missing font properties; fixed
  `.task-block .instr-line`'s margin to 10px (was 4px); added the missing `.refresher`/`.refresher-noline`
  CSS the "Check What You Heard" upside-down box was already using in its markup; reflowed every
  multi-line `font-family` declaration onto one line per the style guide's formatting convention.
- Advanced Lesson 3: `Set_1/Lesson_3_KeyDeer/KeyDeer_Advanced_L3_Packet.html`. Same two-part structure;
  Task D again uses the multi-source compare-pair pattern (news segment vs. the refuge's own official
  government page), introducing the second source inline within the task itself. Generated fresh against
  the current spec, so it already carries the `.masthead-meta` stack and `.idiom-list`/`.irow` table (two
  idioms) from the start - no later sync needed.
- Advanced Lesson 4: `Set_1/Lesson_4_GlassBender/GlassBender_Advanced_L4_Packet.html`. Same two-part
  structure; Task D again uses the multi-source compare-pair pattern (video profile vs. the artist's own
  written interview), introducing the second source inline within the task itself. Generated fresh
  against the current spec, so it already carries the `.masthead-meta` stack and `.idiom-list`/`.irow`
  table (three idioms) from the start - no later sync needed. Completes Set 1's packets.
  None of the eight packets has been reviewed against a printed page yet.

## Module 1 progress, Proficient Band (Describing, Proficient)

Plan approved and logged: `lessons/proficient/Module1_Proficient_Lesson_Plan.md`, `Rotation_Log_Proficient.md`
(new file - the first Set ever planned for this Band). Task Levels 5, 6, 7, 8 (Proficient band; 5 and 6 borrowed
from Advanced, per the Proficient-only two-Levels-down exception in `shared/Program_Conventions.md` §B). Source
calibrated to Level 7 (10-18 min, full unedited TED Talk/long-form interview/lecture excerpt). Level 7's
Listening objective needs two real sources on the same subject (same requirement Advanced's Level 7 has);
Level 8's Listening objective additionally needs a source that genuinely hedges or withholds something - both
flagged per lesson with a suggested angle in the plan. **Set 1: Lesson 1 of 4 generated:**

| Lesson # | Topic Direction | Real source(s) | Status |
| --- | --- | --- | --- |
| 1 | A real neighborhood/district undergoing visible change, described by people with different stakes in it | Primary: PBS NewsHour, "Are newcomers a mixed blessing for the Lower Ninth Ward?" (William Brangham, aired 2015-08-25). Secondary (Level 7 only): "Make It Right Foundation" article on English Wikipedia, documenting that nonprofit's own quoted mission. | Current - generated fresh against v1.1, current 2-day architecture from the start. Two open items flagged (not silently resolved): the Level 7 secondary source is a Wikipedia article, not the org's own live site (unconfirmed as still fetchable); Day 2's Speaking Skill Spotlight is grounded in the source's real situational context rather than a quoted on-screen comparison line - see `Rotation_Log_Proficient.md` for the full notes. |
| 2 | A real designer's or maker's talk about one product or piece of design they created | Not yet sourced | Planned only |
| 3 | A real person profiled by someone who knew them closely, visibly careful around one sensitive aspect of that person's life or reputation | Not yet sourced | Planned only |
| 4 | A real institution or historic site described in a lecture/docent walkthrough, where institutional framing plays down a known shortcoming | Not yet sourced | Planned only |

**Print formatting (student version):** `Set_1/Lesson_1_LowerNinthWard/LowerNinthWard_Proficient_L1_Packet.html`,
generated fresh against the current Student Print Formatting Prompt spec from the start (masthead-meta stack,
idiom-table format, Four-Corner Debate translated to a plain circle-your-answer print activity, multi-source Task
C compare-pair layout for Level 7, upside-down Closing Transfer Check script) - no later sync expected. Not yet
reviewed against a printed page, same as every other packet in this family.

Next step for this Band: run `Generate_Lesson_Prompt_v1.1.md` for Lesson 2 against the approved plan, one lesson
at a time, per the Generation workflow below.

## Generation workflow (current)

**Step 1 - Plan the module.** Run `Generate_Module_Lesson_Plan_Prompt_v1.md` for the
target Module and Band. It reads the Rotation Log first (`Rotation_Log.md` plus that Band's own
`Rotation_Log_<Band>.md`), produces the module's plan table (4 rows by
default), and runs its self-check. Review and approve the plan before
generating any lesson content. Once approved, append its Rotation Log entry to that Band's `Rotation_Log_<Band>.md`.

**Step 2 - Generate lessons.** Run `Generate_Lesson_Prompt_v1.1.md` against the approved
plan. Because each lesson now requires finding and verifying a real source (not just writing to a word-count
ceiling), generate **one lesson at a time** for this family rather than Passage Reading's two-at-a-time pacing,
at least until the sourcing step has proven reliable enough to batch. Check each lesson's self-check
(runtime/citation/task-Level checks) before moving to the next.

**Step 3 - Assess.** Once a Set (4 lessons) is complete, run `Generate_Assessment_Prompt_v1.md` for that Set - both Part A (Listening) and Part B (Speaking) run every Set, not staggered. Part B's
mechanism depends on the Band: Beginner/Intermediate produce a scored Teams Speaking Progress recording task
(the formal assessment itself); Advanced/Proficient produce a live presentation task plus a same-task
Teams-recording alternate for standing use (e.g. an absence). See that prompt's own scope notes (Section B.0-B.1).

**Step 4 - TOEFL Practice Extension.** Run `Generate_TOEFL_LS_Extension_Prompt_v1.md` per completed
Advanced/Proficient-band lesson, as an optional add-on for TOEFL-interested students, while the rest
of the class continues on the standard lesson unchanged. Once a general-track homework prompt exists
for this lesson type, this step should replace homework for that student on that cycle rather than
adding to it, the same relationship Passage Reading's TOEFL Track Extension has to its own homework
step - not yet actionable since Step 5 (homework) isn't built.

**Step 5+ - not yet built.** Homework and the Part 2/presentation-project extension remain pending (see below).

## Pending work

- **Generate Proficient Module 1 Set 1's remaining lessons (2-4)** - Lesson 1 is generated; Lessons 2-4 are still
  planned only. Run `Generate_Lesson_Prompt_v1.1.md` one lesson at a time, per the Generation workflow below,
  applying the same Level 7 two-source pattern and Level 8 withheld-content source each time.
- **Give both Set 1 assessments to a real class** - Intermediate Set 1's and Advanced Set 1's assessments are
  both generated but neither has been field-tested. Once given, expect addenda the same way the Lesson prompt
  got five.
- **Homework Generation Prompt** - not started. Will need its own rules given a homework assignment can't
  hand a student the full copyrighted transcript the way Passage Reading homework reuses the anchor text.
- **Generate any future Set's assessment** - once Set 2 (either Band) is generated, run
  `Generate_Assessment_Prompt_v1.md` and `Generate_Assessment_Student_Packet_Prompt_v1.md` against it, the same
  way both were just run for Advanced Set 1.
- **Part 2 + Presentation Project Extension** - not started. Planned to mirror the content sample's second
  (video) source, cross-source synthesis, and group-presentation assignment, as an optional add-on after a core
  lesson is complete - analogous to how this family's own TOEFL Practice Extension
  (`Generate_TOEFL_LS_Extension_Prompt_v1.md`) now sits on top of a completed lesson rather than inside it.
- **Generate TOEFL Practice Extensions for the remaining Set 1 lessons** - only Advanced Lesson 1 (LostKitchen)
  has one so far. Advanced Lessons 2-4 and any completed Proficient-band lesson are equally eligible (Section
  0.1: Advanced/Proficient bands only); generate on request, not automatically for every lesson.
- **Give the LostKitchen TOEFL packet to a real class** - like every other assessment/extension artifact in this
  family, it hasn't been field-tested yet; expect the same kind of addenda the Lesson and Assessment prompts
  picked up after their own first real uses.
