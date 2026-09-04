# Listening/Speaking Module Lesson-Plan Generation Prompt (v1)

Companion to the Listening/Speaking Lesson Generation Prompt (v1). Mirrors the Passage Reading Module
Lesson-Plan Generation Prompt's structure and reasoning, adapted for a modality where the source is found (real
audio/video), not written, and where every Level's CSV objective already pairs a Listening can-do with a
Speaking can-do.

Produces a **plan for one Set only** - topic/content-format direction, listening-strategy and speaking-skill
rotation, and task-Level-to-objective mapping for that Set's lessons - not an actual source, tasks, or answer
key. Run this first, review/approve the plan, then generate the Set's lessons against it, checking each one
before moving to the next. As with Passage Reading, do not generate a full Set's lessons in a single pass.

**Correction, added 2026-09-03, after user review.** This prompt originally defaulted to 8 lessons per module,
matching an earlier (incorrect) assumption that a Listening/Speaking lesson spans an 8-day cycle. The Lesson
Generation Prompt's Unit Architecture was corrected to a real 2-day cycle (Day 1 = Unit A/Listening, Day 2 =
Unit B/Speaking, 75 minutes each) - see that prompt's fifth addendum. A 2-day lesson matches Passage Reading's
own cycle length, and Passage Reading's module size was independently corrected the same way (a Reading module
is 4 lessons, 8 days, not 8 lessons, 16 days). With cycle-length parity restored, this family's module size is
corrected to match: **4 lessons (8 real class days) per rotation, not 8 lessons (16 days).**

**Sets, added 2026-09-03.** A Module/Band can hold more than one rotation of lessons over time - a fresh batch
of topics for a semester where the module is retaught, without discarding or overwriting what was taught before.
Each such rotation is a **Set**: 4 lessons (matching the corrected module size above) sharing one Module, one
Band, and one plan, distinct in topic/format/strategy/skill from every other Set already planned for that same
Module/Band. Module 1 (Intermediate), originally planned with a single 8-row table before this correction, is
now Set 1 (Lessons 1-4, generated) and Set 2 (Lessons 5-8, planned only, not yet generated) - see that plan's
own Set breakdown. A Set is not tied to a semester in the plan itself; note an actual teaching term against a
Set only once it's been assigned to one, as a light annotation, not a planning input.

**Lesson numbering is global within a Module/Band, continuing across Sets, never resetting.** Set 1 is Lessons
1-4, Set 2 is Lessons 5-8, Set 3 is Lessons 9-12, and so on - so "Lesson 7" unambiguously means Set 2's third
lesson without needing to also state which Set. When planning a new Set, start numbering at the next integer
after the highest lesson number already planned for that Module/Band, across every Set.

Why this exists: several of the lesson prompt's constraints are Set-wide (content-format rotation across the
whole bank, listening-strategy/speaking-skill/protocol variety, no vocabulary-theme overlap within a Set,
task-Level content that must trace to the actual Listening/Speaking objective in `learningobjectives.csv`). Those
are easier to satisfy by planning the whole Set up front than by improvising lesson-by-lesson.

Scope: plan **one Set at a time**. The program has 8 modules (Describing, Narrating, Explaining, Instructing,
Evaluating, Arguing, Transacting, Socializing) shared with Passage Reading's own module set - a class or student
moving through both tracks in parallel will meet the same skill-verb sequence in both.

---

## 0. Program Rotation Log (read before planning, update after approval)

**What it is:** a running record, separate from any one Set's plan, of what every already-planned
Listening/Speaking Set actually used - content format, listening strategy, speaking skill, Phase 1 hook,
Phase 3 protocol, vocabulary theme, and topic direction, one row per lesson, grouped by Set within each
Module/Band section.

**Where it lives:** `claude/Listening Speaking Program Rotation Log.md`, one project doc, appended to (never
overwritten) each time a Set's plan is approved. If it does not exist yet, this is the first Set of the first
Module ever planned for this track; create it fresh and skip the cross-Module and cross-Set checks below.

