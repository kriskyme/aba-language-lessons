# Academic Writing Lesson Generation Prompt (v6.4)

**Lesson type:** an **Academic Writing Lesson** is a fixed 2-day cycle (two 75-minute periods), one of a Set's
four positions, differentiated into band-scoped task Levels that each produce their own written output calibrated
against the Writing rows of `learningobjectives.csv`. What a Writing Set's lessons share is not an anchor text
but one **Scenario**, carried from grammar input on a practice object to a finished piece on a draft object
(0.1a); each task Level gets its own short
**Mentor Text** or **Mentor Essay** because the form of a Level's output changes, not just its depth. For
Intermediate, Advanced, and Proficient, one Scenario spans a **Module Pair** (two consecutive Sets, 8 lessons),
each Module contributing its own Grammar/Essay Focus to the same piece (Conventions §C; "THE MODULE PAIR"
below). Beginner keeps a single-Set, 4-lesson arc. The design was derived from a real grammar-in-context
textbook unit (`Writing Content Sample`) and an essay-writing chapter (`Academic Writing Essay Content Sample`).

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` (taxonomy, task Levels by band, Sets,
Module Pair, version codes) and `shared/Generation_Quality_Standards.md` (every modality-neutral pedagogical and
item-quality rule, plus the shared self-check) alongside it. This prompt states only what is true of a writing
lesson and points to those files for the rest. Conventions §E's CBI/TBLT framing applies with the Scenario as
the content vehicle, layered with a process-writing cycle (model, practice, draft, revise).

**Current version: v6.4.** For the dated version history and the reasoning behind each change, see `Changelog.md`.

**Inputs:** a Module and a Band at minimum (e.g. "Intermediate band, Module 5: Evaluating"); for
Intermediate/Advanced/Proficient, also which of the pair's two Modules and which Pair position (1-8); for
Beginner, which Set position (1-4). If an approved Module Lesson-Plan exists (`Generate_Module_Lesson_Plan_Prompt_*.md`),
take its Scenario, genre, each Module's Focus A/B pairing, and Mentor Ladder direction as given; this prompt then
writes one lesson's worth of content at that position. Without a plan, 0.9 applies in full for Pair position 1
(Beginner: Set position 1); every later position continues what came before it, never re-deriving the Scenario or
genre (position 5 introduces Module N+1's own Focus A/B but not a new Scenario).

**Output:** one Markdown lesson document. Directly under its H1, a metadata line:
`**Module:** ... | **Band:** ... | **Task Levels:** ... | **Version:** <Module>.<Set>.<Lesson>.<Version>` (Conventions
§G). `<Module>` and `<Lesson>` are scoped to the Module the lesson belongs to: Module N+1's Lesson 1 is
`<N+1>.1.1.0`, not a continuation of Module N's numbering. Its student packet is generated separately by the
Student Packet prompt immediately after (Style Guide §G).

**Provisional numbers:** 0.2's output-length targets are a first-pass estimate from the CSV's worked examples and
ESL paragraph-writing norms, not a verified corpus; recalibrate once real student output exists.

---

## SECTION 0: BAND AND OBJECTIVE CALIBRATION (READ AND APPLY BEFORE WRITING ANY LESSON)

### 0.1 Bands, task Levels, and the frame/composition regime boundary

Task Levels by band: Conventions §B. Each task Level cites its own Writing row (Quality Standards §A): pull the
objective for **every task Level in the band** (filter Level, Modality = Writing, Module) before writing that
Level's Mentor Text; never pull only the lower Level's row and scale it informally.

**Why Writing needs a different sharing model than Reading.** The CSV's Writing objectives fall into three
regimes, which are not the same kind of task at different depths:

- **Levels 1-3 (Guided Frame Composition):** the student's entire output is one or two words, spelled from sound,
  dropped into a provided frame the student does not author ("It is ___.", "I want ___ and ___, please.").
- **Levels 4-5 (Paragraph Composition):** the student authors an original single paragraph, with the required
  feature (a comparison, an implied attitude) growing more demanding across the two Levels.
- **Levels 6-8 (Essay Composition):** the student authors a genuine multi-paragraph essay (hook, thesis,
  topic-sentence-led body paragraphs, conclusion), not a longer paragraph; the required feature is realized at
  essay scale.

A single shared text cannot serve a student spelling one word into a frame and a student structuring a
five-paragraph essay. Every band except Beginner spans one of the two regime boundaries:

| Band | Task Levels | Regime mix |
|---|---|---|
| Beginner | 1, 2, 3 | Entirely Guided Frame Composition |
| Intermediate | 2, 3, 4, 5 | Spans the 3/4 boundary: 2-3 frame-based; 4-5 Paragraph Composition |
| Advanced | 4, 5, 6, 7 | Spans the 5/6 boundary: 4-5 Paragraph Composition; 6-7 Essay Composition |
| Proficient | 5, 6, 7, 8 | Spans the 5/6 boundary: 5 Paragraph Composition; 6-8 Essay Composition |

Design deliberately for whichever boundary a band spans (0.1a, and the dual-track guidance in the lesson cycle
section); never let a spanning band collapse into two disconnected tracks that share a topic. No band spans both
boundaries.

**0.1a The shared element is the Scenario.** One real-world writing situation, stimulus (the student's own belonging or an object in the room; a picture
only per Quality Standards §D8), and Module-aligned purpose for writing, identical across every task Level.
Both grammar focuses, the Mentor Ladder, the prewriting stimulus, the drafting task, and the editing checklist are
all built on it. Within any one activity, every task Level describes the same routine, person, or object.

**Two objects, one Scenario (Conventions §C).** The Scenario names a **practice object** and a **draft object**,
both the student's own belongings (a place or person where the Module's form calls for one), fixed once by the
plan. The draft object may be one of a short printed list of like things, four to eight (clothing: jacket,
hoodie, sweater, shirt, T-shirt, dress, scarf, hat), that the student circles at the start of each drafting
lesson, so no student is stuck without one; the lesson and its packet are then titled by the category ("My
Clothing"), and the Draft Word Bank is built for the category, not one item. The practice object carries grammar input, controlled practice, the frame rounds, and the Mentor Ladder from
Lesson 1 through Lesson 2 Day 1. Lesson 2 Day 2's prewriting introduces the draft object together with a **Draft
Word Bank** (the Set's Word Bank groups, refilled with words that fit the draft object; printed in Lesson 2's Day 2
unit and reprinted in every later lesson), and every later position writes about the draft object only: Lesson 3's
draft, Lesson 4's revision and hand-off, a Pair's Lessons 5-8. The draft is the student's first transfer of the
taught grammar to an object they did not drill on; the ladder stays on the practice object because it models
form, not content. Never draft about the practice object, and never change the draft object after Lesson 2 Day
2. The Closing Transfer Check's object (0.8) is a third, separate object, unused elsewhere in the Set.

**0.1b Leveled Mentor Ladder.** One short worked model per task Level, all on the practice object, each modeling
exactly that Level's output form and required feature (0.2): a **Mentor Text** at Levels 1-5 (a word, a frame, or
a paragraph), a **Mentor Essay** at Levels 6-8 (a complete essay, not a longer paragraph). Beginner has 3 Mentor
Texts; Intermediate 4 Mentor Texts; Advanced and Proficient 4 models mixing Texts and Essays. Present them
together, in Level order, as one visible ladder on Lesson 1 Day 2 once Focus A has been introduced, so a student
sees the model one step up and one step down; the paragraph-to-essay jump in kind is exactly what the ladder makes
visible. The ladder is also worked evidence for Level 7's self-revision requirement (0.2, 0.4a).

**The Module governs the writing purpose, not just the difficulty** (Quality Standards §A4):

- **Module 1 (Describing):** a person, object, place, or scene; not a sequence of events or a position.
- **Module 2 (Narrating):** a sequence of real or realistic past events, in order, with a stated or implied reason
  it mattered.
- **Module 3 (Explaining):** cause-and-effect or process, not a policy verdict.
- **Module 4 (Instructing):** ordered steps addressed to a reader who will follow them.
- **Module 5 (Evaluating):** a judgment against a stated or implied criterion.
- **Module 6 (Arguing):** a position with reasons and, from Level 4 up, an addressed counterpoint.
- **Module 7 (Transacting):** a message that accomplishes a real transactional goal (request, complaint, reschedule).
- **Module 8 (Socializing):** a social message calibrated to a relationship and occasion.

### 0.2 Output ceiling and required feature by level

Each entry gives the regime, output form, approximate length, grammar/vocabulary range, and the structural feature
the CSV row requires, which 0.3 verifies by name. Never import a higher regime's expectations into a lower-regime
Level or vice versa.

**Level 1 (A1) - Guided Frame Composition**
- Output: one word, sounded out and spelled from known letter-sound patterns, into a single provided frame ("big
  ___"), prompted by a picture.
- Grammar: none beyond the memorized frame. Vocabulary: concrete, high-frequency, phonics-decodable (CVC).
- Required feature: the word comes from the student sounding it out against the real object in front of them
  (or an embedded picture, per Quality Standards §D8), not from copying a printed list. This "genuine choice inside a constrained task" is Respectful Tiers at this Level (0.5).

**Level 2 (A2) - Guided Frame Composition**
- Output: one word spelled into a one-slot fixed frame that forms a complete sentence ("It is ___.").
- Grammar: the frame's single fixed structure. Vocabulary: concrete, high-frequency.
- Required feature: genuine object-prompted choice inside a full-sentence frame.

**Level 3 (B1) - Guided Frame Composition**
- Output: two words spelled into a two-slot frame ("It is ___ and ___." or a two-sentence sequence).
- Grammar: the frame's fixed structure with "and" built into the frame, not authored.
- Vocabulary: concrete, high-frequency; the two target words must not be synonyms.
- Required feature: the two slots require two genuinely distinct observations of the prompt ("big" and "red,"
  not "big" and "large"). This is where a lesson quietly becomes too easy.

**Level 4 (B1+) - Paragraph Composition floor**
- Output: a short original paragraph, roughly 3-6 sentences, approximately 40-90 words; the first Level with no
  provided frame.
- Grammar: simple present or past; one comparative structure; one "because" reason clause; the student's own
  connector; a compound sentence (and/but/so) where the Scenario calls for one.
- Vocabulary: concrete plus a small set of everyday abstract words.
- Required feature: exactly one comparison and one explicit, directly-stated reason. Never implicit at this Level.

**Level 5 (B2) - Paragraph Composition**
- Output: an extended paragraph, roughly 6-9 sentences, approximately 90-150 words.
- Grammar: mixed past/present as needed, coordination and light subordination, hedging and evaluative language (a
  bit, seems, tends to, at least, worth it).
- Vocabulary: everyday abstract, light topic-specific.
- Required feature: logically organized detail plus exactly one detail or word choice that implies an opinion,
  feeling, or reservation **without stating it directly**. Do not accept a paragraph that states the feeling
  outright. A light visible-revision pass is recommended (0.4a).

**Level 6 (B2+) - Essay Composition floor**
- Output: a five-paragraph essay: introduction (hook, connecting information, thesis), 2-3 body paragraphs each
  opening with its own topic sentence, and a conclusion that restates the thesis and closes with a suggestion,
  prediction, question, or opinion. Approximately 300-450 words. Not three interchangeable body paragraphs.
- Thesis: **direct** (names the essay's points of development). Hook: any of question, observation, scenario,
  quote, statistic.
- Grammar: complex sentences with sustained control; register-shifting cohesive devices (however, in fact, on the
  other hand, given that). Vocabulary: broader abstract and evaluative.
- Required feature: explicitly states why at least one feature or detail matters to a **specified reader** named in
  the Scenario, in one body paragraph or the conclusion, and shifts register or approach at least once to address
  that reader's stated concern. The Scenario must name that reader and concern.

**Level 7 (C1) - Essay Composition**
- Output: introduction, 3 body paragraphs, conclusion; approximately 450-650 words.
- Thesis: **indirect** (signals that points of development exist without naming them). Hook: a quote, statistic, or
  scenario/anecdote, not a plain question.
- Grammar: sophisticated cohesion (this suggests, what's more, admittedly), idiomatic and precise vocabulary,
  concession/counter structures ("while X is true, Y matters more").
- Required feature: at least one implication the reader must infer, built into the essay's selection and emphasis
  of detail across paragraphs (distinct from Level 5's single hedge word), and **visible evidence of unprompted
  self-revision** (0.4a) in at least one paragraph.

**Level 8 (C2) - Essay Composition**
- Output: 5-7 paragraphs (introduction, 4-5 body paragraphs in two clearly distinguishable sections, conclusion);
  approximately 650-900 words.
- Thesis: direct or indirect, but it must set up both audience-calibrated sections.
- Grammar/vocabulary: no ceiling.
- Required feature: deliberately calibrates tone, register, and approach at least twice for two distinct named
  audiences (one body-paragraph group per audience), both sections reaching the same underlying judgment, the
  conclusion resolving both. The Scenario must specify two distinct readers or stakes.

### 0.3 Self-check before finalizing

Run `shared/Generation_Quality_Standards.md` §F first. Then, for the Writing-specific rules in this prompt:

1. **Ceilings (0.2):** every task Level's Mentor Text or Essay and drafting target match that Level's own range
   (words, sentences, or paragraphs), counted, not a neighboring Level's?
2. **Regime (0.1):** Levels 1-3 have a fully provided frame with only the target word(s) student-authored; Levels
   4-5 have no frame and a single paragraph; Levels 6-8 have a genuine essay with hook, thesis, topic-sentence-led
   body paragraphs, and conclusion?
3. **Required feature (0.2):** each Level's exact feature is present in its model and demanded by its drafting and
   editing tasks; thesis kind (direct at 6, indirect at 7-8) and hook type correct at 6-8? A borrowed Level (e.g.
   Level 5 inside Advanced) still hits its full own-Level bar.
4. **Scenario (0.1a):** supplies what every Level needs: a named reader and concern for a band including Level 6;
   two distinct readers or stakes for a band including Level 8?
5. **Focus A/B (0.4):** anchored at the band's native Paragraph Composition row; Focus A equips the band's ladder
   (a comparative structure taught before a Level 4+ task needs a comparison); Focus B adds variety useful to the
   Scenario; any extension-down Level still gets its own row's content, folded into the same whole-class
   mini-lesson; Essay Focus A/B taught as real content for a band reaching Levels 6-8 (0.4c)?
6. **Respectful Tiers (0.5):** every Level, frame-based included, has one moment of genuine authorial choice?
7. **Module verb, Pair-aware:** for Pair positions 5-8 the shared piece still exercises Module N's verb only, and
   Module N+1's verb gets separate coverage in Lesson 8's Closing Transfer Check (0.8)?
8. **Editing (0.6):** the self-edit checklist names this lesson's focuses and required feature; Peer Editing
   scaffolds per Level and sits only where 0.6 places it?
9. **Self-revision (0.4a):** a concrete mechanism with a template at Levels 7-8, at both Pair positions 4 and 8 for
   Intermediate/Advanced/Proficient?
10. **Skill Spotlight, Pair-aware (0.8):** Lesson 5 adds Module N+1's Spotlight; Lesson 8's Closing Transfer Check
    covers both Modules' skill plus the separate Module N+1 verb task?
11. **Rotation (0.9):** different Focus pair, Scenario topic, and real-world writing form than the preceding
    Set/Pair, checked against the Rotation Log; Module N+1's Focus A/B distinct from Module N's?
12. **Content volume (0.4b):** each grammar/practice day has at least 3 distinct activities meeting the item
    minimums and reads as a full page when printed?
13. **Level 5 bridge (0.4c):** in Advanced and Proficient, Level 5 gets a light, receptive look at the shared model
    essay, positioned next to it, without raising Level 5's own output past one paragraph?
14. **Paired tier (0.4c):** each single-audience activity was considered for a lighter or heavier adjacent tier,
    added only where it closes a real gap, drawing only on grammar already taught by that point?
15. **Practice object vs draft object (0.1a):** positions 1-2 through Lesson 2 Day 1 and the Mentor Ladder use the
    practice object; Lesson 2 Day 2's prewriting introduces the draft object and its Draft Word Bank; every later
    position writes about the draft object only, with the Draft Word Bank reprinted; the Closing Transfer Check
    uses a third object?
16. **Self-contained across lessons; concrete prompts (Quality Standards §D9, §E6):** nothing this lesson asks
    for depends on Lesson 2's prewriting or Lesson 1's ladder being in hand (the carried draft excepted); the
    drafting lesson's plan is rebuilt in its own packet; at Beginner and Intermediate no printed question asks
    the student about their own plan, process, or what a model does?

If any check fails, rewrite before proceeding. Do not build the drafting and editing lessons on a Mentor Ladder
that fails its own ceilings.

### 0.4 Grammar-in-Context focus: a two-point cluster, selection, and bank

Every lesson has two grammar focuses: **Focus A**, a core verb-form or structural point, and **Focus B**, a
sentence-variety or cohesion point that pairs with it, mirroring the sample chapters (a verb-form point, then a
sentence-structure point, before the paragraph task). Two grammar lessons (Lesson 1 and Lesson 2 Day 1) let a
lesson pair them without crowding both into one period. Both are chosen top-down from the Scenario and the
band's task ladder, not from a fixed syllabus.

**Grammar Focus Bank by Level** (a starting bank; expand by adding rows):

| Level | Focus A: core form | Focus B: sentence variety / cohesion | Why this Level needs it |
|---|---|---|---|
| 1 | Letter-sound spelling patterns (CVC); the frame is pre-built | n/a (frame regime, single word) | Output is a spelled word |
| 2 | Simple present or simple past, single fixed form | n/a (single slot) | One-slot frame needs one form |
| 3 | Simple present -s form spelling rules (-s/-es/-ies) | "and" inside a two-slot frame only | Two-slot frame; first exposure to the full -s paradigm |
| 4 | Simple present/past control; comparative adjectives (-er/more); "because" plus since/as/given that as richer alternatives | Simple vs. compound sentences (and/but/so), including comma placement | Required feature is one comparison plus one explicit reason |
| 5 | Consistent tense control across a paragraph; hedging/evaluative vocabulary | Complex sentences with a contrast/concession subordinator (although, even though, but) | Implied attitude is often a hedge inside a concession clause |
| 6 | Register-shifting cohesive devices (however, in fact, on the other hand, given that) | Complex sentences with a time, causal, or concessive clause fitting the register shift | The shift for a named reader often lands at a clause boundary |
| 7 | Sophisticated cohesion (this suggests, what's more, admittedly); self-revision language | Concession/counter structures; varied subordination across the piece | Embedded implication plus visible self-revision |
| 8 | Multi-audience calibration devices (deliberate register markers) | Sentence-length and structure variation between the two audience sections | Calibrating tone for two named audiences |

**Alternate rows for a Module Pair's second Module (pending).** The bank gives one Focus A/B per native Level.
Module N+1 needs a genuinely different Focus A/B at the same row (0.9's within-pair rule). Until an "Alternate"
column is authored (tracked in `Index.md`), choose Module N+1's pair by hand from adjacent grammar content fitting
its own writing purpose, checked for genuine distinctness.

**Reason-connector richness.** Teach Level 4's "because" alongside since, as, and given that, each with its own
example, even though "because" alone satisfies the required feature: a single-word grammar point reads as thin,
and when Level 4's row folds into a higher band as light content it would otherwise read as identical to the band
Level 4 is native to. "Given that" also gives essay-regime students a name for Level 6's own device.

**Row selection when a band spans rows.** Anchor Focus A/B at the row of the band's own **native** Paragraph
Composition Level, not automatically its lowest Paragraph Composition Level:
- Intermediate: Level 4 is native, so anchor there.
- Advanced: Level 4 is an extension-down accommodation; anchor at Level 5's row, and teach Level 4's own row as
  additional content sized to exactly its required feature (0.2), folded into the same session.
- Proficient: Level 5 is its only Paragraph Composition Level and an extension-down one with no native sibling;
  Grammar Focus A/B is non-centerpiece content for this band (0.4c is the centerpiece) and Level 5's row is
  taught as its own light content.
Focus B follows the same row as Focus A.

**Grammar is a teaching moment, not a practice moment: never split it for a subset of students.** Whichever
Levels contribute a row, the teacher delivers all of it to the whole room in one sitting. An extension-down Level's
row is additional content inside that session, not a separately timed, labeled, or printed "warm-up." A printed
packet has one combined Grammar box per mini-lesson. Differentiation lives entirely downstream, in the practice
activities and the drafting task. This holds for a band reaching Essay Composition: Levels 6-8 still get the
chosen Focus A/B row as sentence-level content (in Advanced, Level 5's row: tense control, hedging, concession),
just not as their structural centerpiece (0.4c).

**Controlled-practice activity types** (from the sample's activity shapes; use 2-3 per grammar day, matched to
that day's focus):
- **Analyzing/classifying:** identify which sentences use the target structure correctly, or classify by function
  (adapt the categories to the Module).
- **Fill-in-the-blank on a model paragraph** on the Scenario's topic with the target form blanked out; a natural
  home for a frame-regime Mentor Text variant.
- **Editing a paragraph** containing a fixed number of errors in the target structure. Always state the exact
  number, and count it yourself before finalizing.
- **Combining/expanding sentences** into one using the target connector; Focus B's natural home.
- **Choosing between confusable structures** (the sample's "they are / there are"; pick the analogous pair for
  this lesson's focus).
- **Writing original sentences with target items**, one per item; the bridge into the task-ladder warm-up and
  drafting.

### 0.4a Making self-revision checkable, not just claimed

Levels 7 and 8 require "evidence of unprompted self-revision"; Level 5 (and, time allowing, 4 and 6) benefits
from the same practice. "Now revise your work" produces no checkable evidence. Use one of these, and include its
template in the revision lesson's materials explicitly:
- **Visible strikethrough/insertion:** revise on the same page, crossing out rather than erasing, so original and
  revision sit side by side.
- **Two-column before/after:** "what I first wrote" / "what I changed it to, and why," for the one or two
  sentences that changed most.
- **Revision partner note:** a peer names one specific place they were confused or wanted more; the revision
  responds to that note (doubles as part of Peer Editing, 0.6).

### 0.4b Content volume per day

A printed grammar or practice day must read as a full worksheet page and genuinely occupy 75 minutes, not just
add up to 75 in the timing column. Minimums for every generated lesson:
- **Item counts.** A fill-in-the-blank, classify, choose-the-form, or combine activity: at least 6-8 items. A
  confusable-pair drill: at least 6. An editing paragraph: at least 6-8 sentences with 6-8 verified errors.
- **Activities per grammar/practice day** (Lessons 1-2, both days): at least 3 distinct activities from the 0.4
  bank, not the same one or two types reused.
- **Frame-regime parity:** Levels 1-3 get more rounds on their own and classmates' belongings, not one, so they have as much printed material
  as their composition-regime classmates.
- **Essay-regime parity:** Levels 6-8's Essay Focus track gets the same standard in its own shapes: a full short
  model essay (not a paragraph) for essay analysis, at least 2 candidate hooks per hook activity, both a general
  and a specific outline.
- **Drafting and revision days are exempt** from item-count minimums (Lessons 3-4, and 7-8 in a Pair); they are
  governed by 0.2's targets and 0.6's checklists.
- **Check before finalizing:** lay out each grammar/practice day as it would print; if it looks like a handout with
  room to spare, add another activity from the bank rather than padding with filler.

### 0.4c Essay Focus: structure content for Levels 6-8

Grammar Focus A/B is sentence-level and necessary but not sufficient for Levels 6-8. They need **Essay Focus A**
(essay structure and thesis construction) and **Essay Focus B** (paragraph-internal and cross-paragraph cohesion),
drawn from `Academic Writing Essay Content Sample`. Where a band includes Levels 6-8, these run as a parallel
track through Lessons 1-2: composition-regime Levels 4-5 have Grammar Focus A/B as their centerpiece; essay-regime
Levels 6-8 have Essay Focus A/B as theirs, with Grammar Focus A/B folded in as lighter sentence craft (the mirror
of how frame-regime Levels get a light Grammar warm-up inside a Paragraph Composition band).

**Essay Focus Bank by Level:**

| Level | Essay Focus A: structure | Essay Focus B: cohesion | Why this Level needs it |
|---|---|---|---|
| 6 | Five-paragraph shape; direct thesis construction; hook types (question, observation, scenario, quote, statistic) | Topic sentence plus supporting sentences within a body paragraph; general outlining (main points) | A named reader and register shift need a body paragraph and conclusion to land in, and a thesis that sets them up |
| 7 | Indirect thesis construction | Specific outlining (down to supporting detail); combining sentences for cohesion within and across paragraphs | Embedded implication is built through selection and emphasis of detail across paragraphs, which a specific outline plans |
| 8 | Two-section organization (one paragraph group per audience); a thesis setting up both | Deliberate structural variation between the sections as a rhetorical device | Two-audience calibration needs two genuinely distinguishable paragraph groups |

**Row selection:** anchor Essay Focus A/B at Level 6's row (always the band's lowest Essay Composition Level);
Level 7 (and 8 in Proficient) receive their row's content as an additive extension folded into the same sessions.

**Bridging the regime gap at Level 5.** In Advanced and Proficient, Level 5 sits one Level below a jump from one
paragraph to a full essay. Give Level 5 a light, receptive version of the essay-analysis activity on the same
shared model essay the essay Levels analyze that day (find and underline one body paragraph's topic sentence, then
state in their own words what it is about): a few minutes of reading and one short response, positioned next to
the model essay, separate from Level 5's own paragraph-focused grammar activities. Level 5's own required output
stays a single paragraph. This is receptive exposure, not an extension-down Level's own required row.

**Pair a single-audience activity with a lighter or heavier tier for the adjacent Level where a natural one
exists.** Wherever a practice activity serves only part of the band's range, consider a lighter receptive version
for the Level below (identify rather than produce) or a heavier combining version for the Level above (stack two
already-taught points in one sentence). Build any such tier only from content already taught by that point in the
lesson's own sequence; never reach into a later lesson's grammar point. Add a paired tier where it closes a real
engagement gap, not mechanically on every task. Teaching content precedes the practice that depends on it, in the
lesson's own day-by-day order; being modeled inside a Mentor Essay does not count as taught (Quality Standards
§D5).

**Essay-regime activity types** (from the essay sample; use alongside the sentence-level types in 0.4 on the days
that carry Essay Focus A/B):
- **Essay analysis:** a short original model essay built for this Scenario; students identify its purpose,
  paragraph count, thesis, and each body paragraph's topic sentence.
- **Hook-writing practice:** the connecting information and thesis of a short essay without its hook; students
  write one or two candidate hooks and compare effectiveness.
- **Thesis identify/rewrite:** identify a thesis as direct or indirect, then rewrite it as the other kind.
- **Outlining:** a general outline (main points), then a specific outline (supporting detail) for the same essay,
  side by side.

### 0.5 Respectful Tiers for writing

Quality Standards §B applies. What it concretely means here: for Levels 1-3, the one word they supply is a genuine
choice (which word fits their own object), not a foregone answer copyable off the board (0.2's required-feature rows).
For Levels 4+, the lower Level's required feature (a comparison at Level 4) is a real accomplishment inside its own
scaffolding: a genuinely interesting comparison with real stakes, not a trivial one. If the lowest Level's student
would feel they did the easy part while everyone else did the real writing, strengthen that Level's task (a better
object to describe, a more interesting two-slot choice, a comparison that matters).

**Foundation Support** in this cycle (Quality Standards §D8: nothing the teacher must make): matching a printed Word
Bank word to the student's own object (select, don't spell), tracing a pre-written word
with a meaning-check question, or teacher-scribed dictation where the student says the word and the teacher writes
it, checking afterward that the student can point to which word is which. Alongside the lowest task Level, not in
place of it.

### 0.6 Editing checklist and Peer Editing, by regime

**Composition-regime Levels (4-8), self-edit checklist (Lesson 3 Day 2, and Lesson 4 Day 1):** a short checklist
specific to the lesson's two focuses and required feature, in the sample's own pattern. Template to adapt:
- Every sentence has a subject and a verb, and matches Focus A's target form correctly.
- At least one sentence uses Focus B's structure correctly.
- The required feature (named explicitly: "one comparison and one stated reason" / "one detail that implies my
  opinion without stating it" / "a register shift for [the named reader]") is present and locatable.
- Punctuation and capitalization are correct, including comma use in compound or complex sentences.
- (Levels 7-8 required; 4-6 recommended) The self-revision evidence (0.4a) is present and visible.

**Essay-regime Levels (6-8) add:**
- The essay has a real hook of this Level's type, not a flat statement of the thesis.
- The thesis is present at the end of the introduction and is the correct kind (direct at 6, indirect at 7-8).
- Every body paragraph opens with a topic sentence stating its own main point.
- The conclusion restates the thesis and introduces no new information.
- (Level 8) Both audience sections are present and genuinely distinct in register and approach.

**Frame-regime Levels (1-3):** replace the written checklist with a short oral self-check ("does your word
match your object? read your sentence to a partner, does it make sense?").

**Peer Editing:** exchange work with a partner using a short Peer Editing Form with 2-3 questions tied to this
lesson's focuses and required feature, plus one specific compliment and one specific suggestion. A Level 1-3
student's peer edit is an oral partner check (read your sentence aloud; does your partner understand the word?).
Essay-regime Levels add structure questions: can your partner identify the hook, the thesis, and each topic
sentence unaided; for Levels 7-8, what do they think the implication or the two audiences' concerns are, checked
against the writer's intent. **Timing:** Beginner runs Peer Editing at Lesson 4 Day 1. Intermediate/Advanced/
Proficient run it once, at Lesson 8 Day 1 (Pair position 8), covering both Modules' focuses; it is not run at Pair
position 4, since the piece is not yet complete.

**Self-revision timing:** Beginner's hard Level 7-8 requirement (0.4a) applies at Lesson 4 Day 1. In a Module Pair
it applies **twice**: Pair position 4 (Module N's tools, before hand-off) and Pair position 8 (Module N+1's tools,
before publishing). This is deliberately more revision practice than the single-Set model. Levels 4-6 are
encouraged to do the same at both points.

### 0.7 Board-dependent moments: where they fit in a Writing lesson

The rule (Quality Standards §D4) is shared. Typical placements, one per day:
- **Lesson 1 Day 1:** co-construct one new example sentence live, on a fresh prompt, using Focus A.
- **Lesson 1 Day 2:** as the class examines the Mentor Ladder, co-construct a live "what changes at each Level"
  board from student observations.
- **Lesson 2 Day 1:** co-construct one new example sentence live using Focus B.
- **Lesson 2 Day 2:** synthesize prewriting ideas from every task Level into one shared idea board no single
  handout contains.
- **Lesson 3 Day 1:** a running "strong sentence" board populated as students share a line from their draft.
- **Lesson 3 Day 2:** return to and add to that board with newly completed lines.
- **Lesson 4 Day 1:** a before/after board from two or three volunteered revision examples (0.4a).
- **Lesson 4 Day 2:** capture Closing Transfer Check instances live as students share.
Lessons 5-8 mirror these with Module N+1's focus (a "what Module N+1 adds at each Level" board, a revision-plan
board, a "strong revision" board).

### 0.8 Skill Spotlight and Closing Transfer Check in a Writing lesson

The rules (Quality Standards §D1-D3) are shared. Writing-specific placement:
- **Skill Spotlight: Lesson 1 Day 1, during Focus A's mini-lesson,** tied to the Module's verb and the specific
  required feature ("Today we're practicing describing something by comparing it to something else and giving a
  real reason for the comparison"). For a band reaching Essay Composition, add a second sentence naming what
  Levels 6-8 are additionally building toward (structuring that comparison as a full essay).
- **Closing Transfer Check: Lesson 4 Day 2** (Beginner's finale; a Pair's position 4 hand-off): every student
  applies the spotlighted skill to something new (not their Scenario piece), out loud or on a small card; a few
  cold-called. Demonstration, not self-report.
- **Module Pair only, a second Spotlight and Check at Lessons 5 and 8:** Lesson 5's Spotlight (Day 1, during Module
  N+1's Focus A) names Module N+1's transferable skill alongside a one-line reminder of Module N's. Lesson 8's
  Closing Transfer Check covers **both** Modules' combined skill in one instance, **plus** one short, separate task
  exercising Module N+1's own CSV verb on a small new prompt, not the shared essay; since the essay's genre stays
  Module N's throughout ("THE MODULE PAIR"), this second task is what gives Module N+1's objective genuine
  coverage.

### 0.9 Rotation

**Applies in full only when generating Pair position 1 (Beginner: Set position 1) without an approved plan.** Do
not repeat the same grammar focus pair, Scenario topic, or real-world writing form (table below) as the
immediately preceding Set or Pair for the same class, and avoid clustering the same grammar focus across nearby
Modules even when not consecutive (comparatives as Focus A for a Describing pair and an Evaluating pair back to
back). The check covers both the practice object and the draft object. Positions 2-4 continue position 1's
Scenario and Focus without re-running the check.

**Within-pair non-repetition (Intermediate/Advanced/Proficient):** Module N+1's Focus A/B (Pair position 5) must
not repeat Module N's from positions 1-2 of the same pair; a same-plan check, stronger than adjacency. If both
Modules' native Levels map to the same bank row, choose Module N+1's by hand until an Alternate column exists
(0.4).

**Rotation Log mechanics:** Conventions §F (read `Rotation_Log.md` and every `Rotation_Log_<Band>.md` before an
unplanned position 1; Writing's cross-Band check spans every Band's file, not just the one being generated for;
append one row per approved lesson under its Set's subsection). A lesson generated but never logged breaks the
check for every Set after it.

**Module-to-real-world-form mapping** (match formatting to the form). Levels 1-5 use the middle column; Levels 6-8
use the essay type where one is mapped, and where a Module has none yet, continue as an extended paragraph rather
than forcing a bad-fit essay type:

| Module | Real-world writing form (Levels 1-5) | Formatting convention | Essay type (Levels 6-8) |
|---|---|---|---|
| 1: Describing | Descriptive paragraph (a place, person, or object) | Continuous prose | Comparison essay (two instances of the described thing) |
| 2: Narrating | Personal narrative / journal entry | Chronological prose, time connectors | Reaction essay (narrate, then reflect); the loosest mapping, revisit once tested |
| 3: Explaining | Explainer paragraph / how-something-works note | Cause-effect structure, light process language | Cause-effect essay |
| 4: Instructing | Instruction set / how-to note | Numbered or sequenced steps, imperatives | Not yet mapped; extended paragraph |
| 5: Evaluating | Review or opinion paragraph | Criterion stated early, verdict signaled clearly | Problem-solution essay |
| 6: Arguing | Position paragraph / short persuasive note | Claim, reason(s), addressed counterpoint from Level 4 up | Argument essay |
| 7: Transacting | Email or message handling a request or problem | Greeting/sign-off conventions, clear stated ask | Not yet mapped; extended paragraph |
| 8: Socializing | Card, note, or social message | Tone matched to occasion, relationship-appropriate register | Not yet mapped; extended paragraph |

---

## THE MODULE PAIR: A FIXED 4-LESSON ARC (BEGINNER) OR 8-LESSON ARC ACROSS TWO MODULES (ALL OTHER BANDS)

This prompt generates **one 2-day lesson per run**; run it once per position against the same approved plan.
Beginner's 4 lessons in one Set share one Scenario from grammar input (practice object) through a finished,
published piece (draft object, 0.1a). Intermediate, Advanced, and Proficient pair two consecutive Modules (1-2,
3-4, 5-6, 7-8) so one Scenario/essay, on the draft object, spans both Modules' Sets, 8 lessons, each Module contributing its own, different Grammar/Essay Focus (Conventions
§C). Each Module still keeps its own ordinary 4-lesson Set, folder, and version codes; **Pair position** (1-8) is
the lesson's place in the arc, **Set position** (1-4, restarting per Module) is which of the Module's own lessons
it is.

| Pair position | Module | Set position | Content role |
|---|---|---|---|
| 1 | N | 1 | Grammar Focus A: input, modeling, deeper practice; Mentor Ladder |
| 2 | N | 2 | Grammar Focus B, Essay Focus A/B (where applicable); Day 2 prewriting introduces the draft object and Draft Word Bank |
| 3 | N | 3 | Drafting on the draft object, parts 1-2 (a complete opening-through-conclusion draft), self-edit |
| 4 | N | 4 | **Hard self-revision** (Module N's tools), draft completion, hand-off (not published). **Beginner: peer editing, revision, publishing, Closing Transfer Check; the Set's finale.** |
| 5 | N+1 | 1 | Re-engagement (re-read own draft; short recap, no fresh hook) plus Module N+1's own Grammar Focus A: input, modeling; Mentor Ladder second look |
| 6 | N+1 | 2 | Module N+1's Grammar Focus B, Essay Focus A/B (where applicable); revision-planning against the existing draft (replaces prewriting) |
| 7 | N+1 | 3 | Revision and expansion drafting, parts 1-2, applying Module N+1's focus into the existing draft; merged self-edit checklist |
| 8 | N+1 | 4 | Peer editing (both Modules), **hard self-revision** (Module N+1's tools), publishing, Closing Transfer Check for both skills plus Module N+1's verb |

Key rules:
- **Genre, Scenario (practice object and draft object), and essay type are fixed once by Module N's mapping (0.9)
  and inherited unchanged by Module N+1.** The shared piece stays one genre and one draft object throughout.
- **Position 5 does not re-derive the Scenario or genre;** it re-reads Module N's draft and gives a short recap
  (purpose, reader, what is already written), then introduces Module N+1's Focus A as genuinely new content.
- **Module N+1's own CSV verb is covered by Lesson 8's separate Closing Transfer Check task (0.8),** not by the
  shared essay.
- **Hard self-revision sits at both positions 4 and 8;** peer editing and publishing happen only at position 8
  (0.6). Position 4 completes and self-revises the draft but does not publish it or run a Peer Editing exchange.
- **Module N+1's Focus A/B is genuinely different from Module N's** (0.9; 0.4's pending Alternate column).
- Positions 3-4 continue positions 1-2's content; positions 6-8 continue what position 5 established.

## TWO-DAY LESSON CYCLE: STRUCTURE AND DETAILED FLOW

Each lesson is two 75-minute days of three phases; the phase names and minute allocations below are the pacing
diagram the generated lesson opens each day with (Quality Standards §E3). Board-dependent moments per 0.7; item
counts per 0.4b; every item per Quality Standards §C.

### Essay-regime dual-track guidance (Advanced, Proficient)

The flow below is written for a Paragraph Composition band. Where a band includes Levels 6-8, run two tracks in
parallel through Lessons 1-2, the same move a Paragraph Composition band makes for its frame-regime Levels, one
regime higher:
- **Levels 4-5 (where present):** follow the flow exactly, Grammar Focus A/B as centerpiece.
- **Levels 6-8:** the same two lessons on Essay Focus A/B (0.4c) as centerpiece: Lesson 1 covers essay structure,
  hook types, and direct-thesis construction (Level 6's row) plus the Level 7/8 extension; Lesson 2 Day 1 covers
  topic sentences, outlining, and cohesion (Essay Focus B); Lesson 2 Day 2's warm-up and prewriting produce an
  essay outline rather than a paragraph plan. Grammar Focus A/B runs inside the same days as lighter sentence
  craft.
- **Mentor Ladder walkthrough (Lesson 1 Day 2 Phase 3) and prewriting share (Lesson 2 Day 2 Phase 3)** present
  every Level together; the Mentor Essays sit at the top of the same ladder as the Mentor Texts.
- **Lesson 3:** Levels 6-8 draft the introduction and first body paragraph on Day 1, the remaining body
  paragraph(s) and conclusion on Day 2. Provisional pacing, unchecked against a real class; a dedicated outlining
  lesson may be needed later.
- **Lesson 4 (and 8):** use 0.6's essay-specific checklist and Peer Editing additions.

### Lesson 1, Day 1: Grammar Focus A, Input and Modeling

_Phase 1: Hook, Skill Spotlight (15 min)_
- A short hook tied to the Scenario (two students' belongings held up and compared, a real situation, a short
  prompt; never a prop the teacher brings, Quality Standards §D8), pitched near the band's lower
  task Level. Skill Spotlight (0.8).

_Phase 2: Focus A mini-lesson: rule and examples (30 min)_
- Present Focus A (0.4) with a rule statement and 2-3 examples in the sample's grammar-box style. Fold in a brief
  frame-regime warm-up for Levels 1-3 where present (the frame sentence and one elicited example word).

_Phase 3: Controlled practice A, part 1 (30 min)_
- 1-2 activities from the 0.4 bank (analyzing/classifying or fill-in-the-blank) matched to Focus A.

### Lesson 1, Day 2: Grammar Focus A, Deeper Practice and the Mentor Ladder

_Phase 1: Editing a paragraph on Focus A (20 min)_
- A short paragraph with a stated, verified number of Focus A errors.

_Phase 2: Frame warm-up / original sentences with Focus A (25 min)_
- Levels 1-3 (where present): guided frame completion on the student's own object. Levels 4+: original sentences using
  Focus A, one per target item.

_Phase 3: Leveled Mentor Ladder walkthrough (30 min)_
- Present the ladder (0.1b) in Level order on the shared Scenario, naming what makes each model that Level's
  version. Students identify their own Level's model and the one directly above it.

### Lesson 2, Day 1: Grammar Focus B, Sentence Variety

_Phase 1: Focus B mini-lesson: rule and examples (20 min)_
- Present Focus B (0.4) the same way, tied explicitly to how it pairs with Focus A ("yesterday you learned to
  compare two things; today we'll join that comparison to its reason in one compound sentence").

_Phase 2: Controlled practice B (30 min)_
- Identifying sentence types and/or combining short sentences with Focus B's structure.

_Phase 3: Confusable-pair drill and mixed editing (25 min)_
- A forced-choice confusable pair relevant to this lesson ("it's / its" for an object description). A short
  paragraph mixing Focus A and B errors, stated and verified count.

### Lesson 2, Day 2: Task-Ladder Practice and Prewriting

_Phase 1: Frame practice round 2 / required-feature warm-up (25 min)_
- Levels 1-3: a second guided frame round on the Scenario, choosing genuinely distinct observations (0.2 Level 3).
  Levels 4+: a short warm-up targeting only the required feature (one comparison sentence and one because-sentence;
  one sentence with a specific detail a partner tests for the implied attitude).

_Phase 2: Prewriting for the Scenario, differentiated by task Level (30 min)_
- Introduce the draft object (0.1a): students take out their own, and the Draft Word Bank is presented, the same
  groups as the Set's Word Bank refilled for this object. All Levels generate ideas about the draft object by
  whatever means fits: labeling their own object or a drawing of it (1-3), an idea list or organizer (4-6), a
  developed outline naming the intended implication, register shift, or self-revision target (7-8). This
  prewriting is rehearsal: nothing in Lesson 3 depends on it (Quality Standards §D9), so no task here says
  "next time" or "for your draft.

_Phase 3: Prewriting share and board synthesis (20 min)_
- A few students from each Level share one idea or detail.

### Lesson 3, Day 1: Drafting, Part 1

_Phase 1: Quick plan (10 min)_
- Students pick the draft object from the printed list, circle it, and put the real thing on the desk. Then a
  minimal plan built inside this packet, with no reference to Lesson 2's products or Lesson 1's ladder (Quality
  Standards §D9): Levels 1-3 write three Draft Word Bank words that fit the object; Levels 4-6 name one thing to
  compare it to and one real reason, or list ideas; Levels 7-8 outline. The Draft Word Bank is reprinted before
  it. At Beginner and Intermediate the packet carries no questions here, only these actions (§E6); the
  teacher's circulation check (does each plan already carry its Level's required feature?) stays in the
  Markdown.

_Phase 2: Independent/guided drafting, opening and body (50 min)_
- Frame-regime Levels complete their frame(s) on the draft object (not the practice frames), the teacher
  circulating to hear each student sound out their word. Composition-regime Levels draft the opening and body
  toward 0.2's targets; the draft need not be finished today. Circulation checks the required feature is present
  in progress, not only at the end.

_Phase 3: Mid-draft share-out (15 min)_
- A few students share one sentence from their draft.

### Lesson 3, Day 2: Drafting, Part 2 and Self-Edit

_Phase 1: Complete the draft (30 min)_ to the Level's full 0.2 target. Students count sentences only; the word
range is the teacher's circulation check and never reaches the packet (Style Guide §E).

_Phase 2: Self-edit checklist pass (25 min)_ against the regime's checklist (0.6).

_Phase 3: Share-out / final line check (20 min)_: a read-aloud or partner check of the closing line or frame.

### Lesson 4, Day 1: Self-Revision and Draft Completion

_Phase 1: Self-edit checklist pass, Module N's own focus and feature (25 min)_

_Phase 2: Self-revision time, including self-revision evidence (35 min)_
- Revise from the checklist pass. Levels 7-8 must produce one of 0.4a's concrete artifacts; Levels 4-6 encouraged.
  **Beginner:** open with the Peer Editing exchange (0.6) and revise from both the checklist and the partner's
  feedback. **Module Pair:** no Peer Editing here; it happens at position 8.

_Phase 3: Quick revision share (15 min)_

### Lesson 4, Day 2: Draft Hand-off (or Publishing) and Closing Transfer Check

_Phase 1: Final polish / proofread pass, complete the draft to full length (20 min)_

_Phase 2 (Module Pair): Hand-off note (30 min)_
- A short note, differentiated by regime, recording what this Module's focus added and that the piece now moves
  to Module N+1's Set for revision, expansion, peer editing, and publishing. At Levels 1-5 the note is concrete
  actions (Quality Standards §E6): mark each taught feature on the draft (circle the comparative, box the reason
  word, star the compound sentence) and finish a printed stem ("Next time I will add ___"); Level 5 also copies
  its implied-attitude sentence and finishes "I want my reader to guess ___" so the intention travels with the
  draft. Levels 6-8 may write the note as prose. **Do not publish or share the piece here.**

_Phase 2 (Beginner): Publish/share (30 min)_
- A short gallery walk, read-aloud, or class posting; the piece is genuinely finished.

_Phase 3: Closing Transfer Check (25 min)_ (0.8; Module N's skill at this position).

### Lessons 5-8 (Module Pair only): Module N+1's Set

Not generated for Beginner. Lessons 5-8 run Lessons 1-4's structure (same phases, same minutes) with Module N+1's
own Focus A/B and these substitutions, applied to the existing draft on the draft object rather than a new piece:

- **Lesson 5 Day 1 Phase 1** is re-engagement, not a hook: students re-read their Module N draft; a short recap of
  the Scenario's purpose and named reader and what the piece already accomplishes; Module N+1's Skill Spotlight
  alongside a one-line reminder of Module N's (0.8). Phases 2-3 teach Module N+1's Focus A.
- **Lesson 5 Day 2 Phase 3** is a Mentor Ladder **second look**: the same ladder, now asking what Module N+1's focus
  would add to each Level's already-complete model (a before/after framing, not a new ladder).
- **Lesson 6 Day 1** teaches Module N+1's Focus B with the same activity shapes.
- **Lesson 6 Day 2 Phase 1's** warm-up targets Module N+1's required feature on a sentence from the student's own
  draft; **Phase 2** replaces prewriting with **annotating the existing draft** for where Module N+1's focus will be
  added, expanded, or strengthened; Phase 3 shares planned revisions.
- **Lesson 7** is revision and expansion drafting: Day 1 applies Module N+1's focus into the opening and body
  (with a "strong revision" board), Day 2 completes the pass and runs the **merged self-edit checklist** covering
  both Modules' focuses and required features (0.6).
- **Lesson 8 Day 1 Phase 1** is the **Peer Editing exchange** covering both Modules (0.6); Phase 2 is hard
  self-revision with Module N+1's tools (0.4a artifact required at Levels 7-8).
- **Lesson 8 Day 2 Phase 2** is **Publish/share** (the piece is genuinely finished now); **Phase 3's** Closing
  Transfer Check covers both Modules' combined skill plus the separate Module N+1 verb task (0.8).

### Style and Formatting Constraints

Quality Standards §E applies (no em-dashes, a pacing diagram per day, the metadata line). Writing-specific:
- **Mentor Ladder labeled:** every Mentor Text or Essay carries its task Level number, visible at a glance.
- **Regime language:** describe a Level's work as "frame-based," "single-paragraph," or "essay," never an internal
  label.
- **Focus labeling:** label which content belongs to Focus A vs. Focus B (and Essay Focus A vs. B for a band
  reaching Levels 6-8) so a teacher can tell which point an activity reinforces and for which track.
- **Band calibration is non-negotiable:** both an over-dense Level 6 task pushed into a Level 4 slot and a thin task
  that meets a word-count floor without requiring the Level's actual feature are miscalibrations.
