# Program Conventions (v1.10)

Shared, cross-modality reference for facts that are true of the whole program, not any one lesson
type: the Level/Band taxonomy, the Task-Levels-by-Band table, what a Set is, the Set/Lesson folder
shape, the CBI/TBLT pedagogical framework, and Rotation Log mechanics. Each lesson type's own
`Index.md`, `Changelog.md`, and prompts should not carry a copy of this content - point here
(paste this file alongside the lesson-type prompt when generating) and add only what's genuinely
specific to that lesson type.

This exists because, before it did, these facts were independently restated (and drifting slightly
in wording) across `CLAUDE.md` and all three lesson types' docs and prompts - most visibly the
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

Each band has a fixed set of task Levels - one differentiated task per Level:

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
  one Level above, to Level 3 - producing 3 task Levels instead of 4.
- **Proficient does not extend above** (Level 8 is the ceiling of the whole scale), so instead of
  stopping at 3 task Levels the way Beginner does, it extends two Levels below instead of one,
  borrowing both of the Advanced band's Levels (5 and 6) to keep 4 task Levels.

This asymmetry is deliberate, not an oversight: pushing a Beginner-band student's task up into
Intermediate-scoped material is a real stretch risk for a still-developing learner, so that reach
is capped at one Level. Pushing an Advanced-band student's task up into Proficient-scoped material
is a much smaller risk - a step into "harder," not a foundational-literacy stretch - so Proficient
is allowed to borrow both of Advanced's Levels rather than just one.

**Band-distance invariant:** every task Level in the table above is at most one band away from the
centerpiece's own calibrated band. No task is ever built two bands away from what the class is
actually working from. This is what makes it safe to share one anchor text/source/scenario across
every task Level in a lesson: the widest gap any student faces is one band's worth of difficulty
between their assigned task and the shared centerpiece, never two.

Reading's task differentiates *depth of engagement with a shared text*; Writing's task Level
instead changes the *shape of the required output* (a spelled word in a frame at Level 1-3 versus
an independently authored multi-paragraph piece at Level 7-8) - the table and its underlying
band-distance logic are identical, but each lesson type's own prompt documents what a "task" means
concretely for that modality.

**Star ratings on the student-facing packet.** Every lesson type's `Generate_Student_Packet_Prompt_*.md`
hides the numeric task Level from students and shows a star rating instead: the lowest task Level in
the band's row above gets ★, and each step up that row adds one star, up to ★★★★ for the row's
highest task Level. Because each band's row has a different mix of native/borrowed Levels, the same
star count lands on a different band-relative position per band:

| Band | ★ | ★★ | ★★★ | ★★★★ |
|---|---|---|---|---|
| Beginner | native lower (1) | native upper (2) | 1 band above (3) | *(none - only 3 stars)* |
| Intermediate | 1 band below (2) | native lower (3) | native upper (4) | 1 band above (5) |
| Advanced | 1 band below (4) | native lower (5) | native upper (6) | 1 band above (7) |
| Proficient | 1 band below (5) | 1 band below (6) | native lower (7) | native upper (8) |

Don't over-generalize "★★/★★★ = the band's own two native Levels, ★ = one band below, ★★★★ = one
band above" from the Intermediate/Advanced rows to all four bands - it breaks at both ends of the
scale. Beginner has no ★★★★ at all (only 3 stars, since it can't extend below Level 1, per the
asymmetry above). Proficient's ★ *and* ★★ are both "1 band below" (it borrows two Levels down from
Advanced instead of one, since it can't extend above Level 8), so its native Levels are ★★★/★★★★,
not ★★/★★★.

## C. What a Set is

A **Set** is however many lessons together cover one Module's planned instructional time (8 class
days) for a Band - not a fixed lesson count, but derived from how many days each lesson type's
lesson runs. Reading, Listening/Speaking, and Academic Writing all use a 2-day lesson, so a Set is
4 lessons for each of them; a shorter or longer lesson would change that count, since the invariant
is the 8 days, not the number "4."

