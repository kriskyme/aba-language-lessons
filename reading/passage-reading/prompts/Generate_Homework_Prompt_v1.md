# Passage Reading Homework Generation Prompt (v1)

Companion to the Passage Reading Lesson Generation Prompt (v2.5, Band-Calibrated). Updated to match v2.5's
band-scoped task-Level system: every homework section is keyed to a specific task Level from that band's Task
Levels by Band table (Section 0.1), not the old fixed three-tier Level A/B/C model. Generates one homework
assignment from a single completed 2-day lesson cycle, for the general (non-TOEFL) track.

Companion to the Passage Reading Lesson Generation Prompt, the same relationship the Passage Reading
Assessment Generation Prompt and the Passage Reading TOEFL Track Extension Prompt already have to it -
though as of this revision those two companions are still written against v2.4's Tier A/B/C model (see the Master
Generation Document for current sync status). Use this prompt only after a lesson's Day 1 and Day 2 already
exist. Do not use this prompt to generate lesson content, and do not use the lesson prompt to generate
homework: the input is always an already-completed 2-day cycle, supplied in full (both days), not a topic or Level
on its own.

In practice, a generation request supplies the completed Day 1 and Day 2 lesson content directly ("create
homework based on these lessons," with the lesson text attached or pasted in) rather than naming a Level or
Module and asking this prompt to look anything up. If no completed lesson is provided, stop and ask for it before
generating anything.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs before generating

- The source lesson, Day 1 and Day 2 in full: the anchor text with its paragraph lettering, the Phase 1
  target vocabulary and idiom/slang list, the Skill Spotlight (Section 0.8-A of the lesson prompt), Module,
  and Band. Pull all of this directly from the completed lesson; do not invent a new vocabulary word,
  topic, or skill focus.
- Timing: which point in the cycle this homework is assigned at. Default to after Day 1, due at the start of
  Day 2 (see 0.2 for why). If the request specifies otherwise, follow it and state the assumption in the packet
  header.
- Task-Level information: which task Level (per Section 0.1 of the v2.5 lesson prompt's Task Levels by Band
  table - 3 task Levels for a Beginner-band lesson, 4 for Intermediate/Advanced/Proficient) each student or
  group is working at, or below-the-lowest-task-Level Foundation Support (Section 0.8-B of the lesson prompt),
  the same input the Assessment Generation Prompt requires (once it is updated to match; see note above).
  Build each task Level's homework from what that task Level is actually doing in class, not a generic
  assumption.
- Track: confirm the student is on the general track, not the TOEFL track. TOEFL-interested students use
  the companion TOEFL Track Extension Prompt for their homework instead (see 1.4); do not generate both
  for the same student on the same cycle.

### 0.2 Timing determines what content is available to draw from

Default: assigned after Day 1, due at the start of Day 2. At this point the anchor text, target vocabulary, and
idiom/slang have been taught, and the Skill Spotlight has been named and practiced once, through Day 1's own
STOP & CHECK items. Day 2's refresher text, tiered Collaborative Multi-Level Investigation, oral output protocol,
and in-class Closing Transfer Check have not happened yet. Do not draw homework content from any of that
Day 2 material under this default. Part 2 (1.1 below) can still legitimately ask for a light, individual, written
skill-application task, since the Skill Spotlight was already named and modeled on Day 1; it does not need to wait
for Day 2's fuller investigation to exist.

Alternative: assigned after Day 2 (full cycle complete). Only under this timing may Part 2 explicitly build on or
extend the student's own in-class Closing Transfer Check response, since that response now exists. State this
timing explicitly in the packet header, since it changes what Part 2 can reference.

If timing is not specified, default to after-Day-1: that is this prompt's primary designed use, consolidating
vocabulary and the named skill before Day 2's deeper work, rather than review once the cycle has already
closed. Note the assumption in the header either way.

## SECTION 1: STRUCTURE

### 1.0 Target length: 15-20 minutes, one sitting

Homework is light, individual reinforcement, not a scaled-down version of the cumulative assessment. Size the
whole assignment, across both parts below and all task Levels, to run in roughly 15-20 minutes for a student
working at their own task Level, matching the same time budget the TOEFL Track Extension Prompt already
uses for its own extension packet (Section 2.2 of that prompt), so a class running both tracks side by side stays
comparable in workload.

### 1.1 Two parts, every homework assignment, one section per task Level

Every completed lesson has a specific set of task Levels (3 for a Beginner-band lesson, 4 for
Intermediate/Advanced/Proficient), each grounded in its own CSV objective per Section 0.1 of the lesson prompt.
Homework needs one Part-1/Part-2 section per task Level actually present in that lesson's band, not a fixed set
of three named tiers - a Beginner-band lesson's homework has 3 sections, an Advanced-band lesson's has 4.
Which design template a task Level's section uses is determined by its position among that band's task Levels,
not by a letter name:

- The **lowest task Level** in the band's table always uses the most-scaffolded design.
- The **highest task Level** in the band's table always uses the most-independent design.
- Every task Level **between** the lowest and highest (this includes both of the band's native Levels for a
  4-task-Level band, and the second-lowest Level for a Beginner-band lesson) uses the middle design.
- **Below the lowest task Level** (Foundation Support, where applicable) always uses the non-verbal design.

This is the same lowest/highest/in-between framing the v2.5 lesson prompt itself uses throughout (see its
self-check items 6, 7, and 14), extended here to homework design instead of in-class task design. Where a band
has two task Levels using the same middle design (every band except Beginner), give each its own section
grounded in its own CSV objective; only the design template is shared between them, not the content.

**Part 1: Vocabulary & Idiom in Production.** Select 3-4 words or idioms from the cycle's Phase 1 pre-teaching
list, not the full 4-6 word set; homework tests application of a working subset, not full coverage the way the
cumulative assessment's Section 1 does. Require original sentences, not fill-in-the-blank recognition:
recognizing a word in a pre-written sentence is a different, easier skill than producing one, and this program has
already moved away from recognition-only tasks everywhere else (Assessment Generation Prompt, Sections
1.1-1.2).

- **Lowest task Level:** a word bank plus sentence starters or frames (reuse a frame family from the lesson
  itself where one exists). Credit any reasonable, correctly-used sentence; do not require a single exact
  answer.
- **Every task Level between lowest and highest:** independent original sentences, one per word, no
  starter provided.
- **Highest task Level:** combine 2-3 of the words into one connected short paragraph (3-5 sentences) on a
  topic of the student's own choice.
- **Below-the-lowest-task-Level Foundation Support** (where applicable): a non-verbal or minimally-verbal
  version matching how that student worked in class (Section 0.8-B of the lesson prompt): point-and-name
  with a caregiver from 2-3 picture cards, match a word to a picture, or draw a picture illustrating one
  target word, rather than writing sentences.

**Part 2: Skill Practice**, applying the lesson's own Skill Spotlight to something new. Restate the Skill
Spotlight in the exact plain language it was named in on Day 1 Phase 1 of the source lesson; do not paraphrase
it into a different or broader skill. Ask the student to apply that named skill to something in their own life,
surroundings, or experience, new content, not a re-analysis of the anchor text. This is a light, individual, written
preview of the same move the lesson's own Closing Transfer Check formalizes in class on Day 2: producing a
new instance of the skill, not recognizing it again in a text already read (Section 0.8-A of the lesson prompt). Do
not ask students to re-analyze the anchor text here; Phase 3 already did fact-checking and vocabulary-in-context
work on it in class, and repeating that at home is graded busywork without new information for the teacher.

- **Lowest task Level:** 1-2 sentences, using a sentence frame that mirrors the one used in the lesson's own
  Closing Transfer Check design.
- **Every task Level between lowest and highest:** 2-3 sentences, independent, no frame provided.
- **Highest task Level:** 3-4 sentences, including a brief explanation of why the specific word or detail they
  chose reveals what it does, matching the reasoning-about-craft standard used at the highest task Level
  elsewhere in this program.
- **If assigned after Day 2** (the alternative timing in 0.2): instead of a first attempt, ask the student to write
  a second, different example applying the same skill, extending rather than repeating their in-class Closing
  Transfer Check response. This applies at every task Level.

### 1.2 Respectful Tiers applies to homework too

The same principle used throughout this program's lessons and assessments (every task Level reaches the
same essential understanding, none is "the interesting one") applies here. The lowest task Level's homework
must include a genuine, simplified skill-application item in Part 2, not vocabulary practice alone while every
other task Level gets the only real skill work. Before finalizing, check: would a student at the lowest task Level,
comparing their homework to a classmate's at the highest task Level, feel they only ever practiced word lists?

