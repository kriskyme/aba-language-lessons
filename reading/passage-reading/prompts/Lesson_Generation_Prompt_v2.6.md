# Passage Reading Lesson Generation Prompt (v2.6, Band-Calibrated)

**Lesson type:** this prompt generates a **Passage Reading Lesson** - a fixed 2-day cycle built around one shared
anchor text (a single passage or excerpt), differentiated into band-scoped task Levels. It is renamed from "Reading
Lesson Generation Prompt" in v2.5 to distinguish it from a planned separate lesson type, tentatively **Novel
Reading Lesson**, which will span a variable number of days across multiple chapters of a shared novel rather
than one passage. Nothing about the generation logic below changed for this rename - see "What changed in
v2.5" for the actual content changes.

Band-calibrated revision. Builds on the v2 Band-Calibrated revision's text-complexity ceilings and the original
2-Day Text Cycle structure, plus everything added in v2.1-v2.4 (mandatory board-dependent moments per day,
explicit skill naming with a closing transfer check, differentiated Phase 3 participation for low-level learners, and
paragraph lettering with contextual footnotes). v2.5 replaces the fixed two-level-band, three-tier (Level A/B/C)
differentiation model with a band-scoped set of same-modality Reading tasks, sized and pinned per band, and
drops "Level" as a separate request input.

**What changed in v2.1:** Section 0.7 is new. It requires at least one genuine, board-dependent activity per day
(something co-constructed live by the class, not a restatement of material already on a handout or slide).
Self-check item 12 in Section 0.3 was added to enforce it.

**What changed in v2.2:** Section 0.8 is new, in two parts. Part A (Skill Spotlight) requires the lesson to name the
actual transferable skill in plain student-facing language at the start of Day 1 and close the loop at the end of Day
2. Part B (Differentiated Participation) requires Phase 3's oral protocol to give the lesson's lowest task level a
genuinely different participation mode, not just easier sentence stems inside the same live-debate format, and
adds a Foundation Support layer for students functioning below that lowest task level's own floor. Self-check
items 13 and 14 were added to enforce these.

**What changed in v2.3:** Section 0.8, Part A's closing mechanism is corrected. The v2.2 draft closed Day 2 with a
thumbs-up/sideways/down self-report against a can-do statement; that is unreliable evidence, since a
whole-class visible confidence vote tends to converge on "yes" regardless of whether the skill actually
transferred (nobody wants to be the visible thumbs-down). v2.3 replaces self-report with a Closing Transfer
Check: every student produces one instance of the skill on something new, out loud to a partner, and the teacher
cold-calls two or three pairs to share, so the evidence is a demonstration, not a declaration. Self-check item 13
was reworded to match.

**What changed in v2.4:** Section 0.9 is new, in two parts. Part A requires every anchor text's paragraphs to be
labeled with sequential capital letters (A, B, C...) so they can be referenced precisely and consistently across
STOP & CHECK questions, Fact Finders, and the Collaborative Evidence Matrix, instead of by number. Part B
adds textbook-style contextual footnotes: a superscript marker on a real person, place, or reference the text
names but does not explain, with a brief note in the page footer, distinct from target-vocabulary pre-teaching and
the Idiom/Slang Spotlight. Self-check items 15 and 16 were added to enforce these.

**What changed in v2.5:** Section 0.1's tier model is replaced. The old model served every band with exactly
three tiers (Level A/B/C), each mapped somewhere within that band's own two levels. The new model gives each
band a fixed table of task Levels, pulled from the real 1-8 Level scale rather than reinvented per band: three task
Levels for the Beginner band, four for Intermediate, Advanced, and Proficient. Each task Level is anchored to an
actual row in `learningobjectives.csv` (Level x Modality=Reading x the requested Module), never an invented
difficulty curve, and the anchor text's own complexity ceiling (Section 0.2) is still governed solely by the band, as
in v2.4 - only the task ladder built on top of that shared anchor text changed. A lesson request now needs only a
Module and a Band; a specific Level is no longer part of the request, since the Task Levels by Band table
determines every task Level automatically. Every reference to "Level A / Level B / Level C" throughout this
document is replaced with plain language ("the lowest task Level," "the band's native Levels," "the highest task
Level," or a specific Level number), since the number of task Levels per lesson now varies by band and letters
cannot map cleanly onto a variable, asymmetric set. Self-check items 6, 7, and 14 are reworded to match, and a
new self-check item 17 is added. Sections 0.8 and 0.9 are also reordered into their correct numeric sequence (a
v2.4 document-assembly artifact, not an intentional change). Everything else - Section 0.2's complexity ceilings,
idiom rules (0.4), Day 2 refresher-text rules (0.5), genre rotation (0.6), board-dependent moments (0.7), and the
Skill Spotlight / Closing Transfer Check mechanism (0.8, Part A) - is unchanged. Separately, this document and its
lesson type are renamed from "Reading Lesson Generation Prompt" to **"Passage Reading Lesson Generation
Prompt"** to distinguish it from the planned, not-yet-written Novel Reading Lesson type (see the note under the
title). This is a naming change only - it does not alter any rule below.

**Also added within v2.5 (this revision, no version bump):** Section 0.6's genre bank is expanded (6 new genres
added: text-message/chat thread and product listing/description for Intermediate; social media post thread and
advice-column letter-with-response for Advanced; podcast transcript excerpt and historical primary-source-style
document for Proficient), each with a matching formatting-convention sentence. The Reading Execution Rules list
is expanded with 3 new strategies (Think-Aloud Modeling, Say Something, Close Reading with Annotation), each
with its own implementation instruction. This grows both banks without changing any existing entry, calibration
ceiling, or self-check item, so it does not warrant a new version number on its own.

**What changed in v2.6:** Section 0.10 is new. Fishbowl and Concentric Circles/Speed-Dating, as previously
written, assume a class large enough that a 5-6 student inner circle still leaves a meaningful outer circle of
observers who rotate in over time. At a realistic class size (roughly 8-12 students, confirmed against actual
classes this program runs), that assumption breaks: an inner circle already contains most of the room, and one
question circulating for the full 30-minute Phase 3 window is redundant rather than differentiated practice for
whoever's left outside it. Phase 3 now defaults to simultaneous small groups (3-4 students, mixed task Level)
working across 2-3 distinct discussion prompts written directly into the lesson, rather than one prompt and a
rotating circle; Fishbowl and Concentric Circles remain available only where a class is genuinely large enough
(roughly 16+) for an inner/outer split to leave a real audience. This also resolves a standing gap with the
Student Print Formatting Prompt (v1), which independently reached the same simultaneous-small-groups
conclusion for its own packets (its Section 2.9) but, until now, had to invent 2-3 discussion prompts on the spot
because the source lesson only ever supplied one - a lesson generated under v2.6 supplies all of them directly.
Section 0.7's Phase 3 board-dependent-moment guidance and Section 0.8 Part B's differentiated-participation
wording are both updated to fit a small-group format instead of a single visible circle. Self-check item 18 is
added.

Adopt a Content-Based Instruction (CBI) and Task-Based Language Teaching (TBLT) framework. Treat reading
as a tool to explore real-world ideas and build critical thinking, allowing language acquisition to occur naturally
through meaningful communication.

This version carries mandatory text-complexity calibration (Section 0) on top of the existing 2-day structure.
Complexity calibration is a hard constraint: if a generated text or task exceeds the target band's ceiling below, it
must be rewritten before anything else in the lesson is finalized.

Section 0.2 note: word-count and paragraph-count targets below are anchored to real published single-lesson
B1-C1 reading materials (British Council LearnEnglish reading texts and Cambridge English exam
specifications), not derived purely from the narrow templated Reading-modality objective statements in the
learning objectives source. An earlier version of this table under-shot real single-lesson text length by roughly
5-8x at the middle levels (it capped Level 3 at 40-70 words; a real single-lesson B1 passage runs 300+ words
across multiple paragraphs). The learning objectives still govern what skill the text must support (grammar range,
vocabulary tier, inference type); the numbers below govern how much text a real lesson needs to be worth
building a 2-day cycle around.

