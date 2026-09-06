# Passage Reading Module Lesson-Plan Generation Prompt (v1.2)

Companion to the Passage Reading Lesson Generation Prompt (v2.7, Band-Calibrated). Updated to match v2.5's
band-scoped task-Level system: task Levels for a module plan are pulled from Section 0.1's Task Levels by Band
table (3 task Levels for the Beginner band, 4 for Intermediate, Advanced, and Proficient), not the old fixed
three-tier Level A/B/C model this doc used against v2.4. The plan's structure (topics, genres, strategy rotation,
vocabulary themes) is otherwise unchanged.

**Current version: v1.2.** For the full dated version history and the reasoning behind each change (including the
8-lesson vs. 4-lesson module-size correction), see `Changelog.md`.

Produces a 4-lesson **module plan only** (4 lessons x 2 days each = 8 instructional days total) - topics, genres,
reading-strategy and oral-protocol rotation, vocabulary themes, and task-Level-to-objective mapping - not anchor
texts, tasks, or answer keys. Run this first, review/approve the plan, then generate the module's lessons one at a
time (or two at a time, per the master document's Step 2 pacing) against it, checking word count and band
ceiling on each before moving to the next. Do not generate all 4 lessons in a single pass: batching that large is
exactly where this program's own generation prompt has previously let band-calibration errors slip through
undetected.

Why this exists: several of the lesson prompt's constraints are module-wide, not lesson-wide (genre rotation across
the whole bank, reading-strategy/activation/oral-protocol variety, no vocabulary overlap within a module, task-Level
content that must trace to the actual Level objectives in learningobjectives.csv rather than an invented difficulty
curve). Those are much easier to satisfy by planning the whole module up front than by improvising lesson-by-lesson
and hoping variety and objective alignment come out right in aggregate.

Scope: plan **one module at a time**, not the whole program in a single pass. The program has 8 modules total
(learningobjectives.csv: Describing, Narrating, Explaining, Instructing, Evaluating, Arguing, Transacting,
Socializing), so planning all of them up front would mean reviewing roughly 32 lesson-rows in one sitting and
locking in plans for modules you may not teach for months, against a prompt system that is still actively revised.
The risk that matters more than any of that - real cross-module repetition (the same genre opening Module 4 that
just closed Module 3, a vocabulary theme reused two modules later) - is handled instead by the Program Rotation
Log below, which gives each new module-planning run a light memory of the modules already planned, without
requiring them to be planned all at once.

---

## 0. Rotation Log (read before planning, update after approval)

**What it is:** a single running record, separate from any one module's plan, of what every already-planned
module actually used - genre, reading strategy, Phase 1 hook, Phase 3 protocol, vocabulary theme, and topic, one
row per lesson. It is the only thing that lets a new module's plan avoid repeating what a previous module already
did; without it, each module-planning run only ever sees its own 4 lessons and cross-module repetition is
invisible until a teacher notices it in the classroom.

**Where it lives:** `Rotation_Log.md`, one project doc, appended to (never
overwritten) each time a module plan is approved. If it does not exist yet, this is the first module ever planned;
create it fresh and note that cross-module checks below are not applicable this time.

**Before planning a new module:** read the full log. Note, in particular, the LAST lesson row of the most
recently logged module (whichever genre, reading strategy, Phase 1 hook, and Phase 3 protocol it used), and the
full list of vocabulary themes and topics used across every logged module so far.

**Cross-module rules (lighter touch than the within-module rules in Task step 3, deliberately - see note below):**

- **Genre and reading strategy (adjacency only):** the new module's Lesson 1 must not repeat the genre or
  reading strategy used in the previous module's Lesson 4. This is the same adjacency logic the within-module
  rule already uses between consecutive lessons, just carried across the module boundary.
- **Phase 1 hook and Phase 3 protocol (adjacency only):** same rule - Lesson 1 of the new module should not
  repeat what Lesson 4 of the previous module used. These banks only have 4 options each, so full
  non-repetition across 8 modules is not realistic; adjacency is what actually matters for variety a student
  would notice.
- **Vocabulary theme (recency check, not full-history block):** flag, rather than automatically forbid, a new
  theme that duplicates or closely overlaps one used in the immediately preceding module. A theme repeating
  from several modules back is lower-risk and does not need to be blocked; note it in the self-check if you
  notice it, but do not treat the full log as a hard-exhaustion list to avoid forever.
- **Topic/anchor idea:** same recency check as vocabulary theme - flag an obvious repeat from the immediately
  preceding module, note but don't block older repeats.

Why lighter touch than the within-module rules: the within-module rules (no two consecutive lessons repeat a
genre or strategy, no vocabulary theme repeats anywhere in the module) are enforceable exactly because all 4
lessons are visible at once in a single planning pass. Across modules, only the log's history is visible, and a hard
full-history block would eventually make later modules impossible to plan (the genre and Phase 1/3 banks are
finite). Adjacency plus a recency flag catches the repetition a student would actually notice (two modules in a
row opening the same way) without over-constraining a program that will eventually run many modules.

