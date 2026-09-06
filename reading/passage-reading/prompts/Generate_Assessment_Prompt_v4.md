# Passage Reading Assessment Generation Prompt (v4)

Companion to the Passage Reading Lesson Generation Prompt (v2.5, Band-Calibrated). Updated to match v2.5's
band-scoped task-Level system: every assessed section is keyed to a specific task Level from that band's Task
Levels by Band table (Section 0.1 of the lesson prompt - 3 task Levels for a Beginner-band assessment, 4 for
Intermediate/Advanced/Proficient), not the old fixed three-tier Level A/B/C model. Which design template a task
Level's section uses (scaffolded / independent / open-production) is now set by its position among that band's
task Levels - lowest, highest, or in between - the same lowest/highest/in-between framing the lesson prompt
itself uses and that the Passage Reading Homework Generation Prompt was already updated to use. Generates a
differentiated assessment - one section per task Level actually present in the band, plus below-the-lowest-task-
Level Foundation Support where applicable - from already-completed lessons.

**Current version: v4.** For the full dated version history and the reasoning behind each change, see
`Changelog.md`.

Use this prompt to generate a differentiated reading assessment - one section per task Level in the relevant
band's table, plus a below-the-lowest-task-Level Foundation Support check where applicable - from a set of
already-generated lessons. Do not use this prompt to generate lessons, and do not use the lesson prompt to
generate assessments: the two are separate tools with separate inputs.

This prompt assumes the lessons already exist. It does not invent new anchor texts, vocabulary, or idioms: it
draws the assessment content from the specific lessons it is given. If no completed lessons are provided as
input, stop and ask for them before generating anything.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs before generating

- Which lessons are being assessed: the actual lesson content (anchor texts, target vocabulary,
  idioms/slang, Module, Band). Pull vocabulary and idiom lists directly from each lesson's Phase 1
  pre-teaching list; do not re-derive them from learningobjectives.csv or invent new ones.
- Scope: cumulative or per-lesson. A cumulative assessment covers multiple lessons (e.g. all lessons in a
  Module, or a mid-unit checkpoint); a per-lesson assessment covers a single 2-day cycle. Ask if this is not
  specified: the two produce very different-length documents.
- Band and task-Level structure: confirm the same band (per Section 0.1 of the lesson prompt) applies
  across all lessons being assessed. Do not combine lessons from two different bands into one assessment
  without flagging it; a lowest-task-Level task on a Beginner-band lesson and a lowest-task-Level task on an
  Intermediate-band lesson are not equivalent - different CSV Levels, different task-Level counts (3 vs 4) -
  and should not appear side by side without a clear heading distinguishing them.
