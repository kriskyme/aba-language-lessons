# Academic Writing Lesson Generation Prompt (v4)

**Lesson type:** this prompt generates one **Academic Writing Lesson**, the Writing-modality counterpart to the
existing Passage Reading Lesson. Passage Reading and Academic Writing now share the same lesson shape: a fixed
**2-day cycle**, 4 lessons per Set. What's genuinely different is what those 4 lessons share: a Reading Set's 4
lessons each get an independent anchor text, while an Academic Writing Set's 4 lessons share **one** Scenario
carried from grammar input through a finished, published piece, differentiated into band-scoped task Levels that
each produce their own written output, calibrated against the Writing-modality rows of `learningobjectives.csv`.
See "The Four-Lesson Set" section below for exactly how that arc is fixed across the 4 lesson positions. It was
written by working backward from the sample textbook unit the user supplied (`Writing Content Sample`, two full
grammar-in-context chapters from an academic ESL writing textbook: one on the simple present, articles, and
simple/compound sentences; one on the simple past, adverbs of manner, and complex sentences with time clauses,
each chapter ending in a guided paragraph and peer edit) and forward from the existing Passage Reading Lesson
Generation Prompt v2.5.

**Moved to a shared, cross-modality doc:** paste `shared/Program_Conventions.md` alongside this prompt when
generating. §E's CBI/TBLT framework applies here with the Scenario as the content vehicle: writing practice
should grow out of a real scenario and a real reason to write, not an abstract grammar drill for its own sake.
Layered on top of that is a **process-writing** cycle (model, practice, draft, revise) borrowed
directly from the sample's own structure: two grammar boxes with examples, controlled practice on each, sentence-
level editing and combining work, a scaffolded paragraph-writing task with a numbered checklist, and a
peer-editing exchange at the end. Section 0 below exists for the same reason it exists in Reading: to keep every
generated lesson calibrated against real objectives and real output-length targets instead of an invented
difficulty curve.

**Relationship to Passage Reading:** this prompt shares the Band table, the Level 1-8 scale,
`learningobjectives.csv`, and now the 2-day/4-lessons-per-Set lesson shape with Passage Reading, and borrows
several proven mechanisms (Skill Spotlight, Closing Transfer Check, board-dependent moments, Respectful Tiers, no
em-dashes). It still deliberately diverges from Reading in one structural way, explained in Section 0.1 and "The
Four-Lesson Set" below: instead of one shared anchor text with per-Level tasks built on top of it, each task
Level gets its own short **Mentor Text**, and the 4 lessons in a Set share one Scenario/piece of writing rather
than 4 independent topics, because in Writing (unlike Reading) the actual form of a Level's output changes, not
just the depth of engagement with a shared text.

**Provisional status:** unlike Reading's Section 0.2, whose word-count ceilings are anchored to a real corpus
(British Council LearnEnglish, Cambridge exam specs), the output-length targets in Section 0.2 below are a
first-pass estimate built from the CSV's own worked examples and general ESL paragraph-writing norms, not a
verified external corpus. Treat them as a starting point to recalibrate once real generated lessons and real
student output exist to check them against, the same way Reading's Level 3 ceiling was corrected after two
separate rounds of coming in short. Splitting the old 8-day-in-one-document model into 4 separate 2-day lessons
does not raise these ceilings; the CSV still governs the size of the student product, and the Set's 8
instructional days buy depth of instruction and revision time, not a bigger target.

**Current version: v4.** For the full dated version history and the reasoning behind each change, see
`Changelog.md`. (v4 restructures the lesson from one 8-day document into 4 separate 2-day lesson documents per
Set, matching Reading's/Listening-Speaking's lesson shape - see `shared/Program_Conventions.md` §C and
`Changelog.md`'s 2026-09-08 entry. The pedagogical content of Section 0 is unchanged from v3.6; only the
generation unit and the day-numbering/labeling below changed.)

**Relationship to the Module Lesson-Plan prompt:** `Generate_Module_Lesson_Plan_Prompt_v2.md` plans a Set's
Scenario, Grammar Focus A/B pairing (and Essay Focus A/B direction, where applicable), and Leveled Mentor Ladder
direction before this prompt writes any lesson content, the same upstream relationship Reading's and
Listening/Speaking's own Module Lesson-Plan prompts have to their Lesson prompts. If an approved plan exists for
this Set, take its Scenario, Focus A/B pairing, and Mentor Ladder direction as given rather than re-deriving them
from Section 0.9 below for every one of the 4 lessons; this prompt's job then is to write the one lesson's worth
of content the plan calls for at that Set position. Running this prompt without an approved plan remains valid
for a Set's Lesson 1 - Section 0.9 below still applies in full when there is no plan to defer to - but Lessons
2-4 should always continue what Lesson 1 (and any lesson before them in the same Set) already established, never
re-derive the Scenario/Focus from scratch.

**Lesson header metadata:** directly under the generated document's H1, include a metadata line stating
`**Band:** ... | **Version:** S<Set>.<Lesson>.<Iteration>` - the version code per `shared/Program_Conventions.md`
§G. `<Lesson>` is this lesson's global number (continuing across Sets, per §G), not its 1-4 position within the
Set; a Set's four lessons get four consecutive global numbers and four separate version codes (e.g. `S1.1.0`
through `S1.4.0`), not one shared code. Iteration `0` on first generation.

---

**A note on "Day N" references throughout Section 0 below:** the pedagogical design in Section 0 (the grammar
bank, the essay-focus bank, board-dependent-moment placements, checklist timing, and so on) still refers to days
by their original global 1-8 numbering from the pre-v4, one-document-per-Set model, since that numbering is
woven through this section's own internal cross-references and its `Changelog.md` history. Translate using "The
Four-Lesson Set" table above: **Day 1 = Lesson 1's Day 1; Day 2 = Lesson 1's Day 2; Day 3 = Lesson 2's Day 1;
Day 4 = Lesson 2's Day 2; Day 5 = Lesson 3's Day 1; Day 6 = Lesson 3's Day 2; Day 7 = Lesson 4's Day 1; Day 8 =
Lesson 4's Day 2.** A range like "Days 1-4" means Lessons 1-2; "Days 5-6" means Lesson 3; "Days 1-8" or "the
8-day cycle" means the whole 4-lesson Set. The "TWO-DAY LESSON CYCLE" section above and every `### Lesson N, Day
M` heading below already use the new scheme directly - only Section 0's prose still uses the old numbering.

## SECTION 0: BAND AND OBJECTIVE CALIBRATION (READ AND APPLY BEFORE WRITING ANY LESSON)

### 0.1 Bands, task Levels, and the frame/composition regime boundary

**Moved to a shared, cross-modality doc:** paste `shared/Program_Conventions.md` alongside this prompt when
generating - §A has the Band/CEFR table, §B has the Task-Levels-by-Band table (identical here, reused rather
than reinvented, since it's the program's shared difficulty ladder).

**How to specify a lesson request:** every generation request must name at minimum a Module and a Band (e.g.
"Intermediate band, Module 5: Evaluating"). A topic/scenario is optional but recommended. As in Reading, a
specific Level is not part of the request; the table above determines every task Level once the Band is known.

**Why Writing needs a different sharing model than Reading (read this before designing the lesson).** Reading
can put every task Level's work on top of one shared anchor text because the text itself does not change: a
Beginner-extension student and an Intermediate-native student are reading the _same words_, just doing different
things with them. Writing cannot do this cleanly, because look at what the CSV's Writing objectives actually ask
for at each Level. **v3 recognizes three regimes, not two** (v2 collapsed Levels 4-8 into one "Independent
Composition" regime; Lesson 2 under v2 showed that Levels 6-8 need to be their own regime, not just a longer,
fancier version of Level 4-5's paragraph):

- **Levels 1-3 (Guided Frame Composition):** the student's entire output is one or two words, spelled from
  sound, dropped into a memorized or fixed sentence frame the student does not author (`"It is ___."`, `"I want
___ and ___, please."`). There is no original sentence construction yet.
- **Levels 4-5 (Paragraph Composition):** the student authors an original single paragraph independently, with
  the required feature (a comparison, an implied attitude) growing more demanding across the two Levels.
- **Levels 6-8 (Essay Composition):** the student authors a genuine multi-paragraph essay independently: a hook,
  a thesis statement, topic-sentence-led body paragraphs, and a conclusion (see `Academic Writing Essay Content
Sample` for the structural source), not a single longer paragraph. The required feature (a named reader and
  register shift, an inferable implication plus self-revision, two-audience calibration) is now realized at essay
  scale: which paragraph carries it, how the thesis sets it up, how the conclusion returns to it.
  These are not the same _kind_ of task at different depths, the way a Reading Fact Finder and a Reading synthesis
  question both operate on one shared paragraph. A single shared "anchor text" cannot serve a student who is
  spelling one word into a provided frame and a student who is structuring a five-paragraph essay. **Every band
  except Beginner spans, or sits entirely on one side of, one of the two regime boundaries (Levels 3/4 and Levels
  5/6):**

