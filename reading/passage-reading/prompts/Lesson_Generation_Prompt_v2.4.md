# Passage Reading Lesson Generation Prompt (v2.4, Band-Calibrated)

_Recovered from the original PDF, which was stored as a project doc whose text never extracted correctly. This version is the verbatim text, decoded directly from the PDF's internal compressed content streams, replacing the broken .pdf doc. Renamed in v2.5 from "Reading Lesson Generation Prompt" to "Passage Reading Lesson Generation Prompt" to distinguish this lesson type (a fixed 2-day cycle built around one shared anchor text) from the planned, separate Novel Reading Lesson type; this file is otherwise unchanged and superseded by v2.5._

Band-calibrated revision, addendum  adds Section 0.7 (mandatory board-dependent moments per day),
Section 0.8 (explicit skill naming and a closing transfer check, plus differentiated Phase 3 participation for
low-level learners), and Section 0.9 (paragraph lettering and contextual footnotes) on top of the v2
Band-Calibrated revision's text-complexity ceilings and the original 2-Day Text Cycle structure.
What changed in v2.1: Section 0.7 is new. It requires at least one genuine, board-dependent activity per day
(something co-constructed live by the class, not a restatement of material already on a handout or slide).
Self-check item 12 in Section 0.3 was added to enforce it.
What changed in v2.2: Section 0.8 is new, in two parts. Part A (Skill Spotlight) requires the lesson to name the
actual transferable skill in plain student-facing language at the start of Day 1 and close the loop at the end of Day
2. Part B (Differentiated Participation) requires Phase 3's oral protocol to give Level A a genuinely different
participation mode, not just easier sentence stems inside the same live-debate format, and adds a Foundation
Support layer for students functioning below the band's own floor (below Level A). Self-check items 13 and 14
were added to enforce these.
What changed in v2.3: Section 0.8, Part A's closing mechanism is corrected. The v2.2 draft closed Day 2 with a
thumbs-up/sideways/down self-report against a can-do statement; that is unreliable evidence, since a
whole-class visible confidence vote tends to converge on "yes" regardless of whether the skill actually
transferred (nobody wants to be the visible thumbs-down). v2.3 replaces self-report with a Closing Transfer
Check: every student produces one instance of the skill on something new, out loud to a partner, and the teacher
cold-calls two or three pairs to share, so the evidence is a demonstration, not a declaration. Self-check item 13
was reworded to match.
What changed in v2.4: Section 0.9 is new, in two parts. Part A requires every anchor text's paragraphs to be
labeled with sequential capital letters (A, B, C...) so they can be referenced precisely and consistently across
STOP & CHECK questions, Fact Finders, and the Collaborative Evidence Matrix, instead of by number. Part B
adds textbook-style contextual footnotes: a superscript marker on a real person, place, or reference the text
names but does not explain, with a brief note in the page footer, distinct from target-vocabulary pre-teaching and
the Idiom/Slang Spotlight. Self-check items 15 and 16 were added to enforce these. Everything else in
v2/v2.1/v2.2/v2.3 (Section 0 word-count/complexity ceilings, idiom rules, Day 2 refresher-text rules, genre
rotation, board-dependent moments, Section 0.8) is unchanged.
Adopt a Content-Based Instruction (CBI) and Task-Based Language Teaching (TBLT) framework. Treat reading
as a tool to explore real-world ideas and build critical thinking, allowing language acquisition to occur naturally
through meaningful communication.
This version adds mandatory text-complexity calibration (Section 0) on top of the existing 2-day structure.
Complexity calibration is a hard constraint: if a generated text or task exceeds the target band's ceiling below, it
must be rewritten before anything else in the lesson is finalized.
Section 0.2 update: word-count and paragraph-count targets below are anchored to real published single-lesson
B1-C1 reading materials (British Council LearnEnglish reading texts and Cambridge English exam
specifications), not derived purely from the narrow templated Reading-modality objective statements in the
learning objectives source. The earlier version of this table under-shot real single-lesson text length by roughly
5-8x at the middle levels (it capped Level 3 at 40-70 words; a real single-lesson B1 passage runs 300+ words
across multiple paragraphs). The learning objectives still govern what skill the text must support (grammar range,
vocabulary tier, inference type); the numbers below govern how much text a real lesson needs to be worth
building a 2-day cycle around.
Learning objectives source of record: learningobjectives.csv is the single master file for all learning objectives
across all 8 levels, 3 modalities, and 8 modules (192 rows total: Level, Modality, Module, Description, Example).
Always pull objectives from this CSV, not from the older per-level levelN-import.json files, which are now

derived/legacy exports of the same data and are not guaranteed to reflect the latest revisions.
Scope note: This prompt generates lessons only. To build a differentiated (Level A/B/C) assessment from a set
of completed lessons, use the separate companion prompt assessment-generation-prompt-v1.md. Do not
attempt to generate an assessment from this prompt, and do not use the assessment prompt to generate new
lesson content: the two have different inputs and are not interchangeable.
SECTION 0: BAND CALIBRATION (READ AND APPLY BEFORE
WRITING ANY TEXT)
0.1 How to find the target band
Bands are defined as:
Band
Levels
CEFR
Beginner
1-2
A1-A2
Intermediate
3-4
B1-B1+
Advanced
5-6
B2-B2+
Proficient
7-8
C1-C2
The anchor text and the Level B (default tier) tasks are calibrated to the LOWER level in the band (Level 3 for
Intermediate, Level 5 for Advanced, Level 1 for Beginner, Level 7 for Proficient). Tier C stretches up toward the
upper level in the band (4 / 6 / 2 / 8). Tier A supports below the lower level. This means a two-level band is
served by the existing three-tier (A/B/C) structure without needing a fourth tier, but it also means Level B must
never be written at the upper level's difficulty by default.
Always pull the actual Reading-modality Learning Objective for the lower level and the target Module from
learningobjectives.csv before writing the text: filter by Level = the band's lower level, Modality = Reading, and
Module = the requested module, and use that row's Description and Example as the objective to satisfy. The
anchor text's difficulty is governed ONLY by the Reading-modality objective at that level, not by the
Listening/Speaking or Writing objectives at the same level, which may describe more advanced production skills.
Do not let those inflate the reading text's complexity.
How to specify a lesson request: every generation request must name at minimum a Level (or band) and a
Module (e.g. "Advanced band, Module 6: Arguing"); a topic is optional but recommended. Without a
Level/Module pair, the CSV lookup above cannot happen and the generator has no basis for calibration: do not
proceed to write a text until both are known, either from the request or by asking.
The Module objective governs the task, not just the difficulty. Section 0.2's word count, grammar, and vocabulary
ceilings tell you how hard the text can be; the pulled objective tells you what skill it must actually exercise. Do not
treat the objective only as a difficulty gauge and then default to a generic informational-article task regardless of
Module.

