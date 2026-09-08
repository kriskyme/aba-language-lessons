# Academic Writing Assessment Generation Prompt (v4)

Companion to the Academic Writing Lesson Generation Prompt and Module Lesson-Plan Prompt. Generates the assessment
layer on top of one completed **Beginner Set** (4 lessons) or one completed **Intermediate/Advanced/Proficient
Module Pair** (8 lessons across two Modules; the piece only reaches a finished, gradable state at Pair position
8): a check of whether the arc's grammar content and writing skill transferred, not a lesson and not new teaching.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`
alongside it. Quality Standards §A-§C (task Levels, Respectful Tiers, item quality: distinct, not trivially easy,
requires the centerpiece, plausible distractors and padded banks, time-balanced, counted, complete, traceable)
govern every item here and are not restated. This prompt states only what is specific to a Writing assessment.

**Current version: v4.** For the dated version history and reasoning, see `Changelog.md`. Numbers below (item
counts, sitting length, essay time budget) are reasoned starting points; neither this prompt nor its packet
companion has yet been run against a real Set or Pair.

**Why two parts.** A completed arc leaves two different things to check: whether specific grammar forms (Focus A/B,
both Modules' for a Pair) were learned, objectively gradable in minutes; and whether the student can produce the
writing the Level calls for, gradable only by a reader with a rubric.

| | Part A: Grammar & Mechanics Check | Part B: Writing Task |
|---|---|---|
| Cadence | Every Set (Beginner) / every Module Pair (others) | Same as Part A |
| Mechanism | In-class, individual, objectively gradable items | In-class or take-home written piece, rubric-scored |
| Scope | The Set/Pair just completed: its Focus A/B and Essay Focus A/B | The Set/Pair just completed |
| Basis | New example sentences using Focus A/B, never a lesson's own printed items | A new Scenario, never the arc's own |

**No separate study guide.** A Writing Set's lessons share one Scenario, so there is less to consolidate than
Reading's four independent anchor texts; Part B's rubric-derived checklist in the student packet is the only
review aid.

---

## PART A: GRAMMAR & MECHANICS CHECK

### A.0 Scope and inputs

Run after a Beginner Set (all 4 lessons) or a Module Pair (all 8 lessons) is complete, never at Pair position 4.
Inputs: Module(s), Band, and the completed Set's or Pair's content (to confirm which Focus A/B, which confusable
pair(s), and which task Levels were actually taught).

**New example sentences for every item; never a sentence from the Set's own practice activities or editing
paragraphs.** An item built on a sentence the student already corrected in class tests memory of that item, not
transfer (Quality Standards §C3). The Set's own Scenario is fine as subject matter here (unlike Part B); what must
be new is each item's sentence content.

### A.1 What Part A checks

1. **Focus A's and Focus B's target forms** as actually taught: Module N's alone for a Beginner Set, both Modules'
   for a Pair; only the rows this Set/Pair used, not the whole bank.
2. **The confusable pair(s) taught** (it's/its, your/you're), tested directly.
3. **Where the band reaches Essay Composition:** Essay Focus A/B's structural vocabulary (direct vs. indirect
   thesis, hook types, topic sentence vs. supporting sentence) through identification items only; essay
   production is Part B's job.

**Item format:** fill-in-the-blank, choose-the-form, identify-sentence-type, or combine-the-sentences only; no
open-ended writing in Part A. Banks and choice sets padded per Quality Standards §C4. Respectful Tiers (§B): a
frame-regime Level's item is "which word fits the frame and the picture," a genuine choice, never a foregone
answer copied off a model.

### A.2 Structure

```
GRAMMAR & MECHANICS CHECK (approx. 20-30 MIN)  |--Setup (2)--|--Items, by task Level--|--Wrap (3)--|
```

One sitting, shorter than a period. Item counts scale by Level per Quality Standards §C5: 6-8 items at the lowest
Level(s), fewer but more demanding (combine-the-sentences, identify-and-fix) at the highest.

