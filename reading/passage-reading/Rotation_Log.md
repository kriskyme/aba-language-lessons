# Passage Reading Rotation Log

Overview only, as of the 2026-09-06 per-Band split (see `CLAUDE.md`'s "Rotation Log splits by Band" convention
and `shared/Program_Conventions.md` §F for the general mechanics). Each Band that has generated content gets its
own `Rotation_Log_<Band>.md`, holding that Band's Set/lesson tables, nested by Set, plus its own
append-template at the bottom. **A new Band's file is created lazily** the first time a lesson in that Band is
generated, mirroring how `Set_<N>/` folders are created lazily - see `shared/Program_Conventions.md` §D.

**Current files:**
- [`Rotation_Log_Beginner.md`](Rotation_Log_Beginner.md) - Module 1: Describing, Set 1 (complete)
- [`Rotation_Log_Intermediate.md`](Rotation_Log_Intermediate.md) - Module 1: Describing, Set 1 (complete)
- [`Rotation_Log_Advanced.md`](Rotation_Log_Advanced.md) - Module 1: Describing, Set 1 (complete)
- [`Rotation_Log_Proficient.md`](Rotation_Log_Proficient.md) - Module 1: Describing, Set 1 (complete)

**Read the relevant Band's file in full before planning a new Set** (per the Module Lesson-Plan Generation
Prompt's Section 0); append to it (never overwritten) once a Set's plan is reviewed and approved.

## Notes that apply across every Band (not duplicated into any one Band's file)

**Correction, 2026-09-01:** a Set is however many lessons together cover a module's 8 instructional days (4 x
2-day cycles); with Passage Reading's 2-day lesson, that's 4 lessons, not 8 (which would be 16 days) - a miscount
from early on, when "8 days worth of lessons" was read as "8 lessons" rather than "4 lessons of 2 days each."
The Module 1, Describing, Intermediate Band entry (now in `Rotation_Log_Intermediate.md`) originally listed 8
rows; rows 5-8 (Lesson 5: an apartment renovation in Bushwick, Brooklyn; Lesson 6: a hiker's journal entry at
Angel's Landing, Zion National Park; Lesson 7: a food truck in a Portland food cart pod; Lesson 8: a
bicycle-repair workshop in Amsterdam) were planned but never generated as lesson content, and were removed as
out of scope under the corrected 4-lesson model. Unlike Listening/Speaking, where the equivalent leftover rows
became that Module/Band's Set 2, Reading's rows 5-8 are simply dropped, since no Set 2 has been planned for
either Band below - Lessons 1-4, already generated, are each Band's complete Set 1, not half of an 8-lesson
module. See `Index.md` for current status.

**Sets concept introduced (2026-09-06), for parity with Listening/Speaking.** A Module/Band can hold more than
one Set over time - a fresh rotation of lessons for a semester where the module is retaught, without discarding
or conflating it with what was taught before. See `shared/Program_Conventions.md` §C for the full definition and
the global lesson-numbering-across-Sets rule. This log's two Band sections (now split into separate files) were
relabeled `### Set 1` under their Module headings to match - no row data changed, only the heading structure.

Modules are appended within each Band's file in the order they were planned. When planning the next Set, read
the LAST lesson row of the most recently logged Set in that Band's file for the adjacency checks, and the full
set of vocabulary themes and topics in that file for the recency flag.

**Lesson version numbers introduced (2026-09-07).** Each Band file's lesson table now has a `Version` column
(`<Module>.<Set>.<Lesson>.<Version>` - see `shared/Program_Conventions.md` §G) in its "Format for the next Set's
entry" template. This is going-forward only: Set 1 in both Bands above predates it and is not retrofitted with
a version.