Module 1 (Describing): the core task must be describing a person, object, place, or scene (features,
qualities, comparisons), not summarizing cause-and-effect or evaluating a policy. A Level 4 Describing
text can be an extended description of a real place, but the comprehension work must center on
descriptive features, a comparison, and a stated reason for it, matching the objective's actual verbs.


Module 3 (Explaining): cause-and-effect, process, and "why this happens" content belongs here, not in
Describing.

Module 5 (Evaluating): claims, criteria, and verdicts belong here.

Module 6 (Arguing): weighing two sides toward a position belongs here.

Before finalizing, check the objective's Description against the actual comprehension questions and
Collaborative Evidence Matrix prompts. A text can still mention conservation or environmental threats as
color/context, but the graded tasks must trace back to the Module's actual verb, not drift into a
neighboring Module's skill because it made for an easier debate topic.
0.2 Complexity ceiling by level
These are hard targets for the anchor text at each level: a word-count range, paragraph count, and average
sentence length, plus the grammar/vocabulary/comprehension constraints that keep the text inside the right
band. Word counts are anchored to real published single-lesson materials at each CEFR level (see source note
above), not reverse-engineered from the atomic skill described in the objective. Write toward the middle-to-upper
part of the range, not the floor. A text at or below the floor of its word-count range is a fail, not just a warning sign:
this has happened twice already, an earlier draft produced a 55-word, 4-sentence Level 3 text that technically fit
an old, too-low ceiling but did not function as a real reading passage, and a later batch of Level 3 lessons came
in at 212-246 words against a 280-350 word range despite the correct ceiling being in this document. Count the
words before finalizing, every time; do not estimate.
Level 1 (A1, Beginner floor)

Form: short functional text (a notice, a label set, a short exchange of 2-4 lines) or 1-2 short sentences
using a memorized frame; not necessarily continuous prose

Length: 60-120 words total

Grammar: no verb tense variation beyond one memorized frame; present tense or simple past frame only

Vocabulary: concrete, high-frequency, decodable CVC/simple phonics words only; zero abstract nouns

Sentence length: average 6-10 words/sentence

Comprehension demand: literal match to a picture/object; no inference
Level 2 (A2, Beginner ceiling)

Form: 3-4 short paragraphs (or a short email/note-style text), each built from fixed-frame sentences

Length: 150-220 words total

Grammar: single frame per sentence (simple present or simple past "-ed"); no subordination

Vocabulary: concrete, high-frequency; 3-5 target words per text max

Sentence length: average 8-12 words/sentence

Comprehension demand: literal match with visual support; minimal inference (locating a stated fact)
Level 3 (B1, Intermediate floor  Level B default for the Intermediate band)

Form: 4-5 paragraphs of connected prose (a real short article/narrative, not a template)

Length: 280-350 words total

Grammar: simple present and simple past as the backbone; one coordinating connector per sentence
max (and, because, but); light subordination is acceptable if it stays simple (a single "who/which/that"

clause), but avoid stacking two coordinators or two subordinate clauses in one sentence; no passive
voice

Vocabulary: concrete/familiar-topic vocabulary; 4-6 pre-taught target words; no academic/abstract
vocabulary (avoid words like "extraordinary," "civilization," "habitat," "preserved": these are Level 5+
vocabulary)

Sentence length: average 12-18 words/sentence

Comprehension demand: literal comprehension, scanning for direct facts, basic cause-and-effect; decode
target words in context

Numbers/dates: light factual grounding is fine (a text can mention a year, a place, a few concrete details);
avoid a dense multi-date timeline that turns the passage into a biography-style reference article
Level 4 (B1+, Intermediate ceiling  Tier C target for the Intermediate band)

Form: 5-6 paragraphs, original (non-templated) connected prose

Length: 350-430 words total

Grammar: simple past narrative or present-tense description; one comparison structure; one "because"
reason clause; light subordination throughout, still no dense multi-clause sentences

Vocabulary: concrete + a small set of everyday abstract words (e.g. "reliable," "worth it"); no
technical/academic register

Sentence length: average 15-22 words/sentence

Comprehension demand: identify one comparison, one stated outcome, one directly-stated reason (not
implied); reasons are always explicit ("because I need to carry it every day"), never left for the reader to
infer

Numbers/dates: factual grounding fine; still not a dense multi-date timeline
Level 5 (B2, Advanced floor  Level B default for the Advanced band)

Form: 5-7 paragraphs, connected prose organized logically (not a fixed template)

Length: 400-460 words total

Grammar: mixed past/present, coordination and light subordination (one subordinate clause per sentence
is fine), natural connectors chosen by the writer (not fed as a fixed frame)

Vocabulary: everyday abstract + some topic-specific vocabulary (4-6 pre-taught words), but NOT dense
academic/technical register: avoid nominalizations and Latinate technical terms ("neuroplasticity,"
"paradigmatic," "malleability" are Level 7-8, not 5)

Sentence length: average 17-24 words/sentence

Comprehension demand: summarize organization, identify ONE clearly-signaled implied
attitude/feeling/reservation (a conventional signal like a hedge word or evaluative adjective, not a subtle
unsignaled inference; see the Level 5 and 6 rows in learningobjectives.csv for the exact skill boundary)

Numbers/dates: light factual grounding is fine; still not a dense multi-date chronology
Level 6 (B2+, Advanced ceiling  Tier C target for the Advanced band)

Form: 6-8 paragraphs, fluent connected prose without a fixed template

Length: 460-520 words total


Grammar: complex sentences with sustained control, but not dense academic syntax; register shifts are
simple and signaled clearly, not buried in jargon

Vocabulary: broader abstract/evaluative vocabulary, light topic-specific terms; still avoid
specialist/technical jargon or C1-C2 academic collocations

