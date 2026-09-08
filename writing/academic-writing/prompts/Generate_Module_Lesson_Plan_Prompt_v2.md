# Academic Writing Module Lesson-Plan Generation Prompt (v2)

Companion to `Generate_Lesson_Prompt_v4.md`. Mirrors the Passage Reading and Listening/Speaking Module
Lesson-Plan Generation Prompts' structure and reasoning, adapted for Writing's own shape.

**Plans a full Set (4 lessons) in one pass, like Reading and Listening/Speaking - but for a different reason.**
Reading and Listening/Speaking plan a full Set at once specifically to rotate genre/strategy/hook/protocol across
4 *independent* lessons without repeats - a within-Set constraint only checkable with all 4 lessons visible
together. Academic Writing's 4 lessons in a Set are not independent: they share **one** Scenario, carried from
grammar input through a finished, published piece, in a fixed arc (`Generate_Lesson_Prompt_v4.md`'s "The
Four-Lesson Set" table: Lesson 1 = Focus A input/practice, Lesson 2 = Focus B/Essay Focus/prewriting, Lesson 3 =
drafting, Lesson 4 = peer edit/revision/publishing). So this prompt plans the whole Set in one pass not to check
for within-Set repeats (there's only one Scenario to repeat against itself) but because the Scenario, Grammar
Focus A/B pairing, Essay Focus A/B direction, and Leveled Mentor Ladder direction are single decisions that all
4 upcoming lesson-generation runs need to read from identically - deciding them once, up front, is what lets
Lessons 2-4 continue Lesson 1's content instead of re-deriving it (`Generate_Lesson_Prompt_v4.md`'s "Relationship
to the Module Lesson-Plan prompt"). The value of running this as its own step, separate from lesson generation,
is the same reason Reading and Listening/Speaking run theirs first: catching a Scenario or Focus mistake in a
short plan is far cheaper than catching it after 4 full lessons (Mentor Ladder, every lesson's activities,
checklists, Peer Editing Form) have already been written around it.

**Current version: v2.** For version history, see `Changelog.md`. (v2 restructures this prompt from planning one
8-day lesson to planning a full 4-lesson Set in one pass, matching Reading's/Listening-Speaking's Module
Lesson-Plan cadence - see `shared/Program_Conventions.md` §C and `Changelog.md`'s 2026-09-08 entry. The actual
planning decisions - Scenario, Focus A/B, Mentor Ladder direction - are the same kind of decision v1 already
made; only the unit being planned changed, from one lesson to one Set.)

---

## SECTION 0: ROTATION LOG (READ BEFORE PLANNING, UPDATE AFTER APPROVAL)

**Read `Rotation_Log.md` and the target Band's `Rotation_Log_<Band>.md` in full before planning; append the
approved Set's entries to `Rotation_Log_<Band>.md` after approval** (create that Band's file if this is the
Band's first Set, using the template at the bottom of any existing `Rotation_Log_<Band>.md`) - see
`shared/Program_Conventions.md` §F for the general mechanics. If neither file exists yet, this is the first Set
ever planned for any Band; create fresh and note that cross-Set and cross-Band checks below are not applicable
this time.

**Before planning a new Set:** read the full log. If this Band already has one or more Sets logged, note the
highest global Lesson # used so far (this Set's four lessons continue numbering from the next integer) and that
Band's most recently logged Set (Grammar Focus A/B pair, Scenario/topic, real-world writing form - for the
cross-Set adjacency check). Also scan every other Band's most recently logged Set (for the lighter-touch
cross-Band check) and the fuller set of logs for a Focus A/B pair or Scenario topic that has recurred more than
once in the last 3-4 Sets overall, per `Generate_Lesson_Prompt_v4.md` Section 0.9.

