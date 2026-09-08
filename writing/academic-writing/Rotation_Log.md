# Academic Writing Rotation Log

Overview only, as of the 2026-09-06 per-Band split (Writing's first - see `CLAUDE.md`'s "Rotation Log splits by
Band" convention and `shared/Program_Conventions.md` §F for the general mechanics). Each Band that has a
generated Set gets its own `Rotation_Log_<Band>.md`. **A new Band's file is created lazily** the first time a
Set in that Band is generated, mirroring how `Set_<N>/` folders are created lazily - see
`shared/Program_Conventions.md` §D.

**Current files:**
- [`Rotation_Log_Intermediate.md`](Rotation_Log_Intermediate.md) - Set 1 ("my phone case", Lessons 1-4)
- [`Rotation_Log_Advanced.md`](Rotation_Log_Advanced.md) - Set 1 ("Two apartments... for Sam", Lessons 1-4)

Maintained by `Generate_Module_Lesson_Plan_Prompt_v2.md` (Section 0) and `Generate_Lesson_Prompt_v4.md` (Section
0.9): read every existing Band file in full before planning a new Set, appended to (never overwritten) once each
lesson is generated and approved. As of 2026-09-08, each Band file is nested `## Module N` → `### Set S` → one
row per lesson, matching Reading's and Listening/Speaking's per-Band files (see "History" below for why it
wasn't always this way).

## History: why this log used to be flat, and what changed 2026-09-08

Reading's and Listening/Speaking's Rotation Logs were always nested in Module/Band → Set blocks, because each
plans a full Set upfront with its own Module Lesson-Plan Generation Prompt before any lesson content is
generated. Academic Writing's Module Lesson-Plan prompt (`v1`, added 2026-09-08) originally planned one 8-day
lesson at a time rather than a Set, because Academic Writing's lesson was modeled as an 8-day cycle and a Writing
Set was defined as "currently 1 lesson" - so these logs stayed flat, chronological tables rather than nested
blocks.

That 8-day/1-lesson-per-Set sizing turned out to be a miscount: in practice, a Writing lesson actually taught
takes 2 days, the same as Reading and Listening/Speaking. **Corrected 2026-09-08**
(`shared/Program_Conventions.md` §C): a Writing Set is 4 lessons, like every other lesson type, with the one
remaining genuine difference being that a Writing Set's 4 lessons share **one** Scenario across the whole Set
rather than 4 independent anchor texts. The Module Lesson-Plan prompt was rewritten to `v2` to plan a full Set at
once (see that prompt's own header for why this Set-wide pass matters even though there's only one Scenario to
plan, not four), and both Band files were restructured from flat tables into the same `## Module N` → `### Set S`
nesting Reading and Listening/Speaking already use. The one existing Set in each Band (Set 1) was retrofitted
into this shape as part of the same pass, since it already existed as 4 lessons' worth of content generated
under the old 8-day document, just not yet split or logged that way - see each Band file's Set 1 entry for the
full account.

## What to check before generating a lesson

Compare the new Set's intended grammar focus, Scenario topic, and real-world writing form against at least the
last logged Set **across every Band** (by date, not just the target Band's own file), and scan further back for
a grammar focus that has recurred more than once in the last 3-4 Sets overall (see
`Generate_Lesson_Prompt_v4.md` Section 0.9's note on grammar clustering across nearby Modules, not just literal
topic repeats). This check runs once per Set, at Module Lesson-Plan time - Lessons 2-4 of an already-planned Set
never re-run it (they continue Lesson 1's own Scenario/Focus).

## Lesson version numbers (introduced 2026-09-07, corrected 2026-09-08)

Each Band file's "Format for the next entry" template has a `Version` column (`<Module>.<Set>.<Lesson>.<Version>` - see
`shared/Program_Conventions.md` §G). `<Lesson>` is each lesson's own **global** number (continuing across Sets),
not its 1-4 position within its Set - so a Set's four lessons get four different version codes (e.g. `1.1.1.0`
through `1.1.4.0`), never one shared code. This was corrected 2026-09-08 alongside the Set-size fix above; the
2026-09-07 introduction of this column had assumed a Writing Set was still 1 lesson, so Set and Lesson were the
same number - that assumption is now retired along with the 8-day model.
