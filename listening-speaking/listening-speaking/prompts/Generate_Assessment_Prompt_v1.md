# Listening/Speaking Assessment Generation Prompt (v1)

Companion to the Listening/Speaking Lesson Generation Prompt (v1) and Module Lesson-Plan Generation Prompt (v1).
Generates the assessment layer that sits on top of a taught Set: not a lesson, and not a new source's worth of
teaching, but a way to check whether students can transfer what a Set actually built.

**Why two assessment types, not one.** Listening and Speaking scale differently in a real classroom. Listening
comprehension can be checked individually and simultaneously - every student listens on their own (headphones,
a shared device, a link) and answers differentiated items at their own task Level, the same underlying model as
a lesson's Day 1 Phase 4. Speaking cannot be checked the same way: a teacher can watch and score only one
student (or one small group) at a time, and a live in-class round for a full roster eats an entire period doing
almost nothing else. This program uses Microsoft Teams for Education's Speaking Progress feature to solve part
of that (see Part B for how it's actually used at each band):

|           | Listening Assessment                                      | Speaking Assessment                                                                                                                                                                                                                                                                                                                 |
| --------- | --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cadence   | Every Set (every 4 lessons / 8 real class days)           | Every Set (every 4 lessons / 8 real class days)                                                                                                                                                                                                                                                                                     |
| Mechanism | In-class, individual, same-period, new unseen source      | Band-dependent - see Part B: Beginner/Intermediate default to a scored Teams recording (with the same task available as a teacher-approved live delivery for a willing student); Advanced/Proficient default to a live presentation, with a Teams-recording version of the same task always also produced as a standing swap option |
| Scope     | The Set just completed only                               | The Set just completed only                                                                                                                                                                                                                                                                                                         |
| Basis     | A new source, never one of the Set's own 4 taught sources | A new prompt, not tied to any one source                                                                                                                                                                                                                                                                                            |

---

## PART A: LISTENING ASSESSMENT (every Set)

### A.0 Scope and inputs

Run this after a Set's lessons are complete. Required
inputs: the Module, the Band, and the Set number (or the completed lesson files themselves, to confirm which task
Levels, listening strategies, and vocabulary themes were actually taught - this assessment must trace to what
was actually taught, not just what the Module Lesson-Plan originally planned, in case a generated lesson
deviated from its plan row per that prompt's own self-check).

**A new source is required, exactly like a lesson's own source (Section 0.3 sourcing rules, reused wholesale):
never fabricated, always found and verified via search, cited in full, with a real transcript/captions
confirmed before any item is built on it.** Do not reuse any of the Set's taught sources, and do not reuse a
source already used in an earlier Set's assessment for this Module/Band. The new source must match the same
Module verb (Describing, Narrating, etc.) and the same band-lower-Level calibration (Section 0.2's runtime/
pace/register table) that governed the Set's own sources, so that performance on the assessment reflects
transfer of the taught skills, not a harder or easier task than the Set actually prepared students for.

### A.1 What the assessment checks

Two things, kept separate in the item design:

1. **The Module's Listening can-do at each task Level**, quoted verbatim from `learningobjectives.csv` the same
   way the Lesson prompt's Section 0.1 pulls it - the same objective each lesson's Day 1 was already built to
   satisfy. The assessment is not testing new content; it is testing whether the can-do transfers to a source
   the student has never heard.
2. **The specific listening strategies actually taught across the Set's lessons** (e.g., if a Set's
   strategies were Listen for Main Ideas/Gist, Recognize Examples, Listen for Sequence Markers, and Predict from
   Context Before Confirming, the assessment should include at least one item per strategy, not just a generic
   comprehension check). Pull the actual strategies from the Set's lesson files or its Rotation Log
   entry rather than re-guessing from the Module Lesson-Plan alone.
   Do not test vocabulary items from the Set's own lessons directly (a student who missed one lesson would be
   penalized for absence, not for a comprehension gap), but do test the same _kind_ of vocabulary-in-context
   skill using words drawn from the new source's own transcript, glossed the same way a lesson's Phase 1 would.

### A.2 Structure (single class period, matching a lesson's Day 1 in length and shape)

```
LISTENING ASSESSMENT (approx. 45-55 MIN)  |--Setup & Vocab (10)--|--Play & Notes (10-15)--|--Tiered Items (20-25)--|--Wrap (5)--|
```

