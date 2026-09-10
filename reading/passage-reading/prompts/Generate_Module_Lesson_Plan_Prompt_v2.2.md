# Passage Reading Module Lesson-Plan Generation Prompt (v2.1)

Companion to the Passage Reading Lesson Generation Prompt. Produces a plan for **one Set** (4 lessons, 8
instructional days): topics, genres, reading-strategy and oral-protocol rotation, vocabulary themes, and
task-Level-to-objective mapping. Not anchor texts, tasks, or answer keys. Run this first, approve the plan, then
generate the Set's lessons two at a time against it; never a whole Set in one pass, which is where calibration
errors slip through.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` (Sets, §C; Rotation Log mechanics and the
cross-Set / cross-Module adjacency rules, §F) and `shared/Generation_Quality_Standards.md` alongside it.

**Current version: v2.1.** History: `Changelog.md`.

Why this exists: several of the Lesson prompt's constraints are Set-wide (genre rotation across the bank,
strategy/hook/protocol variety, no vocabulary overlap within a Set, task-Level content traced to real CSV rows).
They are far easier to satisfy by planning the Set up front than lesson by lesson. Plan one Set at a time; the
Rotation Log carries the memory across Sets and Modules.

## 0. Rotation Log

Mechanics (read before planning, append after approval, cross-Set and cross-Module adjacency, recency flags):
Conventions §F. This lesson type's rotated columns are genre, reading strategy, Phase 1 hook, and Phase 3
protocol; vocabulary theme and topic get the recency flag. Append the approved Set under this Module/Band's
`## Module N` section in `Rotation_Log_<Band>.md` as:

```
### Set S (planned <date>)
| Lesson # | Genre | Reading Strategy | Phase 1 Hook | Phase 3 Protocol | Vocabulary Theme | Topic |
|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... |
```

## INPUTS (fill in before running)

- **Module:** e.g. "Module 1: Describing".
- **Band:** Beginner / Intermediate / Advanced / Proficient. Task Levels come from Conventions §B; no separate
  Level is requested.
- **Set number:** default the next Set not yet planned for this Module/Band (Set 1 if none).
- **Number of lessons:** default 4.
- **Objectives:** `learningobjectives.csv`, filtered to this Module, the band's task Levels, and the **Reading
  modality only**. Writing and Listening/Speaking rows are out of scope; writing may appear as an activity format
  inside a lesson, but never grounds a task.
- **Rotation Log:** `Rotation_Log.md` plus this Band's `Rotation_Log_<Band>.md`, read in full.

## TASK

1. Read the Rotation Log per Conventions §F: the highest lesson number used so far (this Set starts at the next
   integer), the most recent Set's final lesson row (or the previous Module's, for a new Module/Band), and the
   vocabulary themes and topics used so far.

2. Determine the band's task Levels (Conventions §B). Pull the Reading row from the CSV for this Module and each
   task Level and quote the Can-do verbatim for every Level, including borrowed ones. These statements are the
   authority for what each task Level does in every lesson of the Set (Quality Standards §A).

3. Produce a plan table, one row per lesson, with these columns:
   - **Lesson #** (global for this Module/Band, continuing across Sets).
   - **Topic / anchor idea,** one line, distinct from every other lesson in the Set, flagged if it echoes the
     previous Module. Grounded in reality by band: **Beginner** may use a generic, familiar scene (a kitchen, a
     park); **Intermediate and up** must use a real, verifiable referent (an actual place, food, craft, custom, or
     documented phenomenon a student could look up), with the surrounding frame (an email, a narrator) free to be
     invented; this gets more load-bearing as the band rises. **Guardrail:** never fabricate a quote or statement
     attributed to a real, named individual; an interview-genre lesson uses a fictional or composite person
     describing a real subject. **Sourcing:** use live web search where available to find a concrete real-world
     referent, but the anchor text stays original writing to the program's own ceiling, never copied or closely
     paraphrased source text; without search, ground the topic in well-established knowledge.
   - **Genre,** from the band's bank (Lesson prompt 0.6); every bank exceeds 4 options, so no genre repeats within
     the Set, and Lesson 1 follows the adjacency rule.
   - **Reading strategy,** from the Reading Execution Rules; no consecutive repeat, at least 3 distinct strategies
     across the Set, adjacency rule for Lesson 1.
   - **Phase 1 hook:** Visual Inquiry / Four-Corner Debate / Mystery Quote / K-W-L Walk, each used once across the
     4 lessons, adjacency rule for Lesson 1.
   - **Phase 3 protocol:** Town Hall Role-Play / Fishbowl / Concentric Circles / Jigsaw Expert Panels / small-group
     carousel, all valid at 8-12 students once scaffolded (Lesson prompt 0.10); rotate; adjacency rule for Lesson 1.
   - **Target vocabulary theme,** one line naming the semantic field; no overlap within the Set or with an earlier
     Set in this Module/Band; flagged if it echoes the previous Module.
   - **Task-Level basis:** for every task Level in the band, the exact Reading CSV objective (Level N) that Level's
     task is built to satisfy, mapped explicitly. Never one generic task description; never a Writing objective for
     a task that happens to use writing as its format. For a fixed-output Level (Level 1 or 2), also name the
     0.11 shape each of the lesson's slots uses, so no shape sits in the same slot in consecutive lessons
     (Quality Standards §D10).
   - **Interactivity note:** favor variety across oral, collaborative, and physical or visual formats; writing is
     one format among several, not the default.

4. After the table, report a short self-check: every genre and strategy used without repeats; no topic or theme
   repeats within the Set or against earlier Sets; every task Level traced to a quoted Reading row, exactly the
   band's Level count; the Module's verb consistent across all lessons; Intermediate-and-up topics real and
   verifiable with no fabricated attributed quotes; Fishbowl lessons carrying an explicit outer-circle task and
   every lesson 2-3 rotated prompts; no Level 1-2 task shape in the same slot in consecutive lessons; Lesson 1
   following the adjacency rule in every rotated column, with theme and topic echoes flagged; Lesson #
   continuing the global numbering.

5. Write no anchor text, question, vocabulary list, or answer key in this step. If asked to generate lesson
   content in the same turn, stop and confirm the plan is approved first.

## OUTPUT

The plan table, then the self-check paragraph. Once approved, also the Rotation Log entry in Section 0's format,
ready to append. The plan saves as `lessons/<band>/Module_<N>/Module<N>_<Band>_Lesson_Plan.md` (Conventions §D).
Nothing else.