**Cross-Set rules (same Band, a new Set added after one or more already logged):** the new Set must not repeat
the immediately preceding logged Set's Grammar Focus A/B pair or real-world writing form. Scenario topic: flag
(don't block) an obvious repeat from the immediately preceding Set in this same Band.

**Cross-Band rules (lighter touch, deliberately - same rationale as Reading/L-S's cross-module rules: a hard
full-history block would eventually make planning impossible against Section 0.4's finite Grammar Focus Bank):**

- **Grammar Focus A/B pair (adjacency only):** a new Band's first Set should not repeat the Focus A/B pair
  used by the most recently logged Set in any other Band, where avoidable. The bank in Section 0.4 of the
  Lesson prompt is finite (one row per Level, 1-8), so exact non-repetition across every Band forever is not
  realistic; adjacency is what a student (or a teacher running two Bands) would actually notice.
- **Scenario topic (recency check, not full-history block):** flag, rather than automatically forbid, a new
  Scenario that duplicates or closely overlaps one used in another Band's most recently logged Set. An older
  repeat is lower-risk and does not need to be blocked.
- **Real-world writing form:** same recency check as Scenario topic.

**After a Set's plan is reviewed and approved** (not on a rough draft still being revised): append four new
rows - one per lesson, sharing the plan's Scenario/Focus columns but each naming its own global Lesson # and
Set-position content role (Focus A input / Focus B & prewriting / Drafting / Peer edit, revision & publishing) -
to that Set's own Band's `Rotation_Log_<Band>.md`, nested under a new `### Set S (planned <date>)` subsection,
using that file's own "Format for the next entry" template at the bottom of the file - do not invent a new table
shape here. Do not append a draft still being revised; the log's value depends on it reflecting only plans that
were actually approved and are actually going to be taught.

---

## INPUTS (fill in before running)

- **Module:** [e.g. "Module 1: Describing"]
- **Band:** [Beginner / Intermediate / Advanced / Proficient]. A specific task Level is not requested separately:
  this Band's task Levels are looked up automatically from `Generate_Lesson_Prompt_v4.md` Section 0.1's Task
  Levels by Band table (Beginner: 1, 2, 3; Intermediate: 2, 3, 4, 5; Advanced: 4, 5, 6, 7; Proficient:
  5, 6, 7, 8).
- **Set number:** [this Band's next Set - default: the next integer after the highest Set already logged in
  `Rotation_Log_<Band>.md`, or 1 if this Band has no logged Sets yet]
- **Starting global Lesson #:** [default: the next integer after the highest global Lesson # already logged for
  this Band, or 1 if this is the Band's first Set - this Set's four lessons take four consecutive numbers from
  here, per `shared/Program_Conventions.md` §C/§G]
- **Source of truth for objectives:** `learningobjectives.csv`, filtered to this Module, this Band's task Levels,
  and the **Writing modality only** - matching the Lesson prompt's own grounding rule (Section 0.1). Reading and
  Listening/Speaking objectives are out of scope for this program's Writing class; do not select or justify a
  task by tracing it to a Reading or Listening/Speaking Can-do statement.
- **Rotation Log:** `Rotation_Log.md` plus this Band's `Rotation_Log_<Band>.md`, read in full before planning
  (Section 0 above); if the Band's file does not exist yet, treat this as that Band's first Set and skip
  cross-Set/cross-Band checks.

## TASK

1. Read the Rotation Log per Section 0. If this Band already has one or more Sets logged, identify the highest
   global Lesson # used so far (this Set's four lessons take the next four consecutive integers) and the most
   recently logged Set's row(s) (for the cross-Set adjacency check). Also identify every other Band's most
   recently logged Set (for the cross-Band checks) and scan the fuller log set for a recurring Focus A/B pair or
   Scenario topic. If the log doesn't exist yet, note that this is the first planned Set for any Band.

2. Determine this Band's task Levels from `Generate_Lesson_Prompt_v4.md` Section 0.1's table. Pull the actual
   row from `learningobjectives.csv` for this Module and each of those task Levels, **Writing modality only**.
   Quote the Writing Description verbatim (not paraphrased) for every task Level in the Band, not just the
   Band's own two native CEFR levels. These quoted statements are the authority for what each task Level's
   Mentor Text/Mentor Essay and drafting task must satisfy - do not invent an easier/harder version instead of
   using them.

3. Produce a single Set-level plan (these elements are shared across all 4 of the Set's lessons - they are
   decided once here, not re-derived per lesson) with these elements:

   - **Set number** and the **four global Lesson #s** this Set's lessons will use (continuing this Band's own
     global numbering - see the Rotation Log note above; not restarted per Set).
   - **Lesson-position table**, one row per Set position, mapping each to its fixed content role
     (`Generate_Lesson_Prompt_v4.md`'s "The Four-Lesson Set" table) and its own global Lesson #:

     | Set position | Global Lesson # | Content role |
     | --- | --- | --- |
     | 1 | [N] | Grammar Focus A: input, modeling, deeper practice |
     | 2 | [N+1] | Grammar Focus B, Essay Focus A/B (where applicable), Mentor Ladder, prewriting |
     | 3 | [N+2] | Drafting, parts 1-2, self-edit |
     | 4 | [N+3] | Peer editing, revision, publishing, Closing Transfer Check |

   - **Scenario** (one line: the shared real-world writing situation, stimulus, and Module-aligned purpose every
     task Level, across all 4 lessons in the Set, will write about, per Section 0.1a of the Lesson prompt).
     Unlike Reading's anchor text, a Writing Scenario asserts nothing as factually true - it is a shared
     situation to write from, not a shared text to comprehend - so it does not need Reading's "grounded in a
     real, verifiable referent" rule or its fabricated-quote guardrail. It does need to be concrete and
     genuinely writable at every task Level in the band, from a Level 1-3 single-word frame up through a Level
     6-8 full essay where the band reaches that high: avoid a Scenario so abstract that a frame-regime Level has
     nothing concrete to point to, or so narrow that an essay-regime Level has nothing to develop across several
     paragraphs. It must also sustain a full arc across all 4 lessons (grammar input through a finished,
     published piece), not just a single day's activity. Flag (per Section 0 above) if it closely echoes the
     immediately preceding Set in this Band, or another Band's most recently logged Scenario.
   - **Grammar Focus A/B pairing**, chosen per `Generate_Lesson_Prompt_v4.md` Section 0.4's Grammar Focus Bank
     and its row-selection rule: anchor at the Band's own **native** Paragraph Composition row (not automatically
     its lowest - see Section 0.4's worked distinction between Intermediate, whose lowest Paragraph Composition
     Level, 4, is native, and Advanced, whose lowest, 4, is an extension-down accommodation with its own native
     floor one Level up, at 5). Name which row is chosen and why, per this Band's own native-floor status. Check
     the pairing against Section 0 above: it must not repeat the immediately preceding Set in this Band, and
     should avoid an adjacency repeat against another Band's most recently logged pair where avoidable.
   - **Essay Focus A/B direction** (only for a Band reaching Essay Composition, i.e. Advanced or Proficient): per
     Section 0.4c, this is always anchored at Level 6's row (essay shape, hook types, thesis construction /
     topic-sentence-and-supporting-sentence structure, outlining) regardless of Band - name that this Set will
     teach it, and which essay type (per Section 0.9's Module-to-real-world-form mapping table) the Mentor
     Essay(s) will use, or that the mapping is not yet established for this Module and Levels 6-8 will use an
     extended-paragraph fallback per that table's note.
   - **Real-world writing form**, named directly from Section 0.9's Module-to-real-world-form mapping table (the
     Levels 1-5 form, and the Levels 6-8 essay type where a Band reaches that high and a mapping exists). Check
     against Section 0 above the same way as the Focus A/B pairing.
   - **Leveled Mentor Ladder direction**, one line per task Level in the Band: what that Level's Mentor
     Text/Mentor Essay will model on this Scenario (e.g. "Level 2: one describing word into the fixed frame,
     drawn from the Scenario's object" / "Level 6: a direct-thesis five-paragraph essay naming [a specific reader
     the Scenario will supply] and their stated concern"), per Section 0.1b. This is a direction, not the actual
     Mentor Text/Essay content - do not write the worked model itself in this step (see Task step 5).
   - **Task-Level basis**: for every task Level in this Band's Task Levels by Band table, name the exact Writing
     CSV Description (Level N, Writing, this Module) this Set's Mentor Ladder and drafting task at that Level
     will satisfy. State explicitly which task Level each objective maps to, rather than leaving it implicit;
     every task Level gets its own named objective, never a single generic description scaled informally.