| Band         | Task Levels | Regime mix                                                                              |
| ------------ | ----------- | --------------------------------------------------------------------------------------- |
| Beginner     | 1, 2, 3     | Entirely Guided Frame Composition                                                       |
| Intermediate | 2, 3, 4, 5  | Spans the 3/4 boundary: 2, 3 are frame-based; 4, 5 are Paragraph Composition            |
| Advanced     | 4, 5, 6, 7  | Spans the 5/6 boundary: 4, 5 are Paragraph Composition; 6, 7 are Essay Composition      |
| Proficient   | 5, 6, 7, 8  | Spans the 5/6 boundary: 5 alone is Paragraph Composition; 6, 7, 8 are Essay Composition |

Intermediate is the one band that holds the frame/paragraph boundary; Advanced and Proficient are the two bands
that hold the paragraph/essay boundary. Design for whichever boundary a given band spans deliberately (see 0.1a
below and the dual-track guidance in the Two-Day Lesson Cycle section); do not let a spanning band collapse into two
disconnected tracks that happen to share a topic. No band currently spans both boundaries at once (none reaches
low enough to include Level 3 and high enough to include Level 6 in the same lesson), so a generated lesson never
needs to hold all three regimes together.

**0.1a The shared element is the Scenario, not a shared text.** Because the output form itself changes across the
band's task Levels, what every task Level shares is not one text but one **Scenario**: a single real-world writing
situation, stimulus (a picture set, a short real-world prompt, a simple situation description), and Module-aligned
purpose for writing, identical across every task Level in the lesson. Everything in the lesson (both grammar
focuses, the Mentor Text set, the prewriting stimulus, the drafting task, the editing checklist) is built on that one
Scenario. A Beginner-band lesson on Module 1 (Describing) and an Intermediate-band lesson on the same Module
might both use "describing a person's daily routine," but every task Level within a single generated lesson
describes the _same_ routine, person, or object.

