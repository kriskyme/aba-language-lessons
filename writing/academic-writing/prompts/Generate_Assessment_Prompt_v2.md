# Academic Writing Assessment Generation Prompt (v2)

Companion to `Generate_Lesson_Prompt_v4.md` and `Generate_Module_Lesson_Plan_Prompt_v2.md`. Generates the
assessment layer that sits on top of one completed **Set** (all 4 lessons, the Scenario carried from grammar
input through a finished, published piece), the same once-per-Set cadence Reading and Listening/Speaking use for
their own Set-scoped assessments: not a lesson, and not new teaching, but a way to check whether the Set's
grammar content and writing skill actually transferred.

**Why two parts, not one.** A completed Set leaves behind two genuinely different things to check: whether
specific grammar forms (Focus A/B) were learned, and whether the student can actually produce the kind of
writing the Set's task Level calls for. The first is objectively gradable in a few minutes; the second is not
gradable by a key at all - it needs a human reader applying a rubric, the same underlying problem
Listening/Speaking's Assessment prompt solves by splitting Listening (objectively gradable) from Speaking
(rubric-scored). Writing's split follows the same logic:

|           | Part A: Grammar & Mechanics Check                          | Part B: Writing Task                                                                                          |
| --------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Cadence   | Every Set                                                     | Every Set                                                                                                         |
| Mechanism | In-class, individual, objectively gradable items             | In-class or take-home written piece, rubric-scored (Not yet / Developing / Meets)                                 |
| Scope     | The Set just completed only (Focus A/B and Essay Focus A/B from across its 4 lessons) | The Set just completed only                                                                                       |
| Basis     | New example sentences using Focus A/B, never any lesson's own printed items | A new Scenario (same Module verb, same Band calibration), never the Set's own Scenario the student already drafted, revised, and published about |

**No separate study guide document.** Reading's Assessment prompt produces a required per-task-Level study guide
because its assessment can span up to 4 lessons cumulatively (a whole Set) with 4 independent anchor texts - there
is real material to consolidate before a test that wide. A Writing Set's 4 lessons share one Scenario, not 4
independent topics (`shared/Program_Conventions.md` §C), so there is less to separately consolidate; this prompt
follows Listening/Speaking's simpler precedent instead: Part B's rubric-derived self-check checklist (B.4, carried
into the student packet by `Generate_Assessment_Student_Packet_Prompt_v2.md`) is the only review aid, not a
standalone document.

**Current version: v2.** For version history, see `Changelog.md`. (v2 rescopes this prompt from "one completed
lesson" to "one completed Set" (all 4 lessons), correcting a mismatch left over from when a Writing Set was
modeled as 1 lesson - see `shared/Program_Conventions.md` §C and `Changelog.md`'s 2026-09-08 entry. Neither this
prompt nor its student-packet companion has been run against a real Set yet, so this is a low-risk scope
correction, not a content redesign.)

---

## PART A: GRAMMAR & MECHANICS CHECK (every Set)

### A.0 Scope and inputs

Run this after a Set (all 4 lessons) is complete. Required inputs: the Module, the Band, and the completed Set's content (to
confirm which Focus A/B content, which confusable pair, and which task Levels were actually taught - this
assessment must trace to what was actually taught, not just what the Module Lesson-Plan originally planned, in
case any of the Set's 4 generated lessons deviated from its plan per that prompt's own self-check).

**New example sentences are required for every item - never reuse a sentence from any of the Set's own controlled-
practice activities or editing paragraphs verbatim.** This is the Writing equivalent of Reading/L-S's "new
source" rule: an item built from a sentence the student has already seen and corrected in class tests memory of
that specific item, not whether the grammar transferred to unfamiliar material. Build on the same Scenario is
fine here (unlike Part B - see B.0), since Part A is testing grammar forms, not writing transfer; what must be
new is the specific sentence content of each item.

### A.1 What Part A checks

Three things, kept separate in the item design:

1. **Focus A's target grammar form(s)**, and **Focus B's**, both as actually taught across this Set's 4 lessons (not the full
   Grammar Focus Bank - only the rows this specific Set used).
2. **The confusable pair(s) taught in this Set** (e.g. it's/its, your/you're), tested directly through graded
   items.