Sentence length: average 20-28 words/sentence

Comprehension demand: separate stated fact from clearly-signaled evaluative language; locate ONE
visible tonal or register shift partway through the text (e.g. confident language followed by a hedge)
without needing to infer the writer's underlying motive for that shift

Numbers/dates: factual grounding fine; avoid stacking more than 2-3 discrete facts/dates
Level 7 (C1, Proficient floor)

Form: 7-11 paragraphs; two related extended texts (for comparison) OR one dense extended text; full
academic/idiomatic register allowed

Length: 600-700 words (per text, if two texts are used, each can run shorter, roughly 300-400 words each,
as long as the combined comparison task reaches full C1 demand)

Grammar: full complex sentence range, idiomatic phrasing, flexible register

Sentence length: average 20-25 words/sentence

Vocabulary: academic and idiomatic vocabulary appropriate to topic; abstraction is expected

Comprehension demand: critically compare rhetorical choices across two texts OR identify an unstated
interest/assumption/premise; this is where "Chiribiquete"- and "neuroplasticity"-style density actually
belongs
Level 8 (C2, Proficient ceiling)

Form: 8-12 paragraphs; dense, stylistically layered text (irony, understatement, unreliable framing,
dual-audience calibration)

Length: 700-900 words

Grammar/vocabulary: no ceiling; full native-like range expected

Sentence length: average 22-28 words/sentence

Comprehension demand: reconstruct withheld/downplayed meaning, detect manipulation techniques,
assess risk of divergence between literal and real meaning for a specified reader
0.3 Self-check before finalizing (apply to every generated lesson)
Before finalizing Phase 2 (Text Engagement) content, verify against the Level B ceiling for the LOWER level in
the band:

1. Count the words in the anchor text. Is it inside the range for that level? A text at or near the floor of its
range is a warning sign, not just an acceptable minimum: check that it still reads as real connected prose
with enough substance to support two full class periods, not a thin fact-list.

2. Count paragraphs and average sentence length. Does the text match the paragraph count and average
sentence length for that level, not just the total word count? (A single dense 300-word paragraph is not
equivalent to five well-developed 60-word paragraphs; the paragraph count and sentence-length targets
exist precisely to prevent that substitution.)

3. Check clause complexity. Does any sentence exceed the grammar ceiling for that level?


4. Scan the vocabulary. Circle any word that would only appear 2+ bands higher (cross-check against the
vocabulary guidance above). If found, replace it.

5. Count distinct dates/numbers/named entities. If the text reads like a biography or reference article with
a dense timeline, it is miscalibrated: collapse it to the single-topic, moderate-fact-density form the level
requires.

6. Check the Day 2 Level C task against the UPPER level of the band, not two bands up. A Level C task
for the Intermediate band (Level 3-4) should reach the ceiling described for Level 4 above: critical
evaluation is fine, but it should not require C1-level unstated-premise detection (that belongs to Levels
7-8).

7. Check the Collaborative Evidence Matrix against the Respectful Tiers requirement (see the Dynamic
Tiered Framework section below). Level A's task must include a genuine, simplified interpretive or
evaluative component, not fact-scanning alone.

8. Check any idiom or slang expression against Section 0.4: is it classified transparent or opaque, and if
opaque, is a gloss or confirmation step actually present regardless of level? Check idiom density against
the band's target (0.4).

9. Check the Day 2 refresher text (Section 0.5) against its own ceiling: is it clearly shorter and simpler
than the Day 1 anchor, on an unrelated topic, and does it reuse most of Day 1's target vocabulary rather
than introducing new grammar or vocabulary?

10. Check the genre chosen against Section 0.6: is it a genuine rotation (not the same genre as the prior
cycle), is it calibrated to the band, and does the formatting match that genre's real-world convention?

11. Check Module-objective alignment (Section 0.1): do the comprehension questions and Collaborative
Evidence Matrix prompts actually exercise the pulled objective's verb
(describe/explain/evaluate/argue/etc.), not a neighboring Module's skill? If a Describing lesson's
questions are mostly cause-and-effect or policy evaluation, it has drifted into Explaining or Evaluating
territory and needs to be rewritten around genuine descriptive tasks.
12. (New in v2.1) Check Section 0.7: does each day (Day 1 and Day 2) name a specific board-dependent
moment, and is that moment something the class could only produce together on a shared board, not a
restatement of content already printed on a handout or slide? If a lesson's only "board use" is copying target
words or a debate topic that is already fully printed elsewhere, it fails this check and needs a genuine
board-dependent task added.
13. (New in v2.2, reworded in v2.3) Check Section 0.8, Part A: does Day 1 Phase 1 name the actual
transferable skill in plain, student-facing language (not just the topic or the target words), and does Day 2 Phase
3 close with a Closing Transfer Check that has every student produce one new instance of that skill out loud, with
two or three pairs cold-called to share? A closing moment that only asks students to rate or declare their own
confidence (a thumbs-up/sideways/down, a show of hands, "who feels confident?") fails this check even if it
references the right skill: self-report is not evidence, and a visible whole-class confidence vote reliably converges
on "yes" regardless of whether the skill transferred.
14. (New in v2.2) Check Section 0.8, Part B: does Level A's Phase 3 role differ in participation mode from Level
B/C, not just in stem difficulty? Does the lesson include Foundation Support guidance for a student functioning
below Level A's own floor? A Phase 3 that gives every tier the identical live, unscripted, whole-class or fishbowl
speaking turn, varying only the sentence stem's difficulty, fails this check.
15. (New in v2.4) Check Section 0.9, Part A: is every paragraph of the anchor text labeled with a sequential
capital letter, and does every other reference to a paragraph in the lesson (STOP & CHECK questions, Fact
Finders, the Collaborative Evidence Matrix, board-dependent moments) use that same letter rather than a
number? If Partner/Shared Reading is the chosen strategy, are the paragraph letters visually distinct from the

Partner A/Partner B role labels so the two cannot be confused?
16. (New in v2.4) Check Section 0.9, Part B: does every real person, place, or reference in the text that is not
common knowledge, not already glossed by the sentence itself, and not already covered by the target
vocabulary or idiom/slang spotlight, carry a superscript footnote marker with a corresponding note in the page
footer? Conversely, are footnotes reserved for genuine background gaps rather than added reflexively to every
proper noun, and free of any comprehension question that tests footnote content rather than the text itself?
If a text or task set fails any check, rewrite it before proceeding. Do not proceed to build comprehension
questions on top of a miscalibrated text, and do not finalize a matrix where Level A is fact-retrieval only.
0.4 Idioms and slang: scale by transparency, not by level