**0.1b Leveled Mentor Ladder, not one shared anchor text.** In place of Reading's single anchor text, produce one
short worked model per task Level in the band, all built on the same Scenario, each modeling exactly that Level's
expected output form and required feature per Section 0.2. At Levels 1-5 this is a **Mentor Text** (one word, one
frame, or one paragraph, per that Level's regime). At Levels 6-8 this is a **Mentor Essay**: a complete
multi-paragraph essay (hook, thesis, topic-sentence-led body paragraphs, conclusion), not a longer paragraph
wearing an essay's word count. A Beginner-band lesson therefore has 3 Mentor Texts (Levels 1, 2, 3); an
Intermediate-band lesson has 4 (Levels 2-5, all Mentor Texts); an Advanced or Proficient-band lesson has 4,
mixing Mentor Texts (its Paragraph Composition Level(s)) and Mentor Essays (its Essay Composition Levels).
Present them together, in Level order, as a single visible "writing ladder" on Day 2, once Grammar/Essay Focus A
has been introduced: this lets a Level 2 student see what a Level 3 model looks like one step up, and lets a
Level 6 student see the same scenario handled at Level 5 one step down, even though Level 5's version is a
paragraph and Level 6's is a full essay: that jump in kind is exactly what the ladder should make visible, not
paper over. This also directly supports the self-revision requirement that first appears at Level 7 (see 0.2):
the ladder itself is worked evidence of the same idea growing more developed at each step, which Day 7's revision
work can point back to explicitly ("this is what your Level 6 version might look like if you pushed it toward
what the Level 7 model does").

Always pull the actual Writing-modality Learning Objective for **every task Level in the band** from
`learningobjectives.csv` (filter Level = each task Level, Modality = Writing, Module = the requested module)
before writing that Level's Mentor Text. Each task Level's Mentor Text and student task must satisfy that row's
Description and reflect its Example, never an invented difficulty curve. Do not pull only the anchor (lower) Level's
objective and scale it informally for the rest of the band; every task Level gets its own CSV lookup, the same way
Reading pulls a CSV row for every task Level's differentiated Reading task.

The Module governs the writing purpose, not just the difficulty, exactly as in Reading:

- **Module 1 (Describing):** the task is describing a person, object, place, or scene. Do not let it drift into
  narrating a sequence of events or arguing a position.
- **Module 2 (Narrating):** a sequence of real or realistic past events, in order, with a stated or implied reason
  the sequence mattered.
- **Module 3 (Explaining):** cause-and-effect or process content: why something happens or how something
  works, not a policy verdict.
- **Module 4 (Instructing):** a set of steps for a task, in order, addressed to a reader who will actually follow
  them.
- **Module 5 (Evaluating):** a judgment against a stated or implied criterion, not a plain narrative or a call to
  action.
- **Module 6 (Arguing):** a position with reasons and, from Level 4 up, an addressed counterpoint.
- **Module 7 (Transacting):** a message that accomplishes a real transactional goal (a request, a complaint, a
  reschedule), not a social pleasantry.
- **Module 8 (Socializing):** a social message calibrated to a relationship and occasion (thanks, a decline, a
  congratulation), not a transactional ask.

### 0.2 Output ceiling and required feature by level

Each entry gives the expected output form, an approximate length target (**provisional, see the note above**),
the grammar/vocabulary range, and the specific structural feature the CSV row requires, which the self-check in
0.3 will verify by name. "Regime" tells you whether this Level's task is frame-based, a single paragraph, or a
full essay (0.1); do not import a higher regime's expectations (original sentence construction, multi-paragraph
structure, a thesis statement) into a lower-regime Level, or vice versa.

**Level 1 (A1, Beginner floor - Guided Frame Composition)**

- Regime: Guided Frame Composition. The frame sentence is provided in full; the student supplies one spelled
  word into it, prompted by a picture.
- Output: one word, sounded out and spelled using known letter-sound patterns, into a single provided frame
  (e.g. "big \_\_\_").
- Grammar: none beyond the memorized frame itself.
- Vocabulary: concrete, high-frequency, phonics-decodable (CVC-level) words only.
- Required feature: the spelled word must come from the student sounding it out against a picture prompt, not
  from copying a printed word list. This "genuine choice inside a constrained task" is the Respectful Tiers
  requirement at this Level (see 0.5).
  **Level 2 (A2, Beginner ceiling / Intermediate extension-down - Guided Frame Composition)**
- Regime: Guided Frame Composition.
- Output: one word spelled into one open-slot fixed frame that forms a complete sentence (e.g. "It is \_\_\_.").
- Grammar: the frame's own single fixed structure (a simple present or simple past form); no variation.
- Vocabulary: concrete, high-frequency.
- Required feature: same as Level 1, genuine picture-prompted choice, now inside a full-sentence frame rather
  than a two-word chunk.
  **Level 3 (B1, Intermediate floor / Beginner extension-up - Guided Frame Composition)**
- Regime: Guided Frame Composition.
- Output: two words spelled into a two-slot frame (e.g. "It is **_ and _**." or a two-sentence sequence).
- Grammar: the frame's fixed structure, repeated across two slots; light coordination ("and") built into the frame
  itself, not authored by the student.
- Vocabulary: concrete, high-frequency; the two target words should not be synonyms of each other (this is where
  a lesson can quietly become too easy: pick two words that require genuinely separate observations of the
  prompt, e.g. "big" and "red," not "big" and "large").
- Required feature: as above, plus the two slots must require two distinct observations, not one idea said twice.
  **Level 4 (B1+, Intermediate ceiling - Paragraph Composition floor)**
- Regime: Paragraph Composition. This is the first Level where the student authors original sentences with no
  provided frame.
- Output: a short original paragraph, roughly 3-6 sentences, approximately 40-90 words.
- Grammar: simple present or simple past, a comparative structure (one comparison), one "because" reason
  clause, student's own choice of connector; a compound sentence (and/but/so) is appropriate here if the
  Scenario calls for one.
- Vocabulary: concrete + a small set of everyday abstract words.
- Required feature (per CSV): exactly one comparison and one explicit, directly-stated reason. The reason is
  never left implicit at this Level; that starts at Level 5.
  **Level 5 (B2, Advanced floor / Intermediate extension-up - Paragraph Composition)**
- Regime: Paragraph Composition.
- Output: an extended paragraph, roughly 6-9 sentences, approximately 90-150 words.
- Grammar: mixed past/present as needed, coordination and light subordination, hedging/evaluative language
  (a bit, seems, tends to, at least, worth it) to support the implied-attitude requirement.
- Vocabulary: everyday abstract vocabulary, light topic-specific vocabulary.
- Required feature (per CSV): logically organized detail, plus exactly one detail or word choice that implies an
  opinion, feeling, or reservation **without stating it directly**. This is the first Level where implication, not
  direct statement, is graded. Do not accept a paragraph that states the feeling outright and calls it done; the
  self-check in 0.3 exists specifically to catch this. With 8 days available, a light visible-revision pass is
  recommended (not required) at this Level too; see 0.4a.
  **Level 6 (B2+, Advanced ceiling / Proficient extension-down - Essay Composition floor)**
- Regime: Essay Composition (new in v3; see 0.1). This is the first Level where the output is a genuine
  multi-paragraph essay, not a longer paragraph.
- Output: a five-paragraph essay: an introduction (hook + connecting information + thesis statement), 2-3 body
  paragraphs each opening with its own topic sentence followed by supporting sentences, and a conclusion that
  restates the thesis and closes with a suggestion, prediction, question, or opinion (per `Academic Writing Essay
Content Sample`'s conclusion guidance). Approximately 300-450 words total across the whole essay. Not built on
  a rigid formula beyond this shape (it should not read as three interchangeable body paragraphs with no real
  distinction between them).
- Thesis: **direct** (names the essay's points of development, i.e., what each body paragraph will cover).
- Hook: any of the five types in the sample (a question, an observation, a scenario, a quote, a statistic).
- Grammar: complex sentences with sustained control; register-shifting cohesive devices (however, in fact, on the
  other hand, given that), used in the body paragraph or the conclusion that addresses the named reader's concern.
- Vocabulary: broader abstract/evaluative vocabulary.
- Required feature (per CSV, realized at essay scale): explicitly states why at least one feature/detail matters
  to a **specified reader** named in the Scenario, in one body paragraph or the conclusion, and shifts register
  or approach at least once to address that reader's stated concern. The Scenario must therefore name a specific
  reader and that reader's specific concern or priority; a generic "write about X" prompt does not give this
  Level anything to shift for, and does not give the thesis real points of development to name.
  **Level 7 (C1, Proficient floor / Advanced extension-up - Essay Composition)**
- Regime: Essay Composition.
- Output: a multi-paragraph essay (introduction, 3 body paragraphs, conclusion), approximately 450-650 words
  total.
- Thesis: **indirect** (signals that points of development exist without naming them, per the sample's
  direct/indirect distinction), a step up from Level 6's direct thesis.
- Hook: a quote, a statistic, or a scenario/anecdote, not a plain question; a genuinely stronger opening than
  Level 6's.
- Grammar: sophisticated cohesion (this suggests, what's more, admittedly), idiomatic and precise vocabulary,
  flexible register control, concession/counter structures ("while X is true, Y matters more").
- Required feature (per CSV): embeds at least one implication the reader must infer rather than being told
  directly, built into the essay's own selection and emphasis of detail across paragraphs (distinct from Level
  5's simpler version of this, a single hedge word inside one paragraph), and shows **evidence of unprompted
  self-revision** (see 0.4a) visible in at least one paragraph of the draft.
  **Level 8 (C2, Proficient ceiling - Essay Composition)**
- Regime: Essay Composition.
- Output: an extended essay of 5-7 paragraphs (introduction, 4-5 body paragraphs organized into two clearly
  distinguishable sections, conclusion), approximately 650-900 words total.
- Thesis: direct or indirect, the writer's choice, but it must set up both of the essay's audience-calibrated
  sections, not just one.
- Grammar/vocabulary: no ceiling; full range expected, including everything in Levels 6-7's bank.
- Required feature (per CSV): deliberately calibrates tone, register, and approach at least twice within the same
  essay for two distinct named audiences (most naturally, one body-paragraph group per audience), while keeping
  both sections logically consistent with each other (they must reach the same underlying point or judgment, not
  contradict) and the conclusion resolving both. The Scenario must therefore specify two distinct readers or
  stakes for this Level to have anything to calibrate between.

### 0.3 Self-check before finalizing (apply to every generated lesson)

1. Count words and sentences (or paragraphs, for Levels 6-8) in every task Level's Mentor Text/Mentor Essay and
   in the drafting task's target, **verified programmatically or by an actual count, not estimated**. Does each
   match its own Level's range in 0.2, not a neighboring Level's range?
2. Check every task Level against its own CSV row's Description, not the anchor Level's. A Level 5 task inside an
   Advanced-band lesson (where Level 5 is the extension-down Level) must still hit the full Level 5 bar (implied
   attitude via one hedge word), not be quietly simplified because it is the "easy" Level in that particular band.
3. Regime check: for every task Level at 1-3, confirm the frame is fully provided and only the target word(s) are
   student-authored. For every task Level at 4-5, confirm there is no provided frame and the output is a single
   paragraph, not a multi-paragraph essay. For every task Level at 6-8, confirm the output is a genuine
   multi-paragraph essay with a hook, a thesis statement, topic-sentence-led body paragraphs, and a conclusion,
   not a single longer paragraph with essay-level vocabulary (the specific miscalibration Lesson 2 made under v2).
4. Required-feature check: for each task Level, locate the exact structural feature required by 0.2 (a
   comparison, an implied attitude, a register shift for a named reader, an inferable implication plus
   self-revision, multi-audience calibration) inside that Level's Mentor Text/Mentor Essay and confirm the
   drafting/editing tasks actually ask the student to produce it, not just to write generally on the topic. For
   Levels 6-8, also confirm the thesis is the correct kind (direct at 6, indirect at 7-8) and the hook is of an
   appropriate type for the Level (0.2).
5. Scenario check (0.1a): does the Scenario supply what every task Level in the band needs? Specifically, for a
   band including Level 6, does the Scenario name a specific reader and that reader's concern; for a band
   including Level 8, does it name two distinct readers or stakes?
6. Grammar-focus check (0.4): is Focus A/B anchored at the band's own **native** Paragraph Composition row, not
   simply its lowest, per the corrected row-selection rule (does this band's lowest Paragraph Composition Level
   happen to be native, as with Intermediate, or an extension-down accommodation with its own native floor
   higher up, as with Advanced)? Does Focus A actually equip students to execute the band's task ladder (e.g. a
   comparative structure is taught before a Level 4+ task requires a comparison), and does Focus B genuinely add
   sentence variety useful to the Scenario, not an unrelated grammar point chosen only because the sample
   textbook happened to cover it? Does any extension-down Level within the band still get its own row's content,
   sufficient to execute its own required feature, even though it is not the centerpiece, and is that content
   folded into the same whole-class mini-lesson (not split into a separately labeled or separately printed
   "warm-up" that implies a different lesson for a subset of students)? For a band including Levels 6-8, does the
   lesson also teach Essay Focus A
   (hook + thesis construction) and Essay Focus B (topic sentences + outlining, or combining sentences for
   cohesion) as their own real input-and-practice content, not assumed to be already known?
7. Respectful Tiers check (0.5): would the Level 1-3 student, having done only their own task, feel they did
   rote copying while the Level 4+ students did "the real writing"? Every task Level, including frame-based ones,
   needs one moment of genuine authorial choice (which word fits the picture, not a single correct answer read off
   the board).
8. Module-alignment check: do the Mentor Texts and drafting tasks actually exercise the Module's verb
   (describe/narrate/explain/instruct/evaluate/argue/transact/socialize), not a neighboring Module's skill?
9. Editing/peer-editing check (0.6): does the self-edit checklist name this lesson's specific grammar focuses and
   required feature (not a generic "check your spelling" list), and does the Peer Editing exchange scaffold per
   task Level?
10. Self-revision check: is there an actual mechanism producing visible revision evidence (0.4a) at Levels 7-8
    (required) and, ideally, Level 5 (recommended), not just an instruction to "revise your work" with nothing
    collected to show it happened?
11. Board-dependent moment check (0.7): does each of the 8 days include at least one genuine board-dependent
    moment, not a restatement of material already printed on a handout?
12. Skill Spotlight / Closing Transfer Check (0.8): does Day 1 name the transferable skill in plain language, and
    does Day 8 close with every student producing one new instance of that exact skill out loud or on paper, with
    a few students sharing, rather than a self-report confidence check?
13. Rotation check (0.9): different grammar focuses, different Scenario topic, and different real-world writing
    form than the immediately preceding cycle for the same class, checked against the Rotation Log.
14. No em-dashes anywhere in generated content (style constraint, shared with Reading).
15. Content volume check (0.4b): does each grammar/practice day have at least 3 distinct activities, and does
    each activity meet its item-count minimum (6-8 items; 6-8 sentences with 6-8 verified errors for an editing
    paragraph)? Would this day read as a full page when printed, not a handout with room to spare?
16. Level 5 essay-structure bridge check (0.4c, new in v3.2): for any band whose task-Level span includes both
    Level 5 and Level 6+ (Advanced, Proficient), does Level 5 get a light, receptive activity on the same shared
    model essay the Essay Composition Levels analyze (e.g. find and underline one topic sentence), positioned next
    to that essay rather than buried inside Level 5's own paragraph-focused practice? Confirm this stays receptive
    only and does not quietly raise Level 5's own required output past a single paragraph (0.2).
17. Teaching-before-practice sequencing check (0.4c, new in v3.3): for every controlled-practice or task-ladder
    activity, does the teaching content it depends on (a Grammar table, an Essay Focus explanation, a taught
    distinction like direct/indirect thesis) appear earlier in the lesson's own day-by-day sequence, not later,
    and not only inside a Mentor Text/Mentor Essay where it is modeled but never explicitly taught? Trace this
    for every day, not just Day 1 against Day 2.
18. Paired-tier check (0.4c, new in v3.3): for every controlled-practice activity that serves only part of a
    band's task-Level range, was a lighter receptive tier (for the Level below) or heavier combining tier (for
    the Level above) considered, and added wherever it closes a real engagement gap? Where a heavier tier was
    added, does it draw only on grammar content already taught by that point in the lesson, never reaching into
    a later day's not-yet-taught point?
    If any check fails, rewrite before proceeding. Do not build the drafting and editing days' content on top of a
    Mentor Ladder that fails its own Level ceilings.

### 0.4 Grammar-in-Context focus: a two-point cluster, selection, and bank

Every lesson has **two** grammar/language focuses: **Focus A**, a core verb-form or structural point, and
**Focus B**, a sentence-variety or cohesion point that pairs naturally with it. This mirrors what the sample's two
chapters both actually do: a chapter never stops at one grammar point and moves to writing. Chapter 3 teaches
simple present forms, then moves to simple/compound sentences, then articles, before the paragraph task.
Chapter 4 teaches simple past forms, then adverbs of manner, then complex sentences with time clauses, before
its own paragraph task. Two grammar days (Day 1 and Day 3, see the cycle below) is the minimum that lets a
generated lesson do the same pairing without crowding both points into one 75-minute block the way v1 did.

Both focuses are chosen top-down from the Scenario and the band's task ladder, the same principle as v1: not a
fixed syllabus sequence independent of what the writing task needs.

**Grammar Focus Bank by Level** (a starting bank; expand it the same way Reading's genre bank grew over
versions, by adding entries rather than replacing them):

| Level(s) | Focus A: core form                                                                                                                                                   | Focus B: sentence variety / cohesion                                                                                 | Why this Level needs it                                                                                        |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| 1        | Letter-sound spelling patterns (CVC words); the frame sentence itself is pre-built                                                                                   | n/a (frame regime, single word)                                                                                      | Output is a spelled word, not a sentence                                                                       |
| 2        | Simple present or simple past, single fixed form (no paradigm yet)                                                                                                   | n/a (frame regime, single slot)                                                                                      | One-slot frame needs only one verb form                                                                        |
| 3        | Simple present affirmative -s form spelling rules (add -s/-es/-ies)                                                                                                  | Light coordination "and" inside a two-slot frame only; no independent sentence variety yet                           | Two-slot frame; first exposure to the full -s paradigm                                                         |
| 4        | Simple present/simple past control; comparative adjectives (-er/more); "because" reason clauses, plus since/as/given that as richer alternatives to "because" (v3.3) | Simple vs. compound sentences (and/but/so), including comma placement                                                | Required feature is one comparison + one explicit reason; a compound sentence gives the reason room to breathe |
| 5        | Consistent tense control across a paragraph; hedging/evaluative vocabulary (a bit, seems, tends to, at least, worth it)                                              | Complex sentences with a contrast/concession subordinator (although, even though, but)                               | Required feature is an implied attitude, often carried by a hedge tucked inside a concession clause            |
| 6        | Register-shifting cohesive devices (however, in fact, on the other hand, given that)                                                                                 | Complex sentences with a time, causal, or concessive subordinate clause, chosen to fit the register shift            | Required feature is a register/approach shift for a named reader; the shift often lands at a clause boundary   |
| 7        | Sophisticated cohesion (this suggests, what's more, admittedly); explicit self-revision language                                                                     | Concession/counter structures ("while X is true, Y matters more"); varied subordination across the piece             | Required feature is embedded implication plus visible self-revision                                            |
| 8        | Multi-audience calibration devices (formal/informal register markers used deliberately)                                                                              | Deliberate sentence-length and structure variation as a rhetorical tool between the two audience-calibrated sections | Required feature is calibrating tone for two distinct named audiences within one document                      |

**Reason-connector richness (new in v3.3):** do not teach Level 4's "because" as a single isolated word with no
alternatives. Teach it alongside at least since, as, and given that, each with its own example, even though
"because" alone still satisfies Level 4's own required feature. Two reasons: a single-word grammar point reads as
thin content on its own, and when Level 4's row folds into a higher band as light content rather than the
centerpiece (per the row-selection rule below), a "because"-only treatment reads as literally identical to
whatever band Level 4 is actually native to, undermining the same differentiation this row-selection rule exists
to protect. "Given that" is a natural inclusion for any band that also reaches Essay Composition, since it is
already Level 6's own register-shifting device in the row above; teaching it explicitly at Level 4/5 gives
Essay-regime students a name for something they would otherwise only meet unexplained inside a Mentor Essay.

**Row selection when a band spans rows (resolved in v2, corrected in v3.1):** teach as Focus A **the row belonging
to the band's own native Paragraph Composition Level(s)**, i.e. the Level(s) that define the band's own primary
calibration per 0.1's Band/CEFR table, not automatically the band's lowest Paragraph Composition Level. v2's
guidance conflated the two, reasoning that "higher rows in the same band build additively on the lowest one" and
therefore the lowest row should always anchor Focus A. That reasoning holds only when the band's lowest Paragraph
Composition Level is itself native to the band, which is true for Intermediate (Level 4 is Intermediate's own
ceiling, so anchoring there is correct and nothing changes) but not for Advanced (Level 4 is Intermediate's ceiling
loaned downward as Advanced's extension-down accommodation, not a Level native to Advanced; Advanced's own native
Paragraph Composition floor is Level 5). Concretely:

- If the band's lowest Paragraph Composition Level is native to the band (Intermediate: Level 4), anchor Focus A/B
  there, as before.
- If the band's lowest Paragraph Composition Level is instead an extension-down accommodation, not native to the
  band (Advanced: Level 4 sits below Advanced's own floor, Level 5), anchor Focus A/B at the band's **native**
  Paragraph Composition row instead (Advanced: Level 5's row), and add the extension-down Level's own row,
  teaching exactly what that Level's own required feature (0.2) needs and nothing more, the same treatment
  frame-regime Levels already receive when they sit below a band's Paragraph Composition floor. Do not drop the
  extension-down Level's own required feature just because its row is no longer the centerpiece; 0.3's self-check
  item 2 still applies to it in full.
- If a band's only Paragraph Composition Level is itself an extension-down accommodation with no native sibling to
  compare against (Proficient: Level 5), there is nothing to anchor "instead of," so this correction does not
  apply; Grammar Focus A/B was already non-centerpiece content for that band (0.4c is Proficient's real
  centerpiece), and Level 5's own row is taught as its own light content regardless.
  **Grammar is a teaching moment, not a practice moment: never split it into a separate lesson for a subset of
  students.** Whichever Level(s) contribute a row to a given day's Grammar (or Essay Focus) mini-lesson, the
  teacher delivers all of it, back to back, to the entire room in one sitting; there is no point in the cycle where
  part of the class receives different grammar instruction than the rest. An extension-down Level's own row is
  additional content inside that same session, not a separately timed, separately labeled, or separately printed
  "warm-up" that only some students see. A printed packet should reflect this: one combined Grammar box per
  mini-lesson, not one box per Level. Differentiation belongs entirely downstream of the teaching input, in the
  controlled-practice activities and the drafting task, where it already lives per this section's own bank and per
  0.2's per-Level required features.

This stays true even for a band that reaches into Essay Composition (Advanced, Proficient): Levels 6-8 still get
the chosen Focus A/B row as sentence-level grammar content (a Level 6-8 essay is still built out of correctly
formed sentences), it is just no longer their _structural_ centerpiece; see 0.4c for what is. In Advanced's case,
Levels 6-7 now fold in Level 5's row (tense control and hedging/evaluative language, concession subordination)
rather than Level 4's (comparatives), which is also simply a better sentence-level fit for essay writing than
raw comparatives were. Focus B follows the same row chosen for Focus A, per the table above, regardless of which
row that was.

### 0.4c Essay Focus: structure content for Levels 6-8 (new in v3)

Grammar Focus A/B (above) is sentence-level and applies across the whole band. It is necessary but not sufficient
for Levels 6-8: a well-formed sentence is not an essay. Levels 6-8 need their own centerpiece content, **Essay
Focus A** (essay structure and thesis construction) and **Essay Focus B** (paragraph-internal and cross-paragraph
cohesion), drawn from `Academic Writing Essay Content Sample` the same way Grammar Focus A/B was drawn from
`Writing Content Sample`. Where a band includes Levels 6-8, these run as their own parallel track through Days
1-4, alongside (not instead of) Grammar Focus A/B: composition-regime Levels 4-5 spend Day 1-2/Day 3 on Grammar
Focus A/B as the centerpiece; Essay-regime Levels 6-8 spend the same days on Essay Focus A/B as their centerpiece,
with Grammar Focus A/B folded in as a lighter sentence-craft component (the mirror image of how frame-regime
Levels get a light Grammar Focus A/B warm-up while composition-regime Levels get it as their centerpiece).

**Essay Focus Bank by Level:**

| Level | Essay Focus A: structure                                                                                                                                        | Essay Focus B: cohesion                                                                                                                                                                | Why this Level needs it                                                                                                                                   |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 6     | Five-paragraph essay shape (introduction/body/conclusion); direct thesis statement construction; hook types (question, observation, scenario, quote, statistic) | Topic sentence + supporting sentence structure within a body paragraph; general outlining (main points only)                                                                           | Level 6's required feature (a named reader and a register shift) needs a body paragraph and a conclusion to land in, and a thesis that sets it up         |
| 7     | Indirect thesis construction, a step up from Level 6's direct thesis                                                                                            | Specific outlining (down to supporting detail); combining sentences for cohesion across and within paragraphs                                                                          | Level 7's embedded implication is built through selection and emphasis of detail across several paragraphs, which a specific outline plans for in advance |
| 8     | Two-section essay organization (an audience-calibrated paragraph group per audience); a thesis that sets up both sections                                       | Deliberate structural variation between the two sections as a rhetorical device (e.g. shorter, more direct sentences for one audience; longer, more qualified sentences for the other) | Level 8's two-audience calibration needs two genuinely distinguishable paragraph groups, not one paragraph mentally split in half                         |

**Row selection for Essay Focus (same principle as Grammar Focus A/B):** teach Essay Focus A/B anchored at
**Level 6's row**, since Level 6 is always the band's lowest Essay Composition Level in both bands that reach
this regime (Advanced and Proficient alike). Level 7 (and Level 8, in a Proficient-band lesson) receive their
row's content as an additive extension folded into the same sessions, the same way Level 5's hedging extension
already folds into Day 3's close and Day 4 for the paragraph regime (0.4's existing pattern, unchanged).

**Bridging the regime gap at Level 5 (new in v3.2):** in any band whose task-Level span crosses from Paragraph
Composition into Essay Composition (Advanced: Level 5 sits directly below Levels 6-7; Proficient: Level 5 sits
directly below Levels 6-8), Level 5 is one Level away from a jump in output demand large enough to notice: one
paragraph at Level 5, a full five-paragraph essay at Level 6, with nothing in between. Give Level 5 a light,
receptive version of the Essay analysis activity below, built on the same shared model essay the Essay Composition
Levels are analyzing that same day: for example, find and underline the topic sentence of one body paragraph, then
state in their own words what that paragraph is about. Keep this receptive only, a few minutes of reading and one
short written response, not essay-length production; Level 5's own required output stays a single paragraph per
0.2, unchanged. Position it physically next to the shared model essay (in the lesson plan and in any print
packet), separate from Level 5's own paragraph-focused Grammar Focus A/B activities, so it reads as an early,
lightweight look at essay structure rather than as extra grammar practice. This is not the same move as an
extension-down Level's own row inside Grammar Focus A/B (0.4): that gives a Level its _own_ required content it
must produce; this gives Level 5 optional-strength, receptive-only exposure to content it is not yet required to
produce, in service of a smoother climb into the next regime.

**Teaching content must precede the practice that depends on it (new in v3.3).** Before finalizing a lesson,
trace every controlled-practice or task-ladder activity back to the teaching content (a Grammar mini-lesson
table, an Essay Focus explanation, a worked distinction like direct/indirect thesis) it depends on, and confirm
that content appears **earlier in the lesson's own day-by-day sequence**, not later and not only inside a Mentor
Text/Mentor Essay where it is merely modeled, not explained. This failure mode is easy to miss because both
pieces are present somewhere in the lesson; the bug is purely about order. Where a distinction is needed by a
Day 1 activity but was drafted as Day 2 teaching content (the mistake caught in Lesson 2: a Day 1 thesis
identify/rewrite activity ran before Day 2's direct/indirect table), move the teaching earlier rather than
moving the practice later by default, since earlier teaching gives every subsequent day's content the same
foundation, not just the one activity that happened to expose the gap. See Self-check item 17.

**Pair a single-audience activity with a lighter or heavier tier for the Level next to it, where a natural one
exists (new in v3.3, generalizing the Level 5 essay-structure bridge above).** Wherever a controlled-practice
activity serves only part of a band's task-Level range (for example, an activity built only for the essay-regime
Levels, or only for the paragraph-regime Levels), check whether the Level immediately adjacent to that range
could take a lighter, receptive version (identify rather than produce; recognize rather than construct) or,
symmetrically, whether Levels above an activity's normal range could take a heavier, combining version (stack
two already-taught grammar points into one sentence, rather than drilling one at a time). Build any such tier
only from content already taught by that point in the lesson's own sequence; do not have a higher Level's harder
tier reach into a later day's not-yet-taught grammar point (the mistake caught in Lesson 2's first draft of the
hedge-word combining activity, which reached into Day 3's concession subordinators from inside a Day 1-2
activity). Not every single-audience activity needs this treatment: add a paired tier where it closes a real gap
in engagement, not as a mechanical requirement on every task. See Self-check item 18.

**Essay-regime controlled-practice activity types** (drawn directly from `Academic Writing Essay Content Sample`;
use alongside, not instead of, the sentence-level activity types below, for whichever days carry Essay Focus
A/B):

- **Essay analysis:** give a short original model essay (built for this lesson's Scenario, not lifted from the
  sample) and ask students to identify its purpose, paragraph count, thesis statement, and each body paragraph's
  topic sentence (the sample's Activities 1-4, 9 pattern).
- **Hook-writing practice:** give the connecting information and thesis of a short essay without its hook, and
  have students write one or two candidate hooks, then compare effectiveness (the sample's Activities 5, 8
  pattern).
- **Thesis identify/rewrite:** identify a given thesis statement as direct or indirect, then rewrite it as the
  other kind (the sample's Activities 6, 9 pattern).
- **Outlining:** complete a general outline (main points only), then a specific outline (down to supporting
  detail) for the same short essay (the sample's Activities 10, 11 pattern, shown side by side so students see
  how one expands into the other).
  **Self-revision extension (resolved in v2):** the 8-day cycle gives every composition-regime Level real revision
  time, not just Levels 7-8. Section 0.2 above marks Level 5's light visible-revision pass as recommended rather
  than required; treat Levels 4 and 6 the same way if time allows on Day 7. It remains a hard CSV-compliance
  requirement only at Levels 7-8.

**Controlled-practice activity types** (borrowed directly from the sample's activity shapes; use 2-3 per grammar
day, matched to that day's focus):

- **Analyzing/classifying:** identify which sentences use the target structure correctly, or classify sentences by
  function (the sample's Habit/Fact/Process sort is one instance of this pattern; adapt the categories to the
  lesson's Module).
- **Fill-in-the-blank on a model paragraph:** a short paragraph on the Scenario's topic (or a closely related one)
  with the target grammar form blanked out, to be completed correctly. This is a natural home for a Mentor Text
  variant at the frame-regime Levels.
- **Editing a paragraph:** a short paragraph containing a fixed number of errors in the target structure, to find
  and correct (the sample's Activity 5, 13, 22 pattern). Always state the exact number of errors, as the sample
  does, so the task is self-checking; count them yourself before finalizing rather than reusing an unchecked
  figure (see the note in Lesson 1's own self-check about exactly this mistake).
- **Combining/expanding sentences:** combine short simple sentences into one sentence using the target
  connector or structure (the sample's Activity 12, 24 pattern). This is Focus B's natural home once Focus A's
  forms are solid.
- **Choosing between confusable structures:** a forced choice between two structures students commonly
  confuse at this Level (the sample's "they are / there are" pattern; pick the analogous confusable pair for the
  lesson's own grammar focus where one exists).
- **Writing original sentences with target words:** one sentence per target vocabulary/grammar item, using it
  correctly (the sample's Activity 23 pattern); this is the bridge from controlled practice into Day 4's
  task-ladder warm-up and Day 5's freer writing.

### 0.4a Making self-revision checkable, not just claimed

Levels 7 and 8 both require "evidence of unprompted self-revision"; Level 5 (and, time allowing, 4 and 6) benefits
from the same practice without the hard requirement (0.4). A closing instruction like "now revise your work"
produces no evidence a reviewer (teacher, peer, or a later audit of the lesson) can actually check, the same
problem Reading's v2.2 thumbs-up self-report had and v2.3 replaced with a demonstration. Use one of these
concrete mechanisms instead:

- **Visible strikethrough/insertion revision:** students revise on the same page, crossing out the original
  wording rather than erasing it, so the original and the revision are both visible side by side.
- **Two-column before/after:** a short "what I first wrote" / "what I changed it to, and why" two-column note for
  just the one or two sentences that changed most, rather than a full clean rewrite with no trace of the process.
- **Revision partner note:** a peer reads the draft once, names one specific place they got confused or wanted
  more, and the writer's revision responds to that specific note (this doubles as part of Day 7's Peer Editing
  step; see 0.6).
  Whichever mechanism is used, the lesson's Day 7 materials must include the template for it explicitly; do not
  leave it to the teacher to improvise on the day.

### 0.4b Content volume per day (added after Lesson 1 review)

Lesson 1's first printed packet (Days 1-2) read thin: a 3-item fill-in-blank, a 5-item classify task, and a
5-sentence editing paragraph do not fill a printed page, and do not obviously occupy a full 75-minute class
period either, even though the phase timings on paper add up to 75 minutes. The fix is not fewer days; the
8-day cycle stays (see the note in v2's history above). The fix is more content inside each day's existing phases.
Concrete minimums, applied to every generated lesson from here forward:

- **Item counts.** A fill-in-the-blank, classify, choose-the-form, or combine-the-sentences activity should have
  at least 6-8 items, not 3-5. A confusable-pair drill should have at least 6 items. An editing-a-paragraph
  activity should use a paragraph of at least 6-8 sentences with a correspondingly higher, still-verified error
  count (aim for 6-8 errors, not 4-5).
- **Activities per grammar/practice day.** Days 1-4 (both grammar-focus days, the task-ladder day, and any day
  built primarily around controlled practice) should include at least 3 distinct activities across their phases,
  not 2, pulling from more of the bank in 0.4 rather than reusing the same one or two activity types across the
  whole lesson. A day with only a mini-lesson and one activity is under-filled even if the timing column says 75
  minutes.
- **Frame-regime parity.** Levels 1-3's parallel practice should scale up the same way: more picture-based
  rounds, not just one, so a frame-regime student also has enough printed material to fill the page their
  composition-regime classmates are filling with a longer activity list.
- **Essay-regime parity (new in v3).** Where a band includes Levels 6-8, their parallel Essay Focus A/B track
  (0.4c) needs the same volume standard applied to its own activity shapes, not the sentence-level item counts
  above: a full short model essay for the essay-analysis activity (not a single paragraph), at least 2 candidate
  hooks per hook-writing activity, both a general and a specific outline (not just one) for the outlining
  activity. A day that gives Levels 6-8 only a mini-lesson and one essay-analysis worksheet is as under-filled as
  a grammar day with only one activity.
- **Drafting and revision days are exempt from item-count minimums.** Days 5-6 (drafting) and Day 7 (revision)
  are governed by Section 0.2's word-count targets and the checklist/Peer Editing Form in 0.6, not by activity
  item counts; a drafting day is not "thin" just because it has fewer discrete printed items than a grammar day.
- **Check this before finalizing.** Before a lesson is considered done, mentally lay out each grammar/practice
  day as it would print: does it look like a full worksheet page, or does it look like a handout with room to
  spare? If the latter, add another activity from the 0.4 bank rather than padding an existing one with filler
  items that don't teach anything new.

### 0.5 Respectful Tiers for writing

The same standing check Reading applies to its matrix and oral protocol applies here: no task Level should feel
like "the busywork one" while another gets "the real writing." For Levels 1-3, this cannot mean giving them an
unscaffolded composition task; it means making sure the one word they do supply is a genuine choice, not a
foregone answer copyable off the board (see 0.2's "required feature" rows for each frame-regime Level). For
Levels 4+, it means the lower task Level's required feature (a comparison, in Level 4's case) should feel like a
real accomplishment inside its own scaffolding, not a lesser version of the higher Levels' work: give it a strong,
genuinely interesting comparison to make, not a trivial one.

Before finalizing, apply the same test Reading uses: would the lowest task Level's student, having only done
their own Level's work, feel they did the easy part while everyone else did the real thinking? If yes, strengthen
that Level's task (a better picture prompt, a more genuinely interesting two-slot choice, a comparison with real
stakes) rather than leaving the imbalance in place.

**Foundation Support (below the lowest task Level):** for a student functioning below even Level 1's floor,
provide picture-to-word matching (select, don't spell), tracing a pre-written word with a meaning-check question,
or teacher-scribed dictation where the student says the word aloud and the teacher writes it, checking the
student can point to which word is which afterward. This sits alongside the lowest task Level, not in place of it.

### 0.6 Editing checklist and Peer Editing, by regime

**Composition-regime Levels (4-8), Day 6 self-edit checklist:** build a short checklist specific to the lesson's two
grammar focuses and required feature, following the sample's own checklist pattern (Activity 25's "each sentence
has a subject and a verb," "I used the base form and -s form correctly," and so on). A generic template to adapt
per lesson:

- Every sentence has a subject and a verb, and matches Focus A's target grammar form correctly.
- At least one sentence uses Focus B's sentence-variety structure correctly.
- The required feature (name it explicitly: "one comparison and one stated reason" / "one detail that implies my
  opinion without stating it" / "a register shift for [the named reader]" / etc.) is actually present and locatable
  in the piece.
- Punctuation and capitalization are correct, including comma use in any compound or complex sentence.
- (Levels 7-8 required; Levels 4-6 recommended) The self-revision evidence (0.4a) is present and visible, not
  just a note saying "I revised this."
  **Essay-regime Levels (6-8) add these items to the checklist above (new in v3), rather than replacing it:**

- The essay has a hook, and it is a real hook (0.2's type for this Level), not a flat statement of the thesis.
- The thesis statement is present, at the end of the introduction, and is the correct kind for this Level (direct
  at 6, indirect at 7-8).
- Every body paragraph opens with a topic sentence that states that paragraph's own main point.
- The conclusion restates the thesis and does not introduce new information.
- (Level 8 only) Both audience-calibrated sections are present, and each one's register/approach is genuinely
  distinct from the other's, not the same content with a different opening line.
  **Frame-regime Levels (1-3), Day 6 equivalent:** replace the written checklist with a short oral or picture-matching
  self-check ("does your word match the picture? read your sentence to a partner, does it make sense?"), scaffolded
  down to the Level, not a written checklist these students cannot yet produce independently.

**Peer Editing (Day 7):** exchange work with a partner and use a short Peer Editing Form with 2-3 questions tied
specifically to this lesson's grammar focuses and required feature (not a generic "did you like it?"), plus one
specific compliment and one specific suggestion, following the sample's Activity 26 pattern. Differentiate
participation the same way Reading differentiates Phase 3 (0.8, Part B, in the Reading prompt): a Level 1-3
student's "peer edit" can be an oral partner check (read your sentence aloud, does your partner understand the
word?) rather than a written comment exchange. For essay-regime Levels (6-8), add questions that check the essay's
structure specifically: can your partner identify the hook, the thesis, and each body paragraph's topic sentence
without your help; for Level 7-8, what do they think the embedded implication or the two audiences' distinct
concerns are, checked against what the writer actually intended.

### 0.7 Board-dependent moments

Each of the 8 days needs at least one genuine board-dependent moment (co-constructed live, synthesizes
distributed input, or persists and gets built on across days), using the same three-property test as Reading's
Section 0.7. With 8 days there is room for one clearly homed moment per day rather than leaning on the
persists-across-days exception the way the v1, 4-day cycle sometimes had to. Typical placements:

- **Day 1:** co-construct one new example sentence live, on a fresh prompt, using Focus A.
- **Day 2:** as the class examines the Leveled Mentor Ladder, co-construct a live "what changes at each Level" board,
  built from student observations of the ladder rather than pre-written by the teacher.
- **Day 3:** co-construct one new example sentence live using Focus B, the same way Day 1 did for Focus A.
- **Day 4:** synthesize prewriting ideas from every task Level's pair/group work into one shared idea board for
  the Scenario, so no single handout contains the complete set of ideas the class generated.
- **Day 5:** a running "strong sentence" board, populated as students share one sentence from their in-progress
  draft.
- **Day 6:** return to and add to Day 5's board with newly completed lines as students finish drafting.
- **Day 7:** a before/after board built from two or three volunteered revision examples (0.4a).
- **Day 8:** capture Closing Transfer Check instances live on the board as students share them.

### 0.8 Skill Spotlight and Closing Transfer Check

**Day 1, during Focus A's mini-lesson:** state the lesson's transferable skill in one or two plain, student-facing
sentences, tied to the Module's verb and the specific required feature from 0.2 ("Today we're practicing
describing something by comparing it to something else and giving a real reason for the comparison," not just
"Today we're writing about backpacks"). For a band spanning into Essay Composition, add a second sentence
covering what Levels 6-8 are additionally building toward that day (structuring that comparison, or that
explanation, as a full essay), so the spotlight names both tracks rather than only the paragraph-regime one.

**Day 8, closing the lesson:** every student applies the exact spotlighted skill to something new (not their main
Scenario piece), produces it out loud or on a small card, and a few students are cold-called to share. Do not
close with a self-report ("thumbs up if you feel confident") for the same reason Reading's v2.3 replaced that
mechanism: a visible whole-class confidence vote converges on "yes" regardless of whether the skill transferred.

### 0.9 Rotation

**Applies in full only when generating a Set's Lesson 1 without an approved Module Lesson-Plan** (see "Relationship
to the Module Lesson-Plan prompt" above). Do not repeat the same grammar focus pair, the same Scenario topic, or
the same real-world writing form (see the Module-to-form mapping below) in two consecutive Sets for the same
class, and avoid clustering the same grammar focus across nearby Modules even when they are not strictly
consecutive (e.g. teaching comparatives as Focus A for both a Describing Set and an Evaluating Set generated back
to back), since both draw from the same shared grammar range and can overlap without the topic itself repeating.
Lessons 2-4 of a Set never re-run this check - they continue Lesson 1's own Scenario/Focus, already checked once
for the whole Set.

**Before generating a Set's Lesson 1 (or any lesson without an approved plan):** read `Rotation_Log.md` (overview)
and every existing `Rotation_Log_<Band>.md` in full - the check below spans every Band, not just the one being
generated for, so a single Band's file is not enough on its own. Check the grammar focus pair, Scenario topic,
and real-world writing form against at least the immediately preceding logged Set across all Bands (by date), and
scan the fuller set of logs for a grammar focus that has recurred more than once in the last 3-4 Sets overall.
Flag any repeat before finalizing the lesson rather than after.

**After each lesson is generated and approved:** append one row to that lesson's own Band's `Rotation_Log_<Band>.md`,
nested under that Set's own subsection (creating the Set subsection, using the template at the bottom of any
existing `Rotation_Log_<Band>.md`, if this is that Set's first approved lesson) per its own format instructions.
This is the mechanism the log depends on; a lesson that is generated but never logged breaks the rotation check
for every Set generated after it.

**Module-to-real-world-form mapping** (the Writing equivalent of Reading's genre bank in its 0.6; match
formatting convention to the form, not generic paragraph formatting for everything). The rightmost column is new
in v3: `Academic Writing Essay Content Sample` names five essay types (cause-effect, comparison, argument,
problem-solution, reaction). Levels 1-5 always use the middle column (paragraph/frame form). Levels 6-8 use the
essay type where one is mapped; where a Module has no clean mapping yet, treat that Module's Levels 6-8 as
provisional (an extended paragraph, per v2's ceiling) until a suitable essay-type parallel is established, rather
than forcing a bad-fit essay type onto it:

| Module         | Real-world writing form (Levels 1-5)                 | Formatting convention                                       | Essay type (Levels 6-8)                                                                                                                              |
| -------------- | ---------------------------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1: Describing  | Descriptive paragraph (a place, person, or object)   | Continuous prose                                            | Comparison essay (compare two instances of the described thing, e.g. two places or two options)                                                      |
| 2: Narrating   | Personal narrative / journal entry                   | Chronological prose, time connectors                        | Reaction essay (narrate an experience, then reflect on/react to it) - the loosest of the five mappings; revisit once a lesson has actually tested it |
| 3: Explaining  | Explainer paragraph / short how-something-works note | Cause-effect structure, may use light process language      | Cause-effect essay                                                                                                                                   |
| 4: Instructing | Instruction set / how-to note                        | Numbered or sequenced steps, imperative verb forms          | Not yet mapped; Levels 6-8 continue as an extended paragraph                                                                                         |
| 5: Evaluating  | Review or opinion paragraph                          | Criterion stated early, verdict signaled clearly            | Problem-solution essay (evaluate a problem, argue for one solution's value over the alternatives)                                                    |
| 6: Arguing     | Position paragraph / short persuasive note           | Claim, reason(s), addressed counterpoint from Level 4 up    | Argument essay                                                                                                                                       |
| 7: Transacting | Email or written message handling a request/problem  | Greeting/sign-off conventions, clear stated ask             | Not yet mapped; Levels 6-8 continue as an extended paragraph                                                                                         |
| 8: Socializing | Card, note, or social message                        | Tone matched to occasion, relationship-appropriate register | Not yet mapped; Levels 6-8 continue as an extended paragraph                                                                                         |

---

## THE FOUR-LESSON SET: A FIXED ARC, ONE SCENARIO CARRIED THROUGHOUT

**Unlike Reading, whose 4 lessons in a Set each get an independent anchor text and topic, Academic
Writing's 4 lessons in a Set share one Scenario, carried from grammar input through a finished,
published piece.** This is a fixed pedagogical arc, not an open per-lesson choice: which position
in the Set a lesson occupies (1 through 4) determines its content role directly. This prompt
generates **one 2-day lesson per run** (75 min/day, 150 min total) - run it four times per Set, once
per position, against the same approved Module Lesson-Plan (`Generate_Module_Lesson_Plan_Prompt_v2.md`).

| Set position | Content role | (Was, under the old 8-day-in-one-doc model) |
| --- | --- | --- |
| **Lesson 1** | Grammar Focus A: input, modeling, and deeper practice | Days 1-2 |
| **Lesson 2** | Grammar Focus B, Essay Focus A/B (where applicable), Mentor Ladder, prewriting | Days 3-4 |
| **Lesson 3** | Drafting, parts 1 and 2, and self-edit | Days 5-6 |
| **Lesson 4** | Peer editing, revision, publishing, and the Closing Transfer Check | Days 7-8 |

Lessons 3 and 4 do not re-derive the Scenario, Grammar Focus A/B, Essay Focus A/B, or Mentor Ladder
from Section 0.9 - they continue the same lesson content Lessons 1-2 already established for this
Set. Every request to this prompt names the Set (and therefore the approved plan/prior lessons to
continue from) and which of the four positions is being generated.

## TWO-DAY LESSON CYCLE: STRUCTURE AND DETAILED FLOW

**LESSON 1 (150 MIN TOTAL, 75 MIN/DAY) - GRAMMAR FOCUS A**

```
DAY 1: GRAMMAR FOCUS A - INPUT AND MODELING (75 MIN)
|-- Phase 1: Hook, Skill Spotlight (15 min)
|-- Phase 2: Focus A mini-lesson: rule + examples (30 min)
|-- Phase 3: Controlled practice A, part 1 (30 min)

DAY 2: GRAMMAR FOCUS A - DEEPER PRACTICE AND THE MENTOR LADDER (75 MIN)
|-- Phase 1: Editing-a-paragraph on Focus A, stated error count (20 min)
|-- Phase 2: Frame warm-up (Levels 1-3) / original sentences with Focus A (Levels 4+) (25 min)
|-- Phase 3: Leveled Mentor Ladder walkthrough (30 min)
```

**LESSON 2 (150 MIN TOTAL) - GRAMMAR FOCUS B AND PREWRITING**

```
DAY 1: GRAMMAR FOCUS B - SENTENCE VARIETY (75 MIN)
|-- Phase 1: Focus B mini-lesson: rule + examples (20 min)
|-- Phase 2: Controlled practice B: identifying/combining sentences (30 min)
|-- Phase 3: Confusable-pair drill + mixed A/B editing paragraph (25 min)

DAY 2: TASK-LADDER PRACTICE AND PREWRITING (75 MIN)
|-- Phase 1: Frame practice round 2 (Levels 1-3) / required-feature warm-up (Levels 4+) (25 min)
|-- Phase 2: Prewriting for the Scenario, differentiated by task Level (30 min)
|-- Phase 3: Prewriting share and board synthesis (20 min)
```

**LESSON 3 (150 MIN TOTAL) - DRAFTING**

```
DAY 1: DRAFTING, PART 1 (75 MIN)
|-- Phase 1: Mentor Ladder and prewriting re-look (10 min)
|-- Phase 2: Independent/guided drafting: opening and body (50 min)
|-- Phase 3: Mid-draft share-out (15 min)

DAY 2: DRAFTING, PART 2 AND SELF-EDIT (75 MIN)
|-- Phase 1: Complete the draft (30 min)
|-- Phase 2: Self-edit checklist pass (25 min)
|-- Phase 3: Share-out / final line check (20 min)
```

**LESSON 4 (150 MIN TOTAL) - PEER EDITING, REVISION, AND PUBLISHING**

```
DAY 1: PEER EDITING AND REVISION (75 MIN)
|-- Phase 1: Peer Editing exchange (25 min)
|-- Phase 2: Revision time, incl. self-revision evidence (35 min)
|-- Phase 3: Quick revision share (15 min)

DAY 2: PUBLISHING AND CLOSING TRANSFER CHECK (75 MIN)
|-- Phase 1: Final polish / proofread pass (20 min)
|-- Phase 2: Publish/share (30 min)
|-- Phase 3: Closing Transfer Check (25 min)
```

### Essay-regime dual-track guidance (new in v3)

The flow above is written for a Paragraph Composition band (Beginner/Intermediate's composition
Levels, or a lesson where no task Level reaches 6). For Advanced and Proficient, which both include
Levels 6-8, run two tracks in parallel through Lessons 1-2, the same structural move v2 already
makes for frame-regime Levels inside Intermediate, now one regime higher:

- **Levels 4-5 (where present in the band):** follow the flow below exactly, with Grammar Focus A/B (0.4) as
  their centerpiece.
- **Levels 6-8:** spend the same two lessons (four days) on Essay Focus A/B (0.4c) as their centerpiece instead:
  Lesson 1 covers essay structure, hook types, and direct-thesis construction (Level 6's row) plus the Level 7
  (and, in a Proficient lesson, Level 8) extension; Lesson 2 Day 1 covers topic sentences, outlining, and
  cohesion (Essay Focus B); Lesson 2 Day 2 is required-feature warm-up and prewriting, now producing an actual
  essay outline rather than a paragraph plan. Grammar Focus A/B is not dropped for these Levels, it runs as a
  lighter sentence-craft component inside the same days (their essay still needs correctly formed comparative
  sentences and compound sentences), mirroring how Levels 1-3 get a light Grammar Focus A/B fold-in inside a
  Paragraph Composition band's Lesson 1.
- **Mentor Ladder walkthrough (Lesson 1, Day 2, Phase 3) and prewriting share (Lesson 2, Day 2, Phase 3)** already
  present every task Level together in one place (0.1b); keep doing this. Levels 6-8's Mentor Essays sit at the
  top of the same ascending ladder Levels 4-5's Mentor Texts sit in, so the jump from paragraph to essay is
  visible material, not a note explaining it.
- **Lesson 3 (drafting):** an essay is more to draft than a paragraph in the same two days. Levels 6-8 draft the
  introduction and first body paragraph on Day 1, and the remaining body paragraph(s) and conclusion on Day 2,
  the same two-day split Levels 4-5 already use for opening/body then completion, just distributed across more
  material. Flag this pacing as provisional the same way 0.2's word counts are: it has not yet been checked
  against a real class's actual drafting speed, and may need a dedicated outlining lesson added later if it
  proves too tight.
- **Lesson 4 (peer edit, revision, publishing, closing):** use the essay-specific checklist and Peer Editing
  additions in 0.6, and the essay-regime item in each day's board-dependent moment where relevant (0.7 is
  otherwise unchanged in structure).

### Lesson 1, Day 1: Grammar Focus A, Input and Modeling

_Phase 1: Hook, Skill Spotlight (15 min)_

- Open with a short hook tied to the Scenario (a picture, a real-world situation, a short prompt), pitched at
  language near the band's lower task Level, not the band's ceiling.
- Skill Spotlight (0.8): name the transferable skill in plain language.
  _Phase 2: Focus A mini-lesson: rule and examples (30 min)_
- Present Focus A (0.4) with a rule statement and 2-3 examples, in the sample's own grammar-box style: a short
  rule, then example sentences that make the rule concrete.
- Fold in a brief frame-regime warm-up here for Levels 1-3 where present in the band (the frame sentence and one
  elicited example word), since their own Focus A cell is usually much lighter than the composition-regime
  Levels'.
  _Phase 3: Controlled practice A, part 1 (30 min)_
- 1-2 controlled-practice activities from the bank in 0.4 (analyzing/classifying or fill-in-the-blank), matched to
  Focus A.
- Board-dependent moment (0.7): co-construct one fresh example live.

### Lesson 1, Day 2: Grammar Focus A, Deeper Practice and the Mentor Ladder

_Phase 1: Editing a paragraph on Focus A (20 min)_

- A short paragraph with a stated, verified number of Focus A errors to find and correct.
  _Phase 2: Frame warm-up / original sentences with Focus A (25 min)_
- Levels 1-3 (where present): guided practice completing frames on the Scenario picture.
- Levels 4+: write original sentences using Focus A correctly, one per target item.
  _Phase 3: Leveled Mentor Ladder walkthrough (30 min)_
- Present the Leveled Mentor Ladder (0.1b) in Level order, on the shared Scenario. For each task Level's Mentor
  Text, briefly name what makes it that Level's version (the frame it fills, or the required feature it demonstrates).
- Students identify their own task Level's Mentor Text and the one directly above it.
- Board-dependent moment (0.7): co-construct a live "what changes at each Level" board from student
  observations of the ladder.

### Lesson 2, Day 1: Grammar Focus B, Sentence Variety

_Phase 1: Focus B mini-lesson: rule and examples (20 min)_

- Present Focus B (0.4) the same way Day 1 presented Focus A: a rule, then examples, tied explicitly to how it
  pairs with Focus A (e.g. "yesterday you learned to compare two things; today we'll join that comparison to its
  reason in one sentence using a compound sentence").
  _Phase 2: Controlled practice B (30 min)_
- Identifying sentence types, and/or combining short sentences using Focus B's structure (the sample's Activity
  10, 12, 24 pattern).
  _Phase 3: Confusable-pair drill and mixed editing (25 min)_
- A forced-choice confusable pair relevant to the lesson (the sample's "they are / there are" pattern; pick the
  analogous pair for this lesson, e.g. "it's / its" for an object-description Scenario).
- A short paragraph mixing Focus A and Focus B errors, stated and verified error count, to find and correct.
- Board-dependent moment (0.7): co-construct one fresh example live using Focus B.

### Lesson 2, Day 2: Task-Ladder Practice and Prewriting

_Phase 1: Frame practice round 2 / required-feature warm-up (25 min)_

- Levels 1-3 (where present): a second guided frame-practice round directly on the Scenario, choosing genuinely
  distinct observations for any multi-slot frame (0.2's Level 3 note).
- Levels 4+: a short guided warm-up targeting just the required feature (write one comparison sentence and one
  because-sentence; write one sentence with a concrete, specific detail and test whether a partner can infer the
  implied attitude from it) before Day 5's full draft.
  _Phase 2: Prewriting for the Scenario, differentiated by task Level (30 min)_
- All task Levels generate ideas about the same Scenario through whatever means fits their Level: labeling a
  picture (Levels 1-3), a short idea list or graphic organizer (Levels 4-6), a more developed outline naming the
  intended implication/register shift/self-revision target (Levels 7-8).
  _Phase 3: Prewriting share and board synthesis (20 min)_
- A few students from each task Level share one idea or detail.
- Board-dependent moment (0.7): synthesize ideas from every task Level into a shared idea board.

### Lesson 3, Day 1: Drafting, Part 1

_Phase 1: Mentor Ladder and prewriting re-look (10 min)_

- Each student re-reads their own task Level's Mentor Text and their Day 4 prewriting notes.
  _Phase 2: Independent/guided drafting, opening and body (50 min)_
- Frame-regime task Levels: complete their frame(s) for the actual Scenario (not the Day 2/4 practice frames),
  with the teacher circulating to hear each student sound out their word choice.
- Composition-regime task Levels: draft the opening and body of their piece, working toward the length and
  required-feature targets in 0.2 for their own task Level. A multi-day draft does not need to be finished today;
  Day 6 completes it.
- Teacher circulation should specifically check the required feature is present in-progress, not only at the end.
  _Phase 3: Mid-draft share-out (15 min)_
- A few students share one sentence from their draft so far.
- Board-dependent moment (0.7): a running "strong sentence" board, populated from the share-out.

### Lesson 3, Day 2: Drafting, Part 2 and Self-Edit

_Phase 1: Complete the draft (30 min)_

- Students finish their piece, meeting their own task Level's full 0.2 target.
  _Phase 2: Self-edit checklist pass (25 min)_
- Students run their own draft against the checklist appropriate to their regime (0.6).
  _Phase 3: Share-out / final line check (20 min)_
- A quick read-aloud or partner check of the piece's closing line or frame.
- Board-dependent moment (0.7): return to and add to Day 5's "strong sentence" board with newly completed
  lines.

### Lesson 4, Day 1: Peer Editing and Revision

_Phase 1: Peer Editing exchange (25 min)_

- Partner exchange using the lesson's Peer Editing Form (0.6), differentiated by task Level as described there.
  _Phase 2: Revision time, including self-revision evidence (35 min)_
- Students revise based on their own checklist pass and their partner's feedback. Levels 7-8 must produce one of
  the concrete self-revision artifacts from 0.4a; this is not optional at those Levels. Levels 4-6, especially Level
  5, are encouraged to do the same if time allows.
  _Phase 3: Quick revision share (15 min)_
- Board-dependent moment (0.7): a before/after board built from two or three volunteered revision examples.

### Lesson 4, Day 2: Publishing and Closing Transfer Check

_Phase 1: Final polish / proofread pass (20 min)_

- A last quiet read-through against the self-edit checklist, focused on anything the Day 7 revision changed.
  _Phase 2: Publish/share (30 min)_
- A short gallery walk, read-aloud, or class posting, appropriate to time and class size.
  _Phase 3: Closing Transfer Check (25 min)_
- Closing Transfer Check (0.8): every student applies the spotlighted skill once more to something new, out loud
  or on a card; a few are cold-called to share.
- Board-dependent moment (0.7): capture Closing Transfer Check instances live on the board as students share.

### Style and Formatting Constraints

- **Pacing diagrams:** include a visual ASCII timeline for the lesson's Day 1 and Day 2, matching the format
  above.
- **No em-dashes:** never use em-dashes anywhere in generated content; use hyphens, colons, or parentheses.
- **Leveled Mentor Ladder clearly labeled:** label every Mentor Text with its task Level number, visible at a glance,
  the way Reading labels anchor-text paragraphs with letters.
- **Regime language:** when describing a task Level's work in the lesson materials, use the plain-language
  regime name ("frame-based," "single-paragraph," "essay") rather than internal labels like "Level A/B/C."
- **Grammar Focus labeling:** always label which day's content belongs to Focus A versus Focus B (and, for a band
  reaching Levels 6-8, Essay Focus A versus Essay Focus B), so a teacher can tell at a glance which point a given
  activity is reinforcing and for which track.
  **Band Calibration Is Non-Negotiable:** exactly as in Reading, a well-scaffolded but genuinely calibrated lesson
  is correct; both an over-dense Level 6-level task pushed down into a Level 4 slot, and a thin task that technically
  hits a word-count floor but doesn't require the Level's actual feature, are miscalibrations, and must be rewritten
  before the lesson is finalized.