- Which task Level each student or group actually completed: for every task Level being assessed (per
  the band's Task Levels by Band table), confirm whether the source lesson's Phase 2 Collaborative
  Multi-Level Investigation and Phase 3 oral output were completed at that task Level's standard task set, or
  - for students functioning below the lowest task Level - the Foundation Support layer described in
  Section 0.8-B of the lesson prompt. Build each task Level's assessment content from that task Level's
  actual completed tasks (its specific matrix items, its specific participation-mode stems), not from a
  generic assumption of what the lowest or highest task Level usually contains. If this is not specified and
  the source lesson contains a Foundation Support layer or multiple participation modes, ask before
  generating.
- Each source lesson's Skill Spotlight: the plain-language skill statement from Section 0.8-A of the lesson
  prompt (e.g. "noticing specific word choices that reveal a writer's attitude toward a place"). Section 2's
  comprehension task for that lesson's vocabulary must exercise this exact named skill on the new passage
  (see 1.1), not a different or broader reading skill. If a source lesson has no recorded Skill Spotlight (an
  older lesson predating Section 0.8-A), ask for one or fall back to the Module's own objective (0.1 above)
  as the closest available anchor.
- Each source lesson's own task-Level grounding: the exact Reading-modality `learningobjectives.csv` row
  (Level, Description) that lesson already cited for each task Level present, per the lesson's own Dynamic
  Tiered Framework grounding (Section 0.1 of the lesson prompt). Pull this directly from the lesson rather
  than re-deriving it from the Level number alone; this is the source for Section 0.3's Tests tag below, and it
  is what lets the assessment prove the CSV objective, not just a same-numbered task, was actually tested.

### 0.2 What this prompt does NOT do

- Does not alter the Module-objective alignment of the source lessons; if a source lesson's comprehension
  tasks drifted from its Module's objective (see Section 0.1 of the lesson prompt), fix the lesson first, not the
  assessment.
- Does not test content the lessons did not actually cover. If a vocabulary word or idiom appears in the
  assessment, it must trace back to a specific lesson's Phase 1 pre-teaching list.
- Does not test the vocabulary, idioms, or skill the lessons did not actually teach. Every word, idiom, and
  comprehension task type must trace back to a specific lesson's Phase 1 pre-teaching list, Phase 2/3 task
  content, or Skill Spotlight (0.1). It does, however, assess that content on a new passage rather than the
  original one; see the next bullet and Section 1.1.
- Does not assume a student remembers a text from a previous class period, and does not test the original
  anchor text's specific content at all. Every reading-comprehension item must be answerable using only
  the new passage printed in the assessment (Section 1.1); do not write an item that only works if the
  student recalls a plot or content detail from the lesson's own story, and do not quiz the specifics of that
  story even with the text hidden. A cumulative or mid-unit assessment in particular may be administered
  weeks after the lesson was taught.

### 0.3 Lesson tagging and objective traceability (every item)

Every item in Section 1 and Section 2 - vocabulary, idiom, and comprehension alike - must carry two pieces of
information printed directly on the assessment document itself, not just tracked internally by whoever generates
it:

- **Source lesson:** which specific completed lesson (number and topic, e.g. "Lesson 2: New Corner of Yoyogi
  Park") the item's content, passage, and skill all come from. Every item traces to exactly one lesson; an item
  that blends content from two lessons is not permitted, since it cannot be cleanly removed if one of those
  lessons drops out of scope (see 1.1a).
- **Tests:** a one-line citation of the specific `learningobjectives.csv` row the item is built to assess. For a
  Section 2 comprehension item, this is the same Reading-modality objective (Level + quoted or closely
  paraphrased Description) that lesson's task at that task Level was already built to satisfy, pulled per 0.1's
  last bullet - not re-derived from the Level number alone. For a Section 1 vocabulary item, cite the source
  lesson and Module rather than inventing a modality-specific objective for vocabulary knowledge itself,
  since individual vocabulary words are not themselves leveled CSV objectives.

This does two things an untagged, merged assessment cannot do. First, it makes the assessment's claim
checkable, item by item: a teacher (or the next run of this prompt) can confirm the test is actually measuring
what the CSV says that Level should have learned in that Module, not a same-difficulty substitute that happens
to look right. Second, combined with the lesson-block structure in 1.1, it makes the assessment decomposable
by lesson - if a lesson was skipped, taught out of order, or missed by a student, its tagged items can be
identified and removed as a group, with nothing left dangling in the rest of the test (see 1.1a).

**Print format:** place the tag directly beneath each item's prompt, in italics, e.g.:

```
3. What does the writer compare the mountain view to?
*(Lesson 6: A Hiker's Journal - Tests: Level 4 Reading, "identify its features, one comparison, and the
brief reason given for that comparison")*
```

For Section 1 vocabulary items sharing one instruction line (e.g. a fill-in-the-blank set), one tag line covering
the whole set is sufficient as long as every word in that set comes from the same lesson; do not merge words
from two lessons under one tag.

## SECTION 1: STRUCTURE

### 1.0 Target length: 30-45 minutes per task Level

Each task Level's test should be completable in 30-45 minutes by a student working at that task Level. This is a
hard sizing constraint, not a suggestion: the intended classroom flow is roughly 30 minutes of study-guide review
immediately followed by the test in a single class period, so an oversized test breaks the period, not just the
pacing.

Item counts should stay close to what was built for the sample assessment, assigned by position among the
band's task Levels, not by a fixed letter:

- **Lowest task Level:** around 13 items total (6 vocabulary + 7 comprehension).
- **Every task Level between lowest and highest:** around 12 items each (6 vocabulary + 6 comprehension).
  For a 4-task-Level band this applies to both of the band's native Levels - each gets its own ~12-item test,
  drawing on its own CSV objective, not a shared or merged one.
- **Highest task Level:** around 12 items (3 vocabulary + 9 comprehension), weighted toward fewer, longer
  open-production items since those take more time per item to answer.

When multiple lessons are in scope, these totals are divided across that task Level's lesson-blocks (1.1), not
multiplied by the number of lessons. Divide roughly evenly, but let the 30-45 minute time estimate (not an equal
split) be the actual constraint - a lesson whose comprehension item is a short-answer question can afford a
slightly larger share than one whose item is extended reasoning.

Time, not just item count, scales differently by position: the lowest task Level's items are quick (matching,
multiple choice, short fill-in), so it can carry slightly more items in the same 30-45 minutes. The highest task
Level's items are slow (extended paragraphs, cross-text synthesis), so it must carry fewer items even though
each one is worth more points.

If a request's scope (e.g. a cumulative assessment spanning many lessons) would naturally produce a longer
test, do not simply add more items. Instead, sample representatively across the lessons in scope (do not drop
entire lessons, but do not test every vocabulary word from every lesson either) and note in the assessment
header which lessons were sampled versus fully covered.

Before finalizing, estimate time per item by task type (a matching item is faster than a short-answer item, which
is faster than an extended paragraph) and check the running total against the 30-45 minute target for that task
Level. If a task Level's estimated time exceeds 45 minutes, cut items, don't just note the overage.

Each lesson's new passage (Section 1.1) adds page length, not necessarily extra administration time, but unlike
a reprinted anchor text, the student is reading it for the first time during the test. Budget real reading time for it,
the way the lesson prompt budgets Phase 2 reading time for a first encounter with the anchor text, not the few
seconds it takes to relocate a paragraph in a familiar text.

### 1.1 Two sections, every assessment, organized into lesson-blocks

**Section 1: Vocabulary & Idiom Mastery.** Organize by lesson, not as one merged word bank across every
lesson in scope: one lesson-block per lesson, each headed with that lesson's name and topic, presenting only
that lesson's own sampled words (per 1.0's sampling rule), each tagged per 0.3.