3. **Where the Band reaches Essay Composition (Advanced, Proficient): Essay Focus A/B's structural vocabulary**
   (direct vs. indirect thesis, hook types, topic sentence vs. supporting sentence), tested through
   identification items (e.g. "is this thesis direct or indirect?"), not through writing an essay - essay
   production itself is Part B's job, not Part A's.

**Item format:** every task Level's items are fill-in-the-blank, choose-the-form, identify-sentence-type, or
combine-the-sentences only - no open-ended writing at any Level in Part A, so the whole part stays objectively
gradable. (This mirrors the item-format restriction in `Generate_Assessment_Prompt_v1.md`'s Listening/Speaking
counterpart, Part A.1.)

**Respectful Tiers still applies.** The lowest task Level's item(s) must still require a genuine, if
scaffolded, choice - a frame-regime Level's item can be "which word fits the frame and the picture," never a
single foregone answer copied off a model.

### A.2 Structure

```
GRAMMAR & MECHANICS CHECK (approx. 20-30 MIN)  |--Setup (2)--|--Items, by task Level--|--Wrap (3)--|
```

Single sitting, shorter than a full class period since there is no pre-teach step. Item counts scale by task
Level the same balanced-duration principle `Generate_Lesson_Prompt_v4.md` Section 0.4b uses for controlled
practice: 6-8 items for the lowest task Level(s) in the Band, fewer but more demanding items (a combine-the-
sentences or identify-and-fix task) for the highest.

### A.3 Scoring

Provide a simple point-value key per item, plus one holistic note per task Level describing what a passing
performance looks like in plain language (e.g., "Level 4: correctly forms the comparative and identifies the
because-clause in at least 6 of 8 items"). Do not assign letter grades or numeric percentages in the generated
document itself - that conversion is a teacher/gradebook decision outside this prompt's scope.

### A.4 Self-check (apply before finalizing)

1. Does every item use a new example sentence, not one lifted verbatim from any of the Set's own controlled-practice
   or editing content?
2. Does every item trace to Focus A, Focus B, the taught confusable pair, or (where applicable) Essay Focus A/B
   structural vocabulary actually taught in this specific Set, not the full Grammar Focus Bank?
3. Is every item fill-in-the-blank, choose-the-form, identify-sentence-type, or combine-the-sentences - none
   open-ended?
4. Does item count scale by task Level (more/shorter at the lowest, fewer/deeper at the highest), per Section
   0.4b's balanced-duration principle?
5. Does the lowest task Level get a genuine (if scaffolded) choice, not a foregone answer - Respectful Tiers
   applied to an assessment context?
6. Where the Band reaches Essay Composition, are Essay Focus A/B items identification-only (direct/indirect
   thesis, topic sentence vs. supporting sentence), not essay production?
7. No em-dashes anywhere.

---

## PART B: WRITING TASK (every Set)

### B.0 Scope, cadence, and inputs

Run this after the same Set Part A was just generated for - both parts run on the same per-Set cadence.
Required inputs: the Module, the Band, and the completed Set's content (to confirm the task Levels, required
features, and real-world writing form actually taught).

**A new Scenario is required - never the Set's own Scenario the student already drafted, revised, and
published against.** This mirrors Listening/Speaking's Part B: the assessed prompt is invented fresh, grounded
in the same Module verb and the same Band-lower-Level calibration the Set's own Scenario used, so the task
checks whether the taught skill transfers to a new situation rather than whether the student can reproduce (or
lightly edit) a piece they already have on paper. Match the new Scenario's shape to the Set's own: if the
Set's Scenario named a specific reader and concern (required for a Band reaching Level 6+, per Lesson prompt
Section 0.2), the assessment's new Scenario must too.

### B.1 Structure by task Level

For each task Level in the Band, write one self-contained task with:

- **A writing task grounded in the Module's own verb**, scoped to that task Level's verbatim CSV Description,
  drawing on the Focus A/B grammar and, where applicable, Essay Focus A/B structural content actually taught in
  this Set (state in the task itself which grammar/structural elements this Level's task is emphasizing, so
  scoring can target them specifically).
- **A new Scenario** (per B.0), concrete enough that a student is not left guessing what to write about - the
  same standard the Lesson prompt's own Scenario always meets.