**Corrected 2026-09-08 (Academic Writing):** Academic Writing's lesson was originally modeled as a
single 8-day cycle, making a Writing Set "1 lesson" - the same kind of sizing miscount the whole
program's Set concept itself was corrected from once before (see the note below this section). In
practice, each lesson actually taught took 2 days, the same as Reading and Listening/Speaking; the
8-day span was really 4 separate lessons back to back, not one long one. A Writing Set is now 4
lessons, like every other lesson type. The one genuine, permanent difference from Reading/
Listening-Speaking that survives this correction: a Writing Set's 4 lessons share **one** Scenario
carried across the whole Set (grammar input in Lessons 1-2, drafting in Lesson 3, revision and
publishing in Lesson 4 - one piece of writing taken from introduction to finished, published
product), rather than each lesson getting its own independent anchor text the way a Reading Set's 4
lessons do. A Scenario is one writing situation and Module-aligned purpose built on **two** of the
student's own belongings (Quality Standards §D8): a **practice object**, which carries grammar input,
controlled practice, the frame rounds, and the Mentor Ladder from Lesson 1 through Lesson 2 Day 1,
and a **draft object**, introduced at Lesson 2 Day 2's prewriting and the only object every later
position writes about (Lesson 3's draft, Lesson 4's revision, and for a Module Pair the whole second
Module). The draft is the student's first transfer of the taught grammar to something they did not
drill on; the ladder stays on the practice object because it models form, not content. See `writing/academic-writing/Index.md`'s "Sets" section for how this plays out in that
lesson type's own prompt family.

