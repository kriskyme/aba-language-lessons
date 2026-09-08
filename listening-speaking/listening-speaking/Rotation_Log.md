# Listening/Speaking Rotation Log

Overview only, as of the 2026-09-06 per-Band split (see `CLAUDE.md`'s "Rotation Log splits by Band" convention
and `shared/Program_Conventions.md` §F for the general mechanics). Each Band that has generated content gets its
own `Rotation_Log_<Band>.md`, holding that Band's Set/lesson tables and per-lesson notes, nested by Set, plus
its own append-template at the bottom. **A new Band's file is created lazily** the first time a lesson in that
Band is generated, mirroring how `Set_<N>/` folders are created lazily - see `shared/Program_Conventions.md` §D.

**Current files:**
- [`Rotation_Log_Intermediate.md`](Rotation_Log_Intermediate.md) - Module 1: Describing, Set 1 (generated), Set 2 (planned only)
- [`Rotation_Log_Advanced.md`](Rotation_Log_Advanced.md) - Module 1: Describing, Set 1 (complete, 4 of 4 lessons generated, assessment generated), Set 2 (planned only)
- [`Rotation_Log_Proficient.md`](Rotation_Log_Proficient.md) - Module 1: Describing, Set 1 (planned 2026-09-07; Lesson 1 of 4 generated) - first Set ever planned for this Band
- [`Rotation_Log_Beginner.md`](Rotation_Log_Beginner.md) - Module 1: Describing, Set 1 (planned 2026-09-07, Lesson 1 generated, Lessons 2-4 planned only) - first Set ever planned for this Band

**Read the relevant Band's file in full before planning a new Set** (per the Module Lesson-Plan Generation
Prompt's Section 0); append to it (never overwritten) once a Set's plan is reviewed and approved.

## Notes that apply across every Band (not duplicated into any one Band's file)

**Day-count correction, applied program-wide (2026-09-03):** the Lesson Generation Prompt's Unit Architecture
was corrected from an 8-day cycle (Unit A across Days 1-4, Unit B across Days 5-8, 600 minutes per lesson) to
the real 2-day cycle (Day 1 = Unit A, Day 2 = Unit B, 75 minutes each, 150 minutes per lesson) - see that
prompt's fifth addendum. Practical effect: one module's 8-day real budget is 4 lessons at 2 days each, not 8
lessons at 8 days each. All four Intermediate Module 1 lessons already generated (Lessons 1-4: New Bakery,
Porto Food Tour, How to Choose a Backpack, Great-Grandmother Learns English) were retroactively rewritten into
the corrected Day 1/Day 2 structure - no task, vocabulary item, quote, or differentiated activity was cut in
any of them, only reorganized into two real class periods instead of eight, per each file's own restructure
note and updated self-check. The Module 1 Intermediate Lesson Plan's day-count note was corrected to match.
Advanced Module 1 Lessons 1-2 received the same restructure treatment on 2026-09-04 (see
`Rotation_Log_Advanced.md`), completing the day-count correction across every lesson generated so far in this
family.

