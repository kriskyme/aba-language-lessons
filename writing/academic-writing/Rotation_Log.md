# Academic Writing Rotation Log

Overview only, as of the 2026-09-06 per-Band split (Writing's first - see `CLAUDE.md`'s "Rotation Log splits by
Band" convention and `shared/Program_Conventions.md` §F for the general mechanics). Each Band that has a
generated Set gets its own `Rotation_Log_<Band>.md`. **A new Band's file is created lazily** the first time a
Set in that Band is generated, mirroring how `Set_<N>/` folders are created lazily - see
`shared/Program_Conventions.md` §D.

**Current files:**
- [`Rotation_Log_Intermediate.md`](Rotation_Log_Intermediate.md) - Module 1, Set 1 ("my phone case" then "my clothing", Lessons 1-4) and Module 2, Set 1 (the same clothing, Lessons 1-4 at `2.1.x.0`): the complete Module Pair 1-2, planned by `lessons/intermediate/ModulePair_1-2/ModulePair_1-2_Intermediate_Lesson_Plan.md`
- [`Rotation_Log_Advanced.md`](Rotation_Log_Advanced.md) - Module 1, Set 1 ("Two Places to Study", Lessons 1-4; Part 1 of Module Pair 1-2, Module 2 pending)

Maintained by `Generate_Module_Lesson_Plan_Prompt_v4.5.md` (Section 0) and `Generate_Lesson_Prompt_v6.13.md` (Section
0.9): read every existing Band file in full before planning a new Set or Module Pair, appended to (never
overwritten) once each lesson is generated and approved. As of 2026-09-08, each Band file is nested `## Module N`
→ `### Set S` → one row per lesson, matching Reading's and Listening/Speaking's per-Band files (see "History"
below for why it wasn't always this way). For Intermediate/Advanced/Proficient, a Module Pair's 8 lessons split
across the pair's two Modules' own `## Module N` / `## Module N+1` sections in the same Band file, cross-referenced
as Part 1/Part 2 of the same Pair - see "Module Pair non-repetition" below.

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

Compare the new Set's/Pair's intended grammar focus, Scenario topic, and real-world writing form against at least
the last logged Set/Pair **across every Band** (by date, not just the target Band's own file), and scan further
back for a grammar focus that has recurred more than once in the last 3-4 Sets/Pairs overall (see
`Generate_Lesson_Prompt_v6.13.md` Section 0.9's note on grammar clustering across nearby Modules, not just literal
topic repeats). This check runs once per Set/Pair, at Module Lesson-Plan time - later positions within an
already-planned Set/Pair never re-run it (they continue the arc's own Scenario/Focus).

## Module Pair non-repetition (Intermediate/Advanced/Proficient only, new 2026-09-08)

Within one Module Pair, Module N+1's own Grammar/Essay Focus A/B must not repeat Module N's own Focus A/B chosen
earlier in the same plan - a same-plan check, stronger than the cross-Set/cross-Band adjacency check above, since
both choices are decided together in one `Generate_Module_Lesson_Plan_Prompt_v4.5.md` pass. See
`Generate_Lesson_Prompt_v6.13.md` Section 0.9 and `shared/Program_Conventions.md` §C's Module Pair addendum.

## Lesson version numbers (introduced 2026-09-07, corrected 2026-09-08)

Each Band file's "Format for the next entry" template has a `Version` column (`<Module>.<Set>.<Lesson>.<Version>` - see
`shared/Program_Conventions.md` §G). `<Lesson>` is each lesson's own **global** number (continuing across Sets),
not its 1-4 position within its Set - so a Set's four lessons get four different version codes (e.g. `1.1.1.0`
through `1.1.4.0`), never one shared code. This was corrected 2026-09-08 alongside the Set-size fix above; the
2026-09-07 introduction of this column had assumed a Writing Set was still 1 lesson, so Set and Lesson were the
same number - that assumption is now retired along with the 8-day model.
