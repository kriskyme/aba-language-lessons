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
| `Generate_Lesson_Prompt_v2.1.md` | Generates one lesson (a 2-day cycle: Day 1 Listening, Day 2 Speaking): sources a real audio/video text, builds tiered listening and speaking tasks around it, and produces three artifacts in order (transcript file, lesson `.md`, packet `.html`). Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; states only what is true of a real-source lesson (Section 0.2 runtime/pace/register ceilings, 0.3 sourcing and fair-use rules and the transcript file, 0.4 rotation banks, the two-day phase structure) and points to the shared files for everything modality-neutral. Section 0.5's self-check is the shared Quality Standards §F list plus 13 Listening/Speaking-only items. The TOEFL Track Tier (formerly Section 0.6) now lives in its own companion prompt, next row. | Current (v2.1); nine real lessons generated against v1.1-v1.10 (Beginner 1, Intermediate 1-4, Advanced 1-4), all on the 2-day cycle; the transcript-file requirement is going-forward only so far - see Pending work |
| `Generate_TOEFL_Track_Tier_Prompt_v1.md` | Generates a TOEFL-capable variant of an already-generated Advanced/Proficient Set, forked into a sibling `Set_<N>_T/` folder (never editing the base files): four touchpoint kinds threaded through both days - (A) teacher-only "TOEFL Connection" framing in Phases 1 and 3 of each day, (B) three in-class touchpoints on the class's shared pacing (organizer column, extra transfer-check question, reframed protocol turn), (C) a Listening capstone answered from the same shared source, (D) a Speaking capstone split into an untimed in-class rehearsal plus a teacher-recorded Teams homework whose script and scoring guides live in a separate teacher-only `_TOEFL_Homework.html` file. Section 1 is the lesson side, Section 2 the packet rendering (the former 2.6a/2.7a/2.8a/2.10a/2.10b/2.11a of the Student Packet prompt), Section 3 the self-check. Extracted 2026-09-08 from the Lesson prompt's Section 0.6 and the packet prompt's TOEFL sub-sections, mirroring how Passage Reading keeps its TOEFL extension as a separate companion. | Current (v1); one fork generated under the old embedded mechanism (Advanced Set 1 Lesson 1, `Module_1/Set_1_T/`, `1.1T.1.4`), content unchanged by the extraction |
| `Generate_Module_Lesson_Plan_Prompt_v2.1.md` | Plans **one Set** (4 lessons: topic directions, content-format/strategy/skill/hook/protocol rotation, vocabulary themes, task-Level-to-objective mapping with both CSV halves named) before any lesson is generated. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; Rotation Log mechanics and adjacency rules point to Conventions §F; the 2026-09-03 8-lesson correction narrative and the "same as Passage Reading" cross-references are gone. Listening/Speaking objectives only. | Current (v2.1) |
| `Rotation_Log.md`                                                     | Overview only as of the per-Band split: purpose, the cross-Band historical notes (day-count correction, Sets/Assessment-prompt introductions), and links to each Band's own log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | N/A (data, not a prompt) |
| `Rotation_Log_Intermediate.md`                                        | Running record of every approved Intermediate-Band Set's format/strategy/skill/hook/protocol/vocabulary/topic choices, one subsection per Set. Read before planning a new Set; appended to after approval.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1/Set 2 |
| `Rotation_Log_Advanced.md`                                            | Same, for the Advanced Band. A new Band's file is created lazily the first time a lesson in that Band is generated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1/Set 2 |
| `Rotation_Log_Proficient.md`                                          | Same, for the Proficient Band. Created 2026-09-07 - the first Band file created purely from a plan, before any lesson in the Band had been generated; Lesson 1 generated the same day.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1 (Lesson 1 of 4 generated) |
| `Rotation_Log_Beginner.md`                                            | Same, for the Beginner Band. Created 2026-09-07.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1 (Lesson 1 generated) |
| `Changelog.md`                                                        | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | N/A (data, not a prompt)                                                                                                                                                                                            |
| `Generate_Student_Packet_Prompt_v2.2.md` | Takes one completed lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML) in two parts (Unit _A Listening / Unit _B Speaking). Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; states only what is specific to a Listening/Speaking packet (the citebox and its placement and media-type wording, Good to Know boxes front-loaded, the Listening Notes organizer, fixed-frame and multi-source task rules, the upside-down Check What You Heard script, Learn the Phrase, `.qitem`-numbered Discuss It, jargon-free closing headings) and points to the Style Guide for the translation table, star and lettered-Task rules, the regeneration rule, the delta CSS (now §H.1 there, moved out of this prompt), and the shared packet self-check. TOEFL Track Tier rendering moved to `Generate_TOEFL_Track_Tier_Prompt_v1.md` Section 2. Section 5 is Style Guide §I plus 10 Listening/Speaking items. | Current (v2.0); every packet under `lessons/` was generated against v1.3-v1.10 and hand-swept to the shared conventions in earlier passes (see `Changelog.md`) |
| `Generate_Assessment_Prompt_v2.md` | Generates a Set's Listening (Part A) and Speaking (Part B) assessments. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; keeps what is Listening/Speaking-specific (2-3 new real clips sourced like a lesson's, vocabulary pooled across the Set and tested only inside items, objective-only formats, the single-period structure, Part B's mechanism-by-band table and countable content requirements, the 3-point rubric) and points to Quality Standards §C for item quality, which now carries the distractor, padded-bank, and time-balance rules this prompt introduced program-wide. Self-checks are Quality Standards §F plus 8 Part A and 6 Part B items. | Current (v2); two assessments generated under v1 (Intermediate and Advanced Set 1) |
| `Generate_Assessment_Student_Packet_Prompt_v2.1.md` | Takes a completed Assessment and produces the student handout: Listening Test pages per Level with a citebox per clip, Speaking Task cards with the rubric's Meets column as a `.checklist` (now Style Guide §H.4), no answer keys, rubric tables, or submission information. Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; Section 5 is Style Guide §I plus 6 items. | Current (v2); two packets generated under v1 |
| `learningobjectives.csv` (project file, shared with Passage Reading) | Source of truth for every Learning Objective, including the Listening/Speaking modality rows this family pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | N/A (data)                                                                                                                                                                                                          |