- **A target length**, matching that task Level's own output-ceiling range from `Generate_Lesson_Prompt_v4.md`
  Section 0.2 (the same range the Set's Mentor Text/Mentor Essay and drafting task used), so the assessment
  stays comparable to what was actually taught and practiced - not a shortened or padded version of that range.
- **Concrete, countable content requirements, not just a target length** (e.g. "include one comparison and one
  stated reason," "your thesis must be indirect," "shift register at least once to address [the named reader]'s
  stated concern"), drawn directly from that Level's own required feature per Lesson prompt Section 0.2.

**Structure varies by regime, the way Listening/Speaking's Part B varies by Band (its own mechanism table):**

- **Frame-regime task Levels (1-3):** a fresh picture/object prompt, same frame structure as taught, completed
  in the same single sitting as Part A.
- **Paragraph-regime task Levels (4-5):** a single paragraph, same single sitting as Part A, or immediately
  after it.
- **Essay-regime task Levels (6-8):** a full essay at the Level's own Section 0.2 length target. Producing this
  well may need its own dedicated sitting separate from Part A and from the paragraph-regime Levels' shorter
  task, the same way the Set itself needs a full dedicated lesson (Lesson 3) to draft an essay, not one day. State this
  explicitly in the generated assessment rather than assuming it fits inside Part A's 20-30 minute window.

### B.2 Scoring rubric

One rubric per task Level, 3-4 criteria, each tied directly to that Level's CSV Description and Lesson prompt
Section 0.2's required feature (a comparison, an implied attitude, a register shift for a named reader, an
inferable implication plus self-revision, two-audience calibration), plus, where applicable, one criterion for
Essay Focus A/B structure (hook, thesis, topic-sentence-led body paragraphs, conclusion). Use a simple 3-point
scale per criterion (Not yet / Developing / Meets), matching Listening/Speaking's Speaking rubric, rather than a
numeric score out of 100. Do not invent a program-wide letter-grade conversion here - a teacher/admin decision
outside this prompt's scope. **Per program convention, the student-facing packet derives a short self-check
checklist from this rubric's Meets column** - see `Generate_Assessment_Student_Packet_Prompt_v2.md` Section 2.7.
The rubric itself, with its Not yet/Developing/Meets columns, stays teacher-only.

### B.3 Self-check (apply before finalizing)

1. Is the Scenario genuinely new - not the Set's own Scenario the student already drafted, revised, and
   published against?
2. Does the new Scenario match the Module verb and, where the Band requires it (Level 6+), name a specific
   reader and stated concern?
3. Does every task Level's task trace to that Level's verbatim CSV Description?
4. Does the target length match that Level's own Section 0.2 range from the source Set, not a shortened or
   padded substitute?
5. Does every task Level's task specify concrete, countable content requirements, not just a target length?
6. Does the rubric use the same 3-point (Not yet/Developing/Meets) scale at every task Level, with criteria tied
   directly to that Level's own required feature and, where applicable, Essay Focus A/B structure?
7. For essay-regime task Levels, is a realistic time budget (a dedicated sitting, not folded into Part A's
   window) noted explicitly?
8. Does the lowest task Level get a genuine production task (not a fill-in-the-blank substitute) - Respectful
   Tiers applied to Part B?
9. No em-dashes anywhere.

---

## Style & Formatting Constraints (both parts)

Same constraints as the Lesson Generation Prompt: no em-dashes anywhere; task Levels shown as the star system
`Generate_Student_Packet_Prompt_v2.2.md` already uses. This prompt generates the teacher-facing assessment
(including Part A's full answer key and Part B's rubric); the student-facing print version is a separate step,
run by `Generate_Assessment_Student_Packet_Prompt_v2.md`, which strips Part A's answer keys/point values/pass
notes as teacher-only, but carries Part B's rubric over to the student only as a self-check checklist (B.2).

## Open items for this v1

- Not yet run against a real completed Set. Treat every number above (item counts, sitting length, essay-
  regime time budget) as a reasoned starting point, the same way the Lesson prompt's v1 was, and expect addenda
  once a real assessment has actually been generated and given.
- Scoring-to-gradebook conversion (how Part A's point key or Part B's Not yet/Developing/Meets becomes a
  report-card mark) is intentionally out of scope - a program-level policy decision, not a generation-time one.