Learning objectives source of record: `learningobjectives.csv` is the single master file for all learning objectives
across all 8 levels, 3 modalities, and 8 modules (192 rows total: Level, Modality, Module, Description, Example).
Always pull objectives from this CSV, not from older per-level import files, which are derived/legacy exports of
the same data and are not guaranteed to reflect the latest revisions.

Scope note: This prompt generates Passage Reading Lessons only - the fixed 2-day, single-anchor-text type
defined above. It does not generate the planned Novel Reading Lesson type (multi-day, multi-chapter); that will
be its own, separate prompt when written. To build a differentiated, per-task-Level assessment from a set
of completed lessons, use the separate companion prompt `assessment-generation-prompt-v4.md`. Do not
attempt to generate an assessment from this prompt, and do not use the assessment prompt to generate new
lesson content: the two have different inputs and are not interchangeable. **Note:** as of this revision, the
Assessment Generation Prompt and the Module Lesson-Plan Generation Prompt still assume the old three-tier
Level A/B/C model and have not yet been updated to match Section 0.1 below; treat them as out of sync with this
prompt's tier system until they are revised to match.

---

## SECTION 0: BAND CALIBRATION (READ AND APPLY BEFORE WRITING ANY TEXT)

### 0.1 How to find the target band and task Levels

Bands are defined as:

| Band | Levels | CEFR |
|---|---|---|
| Beginner | 1-2 | A1-A2 |
| Intermediate | 3-4 | B1-B1+ |
| Advanced | 5-6 | B2-B2+ |
| Proficient | 7-8 | C1-C2 |

**The anchor text is calibrated to the band's LOWER level**, exactly as in v2.4 (Level 3 for Intermediate, Level 5
for Advanced, Level 1 for Beginner, Level 7 for Proficient). This single Level governs Section 0.2's word count,
grammar, and vocabulary ceiling for the whole lesson. The anchor text itself never changes complexity based on
which task Levels are assigned within it - every student in the room reads the same text; only the task built on
top of it differs by Level.

Always pull the actual Reading-modality Learning Objective for the band's lower level and the target Module from
`learningobjectives.csv` before writing the anchor text: filter by Level = the band's lower level, Modality =
Reading, and Module = the requested module, and use that row's Description and Example as the objective the
anchor text must satisfy. The anchor text's difficulty is governed ONLY by the Reading-modality objective at that
level, not by the Listening/Speaking or Writing objectives at the same level, which may describe more advanced
production skills. Do not let those inflate the reading text's complexity.

**Task Levels by band (v2.5):** each band has a fixed set of task Levels - one differentiated Reading task per
Level, all built on the single shared anchor text described above:

| Band | Task Levels | Count |
|---|---|---|
| Beginner | 1, 2, 3 | 3 |
| Intermediate | 2, 3, 4, 5 | 4 |
| Advanced | 4, 5, 6, 7 | 4 |
| Proficient | 5, 6, 7, 8 | 4 |

How this table is built: a band's own two Levels always get a task (its "native" Levels). Where a neighboring
band has a Level to lend, the set extends one Level below and one Level above those native Levels, with two
deliberate exceptions:

- **Beginner does not extend below** (Level 1 is the floor of the whole scale) and extends only one Level
  above, to Level 3 - producing 3 task Levels instead of 4.
- **Proficient does not extend above** (Level 8 is the ceiling of the whole scale), so instead of stopping at 3
  task Levels the way Beginner does, it extends two Levels below instead of one, borrowing both of the
  Advanced band's Levels (5 and 6) to keep 4 task Levels.

This asymmetry is deliberate, not an oversight: pushing a Beginner-band student's task up into
Intermediate-scoped material is a real stretch risk for a still-developing reader, so that reach is capped at one
Level. Pushing an Advanced-band student's task up into Proficient-scoped material is a much smaller risk - it is a
step into "harder," not a foundational-literacy stretch - so the Proficient band is allowed to borrow both of
Advanced's Levels rather than just one.

**Band-distance invariant:** every task Level in the table above is at most one band away from the anchor text's
own calibrated band. No task is ever built two bands away from what the class is actually reading. This is what
makes it safe to share one anchor text across every task Level in a lesson: the widest gap any student faces is
one band's worth of difficulty between their assigned task and the text they're all reading together, never two.

**How to specify a lesson request:** every generation request must name at minimum a Module and a Band (e.g.
"Advanced band, Module 6: Arguing"); a topic is optional but recommended. A specific Level is no longer part of
the request - the Task Levels by band table above determines every task Level automatically once the Band is
known. Without a Module/Band pair, the CSV lookups above cannot happen and the generator has no basis for
calibration: do not proceed to write a text until both are known, either from the request or by asking.

The Module objective governs the task, not just the difficulty. Section 0.2's word count, grammar, and vocabulary
ceilings tell you how hard the text can be; the pulled objective tells you what skill it must actually exercise. Do not
treat the objective only as a difficulty gauge and then default to a generic informational-article task regardless of
Module.

- **Module 1 (Describing):** the core task must be describing a person, object, place, or scene (features,
  qualities, comparisons), not summarizing cause-and-effect or evaluating a policy. A Level 4 Describing text
  can be an extended description of a real place, but the comprehension work must center on descriptive
  features, a comparison, and a stated reason for it, matching the objective's actual verbs.
- **Module 3 (Explaining):** cause-and-effect, process, and "why this happens" content belongs here, not in
  Describing.
- **Module 5 (Evaluating):** claims, criteria, and verdicts belong here.
- **Module 6 (Arguing):** weighing two sides toward a position belongs here.

Before finalizing, check the objective's Description against the actual comprehension questions and
Collaborative Evidence Matrix prompts. A text can still mention conservation or environmental threats as
color/context, but the graded tasks must trace back to the Module's actual verb, not drift into a neighboring
Module's skill because it made for an easier debate topic.

### 0.2 Complexity ceiling by level

These are hard targets for the anchor text at each level: a word-count range, paragraph count, and average
sentence length, plus the grammar/vocabulary/comprehension constraints that keep the text inside the right
band. Word counts are anchored to real published single-lesson materials at each CEFR level (see source note
above), not reverse-engineered from the atomic skill described in the objective. Write toward the middle-to-upper
part of the range, not the floor. A text at or below the floor of its word-count range is a fail, not just a warning
sign: this has happened twice already, an earlier draft produced a 55-word, 4-sentence Level 3 text that
technically fit an old, too-low ceiling but did not function as a real reading passage, and a later batch of Level 3
lessons came in at 212-246 words against a 280-350 word range despite the correct ceiling being in this
document. Count the words before finalizing, every time; do not estimate.

Each entry below also notes which band(s) use that Level as a task Level per Section 0.1's table - "native" means
it is one of that band's own two Levels, "extension" means the level borrows into a neighboring band.

