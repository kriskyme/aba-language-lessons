# Academic Writing Module Lesson-Plan Generation Prompt (v4)

Companion to the Academic Writing Lesson Generation Prompt. Plans a full **Set** (Beginner: 4 lessons, one
Module) or a full **Module Pair** (Intermediate/Advanced/Proficient: two consecutive Modules' Sets, 8 lessons;
Conventions §C) in one pass. Reading and Listening/Speaking plan a Set at once to rotate across four independent
lessons; Writing plans the whole arc at once because its lessons share one Scenario in a fixed arc, and the
Scenario, genre, each Module's Focus A/B pairing, Essay Focus direction, and Mentor Ladder direction are decisions
every later lesson-generation run reads identically. Planning both Modules of a Pair together is what catches a
Focus A/B collision or a gap in Module N+1's CSV coverage before 8 lessons are written around it.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` (Sets and Module Pair, §C; Rotation Log
mechanics and adjacency rules, §F) and `shared/Generation_Quality_Standards.md` alongside it.

**Current version: v4.** History: `Changelog.md`.

## 0. Rotation Log

Mechanics: Conventions §F. This lesson type's rotated columns are Grammar Focus A/B pair and real-world writing
form; Scenario topic gets the recency flag. Two Writing-specific additions: the cross-Band check spans every
Band's `Rotation_Log_<Band>.md`, not only the Band being planned (adjacency on the Focus pair, recency flag on
Scenario and form); and the **within-pair rule**: Module N+1's Focus A/B must not repeat Module N's in the same
plan, a same-plan check stronger than adjacency. Append the approved plan's rows to that Band's file: 4 rows
under one `### Set S` subsection for Beginner; 8 rows for a Pair split across the two Modules' own `## Module N`
/ `## Module N+1` sections (creating Module N+1's heading and `### Set 1` if new), each Module's 4 rows using
its own Set and Lesson numbering, cross-referenced as Part 1 / Part 2 of the same Pair, using the Band file's
own template.

## INPUTS (fill in before running)

- **Band:** Beginner / Intermediate / Advanced / Proficient. Task Levels come from Conventions §B.
- **Beginner: Module** (e.g. "Module 1: Describing"). **Others: Module Pair** (e.g. "Modules 1-2"), always the
  fixed odd/even grouping, both Modules named.
- **Set number(s):** each named Module's next Set (default: the next integer after the highest logged for that
  Module in this Band, or 1). Set numbering restarts per Module, even inside a Pair.
- **Starting global Lesson # per Module:** default the next integer after the highest logged for that Module in
  this Band, or 1; each Module's 4 lessons take four consecutive numbers within that Module (Conventions §C/§G).
- **Objectives:** `learningobjectives.csv`, filtered to the Module(s), the band's task Levels, and the **Writing
  modality only**.
- **Rotation Log:** `Rotation_Log.md` plus every `Rotation_Log_<Band>.md`, read in full.

## TASK

1. Read the Rotation Log per Section 0: the highest global Lesson # for each named Module, this Band's most
   recently logged Set or Pair, every other Band's most recent, and any Focus pair or Scenario recurring more
   than once in the last 3-4 Sets overall.

2. Determine the band's task Levels (Conventions §B). Pull the Writing row for **Module N** and each task Level
   and quote the Description verbatim for every Level. For a Pair, also pull **Module N+1's** row per Level; it
   grounds step 3's coverage check even though the shared essay's genre stays Module N's.

3. Produce a single plan; these elements are decided once and shared across every lesson in the arc:
   - **Module(s), Set number(s), and global Lesson #s** each Module's lessons use, never shared or restarted
     mid-Pair.
   - **Lesson-position table:** Beginner's 4-row Set-position table, or the Pair's 8-row table (Pair position,
     Module, Set position, global Lesson #, content role), from the Lesson prompt's "THE MODULE PAIR" section,
     filled with this Pair's Module numbers and Lesson #s.
   - **Scenario,** one line: the shared writing situation, stimulus, and Module-aligned purpose (Lesson prompt
     0.1a). A Scenario asserts nothing as fact, so it needs no real-world-verifiability rule or fabricated-quote
     guardrail; it must be concrete and writable at every task Level in the band (from a single-word frame to a
     full essay where the band reaches that high), sustain the full arc, and be flagged per Section 0 if it
     echoes the preceding Set/Pair or another Band's most recent.
   - **Genre / real-world writing form,** from the Lesson prompt's 0.9 mapping using **Module N's row only** (the
     Levels 1-5 form and the Levels 6-8 essay type where mapped); for a Pair, state that Module N+1 inherits it
     unchanged. Checked per Section 0.
   - **Grammar Focus A/B pairing for Module N,** per the Lesson prompt's 0.4 bank and row-selection rule: anchored
     at the band's own **native** Paragraph Composition row, not automatically its lowest. Name the row and why.
     Checked per Section 0.
   - **Grammar Focus A/B pairing for Module N+1 (Pair only),** genuinely different in content from Module N's
     (Section 0's within-pair rule), from the bank's Alternate column once authored or hand-selected for Module
     N+1's own purpose. Name the row and confirm no collision.
   - **Essay Focus A/B direction (Advanced, Proficient only),** anchored at Level 6's row (Lesson prompt 0.4c),
     taught once via Module N (Module N+1 may add a distinct cohesion extension, not a re-teach), and the essay
     type from Module N's mapping, or the extended-paragraph fallback where none is mapped.
   - **CSV-objective-coverage check (Pair only):** state concretely what Lesson 8's separate Closing Transfer
     Check task will ask students to do to exercise Module N+1's own verb (Lesson prompt 0.8), calibrated to the
     Scenario's subject matter where reasonable, so the Lesson prompt is not left to invent it.
   - **Leveled Mentor Ladder direction,** one line per task Level: what that Level's Mentor Text or Essay will
     model on this Scenario (Lesson prompt 0.1b), a direction, not the model itself; for a Pair, one more line per
     Level on what Lesson 5's second look will ask students to notice.
   - **Task-Level basis:** for every task Level, the exact Writing CSV Description (Level N, Module N) the Mentor
     Ladder and drafting task satisfy, mapped explicitly.

4. After the plan, report a short self-check: every task Level with its own quoted Writing row, exactly the
   band's Level count; the Scenario writable at every Level and sustaining the full arc; Focus A/B anchored at
   the native Paragraph Composition row and Essay Focus at Level 6's row; (Pair) Module N+1's Focus genuinely
   distinct, the genre inherited unchanged, and a concrete separate Module N+1 verb task named; the Focus pair
   and writing form not repeating the preceding Set/Pair, cross-Band echoes flagged; each Module's Lesson #s
   continuing its own numbering; the position table complete and correct; the Mentor Ladder direction distinct in
   kind across a regime boundary, not just in wording.

5. Write no Mentor Text, Mentor Essay, grammar table, drafting task, checklist, or Peer Editing Form in this
   step. If asked to generate lesson content in the same turn, stop and confirm the plan is approved first.

## OUTPUT

The plan (shared fields plus the position table), then the self-check paragraph. Save a Beginner plan as
`lessons/<band>/Module_<N>/Module<N>_<Band>_Lesson_Plan.md`; a Pair plan as
`lessons/<band>/ModulePair_<N>-<N+1>/ModulePair_<N>-<N+1>_<Band>_Lesson_Plan.md`. Once approved, also the Rotation
Log rows per Section 0, ready to append. Nothing else.
