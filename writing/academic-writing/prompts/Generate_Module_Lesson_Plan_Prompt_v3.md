# Academic Writing Module Lesson-Plan Generation Prompt (v3)

Companion to `Generate_Lesson_Prompt_v5.md`. Mirrors the Passage Reading and Listening/Speaking Module
Lesson-Plan Generation Prompts' structure and reasoning, adapted for Writing's own shape.

**Plans a full Set (Beginner) or a full Module Pair - two Sets together (Intermediate/Advanced/Proficient) - in
one pass, like Reading and Listening/Speaking plan a full Set - but for a different reason.** Reading and
Listening/Speaking plan a full Set at once specifically to rotate genre/strategy/hook/protocol across 4
*independent* lessons without repeats - a within-Set constraint only checkable with all 4 lessons visible
together. Academic Writing's lessons are not independent: they share **one** Scenario, carried from grammar input
through a finished piece, in a fixed arc (`Generate_Lesson_Prompt_v5.md`'s "THE MODULE PAIR" section). For
Beginner that arc is 4 lessons, one Set, one Module. **For Intermediate, Advanced, and Proficient, that arc is 8
lessons spanning two consecutive Modules paired together** (odd with the next even: 1-2, 3-4, 5-6, 7-8 - see
`shared/Program_Conventions.md` §C's Module Pair addendum), because the essay itself now takes a whole month
(roughly) to finish, with each Module teaching its own Grammar/Essay Focus and contributing it to the shared
piece rather than each Module producing an independent essay. This prompt plans the whole arc in one pass not to
check for within-arc repeats (there's only one Scenario to repeat against itself) but because the Scenario,
genre/real-world-writing-form, **each Module's own** Grammar Focus A/B pairing, Essay Focus A/B direction, and
Leveled Mentor Ladder direction are decisions every upcoming lesson-generation run needs to read from
identically - deciding them once, up front, is what lets every later lesson continue what came before it instead
of re-deriving it. Planning both Modules of a pair together, rather than one at a time, is what catches a
Focus-A/B collision between the two Modules (Section 0.9's within-pair non-repetition rule) or a gap in Module
N+1's own CSV-objective coverage (see Task step 3 below) *before* any lesson content is written around it - the
same reasoning that makes running this as its own step, separate from lesson generation, valuable in the first
place: catching a mistake in a short plan is far cheaper than catching it after 8 full lessons have already been
written.

**Current version: v3.** For version history, see `Changelog.md`. (v3 rescopes this prompt from planning one
Module's 4-lesson Set to planning a full **Module Pair** - two Modules' Sets together - for Intermediate,
Advanced, and Proficient, per the Module Pair mechanic introduced in `shared/Program_Conventions.md` §C and this
family's own `Changelog.md`. Beginner is unaffected and still plans one Module's Set at a time, exactly as v2
did. The actual planning decisions - Scenario, Focus A/B, Mentor Ladder direction - are the same kind of decision
v1 and v2 already made; only the unit being planned grew, from one Set to two Sets for three of the four Bands.)

---

## SECTION 0: ROTATION LOG (READ BEFORE PLANNING, UPDATE AFTER APPROVAL)

**Read `Rotation_Log.md` and the target Band's `Rotation_Log_<Band>.md` in full before planning; append the
approved plan's entries to `Rotation_Log_<Band>.md` after approval** (create that Band's file if this is the
Band's first Set, using the template at the bottom of any existing `Rotation_Log_<Band>.md`) - see
`shared/Program_Conventions.md` §F for the general mechanics. If neither file exists yet, this is the first Set
ever planned for any Band; create fresh and note that cross-Set and cross-Band checks below are not applicable
this time.

**Before planning:** read the full log. If this Band already has one or more Sets logged, note the highest
global Lesson # used so far **for each Module** (each Module's own lessons number independently - see
`shared/Program_Conventions.md` §C/§G) and that Band's most recently logged Set (Grammar Focus A/B pair,
Scenario/topic, real-world writing form - for the cross-Set adjacency check). Also scan every other Band's most
recently logged Set (for the lighter-touch cross-Band check) and the fuller set of logs for a Focus A/B pair or
Scenario topic that has recurred more than once in the last 3-4 Sets/Pairs overall, per
`Generate_Lesson_Prompt_v5.md` Section 0.9.

**Cross-Set/cross-Pair rules (same Band, a new Set or Pair added after one or more already logged):** the new
plan must not repeat the immediately preceding logged Set's/Pair's Grammar Focus A/B pair(s) or real-world
writing form. Scenario topic: flag (don't block) an obvious repeat from the immediately preceding Set/Pair in
this same Band.

**Within-pair rule (Intermediate/Advanced/Proficient only, new in v3):** Module N+1's own Grammar/Essay Focus A/B
must not repeat Module N's own Focus A/B chosen earlier in the same plan - this is a same-plan check, stronger
than the cross-Set adjacency rule above, since both choices are being decided in one pass right now. See Task
step 3's Focus A/B guidance and `Generate_Lesson_Prompt_v5.md` Section 0.9.

**Cross-Band rules (lighter touch, deliberately - same rationale as Reading/L-S's cross-module rules: a hard
full-history block would eventually make planning impossible against Section 0.4's finite Grammar Focus Bank):**

- **Grammar Focus A/B pair (adjacency only):** a new Band's first Set/Pair should not repeat the Focus A/B pair
  used by the most recently logged Set/Pair in any other Band, where avoidable. The bank in Section 0.4 of the
  Lesson prompt is finite (one row per Level, 1-8), so exact non-repetition across every Band forever is not
  realistic; adjacency is what a student (or a teacher running two Bands) would actually notice.
- **Scenario topic (recency check, not full-history block):** flag, rather than automatically forbid, a new
  Scenario that duplicates or closely overlaps one used in another Band's most recently logged Set/Pair. An older
  repeat is lower-risk and does not need to be blocked.
- **Real-world writing form:** same recency check as Scenario topic.

**After a plan is reviewed and approved** (not on a rough draft still being revised): append new rows - one per
lesson, sharing the plan's Scenario/genre columns but each naming its own Module, global Lesson # within that
Module, and Set-position/Pair-position content role - to that Band's own `Rotation_Log_<Band>.md`. For
Beginner: 4 rows, nested under a new `### Set S (planned <date>)` subsection under that Module's `## Module N`
heading, exactly as v2 did. For Intermediate/Advanced/Proficient: 8 rows, split across the plan's two Modules'
own `## Module N` / `## Module N+1` sections in that Band's log (creating Module N+1's own `## Module N+1`
heading and `### Set 1` subsection if this is that Module's first Set), each Module's 4 rows using that Module's
own Set/Lesson numbering - plus one note, on either Module's subsection, cross-referencing the other as "Part 1
of 2" / "Part 2 of 2" of the same Module Pair's essay. Use each Band file's own "Format for the next entry"
template - do not invent a new table shape here. Do not append a draft still being revised; the log's value
depends on it reflecting only plans that were actually approved and are actually going to be taught.

---

## INPUTS (fill in before running)

- **Band:** [Beginner / Intermediate / Advanced / Proficient]. A specific task Level is not requested separately:
  this Band's task Levels are looked up automatically from `Generate_Lesson_Prompt_v5.md` Section 0.1's Task
  Levels by Band table (Beginner: 1, 2, 3; Intermediate: 2, 3, 4, 5; Advanced: 4, 5, 6, 7; Proficient:
  5, 6, 7, 8).
- **Beginner: Module.** [e.g. "Module 1: Describing"] - Beginner plans one Module's Set at a time, unaffected by
  Module Pairing.
- **Intermediate/Advanced/Proficient: Module Pair.** [e.g. "Modules 1-2"] - always the fixed odd/even grouping
  (1-2, 3-4, 5-6, 7-8); name both Modules, not one.
- **Set number(s):** [each named Module's next Set - default: the next integer after the highest Set already
  logged for that Module in `Rotation_Log_<Band>.md`, or 1 if that Module has no logged Sets yet. Set numbering
  restarts per Module (`shared/Program_Conventions.md` §C) - Module N+1's Set 1 is not a continuation of Module
  N's Set count, even inside the same Pair.]
- **Starting global Lesson # (per Module):** [default: the next integer after the highest global Lesson # already
  logged for that specific Module in this Band, or 1 if that Module has no logged Sets yet - each Module's own 4
  lessons take four consecutive numbers within that Module, per `shared/Program_Conventions.md` §C/§G. Module
  N+1's Lesson 1 is not a continuation of Module N's lesson numbering.]
- **Source of truth for objectives:** `learningobjectives.csv`, filtered to the relevant Module(s), this Band's
  task Levels, and the **Writing modality only** - matching the Lesson prompt's own grounding rule (Section 0.1).
  Reading and Listening/Speaking objectives are out of scope for this program's Writing class; do not select or
  justify a task by tracing it to a Reading or Listening/Speaking Can-do statement.
- **Rotation Log:** `Rotation_Log.md` plus this Band's `Rotation_Log_<Band>.md`, read in full before planning
  (Section 0 above); if the Band's file does not exist yet, treat this as that Band's first Set/Pair and skip
  cross-Set/cross-Band checks.

## TASK

1. Read the Rotation Log per Section 0. Identify the highest global Lesson # used so far **for each Module named
   in this request** (each Module's own lessons take the next four consecutive integers within that Module) and
   the most recently logged Set's/Pair's row(s) (for the cross-Set adjacency check). Also identify every other
   Band's most recently logged Set/Pair (for the cross-Band checks) and scan the fuller log set for a recurring
   Focus A/B pair or Scenario topic. If the log doesn't exist yet, note that this is the first planned Set/Pair
   for any Band.

2. Determine this Band's task Levels from `Generate_Lesson_Prompt_v5.md` Section 0.1's table. Pull the actual row
   from `learningobjectives.csv` for **Module N** (Beginner's single Module, or the first Module of an
   Intermediate/Advanced/Proficient Pair) and each of those task Levels, **Writing modality only**. Quote the
   Writing Description verbatim (not paraphrased) for every task Level in the Band, not just the Band's own two
   native CEFR levels. For Intermediate/Advanced/Proficient, also pull **Module N+1's** own row for each task
   Level - this grounds the CSV-coverage self-check in step 4, even though the shared essay's genre itself stays
   Module N's throughout. These quoted statements are the authority for what each task Level's Mentor
   Text/Mentor Essay and drafting task must satisfy - do not invent an easier/harder version instead of using
   them.

3. Produce a single plan (these elements are shared across every lesson in the arc - they are decided once here,
   not re-derived per lesson):

   - **Module(s), Set number(s), and global Lesson #s** each Module's lessons will use (Beginner: one Module,
     one Set, 4 lesson #s; Intermediate/Advanced/Proficient: both Modules, each with its own Set number and its
     own 4 lesson #s, continuing that specific Module's own numbering - never restarted mid-Pair, never shared
     between the two Modules).
   - **Lesson-position table.** Beginner uses the original 4-row table (Set position, global Lesson #, content
     role) from `Generate_Lesson_Prompt_v5.md`'s "THE MODULE PAIR" section (its Beginner half).
     Intermediate/Advanced/Proficient use the full 8-row table from that same section, filling in this Pair's
     actual Module numbers and global Lesson #s:

     | Pair position | Module | Set position | Global Lesson # | Content role |
     | --- | --- | --- | --- | --- |
     | 1 | N | 1 of 4 | [N's lesson #] | Module N's Grammar Focus A: input, modeling, deeper practice |
     | 2 | N | 2 of 4 | [N's lesson #] | Module N's Grammar Focus B, Essay Focus A/B (where applicable), Mentor Ladder, prewriting |
     | 3 | N | 3 of 4 | [N's lesson #] | Drafting, parts 1-2 |
     | 4 | N | 4 of 4 | [N's lesson #] | Hard self-revision, draft completion, hand-off (not published) |
     | 5 | N+1 | 1 of 4 | [N+1's lesson #] | Re-engagement + Module N+1's Grammar Focus A: input, modeling |
     | 6 | N+1 | 2 of 4 | [N+1's lesson #] | Module N+1's Grammar Focus B, Essay Focus A/B (where applicable), Mentor Ladder second look, revision-planning |
     | 7 | N+1 | 3 of 4 | [N+1's lesson #] | Revision and expansion drafting, parts 1-2, merged self-edit |
     | 8 | N+1 | 4 of 4 | [N+1's lesson #] | Peer editing, hard self-revision, publishing, Closing Transfer Check (both Modules + Module N+1's own CSV verb) |

   - **Scenario** (one line: the shared real-world writing situation, stimulus, and Module-aligned purpose every
     task Level, across every lesson in the arc, will write about, per Section 0.1a of the Lesson prompt).
     Unlike Reading's anchor text, a Writing Scenario asserts nothing as factually true - it is a shared
     situation to write from, not a shared text to comprehend - so it does not need Reading's "grounded in a
     real, verifiable referent" rule or its fabricated-quote guardrail. It does need to be concrete and
     genuinely writable at every task Level in the band, from a Level 1-3 single-word frame up through a Level
     6-8 full essay where the band reaches that high: avoid a Scenario so abstract that a frame-regime Level has
     nothing concrete to point to, or so narrow that an essay-regime Level has nothing to develop across several
     paragraphs. It must also sustain the full arc (Beginner: 4 lessons, grammar input through a finished,
     published piece; Intermediate/Advanced/Proficient: 8 lessons across two Modules, grammar input through
     hand-off through revision/expansion to a finished, published piece), not just a single day's activity. Flag
     (per Section 0 above) if it closely echoes the immediately preceding Set/Pair in this Band, or another
     Band's most recently logged Scenario/Pair.
   - **Genre / real-world writing form**, named directly from Section 0.9's Module-to-real-world-form mapping
     table, using **Module N's own mapping only** (the Levels 1-5 form, and the Levels 6-8 essay type where a
     Band reaches that high and a mapping exists). For Intermediate/Advanced/Proficient, state explicitly that
     Module N+1 inherits this same genre unchanged - the shared piece does not switch genres partway through the
     pair, even if Module N+1's own mapping would normally point elsewhere. Check against Section 0 above the
     same way as the Focus A/B pairing.
   - **Grammar Focus A/B pairing for Module N** (Beginner's only Focus A/B; the first half of an
     Intermediate/Advanced/Proficient pair), chosen per `Generate_Lesson_Prompt_v5.md` Section 0.4's Grammar
     Focus Bank and its row-selection rule: anchor at the Band's own **native** Paragraph Composition row (not
     automatically its lowest - see Section 0.4's worked distinction between Intermediate, whose lowest Paragraph
     Composition Level, 4, is native, and Advanced, whose lowest, 4, is an extension-down accommodation with its
     own native floor one Level up, at 5). Name which row is chosen and why. Check the pairing against Section 0
     above: it must not repeat the immediately preceding Set/Pair in this Band, and should avoid an adjacency
     repeat against another Band's most recently logged pair where avoidable.
   - **Grammar Focus A/B pairing for Module N+1 (Intermediate/Advanced/Proficient only).** Must be genuinely
     different in content from Module N's own Focus A/B chosen above (Section 0's within-pair rule) - use the
     Grammar Focus Bank's Alternate column once authored, or hand-select distinct content appropriate to Module
     N+1's own native row and its own writing purpose. Name the row chosen and confirm it does not collide with
     Module N's pairing.
   - **Essay Focus A/B direction** (only for a Band reaching Essay Composition, i.e. Advanced or Proficient): per
     Section 0.4c, this is always anchored at Level 6's row (essay shape, hook types, thesis construction /
     topic-sentence-and-supporting-sentence structure, outlining) regardless of Band - name that this arc will
     teach it (once, via Module N; Module N+1 does not re-teach essay structure from scratch, though it may add
     its own cohesion-focused extension if genuinely distinct), and which essay type (per Section 0.9's
     Module-to-real-world-form mapping table, Module N's mapping) the Mentor Essay(s) will use, or that the
     mapping is not yet established for Module N and Levels 6-8 will use an extended-paragraph fallback per that
     table's note.
   - **CSV-objective-coverage check (Intermediate/Advanced/Proficient only, new in v3).** Because the shared essay
     stays Module N's genre throughout, Module N+1's own CSV learning objective (its own writing-purpose verb) is
     not exercised by the essay itself. State explicitly how this is covered: the plan must confirm Lesson 8's
     Closing Transfer Check will include a short, separate task exercising Module N+1's own verb on a new small
     prompt (per `Generate_Lesson_Prompt_v5.md` Section 0.8) - name concretely what that small separate task will
     ask students to do, calibrated to the Scenario's own subject matter where reasonable, so this is not left
     for the Lesson prompt to invent unplanned.
   - **Real-world writing form**: restated from the genre bullet above, for clarity in the plan's own summary.
     Check against Section 0 above the same way as the Focus A/B pairing.
   - **Leveled Mentor Ladder direction**, one line per task Level in the Band: what that Level's Mentor
     Text/Mentor Essay will model on this Scenario (e.g. "Level 2: one describing word into the fixed frame,
     drawn from the Scenario's object" / "Level 6: a direct-thesis five-paragraph essay naming [a specific reader
     the Scenario will supply] and their stated concern"), per Section 0.1b. This is a direction, not the actual
     Mentor Text/Essay content - do not write the worked model itself in this step (see Task step 5). For
     Intermediate/Advanced/Proficient, also note in one line per task Level what Lesson 5-6's "Mentor Ladder
     second look" will ask students to notice once Module N+1's focus is introduced (e.g. "Level 6: what would
     [Module N+1's cohesion device] add to this essay's second body paragraph?").
   - **Task-Level basis**: for every task Level in this Band's Task Levels by Band table, name the exact Writing
     CSV Description (Level N, Writing, Module N) this arc's Mentor Ladder and drafting task at that Level will
     satisfy. State explicitly which task Level each objective maps to, rather than leaving it implicit; every
     task Level gets its own named objective, never a single generic description scaled informally.

4. After the plan, run a self-check and report it in a few sentences:

   - Does every task Level in this Band get its own quoted Writing CSV Description, not a generic
     simplification of the centerpiece task?
   - Is the Scenario genuinely writable at every task Level in the Band, from its lowest (frame-regime, where
     applicable) through its highest (essay-regime, where applicable), without needing Reading-style real-world
     verifiability, and does it sustain the full arc (4 lessons for Beginner; 8 lessons across two Modules for
     Intermediate/Advanced/Proficient)?
   - Is Grammar Focus A/B anchored at the Band's own native Paragraph Composition row per Section 0.4's
     corrected row-selection rule, not automatically its lowest? For a Band reaching Essay Composition, is Essay
     Focus A/B correctly anchored at Level 6's row regardless of the Band?
   - **(Intermediate/Advanced/Proficient)** Is Module N+1's own Grammar/Essay Focus A/B genuinely distinct from
     Module N's, not a relabeling of the same content (Section 0's within-pair rule)?
   - **(Intermediate/Advanced/Proficient)** Does the plan confirm Module N+1 inherits Module N's genre/real-world
     writing form unchanged, rather than switching genres mid-pair?
   - **(Intermediate/Advanced/Proficient)** Does the plan name a concrete, separate Closing-Transfer-Check task
     giving Module N+1's own CSV verb genuine coverage, rather than leaving that gap unaddressed?
   - Does the Focus A/B pairing and the real-world writing form avoid repeating the immediately preceding
     Set/Pair in this same Band? Is any cross-Band adjacency or recency repeat flagged rather than silently
     repeated?
   - Do the global Lesson #s for each Module continue that Module's own numbering, rather than restarting or
     borrowing from the other Module in the Pair?
   - Does the lesson-position table correctly map every position to its fixed content role, its correct Module,
     and consecutive global Lesson #s within that Module?
   - Is the Leveled Mentor Ladder direction distinct in kind, not just in wording, across a Band that spans a
     regime boundary (e.g. an Intermediate lesson's Level 2-3 direction should describe frame content, not a
     scaled-down paragraph)?

5. Do not write any Mentor Text, Mentor Essay, grammar-focus table content, drafting task, checklist, or Peer
   Editing Form in this step. If asked to also generate full lesson content in the same turn, stop and confirm
   the plan is approved first.

## OUTPUT

The plan (shared fields plus the lesson-position table - 4 rows for Beginner, 8 for
Intermediate/Advanced/Proficient), then the self-check paragraph. For Intermediate/Advanced/Proficient, save the
approved plan as `lessons/<band>/ModulePair_<N>-<N+1>/ModulePair_<N>-<N+1>_<Band>_Lesson_Plan.md` (Beginner keeps
the existing `lessons/<band>/Module_<N>/Module<N>_<Band>_Lesson_Plan.md` shape, unaffected). Once the plan is
reviewed and approved, also produce the Rotation Log entries per Section 0's format (4 rows for Beginner under one
`### Set S` subsection; 8 rows for Intermediate/Advanced/Proficient split across the two Modules' own `## Module
N` / `## Module N+1` sections, cross-referenced as Part 1/Part 2 of the same Pair) ready to append. Nothing else.
