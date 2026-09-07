# Program Conventions (v1.2)

Shared, cross-modality reference for facts that are true of the whole program, not any one lesson
type: the Level/Band taxonomy, the Task-Levels-by-Band table, what a Set is, the Set/Lesson folder
shape, the CBI/TBLT pedagogical framework, and Rotation Log mechanics. Each lesson type's own
`Index.md`, `Changelog.md`, and prompts should not carry a copy of this content — point here
(paste this file alongside the lesson-type prompt when generating) and add only what's genuinely
specific to that lesson type.

This exists because, before it did, these facts were independently restated (and drifting slightly
in wording) across `CLAUDE.md` and all three lesson types' docs and prompts — most visibly the
Task-Levels-by-Band table, which every lesson-generation prompt already admitted in prose it was
"reusing wholesale" from Reading rather than deriving independently. See `Changelog.md` for what
changed when this file was extracted.

## A. Shared skill taxonomy

All three modalities key off the same skill taxonomy defined in `learningobjectives.csv`: **8
Levels × 8 Modules** (Module 1: Describing … Module 8: Socializing), banded into
Beginner / Intermediate / Advanced / Proficient:

| Band | Levels | CEFR |
|---|---|---|
| Beginner | 1-2 | A1-A2 |
| Intermediate | 3-4 | B1-B1+ |
| Advanced | 5-6 | B2-B2+ |
| Proficient | 7-8 | C1-C2 |

A lesson's anchor text/source/scenario is calibrated to the band's **lower** Level (Level 3 for
Intermediate, Level 5 for Advanced, Level 1 for Beginner, Level 7 for Proficient). Every student in
the room engages with the same band-calibrated centerpiece; only the task built on top of it
differs by task Level (see §B).

## B. Task Levels by Band

Each band has a fixed set of task Levels — one differentiated task per Level:

| Band | Task Levels | Count |
|---|---|---|
| Beginner | 1, 2, 3 | 3 |
| Intermediate | 2, 3, 4, 5 | 4 |
| Advanced | 4, 5, 6, 7 | 4 |
| Proficient | 5, 6, 7, 8 | 4 |

How this table is built: a band's own two Levels always get a task (its "native" Levels). Where a
neighboring band has a Level to lend, the set extends one Level below and one Level above those
native Levels, with two deliberate exceptions:

- **Beginner does not extend below** (Level 1 is the floor of the whole scale) and extends only
  one Level above, to Level 3 — producing 3 task Levels instead of 4.
- **Proficient does not extend above** (Level 8 is the ceiling of the whole scale), so instead of
  stopping at 3 task Levels the way Beginner does, it extends two Levels below instead of one,
  borrowing both of the Advanced band's Levels (5 and 6) to keep 4 task Levels.

This asymmetry is deliberate, not an oversight: pushing a Beginner-band student's task up into
Intermediate-scoped material is a real stretch risk for a still-developing learner, so that reach
is capped at one Level. Pushing an Advanced-band student's task up into Proficient-scoped material
is a much smaller risk — a step into "harder," not a foundational-literacy stretch — so Proficient
is allowed to borrow both of Advanced's Levels rather than just one.

**Band-distance invariant:** every task Level in the table above is at most one band away from the
centerpiece's own calibrated band. No task is ever built two bands away from what the class is
actually working from. This is what makes it safe to share one anchor text/source/scenario across
every task Level in a lesson: the widest gap any student faces is one band's worth of difficulty
between their assigned task and the shared centerpiece, never two.

Reading's task differentiates *depth of engagement with a shared text*; Writing's task Level
instead changes the *shape of the required output* (a spelled word in a frame at Level 1-3 versus
an independently authored multi-paragraph piece at Level 7-8) — the table and its underlying
band-distance logic are identical, but each lesson type's own prompt documents what a "task" means
concretely for that modality.

**Star ratings on the student-facing packet.** Every lesson type's `Generate_Student_Packet_Prompt_*.md`
hides the numeric task Level from students and shows a star rating instead: the lowest task Level in
the band's row above gets ★, and each step up that row adds one star, up to ★★★★ for the row's
highest task Level. Because each band's row has a different mix of native/borrowed Levels, the same
star count lands on a different band-relative position per band:

| Band | ★ | ★★ | ★★★ | ★★★★ |
|---|---|---|---|---|
| Beginner | native lower (1) | native upper (2) | 1 band above (3) | *(none — only 3 stars)* |
| Intermediate | 1 band below (2) | native lower (3) | native upper (4) | 1 band above (5) |
| Advanced | 1 band below (4) | native lower (5) | native upper (6) | 1 band above (7) |
| Proficient | 1 band below (5) | 1 band below (6) | native lower (7) | native upper (8) |

Don't over-generalize "★★/★★★ = the band's own two native Levels, ★ = one band below, ★★★★ = one
band above" from the Intermediate/Advanced rows to all four bands — it breaks at both ends of the
scale. Beginner has no ★★★★ at all (only 3 stars, since it can't extend below Level 1, per the
asymmetry above). Proficient's ★ *and* ★★ are both "1 band below" (it borrows two Levels down from
Advanced instead of one, since it can't extend above Level 8), so its native Levels are ★★★/★★★★,
not ★★/★★★.

## C. What a Set is