### A.3 Scoring

A point-value key per item plus one holistic note per Level describing a passing performance in plain language
("Level 4: forms the comparative and identifies the because-clause in at least 6 of 8"). No letter grades or
percentages in the document.

### A.4 Self-check

Run Quality Standards §F first. Then:

1. Every item on a new example sentence, none lifted from the Set's own practice or editing content?
2. Every item traces to Focus A, Focus B, the taught confusable pair, or (where applicable) Essay Focus A/B
   structural vocabulary actually taught in this Set/Pair, both Modules' for a Pair?
3. Every item in one of the four objective formats, none open-ended?
4. Essay Focus items identification-only where the band reaches Essay Composition?

---

## PART B: WRITING TASK

### B.0 Scope, cadence, and inputs

Run for the same Set/Pair as Part A. Inputs: Module(s), Band, and the completed content (to confirm the task
Levels, required features, and real-world writing form taught).

**A new Scenario is required; never the arc's own Scenario the student already drafted, revised, and published
against.** Ground it in the piece's own Module verb (Module N's for a Pair; the genre never switched) and the
same band-lower-Level calibration the original used, so the task checks transfer to a new situation. Match the
original Scenario's shape: if the band reaches Level 6+, the new Scenario names a specific reader and concern; if
it reaches Level 8, two distinct readers or stakes (Lesson prompt 0.2).

### B.1 Structure by task Level

One self-contained task per Level with:
- **A writing task grounded in the piece's Module verb,** scoped to that Level's verbatim CSV Description, drawing
  on the Focus A/B grammar (both Modules' for a Pair) and any Essay Focus A/B content taught, naming in the task
  which elements it emphasizes.
- **The new Scenario,** concrete enough that a student knows what to write about.
- **A target length** matching that Level's own 0.2 range from the Lesson prompt, the same range the Mentor model
  and drafting task used, neither shortened nor padded.
- **Concrete, countable content requirements** drawn from that Level's required feature ("include one comparison
  and one stated reason," "your thesis must be indirect," "shift register at least once to address [the named
  reader]'s concern").

By regime: frame-regime Levels (1-3) get a fresh picture or object prompt in the same frame structure, in the
same sitting as Part A; paragraph-regime Levels (4-5) write a single paragraph in the same sitting or immediately
after; essay-regime Levels (6-8) write a full essay at the Level's 0.2 length, which may need its own dedicated
sitting, stated explicitly in the document.

### B.2 Scoring rubric

One rubric per task Level, 3-4 criteria tied to that Level's CSV Description and required feature (a comparison,
an implied attitude, a register shift for a named reader, an inferable implication plus self-revision,
two-audience calibration), plus one criterion for Essay Focus structure where applicable, on a 3-point scale (Not
yet / Developing / Meets). The rubric is teacher-only; the student packet derives a short self-check checklist
from its Meets column.

### B.3 Self-check

Run Quality Standards §F first. Then:

1. Scenario genuinely new, matching the Module verb and naming a reader and concern (Level 6+) or two readers
   (Level 8) where the band requires it?
2. Every Level's task traces to its verbatim CSV Description, with countable requirements from its required
   feature?
3. Target length matches the Level's own 0.2 range, neither shortened nor padded?
4. Rubric on the 3-point scale at every Level, criteria tied to the required feature and, where applicable, essay
   structure?
5. Essay-regime Levels' dedicated sitting stated explicitly?
6. Lowest Level a genuine production task, not a fill-in-the-blank substitute (§B)?

---

## Style & Formatting Constraints (both parts)

Quality Standards §E. Task Levels shown with the packet's star system. This prompt produces the teacher-facing
document (Part A's answer key, Part B's rubric); the student-facing version is a separate step,
`Generate_Assessment_Student_Packet_Prompt_*.md`. The scoring-to-gradebook conversion is a program-level policy
decision outside this prompt.