- **Setup & Vocabulary (10 min):** present the new source's citation block. Pre-teach 3-5 target words/phrases
  from its real transcript (fewer than a lesson's 4-6, since this is a shorter single-purpose period). No
  Background Notes needed unless the source names something genuinely opaque - keep this section lean.
- **Play & Notes (10-15 min):** play the source once (twice only if the band/Level table's runtime is short
  enough that two plays still fit the period - state which in the generated assessment). Students take notes on
  a simple organizer matched to the Module (same organizer type the Set's lessons used), individually, not as a
  shared board-dependent moment - this is an individual assessment, so there is no board synthesis step here,
  unlike a lesson's Phase 4.
- **Tiered Items (20-25 min):** one item set per task Level in the band (3 for Beginner, 4 for Intermediate/
  Advanced/Proficient), each set testing that Level's exact CSV Listening can-do plus at least one item per
  strategy taught in the Set (A.1). Apply the same balanced-duration principle as the Lesson prompt's fourth
  addendum: lower Levels get more, shorter items; higher Levels get fewer, deeper items, so time-on-task is
  roughly even across Levels. Students work at their own assigned task Level; there is no live differentiated
  discussion step, since this is individual seatwork, not a class activity.
- **Wrap (5 min):** collect. No transfer-check performance step here (unlike a lesson's Phase 5) - the whole
  period already is the transfer check.

### A.3 Scoring

Provide a simple point-value key per item (not a full rubric - most items are short-answer, multiple-choice, or
fill-in-the-frame, mirroring the lesson's own differentiated task formats) plus one holistic note per task Level
describing what a passing performance looks like in plain language (e.g., "Level 3: correctly identifies the
described object from the two-slot frame and completes both slots using words actually heard in the source").
Do not assign letter grades or numeric percentages in the generated document itself - that conversion is a
teacher/gradebook decision outside this prompt's scope.

### A.4 Self-check (apply before finalizing)

1. Is the source real, verified, cited in full, distinct from all 4 of the Set's own taught sources and from
   every prior Set's assessment source for this Module/Band?
2. Does the source match the Module's verb and the band's lower-Level runtime/pace/register ceiling (Section
   0.2 of the Lesson prompt)?
3. Does every task Level's item set trace to that Level's verbatim CSV Listening can-do?
4. Does the item set cover every listening strategy actually taught in this Set's 4 lessons, at least once each?
5. Is time-on-task roughly balanced across task Levels (more/shorter items low, fewer/deeper items high)?
6. Does the lowest task Level get a genuine (if scaffolded) interpretive item, not fact-retrieval only -
   Respectful Tiers applied to an assessment context?
7. No em-dashes anywhere. Citation block first. Timestamp ranges used for any segment reference, never
   paragraph letters.

---

## PART B: SPEAKING ASSESSMENT (every Set)

### B.0 Scope, cadence, and inputs

Run this after the same Set (4 lessons) that Part A was just generated for - both parts now run on the same
per-Set cadence, not staggered. Required inputs: the Module, the Band, and the Set number (or the 4 lesson files
themselves, to confirm the four speaking skills actually taught, the same "confirm against what was actually
generated" rule as A.0).

No new source is sourced or searched for this assessment. The speaking prompt is original (invented for the
assessment, the same way a lesson's Day 1 Phase 5 Closing Transfer Check script is invented), grounded in the
Module's own verb and topic range rather than in any one taught source, since the point is to check whether the
skill transfers away from every specific text the student has already rehearsed against.

### B.1 Mechanism by band

**The mechanism is not uniform across bands - it is chosen by band, per user direction 2026-09-04, because
live presentation and solo recording trade off differently depending on how much of a public-performance ask a
band's students can reasonably handle, and because Advanced/Proficient's actual Speaking can-dos increasingly
call for register adjustment in response to a real listener, which only a live format can show.**

**Beginner and Intermediate bands: Teams Speaking Progress solo recording is the default and the formally scored
Speaking assessment for the Set.** There is no separate in-class live speaking test layered on top for these two
bands - the recording IS the assessment, not homework or practice for something else. It is still rubric-scored
(B.4), just lower-stakes in format than a live public performance would be: students may re-record before
submitting, which is a deliberate feature (scoring reflects a student's best take, not their most nervous one),
not a gap to patch.

**A student who wants to present live instead may do so, teacher-approved, using the exact same prompt.** Per
user direction 2026-09-04, this is an opt-in in the other direction from Advanced/Proficient's swap (B.1 below):
the default stays the recording, but a willing student is not held to it. Unlike the Advanced/Proficient case,
this does not require generating a second version of the task - the Teams-recording prompt (B.3) is already a
short, self-contained monologue with a fixed topic and target length, and it can be delivered live to the class
exactly as written, scored against the same rubric (B.4). Do not generate a separate live-presentation task or
rubric for Beginner/Intermediate; the assessment document only needs a one-line note that the same task may be
delivered live instead of recorded, teacher-approved, same scoring either way. As with the Advanced/Proficient
swap, tracking who opts in and any scheduling it requires is a teacher decision outside this prompt's scope.

**Advanced and Proficient bands: a live presentation (solo or small-group, per B.2) is the default and the
formally scored Speaking assessment for the Set.** In addition, generate a Teams-recording version of the exact
same task for every Set at these bands - not as homework, and not as a separate lighter assessment, but as a
standing scored alternative a student can be moved to (an absence, illness, or any teacher-approved reason).
Both versions are scored against the same rubric (B.4) so a swap never changes what's being measured, only how
it's captured. **This prompt does not need to track or enforce how many times a given student uses the
recording alternative** - how many swaps a student gets and who approves them is a program/teacher policy
decision (per user direction, tracked outside this prompt, e.g. a per-semester cap with teacher approval); this
prompt's only obligation is to make sure a Teams-recording version of the task always exists so that option is
available whenever a teacher needs it.

| Band         | Default mechanism                             | Teams-recording version also generated? | Live-delivery option?                                                                   |
| ------------ | --------------------------------------------- | --------------------------------------- | --------------------------------------------------------------------------------------- |
| Beginner     | Teams solo recording (this IS the assessment) | N/A - it's already the recording        | Yes, teacher-approved, same task delivered live instead - no separate version generated |
| Intermediate | Teams solo recording (this IS the assessment) | N/A - it's already the recording        | Yes, teacher-approved, same task delivered live instead - no separate version generated |
| Advanced     | Live presentation (solo or small-group)       | Yes, every Set, same task, same rubric  | N/A - live is already the default                                                       |
| Proficient   | Live presentation (solo or small-group)       | Yes, every Set, same task, same rubric  | N/A - live is already the default                                                       |

### B.2 Format specifics

**Teams solo recording (Beginner/Intermediate, and the standing alternate version at Advanced/Proficient):**
each student individually records themselves responding to one written or teacher-delivered prompt, at their
assigned task Level, using Teams Speaking Progress. A monologue by default at every task Level (no partner/
peer-response step required) - keep the format logistically simple, since these recordings happen outside class
time without a partner's coordination. At Beginner/Intermediate, note plainly in the generated assessment that a
student may instead deliver this same prompt live in class, teacher-approved, scored against the same rubric -
this is not a different task, just a different delivery of the one already written.

**Live presentation (Advanced/Proficient default):** solo or small-group, teacher's choice per Set based on
what the Set's Module/task naturally supports (a small-group presentation fits a Module like Socializing or a
task with a natural multi-speaker shape better than a strictly individual Module task does; default to solo
when the Module doesn't clearly call for a group). Budget real class time separately from a normal period -
roughly 2-3 minutes per student (or per group) times roster size, likely a dedicated period or a spread across
several days, not folded into a single 75-minute lesson-length slot the way Part A's Listening assessment is.
Note this time budget explicitly in the generated assessment so it doesn't get planned like a normal single
period.

### B.3 Structure (per task Level)

For each task Level in the band, write one self-contained prompt with:

- **A speaking task grounded in the Module's own verb**, scoped to that Level's verbatim CSV Speaking can-do,
  drawing on the speaking skills actually taught in this Set (state in the prompt itself which 1-2 speaking
  skills this particular Level's task is emphasizing, so scoring can target them specifically).
- **A clear topic**, invented for the assessment (not tied to any of the Set's own 4 lessons' sources), matched
  to the Module's topic range (e.g., Describing: describe a real or invented person/place/object using the
  Level's required feature/comparison/evaluative-word elements) - concrete enough that a student is not left
  guessing what to talk about, the same way the Lesson prompt's Day 2 Phase 2 tasks are never open-ended without
  a frame.
- **A target length**, scaled by task Level the same balanced-duration way the Lesson prompt scales item counts:
  roughly 30-45 seconds for the lowest task Level in a band, up to 90-120 seconds for the highest (Teams
  recording format); a live presentation's target length can run longer per the teacher's own time budget (B.2)
  but should still scale the same direction, shorter at the lowest Level and longer at the highest.
- **A plain submission or delivery instruction** - for a Teams recording, how and by when to submit; for a live
  presentation, which class day(s) it runs on.
- **At Advanced/Proficient, the Teams-recording version's prompt and target length should match the live
  version's as closely as the format allows** (same topic, same emphasized skills, same task Level requirements)
  so the two are genuinely interchangeable for scoring purposes, not two different assessments that happen to
  share a rubric.

### B.4 Scoring rubric

One rubric per task Level, 3-4 criteria, each tied directly to that Level's CSV can-do language and the 1-2
speaking skills the task is emphasizing (per B.3). Use a simple 3-point scale per criterion (Not yet / Developing
/ Meets) rather than a numeric score out of 100 - this keeps the rubric usable directly against Teams Speaking
Progress's own review interface for the recorded format, and just as quickly markable on a clipboard for a live
presentation. At Advanced/Proficient, use the same rubric for both the live and Teams-recording versions of a
Set's assessment (per B.1/B.3) - one rubric per task Level, not two. Do not invent a program-wide letter-grade
conversion here; that is a teacher/admin decision outside this prompt's scope, same as A.3.

### B.5 Self-check (apply before finalizing)

1. Does the Speaking assessment run for the same Set Part A was just generated for (same-Set cadence, not
   staggered)?
2. Is the correct mechanism used for the band - Teams recording as the default and formal assessment for
   Beginner/Intermediate; live presentation as the default plus a same-task Teams-recording version for
   Advanced/Proficient?
3. At Advanced/Proficient, does the Teams-recording alternate use the same topic, same emphasized skills, and
   the same rubric as the live version, so a swap doesn't change what's being measured?
4. At Beginner/Intermediate, does the assessment note the same-task, teacher-approved live-delivery option (not
   a separately generated task or rubric) rather than staying silent on it or inventing a second version?
5. Does every task Level's prompt trace to that Level's verbatim CSV Speaking can-do?
6. Is the emphasized skill set (1-2 skills per Level) drawn from what was actually taught in this Set?
7. Is target length/time scaled by task Level (shorter/lower at the lowest Level, longer/deeper at the highest)?
8. Does the lowest task Level get a genuine production task (not just a fill-in-the-blank recitation) -
   Respectful Tiers applied to whichever format this band uses?
9. For a live presentation, is the actual class-time budget (minutes per student/group times roster size) noted
   explicitly, distinct from a normal single-period plan?
10. No em-dashes anywhere.

---

## Style & Formatting Constraints (both parts)

Same constraints as the Lesson Generation Prompt: no em-dashes anywhere; citation block first for any real
source (Part A only - Part B's prompts are invented, so no citation block applies there); timestamp ranges, not
paragraph letters, for any segment reference. Task Levels are shown as the same star system the Student Print
Formatting Prompt already uses if a student-facing version of either part is produced - this prompt generates
the teacher-facing assessment and key/rubric only; a student-facing print version is a separate step, the same
relationship the Lesson prompt has with the Student Print Formatting Prompt, and is not yet built for
assessments (flag as pending work if requested).

## Open items for this v1

- Not yet run against a real Set. Treat every number above (period length, recording length, item counts,
  live-presentation time budget) as a reasoned starting point, exactly the way the Lesson prompt's v1 did, and
  expect addenda once a real Listening assessment and a real Speaking assessment (both mechanisms) have actually
  been generated and given.
- A student-facing print/submission version (mirroring the Student Print Formatting Prompt) is not yet built for
  either part.
- The recording-swap budget and approval process at Advanced/Proficient (how many times a student may use the
  Teams-recording alternate instead of presenting live, and who approves it) is intentionally out of scope for
  this prompt - a program/teacher policy decision, tracked outside generation time. This prompt's only
  obligation is to make sure the alternate version always exists.
- Scoring-to-gradebook conversion (how a rubric's Not yet/Developing/Meets or a Listening item key becomes a
  report-card mark) is intentionally out of scope - a program-level policy decision, not a generation-time one.