Students respond well to idioms and slang, so every anchor text from Level 2 upward should include at
least one. The rule is NOT a level gate ("no idioms below X, stop glossing above Y"). It is a
transparency/frequency rule that applies at every level.

Classify each candidate expression as transparent or opaque before deciding how to handle it. A
transparent (functional) chunk is one whose meaning is recoverable from its parts and everyday use ("no
way," "for sure," "hang on a second," "a big deal"). An opaque (figurative) idiom is one whose meaning
cannot be derived from its literal words ("kick the bucket," "under the weather," "cost an arm and a leg,"
"spill the beans").

Transparent chunks can appear from Level 2 onward, lightly glossed or left for incidental pickup, since
their meaning is largely guessable in context and low-risk if missed.

Opaque idioms require explicit glossing or a brief teacher confirmation at every level, including Levels 7
and 8. Do not phase out glossing for idioms at the top of the program on the assumption that advanced
students can infer figurative meaning from context alone. Research on advanced (C1-C2) learners
inferring idioms from context without glossing found no significant comprehension advantage over
glossed presentation, and incorrect inferences tend to persist even after correction. Treat "infer this
idiom's meaning entirely unassisted" as a task to avoid at any level.

What changes with level is density and register, not glossing. Lower levels (2-4): one or two transparent
chunks per text, tied to the topic, always glossed. Middle levels (5-6): two to three idioms per text, mixing
transparent chunks with one opaque idiom, still glossed. Upper levels (7-8): higher density (three to five
expressions), more opaque and register-marked idioms/slang, and students can confirm or refine a
guessed meaning against a provided gloss rather than being handed the gloss first, but the gloss or
confirmation step never disappears.

Selection criteria: favor idioms that are high-utility, reasonably fixed in form, and teachable in one short
aside; avoid obscure, archaic, or region-specific slang needing a paragraph of explanation.

Where to place it: in the anchor text itself (naturally, not shoehorned in), with the gloss delivered as a brief
inline bracket, footnote-style box, or a Phase 1 pre-teaching item. A short "Idiom/Slang Spotlight" callout
box works well. Do not let idiom glossing crowd out the 4-6 target-vocabulary budget; treat it as a small
addition on top.
0.5 Day 2 vocabulary refresher text (Phase 1 addition)
In addition to the existing 3-minute partner re-scan of the Day 1 anchor text, Day 2 Phase 1 should include a
short secondary reading that recycles Day 1's target vocabulary in a new context:

Topic: unrelated to the Day 1 anchor text. The refresher text should be on a different topic entirely,
connected to Day 1 only through vocabulary reuse, not subject matter. Recycling the same words in an
unrelated context gives students a cleaner test of whether they actually know the word (not just the

passage) and produces stronger retention than re-reading the original topic. Spacing/recycling research
on vocabulary review favors semantically varied re-exposure over massed same-topic repetition.

Reuse target: aim to reuse at least 5 of the 4-6 words pre-taught on Day 1 (i.e., most or all of them), plus
1-2 words from the idiom/slang spotlight if one was used.

Length and complexity: shorter and simpler than the Day 1 anchor text, never harder. Target roughly
one-third to one-half the Day 1 anchor's word count, capped at or below the Day 1 text's own Section 0.2
sentence-length and grammar ceiling for that level. This is a warm-up, not a second anchor text: it must
never introduce new grammar structures or vocabulary beyond the recycled set plus ordinary
high-frequency connective language.

Form: a short paragraph or two, or a short functional text (a notice, a text message exchange, a short
news blurb) appropriate to the level's Section 0.2 form guidance. It does not need Day 1's full genre or
formatting treatment.

Task: 3-4 minutes, light-touch: a quick gist question, a "find these 5 words and circle them" scan, or a
1-sentence oral summary to a partner. This should not become a second comprehension-question set.

Caution at lower levels: at Levels 1-2, keep the topic shift gentle (a different everyday scenario, not a
wholly abstract new domain). Topic-varied recycling helps retention on average, but very low-proficiency
learners can find an unrelated context harder to bridge back to the target words than a same-topic one. If
a Level 1-2 refresher text is not landing as an easy warm-up, narrow the topic gap rather than abandoning
the recycling approach.

Where this lives in the phase: the existing 15-minute Day 2 Phase 1 slot now contains three short pieces:
the 3-minute Day 1 re-scan, this new refresher text plus its quick task (aim for 8-9 minutes), and the
spoken vocabulary mastery activity (aim for 3-4 minutes). Trim the oral word-forms drill if needed to keep
Phase 1 inside its 15-minute budget.
0.6 Genre and text-type rotation (expanded)
"Genre Rotation" means varying the actual text TYPE the anchor is written as, not just changing the topic while
always defaulting to a generic expository article. Rotate genuinely across cycles using a bank appropriate to the
band, and adapt the Reading Execution Rules, formatting, and task design to fit the chosen genre's real-world
conventions. Use Section 0.2's word count/complexity ceiling for the target level regardless of genre; genre
changes form and voice, never the ceiling.

Beginner (1-2): Picture-supported label sets and short notices (signs, simple ads); short personal notes,
texts, or postcards; simple dialogues/exchanges (2-4 lines); very short how-to/instruction lists (3-5 steps).

Intermediate (3-4): Short narrative/personal-story articles; simple newspaper-style news briefs
(who/what/when/where lead, short follow-up); how-to/instructional guides; short interview transcripts
(Q&A; format); simple email/message exchanges; short field-journal or diary-style entries.

Advanced (5-6): Feature-style newspaper or magazine articles; short stories with a clear narrative arc;
opinion/editorial pieces (single clear stance); interview or profile pieces; travel/field-journal narrative;
product or place reviews; short policy or issue explainers.

Proficient (7-8): Full newspaper feature or investigative-style articles; literary short story excerpts;
editorial/op-ed with rhetorical complexity; formal debate transcripts or dual-perspective point-counterpoint
pieces; academic-style explainer or research-summary excerpts; satire or irony-dependent pieces (Level
8 only).
Formatting implications per genre: apply the matching convention, not generic paragraph formatting.
Newspaper/news brief: headline, byline-style dateline, inverted-pyramid structure, short paragraphs. Short
story/narrative: paragraph-based prose, dialogue formatting with quotation marks. Interview/Q&A;: speaker

labels, turn-based formatting. How-to/instructions: numbered or bulleted steps, imperative verb forms.
Email/message exchange: greeting/sign-off conventions, subject line where relevant. Editorial/opinion: clear
thesis placement, signaled stance language matching the level's evaluative-vocabulary ceiling.
Debate/point-counterpoint: two clearly labeled voices or columns, parallel structure.
Do not repeat the same genre in two consecutive 2-Day cycles for the same class. When a genre implies a
register or structural feature above the band's ceiling (e.g. satire requires inference beyond Level 6), reserve that
genre for the band where it is calibrated rather than attempting a "simplified" version that strips out the feature
that defines the genre.
0.7 Board-dependent moments (new in v2.1)
This section is new in v2.1. It was added after classroom feedback that generated lessons, while rich in printed
handouts, tiered matrices, and oral protocols, gave the teacher no genuine reason to use the physical
whiteboard. Structural richness elsewhere in the lesson (timelines, matrices, debate protocols) must not be
mistaken for board use, and board use must not be satisfied by a trivial gesture toward the board.
Each Day 1 and Day 2 must include at least one board-dependent moment: an activity for which the whiteboard
(or equivalent shared writing surface) is structurally necessary, not optional. A board-dependent moment has at
least one of these properties:

Co-constructed live: the content going onto the board is generated by student responses in real time, not
pre-written by the teacher or pre-printed on a handout. Nobody in the room knows the final content until
the class produces it together.

Synthesizes distributed input: the board is the only place where information scattered across individual
students, pairs, or tiers (for example, the three tiers of a Collaborative Evidence Matrix) gets combined
into one shared, visible whole. No single student's handout contains the complete picture.

Persists and gets built on: content is started on the board on Day 1 and deliberately returned to, added to,
or checked against on Day 2, giving the board a role no single-day handout can fill.
A board use that only restates material that is already fully printed or projected elsewhere (writing the 4-6 target
vocabulary words up, or copying a debate topic that is already on a handout) does NOT satisfy this requirement.
That is transcription, not a board-dependent moment, and should not be logged as satisfying Section 0.7.
Where board-dependent moments typically fit

Phase 1 (Day 1) activation: when using a K-W-L Walk, the K and W columns should be built live on the
board (or a class chart) from student call-outs before reading, not handed to students pre-filled; the L
column is completed as a whole-class board activity after reading, on Day 1 or in Day 2 Phase 1. When
using Mystery Quote, student guesses about the quote's source or meaning are collected on the board
before reading and checked off against the text afterward.

Phase 2 (Day 2) Collaborative Investigation: build a shared graphic organizer on the board as each
mixed-ability triad reports back, so the class synthesis exists only once all three tiers have contributed.
Match the organizer to the Module's actual skill per Section 0.1: a comparison T-chart or Venn diagram
for Describing, a cause-and-effect chain for Explaining, a criteria/verdict rubric for Evaluating, a
two-column claims tracker for Arguing, a numbered process map for Instructing, and the equivalent
structure for Narrating, Transacting, and Socializing.

Phase 3 (Day 2) Oral Output: during the debate/discussion protocol (Fishbowl, Town Hall, Concentric
Circles, Jigsaw Expert Panels), keep a running board record of claims or evidence AS THEY ARE
ACTUALLY SPOKEN, not a pre-scripted list of the sentence stems already on the handout. This gives the
board a real-time transcription role that the printed stems cannot replace, and it feeds the closing
whole-class synthesis.

Every lesson does not need a board-dependent moment in all three of these slots; one genuine instance per day,
correctly matched to that day's structure, satisfies Section 0.7. Prefer Phase 2 (Day 2) as the anchor slot when in
doubt, since the tiered-matrix synthesis is the strongest natural fit across every Module.
Self-check: see Section 0.3, item 12.
0.9 Paragraph lettering and contextual footnotes (new in v2.4)
This section is new in v2.4. It adds two small but load-bearing formatting conventions, requested after generated
lessons proved awkward to discuss aloud ("paragraph 4, no, the one with the plazas") and left real-world names
and references (a mountain range, a glacier, a city known for violin-making) sitting in the text with no way for a
curious student to look them up, the way a real textbook would handle it with a footnote.
Part A: Paragraph lettering
Label every paragraph of the Day 1 anchor text with a sequential capital letter (A, B, C, and so on), not just an
implicit position in the text. This lets STOP & CHECK questions, Fact Finders, the Collaborative Evidence Matrix,
board-dependent moments, and classroom discussion all refer to "Paragraph C" precisely and consistently,
rather than counting paragraphs or describing them ("the one about the plazas") each time.

Format: place a bold letter marker in brackets, e.g. "[A]", immediately before each paragraph of the
anchor text. Use the letter form everywhere else in the lesson a paragraph is referenced (a Fact Finder
that says "Paragraph 4" must instead say "Paragraph D"; a matrix item that says "Paragraphs 1-4" must
say "Paragraphs A-D").

Partner A/Partner B conflict: the Partner/Shared Reading strategy already uses "Partner A" and "Partner
B" as reader-role labels (see Reading Execution Rules). Because paragraph letters and partner-role
letters can both be "A" in the same lesson, keep them visually distinct: paragraph letters are always
bracketed ("[A]"), partner-role labels are always spelled out in full ("Partner A", never just "A"). A
turn-taking instruction under this strategy should read "Partner A reads Paragraphs [A]-[B]" so a reader
can never confuse the two.

Apply the same lettering to the Day 2 refresher text when it runs more than one paragraph. A
single-paragraph refresher text does not need a letter.
Part B: Contextual footnotes
Footnotes are a third, distinct layer of support, separate from the 4-6 target vocabulary words (Phase 1) and the
Idiom/Slang Spotlight (Section 0.4). Vocabulary and idioms support the language needed to decode the
sentence; footnotes support background or world knowledge the text assumes but does not supply, the way a
textbook footnotes a historical figure or a foreign term.

When to add one: the anchor text names a real person, place, historical event, or specialized/cultural
reference that (a) is unlikely to be common knowledge at the target band, (b) is not already explained by
the sentence itself (an appositive like "Ciudad Perdida, the Lost City" already glosses itself and needs no
footnote), and (c) is not already covered by the target vocabulary list or the idiom/slang spotlight.

Format: mark the term at its first mention with a superscript numeral in the body text, and list the
corresponding numbered note in a footer at the bottom of the same page. Keep each note to one short,
plain sentence, written inside the same Section 0.2 vocabulary ceiling as the anchor text itself: a footnote
in a Level 3 text should not require Level 6 vocabulary to explain.

Density: footnotes are genuinely occasional, typically 1-3 per anchor text. A text that seems to need many
more has too much unexplained real-world density for its band and should be revisited against Section
0.3, item 5 (the numbers/named-entities check), rather than patched with a long footnote list.


Footnotes are informational only. Do not write a comprehension question, Fact Finder, or matrix item that
tests footnote content; the footnote supports background understanding, it is not part of the skill being
assessed.
Self-check: see Section 0.3, items 15 and 16.
0.8 Skill Spotlight, closing transfer check, and differentiated participation
(new in v2.2, Part A corrected in v2.3)
This section is new in v2.2. It was added after feedback that generated lessons, while full of vocabulary practice,
reading practice, and speaking practice, gave students no clear moment of feeling they had learned something,
and gave a genuinely low-level student in the room no real way to participate in Phase 3 beyond an easier
sentence stem attached to the same live speaking task as everyone else. Part A's closing mechanism was
corrected in v2.3: see the note below.
Part A: Skill Spotlight and closing transfer check
Every lesson practices a specific transferable skill (the Module's actual verb from Section 0.1: describing,
explaining, evaluating, arguing, and so on, applied through a concrete strategy such as "finding a comparison" or
"spotting a word that signals the writer's attitude"). Right now that skill is exercised through the tasks but never
named aloud to students, so a lesson can easily read as "we read about a topic and talked about it" rather than
"we got better at something." Two additions fix this without adding a new graded task or artifact:

Skill Spotlight (Day 1, Phase 1): immediately after or alongside the activation hook, state the lesson's
actual skill in one or two plain, student-facing sentences, separate from the topic. For example, not
"Today we're reading about Ciudad Perdida" alone, but "Today we're practicing describing a place by
comparing it to somewhere more familiar, the way the writer compares Ciudad Perdida to Machu Picchu."
Tie the wording directly to the Module's verb from Section 0.1 so it stays honest about what the lesson
actually trains.

Closing Transfer Check (Day 2, Phase 3, end of Group Synthesis): close the lesson by having every
student apply the exact skill named in the Skill Spotlight to something new, not the anchor text, and
produce it out loud rather than rate themselves against it. In pairs, every student generates one instance
of the skill (for Describing: "in one sentence, describe something in this room by comparing it to
something else"; for Explaining: "in one sentence, explain why something in this room happens the way it
does"; for Evaluating: "in one sentence, give your verdict on something and one reason"; for Arguing: "in
one sentence, state a position on something and one reason"; adapt similarly for the remaining Modules
using their Section 0.1 verb). The teacher then cold-calls two or three pairs to share aloud. This stays
oral-only (consistent with the Oral Focus constraint) and inside the existing 5-minute synthesis window,
and nothing is collected or graded, so it does not become a new task or artifact.
Corrected in v2.3: do not close with a self-report (a thumbs-up/sideways/down, a show of hands, or any "can you
do this now?" question answered by the student rating their own confidence). A visible, whole-class confidence
vote reliably converges on "yes" regardless of whether the skill actually transferred, since no student wants to be
the visible outlier. The Closing Transfer Check above replaces that mechanism: the teacher listens for whether
the skill was actually produced, which is evidence, rather than counting how many students claim it was learned,
which is not.
The Skill Spotlight and the Closing Transfer Check's target skill must match exactly. A closing task that exercises
a different skill than the one spotlighted on Day 1 does not close the loop.
Part B: Differentiated Phase 3 participation

The Dynamic Tiered Framework already scaffolds Phase 2 (the Collaborative Evidence Matrix) well for Level A:
pointing to a sentence, circling a word, completing a sentence starter. Phase 3 must be scaffolded with the same
seriousness. Giving Level A an easier sentence stem inside the same live, unscripted, whole-class or
Fishbowl-style speaking turn is not sufficient: the cognitive and affective demand of real-time public speech is
roughly constant across a stem's difficulty, and a genuinely low-level student can be shut out of the activity even
while holding a stem card written at their level.

Give Level A a different participation mode within the same protocol, not just an easier line to say. Two
reliable options: (1) a rehearsed pair-share immediately before the public protocol, where the Level A
student says their stem once, quietly, to a partner and gets a thumbs-up before the whole-class or
Fishbowl round begins, so their first public attempt is already a repetition; or (2) a listening/tracking role
during the protocol itself (a simple tally sheet marking which side each speaker argues, or which target
vocabulary word they hear), with one fully-prepared sentence to contribute at a natural pause rather than
an on-demand turn.

Foundation Support (below Level A): for a student functioning below the band's own floor, below what
Level A assumes, do not simply reuse Level A's tasks at a slower pace. Provide non-verbal or
minimally-verbal response modes throughout: matching a picture or a printed word to the correct target
vocabulary term, pointing to the paragraph that answers a Fact Finder question, a two-choice circle
instead of an open sentence completion, and in Phase 3 a role limited to physical participation (moving to
a side of the room per the Stand Up/Move activity, holding up a prepared word or picture card at the right
moment) rather than any spoken turn. Pair this student with a peer buddy for the paired-reading and
matrix steps. This is support to be added on top of Level A, not a replacement for it: most classrooms will
not need it every cycle, but the lesson should say explicitly where it plugs in for the cycles that do.
Self-check: see Section 0.3, items 13 and 14.

Unit Architecture: 2-Day Text Cycle Model
Every unit of instruction must span two 75-minute lessons centered on a single core anchor text, calibrated per
Section 0. Rather than introducing a new passage daily, Day 1 focuses on text decoding, strategy execution, and
literal comprehension, while Day 2 focuses on re-engagement, multi-level analysis, and structured oral
production.
2-DAY TEXT CYCLE OVERVIEW (150 MIN TOTAL)
DAY 1: COMPREHENSION & TEXT DECODING (75 MIN)
- Phase 1: Pre-Reading & Activation (15 min)
- Phase 2: Text Engagement & Strategy Execution (35 min)
- Phase 3: Day 1 Literal Comprehension & Vocab Context Check (25 min)
DAY 2: DEEP ANALYSIS, EVALUATION & PRODUCTION (75 MIN)
- Phase 1: Text Re-Engagement & Vocab Warm-Up (15 min)
- Phase 2: Collaborative Multi-Level Investigation (30 min)
- Phase 3: Structured Oral Output Debate & Synthesis (30 min)
Reading Execution Rules & Adaptive Structural Integration
Strictly avoid unrehearsed round-robin reading (cold-calling students to read aloud one-by-one). Always specify
the chosen reading strategy for the lesson and fully adapt the lesson content and formatting to support that
specific strategy directly:
Whole-Class & Modeling Strategies

Teacher Read-Aloud with Interactive Stops: Embed explicit, pre-written teacher pause points directly into
the text layout (e.g., [STOP & CHECK 1: Ask "Why did..."]) with designated comprehension or vocabulary
check questions.

Choral Reading: Format the text with clear section breaks, rhythm markers, or staggered chorus/solo
cues where appropriate.

Echo Reading: Segment the text into short, highly expressive phrases separated by clear echo markers
(e.g., / or [ECHO]).
Peer & Small-Group Strategies

Partner / Shared Reading: Format text with explicit partner turn-taking markers (e.g., Partner A reads
Paragraphs [A]-[B], Partner B reads Paragraphs [C]-[D]) and brief turn-checking prompts. See Section
0.9, Part A for why the bracketed paragraph letters and the spelled-out Partner A/Partner B role labels
must stay visually distinct.

Peer-Assisted Learning Strategies (PALS): Include structured Coach/Reader prompt cards, step-by-step
re-tell checklists, and peer feedback prompts alongside the text.

Whisper Reading: Provide self-paced student focus questions and a Teacher Circulation Checklist with
targeted oral coaching prompts for individual check-ins.
Comprehension & Performance Strategies

Reciprocal Teaching: Structure the text with dedicated role prompts and graphic organizer templates for
the four assigned roles (Summarizer, Questioner, Clarifier, Predictor).


Reader's Theater: Format the passage as an explicit script with assigned speaker roles, stage directions,
and repeated rehearsal cues.
Relative Multi-Level Strategy: Dynamic Tiered Framework
To serve a multi-level classroom centered on a single core text, design all Day 1 and Day 2 comprehension and
discussion tasks using an anchor-based 3-tier system. Tier definitions are now anchored to the specific level pair
in the band (see Section 0.1), not to abstract "-1/+1" difficulty:
Tier
Learner Profile
Anchored To
Task Strategy
Level A
(-1 Difficulty)
Slightly below target text level
Below the band's lower level
Literal comprehension, scanning for direct facts, visual key details, sentence completion. Scaffolds: sentence starters, option choices, word banks, direct paragraph pointers. In Phase 3 (new in v2.2, see 0.8): a different participation mode, not just an easier stem  rehearsed pair-share before the public round, or a listening/tracking role with one prepared line.
Level B
(Default Target)
On target with reading text
The band's LOWER level (3 or 5)
Core comprehension, main ideas, cause-and-effect, standard inference appropriate to that level's ceiling (Section 0.2). Scaffolds: guided short-answer prompts, clear question cues.
Level C
(+1 Difficulty)
Slightly above target text level
The band's UPPER level (4 or 6), NOT the next band up
Deeper inferencing, text synthesis, critical evaluation of claims, weighing counter-arguments, capped at the upper level's ceiling (Section 0.2). Scaffolds: open-ended analytical prompts, perspective-taking tasks, synthesis frames.

Anchor-Driven: The default level (Level B) is defined by the target reading passage itself, calibrated per
Section 0, avoiding rigid baseline labels like "Foundation" or "Advanced."

Interdependent Roles: Level A provides the factual foundation, Level B maps the logical connections, and
Level C evaluates the broader impact, all while staying within the band's two-level ceiling, not drifting into
the next band's complexity.

Seamless Collaboration: Because all tiers focus on the exact same passage and theme across both days,
format activities so students from different levels can partner up without breaking class cohesion.
Respectful Tiers (required check): Every tier must reach the same essential understanding of the text and be
equally engaging: none of the three tiers is "the interesting one." Level A must not be limited to rote fact-copying
while only Level B/C get to interpret, evaluate, or discuss meaning; give Level A its own genuine (simpler, more
scaffolded) interpretive or evaluative task, not just a scanning task. Before finalizing the Collaborative Evidence
Matrix, check: would a Level A student, having only done their own tier, feel they did "the easy busywork" while B
and C did "the real thinking"? If yes, add an interpretive component to Level A's task (e.g. a simple opinion
question with a word bank, not just fact retrieval) and revise. This check applies whenever tiers are built for a
specific level pair (band-wide now, or individual levels later): it is not a one-time fix, it is a standing requirement
on every generated matrix.
New in v2.2: Respectful Tiers extends into Phase 3. The same test applies to the oral protocol as to the matrix:
would a Level A student, given only an easier stem inside the same live public-speaking format, feel shut out of
real participation while B and C did "the real talking"? If yes, give Level A a genuinely different participation mode
(rehearsed pair-share first, or a listening/tracking role), not just simpler words for the same turn. See Section 0.8,
Part B, for the Foundation Support layer for students below Level A's own floor.

2-Day Lesson Structure & Detailed Flow
DAY 1: COMPREHENSION & TEXT DECODING (75 MIN)
Phase 1: Pre-Reading & Activation (15 Min)

Spark curiosity before introducing the text using visual prompts, open-ended opinion questions, or
interactive movement activities (e.g., Stand Up/Move, Four-Corners). Keep discussion-question language
at or near the Level B reading ceiling for the band; do not open with abstract philosophical framing
calibrated to a higher band.

Skill Spotlight (new in v2.2, see Section 0.8): immediately after or alongside the activation hook, state the
lesson's transferable skill in one or two plain, student-facing sentences, separate from the topic. This is
the exact skill Day 2's Closing Transfer Check asks students to reproduce.

Pre-teach 4 to 6 high-yield target keywords during activation to prevent decoding barriers using in-context
paragraph matching. Target keywords must come from the anchor text itself and must respect the
vocabulary ceiling in Section 0.2 for the band's lower level.

If the anchor text includes an idiom or slang expression (Section 0.4), introduce it here as a brief
"Idiom/Slang Spotlight" alongside the target keywords, on top of (not instead of) the 4-6 word budget.
Opaque idioms get a gloss or guided-confirmation step at every level; do not skip this step at upper levels.
Phase 2: Text Engagement & Strategy Execution (35 Min)

Execute reading using the chosen strategy, fully incorporating its required structural elements (e.g.,
embedded stops, role guides, or turn-taking indicators).

Include clear paragraph markers and explicit check-in frames.

The anchor text itself must pass the Section 0.3 self-check before this phase is finalized.
Phase 3: Day 1 Literal Comprehension & Vocab Context Check (25 Min)

Conduct a rapid factual check using Level A (Fact Finder) and Level B (Cause & Effect) quick-scanning
items.

Execute a post-reading vocabulary context completion exercise using target terms from Phase 1.
DAY 2: DEEP ANALYSIS, EVALUATION & PRODUCTION (75 MIN)
Phase 1: Text Re-Engagement & Vocab Warm-Up (15 Min)

3-Minute Partner Re-Scan: Students pair up to quickly scan the Day 1 anchor text for key details, dates,
and paragraph markers.

Vocabulary Refresher Text (8-9 Min): Students read a short secondary text on an unrelated topic that
recycles most of Day 1's target vocabulary (and idiom/slang, if used), per Section 0.5, then complete a
light gist or word-scan task.

Spoken Vocabulary Mastery (3-4 Min): Reinforce target vocabulary through oral word form practice (e.g.,
Noun vs. Verb usage) or oral scenario questions.
Phase 2: Collaborative Multi-Level Investigation (30 Min)

Execute the Collaborative Evidence Matrix using mixed-ability triads (Level A, Level B, Level C).


Each student completes their assigned tier as a quick rehearsal prep tool, then shares orally to combine
knowledge for the team discussion.

Level C tasks must stay at the band's upper level ceiling (Section 0.2), not escalate into the next band's
inference demands (no unstated-premise/rhetorical-manipulation detection below Level 7).
New in v2.1: This phase is the preferred anchor slot for the Section 0.7 board-dependent moment  build a
shared graphic organizer on the board live, as each triad reports its tier's findings (see Section 0.7 for the
organizer-to-Module mapping).
Phase 3: Structured Oral Output Debate & Synthesis (30 Min)