A **Set** is however many lessons together cover one Module's planned instructional time (8 class
days) for a Band — not a fixed lesson count, but derived from how many days each lesson type's
lesson runs. Reading and Listening/Speaking both use a 2-day lesson, so a Set is 4 lessons for each
of them today; a shorter or longer lesson would change that count, since the invariant is the 8
days, not the number "4." Academic Writing's lesson is already a full 8-day cycle on its own, so a
Writing Set is currently **1 lesson** — Writing has no Module Lesson-Plan prompt yet to drive
Set-aware planning (see that lesson type's own `Index.md`), but the same definition applies.

A Module/Band can hold more than one Set over time — a fresh rotation of lessons for a semester
where the module is retaught, without discarding or conflating it with what was taught before.
**Lesson numbering is global within a Module/Band, continuing across Sets rather than restarting:**
Set 1 is Lessons 1-4, Set 2 (if planned) is Lessons 5-8, Set 3 is Lessons 9-12, and so on — so
"Lesson 7" unambiguously means Set 2's third lesson without needing to also state which Set. When
planning a new Set, numbering starts at the next integer after the highest lesson number already
planned for that Module/Band, across every Set. A Set is not tied to a semester in the plan itself;
note an actual teaching term against a Set only once it's been assigned to one, as a light
annotation, not a planning input.

For the history of how this figure was originally miscounted as 8 lessons/16 days per module and
corrected, see `CLAUDE.md`'s Sets bullet or Reading's `Changelog.md` (2026-09-01 entry) — not
restated here.

## D. Set/Lesson folder-nesting convention

A lesson's files (raw `.md`, student packet `.html`, later homework) travel together:
`lessons/<band>/Set_<N>/Lesson_<N>_<Slug>/` holds one lesson's files. A Set's own assessment (one
per Set, not per lesson) sits in `Set_<N>/` itself rather than inside any one lesson's folder. The
Module/Band Lesson Plan spans every Set generated for that band so far, and sits at the band-folder
root (`lessons/<band>/`), above the `Set_<N>/` folders:

```
lessons/<band>/
├── Module{N}_{Band}_Lesson_Plan.md
└── Set_{N}/
    ├── Set{N}_{Band}_Assessment.md
    └── Lesson_{n}_{Slug}/{lesson .md, packet .html}
```

This nesting is kept even at one lesson per Set (Academic Writing's current case), so no
special-casing is needed later if a shorter lesson cycle ever makes room for more than one lesson
per Set.

## E. Pedagogical framework (CBI/TBLT)

Adopt a Content-Based Instruction (CBI) and Task-Based Language Teaching (TBLT) framework: treat
the lesson's centerpiece (text, source, or scenario) as a tool to explore real-world ideas and
build critical thinking, letting language acquisition happen through meaningful communication
rather than isolated drills. Each lesson type's own prompt keeps its own one-clause adaptation of
this framing (what the "content" concretely is for that modality) rather than restating the
principle itself.

## F. Rotation Log purpose and mechanics

A **Rotation Log** is a single running record, separate from any one lesson's or Set's plan, of
what every already-generated lesson actually used (genre/format, strategy, hook, protocol,
vocabulary or grammar focus, topic) — one row per lesson. It is the only thing that lets a new
lesson or Set avoid repeating what came immediately before it; without it, each generation run only
ever sees its own lesson(s) and cross-Set/cross-Module repetition is invisible until a teacher
notices it in the classroom. Read it in full before planning or generating; append to it (never
overwrite) once a lesson or Set is approved.

A lesson type nests its Rotation Log by Set within Module/Band once it has a Module Lesson-Plan
prompt driving Set-aware planning (Reading, Listening/Speaking); one generated one at a time
against a bare Module/Band request instead stays a flat chronological table (Academic Writing,
today). As of the per-Band split (see each lesson type's own `Rotation_Log.md`), a lesson type's
"Rotation Log" is an overview file plus one file per Band that has entries — see that overview for
the current file list and the rule for when a new Band's file gets created.

## G. Lesson version numbers

Every individual Lesson document and its student packet carries a version code,
`S<Set>.<Lesson>.<Iteration>`, distinct from the "vX.Y" numbers used elsewhere in this repo (those
version the *generation prompt files* themselves, e.g. `Generate_Lesson_Prompt_v2.7.md`, tracked in
each lesson type's own `Changelog.md` - a separate axis from an individual lesson's own content
version).

- `<Set>` is the Set the lesson belongs to (see §C).
- `<Lesson>` is that lesson's **global** lesson number (§C's continuing numbering across Sets - Set
  2's first lesson is Lesson 5, not Lesson 1), not its position within the Set. This keeps the
  version consistent with the one lesson-numbering scheme the program already uses everywhere else.
- `<Iteration>` starts at `0` when a lesson is first generated and saved, and increments by 1 each
  time that specific lesson's content is substantively revised afterward (e.g. after it's been
  taught and a revision pass changes it) - tracked **per lesson**, not per Set, so two lessons in
  the same Set can sit at different iterations if only one of them was revised.

Example: Set 1's four lessons start at `S1.1.0`, `S1.2.0`, `S1.3.0`, `S1.4.0`; if Lesson 2 is later
revised after being taught, it becomes `S1.2.1` while its Set-mates stay at their original iteration.

Applies to individual Lesson docs/packets only - not Module Lesson-Plans or Assessments. A lesson
type's own Rotation Log (§F) is the source of truth for a lesson's current version (see each
`Rotation_Log_<Band>.md`'s lesson table); the Markdown lesson doc and its HTML student packet each
restate it (see `Student_Packet_Style_Guide.md` §B for the packet masthead's version line).

This is a going-forward convention: a Set planned before this section existed doesn't get a version
retrofitted onto it, and its Rotation Log table is not restructured to add one.

## Changelog

See `Changelog.md` in this folder.