**Cross-Set rules (same Module/Band, a new Set added to one already planned):** identify the highest lesson
number already used for this Module/Band across every existing Set, and start this Set's numbering at the next
integer. The new Set's Lesson 1 must not repeat the most recent existing Set's final lesson's content format,
listening strategy, speaking skill, Phase 1 hook, or Phase 3 protocol - same adjacency check as the cross-Module
rule below, just one level narrower (same Module/Band, different Set, instead of a different Module). Vocabulary
theme and topic direction: flag (don't block) an obvious repeat from the most recent existing Set in this same
Module/Band.

**Cross-Module rules (adjacency-only, same lighter touch as Passage Reading's log, for the same reason - full
history would eventually make later modules unplannable against a finite bank):**

- A new Module/Band's first Set, Lesson 1: content format, listening strategy, speaking skill, Phase 1 hook, and
  Phase 3 protocol must not repeat the previous Module's most recently planned Set's final lesson choices.
- Vocabulary theme and topic direction: flag (don't block) an obvious repeat from the immediately preceding
  Module; older repeats are lower-risk and don't need flagging.
  **After the Set's plan is reviewed and approved:** append one new subsection to the log, under that Module/Band's
  existing section if one exists, or as a new section if this is that Module/Band's first Set:

```
### Set S (planned <date>)
| Lesson # | Content Format | Listening Strategy | Speaking Skill | Phase 1 Hook | Phase 3 Protocol | Vocabulary Theme | Topic Direction |
|---|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... | ... | ... |
```

(Lesson # continues the global numbering for this Module/Band - see the Sets note above; do not restart at 1
for Set 2 onward.) Do not append a draft still being revised.

---

## INPUTS (fill in before running)

- **Module:** [e.g. "Module 2: Narrating"]
- **Band:** [Beginner / Intermediate / Advanced / Proficient]. Task Levels are looked up automatically from the
  Lesson prompt's Section 0.1 table (Beginner: 1-2-3; Intermediate: 2-3-4-5; Advanced: 4-5-6-7; Proficient:
  5-6-7-8).
- **Set number:** [which Set this is for this Module/Band - default: the next Set not yet planned. Set 1 if
  this Module/Band has no existing Sets. See the Sets note above.]
- **Number of lessons in this Set:** [default 4, matching a 2-day-per-lesson cycle and an 8-real-class-day
  rotation - see the correction note above]
- **Source of truth for objectives:** `learningobjectives.csv`, filtered to this Module, this band's task Levels,
  and the **Listening/Speaking modality only**. Reading and Writing objectives are out of scope for this plan the
  same way Listening/Speaking is out of scope for the Reading plan.
- **Program Rotation Log:** `claude/Listening Speaking Program Rotation Log.md`, read in full before planning; if
  it doesn't exist yet, treat this as the first Set of the first Module.

## TASK

1. Read the Program Rotation Log per Section 0. If this Module/Band already has one or more Sets planned,
   identify the highest lesson number used so far (this Set's numbering starts at the next integer) and the most
   recently planned Set's final lesson row (for the cross-Set adjacency check). Otherwise, identify the previous
   Module's most recently planned Set's final lesson row (for the cross-Module check) and the set of vocabulary
   themes/topic directions used so far.
2. Determine this band's task Levels from the Lesson prompt's Section 0.1 table. Pull the actual rows from
   `learningobjectives.csv` for this Module and each task Level, **Listening/Speaking modality only**. Quote the
   full Description verbatim for every task Level - it contains both halves (Listening and Speaking) - and note
   which half each lesson's day (Day 1 vs Day 2) will build toward. Do not also pull that Level's Reading or
   Writing objective. This is the same for every Set of a given Module/Band - the CSV grounding doesn't change
   Set to Set, only the topics and real sources do.
3. Produce a plan table, one row per lesson (4 rows unless told otherwise), with these columns:
   - Lesson # (global for this Module/Band - see the Sets note above; not restarted at 1 for Set 2 onward)
   - Topic direction (one line naming a real-world subject area to search within, e.g. "a home cook's
     neighborhood food tradition" or "a city's public-transit redesign" - distinct from every other lesson in this
     Set, and from every topic used in an earlier Set of this same Module/Band; flag if it closely echoes the
     previous Module's). This is a search direction, not a specific source: the actual video/audio is found at
     generation time against Section 0.1-0.2 of the Lesson prompt, so do not name a specific real title/speaker
     here unless one is already confirmed.
   - Content format (from the Lesson prompt's Module-to-format guidance in Section 0.1, e.g. a personal-story
     talk for Narrating, a tutorial for Instructing; across this Set's lessons the format should be genuinely
     varied, no two consecutive lessons using the identical format; this Set's Lesson 1 must not repeat the most
     recent existing Set's final lesson's format if this Module/Band already has a Set planned, otherwise must
     not repeat the previous Module's final lesson's format)
   - Listening strategy (from the Lesson prompt's Section 0.4 bank; no two consecutive lessons repeat one; at
     least 3 distinct strategies across this Set's 4 lessons; same cross-Set/cross-Module adjacency rule as
     content format above)
   - Speaking skill (from the same bank; same adjacency and variety rules)
   - Phase 1 activation hook and Phase 3 oral output protocol (same four-option banks as Passage Reading;
     rotate, same cross-Set/cross-Module adjacency rule applies)
   - Target vocabulary theme (one line describing the semantic field; must not overlap another lesson's theme in
     this Set, or an earlier Set's theme in this same Module/Band; flag if it echoes the previous Module's)
   - Task-Level basis: for every task Level in this band's row, quote the exact Listening/Speaking CSV objective
     (Level N) that lesson's Day 1 (Listening half) and Day 2 (Speaking half) are built to satisfy. Name both
     halves explicitly per task Level rather than treating the objective as one undifferentiated statement.
4. After the table, run a self-check and report it in a few sentences:
   - Is every content format, listening strategy, and speaking skill used at least once across this Set's
     lessons (twice if a bank is smaller than the lesson count)?
   - Does any topic direction or vocabulary theme repeat across this Set, or against an earlier Set in this same
     Module/Band?
   - Does every task Level's basis trace to an actual quoted Listening/Speaking CSV line for that specific Level
     (both halves), not a generic simplification and not a Reading or Writing objective?
   - Does the Module's own skill verb stay consistent across all of this Set's planned lessons?
   - Does this Set's Lesson 1 avoid repeating the most recent existing Set's final lesson's format, strategy,
     skill, hook, and protocol (if this Module/Band already has a Set planned), or the previous Module's final
     lesson's choices (if this is this Module/Band's first Set)? Is any vocabulary-theme or topic-direction echo
     noted?
   - Does the Lesson # column continue the global numbering for this Module/Band, rather than restarting at 1?
5. Do not search for or name an actual source, write any task, or produce an answer key in this step. If asked to
   also generate lesson content in the same turn, stop and confirm the plan is approved first.

## OUTPUT

The plan table, then the self-check paragraph. Once reviewed and approved, also produce the Program Rotation
Log entry (Section 0's format, under this Module/Band's existing section if one exists) ready to append to
`claude/Listening Speaking Program Rotation Log.md`. Nothing else.
