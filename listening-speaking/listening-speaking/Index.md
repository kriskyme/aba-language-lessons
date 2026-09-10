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
| `Generate_Lesson_Prompt_v2.6.md` | Generates one lesson (a 2-day cycle: Day 1 Listening, Day 2 Speaking): sources a real audio/video text, builds tiered listening and speaking tasks around it, and produces three artifacts in order (transcript file, lesson `.md`, packet `.html`). Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; states only what is true of a real-source lesson (Section 0.2 runtime/pace/register ceilings, 0.3 sourcing and fair-use rules and the transcript file, 0.4 rotation banks, the six-phase Day 1 and five-phase Day 2 structure) and points to the shared files for everything modality-neutral. Section 0.5's self-check is the shared Quality Standards §F list plus 16 Listening/Speaking-only items. The TOEFL Track Tier (formerly Section 0.6) now lives in its own companion prompt, next row. | Current (v2.6, 2026-09-10: Day 1 runs Quality Standards §D12's three beats, so it is six phases rather than five - the clip plays twice with no wording on the page (Phases 2 and 4, the second under a narrower stated purpose), then a new Phase 5 prints one or two bounded verification windows of the source's real words and ends on a covered-window replay; §0.3 item 4 carves out those windows at two per lesson, six lines or eighty words each, and item 8 no longer keeps the transcript wholly out of the packet; v2.5, same day: §0.3 item 7 requires a two-source task to print both sources' own words in the `.md`, paired by subject, to Quality Standards §C9's floor; v2.4, 2026-09-09: the Phase 1 hook and Phase 3 protocol banks take their room-neutral names, per Quality Standards §D11 - see `Changelog.md`); thirteen real lessons generated (Beginner 1, Intermediate 1-4, Advanced 1-4 against v1.1-v1.10, Advanced 5-8 against v2.5), all on the 2-day cycle; **no generated lesson yet carries the §D12 beats** and the transcript-file requirement is going-forward only too - both backlogged by name, see Pending work |
| `Generate_TOEFL_Track_Tier_Prompt_v1.1.md` | Generates a TOEFL-capable variant of an already-generated Advanced/Proficient Set, forked into a sibling `Set_<N>_T/` folder (never editing the base files): four touchpoint kinds threaded through both days - (A) teacher-only "TOEFL Connection" framing in Phases 1 and 3 of each day, (B) three in-class touchpoints on the class's shared pacing (organizer column, extra transfer-check question, reframed protocol turn), (C) a Listening capstone answered from the same shared source, (D) a Speaking capstone split into an untimed in-class rehearsal plus a teacher-recorded Teams homework whose script and scoring guides live in a separate teacher-only `_TOEFL_Homework.html` file. Section 1 is the lesson side, Section 2 the packet rendering (the former 2.6a/2.7a/2.8a/2.10a/2.10b/2.11a of the Student Packet prompt), Section 3 the self-check. Extracted 2026-09-08 from the Lesson prompt's Section 0.6 and the packet prompt's TOEFL sub-sections, mirroring how Passage Reading keeps its TOEFL extension as a separate companion. | Current (v1); one fork generated under the old embedded mechanism (Advanced Set 1 Lesson 1, `Module_1/Set_1_T/`, `1.1T.1.4`), content unchanged by the extraction |
| `Generate_Module_Lesson_Plan_Prompt_v2.1.md` | Plans **one Set** (4 lessons: topic directions, content-format/strategy/skill/hook/protocol rotation, vocabulary themes, task-Level-to-objective mapping with both CSV halves named) before any lesson is generated. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; Rotation Log mechanics and adjacency rules point to Conventions §F; the 2026-09-03 8-lesson correction narrative and the "same as Passage Reading" cross-references are gone. Listening/Speaking objectives only. | Current (v2.1) |
| `Rotation_Log.md`                                                     | Overview only as of the per-Band split: purpose, the cross-Band historical notes (day-count correction, Sets/Assessment-prompt introductions), and links to each Band's own log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | N/A (data, not a prompt) |
| `Rotation_Log_Intermediate.md`                                        | Running record of every approved Intermediate-Band Set's format/strategy/skill/hook/protocol/vocabulary/topic choices, one subsection per Set. Read before planning a new Set; appended to after approval.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Module 1 Sets 1-2; Module 2 Set 1 |
| `Rotation_Log_Advanced.md`                                            | Same, for the Advanced Band. A new Band's file is created lazily the first time a lesson in that Band is generated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Module 1 Set 1/Set 2; Module 2 Set 1 (planned 2026-09-10, first table in this file to carry the `Version` column) |
| `Rotation_Log_Proficient.md`                                          | Same, for the Proficient Band. Created 2026-09-07 - the first Band file created purely from a plan, before any lesson in the Band had been generated; Lesson 1 generated the same day.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1 (Lesson 1 of 4 generated) |
| `Rotation_Log_Beginner.md`                                            | Same, for the Beginner Band. Created 2026-09-07.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set 1 complete (Lessons 1-4 generated) |
| `Changelog.md`                                                        | Version history for this prompt family. Not a prompt itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | N/A (data, not a prompt)                                                                                                                                                                                            |
| `Generate_Student_Packet_Prompt_v2.7.md` | Takes one completed lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML) in two parts (Unit _A Listening / Unit _B Speaking). Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; states only what is specific to a Listening/Speaking packet (the citebox and its placement and media-type wording, Good to Know boxes front-loaded, the Listening Notes organizer, fixed-frame and multi-source task rules, the Check It Against the Source block, the STOP-badged "Don't read ahead" callout and the upside-down Check What You Heard script, Learn the Phrase, `.qitem`-numbered Discuss It, jargon-free closing headings) and points to the Style Guide for the translation table, star and lettered-Task rules, the regeneration rule, the delta CSS (now §H.1 there, moved out of this prompt), and the shared packet self-check. TOEFL Track Tier rendering moved to `Generate_TOEFL_Track_Tier_Prompt_v1.1.md` Section 2. Section 5 is Style Guide §I plus 11 Listening/Speaking items. | Current (v2.7, 2026-09-10: new Section 2.8 "Check It Against the Source" prints the lesson's Day 1 Phase 5 verification windows in `.verify-window`, always after the response spaces of every task they could answer, and the input rule now lets that one bounded part of the transcript reach the packet; former 2.8-2.13 renumbered to 2.9-2.14; v2.6, 2026-09-09: both masthead sections carry the meta stack; v2.5, same day: "Don't read ahead" in a `.stop-flag` callout with a STOP badge; v2.4, same day: the Level 7 compare layout prints at least three verbatim excerpts per source on shared subjects, in one of the Style Guide's two layouts, on top of v2.3's Answer notes stripped, stems carried without answer-stating parentheticals, compare layout holds source content not the contrast - see `Changelog.md`); every packet under `lessons/` was generated against v1.3-v1.10 and hand-swept to the shared conventions in earlier passes (see `Changelog.md`); all 11 carry the two-line `.masthead-meta` stack (modality `·` Module name, then Band and version code) on both mastheads and the STOP-badged "Don't read ahead" callout as of 2026-09-09 |
| `Generate_Assessment_Prompt_v2.1.md` | Generates a Set's Listening (Part A) and Speaking (Part B) assessments. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; keeps what is Listening/Speaking-specific (2-3 new real clips sourced like a lesson's, vocabulary pooled across the Set and tested only inside items, objective-only formats, the single-period structure, Part B's mechanism-by-band table and countable content requirements, the 3-point rubric) and points to Quality Standards §C for item quality, which now carries the distractor, padded-bank, and time-balance rules this prompt introduced program-wide. Self-checks are Quality Standards §F plus 8 Part A and 6 Part B items. | Current (v2); two assessments generated under v1 (Intermediate and Advanced Set 1) |
| `Generate_Assessment_Student_Packet_Prompt_v2.1.md` | Takes a completed Assessment and produces the student handout: Listening Test pages per Level with a citebox per clip, Speaking Task cards with the rubric's Meets column as a `.checklist` (now Style Guide §H.4), no answer keys, rubric tables, or submission information. Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; Section 5 is Style Guide §I plus 6 items. | Current (v2); two packets generated under v1 |
| `learningobjectives.csv` (project file, shared with Passage Reading) | Source of truth for every Learning Objective, including the Listening/Speaking modality rows this family pulls from.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | N/A (data)                                                                                                                                                                                                          |

Not yet started for this family: a homework-generation prompt and the Part-2/presentation-project extension
described above. See Pending work.

## Module 1 progress, Beginner Band (Describing, Beginner)

Plan approved and logged: `lessons/beginner/Module_1/Module1_Beginner_Lesson_Plan.md`,
`Rotation_Log_Beginner.md` (new file - the first Set ever planned for this Band). Task Levels 1, 2,
3 (Beginner band; only 3, not 4, since Level 1 is the scale's floor). Source calibrated to Level 1
(30 sec-2 min, graded-for-absolute-beginners clip). **Set 1 plan approved 2026-09-07; Set 1 complete
(Lessons 1-4 generated):**

| File | Lesson # | Real source | Status |
| --- | --- | --- | --- |
| `Module_1/Set_1/Lesson_1_WhatIsIt/Lesson1_WhatIsIt.md` | 1 | "Let's Learn English - Level 1 - Lesson 4: What Is It?", VOA Learning English (characters Anna, Pete, Marsha) | Current. Flagged deviations: runtime (~5:00 vs. the 30 sec-2 min Level 1 target; kept as Section 0.2's own named Level 1 platform); Speaking Skill (Giving Examples) grounded in source context rather than a directly quoted exchange |
| `Module_1/Set_1/Lesson_2_AreYouBusy/Lesson2_AreYouBusy.md` | 2 | "Let's Learn English - Level 1 - Lesson 8: Are You Busy?", VOA Learning English (Anna, Anne, Jonathan, Amelia, Caty) | Current. Anchors on the page's 1:58 Conversation audio, so **no runtime deviation** and the Speaking Skill is quoted directly from the real speakers. One deviation flagged: the CSV's Level 2/3 object frames ("It is ___.") are instantiated as person-and-time frames, since this lesson's topic is a routine. First Beginner lesson with a transcript file and embedded cited images |
| `Module_1/Set_1/Lesson_3_FamilyPhotos/Lesson3_FamilyPhotos.md` | 3 | "Starting Out, Episode 09 - Family photos", British Council LearnEnglish (Julia and Sammy) | Current. **First non-VOA source in this Set**, resolving the same-series repeat Lesson 2 flagged; script confirmed three independent ways. Three deviations flagged: runtime not stated by the source and unverifiable (est. 1:30-2:00); page level reads "A1 Elementary / A2 Pre-intermediate", somewhat above the Level 1 register ceiling; two adults in dialogue rather than the planned child or narrator |
| `Module_1/Set_1/Lesson_4_HowAboutThis/Lesson4_HowAboutThis.md` | 4 | "Let's Learn English - Level 1 - Lesson 14: How About This?", VOA Learning English (Anna and Genie) | Current. **Row amended before generation** for Style Guide v2.27 §A.2: the planned "Colors & shapes" theme became **Sizes & fit**, since no item may be answered by reading a chromatic colour off a printed picture and no A1 shapes clip with a verifiable transcript exists. Three deviations flagged: ~5:00 runtime; topic narrowed twice from the approved row; third clip from the same VOA Level 1 series |

**Lesson 4's artifacts:** `Module_1/Set_1/Lesson_4_HowAboutThis/` holds all three -
`HowAboutThis_Transcript.md`, `Lesson4_HowAboutThis.md`, and `HowAboutThis_Beginner_L4_Packet.html`.
**This is the lesson Style Guide v2.27 §A.2 reshaped.** Its approved row read "Colors and shapes of
common items"; §A.2 (added the same day, while Passage Reading's Beginner Set was being generated)
forbids any item answered by reading a chromatic colour off a printed picture, because packets print
in grayscale. The row moved first to shapes and sizes, mirroring how Reading fixed its own colour
lesson, and then to **sizes & fit** once neither shapes candidate could clear the transcript bar:
Oxford University Press's "It's a square!" is JavaScript-gated and returns an empty page body, so its
lyrics exist only in a search index, and PBS's "The Shapes Song" is an otherwise ideal 1:57 but prints
no transcript and exposes no caption file. Both were rejected rather than built on unverifiable
wording - the exact defect Lesson 1 carries. The VOA clip that was verifiable supplies a genuine size
scale (small / medium / large) and the Set's richest comparison language ("too small", "too large",
"more formal", "That's better"). Packet carries three embedded cited museum images (a dress, a
jacket, a hat) told apart by **outline alone** so they survive a grayscale print, "I can" objectives
on both Units, and three star-rated Tasks per Unit. Not yet reviewed against a printed page.

**Lesson 3's artifacts:** `Module_1/Set_1/Lesson_3_FamilyPhotos/` holds all three -
`FamilyPhotos_Transcript.md`, `Lesson3_FamilyPhotos.md`, and `FamilyPhotos_Beginner_L3_Packet.html`.
This is the Set's **first source from outside VOA's "Let's Learn English - Level 1"** and its first
British speaker. Its script is the best-verified in the repo: the lesson page returned a complete
transcript in one fetch, an independent second fetch returned identical text, and the episode's
official support-pack PDF was downloaded and its text extracted locally, confirming the same script,
the episode's own vocabulary list, and a 2017 copyright year the web page does not print. The clip is
also the Set's strongest **Asking for Clarification** model, because Julia's questions are genuine
repair moves on a misunderstanding rather than information-seeking questions. Packet carries three
embedded cited CC0 images (a nephew / a sister / a brother) with no empty picture boxes, "I can"
objectives on both Units, and three star-rated Tasks per Unit. Not yet reviewed against a printed page.

**Lesson 2's artifacts:** `Module_1/Set_1/Lesson_2_AreYouBusy/` holds all three -
`AreYouBusy_Transcript.md` (teacher-only, honest about the one reconstructed turn-ordering in the two
middle exchanges), `Lesson2_AreYouBusy.md`, and `AreYouBusy_Beginner_L2_Packet.html`, generated against
`Generate_Lesson_Prompt_v2.5.md` and `Generate_Student_Packet_Prompt_v2.6.md`. The packet is the first in
this Band built to the current standard throughout: "I can" objectives on both Units, the two-line
`.masthead-meta` stack on both mastheads, the STOP-badged "don't read ahead" callout, three star-rated
Tasks per Unit, and **three embedded cited Wikimedia Commons images with no empty picture boxes**.
Its three image assets are registered in the Set's new
`Module_1/Set_1/Set1_Beginner_Image_Credits.md`. Not yet reviewed against a printed page.

**Lesson 1's student packet:** `Module_1/Set_1/Lesson_1_WhatIsIt/WhatIsIt_Beginner_L1_Packet.html`, generated
against `Generate_Student_Packet_Prompt_v1.4.md` - two parts (Unit 1A Listening / Unit 1B Speaking),
each with 3 star-rated task blocks (Beginner has 3 task Levels, not 4), a plain citation box, a
2-column order-and-name Listening Notes organizer (adapted from the module's usual comparison
T-chart, since this source is a sequence of named objects rather than a two-category comparison),
and the upside-down Closing Transfer Check script. Not yet reviewed against a printed page.

Next steps for this Band: **regenerate Lesson 1** against `Generate_Lesson_Prompt_v2.5.md` (it is the
only lesson in the Set still carrying backlog items - see Pending work), then run
`Generate_Assessment_Prompt_v2.1.md` for the Set 1 assessment, now that all four lessons exist. The approved plan now also carries a slot-to-shape table for Section 0.6's
fixed-output task shapes across all four lessons, so each lesson's shapes are checked against the plan
rather than against its neighbours.

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

**Set 2 complete (generated 2026-09-10):** Lessons 5-8, a second full rotation of topics for whenever this
module is retaught with fresh material, per the Lesson Plan's Sets note. Not needed to complete this module;
Set 1 already does that on its own. (The Set 2 row block was approved and logged 2026-09-01 alongside Set 1;
this pass was Step 2 of the workflow, not a re-plan. An earlier line here described Lesson 8 as an
"Atelier/workshop profile"; the Lesson Plan and Rotation Log both say Travel/landmark description, a real
natural landmark, and they are the authoritative rotation record, so that is what was generated and the stale
wording is corrected here.)

| File | Lesson # | Real source | Status |
| --- | --- | --- | --- |
| `Module_1/Set_2/Lesson_5_IberianLynx/Lesson5_IberianLynx.md` | 5 | "Wild Cat Is Back from Near Extinction," VOA Learning English (the Iberian lynx) | Current, `1.2.5.0`. Flagged: runtime 5:29 against the 2-4 min Level 3 target, kept per Section 0.2's soft-target rule; the piece's recovery-effort layer is used only as opinion material, never as a describing task. Day 2's Level 2 Better-of-two pair was corrected the same day to Style Guide v2.27 (colour swapped for pattern), inside the same generation pass, so the version code did not move |
| `Module_1/Set_2/Lesson_6_TapestryFactory/Lesson6_TapestryFactory.md` | 6 | "Spanish Tapestry Factory Creating Pieces after 300 Years," VOA Learning English (Spain's Royal Tapestry Factory) | Current, `1.2.6.0`. Runtime 3:24, inside target. Flagged: a narrated report about a weaver's workshop rather than a first-person studio tour; the Day 2 speaking model is the narrator's real reported speech |
| `Module_1/Set_2/Lesson_7_RosettaStone/Lesson7_RosettaStone.md` | 7 | "Museum Marks Rosetta Stone's Role in Understanding Hieroglyphs," VOA Learning English | Current, `1.2.7.0`. Runtime 3:59, inside target. Flagged: three of six target words taken from the real transcript because the source glossary has only four entries, one of them off-theme; the interrupting half of the Day 2 skill is taught from frames |
| `Module_1/Set_2/Lesson_8_WrangellStElias/Lesson8_WrangellStElias.md` | 8 | "The Untouched Beauty of Wrangell-St. Elias National Park," VOA Learning English (America's National Parks) | Current, `1.2.8.0`. Flagged: full recording is 10:02, so the lesson is scoped to a defined opening portion of roughly 3:45 with a stated stopping line, marked in the transcript file and told to students in the packet |

Each Set 2 lesson folder holds all three artifacts in generation order: a verbatim `<Slug>_Transcript.md`
(teacher-only), the lesson `.md`, and the student packet `.html`, plus a `.webloc` shortcut to the source page
and the lesson's image assets. All four packets are built to the current standard: "I can" objectives on both
Units, the two-line `.masthead-meta` stack, Unit _A / Unit _B headings, the STOP-badged "don't read ahead"
callout with the script printed upside-down after the response space, four star-rated Tasks per listening unit,
every image really embedded with no empty picture boxes, and no undefined CSS selectors. Not yet reviewed
against a printed page.

**Set 2's image register:** `lessons/intermediate/Module_1/Set_2/Set2_Intermediate_Image_Credits.md` - all 12
images embedded across the four packets, one table per lesson with asset file, where used, Commons title,
author, license, and source URL (`shared/Program_Conventions.md` §D/§I). Packets print no credit.

All four Set 1 lessons' student packets (`.html`) are current against the Student Print Formatting Prompt
standard (Good to Know at the top, citebox at the point of watching, compact inline multiple-choice, real
picture placeholders, word banks positioned before their items, universal question numbering, full-width answer
lines, the `.match-row`/`.qitem`/`.num` consistency fixes) - see that prompt's own changelog for the complete
list. Not yet reviewed against a printed page.

**Set 1's image register:** `lessons/intermediate/Module_1/Set_1/Set1_Intermediate_Image_Credits.md` - every image
embedded in the four lessons' packets (19 today), one table per lesson with asset file, where used, Commons title,
author, license, and source URL (`shared/Program_Conventions.md` §D/§I). Packets print no credit.

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

## Module 2 progress, Intermediate Band (Narrating, Intermediate)

Plan approved and logged 2026-09-10: `lessons/intermediate/Module_2/Module2_Intermediate_Lesson_Plan.md`,
`Rotation_Log_Intermediate.md` (this Band's first Module 2 entry). Task Levels 2, 3, 4, 5, same as this Band's
Module 1; source calibrated to Level 3 (2-4 min). Set numbering and lesson numbering both restart for a new
Module (`shared/Program_Conventions.md` §C), so this is Set 1, Lessons 1-4, versioned `2.1.1.0`-`2.1.4.0`.
**Set 1: Lessons 1-2 of 4 generated (2026-09-10); Lessons 3-4 planned only:**

| Lesson # | Topic direction | Content format | Listening strategy | Speaking skill | Status |
| --- | --- | --- | --- | --- | --- |
| 1 | A first day at a new school, told by the person it happened to | Personal-story talk | Listen for Sequence Markers | Summarizing What Someone Said | Current (`Module_2/Set_1/Lesson_1_NewKid/`, `2.1.1.1`). Source: "A schoolmate saved him from a bully and changed his life," NPR's "My Unsung Hero" (Darrell Barber, 2:55, audio only). Flagged deviations: vocabulary theme (the source's real words are about being new, not the planned "arrival & journey words"); no published timestamps, so the source's own four-part structure labels the segments; three register features slightly above the Level 3 ceiling |
| 2 | A rescue or emergency told by someone who was there | Oral-history interview clip (swapped with Lesson 4) | Predict from Context Before Confirming | Asking for Clarification | Current (`Module_2/Set_1/Lesson_2_FireRescue/`, `2.1.2.0`). Source: "LA firefighter tells woman he saved 30 years ago that she helped him in tough times," StoryCorps on NPR (Derek Bart and Myeshia Oates, 3:15, audio only). Flagged deviations: the first listen stops at the prediction point rather than playing the whole clip, since the assigned strategy needs the ending withheld; two fire-service terms and the speaker's present-tense storytelling sit above the Level 3 ceiling, none taught or tested; no published timestamps, so the source's own four-part structure labels the segments |
| 3 | How someone got an unusual job or started something | Storytelling-podcast episode | Listen for Cause-and-Effect Language | Giving Examples | Not yet sourced - planned only |
| 4 | An older person's account of one remembered day | First-hand/eyewitness news account (swapped with Lesson 2) | Listen for Stated vs. Implied Opinion | Hedging an Opinion | Not yet sourced - planned only |

The plan also fixes the Set-wide note-taking organizer (sequence chain, the Narrating match) and the Level 2
slot-to-shape assignment the Lesson prompt's §0.6 requires, and flags two deviations rather than resolving
them silently: Level 2's two production shapes necessarily repeat their slots across all four lessons, and
Lesson 4's topic mildly echoes Module 1 Set 1 Lesson 4's family-elder direction. See the plan and
`Rotation_Log_Intermediate.md` for both.

**Lesson 1's files:** `Lesson1_NewKid.md`, `NewKid_Transcript.md` (the full published NPR transcript,
teacher-only, saved in the same pass, so this lesson is not on the transcript-backfill list below), and
`NewKid_Intermediate_L1_Packet.html`. The packet was generated fresh against
`Generate_Student_Packet_Prompt_v2.6.md` and the current Style Guide, so it carries the two-line
`.masthead-meta` stack on both mastheads (`Listening & Speaking` dot `Narrating`, then `Intermediate
2.1.1.0`), the "I can" objective form, the STOP-badged "Don't read ahead" callout, and the upside-down Check
What You Heard script from the start. Its four embedded Wikimedia Commons photos (a locker row for the
opening photo; a moving truck, a school hallway, and a school cafeteria for the Level 2 and Level 3 picture
items) are registered in `Module_2/Set_1/Set1_Intermediate_Image_Credits.md`, created with this lesson. Not
yet reviewed against a printed page.

**Content bound for this Set (2026-09-10, per user direction):** no refugee, migration-status, or
displacement content in any of Set 1's four sources; an arrival story here is an everyday one (a new school,
job, or city). Two otherwise-suitable VOA Learning English refugee stories were rejected on this ground
during Lesson 1's search.

**Lesson 2's files:** `Lesson2_FireRescue.md`, `FireRescue_Transcript.md` (teacher-only), and
`FireRescue_Intermediate_L2_Packet.html`, generated 2026-09-10 with three cited Wikimedia Commons photos added
to `Module_2/Set_1/Set1_Intermediate_Image_Credits.md`. Its opening hook is a printed line from the clip rather
than a photo. **This is the first lesson in this family built to the six-phase Day 1**
(`Generate_Lesson_Prompt_v2.6.md` and `Generate_Student_Packet_Prompt_v2.7.md`, both released mid-pass that
day): the clip plays twice with nothing written on the page, answers are committed before the second listen,
and a Phase 5 verification window of 49 verbatim words (the "So I ran there, I grab her" stretch, chosen for
three word boundaries this Band mishears) prints after every listening task's response space and ends in the
covered-window replay. **Lesson 1 was retrofitted to the same shape later that day** (`2.1.1.0` to
`2.1.1.1`): its Day 1 is now six phases with the commit, second-listen and revise beats and a 35-word Phase 5
window from Segment 3 ("And after Reuben and his friends left ... never bothered me again"), chosen because
three of its own tasks turn on it and it carries three joins this Band mishears; no task, answer, or Day 2
content changed, and its packet was regenerated against the v2.7 spec. Neither lesson is on the §D12 backlog
below. Neither packet has been reviewed against a printed page.

**Content formats swapped between Lessons 2 and 4 (2026-09-10, per user direction):** the verified Lesson 2
source is an oral-history interview, so Lesson 2 took that format and Lesson 4 now needs a first-hand or
eyewitness news account. Adjacency still holds across all four lessons; the plan doc and
`Rotation_Log_Intermediate.md` carry the swap.

Next step for this Module/Band: generate Lesson 3 against the approved plan, one lesson at a time, per the
Generation workflow below.

## Module 1 progress, Advanced Band (Describing, Advanced)

Plan approved and logged: `lessons/advanced/Module_1/Module1_Advanced_Lesson_Plan.md`. Task Levels
4, 5, 6, 7 (Advanced band). Level 7's Listening objective needs two real sources on the same subject (compare
rhetorical framing) - flagged per lesson with a suggested angle in the plan. **Set 1 complete (Lessons 1-4, 4 of
4 generated)**; **Set 2 (Lessons 5-8) is complete, 4 of 4 generated and retrofitted to §D12; its assessment is now due**:

| File                                                                                                    | Lesson # | Real source(s)                                                                                                                                                                         | Status                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Module_1/Set_1/Lesson_1_LostKitchen/Lesson1_LostKitchen.md`             | 1        | Primary: PBS NewsHour feature on Erin French/The Lost Kitchen (Freedom, Maine). Secondary (Level 7 excerpt only): Radio Cherry Bombe podcast interview with Erin French.               | Current, per the Lesson prompt's fifth-addendum mapping table. No task, quote, vocabulary item, or differentiated activity was cut, only reorganized Stem sweep 2026-09-09 (Quality Standards §C9): Day 1 Phase 4 parentheticals moved to `Answer note:` lines, version bumped, packet Tasks B-D made to match. Task D rebuilt 2026-09-09 (Quality Standards §C9 enough-to-compare floor, `1.1.1.2`): four subject-paired rows of verbatim PBS/Cherry Bombe excerpts in the `.md` Level 7 task and the packet, replacing a one-sentence summary and three fragments. |
| `Module_1/Set_1/Lesson_2_LivingTextbooks/Lesson2_LivingTextbooks.md`     | 2        | Primary: PBS NewsHour Weekend feature on Phoenix mid-century modern preservation. Secondary (Level 7 excerpt only): Modern Phoenix's Beadle Archive page on the White Gates Residence. | Current, same treatment as Lesson 1 Stem sweep 2026-09-09 (Quality Standards §C9): Day 1 Phase 4 parentheticals moved to `Answer note:` lines, version bumped, packet Tasks B-D made to match. Task D rebuilt 2026-09-10 (Quality Standards §C9 enough-to-compare floor, `1.1.2.2`): three subject-paired rows (why these buildings are worth keeping, what the architecture is like, what happens when a building is threatened) of verbatim PBS transcript and Modern Phoenix archive excerpts, both re-fetched; 6 excerpts per source. `LivingTextbooks_Transcript.md` saved in the same pass. |
| `Module_1/Set_1/Lesson_3_KeyDeer/Lesson3_KeyDeer.md`                     | 3        | Primary: PBS News Weekend "Saving Species" feature on the Key deer and the National Key Deer Refuge (Florida Keys). Secondary (Level 7 excerpt only): U.S. Fish & Wildlife Service's official National Key Deer Refuge pages. | Current - generated fresh against v1.1, current 2-day architecture from the start, no restructure needed Stem sweep 2026-09-09 (Quality Standards §C9): Day 1 Phase 4 parentheticals moved to `Answer note:` lines, version bumped, packet Tasks B-D made to match. Task D rebuilt 2026-09-10 (Quality Standards §C9 enough-to-compare floor, `1.1.3.2`): four subject-paired rows (what the deer is and where it is found, the habitat, how the refuge began and what happened after, what puts the deer in danger now) of verbatim PBS transcript and U.S. Fish & Wildlife Service refuge-page excerpts, the refuge page re-fetched; 7 PBS and 6 refuge excerpts. |
| `Module_1/Set_1/Lesson_4_GlassBender/Lesson4_GlassBender.md`             | 4        | Primary: Idaho Public Television's *createid* series, "Glass Bender: Wil Kirkman" (Rocket Neon, Boise). Secondary (Level 7 excerpt only): Boise Art Scene's written interview with Wil Kirkman. | Current - generated fresh against v1.1, current 2-day architecture from the start, no restructure needed. Completes Set 1. **2026-09-09, bumped to `1.1.4.2`:** Day 2's Concentric Circles became Rotating Partners and Day 1's K-W-L Walk became the packet's own K-W-L Chart, per new Quality Standards §D11 (room-neutral participation); packet Discuss It and Before You Watch instructions reworded to match. Stem sweep 2026-09-09 (Quality Standards §C9): Day 1 Phase 4 parentheticals moved to `Answer note:` lines, version bumped, packet Tasks B-D made to match. Task D rebuilt 2026-09-10 (Quality Standards §C9 enough-to-compare floor, `1.1.4.3`): four subject-paired rows (doing the work by hand, why he makes it, neon next to LEDs, how much work there is) of verbatim video-caption and Boise Art Scene interview excerpts, both re-fetched; 7 excerpts per source. `GlassBender_Transcript.md` saved in the same pass. |

All four lessons above follow the current Day 1 (Unit A)/Day 2 (Unit B) architecture, and their student packets
match the current Student Print Formatting Prompt conventions (Good to Know at the top, citebox at the point of
watching, compact inline multiple-choice, real picture placeholders, word banks positioned before their items,
multi-source Task D layout for Level 7, upside-down Closing Transfer Check script) - see the Rotation Log's
Advanced Band section for the full note.

**Set 2 (Lessons 5-8, a fresh rotation) is complete as of 2026-09-10.** All four lessons are generated;
the Set's assessment is the remaining step:

| File                                                        | Lesson # | Real source(s)                                                                                                                                                                                                                                                                | Status                                                                                                                                                                              |
| ----------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Module_1/Set_2/Lesson_5_HighLine/Lesson5_HighLine.md`      | 5        | Primary: PBS NewsHour, "Above Manhattan's bustle, a reshaped public space" (Jeffrey Brown walking New York's High Line with its landscape architect James Corner; 2016-08-11, 6:32). Secondary (Level 7 excerpt only): TED2011, Robert Hammond, "Building a park in the sky" (5:24). | Current, generated 2026-09-10 against `Generate_Lesson_Prompt_v2.5.md` and `Generate_Student_Packet_Prompt_v2.6.md`, version `1.2.5.1`. Both sources spoken, both full transcripts fetched and saved teacher-only in `HighLine_Transcript.md`. Packet built with the "I can ..." objective, room-neutral hook and protocol names, and no teacher-prepared media, all applied by hand since neither prompt has been bumped for them. |
| `Module_1/Set_2/Lesson_6_GodsAndGoddesses/Lesson6_GodsAndGoddesses.md` | 6 | Primary: PBS NewsHour *Canvas*, "Museum uses technology to deepen visitor engagement with ancient sculptures" (Jared Bowen of GBH Boston with curators Christine Kondoleon and Laure Marest, on the Museum of Fine Arts Boston's rebuilt ancient galleries; 2022-11-28, 5:45). Secondary (Level 7 excerpt only): WBUR Commentary, arts critic Lloyd Schwartz's review of the same galleries (2022-03-14). | Current, generated 2026-09-10, version `1.2.6.1`. Both sources fetched in full and saved teacher-only in `GodsAndGoddesses_Transcript.md`. First Advanced lesson to embed an image: a CC BY 4.0 Commons photograph of the museum's Athena Parthenos carries the Visual Inquiry hook, saved as `Lesson6_GodsAndGoddesses_Img_Hook.jpg` and credited in `Set2_Advanced_Image_Credits.md`. Three deviations flagged in the lesson, not hidden: the Level 7 second source is written rather than spoken (as in Set 1 Lessons 3-4, and as this row's plan suggests); the note-taking organizer is a tour-route chart rather than §0.4's T-chart, which Lesson 5 used; and Visual Inquiry with Panel Round repeats Set 1 Lesson 2's pairing, which §D6 permits. |
| `Module_1/Set_2/Lesson_7_QuietZone/Lesson7_QuietZone.md` | 7 | Primary (audio, the Set's first): NPR All Tech Considered, "Enter The Quiet Zone: Where Cell Service, Wi-Fi Are Banned" (Elise Hu reporting from the National Radio Quiet Zone and the Green Bank Telescope, with Karen O'Neil and engineer Chuck Niday; 2013-10-08, 5:25). Secondary (Level 7 excerpt only): the Green Bank Observatory's own "What is the Green Bank Observatory?" and "National Radio Quiet Zone" pages. | Current, generated 2026-09-10, version `1.2.7.1`. Both sources fetched in full and saved teacher-only in `QuietZone_Transcript.md`. The Level 7 pairing turns on the thirteen-year gap: the observatory's page argues openly with coverage like the 2013 report ("we are NOT the land of no internet!"). Pronunciation is reduced forms in fast speech, Section 0.4's Advanced/Proficient-only feature, unused in this Band before now. Two deviations flagged in the lesson, not hidden: the Level 7 second source is written rather than spoken (as in Lesson 6 and Set 1 Lessons 3-4, and as this row's plan suggests); and the piece is a reported feature carrying only two real reporter clarification questions, so Day 2's speaking skill is grounded in genuine but thin source language. |
| `Module_1/Set_2/Lesson_8_Lesage/Lesson8_Lesage.md` | 8 | Primary (audio): NPR Morning Edition, "At Maison Lesage, Beauty Embroidered By Hand" (Susan Stamberg inside the Paris embroidery house that works for the couture designers, with Francois Lesage and Angelique Ginguene of Chanel; 2011-09-09, 7:20). Secondary (Level 7 excerpt only): The Week, "Chanel's special effects studio: Maison Lesage," by Alexandra Zagalsky (2018-12-07), on the same workshop seven years later. | Current, generated 2026-09-10, version `1.2.8.1`; **completes Set 2**. Both sources fetched in full and saved teacher-only in `Lesage_Transcript.md`. Pronunciation is linking, the last unused entry in §0.4's bank, so this Band has now used all six. Two departures recorded in the lesson: the plan's suggested angle was the brand's own account, but every Chanel-side domain (chanel.com, le19m.com, English lesage-paris.com) refuses automated retrieval, so the second source is a second journalist, the same call Lesson 5 made; and the Level 7 second source is written rather than spoken, as in Lessons 6 and 7. |

`lessons/advanced/Module_1/Set_2/Set2_Advanced_Image_Credits.md` was created 2026-09-10 with Lesson 6, the
Set's first embedded image. Lesson 5 embeds none and has no rows there.

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
exactly as before; a class with TOEFL-interested students uses the `Module_1/Set_1_T/` copy instead. Two later
passes mirror the base lesson's own revisions: `1.1T.1.5` (2026-09-09) the stem sweep, `1.1T.1.6` (2026-09-09)
the Task D compare-row rebuild. Not yet given to a real class.

**Print formatting (student version), all current:**

- Intermediate Lesson 1: `Module_1/Set_1/Lesson_1_NewBakery/NewBakery_Intermediate_L1_Packet.html`. **2026-09-09:**
  all seven of its images (two hook photos, three choice pictures, the hand-mill/factory-machine pair) are now
  embedded, cited Wikimedia Commons files per `shared/Program_Conventions.md` §I (`Lesson1_NewBakery_Img_*.jpg`);
  the hand-supplied raw files that had been sitting in the folder were removed. Credits live in
  `Module_1/Set_1/Set1_Intermediate_Image_Credits.md`, not in the packet captions (Style Guide v2.17, same day).
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
- Intermediate Lesson 2: `Module_1/Set_1/Lesson_2_PortoFoodTour/PortoFoodTour_Intermediate_L2_Packet.html`.
  **2026-09-09:** its five images (three choice pictures, sardines, the old grocery store) are embedded, cited
  Commons files (`Lesson2_PortoFoodTour_Img_*.jpg`); the grocery photo is A Pérola do Bolhão itself, the 1896 shop the
  video visits; credits in `Set1_Intermediate_Image_Credits.md`. Same
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
  (`shared/Program_Conventions.md` §H): `Lesson3_Backpack_Img_Hook.jpg` (the Mystery Quote hook's cropped
  hip-belt photo), `Lesson3_Backpack_Img_ChoiceBackpack.jpg`/`Img_ChoiceBicycle.jpg`/`Img_ChoiceTent.jpg` (the
  three answer-choice images for Day 1 Phase 4's Level 2 "backpack/bicycle/tent" item), and a
  `Lesson3_Backpack_SourceVideo.webloc`/`.url` link-shortcut pair to the cited YouTube source video. None of
  these is embedded into `Lesson3_Backpack.md` or the packet HTML yet (the packet still uses a placeholder for
  the Mystery Quote photo and no images for the Level 2 choice item) - that integration is still pending, see
  Pending work.
- Intermediate Lesson 4: `Module_1/Set_1/Lesson_4_GreatGrandmother/GreatGrandmother_Intermediate_L4_Packet.html`.
  **2026-09-09:** its three choice pictures (Day 1 Phase 4's Level 2 "great-grandmother/teacher/soccer team" item)
  are now embedded, cited Wikimedia Commons files per `shared/Program_Conventions.md` §I
  (`Lesson4_GreatGrandmother_Img_Choice*.jpg`; credits in `Set1_Intermediate_Image_Credits.md`) - the last empty
  `.pic-box` in Intermediate Set 1's four lessons. Fully
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

## Module 2 progress, Advanced Band (Narrating, Advanced)

Plan approved and logged 2026-09-10: `lessons/advanced/Module_2/Module2_Advanced_Lesson_Plan.md`,
`Rotation_Log_Advanced.md` (this Band's first Module 2 entry). Task Levels 4, 5, 6, 7, same as this Band's
Module 1; source calibrated to Level 5 (5-8 min, natural native pace). Set numbering and lesson numbering both
restart for a new Module (`shared/Program_Conventions.md` §C), so this is Set 1, Lessons 1-4, versioned
`2.1.1.0`-`2.1.4.0`. **Set 1 is 3 of 4 lessons generated** (Lessons 1-3, 2026-09-10):

| Lesson # | Topic direction | Content format | Listening strategy | Speaking skill | Status |
| --- | --- | --- | --- | --- | --- |
| 1 | An astronaut's account of one high-stakes repair | Personal-story talk | Listen for Sequence Markers | Sequencing Language | **Generated 2026-09-10**, `2.1.1.0`. "A View of the Earth," Michael J. Massimino, The Moth (2009 Hubble spacewalk); NASA's own STS-125 record as the Level 7 second source. Flagged deviation: the telling runs ~20-24 min against a 5-8 min target, so the lesson plays a defined span |
| 2 | An insider's account of uncovering something an organization hid | Investigative news feature with insider interview | Predict from Context Before Confirming | Summarizing What Someone Said | **Generated 2026-09-10**, `2.1.2.0`. "In Flint, public trust poisoned by toxic drinking water crisis," PBS NewsHour (Dr. Mona Hanna-Attisha on finding the lead); the CDC's own MMWR report on the same finding as the Level 7 second source. Runs ~9-10 min against a 5-8 min target |
| 3 | An expedition, voyage, or survival ordeal told by a participant | Storytelling-podcast narrative episode segment | Listen for Stated vs. Implied Opinion | Giving Examples | **Generated 2026-09-10**, `2.1.3.0`. "Follow me up a mountain," ABC Radio National *Earshot* (Warren Macdonald, trapped under a boulder on Mount Bowen, 1997); the other two participants' telling as the Level 7 second narrator. No cell amended. Built on a **partial** source record: ABC publishes no transcript. Runs 29:45, played as a defined span |
| 4 | A first-hand oral history of a documented historical event | Oral-history archive interview clip | Listen for Contrastive/Concession Language | Asking for Clarification | Not yet sourced - planned only |

Lesson 1's files: `Module_2/Set_1/Lesson_1_HubbleRepair/Lesson1_HubbleRepair.md`, its teacher-only
`HubbleRepair_Transcript.md`, and `HubbleRepair_Advanced_L1_Packet.html`. **Its topic direction was amended
2026-09-10 before generation**, from the approved athlete-contest direction, which had no transcript-verifiable
source; the format and all five rotated columns are unchanged, so the plan's adjacency clearances still hold. The
reasoning is in the plan's own amendment note and in `Rotation_Log_Advanced.md`. The lesson embeds no images, so
this Set has no images of its own. Its packet is the first in this lesson type built with the complete
`shared/Student_Packet_Style_Guide.md` §B stylesheet rather than a subset, and with the "Objective: I can ..."
student-voice form; it has not been reviewed against a printed page.

Lesson 2's files: `Module_2/Set_1/Lesson_2_FlintWater/Lesson2_FlintWater.md`, its teacher-only
`FlintWater_Transcript.md`, `FlintWater_Advanced_L2_Packet.html`, and two hook image assets. **Its Content Format
cell was amended 2026-09-10 before generation**, from "Long-form investigative interview clip," because no
verifiable long-form interview carrying an insider's own account could be confirmed at this band's runtime; every
other rotated column is unchanged. This lesson brought the Set its first images and so created
`Module_2/Set_1/Set1_Advanced_Image_Credits.md` (two Public domain EPA photographs from Wikimedia Commons, used
for the Day 1 Visual Inquiry hook). Three things are flagged in the lesson's own self-check rather than hidden:
the runtime overage, the subject matter (children's lead exposure, worth a teacher preview), and the absence of
the state's own voice from the source, which is both what the Level 6 task is built to notice and the reason
Level 7's second source is the CDC rather than the organization that did the dismissing.

The plan also fixes the Set-wide note-taking organizer (sequence chain, the Narrating match) and carries a
suggested Level 7 second-source angle per lesson - Level 7's Listening objective needs two real narratives of the
same events, and the Lesson prompt's §0.3 item 7 requires the lesson `.md` to print both sources' own words, so
each lesson's sourcing work is roughly doubled. Two things are flagged rather than resolved silently: the
cross-Module adjacency check is ambiguous for this Band (Module 1's most recently *logged* Set is Set 2, which was
never generated, so Lesson 1 was checked against both Set 2's Lesson 8 and Set 1's Lesson 4 and clears both), and
two topic directions are domain-adjacent to Intermediate's Module 2 Set 1, planned the same day - §F does not
block across Bands. See the plan and `Rotation_Log_Advanced.md` for both.

Module 1's Set 2 (Lessons 5-8) had been left planned-only per user direction 2026-09-10, with this Band moving
on to Module 2 without generating it. **Reversed later the same day at the user's request:** Module 1 Set 2 is
now being generated after all, Lesson 5 first (see the Module 1 Advanced section above). Module 2 Set 1 remains
planned only and unsourced; it is not blocked by Set 2's generation.

Lesson 3's files: `Module_2/Set_1/Lesson_3_MountBowen/Lesson3_MountBowen.md`, its teacher-only
`MountBowen_Transcript.md`, and `MountBowen_Advanced_L3_Packet.html`. It is the first lesson in this lesson type
built on a **partial** source record: ABC publishes no transcript for the episode, so under the Lesson prompt's
§0.3 item 8 the transcript file holds ABC's own companion feature for the same episode, verbatim, with an explicit
statement of what is missing; nothing was reconstructed. Every quotation traces to that file. Three further items
are flagged in the lesson's own self-check: the 29:45 runtime played as a defined span, the fact that Level 7's
two narrators come from one published feature rather than two independent sources, and the content (a double
amputation and a near-death rescue, worth a teacher preview).

Next step for this Module/Band: generate Lesson 4, then the Set assessment, per the Generation workflow below.
Lesson 1's flagged echo against Lesson 3 is resolved - Lesson 3 as generated is terrestrial. The flag against
Module 1 Set 2's planned Lesson 7 ("a real research facility or observatory") still stands for whenever that Set
is taken up.


## Module 1 progress, Proficient Band (Describing, Proficient)

Plan approved and logged: `lessons/proficient/Module_1/Module1_Proficient_Lesson_Plan.md`, `Rotation_Log_Proficient.md`
(new file - the first Set ever planned for this Band). Task Levels 5, 6, 7, 8 (Proficient band; 5 and 6 borrowed
from Advanced, per the Proficient-only two-Levels-down exception in `shared/Program_Conventions.md` §B). Source
calibrated to Level 7 (10-18 min, full unedited TED Talk/long-form interview/lecture excerpt). Level 7's
Listening objective needs two real sources on the same subject (same requirement Advanced's Level 7 has);
Level 8's Listening objective additionally needs a source that genuinely hedges or withholds something - both
flagged per lesson with a suggested angle in the plan. **Set 1 complete, 4 of 4 generated:**

| Lesson # | Topic Direction | Real source(s) | Status |
| --- | --- | --- | --- |
| 1 | A real neighborhood/district undergoing visible change, described by people with different stakes in it | Primary: PBS NewsHour, "Are newcomers a mixed blessing for the Lower Ninth Ward?" (William Brangham, aired 2015-08-25). Secondary (Level 7 only): "Make It Right Foundation" article on English Wikipedia, documenting that nonprofit's own quoted mission. | Current - generated fresh against v1.1, current 2-day architecture from the start. Two open items flagged (not silently resolved): the Level 7 secondary source is a Wikipedia article, not the org's own live site (unconfirmed as still fetchable); Day 2's Speaking Skill Spotlight is grounded in the source's real situational context rather than a quoted on-screen comparison line - see `Rotation_Log_Proficient.md` for the full notes. **2026-09-10, bumped to `1.1.1.1`:** Task D rebuilt to Quality Standards §C9 - three subject-paired rows (what was promised and what is there, what the houses are like, what the neighborhood says it needs) of verbatim PBS transcript and foundation-claim excerpts, both re-fetched, 5 and 6 excerpts; the two source labels no longer characterize each source's tone, and the `.md`'s inline answer moved to an `Answer note:` line (§E2). `LowerNinthWard_Transcript.md` saved in the same pass. |
| 2 | A real designer's or maker's talk about one product or piece of design they created | Primary: TED, "Design for people, not awards" (Timothy Prestero, TEDxBoston 2012, filmed 2012-06-22, approx. 11 min), on the NeoNurture infant incubator his team built. Secondary (Level 7 only): "2010's Most Innovative Tech Product Is Not a Damn Jetpack" (John Pavlus, MIT Technology Review, 2010-11-16), an independent journalist's description of the same incubator, published before it was known to have failed. | Current - generated 2026-09-10 against `Generate_Lesson_Prompt_v2.5.md`, `1.1.2.0`. Three artifacts: `Lesson_2_NeoNurture/NeoNurture_Transcript.md`, `Lesson2_NeoNurture.md`, `NeoNurture_Proficient_L2_Packet.html`. Built as Panel Round from the start (post-§D11), Level 7's compare set holds four subject-paired rows with three to five verbatim excerpts per source, and every exemplar sits on an `Answer note:` line, so it carries none of Lesson 1's §D11 or §C9 backlog. Four open items flagged (not silently resolved): module alignment reasoned through, since the talk carries a thesis; the transcript came through English-Video.net's mirror of TED's own English transcript rather than TED.com directly; the secondary source is short, so six of its sentences are a large share of it; and the hook image is a real 1978 hospital incubator, not the NeoNurture, which has no free-licensed photograph. See `Rotation_Log_Proficient.md` for the full notes. |
| 3 | A real person profiled by someone who knew them closely, visibly careful around one sensitive aspect of that person's life or reputation | Primary: NPR Fresh Air, "Remembering Ernest Hemingway Biographer A. E. Hotchner" (Terry Gross interviewing A. E. Hotchner about Ernest Hemingway; first broadcast 1999-07-21, rebroadcast 2020-02-18; 16:01). Secondary (Level 7 only): the Nobel Prize's own Hemingway biographical note, written at the time of the 1954 award. | Current - generated 2026-09-10 against `Generate_Lesson_Prompt_v2.5.md`, `1.1.3.0`. Three artifacts: `Lesson_3_PapaHemingway/PapaHemingway_Transcript.md`, `Lesson3_PapaHemingway.md`, `PapaHemingway_Proficient_L3_Packet.html`. No image, so the Set's image register is unchanged. **Taught as two cued ranges, not in full:** the opening two minutes describe Hemingway's suicide graphically and a later stretch ends in a crude joke, so both are excluded and no task, quotation, or hook draws on them; a teacher must cue the two ranges rather than press play at 0:00. See `Rotation_Log_Proficient.md` and the transcript file's own content warning. Other open items: NPR publishes no timestamps, so segment labels are proportioned by content order; the Nobel note is short, so five sentences are a large share of it; one quotation preserves NPR's own mid-sentence ellipsis. |
| 4 | A real institution or historic site described in a lecture/docent walkthrough, where institutional framing plays down a known shortcoming | Primary: BBC Radio 4 with the British Museum, "A History of the World in 100 Objects" Ep. 77, "Benin plaque: the oba with Europeans" (written and presented by Neil MacGregor, then director of the British Museum; first broadcast 2010-09-21; approx. 14 min, derived). Secondary (Level 7 only): "Smithsonian agrees to return its collection of Benin Bronzes to Nigeria" (NPR via DCist/WAMU, 2022-03-09). | Current - generated 2026-09-10 against `Generate_Lesson_Prompt_v2.6.md`, `1.1.4.0`. Three artifacts: `Lesson_4_BeninPlaque/BeninPlaque_Transcript.md`, `Lesson4_BeninPlaque.md`, `BeninPlaque_Proficient_L4_Packet.html`. **The first Proficient lesson built to the six-phase Day 1 and the §D12 beats**, and the purest fit for this row in the Set: the museum's own director describes an object his museum holds because of the 1897 raid, and Level 8 turns on the one thing he never says, that the plaque is in his own building. Open items: the episode quotes an 1897 curator's racist characterization in order to refute it, so a teacher should preview it (no task uses it and it is not in the packet); the runtime is derived from word count because the BBC programme page no longer resolves; the transcript came from the Wayback Machine's capture of the BBC's own transcript page; the NPR article is short; and a 14-minute source fills Phase 2 almost entirely. See `Rotation_Log_Proficient.md`. |

**Set 1's image register:** `lessons/proficient/Module_1/Set_1/Set1_Proficient_Image_Credits.md`, created
2026-09-10 on this Set's first embedded image (Lesson 2's Visual Inquiry hook photograph, one row today).
Lesson 1 embeds no image and so has no table there. Packets print no credit
(`shared/Program_Conventions.md` §D/§I).

**Print formatting (student version), Lesson 1:** `Module_1/Set_1/Lesson_1_LowerNinthWard/LowerNinthWard_Proficient_L1_Packet.html`,
generated fresh against the then-current Student Print Formatting Prompt spec (masthead-meta stack,
idiom-table format, Four-Corner Debate translated to a plain circle-your-answer print activity, multi-source Task
C compare-pair layout for Level 7, upside-down Closing Transfer Check script). Its idiom table (one idiom,
"mixed blessing") was reverted 2026-09-08 to the `.spotlight-box`/`.idiom-item` "Phrase Spotlight" treatment,
per the retired idiom-table rule (see `Changelog.md`). Not yet reviewed against a printed page, same as every
other packet in this family.

**Print formatting (student version), Lesson 2:** `Module_1/Set_1/Lesson_2_NeoNurture/NeoNurture_Proficient_L2_Packet.html`,
generated fresh against `Generate_Student_Packet_Prompt_v2.6.md` and the current Style Guide. It is the first
packet in this family built to the full §B base stylesheet rather than a subset of it, and the first whose two
`.objective` lines use the "I can ..." form the Style Guide §E requires (every earlier packet in this family
still opens with a bare verb, logged in Pending work below). Two parts (Unit 2A Listening / Unit 2B Speaking),
each with four star-rated task blocks, the `.masthead-meta` stack on both mastheads, three Good to Know boxes
front-loaded, a citebox at the point of watching, a four-row fillable Listening Notes organizer, the Level 7
four-row multi-source compare layout, an embedded public-domain hook photograph, the STOP-badged "Don't read
ahead" callout, and the upside-down closing script. No protocol is named in student-facing text. Not yet
reviewed against a printed page, same as every other packet in this family.

**Print formatting (student version), Lesson 3:** `Module_1/Set_1/Lesson_3_PapaHemingway/PapaHemingway_Proficient_L3_Packet.html`,
generated fresh against `Generate_Student_Packet_Prompt_v2.6.md` and the current Style Guide, to the same
standard as Lesson 2's (full §B base stylesheet, "I can ..." objectives on both mastheads, no inline styles, no
selector outside §B/§H.1). Two parts (Unit 3A Listening / Unit 3B Speaking), each with four star-rated task
blocks, three Good to Know boxes front-loaded, a Mystery Quote hook printed as a bare line with two prediction
questions, a citebox at the point of listening, a four-row fillable Listening Notes organizer, the Level 7
three-row multi-source compare layout, the STOP-badged callout, and the upside-down closing script. It is the
first packet in this family for an **audio** source, so every student-facing instruction says "listen" and the
words "watch" and "video" appear nowhere in it. No protocol is named in student-facing text. Not yet reviewed
against a printed page, same as every other packet in this family.

**Print formatting (student version), Lesson 4:** `Module_1/Set_1/Lesson_4_BeninPlaque/BeninPlaque_Proficient_L4_Packet.html`,
generated fresh against `Generate_Student_Packet_Prompt_v2.7.md` and the current Style Guide. Two parts (Unit 4A
Listening / Unit 4B Speaking), each with four star-rated task blocks, a three-column chart as the opening hook,
three Good to Know boxes, a citebox at the point of listening, a five-row fillable Listening Notes organizer of
signpost phrases, the Level 7 three-row multi-source compare layout, **two `.verify-window` blocks in a "Check
It Against the Source" section placed after every listening task's response space and closing on the cover
instruction**, the STOP-badged callout, and the upside-down closing script. Audio source, so "listen" throughout
and the words "watch" and "video" appear nowhere. The four Jigsaw quotations are printed for every student. Not
yet reviewed against a printed page, same as every other packet in this family.

**Set 1 is now complete**, so Step 3 of the Generation workflow is runnable for this Band: run
`Generate_Assessment_Prompt_v2.1.md` and `Generate_Assessment_Student_Packet_Prompt_v2.1.md` against the Set.
Set 2 has not been planned for this Band. Lesson 4 completes the Set and unblocks Step 3, the Set assessment.

## Generation workflow (current)

**Step 1 - Plan the module.** Run `Generate_Module_Lesson_Plan_Prompt_v2.1.md` for the
target Module and Band. It reads the Rotation Log first (`Rotation_Log.md` plus that Band's own
`Rotation_Log_<Band>.md`), produces the module's plan table (4 rows by
default), and runs its self-check. Review and approve the plan before
generating any lesson content. Once approved, append its Rotation Log entry to that Band's `Rotation_Log_<Band>.md`.

**Step 2 - Generate lessons.** Run `Generate_Lesson_Prompt_v2.6.md` (pasted with
`shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`) against the approved plan. Any image a lesson needs is fetched and cited in this same step (`shared/Program_Conventions.md` §I). Because each lesson now requires finding and verifying a real source (not just writing to a word-count
ceiling), generate **one lesson at a time** for this family rather than Passage Reading's two-at-a-time pacing,
at least until the sourcing step has proven reliable enough to batch. As of v1.3, generate three artifacts per
lesson, in order: the source's `<Slug>_Transcript.md` (full real transcript, verbatim, teacher-only), then the
lesson `.md`, then its student packet `.html`. Check each lesson's self-check (runtime/citation/task-Level/
transcript-file checks) before moving to the next.

**Step 3 - Assess.** Once a Set (4 lessons) is complete, run `Generate_Assessment_Prompt_v2.1.md` for that Set - both Part A (Listening) and Part B (Speaking) run every Set, not staggered. Part B's
mechanism depends on the Band: Beginner/Intermediate produce a scored Teams Speaking Progress recording task
(the formal assessment itself); Advanced/Proficient produce a live presentation task plus a same-task
Teams-recording alternate for standing use (e.g. an absence). See that prompt's own scope notes (Section B.0-B.1).

**Step 4 - TOEFL Track Tier (optional, per Set).** When a TOEFL-capable variant of a completed Set is
wanted, run `Generate_TOEFL_Track_Tier_Prompt_v1.1.md` (pasted with the three shared files) against each of that
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

- **Pronunciation has a rotation bank, not a progression (2026-09-10).** The new
  `design/Pronunciation_Scope_and_Sequence.md` sequences pronunciation across the program's 8 Levels;
  nothing in this family has been wired to it yet. Three separate items, all blocked on the same fold-in
  pass and none of them mechanical:

  1. **`Generate_Lesson_Prompt_v2.6.md` §0.4's pronunciation bank (its lines 184-186) has no entry below
     Level 3 or above Level 6.** Its six features map to Level 3 (content-word stress), Level 4
     (thought-group pausing, rising and falling intonation, list intonation), Level 5 (contrastive
     stress), and Level 6 (linking, reduced forms). The bank is also entirely prosodic: no lesson in this
     family has ever taught a sound, a contrast, or a cluster. Replace it with the per-Level table at that
     spec's §E.0 and bump the prompt to v2.7; rewrite Phase 3's three-sentence spec (lines 374-377) as the
     spec's §F five-move cycle in the same pass.

  2. **Eight generated lessons teach a feature outside their band's task-Level range**
     (`Program_Conventions.md` §B), a direct consequence of item 1:
     `beginner/Module_1/Set_1/Lesson_1_WhatIsIt/` (rising and falling intonation, Level 4, one above the
     Beginner ceiling); `beginner/Module_1/Set_1/Lesson_3_FamilyPhotos/` (thought-group pausing, Level 4,
     one above); `beginner/Module_1/Set_1/Lesson_4_HowAboutThis/` (contrastive stress, Level 5, **two**
     above, which breaks the band-distance invariant outright);
     `intermediate/Module_1/Set_1/Lesson_3_Backpack/` and
     `intermediate/Module_1/Set_2/Lesson_7_RosettaStone/` (linking, Level 6, one above);
     `advanced/Module_1/Set_2/Lesson_6_GodsAndGoddesses/` (content-word stress, Level 3, one **below**);
     `proficient/Module_1/Set_1/Lesson_3_PapaHemingway/` (rising and falling intonation, Level 4, one
     below); `proficient/Module_1/Set_1/Lesson_4_BeninPlaque/` (thought-group pausing, Level 4, one
     below). Fixing one is not mechanical: it means choosing a Level-appropriate feature that is actually
     audible in that lesson's own cited clip (self-check item 12), rewriting the `.md` Phase 3, and
     regenerating the packet. Do it when each lesson is next touched, folding it into the §D12 pass those
     lessons are already queued for; bump the `<Version>` and add the `Rotation_Log_<Band>.md` row in the
     same pass. Because the bank stops at Level 6, no lesson in the **Proficient** band has ever been
     taught a pronunciation feature at its own Levels (7-8) at all; that is not fixable by reassignment
     and waits on item 1.

  3. **"Say It Like a Native Speaker" is printed in all 24 packets and codified nowhere.** It is a
     `.spotlight-box` with a `.spotlight-label`, and neither `Generate_Student_Packet_Prompt_v2.7.md` nor
     `shared/Student_Packet_Style_Guide.md` §H.1 defines it. §2.11 of the packet prompt instead describes
     a different thing ("any pronunciation marking exercise folded in as a short bonus line under the
     relevant task") that no packet actually does. Codify the real convention in Style Guide §H.1 with a
     delta class for minimal-pair and contour-marking items plus matching §I self-check items, and revisit
     the heading itself: "like a native speaker" names a target the scope-and-sequence spec explicitly
     rejects (§B, intelligibility not accent reduction).


- **§D12 verification beat backlog (Quality Standards v1.17, Lesson prompt v2.6, 2026-09-10).** Day 1 is now
  six phases: the clip plays twice with nothing written on the page (Phases 2 and 4, the second under a
  narrower stated purpose), and a new Phase 5 prints one or two bounded verification windows of the source's
  own words, ending on a covered-window replay. **23 of the 30 generated lessons predate this and still run the old
  five-phase Day 1 with a single play and no window.** Fixing one is not mechanical: it means reading that
  lesson's transcript and choosing a stretch on evidence (one a Phase 4 item actually turned on, or one
  carrying a connected-speech feature that Band predictably mishears), then rewriting Day 1's phase budgets in
  the `.md` and regenerating the packet against `Generate_Student_Packet_Prompt_v2.7.md`. Do it when each
  lesson is next touched for any reason; bump its `<Version>` (Conventions §G) and add its
  `Rotation_Log_<Band>.md` row in the same pass. Do not generate any new lesson without the beat.

  **18 lessons that have a transcript on disk and need only a window chosen plus the Day 1 rewrite**
  (Intermediate Module 2's two lessons were cleared 2026-09-10: Lesson 2 was built to the six-phase Day 1 in
  the pass that generated it, and Lesson 1 was retrofitted to it the same day, `2.1.1.0` to `2.1.1.1`; **all
  four of Advanced Module 1 Set 2's lessons were cleared the same day**, retrofitted in the session that
  generated them and bumped to `1.2.5.1`-`1.2.8.1`)**:**
  `beginner/Module_1/Set_1/Lesson_2_AreYouBusy/`, `Lesson_3_FamilyPhotos/`, `Lesson_4_HowAboutThis/`;
  `intermediate/Module_1/Set_1/Lesson_1_NewBakery/`, `Lesson_4_GreatGrandmother/`;
  `intermediate/Module_1/Set_2/Lesson_5_IberianLynx/`, `Lesson_6_TapestryFactory/`, `Lesson_7_RosettaStone/`,
  `Lesson_8_WrangellStElias/`;
  `advanced/Module_1/Set_1/Lesson_2_LivingTextbooks/`, `Lesson_3_KeyDeer/`, `Lesson_4_GlassBender/`;
  `advanced/Module_2/Set_1/Lesson_1_HubbleRepair/`, `Lesson_2_FlintWater/`, `Lesson_3_MountBowen/`;
  `proficient/Module_1/Set_1/Lesson_1_LowerNinthWard/`, `Lesson_2_NeoNurture/`, `Lesson_3_PapaHemingway/`
  (Proficient `Lesson_4_BeninPlaque/` was cleared 2026-09-10, built to the six-phase Day 1 in the same pass that
  generated it, and is this Band's worked example of the beats: two windows, one chosen for what a task turned
  on and one for the connected speech it carries).

  **5 lessons with no transcript on disk, blocked on the transcript backfill entry below** (do the backfill
  first, in the same pass, or the window will be cut from recalled wording rather than real wording):
  `beginner/Module_1/Set_1/Lesson_1_WhatIsIt/`; `intermediate/Module_1/Set_1/Lesson_2_PortoFoodTour/`,
  `Lesson_3_Backpack/`; `advanced/Module_1/Set_1/Lesson_1_LostKitchen/` and its TOEFL fork
  `advanced/Module_1/Set_1_T/Lesson_1_LostKitchen/`, which inherits from the base copy.

  Set 1's two generated assessments are deliberately **not** on this list: Quality Standards §D12 exempts
  assessments, since a verification beat inside a graded task contaminates the measure. The two Assessment
  prompts were not bumped for the same reason.

- **Beginner Lesson 1 carries a Style Guide §A.2 colour violation (2026-09-10).**
  `Module_1/Set_1/Lesson_1_WhatIsIt/` offers *"It is small and red"* and *"It is short and green"* as
  Level 3 answer options about the map, and its packet prints the same two. §A.2 (Style Guide v2.27)
  forbids an item answered by reading a chromatic colour off a printed picture. Fold this into
  Lesson 1's already-pending full regeneration rather than patching it alone - that pass also has to
  clear the missing transcript file, the empty `.pic-box` grids plus the "hold up real objects" hook,
  and the bare-verb objective. **Lesson 1 is now the only lesson in Beginner Set 1 not built to the
  current standard**; Lessons 2, 3, and 4 are clean against §A.2.

- **Resolved 2026-09-10 (Quality Standards §D11, room-neutral participation):** all seven affected lessons in
  this modality were rewritten, not backlogged: Beginner `Module_1/Set_1/Lesson_1_WhatIsIt/` (Fishbowl ->
  Panel Round, `1.1.1.0` -> `1.1.1.1`); Intermediate `Lesson_1_NewBakery/` (Fishbowl -> Panel Round,
  `1.1.1.0` -> `1.1.1.1`), `Lesson_2_PortoFoodTour/` (Four-Corner Debate -> Take a Side, `1.1.2.0` ->
  `1.1.2.1`), `Lesson_4_GreatGrandmother/` (Concentric Circles -> Rotating Partners and K-W-L Walk -> the
  K-W-L Chart its packet already printed, `1.1.4.1` -> `1.1.4.2`); Advanced `Lesson_2_LivingTextbooks/`
  (Fishbowl -> Panel Round, plus the listener task §D7 required and it lacked, `1.1.2.2` -> `1.1.2.3`),
  `Lesson_3_KeyDeer/` (Four-Corner Debate -> Take a Side, `1.1.3.2` -> `1.1.3.3`); Proficient
  `Lesson_1_LowerNinthWard/` (Four-Corner Debate -> Take a Side, `1.1.1.1` -> `1.1.1.2`). Every Band's
  rotation log and all four Module lesson plans carry the new names; `Rotation_Log.md` holds the
  old-to-new mapping for adjacency checks against older rows.
- **Stem-answer backlog (Quality Standards §C9, 2026-09-09):** Proficient
  `Module_1/Set_1/Lesson_1_LowerNinthWard/` still prints the segment's organization and the tonal shift inside
  the Task stems' parentheses (packet Unit A Tasks; matching `.md` Phase 4 lines). Move each to an `Answer note:`
  line and strip the packet stem when the lesson is next touched. Its Task D share of this backlog was cleared
  2026-09-10 (tone-characterizing source labels replaced, inline answer moved to an `Answer note:` line); the
  Task A-C stem parentheticals are what remain. Intermediate Set 1's Unit B stems that offer
  "(for example, calling something 'impressive' or 'unusual')" are option menus, not answers, unless the quoted
  word is from the clip - check each when its packet is next regenerated.
- **Resolved 2026-09-09 (Conventions §I):** Backpack's four hand-supplied images were replaced with cited Wikimedia
  Commons files (the hook is a hip-belt crop of the same CC0 backpack photo used as the "a backpack" choice; the
  bicycle and tent are CC BY-SA 4.0 / CC0), with `Image:` citation lines in the `.md` and credits in
  `Set1_Intermediate_Image_Credits.md`. The two former `.webp` assets are now `.jpg`.
- **Resolved 2026-09-09 (Conventions §I):** GreatGrandmother's three empty choice boxes (a great-grandmother / a
  teacher / a soccer team) now hold cited Wikimedia Commons photos (CC BY-SA 3.0 / CC BY 4.0 / CC BY 2.0), with
  `Image:` citation lines in the `.md` and credits in `Set1_Intermediate_Image_Credits.md`.
- **Resolved 2026-09-09 (Conventions v1.13 / Style Guide v2.17):** photo credits moved out of the four Intermediate
  Set 1 packets into one Set-level register, `Module_1/Set_1/Set1_Intermediate_Image_Credits.md` (19 images, one
  table per lesson); the packets' credit clauses were stripped and the credit-only captions under the four
  `.pic-options` grids removed - see `shared/Changelog.md`.
- **Objective as a student can-do (Style Guide v2.10, 2026-09-08):** every packet except Proficient Lessons 2
  and 3 opens its objective with a bare verb ("Objective: describe...", "Objective: listen for..."), the form
  the Style Guide retired in favor of "I can" plus the skill in the student's voice.
  `NeoNurture_Proficient_L2_Packet.html` (2026-09-10) was the first built to the "I can ..." form and
  `PapaHemingway_Proficient_L3_Packet.html` follows it; either is the model to copy. Rewrite each of the others
  when its packet is next regenerated; this lesson type's packet prompt was not bumped for it and should state
  the §E form when next revised.
- **Self-contained rule backlog (Quality Standards §D8, 2026-09-08):** these packets still carry empty `.pic-box`
  grids, "[TEACHER: insert photo ...]" notes, or a "hold up real objects" hook, to be replaced by embedded images
  or a real-object redesign when each is next touched: `WhatIsIt_Beginner_L1_Packet.html` (18 empty boxes plus
  the real-objects hook in its `.md`), `LivingTextbooks_Advanced_L2_Packet.html`
  (one box), `Backpack_Intermediate_L3_Packet.html`
  (three remaining boxes; its hook and choice images are already embedded), and
  `Set1_Intermediate_Assessment_Packet.html` (three boxes on a graded item).

- **Backfill transcript files for the 9 lessons generated before v1.3's requirement** - the
  `<Slug>_Transcript.md` file (Section 0.3, item 7) is going-forward only as of 2026-09-07; these 9
  lessons predate it and don't have one yet. Each needs the source re-fetched to confirm the full
  real transcript, not just re-derived from the existing lesson `.md`'s own short quotes:
  Beginner `Module_1/Set_1/Lesson_1_WhatIsIt/`; Intermediate `Module_1/Set_1/Lesson_2_PortoFoodTour/`,
  `Module_1/Set_1/Lesson_3_Backpack/`; Advanced `Module_1/Set_1/Lesson_1_LostKitchen/` (all under their
  respective `lessons/<band>/` root). Corrected 2026-09-10 against disk: this entry previously also listed
  `Lesson_1_NewBakery/`, `Lesson_4_GreatGrandmother/`, `Lesson_2_LivingTextbooks/`, `Lesson_3_KeyDeer/`,
  `Lesson_4_GlassBender/` and Proficient `Lesson_1_LowerNinthWard/` as missing a transcript; all six have one.
  Three of them are simply **misnamed** and want a rename, not a re-fetch, to match §0.3 item 8's
  `<Slug>_Transcript.md`: `Lesson_1_NewBakery/Audio_Transcript.md` and
  `Lesson_4_GreatGrandmother/Audio_Transcript.md` -> `NewBakery_Transcript.md` /
  `GreatGrandmother_Transcript.md`, and `Lesson_3_KeyDeer/Video_Transcript.md` -> `KeyDeer_Transcript.md`.
- **Generate Intermediate Module 2 (Narrating) Set 1's Lessons 3-4** - Lessons 1-2 are generated
  (2026-09-10); Lessons 3-4 are planned only. Run `Generate_Lesson_Prompt_v2.6.md` one lesson at a time
  against `lessons/intermediate/Module_2/Module2_Intermediate_Lesson_Plan.md`, honoring that plan's standing
  content bound (no refugee, migration-status, or displacement sources), its Level 2 slot-to-shape table, and
  the Lesson 2/Lesson 4 format swap: Lesson 4 now needs a first-hand or eyewitness news account.
- **Rule conflict to settle: how many productions a fixed-output Level gets per day.** The Listening/Speaking
  Lesson prompt's Section 0.6 bank assigns Level 2 both a practice production (Day 1 Phase 4 *Point or name*,
  Day 2 Phase 4 *a partner's own past action*) and a Transfer production in Phase 5 of each day, while
  `shared/Generation_Quality_Standards.md` §D10 counts a Transfer Check as one of the day's productions and
  caps the Level at one per day. Following the bank, as every approved Set plan does, puts Level 2 at two
  productions per day. Found while generating Module 2 Lesson 1 (`Lesson1_NewKid.md` self-check item 14),
  which follows the bank and flags it. Settling it means amending §D10 or §0.6, and it reaches every lesson
  type with a fixed-output Level, so it is logged here rather than decided inside one lesson.
- **Generate Proficient Module 1 Set 1's remaining lesson (4)** - Lessons 1, 2, and 3 are generated; Lesson 4
  is still planned only. Run `Generate_Lesson_Prompt_v2.6.md` per the Generation workflow below, applying the
  same Level 7 two-source pattern and Level 8 withheld-content source. Lesson 4 needs an institution's own
  lecture or docent walkthrough that plays down a known shortcoming, plus an independent historian's or
  journalist's account of the same site. Confirm a real, fetchable transcript exists before committing to a
  source, and check the whole of it for content a class cannot use before building tasks on it - Lesson 3's
  source had to be rebuilt around two cued ranges after its opening was read in full.
- **Give both Set 1 assessments to a real class** - Intermediate Set 1's and Advanced Set 1's assessments are
  both generated but neither has been field-tested. Once given, expect addenda the same way the Lesson prompt
  got five.
- **Homework Generation Prompt** - not started. Will need its own rules given a homework assignment can't
  hand a student the full copyrighted transcript the way Passage Reading homework reuses the anchor text.
- **Generate Intermediate Set 2's assessment (now due)** - Intermediate Module 1 Set 2 was completed
  2026-09-10, so `Generate_Assessment_Prompt_v2.1.md` and `Generate_Assessment_Student_Packet_Prompt_v2.1.md`
  are due against it, the same way both were run for Advanced Set 1. Part A (Listening) needs 2-3 new verified
  real clips distinct from all four taught sources (Iberian lynx, Spanish tapestry factory, Rosetta Stone,
  Wrangell-St. Elias) and from Set 1's assessment clips (HaHaHouse Museum, Pompeii bathhouse), with items
  covering all four of Set 2's listening strategies (Stated vs. Implied Opinion, Signposting, Cause-and-Effect
  Language, Contrastive/Concession Language) and vocabulary pooled across the Set's four lessons. Part B
  (Speaking) is a scored Teams recording task at this Band. Output goes to
  `lessons/intermediate/Module_1/Set_2/Set2_Intermediate_Assessment.md` and `Set2_Intermediate_Assessment_Packet.html`.
- **Generate Advanced Set 2's assessment (now due)** - Advanced Module 1 Set 2 was completed 2026-09-10, so
  `Generate_Assessment_Prompt_v2.1.md` and `Generate_Assessment_Student_Packet_Prompt_v2.1.md` are due against
  it. Part A (Listening) needs 2-3 new verified real clips distinct from all four taught sources (the High
  Line, the MFA Boston ancient galleries, the National Radio Quiet Zone, Maison Lesage), from Set 1's four
  (The Lost Kitchen, Phoenix mid-century modern, the Key deer, the Boise glass bender) and from Set 1's
  assessment clips (Jump the Moon, the women lighthouse keepers), with items covering all four of Set 2's
  listening strategies (Predict from Context Before Confirming, Sequence Markers, Contrastive/Concession
  Language, Main Ideas/Gist) and vocabulary pooled across the Set's four lessons. Part B (Speaking) at this
  Band is a live presentation task plus a same-task Teams-recording alternate. Output goes to
  `lessons/advanced/Module_1/Set_2/Set2_Advanced_Assessment.md` and `Set2_Advanced_Assessment_Packet.html`.
- **Generate any other future Set's assessment** - same two prompts, whenever a Set in any other Band is
  completed.
- **Section 0.6 versus Quality Standards Section B, a prompt-level conflict found generating Intermediate Set 2
  (2026-09-10)** - `Generate_Lesson_Prompt_v2.6.md` Section 0.6 requires every Level 1-2 item other than the
  day's one production to come from a seven-shape bank, most of whose shapes are pinned to a single Phase slot,
  and forbids a shape landing in the slot it held in the previous lesson. Quality Standards Section B
  separately requires the lowest task Level's Day 1 task to carry a genuine interpretive component, and the
  bank has no interpretive shape. Over a four-lesson Set the two rules collide: **Lesson 5
  (`Lesson_5_IberianLynx/`, Day 1 Phase 4 item 4) and Lesson 7 (`Lesson_7_RosettaStone/`, Day 1 Phase 4 item 3)
  each carry one interpretive item that is not a bank shape**, flagged in place in both lessons rather than
  dropped. The same narrowness forces the slot map to cycle with a period of two, so **Lesson 8's map is
  identical to Lesson 6's**, also flagged in place. Both are prompt problems, not lesson problems: fixing them
  means either adding an interpretive shape to the bank or relaxing the slot pinning, then bumping
  `Generate_Lesson_Prompt` and sweeping. Left for a deliberate prompt pass rather than patched lesson by lesson.
- **An undefined `.no-print` class sits in 24 already-generated packets across Passage Reading and
  Listening/Speaking (found 2026-09-10)** - `<div class="toolbar no-print">` appears in every packet in this
  repo except the four new Intermediate Set 2 ones, but `.no-print` is defined nowhere in
  `shared/Student_Packet_Style_Guide.md` §B or §H, which §D forbids and §I item 13 checks for. It is inert
  (the `.toolbar` rule already hides the button in print), so nothing renders wrong; it is a one-token
  mechanical sweep across 24 files, each of which would also take a version-code bump and a Rotation Log row
  under the generalization pass. Not swept here because it was found mid-generation and the churn is
  disproportionate to a no-op class; flagged for a decision.
- **Part 2 + Presentation Project Extension** - not started. Planned to mirror the content sample's second
  (video) source, cross-source synthesis, and group-presentation assignment, as an optional add-on after a core
  lesson is complete - a genuinely separate, sit-on-top document (unlike the TOEFL Track Tier mechanism above,
  which is embedded directly in the lesson).
- **Generate TOEFL Track Tier forks for the remaining Set 1 lessons** - only Advanced Lesson 1 (LostKitchen) has
  a `Module_1/Set_1_T/` fork so far. Advanced Lessons 2-4 and any completed Proficient-band lesson are equally eligible
  (`Generate_TOEFL_Track_Tier_Prompt_v1.1.md`: Advanced/Proficient bands only); fork on request, not automatically for every lesson.
- **Give the `Module_1/Set_1_T` Lesson 1 fork to a real class** - like every other assessment/extension artifact in this
  family, it hasn't been field-tested yet; expect the same kind of addenda the Lesson and Assessment prompts
  picked up after their own first real uses.
- **Embed Lesson 3 Backpack's real images into the lesson content** - `Lesson3_Backpack_Img_Hook.jpg` and the
  three `Img_Choice*` files (see the Intermediate Lesson 3 print-formatting note above) are renamed and sitting
  in the lesson folder but not yet wired into `Lesson3_Backpack.md` or `Backpack_Intermediate_L3_Packet.html`
  (the packet still uses a generic "real picture placeholder" for the Mystery Quote hook and no image for the
  Day 1 Phase 4 Level 2 choice item).