Not yet started for this family: a homework-generation prompt and the Part-2/presentation-project extension
described above. See Pending work.

## Module 1 progress, Beginner Band (Describing, Beginner)

Plan approved and logged: `lessons/beginner/Module_1/Module1_Beginner_Lesson_Plan.md`,
`Rotation_Log_Beginner.md` (new file - the first Set ever planned for this Band). Task Levels 1, 2,
3 (Beginner band; only 3, not 4, since Level 1 is the scale's floor). Source calibrated to Level 1
(30 sec-2 min, graded-for-absolute-beginners clip). **Set 1 plan approved 2026-09-07; Lesson 1
generated:**

| File | Lesson # | Real source | Status |
| --- | --- | --- | --- |
| `Module_1/Set_1/Lesson_1_WhatIsIt/Lesson1_WhatIsIt.md` | 1 | "Let's Learn English - Level 1 - Lesson 4: What Is It?", VOA Learning English (characters Anna, Pete, Marsha) | Current. Flagged deviations: runtime (~5:00 vs. the 30 sec-2 min Level 1 target; kept as Section 0.2's own named Level 1 platform); Speaking Skill (Giving Examples) grounded in source context rather than a directly quoted exchange |
| - | 2 | A simple daily routine shown step by step | Not yet sourced - planned only |
| - | 3 | A family member introduced by a child or narrator | Not yet sourced - planned only |
| - | 4 | Colors and shapes of common items, shown and named | Not yet sourced - planned only |

**Lesson 1's student packet:** `Module_1/Set_1/Lesson_1_WhatIsIt/WhatIsIt_Beginner_L1_Packet.html`, generated
against `Generate_Student_Packet_Prompt_v1.4.md` - two parts (Unit 1A Listening / Unit 1B Speaking),
each with 3 star-rated task blocks (Beginner has 3 task Levels, not 4), a plain citation box, a
2-column order-and-name Listening Notes organizer (adapted from the module's usual comparison
T-chart, since this source is a sequence of named objects rather than a two-category comparison),
and the upside-down Closing Transfer Check script. Not yet reviewed against a printed page.

Next step for this Band: generate Lesson 2 against the approved plan, one lesson at a time, per the
Generation workflow below.

## Module 1 progress, Intermediate Band (Describing, Intermediate)

Plan approved and logged: `lessons/intermediate/Module_1/Module1_Intermediate_Lesson_Plan.md`. Task
Levels 2, 3, 4, 5 (Intermediate band). **Set 1 complete:** Lessons 1-4 fill one full rotation's
8-day allocation. Each lesson's `.md` and student-packet `.html` now live together in their own
`Module_1/Set_1/Lesson_<N>_<Slug>/` folder.

| File                                                                                               | Lesson # | Real source                                                                                              | Status                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Module_1/Set_1/Lesson_1_NewBakery/Lesson1_NewBakery.md`                | 1        | "New Bakery, Old Baking Method," VOA Learning English (Jonathan Bethony, Seylou Bakery, Washington D.C.) | Current (source is audio, not video; item counts balanced)                                                                        |
| `Module_1/Set_1/Lesson_2_PortoFoodTour/Lesson2_PortoFoodTour.md`        | 2        | "Porto Food Tour," Rick Steves Classroom Europe (guide Andre, Taste Porto Food Tours)                    | Current                                                                                                                                                                    |
| `Module_1/Set_1/Lesson_3_Backpack/Lesson3_Backpack.md`                  | 3        | "How to Choose a Backpack," REI Co-op Expert Advice (article + embedded video)                           | Current. Flagged deviations: source register not simplified for learners (draws only from simpler sections); module alignment reasoned through (Describing vs. Instructing)                                       |
| `Module_1/Set_1/Lesson_4_GreatGrandmother/Lesson4_GreatGrandmother.md` | 4        | "Great-Grandmother Proves It Is Never Too Late to Learn," VOA Learning English (Setsuko Takamizawa)      | Current (source is audio, not video). Flagged deviations: vocabulary-theme mismatch (family-relationship words vs. planned "personality & character traits"); Speaking Skill grounded in source context rather than a directly quoted exchange |

**Set 2 (Lessons 5-8: Nature description, Craft-studio tour, Museum/exhibit-guide description, Atelier/workshop
profile) is planned only, not yet generated** - a second full rotation of topics for whenever this module is
retaught with fresh material, per the Lesson Plan's Sets note. Not needed to complete this module; Set 1 already
does that on its own.

All four Set 1 lessons' student packets (`.html`) are current against the Student Print Formatting Prompt
standard (Good to Know at the top, citebox at the point of watching, compact inline multiple-choice, real
picture placeholders, word banks positioned before their items, universal question numbering, full-width answer
lines, the `.match-row`/`.qitem`/`.num` consistency fixes) - see that prompt's own changelog for the complete
list. Not yet reviewed against a printed page.

**Set 1's Listening/Speaking Assessment:** `lessons/intermediate/Module_1/Set_1/Set1_Intermediate_Assessment.md`.
Part A (Listening) uses **2 new, verified real clips** (the current prompt's multi-clip design): "Visitors Laugh
Away Troubles at the HaHaHouse Museum" (VOA Learning English, a real laughter museum in Zagreb, Croatia) and
"Researchers Uncover a Bathhouse Complex in Ancient Pompeii" (VOA Learning English, a real excavated Roman
bathhouse) - both distinct from all 4 taught sources and from each other, with items covering all four of the
Set's listening strategies (Main Ideas/Gist, Recognize Examples, Sequence Markers, Predict from Context). Every
item at every task Level is multiple choice, fill-in-the-blank, or matching (no open-ended items); vocabulary is
folded into the items themselves (pooled across the Set's 4 lessons), with no separate pre-teach list and no
notes-taking organizer. **Updated 2026-09-08, per user direction:** Part A's Listening Test grew from a flat
"approx. 40 MIN" to "approx. 45 MIN," lengthened with one genuine new item per clip block (Level 4 gains a Main
Ideas/Gist item on Golubic's pandemic-era origin story; Level 2 gains a Main Ideas/Gist item on the Pompeii
bathhouse), each grounded in an already-cited segment no prior item tested and verified against the real
transcript; new point totals 10/9/9/8 (was 8/9/7/8). Three word banks/matching lists also gained already-taught
distractor words not used as any answer (Level 2 +`bakery`; Level 3 +`sardine`/`waterproof`; Level 4 +`variety`),
per the prompt's new A.1 rule. Part B (Speaking) is a Teams Speaking Progress solo recording (Intermediate's
default mechanism), emphasizing Making Comparisons and Sequencing Language; each Level's prompt states concrete,
countable content requirements (feature/comparison/connector counts) rather than only a target length, and the
student packet shows a short self-check checklist derived from that Level's rubric (not the rubric itself) on
its card, with no submission-mechanism info printed. Not yet given to a real class, so treat
every number in it (period length, item counts, target recording lengths) as a reasoned starting point pending
real classroom feedback, per the prompt's own open items.

**Student-facing packet:** `lessons/intermediate/Module_1/Set_1/Set1_Intermediate_Assessment_Packet.html`, generated
against `Generate_Assessment_Student_Packet_Prompt_v2.1.md` - a Listening Test section (one printable page per
task Level) and a Speaking Task section (a plain instruction card per Level), with every answer key, point
value, holistic pass note, and rubric stripped. Not yet reviewed against a printed page, same as the six lesson
packets.

## Module 1 progress, Advanced Band (Describing, Advanced)

Plan approved and logged: `lessons/advanced/Module_1/Module1_Advanced_Lesson_Plan.md`. Task Levels
4, 5, 6, 7 (Advanced band). Level 7's Listening objective needs two real sources on the same subject (compare
rhetorical framing) - flagged per lesson with a suggested angle in the plan. **Set 1 complete (Lessons 1-4, 4 of
4 generated)**; **Set 2 (Lessons 5-8) is planned only**:

| File                                                                                                    | Lesson # | Real source(s)                                                                                                                                                                         | Status                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Module_1/Set_1/Lesson_1_LostKitchen/Lesson1_LostKitchen.md`             | 1        | Primary: PBS NewsHour feature on Erin French/The Lost Kitchen (Freedom, Maine). Secondary (Level 7 excerpt only): Radio Cherry Bombe podcast interview with Erin French.               | Current, per the Lesson prompt's fifth-addendum mapping table. No task, quote, vocabulary item, or differentiated activity was cut, only reorganized |
| `Module_1/Set_1/Lesson_2_LivingTextbooks/Lesson2_LivingTextbooks.md`     | 2        | Primary: PBS NewsHour Weekend feature on Phoenix mid-century modern preservation. Secondary (Level 7 excerpt only): Modern Phoenix's Beadle Archive page on the White Gates Residence. | Current, same treatment as Lesson 1                                                                                                                    |
| `Module_1/Set_1/Lesson_3_KeyDeer/Lesson3_KeyDeer.md`                     | 3        | Primary: PBS News Weekend "Saving Species" feature on the Key deer and the National Key Deer Refuge (Florida Keys). Secondary (Level 7 excerpt only): U.S. Fish & Wildlife Service's official National Key Deer Refuge pages. | Current - generated fresh against v1.1, current 2-day architecture from the start, no restructure needed |
| `Module_1/Set_1/Lesson_4_GlassBender/Lesson4_GlassBender.md`             | 4        | Primary: Idaho Public Television's *createid* series, "Glass Bender: Wil Kirkman" (Rocket Neon, Boise). Secondary (Level 7 excerpt only): Boise Art Scene's written interview with Wil Kirkman. | Current - generated fresh against v1.1, current 2-day architecture from the start, no restructure needed. Completes Set 1. |

All four lessons above follow the current Day 1 (Unit A)/Day 2 (Unit B) architecture, and their student packets
match the current Student Print Formatting Prompt conventions (Good to Know at the top, citebox at the point of
watching, compact inline multiple-choice, real picture placeholders, word banks positioned before their items,
multi-source Task D layout for Level 7, upside-down Closing Transfer Check script) - see the Rotation Log's
Advanced Band section for the full note.

**Set 1 is now complete**, and its assessment has now been generated too. Set 2 (Lessons 5-8, a fresh rotation,
not yet needed to complete the module) remains the only unstarted next step for this Band.

**Set 1's Listening/Speaking Assessment:** `lessons/advanced/Module_1/Set_1/Set1_Advanced_Assessment.md`. Generated
2026-09-01 against an earlier draft of `Generate_Assessment_Prompt_v2.md`; **fully regenerated 2026-09-08**
against the current design (redesigned four times in place 2026-09-07, after this Set's first pass) - the
original version used one source, a pre-taught vocabulary list, a free-form notes-organizer step, and several
open-ended items, all now retired. The regenerated version uses **2 new, verified real sources**: "Artists with
disabilities let their creativity soar at this Utah studio" (PBS News Weekend, Ali Rogin; Jump the Moon art
studio, Logan, Utah - carried over from the original version) and "The women lighthouse keepers who saved
countless lives from coast to coast" (PBS News Weekend, John Yang; Point Pinos Lighthouse and other U.S. sites) -
both distinct from all 4 taught sources and from each other, with tiered items covering all four of the Set's
listening strategies (Stated vs. Implied Opinion, Recognize Examples, Cause-and-Effect Language,
Signposting/Discourse Markers), every item restricted to multiple choice/fill-in-the-blank/matching, and
vocabulary (phenomenon, preservation, dwindle, trade - one pooled from each of the Set's 4 lessons) tested only
through the graded items. Level 7's item still draws on a second real source (the Utah Division of Arts &
Museums profile page used in the original version) for the same two-source comparative-framing task pattern
this Set's own Level 7 lesson items use. **Updated 2026-09-08, per user direction:** Part A's Listening Test grew
from a flat "approx. 40 MIN" to "approx. 45 MIN," lengthened with one genuine new item per clip block (a new
Level 6 Recognize Examples item on Alex and Lori Jenson's cow-drawing segment; a new Level 5 Stated vs. Implied
Opinion item on Emily Fish's logbook entries), each grounded in an already-cited segment no prior item tested and
verified against the real transcript; new point totals 11/9/8/8 (was 11/7/6/8). Level 4's vocabulary word bank
also gained one already-taught distractor word, `viable` (not the answer to any blank), per the prompt's new A.1
rule. Part B (Speaking) keeps its live solo presentation mechanism
(Advanced's default), same-task Teams-recording standing alternate, topic, and rubric structure from the
original version, with each Level's prompt now stating concrete, countable content requirements (feature
counts, hedging-phrase counts, self-repair/idiom requirements) instead of only a target length. This is the
first assessment regenerated against the current design for the Advanced band - not yet given to a real class,
so treat every number in it (period length, item counts, target recording/live lengths, live-presentation time
budget) as a reasoned starting point pending real classroom feedback, per the prompt's own open items.

**Student-facing packet:** `lessons/advanced/Module_1/Set_1/Set1_Advanced_Assessment_Packet.html`, regenerated 2026-09-08
against `Generate_Assessment_Student_Packet_Prompt_v2.1.md` - a Listening Test section (one printable page per task
Level, matching/fill-in-the-blank/multiple-choice items only, no vocabulary list, no notes organizer) and a
Speaking Task section (a plain instruction card per Level: topic, countable content requirements, target length,
and a self-check checklist derived from that Level's rubric Meets column), with every answer key, point value,
holistic pass note, rubric, and submission-mechanism detail (platform name, present/submit-by date) stripped.
Not yet reviewed against a printed page, same as the eight lesson packets and the Intermediate Set 1 assessment
packet.

**Lesson 1's TOEFL Track Tier variant (new 2026-09-07, revised four times same day after real
feedback):** `Module_1/Set_1_T/Lesson_1_LostKitchen/Lesson1_LostKitchen.md`, its matching
`LostKitchen_Advanced_L1_Packet.html`, and a third, teacher-only sibling file,
`LostKitchen_Advanced_L1_TOEFL_Homework.html` - a fork of `Module_1/Set_1/Lesson_1_LostKitchen/`'s own files,
generated against `Generate_Lesson_Prompt_v1.7.md` Section 0.6. Pass 1 (`1.1T.1.0`) added TOEFL content
only as a single alternate task at Level 7 (the band's highest task Level), isolated to Day 1 Phase 4 and
Day 2 Phase 2 - feedback was that this read as disconnected from the rest of the lesson. Pass 2
(`1.1T.1.1`) threaded TOEFL-relevant skill practice through most of both days instead: a one-sentence
"TOEFL Connection" note in Day 1 Phases 1 & 3 and Day 2 Phases 1 & 3 (teacher narration only); a
note-organizer tag column, an extra Inference question on the Day 1 transfer check, and a reframed Town
Hall turn on Day 2 (all in-class, opt-in, no individual timing needed); a Day 1 Phase 4 Listening
capstone (at that point an original Academic Talk passage faithful to the real PBS segment); and a Day 2
Phase 2 Speaking capstone split into an untimed in-class paired rehearsal plus a take-home page (at that
point still inside the main packet) carrying the real 7 Listen and Repeat sentences, 4 Take an Interview
questions, and TOEFL scoring guides - since the real individually-timed mechanics can't run live against
one student while the rest of a mixed class works a different differentiated task. Pass 3 (`1.1T.1.2`)
fixed a real flaw pass 2 still had in the Listening capstone: its invented Academic Talk passage needed a
teacher/partner to read it aloud *separately, just for TOEFL-track students* while everyone else worked
independently - the same shared-classroom-timing problem the Speaking capstone already solved, just not
yet applied here. The Listening capstone was rewritten to answer from the exact same real PBS segment
every student already heard together in Phase 2 - no separate passage, no separate reading, no pulling
anyone aside - and both capstones began rendering in the student packet as their own `Task D (TOEFL)`
block, styled like the regular lettered tasks, instead of a nested "option" callout. Pass 4 (`1.1T.1.3`)
moved the Speaking capstone's take-home content out of the main packet entirely, into the new
`LostKitchen_Advanced_L1_TOEFL_Homework.html` file - the in-class rehearsal's old pointer line ("the
take-home page is at the end of this packet") was dropped, since the homework file is now a wholly
separate document a teacher hands out on its own; the in-class box also dropped "no clock needed, just
practice the shape of the real thing" and gained an explicit, up-front reader/listener instruction. The
current pass (`1.1T.1.4`) redelivers D's homework as a real teacher-recorded audio assignment posted to
Teams, reusing the Assessment prompt's own "Teams Speaking Progress recording" mechanism: the teacher
records (or otherwise produces) audio of the 7 sentences/4 questions from the homework file's script,
posts it to Teams, and students listen once and record their own spoken response there, submitted by an
assigned date - so the homework file itself is now teacher-only (a recording script and scoring guide,
never shown to a student), its old "for your reading partner" framing dropped entirely. `Module_1/Set_1/
Lesson_1_LostKitchen/`'s own files are untouched - a class with no TOEFL-track students keeps using them
exactly as before; a class with TOEFL-interested students uses the `Module_1/Set_1_T/` copy instead. Not yet given
to a real class.

**Print formatting (student version), all current:**

- Intermediate Lesson 1: `Module_1/Set_1/Lesson_1_NewBakery/NewBakery_Intermediate_L1_Packet.html`.
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
  two-tag stack (`Listening & Speaking` / `Intermediate 1.1.1.0`, Unit 1A masthead only, matching
  LostKitchen's retrofit); Task A item 3's word bank moved from a trailing block after the whole
  list to inline with its item, matching Task B item 2.
- Intermediate Lesson 2: `Module_1/Set_1/Lesson_2_PortoFoodTour/PortoFoodTour_Intermediate_L2_Packet.html`. Same
  two-part structure; the Four-Corner Debate hook was translated into a plain "which sounds
  most like you" print activity rather than the live corner-moving version, and the Jigsaw protocol collapsed
  into three simultaneous small-group discussion prompts, per Section 1's translation rules. Fully synced
  2026-09-07 (had predated every hand-correction pass): added the `.masthead-meta` two-tag stack (`Listening &
  Speaking` / `Intermediate 1.1.2.0`, Unit 2A masthead only) and its CSS, including restoring `.masthead`'s
  `display: flex` layout; moved its one idiom ("in spite of") out of a `Phrase Spotlight` spotlight-box into a
  plain "Idioms to Know" block, matching NewBakery/LostKitchen; added the missing `.refresher`/`.refresher-noline`
  CSS the "Check What You Heard" upside-down box was already using in its markup; fixed `.task-block .instr-line`'s
  margin to 10px (was 4px) and restored `.idiom-item`/`.idiom-phrase`'s missing font properties; reflowed every
  multi-line `font-family` declaration onto one line.
- Intermediate Lesson 3: `Module_1/Set_1/Lesson_3_Backpack/Backpack_Intermediate_L3_Packet.html`. Fully synced 2026-09-07,
  same sweep as Lesson 2: added the `.masthead-meta` two-tag stack (`Intermediate 1.1.3.0`, Unit 3A masthead only)
  and its CSS/`.masthead` flex layout; added the missing `.refresher`/`.refresher-noline` CSS its two upside-down
  boxes (the Mystery Quote reveal and "Check What You Heard") were already using; fixed `.task-block .instr-line`'s
  margin to 10px and restored `.idiom-item`/`.idiom-phrase`'s font properties (unused in this lesson - no idiom in
  the source - but kept in sync for stylesheet consistency); reflowed every multi-line `font-family` declaration.
  **2026-09-08:** raw media assets added to this lesson's folder and renamed to match the new naming convention
  (`shared/Program_Conventions.md` §H): `Lesson3_Backpack_Img_Hook.webp` (the Mystery Quote hook's cropped
  hip-belt photo), `Lesson3_Backpack_Img_ChoiceBackpack.jpg`/`Img_ChoiceBicycle.jpg`/`Img_ChoiceTent.webp` (the
  three answer-choice images for Day 1 Phase 4's Level 2 "backpack/bicycle/tent" item), and a
  `Lesson3_Backpack_SourceVideo.webloc`/`.url` link-shortcut pair to the cited YouTube source video. None of
  these is embedded into `Lesson3_Backpack.md` or the packet HTML yet (the packet still uses a placeholder for
  the Mystery Quote photo and no images for the Level 2 choice item) - that integration is still pending, see
  Pending work.
- Intermediate Lesson 4: `Module_1/Set_1/Lesson_4_GreatGrandmother/GreatGrandmother_Intermediate_L4_Packet.html`. Fully
  synced 2026-09-07, same sweep as Lessons 2-3: added the `.masthead-meta` two-tag stack (`Intermediate 1.1.4.0`,
  Unit 4A masthead only) and its CSS/`.masthead` flex layout; realigned `.vocab-list .word`'s column width to
  the shared 130px (was locally widened to 150px), the same drift LostKitchen had; added the missing
  `.refresher`/`.refresher-noline` CSS the "Check What Happens" upside-down box was already using; fixed
  `.task-block .instr-line`'s margin to 10px and restored `.idiom-item`/`.idiom-phrase`'s font properties (unused
  - no idiom in this source); reflowed every multi-line `font-family` declaration, including the lesson's own
  `.kwl-table` extension class. **2026-09-08, bumped to `1.1.4.1`:** four content fixes per user review - the
  `.vocab-list .word` width corrected again (this time at the shared style-guide level, 165px fixed `width`,
  since 130px was itself too narrow for "great-grandmother"), the redundant Task C matching question removed,
  Task A's starter box reordered above the instruction referencing it, and the "Finish the K-W-L Chart" heading
  renamed to "Finish the Chart" - see `Rotation_Log_Intermediate.md` and `Changelog.md`.
- Advanced Lesson 1: `Module_1/Set_1/Lesson_1_LostKitchen/LostKitchen_Advanced_L1_Packet.html`.
  Same structure as the Intermediate packets, plus one
  pattern the Intermediate ones don't need: Level 7's star task (Task D, both halves) compares two real sources
  directly inside the task block, using a labeled two-part excerpt layout kept within the fair-use ceiling, per
  the Print Formatting Prompt's Section 2.7 multi-source guidance. Hand-corrected 2026-09-06: added the
  `.masthead-tag` (Unit 1A masthead only, per the shared style guide's rule - an earlier pass had
  mistakenly also placed it on the Unit 1B masthead, now removed); realigned `.vocab-list .word`'s
  column width to the shared stylesheet's 130px (was locally widened to 150px); added the
  `.refresher`/`.refresher-noline` CSS the "Check What You Heard" upside-down answer box was
  already using in its markup but had no rule for.
- Advanced Lesson 2: `Module_1/Set_1/Lesson_2_LivingTextbooks/LivingTextbooks_Advanced_L2_Packet.html`.
  Same two-part structure; Task D again uses the
  multi-source compare-pair pattern (news segment vs. an archive website), introducing the second source inline
  within the task itself per the "never name an unintroduced source" rule. Fully synced 2026-09-07 (this
  packet had predated every hand-correction pass): added the `.masthead-meta` two-tag stack (Unit 2A
  masthead only); converted its two idioms from plain `.idiom-item` paragraphs under "Phrases to Know" to
  the `.idiom-list`/`.irow` numbered table under "Idioms to Know"; realigned `.vocab-list .word`'s column
  width to 130px (was 150px); restored `.idiom-item`/`.idiom-phrase`'s missing font properties; fixed
  `.task-block .instr-line`'s margin to 10px (was 4px); added the missing `.refresher`/`.refresher-noline`
  CSS the "Check What You Heard" upside-down box was already using in its markup; reflowed every
  multi-line `font-family` declaration onto one line per the style guide's formatting convention. Its idiom
  table was reverted 2026-09-08 to the `.spotlight-box`/`.idiom-item` "Phrase Spotlight" treatment, per the
  retired idiom-table rule (see `Changelog.md`).
- Advanced Lesson 3: `Module_1/Set_1/Lesson_3_KeyDeer/KeyDeer_Advanced_L3_Packet.html`. Same two-part structure;
  Task D again uses the multi-source compare-pair pattern (news segment vs. the refuge's own official
  government page), introducing the second source inline within the task itself. Generated fresh against
  the current spec, so it already carried the `.masthead-meta` stack and `.idiom-list`/`.irow` table (two
  idioms) from the start. Its idiom table was reverted 2026-09-08 to the `.spotlight-box`/`.idiom-item`
  "Phrase Spotlight" treatment, per the retired idiom-table rule (see `Changelog.md`).
- Advanced Lesson 4: `Module_1/Set_1/Lesson_4_GlassBender/GlassBender_Advanced_L4_Packet.html`. Same two-part
  structure; Task D again uses the multi-source compare-pair pattern (video profile vs. the artist's own
  written interview), introducing the second source inline within the task itself. Generated fresh
  against the current spec, so it already carried the `.masthead-meta` stack and `.idiom-list`/`.irow`
  table (three idioms) from the start. Its idiom table was reverted 2026-09-08 to the
  `.spotlight-box`/`.idiom-item` "Phrase Spotlight" treatment, per the retired idiom-table rule (see
  `Changelog.md`). Completes Set 1's packets.
  None of the eight packets has been reviewed against a printed page yet.

## Module 1 progress, Proficient Band (Describing, Proficient)

Plan approved and logged: `lessons/proficient/Module_1/Module1_Proficient_Lesson_Plan.md`, `Rotation_Log_Proficient.md`
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

**Print formatting (student version):** `Module_1/Set_1/Lesson_1_LowerNinthWard/LowerNinthWard_Proficient_L1_Packet.html`,
generated fresh against the then-current Student Print Formatting Prompt spec (masthead-meta stack,
idiom-table format, Four-Corner Debate translated to a plain circle-your-answer print activity, multi-source Task
C compare-pair layout for Level 7, upside-down Closing Transfer Check script). Its idiom table (one idiom,
"mixed blessing") was reverted 2026-09-08 to the `.spotlight-box`/`.idiom-item` "Phrase Spotlight" treatment,
per the retired idiom-table rule (see `Changelog.md`). Not yet reviewed against a printed page, same as every
other packet in this family.

Next step for this Band: run `Generate_Lesson_Prompt_v2.1.md` for Lesson 2 against the approved plan, one lesson
at a time, per the Generation workflow below.

## Generation workflow (current)

**Step 1 - Plan the module.** Run `Generate_Module_Lesson_Plan_Prompt_v2.1.md` for the
target Module and Band. It reads the Rotation Log first (`Rotation_Log.md` plus that Band's own
`Rotation_Log_<Band>.md`), produces the module's plan table (4 rows by
default), and runs its self-check. Review and approve the plan before
generating any lesson content. Once approved, append its Rotation Log entry to that Band's `Rotation_Log_<Band>.md`.

**Step 2 - Generate lessons.** Run `Generate_Lesson_Prompt_v2.1.md` (pasted with
`shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`) against the approved plan. Because each lesson now requires finding and verifying a real source (not just writing to a word-count
ceiling), generate **one lesson at a time** for this family rather than Passage Reading's two-at-a-time pacing,
at least until the sourcing step has proven reliable enough to batch. As of v1.3, generate three artifacts per
lesson, in order: the source's `<Slug>_Transcript.md` (full real transcript, verbatim, teacher-only), then the
lesson `.md`, then its student packet `.html`. Check each lesson's self-check (runtime/citation/task-Level/
transcript-file checks) before moving to the next.

**Step 3 - Assess.** Once a Set (4 lessons) is complete, run `Generate_Assessment_Prompt_v2.md` for that Set - both Part A (Listening) and Part B (Speaking) run every Set, not staggered. Part B's
mechanism depends on the Band: Beginner/Intermediate produce a scored Teams Speaking Progress recording task
(the formal assessment itself); Advanced/Proficient produce a live presentation task plus a same-task
Teams-recording alternate for standing use (e.g. an absence). See that prompt's own scope notes (Section B.0-B.1).

**Step 4 - TOEFL Track Tier (optional, per Set).** When a TOEFL-capable variant of a completed Set is
wanted, run `Generate_TOEFL_Track_Tier_Prompt_v1.md` (pasted with the three shared files) against each of that
Set's already-generated lessons, forking the result into a sibling `Set_<N>_T/` folder rather than editing the
existing `Set_<N>/` files in place. As of v1.4, this threads TOEFL-relevant skill practice through most of both
days (a teacher-narrated connection in Phases 1/3 of each day, three small in-class touchpoints, and a
capstone task per day - the Day 2 capstone split into an untimed in-class rehearsal plus a take-home
Partner/Family Reader Copy) rather than one isolated task, for the band's highest task Level
(Advanced/Proficient bands only) - a class can pick per student how deep into the TOEFL Track that
Level's student goes. Version the fork's lesson docs/packets `<Module>.<Set>T.<Lesson>.<Version>`, bumping
the version on any substantive revision. Not staggered against Step 3; run whenever a TOEFL-capable variant
is actually wanted, not automatically for every Set.

**Step 5+ - not yet built.** Homework and the Part 2/presentation-project extension remain pending (see below).

## Pending work

- **Objective as a student can-do (Style Guide v2.10, 2026-09-08):** every existing packet's objective opens with
  a bare verb ("Objective: describe...", "Objective: listen for..."), the form the Style Guide retired in favor
  of "I can" plus the skill in the student's voice. Rewrite each as "I can ..." when its packet is next
  regenerated; this lesson type's packet prompt was not bumped for it and should state the §E form when next
  revised.
- **Self-contained rule backlog (Quality Standards §D8, 2026-09-08):** these packets still carry empty `.pic-box`
  grids, "[TEACHER: insert photo ...]" notes, or a "hold up real objects" hook, to be replaced by embedded images
  or a real-object redesign when each is next touched: `WhatIsIt_Beginner_L1_Packet.html` (18 empty boxes plus
  the real-objects hook in its `.md`), `NewBakery_Intermediate_L1_Packet.html` (two photo notes),
  `PortoFoodTour_Intermediate_L2_Packet.html` (photo note plus three boxes), `LivingTextbooks_Advanced_L2_Packet.html`
  (one box), `GreatGrandmother_Intermediate_L4_Packet.html` (three boxes), `Backpack_Intermediate_L3_Packet.html`
  (three remaining boxes; its hook and choice images are already embedded), and
  `Set1_Intermediate_Assessment_Packet.html` (three boxes on a graded item).

- **Backfill transcript files for the 9 lessons generated before v1.3's requirement** - the
  `<Slug>_Transcript.md` file (Section 0.3, item 7) is going-forward only as of 2026-09-07; these 9
  lessons predate it and don't have one yet. Each needs the source re-fetched to confirm the full
  real transcript, not just re-derived from the existing lesson `.md`'s own short quotes:
  Beginner `Module_1/Set_1/Lesson_1_WhatIsIt/`; Intermediate `Module_1/Set_1/Lesson_1_NewBakery/`,
  `Module_1/Set_1/Lesson_2_PortoFoodTour/`, `Module_1/Set_1/Lesson_3_Backpack/`, `Module_1/Set_1/Lesson_4_GreatGrandmother/`;
  Advanced `Module_1/Set_1/Lesson_1_LostKitchen/`, `Module_1/Set_1/Lesson_2_LivingTextbooks/`,
  `Module_1/Set_1/Lesson_3_KeyDeer/`, `Module_1/Set_1/Lesson_4_GlassBender/` (all under their respective
  `lessons/<band>/` root). Proficient Lesson 1 (`Lower Ninth Ward`) was generated before v1.3 too and
  belongs on this list once confirmed.
- **Generate Proficient Module 1 Set 1's remaining lessons (2-4)** - Lesson 1 is generated; Lessons 2-4 are still
  planned only. Run `Generate_Lesson_Prompt_v2.1.md` one lesson at a time, per the Generation workflow below,
  applying the same Level 7 two-source pattern and Level 8 withheld-content source each time.
- **Give both Set 1 assessments to a real class** - Intermediate Set 1's and Advanced Set 1's assessments are
  both generated but neither has been field-tested. Once given, expect addenda the same way the Lesson prompt
  got five.
- **Homework Generation Prompt** - not started. Will need its own rules given a homework assignment can't
  hand a student the full copyrighted transcript the way Passage Reading homework reuses the anchor text.
- **Generate any future Set's assessment** - once Set 2 (either Band) is generated, run
  `Generate_Assessment_Prompt_v2.md` and `Generate_Assessment_Student_Packet_Prompt_v2.1.md` against it, the same
  way both were just run for Advanced Set 1.
- **Part 2 + Presentation Project Extension** - not started. Planned to mirror the content sample's second
  (video) source, cross-source synthesis, and group-presentation assignment, as an optional add-on after a core
  lesson is complete - a genuinely separate, sit-on-top document (unlike the TOEFL Track Tier mechanism above,
  which is embedded directly in the lesson).
- **Generate TOEFL Track Tier forks for the remaining Set 1 lessons** - only Advanced Lesson 1 (LostKitchen) has
  a `Module_1/Set_1_T/` fork so far. Advanced Lessons 2-4 and any completed Proficient-band lesson are equally eligible
  (`Generate_TOEFL_Track_Tier_Prompt_v1.md`: Advanced/Proficient bands only); fork on request, not automatically for every lesson.
- **Give the `Module_1/Set_1_T` Lesson 1 fork to a real class** - like every other assessment/extension artifact in this
  family, it hasn't been field-tested yet; expect the same kind of addenda the Lesson and Assessment prompts
  picked up after their own first real uses.
- **Embed Lesson 3 Backpack's real images into the lesson content** - `Lesson3_Backpack_Img_Hook.webp` and the
  three `Img_Choice*` files (see the Intermediate Lesson 3 print-formatting note above) are renamed and sitting
  in the lesson folder but not yet wired into `Lesson3_Backpack.md` or `Backpack_Intermediate_L3_Packet.html`
  (the packet still uses a generic "real picture placeholder" for the Mystery Quote hook and no image for the
  Day 1 Phase 4 Level 2 choice item).
