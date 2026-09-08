# Passage Reading Assessment Generation Prompt (v5.0)

Companion to the Passage Reading Lesson Generation Prompt. Generates a differentiated reading assessment from
already-completed lessons: one section per task Level in the band (Conventions §B), plus a Foundation Support
check where applicable, plus one study guide per task Level. Every assessed section is keyed to a task Level;
which design template a section uses (scaffolded, independent, open-production) is set by that Level's position
among the band's task Levels (lowest, in between, highest).

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`
alongside it. Quality Standards §A-§C (task Levels, Respectful Tiers, item quality: distinct, not trivially easy,
requires the centerpiece, plausible distractors and padded banks, time-balanced, counted, complete, traceable)
govern every item here and are not restated. This prompt states only what is specific to a Reading assessment.

**Current version: v5.0.** For the dated version history and reasoning, see `Changelog.md`.

**Scope:** assessments only. It does not generate lessons and does not invent anchor texts, vocabulary, or idioms;
it draws from the specific lessons it is given. If no completed lessons are provided, stop and ask.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs

- **The lessons being assessed,** in full: anchor texts, Phase 1 target vocabulary and idiom lists (the source
  of every vocabulary item; never re-derived from the CSV), Module, Band.
- **Set number** (Conventions §C), alongside Module and Band. The normal case is one completed Set (4 lessons),
  run once the Set's lessons are complete. A mid-Set checkpoint or a multi-Set review is supported but must say
  which Set(s) it draws from, since Set number ties the assessment to `lessons/<band>/Module_<N>/Set_<N>/` and a
  Rotation Log entry.
- **Scope:** cumulative (several lessons, typically a full Set) or per-lesson (one 2-day cycle). Ask if not
  specified; the documents differ greatly in length.
- **Band:** confirm one band applies across every lesson in scope. Never combine two bands' lessons without
  flagging it; their task-Level counts and CSV rows differ.
- **Which task Level each student or group actually completed,** and whether any student used the lesson's
  Foundation Support layer. Build each Level's content from that Level's actual completed tasks (its matrix items,
  its participation-mode stems), not a generic assumption. Ask if unspecified and the lesson has a Foundation
  Support layer.
- **Each source lesson's Skill Spotlight** (its plain-language skill statement). Section 2's comprehension task for
  that lesson exercises this exact skill on the new passage. If an older lesson has none, ask, or fall back to
  the Module objective.
- **Each source lesson's task-Level grounding:** the exact Reading CSV row (Level, Description) the lesson cited
  for each task Level, pulled from the lesson, not re-derived; this feeds 0.3's Tests tag.

### 0.2 What this prompt does not do

- Does not fix a source lesson's Module drift; flag it back to the lesson (Quality Standards §A4).
- Does not test content the lessons did not teach: every word, idiom, and comprehension task type traces to a
  specific lesson's pre-teaching list, Phase 2/3 task content, or Skill Spotlight.
- Does not test the original anchor text's content at all, and does not assume a student remembers it (Quality
  Standards §C3): every comprehension item is answerable using only the new passage printed in the assessment.

### 0.3 Lesson tagging and objective traceability (every item)

Every item in Sections 1 and 2 carries two pieces of information printed on the document itself:

- **Source lesson:** which one completed lesson (number and topic) the item's content, passage, and skill come
  from. An item never blends two lessons, so it stays removable (1.1a).
- **Tests:** a one-line citation of the CSV row the item assesses. For a comprehension item, the same Reading
  objective (Level plus quoted or closely paraphrased Description) that lesson's task at that Level was built to
  satisfy. For a vocabulary item, the source lesson and Module (vocabulary words are not themselves leveled
  objectives).

Print the tag beneath the item's prompt, in italics:

```
3. What does the writer compare the mountain view to?
*(Lesson 6: A Hiker's Journal - Tests: Level 4 Reading, "identify its features, one comparison, and the
brief reason given for that comparison")*
```

One tag line may cover a vocabulary set sharing one instruction line if every word comes from the same lesson.

## SECTION 1: STRUCTURE

### 1.0 Target length: 30-45 minutes per task Level

Each task Level's test is completable in 30-45 minutes at that Level; the classroom flow is roughly 30 minutes
of study-guide review immediately followed by the test in one period. Reference item counts, by position:
lowest task Level about 13 (6 vocabulary, 7 comprehension); each in-between Level about 12 (6 and 6, each with
its own CSV objective); highest about 12 (3 vocabulary, 9 comprehension), weighted toward fewer, longer
open-production items. When several lessons are in scope, divide these totals across the lesson-blocks (1.1),
letting the time estimate, not an equal split, be the constraint. Time scales differently by position (Quality
Standards §C5): quick items at the lowest Level, slow ones at the highest. For a wide cumulative scope, sample
representatively across lessons (never drop a whole lesson; never test every word of every lesson) and note in
the header which lessons were sampled versus fully covered. Estimate time per item by type and cut if a Level
exceeds 45 minutes. Budget real first-encounter reading time for each new passage.

### 1.1 Two sections, organized into lesson-blocks

**Section 1: Vocabulary & Idiom Mastery.** One lesson-block per lesson, headed with that lesson's name and topic,
presenting only that lesson's own sampled words, each tagged per 0.3.

**Section 2: Reading Comprehension.** Never reuse a lesson's anchor text or its Day 2 refresher text. Generate
**one new passage per lesson in scope**, unseen by the student: calibrated to the same band and Level via the
Lesson prompt's 0.2, on a topic unrelated to that lesson's anchor text, naturally reusing that lesson's target
vocabulary (and, where the band calls for it, a comparable idiom or footnote element per the Lesson prompt's 0.4
and 0.9). Reprint each passage in full with its own paragraph lettering, headed with its source lesson's name.
Comprehension items for that passage are tagged per 0.3 and grouped into the lesson's block immediately after
it, exercising that lesson's own Skill Spotlight.

**Sizing:** a per-lesson assessment sizes its single passage like a full anchor text. A cumulative assessment
sizes each passage to roughly 40-60% of a full anchor text's word count for that Level, never past the point it
reads as a thin fact list; if the Level's floor cannot be reached at reduced size, cap the number of lessons
sampled (1.0) rather than under-size every passage.

Why a new passage per lesson, not the anchor and not one merged passage: an assessment on the class's own text
proves recall, not transfer; one merged passage cannot tell a teacher which lesson a student struggled with; a
fresh, lesson-tagged passage per lesson proves transfer, answers which lesson, and stays removable.

**Highest task Level's cross-text synthesis (cumulative scope):** compare any two of the lesson passages
directly; no separate comparison passage. Choose two from different lessons with a genuine basis for comparison
and tag the item with both lessons. If either lesson is later removed (1.1a), regenerate the item against two
remaining passages.

**Per-lesson scope:** one lesson, one full-size passage, no cross-text synthesis (1.2 gives the substitute).

**Closed-book by exception only:** if a request explicitly specifies closed-book (testing memorized vocabulary as
a design choice), state it in the header and confine it to Section 1. Section 2 always prints its new passages.

### 1.1a Skipping a lesson from scope

Remove that lesson's block entirely: its Section 1 items, its passage and comprehension items, its study-guide
section (1.6), and its Scoring Guide row. Regenerate a cross-text synthesis item that used its passage. Do not
re-weight another lesson's items or invent untagged filler; a shorter, honestly scoped test is correct. Re-run the
1.0 estimate only if the drop is large enough to matter.

### 1.2 Task-Level task types

Task types escalate in the same direction as the Lesson prompt's task-Level roles (extension-down, native,
extension-up). Pull each Level's actual task type, the kind of move its Phase 2 matrix prompts and Phase 3 stems
asked for, and rebuild it against that lesson's new passage, inside every lesson-block independently.

- **Lowest task Level:** scaffolded, word-bank-supported tasks (matching, fill-in-the-blank with options, multiple
  choice), banks padded per Quality Standards §C4. At least one genuine interpretive item (§B). Credit any
  reasonable, text-supported answer on interpretive or opinion items rather than scoring strictly right or wrong.
- **Every in-between task Level:** no word bank; select or produce the correct word or answer from context plus
  the textual evidence or context clue used; short-answer comprehension requiring a specific detail.
- **Highest task Level:** open production: original sentence- or paragraph-level output with explicit reasoning
  about craft or technique, citing specific evidence from the new passage (a paragraph letter, a quoted phrase).
  Cumulative scope adds the cross-text synthesis item (1.1); per-lesson scope substitutes a second
  extended-reasoning item on the one passage (tracing how the Skill Spotlight's technique builds across it, or
  evaluating a writer's choice) so depth and count match the cumulative version.

### 1.3 Foundation Support check

If a source lesson used a Foundation Support layer, generate a lighter check for those students in the response
mode the lesson used (Quality Standards §B): picture-to-picture or picture-to-word matching, point-and-name, or a
teacher-observed checklist. Draw items from the lowest task Level's target vocabulary and, for a reading-response
item, that lesson's new passage (at Beginner, a new picture-supported label set built the same way), at the
reduced item count the lesson's own Foundation Support boxes used. Score as a completion checklist (demonstrated /
not yet), not a percentage. If no lesson in scope used one, skip this section; do not invent it.

### 1.6 Study guide (required, one per task Level)

One study guide per task Level in scope (plus a Foundation Support version if 1.3 applies), matched to that
Level's test content and reviewable in roughly 30 minutes immediately before the test.

- **Contents:** vocabulary and idiom review in the same lesson-blocks as the test, every tested word with its
  definition or gloss and one example sentence (reuse the lesson's own pre-teaching or refresher sentence where
  possible); a skill and anchor-text review entry per lesson restating its Skill Spotlight and what it looked
  like in that lesson's anchor text (never previewing the new passage's topic); at least one worked example per
  question type on that Level's test, written on different content from the same lessons, never an actual test
  item; a short self-check list at that Level's own register ("Can I explain one comparison the writer made?").
- **Must not leak or replace the test:** no test item verbatim or near-verbatim; no partial answer key; task-Level
  matched, not shared across Levels.
- **Length:** reviewable in about 30 minutes; trim example density before cutting vocabulary coverage.

## SECTION 2: FORMAT

### 2.1 One document, one section per task Level, plus study guides

Unless separate documents are requested, one test document with a clearly labeled section per task Level in the
band (a banner heading per section helps selective printing), plus a Foundation Support Check section if 1.3
applies, sub-headed by lesson-block. Study guides are separate documents, one per Level, named so the pairing is
obvious.

### 2.2 Required elements

- A name / task-Level-assigned / date header block naming Module, Band, and Set number, and listing the lessons
  in scope. For exactly one completed Set, save as `Set{N}_{Band}_Assessment.md` in that Set's folder
  (Conventions §D), with its student packet alongside; a checkpoint or multi-Set assessment is named and placed
  by scope, stated explicitly.
- An open-book / closed-book note (typically "open-book: new passages printed below").
- Section 1 before Section 2, every task Level in sequence lowest to highest, one lesson-block per lesson within
  each Level.
- Every item's Source lesson and Tests tag (0.3).
- Each lesson's full new passage with paragraph lettering, headed with its source lesson's name, immediately
  before that lesson's comprehension items.
- A teacher-facing Scoring Guide: point values per section and task Level broken down by lesson-block; the note
  that task Levels are graded by task-Level-internal percentage, never raw cross-Level comparison; which items
  are credited for reasonable text-supported answers; a rubric for every open-production item; the Foundation
  Support completion checklist if 1.3 applies, kept separate from percentage scoring.

### 2.3 Style

Quality Standards §E. Each task Level's items stay inside that Level's own ceiling from the Lesson prompt's 0.2;
the highest Level does not jump to a Proficient register just because it is the hardest section.

## SECTION 3: SELF-CHECK BEFORE FINALIZING

Run `shared/Generation_Quality_Standards.md` §F first (task Levels and own CSV rows, Module verb, Respectful
Tiers, item distinctness, no trivially easy items, answerable from the passage in front of the student, padded
banks and plausible distractors, time balance, counts, complete instructions, traceability). Then:

1. Every vocabulary and idiom item traces to a specific lesson's pre-teaching list (0.2)?
2. Every item carries both a Source lesson tag and a Tests tag in 0.3's print format?
3. Cumulative scope: every lesson in scope has its own block in every task-Level section, each removable per
   1.1a without editing any other lesson's content?
4. Each task Level inside 30-45 minutes (1.0); any departure from the reference counts a deliberate,
   time-estimated choice?
5. Each lesson's Section 2 passage brand new (same band and Level, unrelated topic, reusing that lesson's
   vocabulary), never its anchor or refresher text, never shared across lessons, printed in full with its own
   lettering (1.1)?
6. Each lesson's comprehension task exercises that lesson's own Skill Spotlight (1.1)?
7. Each Level's Section 1 and 2 content built from that Level's own completed matrix and stem content (0.1, 1.2)?
8. Highest Level: cross-text synthesis tagged with both lessons in cumulative scope, or the extended-reasoning
   substitute in per-lesson scope (1.1, 1.2)?
9. Foundation Support check generated if a source lesson used the layer, in the lesson's own response mode,
   scored as a checklist (1.3)?
10. A study guide per task Level, reviewable in about 30 minutes, in the test's lesson-blocks, free of verbatim
    items and leaked answers (1.6)?
11. Scoring Guide present with per-lesson-block point values, the internal-percentage note, credited-answer
    notes, and a rubric for every open-production item (2.2)?