**After the module plan is reviewed and approved** (not on a rough draft still being revised): append one new
section to the log, formatted as:

```
## Module N: <Name> (planned <date>)
| Lesson # | Genre | Reading Strategy | Phase 1 Hook | Phase 3 Protocol | Vocabulary Theme | Topic |
|---|---|---|---|---|---|---|
| 1 | ... | ... | ... | ... | ... | ... |
| 2 | ... | ... | ... | ... | ... | ... |
| 3 | ... | ... | ... | ... | ... | ... |
| 4 | ... | ... | ... | ... | ... | ... |
```

Do not append a draft that is still being revised; the log's value depends on it reflecting only plans that were
actually approved and are actually going to be taught.

---

## INPUTS (fill in before running)

- **Module:** [e.g. "Module 1: Describing"]
- **Band:** [Beginner / Intermediate / Advanced / Proficient]. A specific Level is not requested separately (matching
  v2.7 of the lesson prompt): this band's task Levels are looked up automatically from Section 0.1's Task Levels by
  Band table (Beginner: Levels 1-2-3; Intermediate: 2-3-4-5; Advanced: 4-5-6-7; Proficient: 5-6-7-8). Note that a
  band's task-Level span reaches one band beyond its own two CEFR levels (the band-distance invariant), so it is
  wider than "this band's own Levels."
- **Number of lessons in this module:** [default 4] (4 lessons x 2 days each = 8 instructional days)
- **Source of truth for objectives:** learningobjectives.csv, filtered to this Module, this band's task Levels (per
  the Task Levels by Band table above), and the **Reading modality only** - matching the v2.7 lesson prompt's own
  grounding rule (Section 0.1: "each task Level anchored to an actual row in learningobjectives.csv (Level x
  Modality=Reading x the requested Module)"). Listening/Speaking and Writing objectives are out of scope for this
  program: Writing is addressed in a separate writing class, and this plan should not select or justify a task by
  tracing it to a Writing (or Listening/Speaking) Can-do statement. Writing can still appear as an occasional
  activity format inside a lesson or its homework - that is fine and expected - it just is not what grounds the
  task design.
- **Rotation Log:** `Rotation_Log.md`, read in full before planning
  (see Section 0 above); if it does not exist yet, treat this as the first module and skip cross-module checks

## TASK

1. Read the Rotation Log per Section 0. Identify the previous module's Lesson 4 row (for the adjacency
   checks) and the full set of vocabulary themes and topics used so far (for the recency flag). If the log doesn't
   exist yet, note that this is the first planned module.

2. Determine this band's task Levels from Section 0.1 of the Passage Reading Lesson Generation Prompt (v2.7)'s
   Task Levels by Band table (3 for Beginner, 4 for Intermediate/Advanced/Proficient). Pull the actual rows from
   learningobjectives.csv for this Module and each of those task Levels, **Reading modality only**. Quote the
   Reading "Can-do" statement verbatim (not paraphrased) for every task Level in the band, not just the band's own
   two CEFR levels. Do not also pull or quote that Level's Writing (or Listening/Speaking) objective: it is not part
   of this program's scope and should not appear in the plan. These quoted Reading statements are the authority
   for what each task Level does in every lesson in this module - do not invent an easier/harder version of the
   main task instead of using them.