**Level 1 (A1, Beginner floor - Beginner's anchor level and lowest native task Level)**
- Form: short functional text (a notice, a label set, a short exchange of 2-4 lines) or 1-2 short sentences using a
  memorized frame; not necessarily continuous prose
- Length: 60-120 words total
- Grammar: no verb tense variation beyond one memorized frame; present tense or simple past frame only
- Vocabulary: concrete, high-frequency, decodable CVC/simple phonics words only; zero abstract nouns
- Sentence length: average 6-10 words/sentence
- Comprehension demand: literal match to a picture/object; no inference

**Level 2 (A2, Beginner ceiling - Beginner's upper native task Level; also Intermediate's extension-down task Level)**
- Form: 3-4 short paragraphs (or a short email/note-style text), each built from fixed-frame sentences
- Length: 150-220 words total
- Grammar: single frame per sentence (simple present or simple past "-ed"); no subordination
- Vocabulary: concrete, high-frequency; 3-5 target words per text max
- Sentence length: average 8-12 words/sentence
- Comprehension demand: literal match with visual support; minimal inference (locating a stated fact)

**Level 3 (B1, Intermediate floor - Intermediate's anchor level and lowest native task Level; also Beginner's extension-up task Level)**
- Form: 4-5 paragraphs of connected prose (a real short article/narrative, not a template)
- Length: 280-350 words total
- Grammar: simple present and simple past as the backbone; one coordinating connector per sentence max (and,
  because, but); light subordination is acceptable if it stays simple (a single "who/which/that" clause), but avoid
  stacking two coordinators or two subordinate clauses in one sentence; no passive voice
- Vocabulary: concrete/familiar-topic vocabulary; 4-6 pre-taught target words; no academic/abstract vocabulary
  (avoid words like "extraordinary," "civilization," "habitat," "preserved": these are Level 5+ vocabulary)
- Sentence length: average 12-18 words/sentence
- Comprehension demand: literal comprehension, scanning for direct facts, basic cause-and-effect; decode target
  words in context
- Numbers/dates: light factual grounding is fine (a text can mention a year, a place, a few concrete details); avoid
  a dense multi-date timeline that turns the passage into a biography-style reference article

**Level 4 (B1+, Intermediate ceiling - Intermediate's upper native task Level)**
- Form: 5-6 paragraphs, original (non-templated) connected prose
- Length: 350-430 words total
- Grammar: simple past narrative or present-tense description; one comparison structure; one "because" reason
  clause; light subordination throughout, still no dense multi-clause sentences
- Vocabulary: concrete + a small set of everyday abstract words (e.g. "reliable," "worth it"); no
  technical/academic register
- Sentence length: average 15-22 words/sentence
- Comprehension demand: identify one comparison, one stated outcome, one directly-stated reason (not implied);
  reasons are always explicit ("because I need to carry it every day"), never left for the reader to infer
- Numbers/dates: factual grounding fine; still not a dense multi-date timeline

**Level 5 (B2, Advanced floor - Advanced's anchor level and lowest native task Level; also Intermediate's extension-up task Level)**
- Form: 5-7 paragraphs, connected prose organized logically (not a fixed template)
- Length: 400-460 words total
- Grammar: mixed past/present, coordination and light subordination (one subordinate clause per sentence is
  fine), natural connectors chosen by the writer (not fed as a fixed frame)
- Vocabulary: everyday abstract + some topic-specific vocabulary (4-6 pre-taught words), but NOT dense
  academic/technical register: avoid nominalizations and Latinate technical terms ("neuroplasticity,"
  "paradigmatic," "malleability" are Level 7-8, not 5)
- Sentence length: average 17-24 words/sentence
- Comprehension demand: summarize organization, identify ONE clearly-signaled implied
  attitude/feeling/reservation (a conventional signal like a hedge word or evaluative adjective, not a subtle
  unsignaled inference; see the Level 5 and 6 rows in `learningobjectives.csv` for the exact skill boundary)
- Numbers/dates: light factual grounding is fine; still not a dense multi-date chronology

**Level 6 (B2+, Advanced ceiling - Advanced's upper native task Level; also Proficient's extension-down task Level)**
- Form: 6-8 paragraphs, fluent connected prose without a fixed template
- Length: 460-520 words total
- Grammar: complex sentences with sustained control, but not dense academic syntax; register shifts are simple
  and signaled clearly, not buried in jargon
- Vocabulary: broader abstract/evaluative vocabulary, light topic-specific terms; still avoid specialist/technical
  jargon or C1-C2 academic collocations
- Sentence length: average 20-28 words/sentence
- Comprehension demand: separate stated fact from clearly-signaled evaluative language; locate ONE visible
  tonal or register shift partway through the text (e.g. confident language followed by a hedge) without needing to
  infer the writer's underlying motive for that shift
- Numbers/dates: factual grounding fine; avoid stacking more than 2-3 discrete facts/dates

**Level 7 (C1, Proficient floor - Proficient's anchor level and lowest native task Level; also Advanced's extension-up task Level)**
- Form: 7-11 paragraphs; two related extended texts (for comparison) OR one dense extended text; full
  academic/idiomatic register allowed
- Length: 600-700 words (per text, if two texts are used, each can run shorter, roughly 300-400 words each, as
  long as the combined comparison task reaches full C1 demand)
- Grammar: full complex sentence range, idiomatic phrasing, flexible register
- Sentence length: average 20-25 words/sentence
- Vocabulary: academic and idiomatic vocabulary appropriate to topic; abstraction is expected
- Comprehension demand: critically compare rhetorical choices across two texts OR identify an unstated
  interest/assumption/premise; this is where "Chiribiquete"- and "neuroplasticity"-style density actually belongs

**Level 8 (C2, Proficient ceiling - Proficient's upper native task Level)**
- Form: 8-12 paragraphs; dense, stylistically layered text (irony, understatement, unreliable framing,
  dual-audience calibration)
- Length: 700-900 words
- Grammar/vocabulary: no ceiling; full native-like range expected
- Sentence length: average 22-28 words/sentence
- Comprehension demand: reconstruct withheld/downplayed meaning, detect manipulation techniques, assess
  risk of divergence between literal and real meaning for a specified reader

### 0.3 Self-check before finalizing (apply to every generated lesson)

Before finalizing Phase 2 (Text Engagement) content, verify against the anchor-level ceiling for the band's LOWER
level:

1. Count the words in the anchor text. Is it inside the range for that level? A text at or near the floor of its range
   is a warning sign, not just an acceptable minimum: check that it still reads as real connected prose with
   enough substance to support two full class periods, not a thin fact-list.
2. Count paragraphs and average sentence length. Does the text match the paragraph count and average
   sentence length for that level, not just the total word count? (A single dense 300-word paragraph is not
   equivalent to five well-developed 60-word paragraphs; the paragraph count and sentence-length targets exist
   precisely to prevent that substitution.)
3. Check clause complexity. Does any sentence exceed the grammar ceiling for that level?
4. Scan the vocabulary. Circle any word that would only appear 2+ bands higher (cross-check against the
   vocabulary guidance above). If found, replace it.
5. Count distinct dates/numbers/named entities. If the text reads like a biography or reference article with a
   dense timeline, it is miscalibrated: collapse it to the single-topic, moderate-fact-density form the level
   requires.
6. **(Reworded in v2.5)** Check every task Level above the anchor level against the ceiling for its own assigned
   Level (Section 0.2), never the level beyond it - even where that assigned Level belongs to a neighboring band.
   An Intermediate-band lesson's Level 5 task should reach exactly the Level 5 ceiling; it should not require
   Level 6 or C1-level unstated-premise detection just because Level 5 happens to sit inside the Advanced
   band's own native range.
7. **(Reworded in v2.5)** Check the Collaborative Evidence Matrix against the Respectful Tiers requirement (see
   the Dynamic Tiered Framework section below). The lowest task Level's work must include a genuine,
   simplified interpretive or evaluative component, not fact-scanning alone.
8. Check any idiom or slang expression against Section 0.4: is it classified transparent or opaque, and if opaque,
   is a gloss or confirmation step actually present regardless of level? Check idiom density against the band's
   target (0.4).
9. Check the Day 2 refresher text (Section 0.5) against its own ceiling: is it clearly shorter and simpler than the
   Day 1 anchor, on an unrelated topic, and does it reuse most of Day 1's target vocabulary rather than
   introducing new grammar or vocabulary?
10. Check the genre chosen against Section 0.6: is it a genuine rotation (not the same genre as the prior cycle),
    is it calibrated to the band, and does the formatting match that genre's real-world convention?
11. Check Module-objective alignment (Section 0.1): do the comprehension questions and Collaborative Evidence
    Matrix prompts actually exercise the pulled objective's verb (describe/explain/evaluate/argue/etc.), not a
    neighboring Module's skill? If a Describing lesson's questions are mostly cause-and-effect or policy
    evaluation, it has drifted into Explaining or Evaluating territory and needs to be rewritten around genuine
    descriptive tasks.
12. **(New in v2.1)** Check Section 0.7: does each day (Day 1 and Day 2) name a specific board-dependent
    moment, and is that moment something the class could only produce together on a shared board, not a
    restatement of content already printed on a handout or slide? If a lesson's only "board use" is copying target
    words or a debate topic that is already fully printed elsewhere, it fails this check and needs a genuine
    board-dependent task added.
13. **(New in v2.2, reworded in v2.3)** Check Section 0.8, Part A: does Day 1 Phase 1 name the actual
    transferable skill in plain, student-facing language (not just the topic or the target words), and does Day 2
    Phase 3 close with a Closing Transfer Check that has every student produce one new instance of that skill out
    loud, with two or three pairs cold-called to share? A closing moment that only asks students to rate or
    declare their own confidence (a thumbs-up/sideways/down, a show of hands, "who feels confident?") fails this
    check even if it references the right skill: self-report is not evidence, and a visible whole-class confidence
    vote reliably converges on "yes" regardless of whether the skill transferred.
14. **(New in v2.2, reworded in v2.5)** Check Section 0.8, Part B: does the lowest task Level's Phase 3 role differ
    in participation mode from the higher task Levels, not just in stem difficulty? Does the lesson include
    Foundation Support guidance for a student functioning below the lowest task Level's own floor? A Phase 3
    that gives every task Level the identical live, unscripted, whole-class or fishbowl speaking turn, varying only
    the sentence stem's difficulty, fails this check.
15. **(New in v2.4)** Check Section 0.9, Part A: is every paragraph of the anchor text labeled with a sequential
    capital letter, and does every other reference to a paragraph in the lesson (STOP & CHECK questions, Fact
    Finders, the Collaborative Evidence Matrix, board-dependent moments) use that same letter rather than a
    number? If Partner/Shared Reading is the chosen strategy, are the paragraph letters visually distinct from the
    Partner A/Partner B role labels so the two cannot be confused?
16. **(New in v2.4)** Check Section 0.9, Part B: does every real person, place, or reference in the text that is not
    common knowledge, not already glossed by the sentence itself, and not already covered by the target
    vocabulary or idiom/slang spotlight, carry a superscript footnote marker with a corresponding note in the page
    footer? Conversely, are footnotes reserved for genuine background gaps rather than added reflexively to
    every proper noun, and free of any comprehension question that tests footnote content rather than the text
    itself?
17. **(New in v2.5)** Check Section 0.1's Task Levels by band table was applied correctly: does the lesson include
    exactly the right number of task Levels for its band (3 for Beginner, 4 for Intermediate/Advanced/Proficient),
    and does each one cite the correct CSV Level's Reading objective, not an invented difficulty curve?
18. **(New in v2.6)** Check Section 0.10: does Phase 3 use simultaneous small groups sized to a realistic class
    (not a rotating inner/outer circle that leaves most of a small class idle), and does the lesson supply 2-3
    distinct discussion prompts rather than one? If Fishbowl or Concentric Circles is used, is a genuine
    large-class justification present, rather than defaulting to it out of habit?

If a text or task set fails any check, rewrite it before proceeding. Do not proceed to build comprehension
questions on top of a miscalibrated text, and do not finalize a matrix where the lowest task Level is fact-retrieval
only.

### 0.4 Idioms and slang: scale by transparency, not by level

Students respond well to idioms and slang, so every anchor text from Level 2 upward should include at least one.
The rule is NOT a level gate ("no idioms below X, stop glossing above Y"). It is a transparency/frequency rule
that applies at every level.

Classify each candidate expression as transparent or opaque before deciding how to handle it. A transparent
(functional) chunk is one whose meaning is recoverable from its parts and everyday use ("no way," "for sure,"
"hang on a second," "a big deal"). An opaque (figurative) idiom is one whose meaning cannot be derived from its
literal words ("kick the bucket," "under the weather," "cost an arm and a leg," "spill the beans").

Transparent chunks can appear from Level 2 onward, lightly glossed or left for incidental pickup, since their
meaning is largely guessable in context and low-risk if missed.

Opaque idioms require explicit glossing or a brief teacher confirmation at every level, including Levels 7 and 8.
Do not phase out glossing for idioms at the top of the program on the assumption that advanced students can
infer figurative meaning from context alone. Research on advanced (C1-C2) learners inferring idioms from
context without glossing found no significant comprehension advantage over glossed presentation, and incorrect
inferences tend to persist even after correction. Treat "infer this idiom's meaning entirely unassisted" as a task to
avoid at any level.

What changes with level is density and register, not glossing. Lower levels (2-4): one or two transparent chunks
per text, tied to the topic, always glossed. Middle levels (5-6): two to three idioms per text, mixing transparent
chunks with one opaque idiom, still glossed. Upper levels (7-8): higher density (three to five expressions), more
opaque and register-marked idioms/slang, and students can confirm or refine a guessed meaning against a
provided gloss rather than being handed the gloss first, but the gloss or confirmation step never disappears.

Selection criteria: favor idioms that are high-utility, reasonably fixed in form, and teachable in one short aside;
avoid obscure, archaic, or region-specific slang needing a paragraph of explanation.

Where to place it: in the anchor text itself (naturally, not shoehorned in), with the gloss delivered as a brief inline
bracket, footnote-style box, or a Phase 1 pre-teaching item. A short "Idiom/Slang Spotlight" callout box works
well. Do not let idiom glossing crowd out the 4-6 target-vocabulary budget; treat it as a small addition on top.

### 0.5 Day 2 vocabulary refresher text (Phase 1 addition)

In addition to the existing 3-minute partner re-scan of the Day 1 anchor text, Day 2 Phase 1 should include a
short secondary reading that recycles Day 1's target vocabulary in a new context:

- **Topic:** unrelated to the Day 1 anchor text. The refresher text should be on a different topic entirely,
  connected to Day 1 only through vocabulary reuse, not subject matter. Recycling the same words in an
  unrelated context gives students a cleaner test of whether they actually know the word (not just the passage)
  and produces stronger retention than re-reading the original topic. Spacing/recycling research on vocabulary
  review favors semantically varied re-exposure over massed same-topic repetition.
- **Reuse target:** aim to reuse at least 5 of the 4-6 words pre-taught on Day 1 (i.e., most or all of them), plus
  1-2 words from the idiom/slang spotlight if one was used.
- **Length and complexity:** shorter and simpler than the Day 1 anchor text, never harder. Target roughly
  one-third to one-half the Day 1 anchor's word count, capped at or below the Day 1 text's own Section 0.2
  sentence-length and grammar ceiling for that level. This is a warm-up, not a second anchor text: it must never
  introduce new grammar structures or vocabulary beyond the recycled set plus ordinary high-frequency
  connective language.
- **Form:** a short paragraph or two, or a short functional text (a notice, a text message exchange, a short news
  blurb) appropriate to the level's Section 0.2 form guidance. It does not need Day 1's full genre or formatting
  treatment.
- **Task:** 3-4 minutes, light-touch: a quick gist question, a "find these 5 words and circle them" scan, or a
  1-sentence oral summary to a partner. This should not become a second comprehension-question set.
- **Caution at lower levels:** at Levels 1-2, keep the topic shift gentle (a different everyday scenario, not a
  wholly abstract new domain). Topic-varied recycling helps retention on average, but very low-proficiency
  learners can find an unrelated context harder to bridge back to the target words than a same-topic one. If a
  Level 1-2 refresher text is not landing as an easy warm-up, narrow the topic gap rather than abandoning the
  recycling approach.
- **Where this lives in the phase:** the existing 15-minute Day 2 Phase 1 slot now contains three short pieces:
  the 3-minute Day 1 re-scan, this new refresher text plus its quick task (aim for 8-9 minutes), and the spoken
  vocabulary mastery activity (aim for 3-4 minutes). Trim the oral word-forms drill if needed to keep Phase 1
  inside its 15-minute budget.

### 0.6 Genre and text-type rotation (expanded)

"Genre Rotation" means varying the actual text TYPE the anchor is written as, not just changing the topic while
always defaulting to a generic expository article. Rotate genuinely across cycles using a bank appropriate to the
band, and adapt the Reading Execution Rules, formatting, and task design to fit the chosen genre's real-world
conventions. Use Section 0.2's word count/complexity ceiling for the target level regardless of genre; genre
changes form and voice, never the ceiling.

- **Beginner (1-2):** Picture-supported label sets and short notices (signs, simple ads); short personal notes,
  texts, or postcards; simple dialogues/exchanges (2-4 lines); very short how-to/instruction lists (3-5 steps).
- **Intermediate (3-4):** Short narrative/personal-story articles; simple newspaper-style news briefs
  (who/what/when/where lead, short follow-up); how-to/instructional guides; short interview transcripts (Q&A
  format); simple email/message exchanges; short field-journal or diary-style entries; **text-message/chat
  threads** (a short exchange of casual messages, distinct in register and formatting from an email); **product
  listings/descriptions** (an e-commerce-style write-up of a real, everyday product type).
- **Advanced (5-6):** Feature-style newspaper or magazine articles; short stories with a clear narrative arc;
  opinion/editorial pieces (single clear stance); interview or profile pieces; travel/field-journal narrative; product
  or place reviews; short policy or issue explainers; **social media post threads** (an original post plus several
  replies, distinct from an interview's clean turn-taking); **advice-column letters with response** (a reader's
  letter followed by a columnist's reply, single clear structure).
- **Proficient (7-8):** Full newspaper feature or investigative-style articles; literary short story excerpts;
  editorial/op-ed with rhetorical complexity; formal debate transcripts or dual-perspective point-counterpoint
  pieces; academic-style explainer or research-summary excerpts; satire or irony-dependent pieces (Level 8
  only); **podcast transcript excerpts** (dialogue-heavy, naturalistic register, distinct from the cleaner Q&A
  interview format); **historical primary-source-style documents** (a period letter or diary entry, invented but
  written in a period-appropriate voice, vocabulary still capped at the level's own Section 0.2 ceiling despite the
  period flavor).

Formatting implications per genre: apply the matching convention, not generic paragraph formatting.
Newspaper/news brief: headline, byline-style dateline, inverted-pyramid structure, short paragraphs. Short
story/narrative: paragraph-based prose, dialogue formatting with quotation marks. Interview/Q&A: speaker
labels, turn-based formatting. How-to/instructions: numbered or bulleted steps, imperative verb forms.
Email/message exchange: greeting/sign-off conventions, subject line where relevant. Editorial/opinion: clear
thesis placement, signaled stance language matching the level's evaluative-vocabulary ceiling. Debate/
point-counterpoint: two clearly labeled voices or columns, parallel structure. **Text-message/chat thread:**
short sender-labeled turns, timestamps optional, casual register (informal contractions, no salutation/sign-off),
each turn short enough to read as a real message rather than a paragraph in disguise. **Product listing/
description:** a short lead description paragraph followed by a bulleted feature list and a spec line or two,
matching how a real listing actually reads rather than one continuous block of prose. **Social media post
thread:** a labeled original post (short, under a stated character-style limit) followed by several labeled replies
indented or marked as replies, light use of a hashtag where natural. **Advice-column letter with response:** the
reader's letter in first person with its own short salutation/sign-off, followed by the columnist's reply with a
distinct byline-style signature; keep the two voices visually separated. **Podcast transcript excerpt:** speaker
labels (by name or role) at each turn, natural-speech markers appropriate to the level (false starts or fillers only
at Proficient, and sparingly), no narrative prose framing between turns. **Historical primary-source-style
document:** a period-appropriate dateline and salutation (for a letter) or dated entry heading (for a diary),
first-person voice, without slipping into vocabulary above the level's own Section 0.2 ceiling just because the
register is period-flavored.

Do not repeat the same genre in two consecutive 2-Day cycles for the same class. When a genre implies a
register or structural feature above the band's ceiling (e.g. satire requires inference beyond Level 6), reserve
that genre for the band where it is calibrated rather than attempting a "simplified" version that strips out the
feature that defines the genre.

### 0.7 Board-dependent moments (new in v2.1)

This section is new in v2.1. It was added after classroom feedback that generated lessons, while rich in printed
handouts, tiered matrices, and oral protocols, gave the teacher no genuine reason to use the physical whiteboard.
Structural richness elsewhere in the lesson (timelines, matrices, debate protocols) must not be mistaken for
board use, and board use must not be satisfied by a trivial gesture toward the board.

Each Day 1 and Day 2 must include at least one board-dependent moment: an activity for which the whiteboard
(or equivalent shared writing surface) is structurally necessary, not optional. A board-dependent moment has at
least one of these properties:

- **Co-constructed live:** the content going onto the board is generated by student responses in real time, not
  pre-written by the teacher or pre-printed on a handout. Nobody in the room knows the final content until the
  class produces it together.
- **Synthesizes distributed input:** the board is the only place where information scattered across individual
  students, pairs, or task Levels (for example, the several task Levels of a Collaborative Evidence Matrix) gets
  combined into one shared, visible whole. No single student's handout contains the complete picture.
- **Persists and gets built on:** content is started on the board on Day 1 and deliberately returned to, added to,
  or checked against on Day 2, giving the board a role no single-day handout can fill.

A board use that only restates material that is already fully printed or projected elsewhere (writing the 4-6 target
vocabulary words up, or copying a debate topic that is already on a handout) does NOT satisfy this requirement.
That is transcription, not a board-dependent moment, and should not be logged as satisfying Section 0.7.

Where board-dependent moments typically fit:

- **Phase 1 (Day 1) activation:** when using a K-W-L Walk, the K and W columns should be built live on the
  board (or a class chart) from student call-outs before reading, not handed to students pre-filled; the L column
  is completed as a whole-class board activity after reading, on Day 1 or in Day 2 Phase 1. When using Mystery
  Quote, student guesses about the quote's source or meaning are collected on the board before reading and
  checked off against the text afterward.
- **Phase 2 (Day 2) Collaborative Investigation:** build a shared graphic organizer on the board as each
  mixed-ability group reports back, so the class synthesis exists only once every task Level has contributed.
  Match the organizer to the Module's actual skill per Section 0.1: a comparison T-chart or Venn diagram for
  Describing, a cause-and-effect chain for Explaining, a criteria/verdict rubric for Evaluating, a two-column
  claims tracker for Arguing, a numbered process map for Instructing, and the equivalent structure for Narrating,
  Transacting, and Socializing.
- **Phase 3 (Day 2) Oral Output:** during Phase 3's simultaneous small-group discussion (Section 0.10), a
  single scribe cannot transcribe several groups talking at once in real time. Instead, once each group's
  discussion window ends, have each group report one notable claim or piece of evidence back to the board, so
  the shared board record is built from what groups actually produced, the same synthesize-distributed-input
  pattern already used in Phase 2. Where a large enough class genuinely runs Fishbowl or Concentric Circles
  (Section 0.10), keep a running board record of claims or evidence AS THEY ARE ACTUALLY SPOKEN instead,
  since that format does have a single visible circle to transcribe from; this gives the board a real-time
  transcription role that the printed stems cannot replace, and it feeds the closing whole-class synthesis.

Every lesson does not need a board-dependent moment in all three of these slots; one genuine instance per day,
correctly matched to that day's structure, satisfies Section 0.7. Prefer Phase 2 (Day 2) as the anchor slot when in
doubt, since the tiered-matrix synthesis is the strongest natural fit across every Module.

Self-check: see Section 0.3, item 12.

### 0.8 Skill Spotlight, closing transfer check, and differentiated participation (new in v2.2, Part A corrected in v2.3, Part B reworded in v2.5)

This section is new in v2.2. It was added after feedback that generated lessons, while full of vocabulary practice,
reading practice, and speaking practice, gave students no clear moment of feeling they had learned something,
and gave a genuinely low-level student in the room no real way to participate in Phase 3 beyond an easier
sentence stem attached to the same live speaking task as everyone else. Part A's closing mechanism was
corrected in v2.3: see the note below.

**Part A: Skill Spotlight and closing transfer check**

Every lesson practices a specific transferable skill (the Module's actual verb from Section 0.1: describing,
explaining, evaluating, arguing, and so on, applied through a concrete strategy such as "finding a comparison" or
"spotting a word that signals the writer's attitude"). Right now that skill is exercised through the tasks but never
named aloud to students, so a lesson can easily read as "we read about a topic and talked about it" rather than
"we got better at something." Two additions fix this without adding a new graded task or artifact:

- **Skill Spotlight (Day 1, Phase 1):** immediately after or alongside the activation hook, state the lesson's actual
  skill in one or two plain, student-facing sentences, separate from the topic. For example, not "Today we're
  reading about Ciudad Perdida" alone, but "Today we're practicing describing a place by comparing it to
  somewhere more familiar, the way the writer compares Ciudad Perdida to Machu Picchu." Tie the wording
  directly to the Module's verb from Section 0.1 so it stays honest about what the lesson actually trains.
- **Closing Transfer Check (Day 2, Phase 3, end of Group Synthesis):** close the lesson by having every student
  apply the exact skill named in the Skill Spotlight to something new, not the anchor text, and produce it out
  loud rather than rate themselves against it. In pairs, every student generates one instance of the skill (for
  Describing: "in one sentence, describe something in this room by comparing it to something else"; for
  Explaining: "in one sentence, explain why something in this room happens the way it does"; for Evaluating: "in
  one sentence, give your verdict on something and one reason"; for Arguing: "in one sentence, state a position
  on something and one reason"; adapt similarly for the remaining Modules using their Section 0.1 verb). The
  teacher then cold-calls two or three pairs to share aloud. This stays oral-only (consistent with the Oral Focus
  constraint) and inside the existing 5-minute synthesis window, and nothing is collected or graded, so it does
  not become a new task or artifact.

Corrected in v2.3: do not close with a self-report (a thumbs-up/sideways/down, a show of hands, or any "can you
do this now?" question answered by the student rating their own confidence). A visible, whole-class confidence
vote reliably converges on "yes" regardless of whether the skill actually transferred, since no student wants to be
the visible outlier. The Closing Transfer Check above replaces that mechanism: the teacher listens for whether
the skill was actually produced, which is evidence, rather than counting how many students claim it was learned,
which is not.

The Skill Spotlight and the Closing Transfer Check's target skill must match exactly. A closing task that exercises
a different skill than the one spotlighted on Day 1 does not close the loop.

**Part B: Differentiated Phase 3 participation**

The Dynamic Tiered Framework already scaffolds Phase 2 (the Collaborative Evidence Matrix) well for the
lesson's lowest task Level: pointing to a sentence, circling a word, completing a sentence starter. Phase 3 must
be scaffolded with the same seriousness. Giving the lowest task Level an easier sentence stem inside the same
live, unscripted, whole-class or small-group speaking turn is not sufficient: the cognitive and affective demand
of real-time public speech is roughly constant across a stem's difficulty, and a genuinely low-level student can be
shut out of the activity even while holding a stem card written at their level.

Give the lowest task Level's student a different participation mode within the same protocol, not just an easier
line to say. Two reliable options: (1) a rehearsed pair-share immediately before their small group's discussion
round begins, where the student says their stem once, quietly, to a partner and gets a thumbs-up, so their first
contribution inside the group is already a repetition; or (2) a listening/tracking role within the group during the
discussion itself (a simple tally sheet marking which side each speaker argues, or which target vocabulary word
they hear), with one fully-prepared sentence to contribute at a natural pause rather than an on-demand turn.

**Foundation Support (below the lowest task Level):** for a student functioning below the band's own floor,
below what the lowest task Level assumes, do not simply reuse the lowest task Level's tasks at a slower pace.
Provide non-verbal or minimally-verbal response modes throughout: matching a picture or a printed word to the
correct target vocabulary term, pointing to the paragraph that answers a Fact Finder question, a two-choice circle
instead of an open sentence completion, and in Phase 3 a role limited to physical participation (moving to a side
of the room per the Stand Up/Move activity, holding up a prepared word or picture card at the right moment)
rather than any spoken turn. Pair this student with a peer buddy for the paired-reading and matrix steps. This is
support to be added on top of the lowest task Level, not a replacement for it: most classrooms will not need it
every cycle, but the lesson should say explicitly where it plugs in for the cycles that do.

Self-check: see Section 0.3, items 13 and 14.

### 0.9 Paragraph lettering and contextual footnotes (new in v2.4)

This section is new in v2.4. It adds two small but load-bearing formatting conventions, requested after generated
lessons proved awkward to discuss aloud ("paragraph 4, no, the one with the plazas") and left real-world names
and references (a mountain range, a glacier, a city known for violin-making) sitting in the text with no way for a
curious student to look them up, the way a real textbook would handle it with a footnote.

**Part A: Paragraph lettering**

Label every paragraph of the Day 1 anchor text with a sequential capital letter (A, B, C, and so on), not just an
implicit position in the text. This lets STOP & CHECK questions, Fact Finders, the Collaborative Evidence Matrix,
board-dependent moments, and classroom discussion all refer to "Paragraph C" precisely and consistently,
rather than counting paragraphs or describing them ("the one about the plazas") each time.

- **Format:** place a bold letter marker in brackets, e.g. "[A]", immediately before each paragraph of the anchor
  text. Use the letter form everywhere else in the lesson a paragraph is referenced (a Fact Finder that says
  "Paragraph 4" must instead say "Paragraph D"; a matrix item that says "Paragraphs 1-4" must say "Paragraphs
  A-D").
- **Partner A/Partner B conflict:** the Partner/Shared Reading strategy already uses "Partner A" and "Partner B"
  as reader-role labels (see Reading Execution Rules). Because paragraph letters and partner-role letters can
  both be "A" in the same lesson, keep them visually distinct: paragraph letters are always bracketed ("[A]"),
  partner-role labels are always spelled out in full ("Partner A", never just "A"). A turn-taking instruction under
  this strategy should read "Partner A reads Paragraphs [A]-[B]" so a reader can never confuse the two.
- Apply the same lettering to the Day 2 refresher text when it runs more than one paragraph. A single-paragraph
  refresher text does not need a letter.

**Part B: Contextual footnotes**

Footnotes are a third, distinct layer of support, separate from the 4-6 target vocabulary words (Phase 1) and the
Idiom/Slang Spotlight (Section 0.4). Vocabulary and idioms support the language needed to decode the
sentence; footnotes support background or world knowledge the text assumes but does not supply, the way a
textbook footnotes a historical figure or a foreign term.

- **When to add one:** the anchor text names a real person, place, historical event, or specialized/cultural
  reference that (a) is unlikely to be common knowledge at the target band, (b) is not already explained by the
  sentence itself (an appositive like "Ciudad Perdida, the Lost City" already glosses itself and needs no
  footnote), and (c) is not already covered by the target vocabulary list or the idiom/slang spotlight.
- **Format:** mark the term at its first mention with a superscript numeral in the body text, and list the
  corresponding numbered note in a footer at the bottom of the same page. Keep each note to one short, plain
  sentence, written inside the same Section 0.2 vocabulary ceiling as the anchor text itself: a footnote in a Level
  3 text should not require Level 6 vocabulary to explain.
- **Density:** footnotes are genuinely occasional, typically 1-3 per anchor text. A text that seems to need many
  more has too much unexplained real-world density for its band and should be revisited against Section 0.3,
  item 5 (the numbers/named-entities check), rather than patched with a long footnote list.

Footnotes are informational only. Do not write a comprehension question, Fact Finder, or matrix item that tests
footnote content; the footnote supports background understanding, it is not part of the skill being assessed.

Self-check: see Section 0.3, items 15 and 16.

### 0.10 Phase 3 discussion format: simultaneous small groups, not a rotating circle (new in v2.6)

This section is new in v2.6, added after classroom feedback that Fishbowl and Concentric Circles do not work
at realistic class sizes - and independently, after the Student Print Formatting Prompt v1 reached the same
conclusion for its own packets (its Section 2.9 already says a class of realistic size, 8-12 students, "cannot be
usefully split into an inner circle that talks and an outer circle that only listens"). Both formats assume a class
large enough that splitting off a 5-6 student inner circle still leaves a meaningful outer circle of observers who
rotate in over time. At a realistic class size (roughly 8-12 students), an inner circle of 5-6 already contains most
of the room, leaving only 2-4 students to "observe" - and a single question circulating through one small circle
for the full 30-minute Phase 3 window is redundant, not differentiated practice, for the students waiting outside it.

**Default format: simultaneous small groups.** Divide the class into small groups (aim for 3-4 students per
group, mixed task Level where possible) that all discuss at the same time, not a format where only one group is
speaking while the rest watch. To make simultaneous groups work without every group having an identical,
redundant conversation, the lesson must supply 2-3 distinct discussion prompts (not one), related but not
identical, so different groups (or a rotation of groups through stations) are working different angles of the same
core question. Sentence stems by task Level (Section 0.8, Part B) apply across all prompts and do not need to
be written per-prompt.

This replaces Fishbowl and Concentric Circles/Speed-Dating as the default choices in the Phase 3 Output
Rotation bank (Style & Formatting Constraints, below). Both remain available only where a class is genuinely
large enough (roughly 16+ students) that an inner/outer split still leaves a real audience with a real reason to
watch; do not default to either out of habit or because they read as more "structured." Town Hall Role-Play and
Jigsaw Expert Panels already suit simultaneous small groups (Jigsaw is small-group by construction; Town Hall
can run as several small simultaneous "town halls," one per group, each with its own moderator role) and
remain in active rotation as the primary protocols alongside the plain small-group discussion carousel described
above.

**Board-dependent moment, adapted:** see Section 0.7's Phase 3 entry - a single scribe cannot transcribe
several simultaneous groups in real time, so the board-dependent moment (where Phase 3 carries it) is built from
groups reporting back after their discussion window, not live transcription during the discussion itself.

Self-check: see Section 0.3, item 18.

---

## Unit Architecture: 2-Day Text Cycle Model

Every unit of instruction must span two 75-minute lessons centered on a single core anchor text, calibrated per
Section 0. Rather than introducing a new passage daily, Day 1 focuses on text decoding, strategy execution, and
literal comprehension, while Day 2 focuses on re-engagement, multi-level analysis, and structured oral
production.

**2-DAY TEXT CYCLE OVERVIEW (150 MIN TOTAL)**

DAY 1: COMPREHENSION & TEXT DECODING (75 MIN)
- Phase 1: Pre-Reading & Activation (15 min)
- Phase 2: Text Engagement & Strategy Execution (35 min)
- Phase 3: Day 1 Literal Comprehension & Vocab Context Check (25 min)

DAY 2: DEEP ANALYSIS, EVALUATION & PRODUCTION (75 MIN)
- Phase 1: Text Re-Engagement & Vocab Warm-Up (15 min)
- Phase 2: Collaborative Multi-Level Investigation (30 min)
- Phase 3: Structured Oral Output Debate & Synthesis (30 min)

### Reading Execution Rules & Adaptive Structural Integration

Strictly avoid unrehearsed round-robin reading (cold-calling students to read aloud one-by-one). Always specify
the chosen reading strategy for the lesson and fully adapt the lesson content and formatting to support that
specific strategy directly:

**Whole-Class & Modeling Strategies**
- Teacher Read-Aloud with Interactive Stops: Embed explicit, pre-written teacher pause points directly into the
  text layout (e.g., [STOP & CHECK 1: Ask "Why did..."]) with designated comprehension or vocabulary check
  questions.
- Choral Reading: Format the text with clear section breaks, rhythm markers, or staggered chorus/solo cues
  where appropriate.
- Echo Reading: Segment the text into short, highly expressive phrases separated by clear echo markers (e.g., /
  or [ECHO]).
- **Think-Aloud Modeling:** Embed explicit teacher think-aloud prompts directly into the text layout (e.g.,
  [THINK-ALOUD: model wondering what this word means from context]), distinct from Teacher Read-Aloud
  with Interactive Stops in that the teacher verbalizes their own reasoning process rather than checking student
  comprehension at that pause point.

**Peer & Small-Group Strategies**
- Partner / Shared Reading: Format text with explicit partner turn-taking markers (e.g., Partner A reads
  Paragraphs [A]-[B], Partner B reads Paragraphs [C]-[D]) and brief turn-checking prompts. See Section 0.9,
  Part A for why the bracketed paragraph letters and the spelled-out Partner A/Partner B role labels must stay
  visually distinct.
- Peer-Assisted Learning Strategies (PALS): Include structured Coach/Reader prompt cards, step-by-step re-tell
  checklists, and peer feedback prompts alongside the text.
- Whisper Reading: Provide self-paced student focus questions and a Teacher Circulation Checklist with
  targeted oral coaching prompts for individual check-ins.
- **Say Something:** Segment the text into short chunks separated by clear pause markers (e.g., [PAUSE: say
  something to your partner]); at each marker, both partners briefly react, question, or connect before reading
  on. Lighter-weight than the four fixed Reciprocal Teaching roles, since either partner can say anything (a
  reaction, a question, a connection), not a role-assigned response.

**Comprehension & Performance Strategies**
- Reciprocal Teaching: Structure the text with dedicated role prompts and graphic organizer templates for the
  four assigned roles (Summarizer, Questioner, Clarifier, Predictor).
- Reader's Theater: Format the passage as an explicit script with assigned speaker roles, stage directions, and
  repeated rehearsal cues.
- **Close Reading with Annotation:** Provide a guided annotation key (e.g., underline unfamiliar words, circle
  connector words, bracket the sentence that states the main idea) and margin space or callout boxes for
  students to mark the text individually before any discussion; best suited to Advanced/Proficient independent
  readers.

### Relative Multi-Level Strategy: Dynamic Tiered Framework

To serve a multi-level classroom centered on a single core text, design all Day 1 and Day 2 comprehension and
discussion tasks using an anchor-based, band-scoped task-Level system: one task per Level in that band's Task
Levels row (Section 0.1) - three task Levels for Beginner, four for Intermediate, Advanced, and Proficient - each
built to satisfy that Level's own Reading-modality CSV objective, never an invented difficulty curve.

Every task, regardless of which Level it targets, falls into one of three roles depending on its position in the
band's Task Levels row:

| Role | Where it sits | Task Strategy |
|---|---|---|
| Extension-down task(s) | A Level borrowed from the neighboring lower band | Literal comprehension, scanning for direct facts, visual key details, sentence completion. Scaffolds: sentence starters, option choices, word banks, direct paragraph pointers. In Phase 3 (see 0.8): a different participation mode, not just an easier stem - rehearsed pair-share before their small group's turn, or a listening/tracking role with one prepared line. |
| Native task(s) | The band's own two Levels (the lower of which is also the anchor level) | Core comprehension, main ideas, cause-and-effect, standard inference appropriate to that Level's own ceiling (Section 0.2). Scaffolds: guided short-answer prompts, clear question cues. |
| Extension-up task(s) | A Level borrowed from the neighboring higher band | Deeper inferencing, text synthesis, critical evaluation of claims, weighing counter-arguments, capped strictly at that Level's own ceiling (Section 0.2) - never drifting toward the Level beyond it. Scaffolds: open-ended analytical prompts, perspective-taking tasks, synthesis frames. |

Recall from Section 0.1 that Beginner has one extension-up task and no extension-down task (3 total); Proficient
has two extension-down tasks and no extension-up task (4 total); Intermediate and Advanced each have one of
each (4 total).

- **Anchor-Driven:** the anchor text is defined by the band's lower level (Section 0.1), calibrated per Section 0,
  avoiding rigid baseline labels like "Foundation" or "Advanced."
- **Interdependent Roles:** the extension-down task(s) establish the factual foundation, the band's native task(s)
  map the logical connections, and the extension-up task(s) evaluate the broader impact and weigh evidence -
  each one strictly at its own assigned Level's ceiling (Section 0.2), never drifting into the Level beyond it.
- **Seamless Collaboration:** because all task Levels focus on the exact same passage and theme across both
  days, format activities so students working different task Levels can partner up without breaking class
  cohesion.

**Respectful Tiers (required check):** every task Level must reach the same essential understanding of the text
and be equally engaging: none of them is "the interesting one." The lowest task Level must not be limited to rote
fact-copying while only the higher task Levels get to interpret, evaluate, or discuss meaning; give the lowest task
Level its own genuine (simpler, more scaffolded) interpretive or evaluative task, not just a scanning task. Before
finalizing the Collaborative Evidence Matrix, check: would a student working the lowest task Level, having only
done their own tier, feel they did "the easy busywork" while the higher task Levels did "the real thinking"? If yes,
add an interpretive component to the lowest task Level's work (e.g. a simple opinion question with a word bank,
not just fact retrieval) and revise. This check applies to every task Level in the Task Levels by band table
(Section 0.1): it is not a one-time fix, it is a standing requirement on every generated matrix.

**New in v2.2 (Respectful Tiers extends into Phase 3):** the same test applies to the oral protocol as to the
matrix: would a student at the lowest task Level, given only an easier stem inside the same live public-speaking
format, feel shut out of real participation while the higher task Levels did "the real talking"? If yes, give that
student a genuinely different participation mode (rehearsed pair-share first, or a listening/tracking role), not just
simpler words for the same turn. See Section 0.8, Part B, for the Foundation Support layer for students below the
lowest task Level's own floor.

### 2-Day Lesson Structure & Detailed Flow

**DAY 1: COMPREHENSION & TEXT DECODING (75 MIN)**

*Phase 1: Pre-Reading & Activation (15 Min)*
- Spark curiosity before introducing the text using visual prompts, open-ended opinion questions, or interactive
  movement activities (e.g., Stand Up/Move, Four-Corners). Keep discussion-question language at or near the
  anchor level's reading ceiling for the band; do not open with abstract philosophical framing calibrated to a
  higher band.
- Skill Spotlight (see Section 0.8): immediately after or alongside the activation hook, state the lesson's
  transferable skill in one or two plain, student-facing sentences, separate from the topic. This is the exact skill
  Day 2's Closing Transfer Check asks students to reproduce.
- Pre-teach 4 to 6 high-yield target keywords during activation to prevent decoding barriers using in-context
  paragraph matching. Target keywords must come from the anchor text itself and must respect the vocabulary
  ceiling in Section 0.2 for the band's lower level.
- If the anchor text includes an idiom or slang expression (Section 0.4), introduce it here as a brief "Idiom/Slang
  Spotlight" alongside the target keywords, on top of (not instead of) the 4-6 word budget. Opaque idioms get a
  gloss or guided-confirmation step at every level; do not skip this step at upper levels.

*Phase 2: Text Engagement & Strategy Execution (35 Min)*
- Execute reading using the chosen strategy, fully incorporating its required structural elements (e.g., embedded
  stops, role guides, or turn-taking indicators).
- Include clear paragraph markers and explicit check-in frames.
- The anchor text itself must pass the Section 0.3 self-check before this phase is finalized.

*Phase 3: Day 1 Literal Comprehension & Vocab Context Check (25 Min)*
- Conduct a rapid factual check using quick-scanning items pitched at the lesson's task Levels: a Fact Finder set
  for the lowest task Level and a Cause & Effect set for the band's native Level(s).
- Execute a post-reading vocabulary context completion exercise using target terms from Phase 1.

**DAY 2: DEEP ANALYSIS, EVALUATION & PRODUCTION (75 MIN)**

*Phase 1: Text Re-Engagement & Vocab Warm-Up (15 Min)*
- 3-Minute Partner Re-Scan: Students pair up to quickly scan the Day 1 anchor text for key details, dates, and
  paragraph markers.
- Vocabulary Refresher Text (8-9 Min): Students read a short secondary text on an unrelated topic that recycles
  most of Day 1's target vocabulary (and idiom/slang, if used), per Section 0.5, then complete a light gist or
  word-scan task.
- Spoken Vocabulary Mastery (3-4 Min): Reinforce target vocabulary through oral word form practice (e.g., Noun
  vs. Verb usage) or oral scenario questions.

*Phase 2: Collaborative Multi-Level Investigation (30 Min)*
- Execute the Collaborative Evidence Matrix using mixed-ability groups sized to the band's task-Level count
  (Section 0.1): triads of 3 for Beginner, groups of 4 for Intermediate/Advanced/Proficient, one student per task
  Level.
- Each student completes their assigned task Level as a quick rehearsal prep tool, then shares orally to combine
  knowledge for the team discussion.
- Every task Level above the anchor level must stay at its own assigned Level's ceiling (Section 0.2), not
  escalate into the Level beyond it (no unstated-premise/rhetorical-manipulation detection at any task Level
  below Level 7).
- **New in v2.1:** This phase is the preferred anchor slot for the Section 0.7 board-dependent moment - build a
  shared graphic organizer on the board live, as each group reports its task Level's findings (see Section 0.7 for
  the organizer-to-Module mapping).

*Phase 3: Structured Oral Output Debate & Synthesis (30 Min)*
- Shift all primary post-reading performance tasks toward oral communication (structured discussions, debates,
  interactive speaking). Omit standalone formal writing assessments (such as essays or written grammar drills).
- Use the simultaneous small-group discussion format (Section 0.10) by default: divide the class into small
  groups that all discuss at once, working across 2-3 distinct prompts written into the lesson, not one prompt
  circulating through a single rotating circle. Scaffold discussions using explicit sentence frames (e.g., "I agree
  with... because...", "On the other hand..."). Reserve Fishbowl, Town Hall's single-circle variant, or Concentric
  Circles for a class genuinely large enough that an inner/outer split still leaves a real audience (Section 0.10).
- Include role-specific scaffolded sentence stems mapped to every task Level in the lesson (Section 0.1) so all
  learners actively participate in the discussion. Keep each stem's vocabulary/grammar inside its own assigned
  Level's ceiling; do not issue a stem written at a register beyond the Level it's assigned to.
- Differentiated participation (see Section 0.8, Part B): the lowest task Level's role in the protocol must differ in
  participation mode, not only in stem difficulty - a rehearsed pair-share before their small group's discussion
  begins, or a listening/tracking role with one prepared line, rather than the same on-demand live turn as the
  higher task Levels. Where a Foundation Support student is present, give them a non-verbal or minimally-verbal
  role in the same protocol.
- Closing Transfer Check (see Section 0.8, Part A): end Group Synthesis by having every student produce, in
  pairs and out loud, one new instance of the Day 1 Skill Spotlight's skill applied to something other than the
  anchor text, then cold-call two or three pairs to share. Do not close with a self-report (thumbs-up/sideways/
  down or a show of hands) - see Section 0.8 for why. Keep this inside the existing synthesis window; nothing is
  collected or graded.

### Style & Formatting Constraints

- **Pacing Diagrams:** Always include a visual ASCII text timeline diagram at the start of both Day 1 and Day 2
  specifying time allocations for each phase.
- **No Em-Dashes:** Never use em-dashes anywhere in the generated content. Use standard hyphens, colons, or
  parentheses instead.
- **Oral Focus:** Prioritize spoken interaction and critical thinking over written grammar drills.

**Lesson Variety & Structural Rotation Rule:**
- **Reading Strategy Rotation:** Never use the same reading strategy across two consecutive 2-Day cycles (e.g.,
  alternate between Modeling, Reciprocal Teaching, Partner Reading, and Reader's Theater).
- **Phase 1 Activation Variety:** Alternate activation hooks between Visual Inquiry, Four-Corner Debates, Mystery
  Quotes, and K-W-L Walks.
- **Phase 3 Output Rotation (updated in v2.6):** Vary the oral discussion protocol for every cycle among the
  formats suited to simultaneous small groups (Town Hall Role-Play, Jigsaw Expert Panels, or a plain small-group
  discussion carousel rotating through the lesson's 2-3 prompts, per Section 0.10); reserve Fishbowl or
  Concentric Circles/Speed-Dating only for a class large enough that a genuine inner/outer split still leaves a real
  audience.
- **Genre Rotation:** Shift the reading text style across units using the genre bank in Section 0.6 (e.g., Expository
  Article to Field Journal/Narrative to Policy Debate/Interview) while still respecting the Section 0.2 complexity
  ceiling for the target band; a genre shift is not license to raise the register.
- **Board-Dependent Moment Rotation (new in v2.1):** Vary which slot (Phase 1 activation, Phase 2 investigation,
  or Phase 3 synthesis) carries the required board-dependent moment across cycles rather than anchoring it to
  the same phase every time, so the board's role in the lesson stays visibly load-bearing rather than becoming
  its own template.

**Band Calibration is Non-Negotiable:** Structural richness (timelines, debate protocols, tiered matrices) must
never be used to compensate for or disguise a miscalibrated anchor text. A well-developed, correctly-sized Level
3-4 text with excellent scaffolding is correct; both an over-dense Level 6-level text at the Level 3-4 band, and a
thin, underdeveloped text that technically meets a word-count floor but doesn't function as real connected prose,
are miscalibrations.

**Board-Dependent Moments Are Equally Non-Negotiable (new in v2.1):** A lesson that satisfies every ceiling and
structural requirement above but never gives the teacher a genuine reason to use the board fails Section 0.7 and
must be revised before it is finalized.