### 1.3 Grading is light-touch, not the assessment's scoring system

Homework is checked for genuine attempt and correct use, not scored with the tier-internal-percentage system
the Assessment Generation Prompt uses for the cumulative test (that prompt's Section 2.2). Provide a short
completion checklist per task Level instead of a rubric or point values, 2-3 plain criteria such as "used the word
correctly," "sentence connects to the named skill," "attempted independently." Four of these across two weeks
are meant to stay low-stakes; the cumulative assessment at the end of the module already carries the graded
weight for the unit.

### 1.4 TOEFL-track students use the other companion prompt

For students working the TOEFL track, generate their homework with the TOEFL Track Extension Prompt
instead of this one: that prompt already produces a Complete the Words plus Read an Academic Passage
packet from the same completed lesson, explicitly sized (15-20 minutes) and pre-approved for delivery
as "an extension/homework packet" (Section 0.2 of that prompt). Do not generate both this prompt's homework
and the TOEFL packet for the same student on the same cycle: that duplicates the reinforcement work and
doubles a single cycle's homework time commitment for no added benefit.

## SECTION 2: FORMAT

### 2.1 One document per homework assignment

Produce a single document with a clearly labeled section per task Level actually present in this lesson's band (3
sections for a Beginner-band lesson, 4 for Intermediate/Advanced/Proficient), plus a Foundation Support section
if 1.1 applies, matching the task-Level-banner convention used in the lesson and assessment documents. No
separate answer key is required: Part 1 has no single correct answer to key against (credit reasonable, correct
usage), and Part 2 is checked against the completion checklist in 1.3, not scored against a key.