3. Produce a plan table, one row per lesson (4 rows unless told otherwise), with these columns:
   - Lesson #
   - Topic / anchor idea (one line; distinct from every other lesson in this module; flag if it closely echoes a
     topic from the previous module per Section 0). **Grounded in reality, band-conditioned:**
     - **Beginner:** a generic, familiar, universal scene (a kitchen, a park, a shoe) is fine and often preferable -
       real-world specificity adds vocabulary/cultural load with no comprehension payoff at a purely-decoding
       task Level, and genericness is not a defect at this band.
     - **Intermediate and up:** the topic must be grounded in a real, verifiable referent - an actual place, food,
       craft, custom, or documented phenomenon a curious student could look up and confirm - not a generic
       invented slice-of-life scene with the names filed off. The surrounding frame (an email, a diary entry, a
       fictional narrator) can still be invented; what the text describes should be real. This gets more load-bearing
       as the band rises: Advanced/Proficient topics should lean further into genuinely real-world subject matter,
       matching Section 0.2's own note that word counts are anchored to real published reading materials, not an
       invented curve.
     - **Guardrail:** never fabricate a quote, dialogue, or first-person statement and attribute it to a real, named,
       identifiable individual as something they actually said. An interview-genre lesson can feature a fictional or
       composite person describing a real place/craft/practice; it must not be framed as a real specific person's
       actual words.
     - **Sourcing:** when the session generating this plan has live web search available, use it to find a current,
       concrete real-world referent (an actual well-documented place, practice, or trend) rather than relying on a
       generic invented scene - but do not copy or closely paraphrase a specific source's text; the anchor text
       itself is still original writing built to this program's own complexity ceiling (Section 0.2), not lifted or
       lightly reworded source content. If live search isn't available, ground the topic in well-established
       real-world knowledge instead (something broadly documented, not requiring a live source) rather than
       skipping grounding altogether.
   - Genre (from Section 0.6's genre bank for this band; across all 4 lessons the bank must be genuinely sampled
     - every band's genre bank has well over 4 options, so no lesson needs to repeat another's genre at all; no
     two consecutive lessons repeat a genre; Lesson 1 must not repeat the previous module's Lesson 4 genre)
   - Reading strategy (from the Reading Execution Rules list; no two consecutive lessons repeat one, and the set
     of 4 lessons uses at least 3 distinct strategies, not alternating between just two; Lesson 1 must not repeat
     the previous module's Lesson 4 strategy)
   - Phase 1 activation hook (Visual Inquiry / Four-Corner Debate / Mystery Quote / K-W-L Walk - the bank has
     exactly 4 options and the module has exactly 4 lessons, so each hook can and should be used exactly once;
     Lesson 1 should not repeat the previous module's Lesson 4 hook)
   - Phase 3 oral output protocol (Town Hall Role-Play / Fishbowl / Concentric Circles / Jigsaw Expert Panels / a
     small-group discussion carousel - all five are valid at this program's actual class size, 8-12 students, per
     Section 0.10 of the lesson generation prompt, as long as the lesson itself supplies the required scaffolding:
     an explicit outer-circle task for Fishbowl, 2-3 rotated discussion prompts for any protocol; rotate, don't
     default to one; Lesson 1 should not repeat the previous module's Lesson 4 protocol)
   - Target vocabulary theme (one line describing the semantic field this lesson's 4-6 words come from; must not
     overlap another lesson's theme in this module; flag if it closely echoes a theme from the previous module)
   - Task-Level basis: for every task Level in this band's Task Levels by Band table (3 rows for a Beginner-band
     module, 4 for Intermediate/Advanced/Proficient - the row count is expected to differ by band, that is not an
     error), name the exact Reading-modality CSV objective sentence (Level N, Reading) that task's content is built
     to satisfy. State explicitly which task Level each objective maps to and why, rather than leaving it implicit.
     Do not collapse this into a single generic task description; each task Level gets its own named objective. If a
     lesson's task or its homework happens to use writing as the activity format, that is a format choice, not a
     grounding one - do not additionally name a Writing CSV objective for it.
   - Interactivity note: nothing above requires a task to be written work. Favor variety across the oral,
     collaborative, and physical/visual task formats the lesson prompt already supports (Reader's Theater,
     Jigsaw, Town Hall, a small-group discussion carousel, board-dependent moments, etc.) rather than defaulting
     every task Level to a writing-based activity; writing is one fine format among several, not the default one.

4. After the table, run a self-check and report it in a few sentences:
   - Is every genre and reading strategy used at least once across the 4 lessons, with no lesson needing to
     repeat another's since every band's bank comfortably exceeds 4 options?
   - Does any topic or vocabulary theme repeat across the module?
   - Does every task Level's content trace to an actual quoted Reading-modality CSV line for that specific Level,
     not a generic simplification of the main task and not a Writing (or Listening/Speaking) objective? Does each
     lesson include exactly the right number of task Levels for its band (3 for Beginner, 4 for
     Intermediate/Advanced/Proficient), matching self-check item 17 of the v2.7 lesson prompt?
   - Does the module's own skill verb (Describing/Explaining/etc.) stay consistent across all 4 planned lessons
     rather than drifting toward a neighboring module's skill?
   - For Intermediate band and up, is every topic grounded in a real, verifiable referent rather than a generic
     invented scene (Beginner is exempt)? Does any topic fabricate a quote or statement attributed to a real,
     named individual (it must not)?
   - Does every lesson using Fishbowl supply an explicit, active outer-circle task (a word/method list, a tally, or
     a one-line reaction - never passive listening) at the plan level, and does every lesson (any protocol) call
     for 2-3 rotated discussion prompts rather than one static prompt for the full window, per Section 0.10 of the
     lesson generation prompt? (All five Phase 3 protocols - Town Hall Role-Play, Fishbowl, Concentric Circles,
     Jigsaw Expert Panels, small-group discussion carousel - are equally valid rotation choices at this program's
     actual class size once scaffolded this way; none is reserved for large classes.)
   - (Cross-module, skip if this is the first planned module) Does Lesson 1 avoid repeating the previous
     module's Lesson 4 genre, reading strategy, Phase 1 hook, and Phase 3 protocol? Does any vocabulary theme
     or topic closely echo one from the immediately preceding module - and if so, is that noted rather than
     silently repeated?

5. Do not write any anchor text, comprehension question, vocabulary list, or answer key in this step. If asked to
   also generate lesson content in the same turn, stop and confirm the plan is approved first.

## OUTPUT

The plan table, then the self-check paragraph. Once the plan is reviewed and approved, also produce the
Rotation Log entry (Section 0's format) ready to append to `Rotation_Log.md`. Nothing else.