**Section 2: Reading Comprehension.** Do not reuse any lesson's anchor text, and do not reuse a lesson's Day 2
refresher text either. Generate one new passage per lesson in scope - not one passage shared across every
lesson - each one the student has not seen before: calibrated to the same band and Level via Section 0.2 of the
lesson prompt, on a topic unrelated to that lesson's own anchor text, naturally reusing that lesson's own target
vocabulary (and, where the band calls for it, a comparable idiom or footnote element, per Sections 0.4 and
0.9-B of the lesson prompt). Reprint each passage in full with its own paragraph lettering (Section 0.9), headed
with its source lesson's name, so items can reference "Paragraph C" precisely; this remains open-book by
default, per the reasoning below. Comprehension items built against a given lesson's passage are tagged per
0.3 and grouped into that lesson's block, immediately after its passage.

Organizing both sections this way - one self-contained block per lesson, each with its own tagged vocabulary
items, its own passage, and its own tagged comprehension items - is what makes a lesson's entire contribution
removable as a unit (1.1a), and what makes 0.3's Tests tags checkable against something the student is actually
looking at, rather than a shared passage no single tag can cleanly own.

**Sizing the per-lesson passages:** a per-lesson assessment (one lesson in scope) sizes its single passage like a
full anchor text at that Level (Section 0.2 of the lesson prompt). A cumulative assessment (multiple lessons)
sizes each lesson's passage down instead - target roughly 40-60% of a full anchor text's word count for that
Level - since comprehension time is now split across several shorter passages rather than one long one. Do not
shrink a passage past the point it reads as a thin fact-list (the same floor warning Section 0.2 of the lesson
prompt gives for anchor texts); if the Level's floor can't be reached at a reduced size within the time budget, cap
the number of lessons sampled (1.0) rather than under-sizing every passage to fit them all in.

