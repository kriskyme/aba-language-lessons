# Academic Writing Homework Generation Prompt (v3)

Companion to `Generate_Lesson_Prompt_v5.md`. Generates one homework assignment from a single completed (or
partially completed) Academic Writing lesson - one lesson within a Beginner Set (4 lessons) or an
Intermediate/Advanced/Proficient Module Pair (8 lessons - see `Generate_Lesson_Prompt_v5.md`'s "THE MODULE PAIR").
Use this prompt only after at least Day 1 of a lesson already exists. Do not use this prompt to generate lesson
content, and do not use the Lesson prompt to generate homework: the input is always the lesson content generated
so far, supplied in full, not a topic or Band on its own. If no lesson content is provided, stop and ask for it
before generating anything.

**Current version: v3.** For version history, see `Changelog.md`. (v3 extends the timing checkpoints below from
four to eight for Intermediate/Advanced/Proficient, matching `Generate_Lesson_Prompt_v5.md`'s Module Pair - see
`shared/Program_Conventions.md` §C. Beginner keeps the original four checkpoints, "after Lesson 1/2/3/4," from v2
unchanged. See 0.2 below for the full eight-checkpoint content-availability table.)

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs before generating

- The source lesson's content generated so far, in full: the Scenario, the Grammar Focus A/B (and Essay Focus
  A/B, where the Band reaches Essay Composition) content already taught, the Leveled Mentor Ladder, the Skill
  Spotlight (Lesson 1, Day 1 Phase 1 of the Lesson prompt - or Lesson 5, Day 1 Phase 1 for
  Intermediate/Advanced/Proficient positions 5-8), Module(s), and Band. Pull all of this directly from the
  completed lesson content; do not invent a new grammar point, Scenario detail, or skill focus.
- Timing: which lesson has been reached when homework is assigned - Beginner: which of the Set's 4 lessons (see
  0.2); Intermediate/Advanced/Proficient: which of the Module Pair's 8 lessons (see 0.2's extended table). Default
  to **after Lesson 2** (Beginner) or **after Lesson 6** (Intermediate/Advanced/Proficient - the Pair-position
  equivalent midpoint, per 0.2), due before the next drafting/revision lesson begins. If the request specifies a
  different point, follow it and state the assumption in the packet header.
- Task-Level information: which task Level (per `Generate_Lesson_Prompt_v5.md` Section 0.1's Task Levels by
  Band table) each student or group is working at, or below-the-lowest-task-Level Foundation Support (Section
  0.5 of the Lesson prompt). Build each task Level's homework from what that task Level is actually doing in
  class, not a generic assumption.

### 0.2 Timing determines what content is available to draw from

**Beginner (4-lesson Set), unchanged from v2:**

- **After Lesson 1** (Grammar Focus A taught, Leveled Mentor Ladder seen, frame-regime rounds done): only Focus A
  content and the Mentor Ladder are available. Focus B, the confusable pair, and any prewriting have not
  happened yet - do not draw on them.
- **After Lesson 2 (default):** Focus A and Focus B (and, where the Band reaches Essay Composition, Essay Focus
  A/B) have both been taught, and Lesson 2's prewriting is done. Drafting itself has not started. This is the
  intended primary use of this prompt, the same consolidate-before-deeper-work rationale Reading's Homework
  prompt uses at its own midpoint: both grammar focuses are fresh, and homework here can meaningfully prime
  Lesson 3's drafting without asking the student to draft the actual Scenario piece at home unsupervised.
- **After Lesson 3** (a full draft exists, self-edit checklist pass done): the student's own in-progress draft
  exists. Part 2 (1.1 below) may extend or apply the checklist to a fresh instance rather than only warming up
  toward a first draft.
- **After Lesson 4** (full Set complete, published, Closing Transfer Check done): Part 2 may extend the student's
  own in-class Closing Transfer Check response, the same way Reading's alternate timing works.

**Intermediate/Advanced/Proficient (8-lesson Module Pair), new in v3:** the same content-availability logic
extends across both Modules. Positions 1-4 read exactly like Beginner's checkpoints above (substitute "Pair
position" for "Lesson"), with one difference at position 4: the draft is complete and self-revised but **not
published** - do not draw on a "finished, published piece" framing at this checkpoint, only a completed draft
handed off to Module N+1.