**Module Pair (added 2026-09-08, Academic Writing only):** for the Intermediate, Advanced, and
Proficient bands, Academic Writing further pairs two consecutive Modules - odd with the next even
(1-2, 3-4, 5-6, 7-8) - so that one Scenario/essay, on the draft object, spans both Modules' Sets (8 lessons total, not 4),
with each Module teaching its own Grammar/Essay Focus and contributing it to the same shared piece
rather than each Module producing an independent essay. The piece is **built in parts**: each Module
drafts only the part its own form fits, and neither Module drafts a complete piece. Essay Levels (6-8):
the first Module plans a working thesis and drafts the body paragraphs; the second Module drafts the
introduction (a hook in its own form, connecting sentences, the thesis in place) and the conclusion.
Paragraph Levels (4-5): one paragraph per Module, in that Module's form, on the same subject, so the
finished piece is two paragraphs. The second Module's last lesson assembles the whole, peer-edits,
revises for effect, and publishes it. Beginner is exempt and keeps the
single-Module model described above (its task Levels are single-word Guided Frame Composition, which
the draft-carrying/revision-focus model doesn't fit). This does not change what a Set is, and does
not merge or restart Set numbering across the two Modules paired together - each Module still keeps
its own ordinary Set, its own folder nesting (§D), and its own version codes (§G) exactly as
described in this section. See `writing/academic-writing/Index.md`'s "Module Pairs" section for the
mechanics (the 8-lesson content-role table, the wrapping Module-Pair Lesson-Plan doc, and how the two
Modules' Focus choices stay distinct).

A Module/Band can hold more than one Set over time - a fresh rotation of lessons for a semester
where the module is retaught, without discarding or conflating it with what was taught before.
**Set numbering is scoped to one Module/Band, not shared across Modules:** a Band's Module 2 starts
its own Set 1 again, the same as Module 1 did - it does not continue Module 1's Set count. This is
why Sets nest inside a `Module_<N>/` folder (see §D) rather than sitting directly under the Band
folder: without that level, two different Modules' Set 1 would collide on the same folder name.
**Lesson numbering is global within a Module/Band, continuing across Sets rather than restarting:**
Set 1 is Lessons 1-4, Set 2 (if planned) is Lessons 5-8, Set 3 is Lessons 9-12, and so on - so
"Lesson 7" unambiguously means Set 2's third lesson without needing to also state which Set. When
planning a new Set, numbering starts at the next integer after the highest lesson number already
planned for that Module/Band, across every Set. A Set is not tied to a semester in the plan itself;
note an actual teaching term against a Set only once it's been assigned to one, as a light
annotation, not a planning input.

For the history of how this figure was originally miscounted as 8 lessons/16 days per module and
corrected, see `CLAUDE.md`'s Sets bullet or Reading's `Changelog.md` (2026-09-01 entry) - not
restated here.

## D. Set/Lesson folder-nesting convention

A lesson's files (raw `.md`, student packet `.html`, later homework) travel together:
`lessons/<band>/Module_<N>/Set_<N>/Lesson_<N>_<Slug>/` holds one lesson's files. A Set's own
assessment (one per Set, not per lesson) sits in `Set_<N>/` itself rather than inside any one
lesson's folder. Sets nest inside a `Module_<N>/` folder because Set numbering restarts at 1 for
each Module (§C) - without that level, two different Modules' Set 1 would collide on the same
folder name. The Module/Band Lesson Plan spans every Set generated for that Module/Band so far, and
sits at the `Module_<N>/` root, above that Module's `Set_<N>/` folders:

```
lessons/<band>/
└── Module_{N}/
    ├── Module{N}_{Band}_Lesson_Plan.md
    └── Set_{N}/
        ├── Set{N}_{Band}_Assessment.md
        └── Lesson_{n}_{Slug}/{lesson .md, packet .html}
```

This nesting is kept even at one lesson per Set (Academic Writing's current case), so no
special-casing is needed later if a shorter lesson cycle ever makes room for more than one lesson
per Set.

**Variant-track Set fork (added 2026-09-07, introduced by Listening/Speaking; see §G's matching version-
code note).** When a lesson type forks a Set into a variant track, its files live in a sibling
`Set_<N><letter>/` folder next to `Set_<N>/`, inside the same `Module_<N>/` -
`lessons/<band>/Module_<N>/Set_<N><letter>/Lesson_<n>_<Slug>/`, same internal shape as the base Set.
The base `Set_<N>/` files are never edited to build the fork; a fork can hold as few as one of the
base Set's lessons (generated on request, not automatically for the whole Set). Example: Listening/
Speaking's `Module_1/Set_1_T/Lesson_1_LostKitchen/` sits beside `Module_1/Set_1/Lesson_1_LostKitchen/`.

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
vocabulary or grammar focus, topic) - one row per lesson. It is the only thing that lets a new
lesson or Set avoid repeating what came immediately before it; without it, each generation run only
ever sees its own lesson(s) and cross-Set/cross-Module repetition is invisible until a teacher
notices it in the classroom. Read it in full before planning or generating; append to it (never
overwrite) once a lesson or Set is approved.

A lesson type's Rotation Log is an overview `Rotation_Log.md` plus one `Rotation_Log_<Band>.md` per
Band that has entries, nested `## Module N` / `### Set S` inside each Band file. A Band's file is
created lazily on that Band's first Set, from the append-template at the bottom of any existing Band
file. Each lesson type's own Module Lesson-Plan prompt defines only the column list its rows carry
(genre/strategy/hook/protocol for Reading, format/strategy/skill/hook/protocol for Listening/Speaking,
Focus A/B/Scenario/writing form for Academic Writing); the mechanics below are the same for all.

**Read before planning; append after approval.** Read `Rotation_Log.md` and the target Band's file in
full before planning any Set. If the Band's file does not exist, this is that Band's first Set: create
it and skip the cross-Set and cross-Module checks. After a plan is reviewed and approved (never a
draft still being revised), append its rows under that Module/Band's existing `## Module N` section,
or a new one, as a new `### Set S (planned <date>)` subsection using the Band file's own template.
Lesson numbers continue the Module/Band's global numbering (§C); note the highest number already
used and start at the next integer.

**Cross-Set rule (same Module/Band, a new Set after one already logged):** the new Set's first lesson
must not repeat the most recent existing Set's final lesson in any rotated column (genre or format,
strategy or skill, hook, protocol, Focus pair, writing form, as applicable) - the same adjacency
logic the within-Set rule applies between consecutive lessons, carried across the Set boundary.
Vocabulary theme and topic: flag (do not block) an obvious repeat from the most recent existing Set.

**Cross-Module rule (a new Module/Band's first Set), and Academic Writing's cross-Band rule:**
adjacency only. The new first lesson must not repeat the immediately preceding Module's (or, for
Writing, any other Band's) most recently logged Set's final lesson in the rotated columns. Vocabulary
theme, topic, and Scenario: flag an obvious repeat from the immediately preceding Module or Set;
older repeats are lower-risk and are noted, not blocked.

Why the lighter touch across Sets and Modules: within a Set every lesson is visible in one planning
pass, so a hard no-repeat rule is enforceable. Across Sets and Modules only the log's history is
visible, the rotation banks are finite (four or five options each), and a full-history block would
eventually make later Sets impossible to plan. Adjacency plus a recency flag catches the repetition a
student would actually notice (two Sets in a row opening the same way) without over-constraining a
program that will run many Sets across many Modules.

## G. Lesson version numbers

Every individual Lesson document and its student packet carries a version code,
`<Module>.<Set>.<Lesson>.<Version>` - four dot-separated numbers, no letter prefix (corrected
2026-09-08 from an earlier `S<Set>.<Lesson>.<Iteration>` shape; see `Changelog.md`) - distinct from
the "vX.Y" numbers used elsewhere in this repo (those version the *generation prompt files*
themselves, e.g. `Generate_Lesson_Prompt_v2.7.md`, tracked in each lesson type's own `Changelog.md`
- a separate axis from an individual lesson's own content version).

- `<Module>` is the Module the lesson belongs to (see §A).
- `<Set>` is the Set the lesson belongs to (see §C), scoped to that Module (§C - Set numbering
  restarts at 1 for each new Module, so `<Module>` is what keeps two different Modules' Set 1 from
  colliding in a version code).
- `<Lesson>` is that lesson's **global** lesson number (§C's continuing numbering across Sets - Set
  2's first lesson is Lesson 5, not Lesson 1), not its position within the Set. This keeps the
  version consistent with the one lesson-numbering scheme the program already uses everywhere else.
- `<Version>` starts at `0` when a lesson is first generated and saved, and increments by 1 each
  time that specific lesson's content is substantively revised afterward (e.g. after it's been
  taught and a revision pass changes it) - tracked **per lesson**, not per Set, so two lessons in
  the same Set can sit at different `<Version>` numbers if only one of them was revised.

Example: Module 1 Set 1's four lessons start at `1.1.1.0`, `1.1.2.0`, `1.1.3.0`, `1.1.4.0`; if Lesson
2 is later revised after being taught, it becomes `1.1.2.1` while its Set-mates stay at their
original `<Version>`.

Applies to individual Lesson docs/packets only - not Module Lesson-Plans or Assessments. A lesson
type's own Rotation Log (§F) is the source of truth for a lesson's current version (see each
`Rotation_Log_<Band>.md`'s lesson table); the Markdown lesson doc and its HTML student packet each
restate it (see `Student_Packet_Style_Guide.md` §B for the packet masthead's version line).

The `<Module>.<Set>.<Lesson>.<Version>` shape itself is retroactive as of 2026-09-08 (unlike most
conventions in this file, which apply going-forward only): every already-assigned version code across
all three modalities was rewritten from the old `S<Set>.<Lesson>.<Iteration>` shape to this one in the
same pass, since every lesson generated so far is Module 1 and the substitution was unambiguous
(`S<Set>...` → `1.<Set>...`). See `Changelog.md`.

**Optional variant-track Set token (added 2026-09-07, introduced by Listening/Speaking).** A lesson type
may fork a Set into a variant track that adds something to every lesson in it without changing their
core content - Listening/Speaking's TOEFL Track Tier (its own Lesson Generation Prompt Section 0.6) is
the first example: one tier of each lesson in the fork gains an added, optional alternate task. Such a
fork's `<Set>` token carries a single uppercase letter suffixed onto the Set number (e.g. `1T`), giving
version codes like `1.1T.1.0` - still fitting this section's `<Module>.<Set>.<Lesson>.<Version>` shape
exactly, just with a non-purely-numeric `<Set>`. The suffix identifies which variant track a lesson doc belongs
to; see §D for where such a fork's files physically live. This is a mechanic a lesson type may use, not
a requirement on every lesson type - Passage Reading's own TOEFL extension, for instance, is a separate
companion document rather than a variant-track fork, and needs no such suffix.

## H. Asset (audio/image/source-link) naming convention

A lesson's raw media assets (audio clips, images, source-video link
shortcuts) live flat in that lesson's own
`Lesson_<N>_<Slug>/` folder (§D), alongside its `.md` and packet `.html` -
no separate `media/` subfolder. Naming, added 2026-09-08:

- **Audio:** `Lesson<N>_<Slug>_Audio.<ext>` - a lesson's own recorded/sourced
  audio clip (e.g. `Lesson1_NewBakery_Audio.mp3`).
- **Images:** `Lesson<N>_<Slug>_Img_<Purpose>.<ext>`, where `<Purpose>` is a
  short PascalCase label for what the image is used for in the lesson (e.g.
  `Lesson3_Backpack_Img_Hook.webp` for a Mystery Quote hook photo,
  `Lesson3_Backpack_Img_ChoiceBicycle.jpg` for one option image in a
  multiple-choice item). Normalize `.jpeg` to `.jpg` (same format, filename
  only); leave other image formats as their source provides them rather than
  re-encoding.
- **Source-video link shortcut:** for a lesson whose real source is a video
  that isn't itself downloaded into the repo, `Lesson<N>_<Slug>_SourceVideo.<ext>`,
  one file per platform as available (`.webloc` for Mac, `.url` for
  Windows/cross-platform) - lets the citation link be opened directly from the
  lesson folder without opening the lesson `.md` to find it. The URL itself
  stays the source of truth in the lesson `.md`'s citation block (Listening/
  Speaking's Section 0.3); the link file is a convenience copy, not a
  replacement for that citation.

Dropping raw assets into a lesson folder does not by itself embed them into
the lesson `.md` or student packet `.html` - integrating an asset into the
actual content (e.g. wiring a choice image to its multiple-choice item, or
swapping a packet's "real picture placeholder" for the real image) is a
separate step, tracked per lesson type's own `Index.md` Pending work until
done.

## Changelog

See `Changelog.md` in this folder.