Why a new passage per lesson, not the original anchor text, and not one merged passage: an assessment built
on a lesson's own anchor text, even reprinted in full, only proves a student can re-locate or recall details from a
story the whole class already read together - it does not prove the skill transferred. A single passage merging
vocabulary from several lessons proves something too, but not something a teacher can act on: if a student fails
part of it, there is no way to tell which lesson's material they actually struggled with. A fresh, lesson-tagged
passage per lesson, each exercising that specific lesson's Skill Spotlight (Section 0.8-A of the lesson prompt,
pulled per 0.1), proves the student can apply what that specific lesson taught to something genuinely new,
answers which lesson, and stays removable if that lesson drops out of scope.

**Highest task Level's cross-text synthesis (cumulative scope):** with one passage already generated per lesson,
the highest task Level's synthesis item compares any two of those lesson passages directly - a dedicated,
separate comparison passage is no longer needed. Choose two passages from different lessons whose content
gives a genuine basis for comparison, and tag the synthesis item with both source lessons (0.3). If either of
those two lessons is later removed from scope (1.1a), regenerate the synthesis item against two of the
remaining lessons' passages rather than leaving a comparison that references a passage no longer in the
document.

**Per-lesson scope:** unchanged - one lesson, one new passage sized to a full anchor text, no cross-text
synthesis at the highest task Level (1.2 gives the substitute).

**Closed-book by exception only:** if a request explicitly specifies closed-book (e.g., deliberately testing
memorized vocabulary recall as a design choice), state this plainly in the header and confine closed-book
treatment to Section 1. Section 2 (Reading Comprehension) defaults to reprinted new passages regardless of
the closed-book flag, since testing comprehension of a passage the student cannot see measures memory, not
reading skill.

### 1.1a Skipping a lesson from scope

If a lesson originally part of this assessment's scope must be excluded - not taught yet, a student missed it, or
the teacher chooses not to test it this cycle - remove that lesson's block entirely: its Section 1 vocabulary items,
its Section 2 passage and comprehension items, its study-guide section (1.6), and its row in the Scoring Guide
(2.2). If the removed lesson's passage was one half of the highest task Level's cross-text synthesis item (1.1),
regenerate that item against two of the remaining lessons' passages.

Do not patch the resulting gap by re-weighting another lesson's items to cover for the missing content, and do
not invent generic, untagged filler items to keep the item count steady. A shorter, honestly-scoped test is
correct; the whole point of tagging every item by lesson (0.3) is that removing one lesson should not require
touching any other lesson's block. Only re-run the 1.0 time estimate if the drop is large enough to matter (e.g.
one lesson out of a two-lesson cumulative assessment); dropping one lesson from a four- or eight-lesson
assessment usually leaves the remaining blocks' timing untouched.

### 1.2 Task-Level task types (apply within each lesson-block, both sections)

Task types must escalate in the same direction as the lesson prompt's own task-Level roles (extension-down /
native / extension-up, per its Relative Multi-Level Strategy section), not just get "harder" in an unstructured
way. Pull each task Level's actual task type - the kind of move the specific Phase 2 Collaborative Multi-Level
Investigation prompts and Phase 3 participation-mode stems asked that task Level's students to make in the
source lesson - and rebuild that same kind of task against that lesson's own new passage (1.1), not the original
anchor text and not another lesson's passage. An item at the highest task Level, for instance, should require the
same kind of synthesis that task Level's own matrix cell asked for in class, now demonstrated on the new
passage instead of the one already read together. This rule applies inside every lesson-block independently -
Lesson 2's lowest-task-Level item and Lesson 4's lowest-task-Level item both follow it, each against their own
passage.

- **Lowest task Level:** scaffolded, word-bank-supported tasks (matching, fill-in-the-blank with options,
  multiple choice). Include at least one genuine interpretive item, not fact-retrieval only (see Respectful
  Tiers below). Do not score this task Level's interpretive/opinion items strictly right-or-wrong; credit any
  reasonable, text-supported answer.
- **Every task Level between lowest and highest:** no word bank; requires selecting/producing the correct
  word or answer from context, plus identifying the textual evidence or context clue used. Short-answer
  comprehension questions requiring a specific detail from the text (not a vague answer) for full credit.
