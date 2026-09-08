# Listening/Speaking Module Lesson-Plan Generation Prompt (v2)

Companion to the Listening/Speaking Lesson Generation Prompt. Produces a plan for **one Set** (4 lessons, 8
instructional days): topic directions to search within, content-format, listening-strategy, speaking-skill,
hook, and protocol rotation, vocabulary themes, and task-Level-to-objective mapping. Not an actual source, tasks,
or answer key. Run this first, approve the plan, then generate the Set's lessons one at a time against it.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` (Sets, §C; Rotation Log mechanics and the
cross-Set / cross-Module adjacency rules, §F) and `shared/Generation_Quality_Standards.md` alongside it.

**Current version: v2.** History: `Changelog.md`.

Why this exists: the Lesson prompt's constraints are Set-wide (format rotation, strategy/skill/protocol variety,
no vocabulary-theme overlap, task-Level content traced to real CSV rows), easier to satisfy by planning the Set
up front. Plan one Set at a time; the Rotation Log carries the memory across Sets and Modules. The 8 Modules are
shared with Passage Reading, so a class moving through both tracks meets the same verb sequence in both.

## 0. Rotation Log

Mechanics: Conventions §F. This lesson type's rotated columns are content format, listening strategy, speaking
skill, Phase 1 hook, and Phase 3 protocol; vocabulary theme and topic direction get the recency flag. Append the
approved Set under this Module/Band's `## Module N` section in `Rotation_Log_<Band>.md` as:

```
### Set S (planned <date>)
| Lesson # | Content Format | Listening Strategy | Speaking Skill | Phase 1 Hook | Phase 3 Protocol | Vocabulary Theme | Topic Direction |
|---|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... | ... |
```

## INPUTS (fill in before running)

- **Module:** e.g. "Module 2: Narrating".
- **Band:** Beginner / Intermediate / Advanced / Proficient. Task Levels come from Conventions §B.
- **Set number:** default the next Set not yet planned for this Module/Band (Set 1 if none).
- **Number of lessons:** default 4.
- **Objectives:** `learningobjectives.csv`, filtered to this Module, the band's task Levels, and the
  **Listening/Speaking modality only**.
- **Rotation Log:** `Rotation_Log.md` plus this Band's `Rotation_Log_<Band>.md`, read in full.

## TASK

1. Read the Rotation Log per Conventions §F: the highest lesson number used so far, the most recent Set's final
   lesson row (or the previous Module's), and the themes and topic directions used so far.

2. Determine the band's task Levels (Conventions §B). Pull the Listening/Speaking row for this Module and each
   task Level and quote the full Description verbatim; it holds both halves, and note which half each lesson's
   day builds toward (Listening on Day 1, Speaking on Day 2). The grounding does not change Set to Set; only the
   topics and real sources do.

3. Produce a plan table, one row per lesson, with these columns:
   - **Lesson #** (global for this Module/Band, continuing across Sets).
   - **Topic direction,** one line naming a real-world subject area to search within ("a home cook's neighborhood
     food tradition"), distinct from every other lesson in the Set and from earlier Sets in this Module/Band,
     flagged if it echoes the previous Module. A search direction, not a specific source: the real video or audio
     is found at generation time against the Lesson prompt's 0.1-0.2; name no real title or speaker here unless
     already confirmed.
   - **Content format,** from the Lesson prompt's Module-to-source guidance (0.1); varied across the Set, no
     consecutive repeat, adjacency rule for Lesson 1.
   - **Listening strategy** and **speaking skill,** from the Lesson prompt's 0.4 banks; no consecutive repeat, at
     least 3 distinct across the Set, adjacency rule for Lesson 1.
   - **Phase 1 hook** and **Phase 3 protocol,** from the 0.4 banks; rotate; adjacency rule for Lesson 1.
   - **Target vocabulary theme,** one line; no overlap within the Set or with earlier Sets in this Module/Band;
     flagged if it echoes the previous Module.
   - **Task-Level basis:** for every task Level, the exact Listening/Speaking CSV objective (Level N) with both
     halves named explicitly, the Listening half for Day 1 and the Speaking half for Day 2.

4. After the table, report a short self-check: every format, strategy, and skill used without repeats (twice
   only where a bank is smaller than the lesson count); no topic direction or theme repeats within the Set or
   against earlier Sets; every task Level traced to a quoted row with both halves, exactly the band's Level
   count; the Module's verb consistent across all lessons; Lesson 1 following the adjacency rule in every rotated
   column, echoes flagged; Lesson # continuing the global numbering.

5. Search for no source, write no task, produce no answer key in this step. If asked to generate lesson content
   in the same turn, stop and confirm the plan is approved first.

## OUTPUT

The plan table, then the self-check paragraph. Once approved, also the Rotation Log entry in Section 0's format,
ready to append. The plan saves as `lessons/<band>/Module_<N>/Module<N>_<Band>_Lesson_Plan.md` (Conventions §D).
Nothing else.