### 2.2 Required elements

- A header naming the source lesson (Module, Band, lesson topic), which point in the cycle it is
  assigned at (Day 1 or Day 2, per 0.2), and an estimated completion time.
- Part 1 (Vocabulary & Idiom in Production) before Part 2 (Skill Practice), each task-Level section labeled
  in sequence, lowest task Level first through highest task Level last, then Foundation Support if applicable.
- The Skill Spotlight restated verbatim from the source lesson, directly above Part 2's prompt, so the
  student sees the exact same framing they heard in class.
- A completion checklist per task Level (1.3), for the teacher, not a percentage-based rubric.

### 2.3 Style constraints

Reuse the program's constraints: no em-dashes, clear instructions over decorative language, each task Level's
vocabulary/grammar inside the same complexity ceiling used for that Level in the source lesson (Section 0.2 of
the lesson prompt).

## SECTION 3: SELF-CHECK BEFORE FINALIZING

- Does every vocabulary/idiom item in Part 1 trace back to the source lesson's Phase 1 pre-teaching list?
- Does Part 2 use the exact Skill Spotlight named in the source lesson's Day 1 Phase 1, not a different or
  invented skill?
- Does Part 2 ask for a genuinely new application (something in the student's own life or experience), not a
  re-analysis of the anchor text already covered in Phase 3?
- Does the packet respect the timing assumption in 0.2: if assigned after Day 1 only, does it avoid requiring
  Day 2 content (refresher text, matrix, oral debate) the student has not encountered yet?
- Does the lowest task Level get a genuine, simplified skill-application item in Part 2, not vocabulary
  practice alone (Respectful Tiers, 1.2)?
- Is grading light-touch, a completion checklist, not the assessment's tier-internal-percentage system (1.3)?
- Is the whole assignment sized to run in roughly 15-20 minutes (1.0)?
- If the student is on the TOEFL track, was the TOEFL Track Extension Prompt used instead of this one,
  not both (1.4)?
- If the source lesson includes a Foundation Support layer, was an appropriately non-verbal or
  minimally-verbal version of Part 1 generated for that student (1.1)?
- Does the homework include exactly the right number of task-Level sections for its band (3 for Beginner, 4
  for Intermediate/Advanced/Proficient), each grounded in that specific Level's own CSV objective from the
  source lesson, not an invented difficulty curve?