- **Highest task Level:** open production. Requires original sentence-level or paragraph-level output and
  explicit reasoning about craft/technique (not just content). In cumulative scope, also requires cross-text
  synthesis comparing two lesson passages in scope (see the cumulative-scope note in 1.1). In per-lesson
  scope, where only one new passage exists, cross-text synthesis is dropped; substitute a second
  extended-reasoning item on that one passage (e.g. tracing how a technique named in the Skill Spotlight
  builds across the passage, or evaluating a choice the writer made) so this task Level's item count and
  depth still match the cumulative version.

No item at any task Level may be answerable only from memory of a lesson's original anchor text (which is not
reprinted); every comprehension item must be answerable by reading that lesson's own new passage in Section
2 (1.1). This applies even to the highest task Level's open-production items: reasoning about craft or technique
should cite specific textual evidence from the new passage (a paragraph letter, a quoted phrase), not the
student's memory of the original story.

### 1.3 Respectful Tiers applies to assessment too

The Respectful Tiers principle from the lesson prompt (every task Level reaches the same essential
understanding, none is "the interesting one") applies to test design, not just lesson task design. Before
finalizing: does the lowest task Level's task set include at least one item where the student interprets or
expresses an opinion, not just scans for a fact? Would a student at the lowest task Level, having only taken their
own task Level's test, feel they were only tested on "the easy stuff" while every other task Level got to show real
understanding? If yes, add a genuine (simplified, scaffolded) interpretive item to the lowest task Level and
revise.

### 1.4 Module-objective alignment applies to assessment too

Test items must match the Module's actual skill (Describing, Explaining, Evaluating, Arguing, etc., see Section
0.1 of the lesson prompt), the same way lesson comprehension tasks must. A Describing-Module assessment
should ask students to describe, compare, and identify features and stated reasons, not summarize
cause-and-effect or evaluate a policy tradeoff, even if the anchor texts happen to touch on a topic (like
conservation) that could invite those questions. If the source lessons drifted into a neighboring Module's skill, do
not reproduce that drift in the assessment; flag it back to the lesson instead.

### 1.5 Below-the-Lowest-Task-Level Foundation Support Check

If a source lesson included a Foundation Support layer (Section 0.8-B of the lesson prompt) for students
functioning below the lowest task Level, generate an additional, lighter check for those students instead of
administering the standard lowest-task-Level test to them unmodified. This is not simply an easier version of
that test: it should mirror the response mode the student actually used in the lesson (pointing, matching,
non-verbal or minimally-verbal response), the same way the Foundation Support layer itself works.

- **Format:** picture-to-picture or picture-to-word matching, point-and-name, or a teacher-observed
  checklist, matching whatever below-the-lowest-task-Level response mode appeared in the source
  lesson's Foundation Support boxes.
- **Content:** draw items from the same target vocabulary as the lowest task Level's test and, for a
  reading-response item, that lesson's own new passage (1.1) rather than the original anchor text, at the
  same reduced item count the lesson itself used for Foundation Support (see the source lesson's own
  Foundation Support boxes for the actual scope, e.g. a 3-word subset rather than the full word list). At the
  Beginner band, where the anchor itself is a picture-supported label set, "new passage" means a new
  picture-supported label set built the same way.
- **Scoring:** a completion checklist (demonstrated / did not yet demonstrate, per item), not a percentage
  score, consistent with this layer not being meant to produce a numeric grade comparable to the lettered
  task Levels.

If no lesson in scope used a Foundation Support layer, skip this section entirely; do not invent one.

## SECTION 1.6: STUDY GUIDE (REQUIRED, ONE PER TASK LEVEL)

Every assessment generation request produces a study guide alongside the test, not just the test. Generate one
study guide per task Level in scope (3 for a Beginner-band assessment, 4 for Intermediate/Advanced/Proficient,
and a Foundation Support version if 1.5 applies), each matched to that task Level's actual test content and sized
to be reviewable in roughly 30 minutes, immediately before the test is administered in the same class period.

### 1.6.1 What the study guide contains

- Vocabulary and idiom review, organized in the same lesson-blocks as the test (1.1): every word and idiom
  tested in that task Level's Section 1, tagged with its source lesson (0.3), with its definition/gloss plus one
  example sentence (reuse the sentence from the lesson's pre-teaching frame or Day 2 refresher text where
  possible, rather than writing a new one).