Shift all primary post-reading performance tasks toward oral communication (structured discussions,
debates, interactive speaking). Omit standalone formal writing assessments (such as essays or written
grammar drills).

Scaffold discussions using explicit sentence frames (e.g., "I agree with... because...", "On the other
hand...") and structured protocols (Fishbowl, Town Hall, Concentric Circles).

Include role-specific scaffolded sentence stems mapped to Levels A, B, and C so all learners actively
participate in the debate. Keep stem vocabulary/grammar inside the band's range; do not issue Level C
debate stems written in Proficient-band (C1-C2) register.

Differentiated participation (new in v2.2, see Section 0.8, Part B): Level A's role in the protocol must differ
in participation mode, not only in stem difficulty  a rehearsed pair-share before the public round, or a
listening/tracking role with one prepared line, rather than the same on-demand live turn as Levels B and
C. Where a Foundation Support student is present, give them a non-verbal or minimally-verbal role in the
same protocol.

Closing Transfer Check (new in v2.2, corrected in v2.3, see Section 0.8, Part A): end Group Synthesis by
having every student produce, in pairs and out loud, one new instance of the Day 1 Skill Spotlight's skill
applied to something other than the anchor text, then cold-call two or three pairs to share. Do not close
with a self-report (thumbs-up/sideways/down or a show of hands)  see Section 0.8 for why. Keep this
inside the existing synthesis window; nothing is collected or graded.
Style & Formatting Constraints

Pacing Diagrams: Always include a visual ASCII text timeline diagram at the start of both Day 1 and Day
2 specifying time allocations for each phase.

No Em-Dashes: Never use em-dashes anywhere in the generated content. Use standard hyphens,
colons, or parentheses instead.

Oral Focus: Prioritize spoken interaction and critical thinking over written grammar drills.
Lesson Variety & Structural Rotation Rule:

Reading Strategy Rotation: Never use the same reading strategy across two consecutive 2-Day cycles
(e.g., alternate between Modeling, Reciprocal Teaching, Partner Reading, and Reader's Theater).

Phase 1 Activation Variety: Alternate activation hooks between Visual Inquiry, Four-Corner Debates,
Mystery Quotes, and K-W-L Walks.

Phase 3 Output Rotation: Vary the oral discussion protocol for every cycle (e.g., Town Hall Role-Play,
Fishbowl, Concentric Circles/Speed-Dating, Jigsaw Expert Panels).


Genre Rotation: Shift the reading text style across units using the genre bank in Section 0.6 (e.g.,
Expository Article to Field Journal/Narrative to Policy Debate/Interview) while still respecting the Section
0.2 complexity ceiling for the target band; a genre shift is not license to raise the register.

Board-Dependent Moment Rotation (new in v2.1): Vary which slot (Phase 1 activation, Phase 2
investigation, or Phase 3 synthesis) carries the required board-dependent moment across cycles rather
than anchoring it to the same phase every time, so the board's role in the lesson stays visibly
load-bearing rather than becoming its own template.
Band Calibration is Non-Negotiable: Structural richness (timelines, debate protocols, tiered matrices) must never
be used to compensate for or disguise a miscalibrated anchor text. A well-developed, correctly-sized Level 3-4
text with excellent scaffolding is correct; both an over-dense Level 6-level text at the Level 3-4 band, and a thin,
underdeveloped text that technically meets a word-count floor but doesn't function as real connected prose, are
miscalibrations.
Board-Dependent Moments Are Equally Non-Negotiable (new in v2.1): A lesson that satisfies every ceiling and
structural requirement above but never gives the teacher a genuine reason to use the board fails Section 0.7 and
must be revised before it is finalized.