**Reserve bank decision (resolved; terminology superseded by the Sets note below - kept as "reserve bank" here
since that's what it was called at the time):** rows 5-8 of the Intermediate plan's table stay in as what is now
called Set 2, for when Module 1 is retaught with fresh material, rather than being trimmed - Lessons 1-4 (Set 1)
already fill the module's real 8-day allocation on their own.

**Second review pass (2026-09-03), Intermediate Lessons 1-2 checked against the fully updated prompts:**
comparing Lessons 1-2 against the current Lesson Generation Prompt and Student Print Formatting Prompt (both had
accumulated fixes since these two lessons were first built) found two things. (1) Lesson 1's original day-count
retrofit had silently dropped two items - Level 2's "why do people keep coming back to Seylou" fact-check and
Level 5's evaluative-language item about Bethony's closing quote - both restored. Lesson 2 came through its
retrofit with content intact. (2) Neither lesson's item counts had ever been rebalanced per the fourth addendum
(which postdates both lessons' original builds); both are now calibrated the same way Lessons 3-4 already are.
Both lessons' `.html` packets were rebuilt from scratch to match every Student Print Formatting Prompt
convention established during Lesson 3's review cycle (Good to Know at the top, citebox at the point of watching
with no "ask your teacher" line, compact inline multiple-choice, real picture placeholders, word banks
positioned right before their items, no redundant "(Choose Your Task)" label, Learn the Phrase frames inside the
spotlight box, and the upside-down treatment for each lesson's Closing Transfer Check script) - unlike the
day-count restructure, these two packets genuinely had not been touched since their original 2026-09-01/09-02
builds and needed the full update, not just a check. This is the same review-and-rebuild pattern later applied
to Advanced Lessons 1-2 on 2026-09-04.

**Sets concept introduced (2026-09-03).** A Module/Band can now hold more than one rotation of lessons over
time - a fresh batch of topics for a semester where the module is retaught, without discarding what was taught
before. See `shared/Program_Conventions.md` §C for the full definition and the global lesson-numbering-across-Sets
rule. This log's existing 8-row tables for both Module 1 sections (now in the two Band files) were retroactively
split into Set 1 (Lessons 1-4) and Set 2 (Lessons 5-8) subsections to match - see the Module Lesson-Plan
Generation Prompt's Sets note for the full rule, including how cross-Set adjacency works. A Set is not tied to a
semester in the plan itself; note an actual teaching term against a Set only once it's been assigned to one.

**Assessment Generation Prompt introduced (2026-09-04).** A new prompt in this family
(`Generate_Assessment_Prompt_v1.md`) generates a per-Set Listening assessment (Part A, new unseen source,
task-Level tiered) and a per-Set Speaking assessment (Part B, mechanism split by band: Teams recording as the
default and formal assessment for Beginner/Intermediate, with a same-task teacher-approved live-delivery option;
live presentation as the default for Advanced/Proficient, with a same-task Teams-recording alternate always also
generated). First assessment generated 2026-09-04 against Module 1 Intermediate Set 1 - see
`lessons/intermediate/Module_1/Set_1/Set1_Intermediate_Assessment.md`. Advanced Set 1 was completed 2026-09-07, and its
assessment was generated 2026-09-07 too (see `Rotation_Log_Advanced.md`) - see
`lessons/advanced/Module_1/Set_1/Set1_Advanced_Assessment.md`. Both Set 1 assessments are now generated; neither has
been field-tested with a real class yet.

**Lesson version numbers introduced (2026-09-07).** Each Band file's lesson table now has a `Version` column
(`<Module>.<Set>.<Lesson>.<Version>` - see `shared/Program_Conventions.md` §G) in its "Format for the next Set's
entry" template. This is going-forward only: Set 1 in both Bands above predates it and is not retrofitted with
a version.

**Intermediate Set 1 assessment regenerated (2026-09-06), replacing the corrupted stub.** Part A (Listening)
uses a real, verified source, "Visitors Laugh Away Troubles at the HaHaHouse Museum" (VOA Learning English,
Andrea Golubic's laughter museum in Zagreb, Croatia), distinct from all 4 taught sources, with tiered items
covering all four of the Set's listening strategies (Main Ideas/Gist, Recognize Examples, Sequence Markers,
Predict from Context). Part B (Speaking) is a Teams Speaking Progress solo recording (Intermediate's default
mechanism), emphasizing Making Comparisons and Sequencing Language, with the same-task live-delivery option
noted. See `lessons/intermediate/Module_1/Set_1/Set1_Intermediate_Assessment.md`.

**Intermediate Set 1 assessment's Part A fully regenerated again (2026-09-07),** against
`Generate_Assessment_Prompt_v1.md`'s redesigned Part A: a second real clip added ("Researchers Uncover a
Bathhouse Complex in Ancient Pompeii," VOA Learning English), vocabulary folded into the graded items instead of
a pre-teach list, the notes-taking organizer dropped, and every item rewritten as multiple choice/fill-in-the-
blank/matching. HaHaHouse stays Clip 1; Part B (Speaking) unchanged. See `Changelog.md` for the full reasoning
and `Index.md` for current file status.