- **After Pair position 4** (Module N's Set complete: draft finished, self-revised, handed off - not published):
  Part 2 may extend the student's own in-class hand-off note or draft, but must not imply the piece is finished.
- **After Pair position 5** (re-engagement done, Module N+1's Focus A taught): only Module N+1's Focus A content
  is newly available, on top of everything from positions 1-4.
- **After Pair position 6 (default for this Band):** Module N+1's Focus A and Focus B (and Essay Focus A/B,
  where applicable) have both been taught, and the revision-plan is done. Revision/expansion drafting has not
  started. Same consolidate-before-deeper-work rationale as Beginner's own default checkpoint.
- **After Pair position 7** (revision/expansion draft complete, merged self-edit done): the student's own
  in-progress revised draft exists, now reflecting both Modules' focuses.
- **After Pair position 8** (Module Pair complete, published, Closing Transfer Check and Module N+1's own
  CSV-verb task both done): Part 2 may extend either the Closing Transfer Check response or the separate
  CSV-verb task, the student's choice.

If timing is not specified, default to after Lesson 2 (Beginner) or after Pair position 6
(Intermediate/Advanced/Proficient) and note the assumption in the header either way.

## SECTION 1: STRUCTURE

### 1.0 Target length: 15-20 minutes, one sitting

Homework is light, individual reinforcement, not a scaled-down version of the cumulative assessment (see
`Generate_Assessment_Prompt_v3.md`). Size the whole assignment, across both parts and all task Levels, to run in
roughly 15-20 minutes for a student working at their own task Level.

### 1.1 Two parts, one section per task Level, design keyed to that Level's own regime

Every completed lesson has a specific set of task Levels (3 for Beginner, 4 for Intermediate/Advanced/
Proficient), each grounded in its own CSV objective. Homework needs one Part-1/Part-2 section per task Level
actually present in the lesson's Band, not a fixed set of named tiers.

**Unlike Reading, where a homework section's design is chosen purely by the task Level's position (lowest/
highest/in-between) in the Band's own range, Writing's per-Level design is keyed to that Level's own composition
regime** (`Generate_Lesson_Prompt_v5.md` Section 0.1: Guided Frame Composition, Levels 1-3; Paragraph
Composition, Levels 4-5; Essay Composition, Levels 6-8). Position alone is not a reliable guide here, because the
frame/paragraph and paragraph/essay regime boundaries do not move smoothly with position the way Reading's single
task range does - a Band's lowest task Level can be frame-regime (Intermediate's Level 2) while its highest is
essay-regime (Advanced's Level 7), two entirely different output shapes, not two depths of the same one. Regime
therefore determines the section's design template directly:

- **Frame-regime task Levels (1-3, where present in the Band):** the most-scaffolded design - a word bank plus
  the lesson's own sentence frame(s), reused verbatim. Credit any reasonable, genuinely-chosen word; do not
  require a single exact answer.
- **Paragraph-regime task Levels (4-5):** independent original sentences using the target Focus A/B items, no
  frame provided.
- **Essay-regime task Levels (6-8):** combine 2-3 target items (Focus A/B and, where taught, Essay Focus A/B
  cohesive devices) into one connected short paragraph, not a full essay - homework stays within the 15-20 minute
  target even at the highest task Level; a full essay draft belongs to Lesson 3 in class, not to homework.
- **Below-the-lowest-task-Level Foundation Support** (where applicable): a non-verbal or minimally-verbal version
  matching how that student worked in class (Lesson prompt Section 0.5): point-and-name from 2-3 picture cards,
  match a word to a picture, or draw a picture illustrating one target word, rather than writing sentences.

Where a Band has two task Levels sharing the same regime (e.g. Intermediate's Levels 4 and 5, both Paragraph
Composition), give each its own section grounded in its own CSV objective; only the design template is shared
between them, not the content.

**Part 1: Grammar Focus in Production.** Select 2-3 items from the Focus A content taught so far (plus Focus B
items, if the timing checkpoint in 0.2 has reached Lesson 2 or later) - not the full grammar-focus bank, the same
"working subset, not full coverage" principle Reading's homework uses for vocabulary. Require original
sentences or a completed frame, not fill-in-the-blank recognition of a pre-written sentence: producing is a
different, harder skill than recognizing, and this program favors production everywhere else it can.

**Part 2: Skill Practice**, applying the lesson's own Skill Spotlight to a new instance of the Scenario's
underlying task, not the Scenario's own specific object/situation already covered in class. Restate the Skill
Spotlight in the exact plain language it was named in on Lesson 1, Day 1 Phase 1; do not paraphrase it into a different or
broader skill. This is the Writing equivalent of Reading's "new application, not re-analysis of the anchor text"
rule: a student who described "my phone case" in class describes a different object of their own at home, using
the same comparison-plus-reason skill, not the same object again.

- **Frame-regime task Levels:** one or two more rounds of the lesson's own frame, on a new object/picture of the
  student's choosing (or a second provided picture), the same scaffolding as in class.
- **Paragraph-regime task Levels:** 2-4 sentences on a new object/situation, including the Level's own required
  feature (per Lesson prompt Section 0.2 - e.g. Level 4's one comparison plus one explicit reason).
- **Essay-regime task Levels:** one paragraph (not a full essay - see the length note in 1.1 above) applying
  Focus A/B and, where a structural element has already been taught by this checkpoint (a hook, a topic
  sentence), that one element, on a new instance of the Scenario's underlying situation.
- **If assigned after Lesson 3 or Lesson 4** (0.2's later checkpoints): instead of a first attempt, ask the student to
  extend or apply their own in-progress draft's or Closing Transfer Check's skill to a second, different
  instance, rather than repeating the same first-attempt framing. This applies at every task Level.

### 1.2 Respectful Tiers applies to homework too

The lowest task Level's homework must include a genuine, simplified skill-application item in Part 2, not
grammar-item practice alone while every other task Level gets the only real writing work. Before finalizing,
check: would a student at the lowest task Level, comparing their homework to a classmate's at the highest task
Level, feel they only ever practiced isolated words or sentences?

### 1.3 Grading is light-touch, not the assessment's rubric

Homework is checked for genuine attempt and correct use, not scored against `Generate_Assessment_Prompt_v3.md`'s
rubric. Provide a short completion checklist per task Level instead, 2-3 plain criteria such as "used the target
grammar item correctly," "sentence/paragraph is about a new object, not the one from class," "attempted
independently." Homework across the cycle stays low-stakes; the end-of-lesson assessment carries the graded
weight.

## SECTION 2: FORMAT

### 2.1 One document per homework assignment

Produce a single document with a clearly labeled section per task Level actually present in this lesson's Band,
plus a Foundation Support section if 1.1 applies. No separate answer key is required: Part 1 credits reasonable,
correct usage rather than keying against one exact answer, and Part 2 is checked against the completion
checklist in 1.3, not scored against a key.

### 2.2 Required elements

- A header naming the source lesson (Module, Band, Scenario), which day the lesson has reached when this is
  assigned (per 0.2), and an estimated completion time.
- Part 1 (Grammar Focus in Production) before Part 2 (Skill Practice), each task-Level section labeled in
  sequence, lowest task Level first through highest task Level last, then Foundation Support if applicable.
- The Skill Spotlight restated verbatim from the source lesson, directly above Part 2's prompt.
- A completion checklist per task Level (1.3), for the teacher, not a percentage-based rubric.

### 2.3 Style constraints

Reuse the program's constraints: no em-dashes, clear instructions over decorative language, each task Level's
vocabulary/grammar inside the same complexity ceiling used for that Level in the source lesson (Lesson prompt
Section 0.2).

## SECTION 3: SELF-CHECK BEFORE FINALIZING

- Does every grammar item in Part 1 trace back to Focus A (and, where the timing checkpoint allows, Focus B)
  content actually taught in the source lesson so far?
- Does Part 2 use the exact Skill Spotlight named in the source lesson's Lesson 1, Day 1 Phase 1, not a different or
  invented skill?
- Does Part 2 ask for a genuinely new object/situation, not the Scenario's own specific object already covered
  in class?
- Does the packet respect the timing checkpoint in 0.2: does it avoid drawing on content (Focus B, prewriting, a
  draft, the Closing Transfer Check) the student has not reached yet?
- Is each task Level's design template keyed to that Level's own composition regime (frame/paragraph/essay),
  not just its position in the Band's range?
- Does the lowest task Level get a genuine, simplified skill-application item in Part 2, not grammar-item
  practice alone (Respectful Tiers, 1.2)?
- Is grading light-touch, a completion checklist, not the assessment's rubric (1.3)?
- Is the whole assignment sized to run in roughly 15-20 minutes (1.0), including at the essay-regime task
  Levels, where Part 1's combining task stays a short paragraph, not a full essay?
- Does the homework include exactly the right number of task-Level sections for its Band (3 for Beginner, 4 for
  Intermediate/Advanced/Proficient), each grounded in that specific Level's own CSV objective from the source
  lesson?
- If the source lesson includes a Foundation Support layer, was an appropriately non-verbal or minimally-verbal
  version of Part 1 generated for that student?