4. After the plan, run a self-check and report it in a few sentences:

   - Does every task Level in this Band get its own quoted Writing CSV Description, not a generic
     simplification of the centerpiece task?
   - Is the Scenario genuinely writable at every task Level in the Band, from its lowest (frame-regime, where
     applicable) through its highest (essay-regime, where applicable), without needing Reading-style real-world
     verifiability, and does it sustain a full grammar-input-through-published-piece arc across all 4 lessons?
   - Is Grammar Focus A/B anchored at the Band's own native Paragraph Composition row per Section 0.4's
     corrected row-selection rule, not automatically its lowest? For a Band reaching Essay Composition, is Essay
     Focus A/B correctly anchored at Level 6's row regardless of the Band?
   - Does the Focus A/B pairing and the real-world writing form avoid repeating the immediately preceding Set
     in this same Band? Is any cross-Band adjacency or recency repeat flagged rather than silently repeated?
   - Do the four global Lesson #s continue this Band's own global numbering, rather than restarting at 1?
   - Does the lesson-position table correctly map all 4 Set positions to their fixed content role and to four
     consecutive global Lesson #s?
   - Is the Leveled Mentor Ladder direction distinct in kind, not just in wording, across a Band that spans a
     regime boundary (e.g. an Intermediate lesson's Level 2-3 direction should describe frame content, not a
     scaled-down paragraph)?

5. Do not write any Mentor Text, Mentor Essay, grammar-focus table content, drafting task, checklist, or Peer
   Editing Form in this step. If asked to also generate full lesson content in the same turn, stop and confirm
   the plan is approved first.

## OUTPUT

The plan (Set-level fields plus the lesson-position table), then the self-check paragraph. Once the plan is
reviewed and approved, also produce the four Rotation Log entries (Section 0's format, one row per lesson, using
this Band's own `Rotation_Log_<Band>.md` "Format for the next entry" template, nested under a new `### Set S`
subsection) ready to append. Nothing else.
