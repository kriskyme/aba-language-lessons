# Listening/Speaking Assessment Generation Prompt (v2)

Companion to the Listening/Speaking Lesson Generation Prompt and Module Lesson-Plan Prompt. Generates the
assessment layer that sits on top of a taught Set: a way to check whether students can transfer what the Set
built, not a lesson and not new teaching.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`
alongside it. Quality Standards §A-§C (task Levels, Respectful Tiers, item quality: distinct, not trivially easy,
requires the centerpiece, plausible distractors and padded banks, time-balanced, counted, complete, traceable)
govern every item here and are not restated. This prompt states only what is specific to a Listening/Speaking
assessment.

**Current version: v2.** For the dated version history and reasoning, see `Changelog.md`. Numbers below (period
length, clip runtimes, item counts, presentation time budget) are reasoned starting points; expect revision as
more real assessments are given.

**Why two parts.** Listening comprehension can be checked individually and simultaneously, like a lesson's Day 1
Phase 4. Speaking cannot: a teacher can watch and score one student or group at a time. Part B therefore uses a
band-dependent mechanism built around Microsoft Teams for Education's Speaking Progress feature.

| | Part A: Listening Assessment | Part B: Speaking Assessment |
|---|---|---|
| Cadence | Every Set | Every Set, same Set as Part A |
| Mechanism | In-class, individual, one period, new unseen clips | Band-dependent (B.1) |
| Scope | The Set just completed | The Set just completed |
| Basis | 2-3 new real clips, never one of the Set's taught sources | A new invented prompt, not tied to any one source |

---

## PART A: LISTENING ASSESSMENT

### A.0 Scope and inputs

Run after a Set's lessons are complete. Inputs: Module, Band, Set number, and the completed lesson files (to
confirm which task Levels, listening strategies, and vocabulary were actually taught, in case a lesson deviated
from its plan).

**2-3 new real clips, sourced exactly like a lesson's own source** (Lesson prompt 0.3: never fabricated, found
and verified via search, cited in full, transcript confirmed before any item is built). Never reuse a taught
source or a clip used in an earlier Set's assessment for this Module/Band. Every clip matches the Module's verb
and the band's lower-Level runtime/pace/register ceiling (Lesson prompt 0.2), so performance reflects transfer,
not a harder or easier task. The new-source rule is about clips only; vocabulary deliberately goes the other
way (A.1). All clips are heard by the whole class in one shared playback sequence; a Level's items may draw on
any of them.

### A.1 What the assessment checks

1. **The Module's Listening can-do at each task Level,** quoted verbatim from the CSV: the same objective each
   lesson's Day 1 was built to satisfy, now on a source the student has never heard.
2. **The specific listening strategies taught across the Set's lessons:** at least one item per strategy, pulled
   from the lesson files or the Rotation Log, not re-guessed from the plan.
3. **Vocabulary already taught in the Set,** tested only inside graded items (a matching item, a fill-in-the-blank
   in a new sentence), using each word's real taught definition, 3-5 words pooled across all 4 lessons so a
   student who missed one lesson loses a fraction of the pool, not all of it. No separate pre-teach or review
   step anywhere in the document. Banks padded per Quality Standards §C4, extras drawn from the same taught pool.

**Item format:** every item at every Level is multiple choice, fill-in-the-blank, or matching; no open-ended
items, so the whole part stays objectively gradable. Where a Level's can-do calls for summarizing, cause-and-
effect, stated vs. implied opinion, or comparing framing across sources, engineer the objective item to require
that judgment (Quality Standards §C2): plausible-paraphrase options with one accurate to the source; matching a
quote to the stance or framing it signals; a blank completing a cause-and-effect or comparison statement in the
source's own language. Respectful Tiers (§B) applies to the lowest Level's item.

### A.2 Structure

```
LISTENING ASSESSMENT (approx. 35-45 MIN)  |--Setup (5)--|--Clip 1 + Items--|--Clip 2 (+3) + Items--|--Wrap (5)--|
```

- **Setup (5 min):** all clips' citation blocks up front. No vocabulary pre-teach. Background Notes only if a
  clip names something genuinely opaque.
- **Clips and items (25-35 min total, repeated per clip):** play one clip (once; twice only if the band's runtime
  makes two plays fit, stated in the document), then immediately administer the items that draw on it. No
  separate notes-taking step; notes are not gradable. Across all clips, one item set per task Level, each testing
  that Level's exact CSV can-do plus at least one item per taught strategy, time-balanced per Quality Standards
  §C5. Students work at their own assigned Level; no live discussion step.
- **Wrap (5 min):** collect. The period itself is the transfer check.

### A.3 Scoring

A point-value key per item plus one holistic note per task Level describing a passing performance in plain
language. No letter grades or percentages in the document; that conversion is a gradebook decision.

### A.4 Self-check

Run Quality Standards §F first. Then:

1. All 2-3 clips real, verified, cited in full, distinct from the Set's taught sources and every prior Set's
   assessment sources for this Module/Band?
2. Every clip matches the Module's verb and the band's lower-Level ceiling?
3. Every task Level's item set traces to that Level's verbatim CSV Listening can-do?
4. Every listening strategy taught in the Set covered at least once?
5. Vocabulary tested only inside graded items, pooled across all 4 lessons, none from the new clips, no
   pre-teach or review step anywhere?
6. Every item multiple choice, fill-in-the-blank, or matching; judgment Levels engineered to require the
   judgment?
7. Items answered right after their clip plays; no notes organizer?
8. Citation block first for every clip; timestamp ranges for any segment reference.

---

## PART B: SPEAKING ASSESSMENT

### B.0 Scope, cadence, and inputs

Run for the same Set Part A was generated for. Inputs: Module, Band, Set number, and the 4 lesson files (to
confirm the speaking skills actually taught). No source is searched: the prompt is original, grounded in the
Module's verb and topic range, so the check is whether the skill transfers away from every text already rehearsed.

### B.1 Mechanism by band

Live presentation and solo recording trade off differently by band: how much public performance a band's students
can handle, and whether the band's Speaking can-dos call for register adjustment to a live listener.

| Band | Default mechanism | Teams-recording version also generated? | Live-delivery option? |
|---|---|---|---|
| Beginner | Teams Speaking Progress solo recording; this IS the scored assessment | n/a, it is the recording | Yes, teacher-approved: the same task delivered live, same rubric, no separate version generated |
| Intermediate | Same as Beginner | n/a | Same as Beginner |
| Advanced | Live presentation (solo or small group) | Yes, every Set, same task, same rubric, as a standing scored alternate (absence, illness, any teacher-approved reason) | n/a, live is the default |
| Proficient | Same as Advanced | Yes | n/a |

At Beginner/Intermediate, students may re-record before submitting; scoring reflects a best take, by design. The
document carries a one-line note that the task may be delivered live instead, teacher-approved, same scoring. At
Advanced/Proficient, how many swaps a student gets and who approves them is a program policy outside this prompt;
the prompt's only obligation is that the alternate version exists.

### B.2 Format specifics

**Teams solo recording:** each student records one response to a written or teacher-delivered prompt at their
assigned Level. A monologue at every Level; no partner step, since recordings happen outside class.

**Live presentation (Advanced/Proficient):** solo or small group, teacher's choice per Set by what the Module
naturally supports (default solo unless the Module clearly calls for a group). Budget roughly 2-3 minutes per
student or group times roster size, a dedicated period or a spread across days, stated explicitly in the
document.

### B.3 Structure (per task Level)

One self-contained prompt per Level with:
- **A speaking task grounded in the Module's verb,** scoped to that Level's verbatim CSV Speaking can-do, drawing
  on 1-2 speaking skills taught in this Set (named in the prompt so scoring can target them).
- **A clear invented topic** matched to the Module's topic range, concrete enough that a student knows what to
  talk about.
- **A target length** scaled by Level: roughly 30-45 seconds at the lowest Level up to 90-120 seconds at the
  highest for a recording; a live presentation may run longer per the teacher's budget but scales the same way.
- **Concrete, countable content requirements,** not just a length ("describe at least 2 features of each place,"
  "use at least 2 different sequence connectors," "include one comparison with a stated reason"), fewer and
  simpler at the lowest Level, more and deeper at the highest.
- **A plain delivery instruction** (how and by when to submit a recording; which day a presentation runs).
- At Advanced/Proficient, the recording version matches the live version's topic, skills, and requirements as
  closely as the format allows, so a swap changes only how the performance is captured.

### B.4 Scoring rubric

One rubric per task Level, 3-4 criteria tied to that Level's CSV can-do and the emphasized skills, on a 3-point
scale (Not yet / Developing / Meets), usable directly against Teams' review interface or a clipboard. One rubric
per Level covers both live and recorded versions. The rubric is teacher-only; the student packet derives a short
self-check checklist from its Meets column (one item per criterion, phrased to the student).

### B.5 Self-check

Run Quality Standards §F first. Then:

1. Same Set as Part A?
2. Correct mechanism for the band; at Advanced/Proficient a same-task, same-rubric recording alternate; at
   Beginner/Intermediate the one-line live-delivery note, no second version?
3. Every Level's prompt traces to its verbatim CSV Speaking can-do, emphasizing 1-2 skills actually taught?
4. Target length scaled by Level, and countable content requirements at every Level?
5. Lowest Level a genuine production task, not recitation (§B)?
6. Live presentation's class-time budget stated explicitly?

---

## Style & Formatting Constraints (both parts)

Quality Standards §E. Citation block first for every real clip (Part A); timestamp ranges for segment references;
task Levels shown with the packet's star system. This prompt produces the teacher-facing document (answer key,
rubric); the student-facing version is a separate step, `Generate_Assessment_Student_Packet_Prompt_*.md`. The
scoring-to-gradebook conversion is a program-level policy decision outside this prompt.
