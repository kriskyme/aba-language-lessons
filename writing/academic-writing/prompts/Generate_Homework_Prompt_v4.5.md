# Academic Writing Homework Generation Prompt (v4.4)

Companion to the Academic Writing Lesson Generation Prompt. Generates one homework assignment from a single
completed or partially completed lesson within a Beginner Set (4 lessons) or an Intermediate/Advanced/Proficient
Module Pair (8 lessons): one section per task Level in the band, each keyed to that Level's composition regime.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`
alongside it. Quality Standards §A-§C govern every item and are not restated. This prompt states only what is
specific to Writing homework.

**Current version: v4.3.** History: `Changelog.md`.

**Input:** the lesson content generated so far, in full (the Scenario, the Grammar Focus A/B and Essay Focus A/B
content taught so far, the Leveled Mentor Ladder, the Skill Spotlight, Module(s), Band). If none is provided,
stop and ask. Never generate lesson content from this prompt.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs

- The lesson content as above; invent no grammar point, Scenario detail, or skill.
- **Timing:** which lesson has been reached (Beginner: Lesson 1-4; others: Pair position 1-8). Default: after
  Lesson 2 (Beginner) or after Pair position 6, due before the next drafting or revision lesson. State the
  assumption in the header.
- **Task-Level information:** which Level each student is working at, or Foundation Support.

### 0.2 Timing determines what content is available

Beginner (or Pair positions 1-4, with one difference at 4):
- **After Lesson 1:** Focus A and the Mentor Ladder only. No Focus B, confusable pair, or prewriting.
- **After Lesson 2 (default):** Focus A and B (and Essay Focus A/B where taught) and the prewriting. Drafting has
  not started; homework primes Lesson 3 without asking the student to draft the Scenario piece at home.
- **After Lesson 3:** the student's draft of the Module's part and its self-edit pass exist; Part 2 may apply the
  checklist to a fresh instance of that part (a body paragraph, a paragraph), never the whole piece.
- **After Lesson 4:** Beginner: the piece is published; Part 2 may extend the Closing Transfer Check response. Pair
  position 4: the Module's part is complete and self-revised but **not published**; Part 2 may extend that
  part, never the other Module's part and never implying the piece is finished.

Pair positions 5-8 extend the same logic with Module N+1's content:
- **After 5:** Module N+1's Focus A newly available, on top of positions 1-4.
- **After 6 (default):** Module N+1's Focus A and B (and Essay Focus where applicable) and the revision plan.
- **After 7:** both parts exist and have been checked together; Part 2 may practice Module N+1's part on a fresh
  instance (a hook and thesis for a given pair of topics; a closing move), never the assembled piece.
- **After 8:** the piece is published; Part 2 may extend either the Closing Transfer Check response or the separate
  Module N+1 verb task.

## SECTION 1: STRUCTURE

### 1.0 Target length: 15-20 minutes, one sitting

Light, individual reinforcement across both parts and all Levels, sized to 15-20 minutes at the student's own
Level, including at essay-regime Levels.

### 1.1 Two parts, one section per task Level, design keyed to regime

One Part 1 / Part 2 section per task Level, each grounded in its own CSV objective. Unlike Reading, the design
template is keyed to the Level's **composition regime** (Lesson prompt 0.1), not its position, because the
frame/paragraph and paragraph/essay boundaries do not move with position (Intermediate's lowest Level is
frame-regime; Advanced's highest is essay-regime).

- **Frame-regime Levels (1-3):** the most scaffolded design: a word bank plus the lesson's own frame verbatim,
  completed once, plus one item in a different shape from the Lesson prompt's 0.4d bank (choose what fits, fix
  the wrong word, better of two); never the frame several times (Quality Standards §D10). Credit any
  reasonable, genuinely chosen word.
- **Paragraph-regime Levels (4-5):** independent original sentences using the target Focus A/B items, no frame.
- **Essay-regime Levels (6-8):** combine 2-3 target items (Focus A/B and any taught Essay Focus cohesive device)
  into one connected short paragraph, never a full essay; a full essay belongs to Lesson 3 in class.
- **Foundation Support:** point-and-name real objects at home with a caregiver, match a printed Word Bank word to
  an object at home, or draw one target word; nothing the teacher or caregiver must prepare (Quality Standards §D8).
Two Levels sharing a regime each get their own section with their own content.

**Part 1: Grammar Focus in Production.** 2-3 items from Focus A taught so far (plus Focus B once the timing
checkpoint allows), a working subset. Require original sentences or a completed frame, not recognition of a
pre-written sentence.

**Part 2: Skill Practice.** Restate the Skill Spotlight in the exact plain language the lesson used. Apply it to
a new instance of the Scenario's underlying task, never the Scenario's own object already covered in class: a
student who described "my phone case" in class describes a different object at home with the same
comparison-plus-reason skill.
- **Frame-regime:** the lesson's frame once on a new object of the student's own at home, plus one other-shape
  item about that object (circle the Word Bank words that fit it, cross out the ones that do not); never "more
  rounds" (Quality Standards §D10).
- **Paragraph-regime:** 2-4 sentences on a new object, including the Level's own required feature (Lesson prompt
  0.2).
- **Essay-regime:** one paragraph applying Focus A/B and, where already taught by this checkpoint, one structural
  element (a hook, a topic sentence), on a new instance of the Scenario's situation.
- **After Lesson 3 or later checkpoints:** at every Level, extend the student's own draft or Closing Transfer Check
  skill to a second, different instance rather than a first attempt.

### 1.2 Grading is light-touch

Checked for genuine attempt and correct use, not scored against the assessment's rubric. A short completion
checklist per Level, 2-3 plain criteria ("used the target grammar item correctly," "about a new object, not the
one from class," "attempted independently").

### 1.3 Respectful Tiers

Quality Standards §B: the lowest Level's Part 2 is a genuine, simplified skill-application item, never grammar
practice alone.

## SECTION 2: FORMAT

One document per assignment: a header naming the source lesson (Module(s), Band, Scenario), the checkpoint
reached, and estimated completion time; Part 1 before Part 2; sections lowest Level first through highest, then
Foundation Support if applicable; the Skill Spotlight restated verbatim above Part 2; a completion checklist per
Level. No answer key; if the teacher needs an exemplar for an item, it sits on an `**Answer note:**` line under
that item (Quality Standards §E2), never in the item itself (§C9), and the student copy carries none. Style per
Quality Standards §E; each Level's vocabulary and grammar inside the same ceiling the lesson used.

## SECTION 3: SELF-CHECK BEFORE FINALIZING

Run `shared/Generation_Quality_Standards.md` §F first. Then:

1. Every Part 1 item traces to Focus A (and, where the checkpoint allows, Focus B) actually taught so far?
2. Part 2 uses the exact Skill Spotlight wording and a genuinely new object or situation?
3. Timing respected: no content the student has not reached (Focus B, prewriting, a draft, the Closing Transfer
   Check), and no "finished/published" framing at Pair position 4?
4. Each Level's design keyed to its regime, not its position; Foundation Support version generated where the
   lesson has the layer?
5. Grading a completion checklist, not the rubric (1.2)?
6. Whole assignment about 15-20 minutes, essay-regime Levels writing a paragraph, not an essay (1.0)?
7. No item states its own answer; any exemplar on an `Answer note:` line only (Quality Standards §C9)?
