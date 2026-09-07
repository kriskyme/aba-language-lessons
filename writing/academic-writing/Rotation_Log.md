# Academic Writing Rotation Log

Overview only, as of the 2026-09-06 per-Band split (Writing's first - see `CLAUDE.md`'s "Rotation Log splits by
Band" convention and `shared/Program_Conventions.md` §F for the general mechanics). Each Band that has a
generated lesson gets its own `Rotation_Log_<Band>.md`. **A new Band's file is created lazily** the first time a
lesson in that Band is generated, mirroring how `Set_<N>/` folders are created lazily - see
`shared/Program_Conventions.md` §D.

**Current files:**
- [`Rotation_Log_Intermediate.md`](Rotation_Log_Intermediate.md) - Intermediate 1 ("my phone case")
- [`Rotation_Log_Advanced.md`](Rotation_Log_Advanced.md) - Advanced 1 ("Two apartments... for Sam")

Maintained by `Generate_Lesson_Prompt_v3.5.md` (Section 0.9): read every existing Band file in full before
generating a new lesson, appended to (never overwritten) once a lesson is generated and approved. Each Band
file is still a flat, chronological table, not nested by Module/Band → Set the way Reading's and
Listening/Speaking's per-Band files are (see "why this differs from Reading's log" below).

## Why this exists, and how it differs from Reading's log

Reading's and Listening/Speaking's Rotation Logs are both organized in nested Module/Band → Set blocks because
each plans a full Set upfront with its own Module Lesson-Plan Generation Prompt before any lesson content is
generated. No Writing equivalent of that planning prompt exists yet (see the companion `Index.md`'s Pending work
and "Sets (aspirational)" sections), so lessons are currently generated one at a time against a bare Module/Band
request, and each Band's log is a flat, chronological table rather than nested blocks. If an Academic Writing
Module Lesson-Plan prompt is built later, these logs' format should likely be restructured to nest by Module and
Set at that point, the same way their content should carry forward - noting that, since a Writing lesson is
already an 8-day cycle, a Writing Set would currently be just 1 lesson (see `Index.md`), so the practical effect
on this shape may be smaller than Reading/Listening-Speaking's restructuring was.

## What to check before generating a lesson

Compare the new lesson's intended grammar focus, Scenario topic, and real-world writing form against at least
the last logged row **across every Band** (by date, not just the target Band's own file), and scan further back
for a grammar focus that has recurred more than once in the last 3-4 rows overall (see Section 0.9's note on
grammar clustering across nearby Modules, not just literal topic repeats).

## Two numbering columns (added 2026-09-03)

`#` is the lesson's position in the whole program's generation order, across every Band (matches how rows were
already numbered before the per-Band split). `Band Lesson #` is that same lesson's position within its own Band
only, so it answers "how many Advanced lessons exist" or "what's the next Intermediate lesson number" without
recounting rows across every Band file by hand. A Band's count restarts at 1 the first time a lesson is
generated in that Band; regenerating an existing lesson in place (a new version of the same
Scenario/Module/Band) does not advance either number, since it is still the same lesson, not a new one.

## Lesson version numbers introduced (2026-09-07)

Each Band file's "Format for the next entry" template now has a `Version` column
(`S<Set>.<Lesson>.<Iteration>` - see `shared/Program_Conventions.md` §G). Since a Writing Set is currently 1
lesson (`Index.md`'s "Sets (aspirational)" section), both the Set and Lesson segments are that entry's own
`Band Lesson #`. Going-forward only: the two rows already logged (Intermediate 1, Advanced 1) predate this and
are not retrofitted.