- Skill and anchor-text review, one entry per lesson in scope: restate that lesson's Skill Spotlight in plain
  language and remind students what it looked like in that lesson's anchor text (a specific descriptive
  feature, comparison, or stated reason, per the Module-objective alignment in 1.4). Since the test itself uses
  brand new passages (Section 1.1), do not preview or hint at any new passage's topic or content here; the
  point is to prime the transferable skill, not the specific story each new passage tells.
- Sample items: at least one worked example per question type that appears on that task Level's test (e.g.
  one modeled vocabulary-in-context item for a task Level between lowest and highest, one modeled
  extended-description paragraph opening for the highest task Level), showing what a strong answer looks
  like. Do not reuse an actual test item as the worked example; write a parallel example using different
  content from the same lessons.
- A short self-check list the student can use during review (e.g. "Can I name two features of each place we
  read about? Can I explain one comparison the writer made?"), phrased at that task Level's own register
  per Section 0.2 of the lesson prompt.

### 1.6.2 Study guide must not leak or replace the test

- Do not include any test item verbatim, or any item close enough in wording that recognizing it would
  substitute for actually knowing the material.
- Do not make the study guide a partial answer key. Worked examples (1.6.1) model the skill and format,
  not the content that will be tested.
- The study guide is task-Level-matched, not a shared document: a study guide for the lowest task Level
  should not casually include the highest task Level's vocabulary or task framing (and vice versa), the same
  way the test itself keeps each task Level inside its own band ceiling.

### 1.6.3 Study guide length

Each task Level's study guide should be reviewable in roughly 30 minutes by a student at that task Level,
matching the 30-45 minute test length in 1.0 (30 minutes review immediately followed by the test, in one class
period). If a study guide is running long, trim example density before cutting vocabulary coverage: every tested
word must still appear in the guide.

## SECTION 2: FORMAT

### 2.1 Default: one document, one section per task Level, plus matching study guides

Unless the request specifies separate documents per task Level, produce a single test document with a clearly
labeled section per task Level actually present in this assessment's band (3 sections for a Beginner-band
assessment, 4 for Intermediate/Advanced/Proficient - a visual banner or heading per section is recommended for
quick sorting when printing/distributing selectively), plus a Foundation Support Check section if 1.5 applies.
Within each task-Level section, sub-headings mark each lesson-block (1.1) so a lesson can be located and
removed at a glance. Study guides (Section 1.6) are separate documents from the test, one per task Level, since
students review the study guide before the test is distributed. Name them so the pairing is obvious (e.g. "...
Assessment (Advanced Band, Levels 4-7).docx" and "... Study Guide - Levels 4-7.docx").

### 2.2 Required elements

- A name/task-Level-assigned/date header block, plus a list of which lessons are in scope for this
  assessment (by number and topic) so a reader can see the full scope at a glance before reading any
  section.
- A note on whether the assessment is open-book or closed-book. Since Section 2 now prints a new
  passage per lesson by default (Section 1.1), this note will typically read "open-book - new passages
  printed below" rather than pointing back to a separate packet.
- Section 1 (Vocabulary & Idiom Mastery) before Section 2 (Reading Comprehension), each with every task
  Level in scope presented in sequence, lowest task Level first through highest task Level last, and within
  each task Level, one lesson-block per lesson in scope (1.1).
- Every item's Source lesson and Tests tag, printed directly beneath the item, in the format given in 0.3.
- The full new passage for each lesson in scope, printed with paragraph lettering intact and headed with its
  source lesson's name (Section 1.1), positioned immediately before that lesson's block of comprehension
  items. Never a lesson's original anchor text, and never one passage standing in for more than one
  lesson.
- A Scoring Guide at the end (teacher-facing), covering:
  - Point values per section/task Level, broken down by lesson-block so a lesson's point contribution is
    visible and can be subtracted cleanly if that lesson is later dropped (1.1a).
  - Explicit note that task Levels are not meant to produce comparable raw scores: grade using
    task-Level-internal percentage (score / that task Level's total), not raw point comparison across
    task Levels, consistent with the lesson prompt's own Relative Multi-Level Strategy.
  - Any items that should be credited for reasonable/text-supported answers rather than a single
    correct answer (per 1.3).
  - A rubric (not just a point value) for any open-production or extended-response item.
  - If 1.5 applies: the Foundation Support Check's completion checklist, kept separate from the
    percentage-based scoring used for the lettered task Levels.

### 2.3 Style constraints

Reuse the lesson prompt's constraints where applicable: no em-dashes, prioritize clear instructions over
decorative language, keep each task Level's vocabulary/grammar inside the same complexity ceiling used for
that specific Level in the source lessons (Section 0.2 of the lesson prompt): the highest task Level's test item
should not suddenly require a Proficient-band (C1-C2) vocabulary or syntax jump just because it is the hardest
task Level in this assessment - it stays inside its own assigned CSV Level's ceiling.

## SECTION 3: SELF-CHECK BEFORE FINALIZING

- Does every vocabulary/idiom item trace back to a specific source lesson's pre-teaching list?
- Does the Module-objective alignment check (1.4) pass for every task Level, not just a task Level between
  lowest and highest?
- Does the Respectful Tiers check (1.3) pass: does the lowest task Level get genuine interpretive work?
- Is the scoring guide's task-Level-internal-percentage note present and is a rubric (not just a point value)
  provided for every open-production item?
- If cumulative: does the assessment draw from ALL lessons in scope, not just the most recent one, and does
  every lesson in scope get its own lesson-block in every task-Level section (1.1)?
- Does each task Level's test fall inside the 30-45 minute target (1.0)? If item counts don't match the
  reference range (lowest task Level ~13, each in-between task Level ~12, highest task Level ~12), was that
  a deliberate, time-estimated choice, not an oversight?
- Does a study guide exist for every task Level in scope, each reviewable in roughly 30 minutes,
  task-Level-matched, organized in the same lesson-blocks as the test, and free of verbatim test items or
  leaked answers (1.6)?
- Does each task Level's Section 1 and Section 2 draw from that task Level's own actual completed Phase
  2/Phase 3 task content, not a generic version of the task Level (0.1, 1.2)? If the source lesson included a
  Foundation Support layer, was a Section 1.5 check generated for it?
- Is Section 2's passage for each lesson a brand new one (calibrated to the same band/Level, unrelated
  topic, reusing that lesson's own target vocabulary), never that lesson's own anchor text or Day 2 refresher
  text, and never shared across two lessons (1.1)?
- Is every new passage printed in full, with its own paragraph lettering and source-lesson heading, rather
  than assumed available or left to memory (1.1)?
- Does every comprehension item avoid relying on memory of the original story - could a student answer it
  correctly only by reading that lesson's own new passage in front of them (1.2)?
- Does Section 2's comprehension task for each lesson exercise that lesson's own Skill Spotlight, the same
  named skill the lesson taught, rather than a generic or different comprehension skill (0.1, 1.1)?
- **(New)** Does every Section 1 and Section 2 item carry both a Source lesson tag and a Tests tag citing the
  specific CSV row it assesses, in the print format given in 0.3, rather than being left to implicit inference?
- **(New)** Is Section 2 built as one self-contained lesson-block per lesson (its own passage, its own tagged
  items) rather than one passage shared across several lessons, such that any single lesson's block could
  be removed per 1.1a without editing any other lesson's content?
- **(New)** If the highest task Level's cross-text synthesis item draws on two lesson passages, are both
  source lessons tagged on that item (0.3), and if either of those lessons was removed from scope, was the
  synthesis item regenerated against two of the remaining lessons rather than left referencing a dropped
  passage (1.1, 1.1a)?
- If per-lesson scope: was cross-text synthesis dropped for the highest task Level in favor of the
  extended-reasoning substitute, rather than an invented, unrelated second passage (1.2)?
- Does the assessment include exactly the right number of task-Level sections for its band (3 for Beginner,
  4 for Intermediate/Advanced/Proficient), each grounded in that specific Level's own CSV objective and
  actual completed classwork, not an invented difficulty curve or generic task-Level assumption?
