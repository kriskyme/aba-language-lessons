# Passage Reading Lesson Generation Prompt (v3.5)

**Lesson type:** a **Passage Reading Lesson** is a fixed 2-day cycle (two 75-minute periods) built around one
shared anchor text (a single passage or excerpt), differentiated into band-scoped task Levels. It is distinct from
the planned Novel Reading Lesson type (multi-day, multi-chapter), which will have its own prompt.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` (taxonomy, task Levels by band, Sets,
version codes) and `shared/Generation_Quality_Standards.md` (every modality-neutral pedagogical and item-quality
rule, plus the shared self-check) alongside it. This prompt does not restate anything in those files; it states
only what is true of a passage-reading lesson and points to them for the rest. Quality Standards' CBI/TBLT
framing (Conventions §E) applies here with reading as the content vehicle: the anchor text is a tool to explore
real-world ideas and build critical thinking, with language acquisition happening through meaningful
communication.

**Current version: v3.5.** For the dated version history and the reasoning behind each change, see `Changelog.md`.

**Inputs:** every request names at minimum a Module and a Band (e.g. "Advanced band, Module 6: Arguing"); a
topic is optional. A specific Level is never part of the request - the band determines every task Level
(Conventions §B). Without a Module/Band pair, stop and ask before writing anything.

**Output:** one Markdown lesson document. Directly under its H1, a metadata line:
`**Module:** ... | **Band:** ... | **Task Levels:** ... | **Version:** <Module>.<Set>.<Lesson>.<Version>` (Conventions
§G; `<Version>` is `0` on first generation). Save per Conventions §D. Its student packet is generated separately
by the Student Packet prompt, immediately after, from this document (Style Guide §G). Any image the lesson embeds is fetched, cited in the `.md`, and added as a row to the Set's `Set<N>_<Band>_Image_Credits.md` in this same pass (Conventions §I); the packet prints no credit.

**Scope:** this prompt generates lessons only. Assessments come from `Generate_Assessment_Prompt_*.md`,
homework from `Generate_Homework_Prompt_*.md`, and a Set is planned first with
`Generate_Module_Lesson_Plan_Prompt_*.md`. `learningobjectives.csv` is the single source of record for every
objective; never use older per-level exports.

---

## SECTION 0: BAND CALIBRATION (READ AND APPLY BEFORE WRITING ANY TEXT)

Complexity calibration is a hard constraint: if a generated text or task exceeds the target band's ceiling below,
rewrite it before anything else in the lesson is finalized. Structural richness (timelines, debate protocols,
tiered matrices) never compensates for a miscalibrated anchor text. Both an over-dense text pitched a band too
high and a thin text that technically meets a word-count floor but does not function as real connected prose are
miscalibrations.

### 0.1 Anchor level, task Levels, and the Module verb

**The anchor text is calibrated to the band's LOWER Level** (Conventions §A). That one Level governs Section 0.2's
word count, grammar, and vocabulary ceiling for the whole lesson. Every student reads the same text; only the
task built on top of it differs by Level.

Pull the Reading-modality objective for the band's lower Level and the requested Module from
`learningobjectives.csv` (filter Level, Modality = Reading, Module) and use that row's Description and Example as
the objective the anchor text must satisfy. The text's difficulty is governed only by the Reading objective at
that Level, not by the Listening/Speaking or Writing rows at the same Level, which may describe more advanced
production skills.

**Task Levels by band:** Conventions §B. One differentiated Reading task per Level, all built on the single
shared anchor text, each citing its own Level's Reading row (Quality Standards §A).

**The Module verb governs the task, not just the difficulty** (Quality Standards §A4). Section 0.2 tells you how
hard the text can be; the pulled objective tells you what skill it must exercise. Do not default to a generic
informational-article task regardless of Module:

- **Module 1 (Describing):** describing a person, object, place, or scene (features, qualities, comparisons). The
  comprehension work centers on descriptive features, a comparison, and a stated reason for it. A text may
  mention threats or policy as color, but the graded tasks trace back to describing.
- **Module 3 (Explaining):** cause-and-effect, process, "why this happens."
- **Module 5 (Evaluating):** claims, criteria, verdicts.
- **Module 6 (Arguing):** weighing two sides toward a position.
- The other Modules follow the same principle with their own CSV verb.

### 0.2 Complexity ceiling by level

Hard targets for the anchor text at each Level: word-count range, paragraph count, average sentence length, and
the grammar, vocabulary, and comprehension constraints that keep the text inside its band. The numbers are
anchored to real published single-lesson materials at each CEFR level (British Council LearnEnglish, Cambridge
exam specifications), not derived from the CSV's atomic skill statements; the CSV governs what skill the text
supports, these numbers govern how much text a 2-day cycle needs. **Write toward the middle-to-upper part of
each range. A text at or below its floor is a fail. Count the words before finalizing; never estimate.**

**Level 1 (A1)**
- Form: short functional text (a notice, a label set, a 2-4 line exchange) or 1-2 sentences using a memorized
  frame; not necessarily continuous prose
- Length: 60-120 words
- Grammar: one memorized frame; present tense or simple past frame only
- Vocabulary: concrete, high-frequency, decodable simple-phonics words; zero abstract nouns
- Sentence length: average 6-10 words
- Comprehension demand: literal match to a picture or object; no inference

**Level 2 (A2)**
- Form: 3-4 short paragraphs (or a short email/note), each built from fixed-frame sentences
- Length: 150-220 words
- Grammar: single frame per sentence (simple present or simple past "-ed"); no subordination
- Vocabulary: concrete, high-frequency; 3-5 target words per text
- Sentence length: average 8-12 words
- Comprehension demand: literal match with visual support; locating a stated fact

**Level 3 (B1)**
- Form: 4-5 paragraphs of connected prose (a real short article or narrative, not a template)
- Length: 280-350 words
- Grammar: simple present and simple past as the backbone; one coordinating connector per sentence (and,
  because, but); a single "who/which/that" clause is acceptable; never two coordinators or two subordinate
  clauses in one sentence; no passive voice
- Vocabulary: concrete, familiar-topic; 4-6 pre-taught target words; no academic or abstract vocabulary
  ("extraordinary," "civilization," "habitat," "preserved" are Level 5+)
- Sentence length: average 12-18 words
- Comprehension demand: literal comprehension, scanning for direct facts, basic cause-and-effect; decoding
  target words in context
- Numbers/dates: light factual grounding (a year, a place, a few concrete details); no dense multi-date timeline

**Level 4 (B1+)**
- Form: 5-6 paragraphs, original connected prose
- Length: 350-430 words
- Grammar: simple past narrative or present-tense description; one comparison structure; one "because" reason
  clause; light subordination throughout, no dense multi-clause sentences
- Vocabulary: concrete plus a small set of everyday abstract words ("reliable," "worth it"); no technical or
  academic register
- Sentence length: average 15-22 words
- Comprehension demand: identify one comparison, one stated outcome, one directly-stated reason (never implied)
- Numbers/dates: factual grounding fine; still no dense timeline

**Level 5 (B2)**
- Form: 5-7 paragraphs, connected prose organized logically
- Length: 400-460 words
- Grammar: mixed past/present, coordination and light subordination (one subordinate clause per sentence),
  natural connectors chosen by the writer
- Vocabulary: everyday abstract plus some topic-specific vocabulary (4-6 pre-taught words), not dense academic
  or technical register (no nominalizations or Latinate technical terms; "neuroplasticity," "paradigmatic" are
  Level 7-8)
- Sentence length: average 17-24 words
- Comprehension demand: summarize organization; identify ONE clearly-signaled implied attitude or reservation (a
  hedge word or evaluative adjective, not an unsignaled inference; see the Level 5 and 6 CSV rows for the boundary)
- Numbers/dates: light factual grounding; no dense chronology

**Level 6 (B2+)**
- Form: 6-8 paragraphs, fluent connected prose
- Length: 460-520 words
- Grammar: complex sentences with sustained control, not dense academic syntax; register shifts simple and
  clearly signaled
- Vocabulary: broader abstract and evaluative vocabulary, light topic-specific terms; no specialist jargon or
  C1-C2 academic collocations
- Sentence length: average 20-28 words
- Comprehension demand: separate stated fact from clearly-signaled evaluative language; locate ONE visible tonal or
  register shift without inferring the writer's motive for it
- Numbers/dates: no more than 2-3 discrete facts or dates stacked together

**Level 7 (C1)**
- Form: 7-11 paragraphs; two related extended texts (for comparison) or one dense extended text; full academic
  and idiomatic register allowed
- Length: 600-700 words (if two texts, roughly 300-400 each, as long as the combined comparison reaches full C1
  demand)
- Grammar: full complex range, idiomatic phrasing, flexible register
- Sentence length: average 20-25 words
- Vocabulary: academic and idiomatic; abstraction expected
- Comprehension demand: critically compare rhetorical choices across two texts, or identify an unstated interest,
  assumption, or premise

**Level 8 (C2)**
- Form: 8-12 paragraphs; dense, stylistically layered (irony, understatement, unreliable framing, dual-audience
  calibration)
- Length: 700-900 words
- Grammar/vocabulary: no ceiling
- Sentence length: average 22-28 words
- Comprehension demand: reconstruct withheld or downplayed meaning, detect manipulation techniques, assess the
  risk of divergence between literal and real meaning for a specified reader

### 0.3 Self-check before finalizing

Run `shared/Generation_Quality_Standards.md` §F first (task Levels, Respectful Tiers, item quality, Skill
Spotlight and Closing Transfer Check, board moment, teaching-before-practice, adjacency, style). Then, for the
anchor text and the Reading-specific rules in this prompt:

1. **Word count** inside the band's lower-Level range (0.2), toward the middle-to-upper part, and does the text
   read as real connected prose with enough substance for two class periods, not a fact list?
2. **Paragraph count and average sentence length** match 0.2 for that Level, not just the total word count (one
   dense 300-word paragraph is not five 60-word paragraphs)?
3. **Clause complexity:** no sentence exceeds the Level's grammar ceiling?
4. **Vocabulary scan:** no word that would only appear two or more bands higher; replaced if found?
5. **Fact density:** distinct dates, numbers, and named entities kept to the Level's guidance; no biography-style
   timeline?
6. **Idioms (0.4):** each expression classified transparent or opaque, opaque ones glossed at every Level, density
   matched to the band?
7. **Refresher text (0.5):** clearly shorter and simpler than the anchor, unrelated topic, reusing most of Day 1's
   target vocabulary, introducing no new grammar or vocabulary?
8. **Genre (0.6):** a genuine rotation from the prior cycle, calibrated to the band, formatted to that genre's
   real-world convention?
9. **Paragraph lettering and footnotes (0.9):** every anchor paragraph lettered `[A]`, `[B]`, ... and referenced by
   letter everywhere; bracketed paragraph letters kept distinct from spelled-out "Partner A/B" labels; footnotes
   only where a real reference is unexplained, 1-3 per text, inside the Level's vocabulary ceiling, never tested?
10. **Phase 3 protocol (0.10):** a Panel Round gives every listener an explicit task and 2-3 rotated
    prompts; Rotating Partners gets 2-3 prompts; Town Hall, Jigsaw, and small-group discussion split 2-3 prompts across groups?
11. **Reading strategy** named and fully integrated into the text's layout per the Reading Execution Rules?
12. **Fixed-output Levels (0.11; Quality Standards §D10):** where Level 1 or 2 is a task Level, its form is
    produced at most once per day, every other Level 1-2 item takes a different 0.11 shape, no shape twice in
    this lesson or in the same slot as the previous lesson, and the frame or label set is printed once per day?
13. **Answer notes:** every expected answer (stops, Fact Finder, Cause & Effect, matrix cells) on an `Answer
    note:` line under its item, with no stem, bracket, or parenthetical stating what the item asks for (Quality
    Standards §F item 23)?

If any check fails, revise before finalizing; do not build Day 2 tasks on an anchor text that failed items 1-5.

### 0.4 Idioms and slang: scale by transparency, not by level

Every anchor text from Level 2 upward includes at least one idiom or slang expression. The rule is not a level
gate; it is a transparency rule applied at every Level.

Classify each candidate as **transparent** (meaning recoverable from its parts and everyday use: "no way," "for
sure," "hang on a second," "a big deal") or **opaque** (meaning not derivable from the literal words: "kick the
bucket," "under the weather," "spill the beans"). Record the classification in the lesson's Idioms item; the
packet prompt uses it.

- Transparent chunks may appear from Level 2 onward, lightly glossed or left for incidental pickup.
- Opaque idioms require an explicit gloss or a brief teacher confirmation at every Level, including 7 and 8.
  Advanced learners inferring idioms unaided show no comprehension advantage over glossed presentation, and
  wrong inferences persist. Never set "infer this idiom entirely unassisted" as a task.
- What changes with Level is density and register. Levels 2-4: one or two transparent chunks, tied to the topic,
  glossed. Levels 5-6: two to three expressions, mixing transparent chunks with one opaque idiom, glossed. Levels
  7-8: three to five, more opaque and register-marked; students may confirm a guessed meaning against a
  provided gloss rather than being handed it first, but the gloss or confirmation step never disappears.
- Favor high-utility, fixed-form idioms teachable in one aside; avoid obscure, archaic, or region-specific slang.
- Place the expression naturally in the anchor text; deliver the gloss as an inline bracket, a footnote-style
  box, or a Phase 1 "Idiom/Slang Spotlight" item, on top of (not inside) the 4-6 target-vocabulary budget.

### 0.5 Day 2 vocabulary refresher text

Day 2 Phase 1 includes, after the 3-minute partner re-scan, a short secondary reading that recycles Day 1's
target vocabulary in a new context:

- **Topic:** unrelated to the anchor text; connected only through vocabulary reuse. Varied re-exposure gives a
  cleaner test of whether students know the word, not just the passage. At Levels 1-2 keep the shift gentle (a
  different everyday scenario, not an abstract new domain).
- **Reuse target:** at least 5 of the 4-6 Day 1 words, plus 1-2 from the idiom spotlight if one was used.
- **Length and complexity:** one-third to one-half the anchor's word count, at or below the anchor Level's 0.2
  sentence-length and grammar ceiling. Never a second anchor text; no new grammar or vocabulary beyond the
  recycled set plus ordinary connective language.
- **Form:** a short paragraph or two, or a short functional text (a notice, a message exchange, a news blurb).
  Letter its paragraphs per 0.9 if there is more than one.
- **Task:** 3-4 minutes, light touch: a gist question, a "find and circle these 5 words" scan, or a one-sentence
  oral summary to a partner. Not a second comprehension set.
- **Budget:** Day 2 Phase 1's 15 minutes hold the 3-minute re-scan, this text plus its task (8-9 minutes), and
  the spoken vocabulary mastery activity (3-4 minutes). Trim the oral drill, not the refresher, if needed.

### 0.6 Genre and text-type rotation

"Genre rotation" means varying the actual text type the anchor is written as, not just the topic. Rotate across
cycles from the band's bank, adapt the Reading Execution Rules and task design to the genre's real conventions,
and keep 0.2's ceiling regardless of genre: genre changes form and voice, never the ceiling. Do not repeat a
genre in two consecutive cycles for the same class. When a genre depends on a feature above the band's ceiling
(satire needs inference beyond Level 6), reserve it for the band where it is calibrated rather than stripping
the feature that defines it.

| Band | Genre bank |
|---|---|
| Beginner (1-2) | Label sets with their images embedded in the packet (Quality Standards §D8) and short notices (signs, simple ads); short personal notes, texts, or postcards; simple 2-4 line dialogues; very short how-to lists (3-5 steps) |
| Intermediate (3-4) | Short narrative or personal-story articles; simple news briefs; how-to guides; short Q&A interview transcripts; email/message exchanges; short field-journal or diary entries; text-message/chat threads; product listings |
| Advanced (5-6) | Feature-style newspaper or magazine articles; short stories with a clear arc; opinion/editorial pieces (single stance); interview or profile pieces; travel/field-journal narrative; product or place reviews; short policy or issue explainers; social media post threads; advice-column letters with response |
| Proficient (7-8) | Full newspaper feature or investigative articles; literary short-story excerpts; op-eds with rhetorical complexity; formal debate transcripts or point-counterpoint pieces; academic-style explainer or research-summary excerpts; satire or irony-dependent pieces (Level 8 only); podcast transcript excerpts; historical primary-source-style documents |

| Genre | Formatting convention |
|---|---|
| Newspaper / news brief | Headline, byline-style dateline, inverted-pyramid structure, short paragraphs |
| Short story / narrative | Paragraph prose; dialogue with quotation marks |
| Interview / Q&A | Speaker labels, turn-based formatting |
| How-to / instructions | Numbered or bulleted steps, imperative verbs |
| Email / message exchange | Greeting and sign-off conventions; subject line where relevant |
| Editorial / opinion | Clear thesis placement; stance language inside the Level's evaluative-vocabulary ceiling |
| Debate / point-counterpoint | Two labeled voices or columns, parallel structure |
| Text-message / chat thread | Short sender-labeled turns, optional timestamps, casual register (contractions, no salutation), each turn message-length |
| Product listing | Short lead paragraph, bulleted feature list, a spec line or two |
| Social media thread | Labeled original post (short, character-limited) plus labeled indented replies; a hashtag where natural |
| Advice-column letter with response | Reader's first-person letter with its own salutation/sign-off, then the columnist's reply with a distinct signature; voices visually separated |
| Podcast transcript excerpt | Speaker labels by name or role each turn; natural-speech markers only at Proficient, sparingly; no narrative framing between turns |
| Historical primary-source document | Period dateline and salutation (letter) or dated entry heading (diary), first-person voice, vocabulary still inside the Level's 0.2 ceiling |

### 0.7 Board-dependent moments: where they fit in a Reading lesson

The rule itself (one genuine board-dependent moment per day; the three-property test; transcription does not
count) is Quality Standards §D4. In this cycle the slots are:

- **Day 1 Phase 1 activation:** a K-W-L Chart builds its K and W columns live on the board from student
  call-outs before reading (the L column after reading, on Day 1 or in Day 2 Phase 1); a Mystery Quote collects
  student guesses about the quote's source or meaning on the board and checks them off against the text.
- **Day 2 Phase 2 investigation (preferred anchor slot):** build a shared graphic organizer on the board as
  each mixed-ability group reports its task Level's findings, so the synthesis exists only once every Level has
  contributed. Match the organizer to the Module: a comparison T-chart or Venn diagram for Describing, a
  cause-and-effect chain for Explaining, a criteria/verdict rubric for Evaluating, a two-column claims tracker for
  Arguing, a numbered process map for Instructing, and the equivalent for Narrating, Transacting, Socializing.
- **Day 2 Phase 3 oral output:** a Panel Round keeps a running board record of claims or evidence as they are
  actually spoken (one speaker at a time is easy to transcribe live). Rotating Partners, Town Hall, Jigsaw, and
  small-group discussion instead have each pair or group report one claim or piece of evidence to the board when
  its window ends.
  Either way this feeds the closing synthesis.

One genuine instance per day satisfies the rule; vary which slot carries it across cycles.

### 0.8 Skill Spotlight, Closing Transfer Check, and Phase 3 participation in a Reading lesson

The rules (Quality Standards §D1-D3, §B) are shared. Reading-specific placement and shapes:

- **Skill Spotlight** sits in Day 1 Phase 1, immediately after or alongside the activation hook: "Today we're
  practicing describing a place by comparing it to somewhere more familiar, the way the writer compares Ciudad
  Perdida to Machu Picchu," not "Today we're reading about Ciudad Perdida."
- **Closing Transfer Check** closes Day 2 Phase 3's Group Synthesis, oral-only (consistent with the Oral Focus
  constraint), inside the existing 5-minute synthesis window. Illustrative shapes, showing grammar only -
  `[pick a fresh object/scenario]` marks a real, concrete, lesson-specific choice made at generation time
  (something visible in the room, a piece of clothing someone is wearing, a sound from outside, a classroom
  routine), different from every other lesson in the Set:
  - Describing: "in one sentence, describe `[pick a fresh object/scenario]` by comparing it to something else"
  - Explaining: "in one sentence, explain why `[pick a fresh object/scenario]` happens the way it does"
  - Evaluating: "in one sentence, give your verdict on `[pick a fresh object/scenario]` and one reason"
  - Arguing: "in one sentence, state a position on `[pick a fresh object/scenario]` and one reason"
- **Differentiated Phase 3 participation** for the lowest task Level, within the chosen protocol: a rehearsed
  pair-share immediately before their turn (their small group's round, or their first rotation into the circle),
  or a listening/tracking role for the stretch before their turn (the same tally or word-list task an
  outer-circle student already has under 0.10) with one fully prepared sentence to contribute at a natural pause.
- **Foundation Support** in this cycle (Quality Standards §D8: nothing the teacher must make): matching a printed
  word in the packet to a target term, pointing to the paragraph that answers a Fact Finder, a two-choice circle
  instead of an open completion, a peer buddy for the paired-reading and matrix steps, and in Phase 3 a physical
  role (moving to a side of the room, holding up a word the student wrote on their own paper) rather than a
  spoken turn.

### 0.9 Paragraph lettering and contextual footnotes

**Part A: Paragraph lettering.** Label every paragraph of the anchor text with a bold bracketed capital letter
(`[A]`, `[B]`, ...) immediately before it, and refer to paragraphs by letter everywhere else in the lesson (STOP &
CHECK questions, Fact Finders, the Collaborative Evidence Matrix, board moments): "Paragraph D," "Paragraphs A-D."
Because the Partner/Shared Reading strategy also uses "Partner A" and "Partner B," keep the two visually
distinct: paragraph letters are always bracketed, partner roles are always spelled out in full ("Partner A reads
Paragraphs [A]-[B]"). Letter the Day 2 refresher text the same way when it runs more than one paragraph.

**Part B: Contextual footnotes.** A third support layer, distinct from the 4-6 target words (language needed to
decode the sentence) and the Idiom/Slang Spotlight: footnotes supply background or world knowledge the text
assumes but does not give, the way a textbook footnotes a historical figure or a foreign term.

- **When:** the text names a real person, place, event, or cultural reference that is unlikely to be common
  knowledge at the band, is not already explained by the sentence itself (an appositive glosses itself), and is
  not already in the vocabulary list or idiom spotlight.
- **Format:** superscript numeral at first mention; numbered note in a footer on the same page; one short plain
  sentence inside the same 0.2 vocabulary ceiling as the anchor text.
- **Density:** 1-3 per text. A text that seems to need many more has too much unexplained real-world density for
  its band; revisit it against self-check item 5 rather than patching with a long footnote list.
- Footnotes are informational only; no item ever tests footnote content.

### 0.10 Phase 3 discussion protocols: an active task for every seat

All five protocols (Town Hall Role-Play, Panel Round, Rotating Partners, Jigsaw Expert Panels, small-group
discussion) are valid at this program's actual class size (8-12 students), provided every seat has an explicit
task and the prompts rotate (Quality Standards §D7). Rotate across cycles. All five run from where students
sit: no facing circles, corners, or stations (Quality Standards §D11).

- **Panel Round, the speakers:** roughly half the class (4-6 of 8-12) speaks in turn from their seats, using
  their task-Level stems, so the listeners stay a real group rather than one or two leftovers.
- **Panel Round, the listeners - never passive.** Every listener has a concrete task tied to what is being
  said, matched to the Module and stated in the lesson: a running list (3 words, phrases, comparisons, or
  methods that strike you as well put: Describing, Narrating, Instructing); a tally (which side each speaker
  takes, or how often a target word or claim type appears: Arguing, Evaluating); or a one-line reaction (one
  claim you agree or disagree with and a one-sentence reason, ready for when it is your turn). The lowest task
  Level's version of this task doubles as its differentiated participation (0.8), not a second requirement.
- **2-3 prompts, advanced at each changeover** (roughly every 8-10 minutes across the 25-30 minute window), never
  one static question. The panel and the listeners swap at a changeover, and a new speaker brings their
  listening notes as live material.
- **Rotating Partners:** everyone talks at once in pairs, so no listener task is needed; give it the same 2-3
  rotating prompts and have students find a new partner for each, so every partner works a fresh angle.
- **Town Hall, Jigsaw, small-group discussion:** every student is already active in a group; split the 2-3
  prompts across groups so simultaneous conversations are not identical.
- Board record by protocol: see 0.7.

### 0.11 Fixed-output Levels (1-2): task shape bank and slot assignment

Quality Standards §D10 applies. Level 1's row is a literal match of a decoded word or frame to a picture or
object, and Level 2's is a fixed-frame sentence located or completed with visual support; the form does not
change, so the activity around it must. **The cap:** the student produces the form (decodes and writes or
matches the word, completes the frame) at most once per lesson day; no task says "three times." Every other
Level 1-2 item in the lesson takes a different shape from this bank, and no shape appears twice in one lesson
or in the same slot as the previous lesson:

| Shape | What the student does | Slot |
|---|---|---|
| Decode and match | Sound out the printed word or frame sentence and match it to the embedded picture or the student's own object; the one production | Day 1 Phase 3 (Fact Finder) or Day 2 Phase 2 (matrix cell), not both |
| Choose what fits | From the target-word list, circle the words the text or picture supports and cross out the ones it does not | Day 1 Phase 3 |
| Fix the wrong word | A printed frame sentence about the text with a word that does not fit or is misspelled; cross out, write the right one | Day 2 Phase 1 (refresher task) |
| Sort first | Sort the word bank into its groups (color, size, action) before reading the frame sentences that use them | Day 1 Phase 1 (pre-teach) |
| Read to a partner | Read a completed frame to a partner who says what it describes or points to the matching paragraph letter | Day 2 Phase 2 or Phase 3 |
| Better of two | Two printed frame sentences about the picture; circle the one that fits and say the word that makes it fit | Day 2 Phase 2 |
| Transfer | The form once, on the lesson's fresh object (0.8) | Day 2 Phase 3 |

The frame or label set is printed once per day, in the pre-teach box or the first task that uses it; later
tasks say "the frame." A Set's Module Lesson-Plan names the slot-to-shape assignment per lesson so the same
shape does not land in the same slot twice running.

---

## Unit Architecture: 2-Day Text Cycle Model

Every unit spans two 75-minute lessons centered on one anchor text calibrated per Section 0. Day 1 is decoding,
strategy execution, and literal comprehension; Day 2 is re-engagement, multi-level analysis, and structured oral
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

### Reading Execution Rules

Never use unrehearsed round-robin reading. Name the lesson's reading strategy and adapt the text's layout and
supports to it:

**Whole-class and modeling**
- **Teacher Read-Aloud with Interactive Stops:** pre-written pause points embedded in the text (`[STOP & CHECK 1:
  Ask "Why did..."]`) with comprehension or vocabulary checks. The bracket carries the question only; the
  expected answer goes on an `**Answer note:**` line under the stop, never inside the bracket (Quality
  Standards §C9, §E2).
- **Choral Reading:** clear section breaks, rhythm markers, staggered chorus/solo cues.
- **Echo Reading:** short expressive phrases separated by echo markers (`/` or `[ECHO]`).
- **Think-Aloud Modeling:** embedded teacher think-aloud prompts (`[THINK-ALOUD: model wondering what this word
  means from context]`); the teacher voices their own reasoning rather than checking comprehension.

**Peer and small-group**
- **Partner / Shared Reading:** explicit turn-taking markers ("Partner A reads Paragraphs [A]-[B]") and brief
  turn-checking prompts (see 0.9 Part A).
- **Peer-Assisted Learning Strategies (PALS):** Coach/Reader prompt cards, step-by-step retell checklists, peer
  feedback prompts alongside the text.
- **Whisper Reading:** self-paced focus questions and a Teacher Circulation Checklist with oral coaching prompts.
- **Say Something:** short chunks separated by `[PAUSE: say something to your partner]`; either partner reacts,
  questions, or connects before reading on. Lighter than Reciprocal Teaching's fixed roles.

**Comprehension and performance**
- **Reciprocal Teaching:** role prompts and organizer templates for Summarizer, Questioner, Clarifier, Predictor.
- **Reader's Theater:** explicit script with speaker roles, stage directions, rehearsal cues.
- **Close Reading with Annotation:** a guided annotation key (underline unfamiliar words, circle connectors,
  bracket the main-idea sentence) and margin space for individual marking before discussion; best for
  Advanced/Proficient independent readers.

### Relative Multi-Level Strategy: Dynamic Tiered Framework

All Day 1 and Day 2 comprehension and discussion tasks use one task per Level in the band's Task Levels row
(Conventions §B), each built to satisfy that Level's own Reading CSV objective. Every task falls into one of
three roles by its position in the row:

| Role | Where it sits | Task strategy |
|---|---|---|
| Extension-down task(s) | A Level borrowed from the neighboring lower band | Literal comprehension, scanning for direct facts, visual key details, sentence completion. Scaffolds: sentence starters, option choices, word banks, direct paragraph pointers. In Phase 3: a different participation mode, not just an easier stem (0.8). |
| Native task(s) | The band's own two Levels (the lower of which is the anchor Level) | Core comprehension, main ideas, cause-and-effect, standard inference at that Level's own ceiling (0.2). Scaffolds: guided short-answer prompts, clear question cues. |
| Extension-up task(s) | A Level borrowed from the neighboring higher band | Deeper inference, synthesis, critical evaluation of claims, weighing counter-arguments, capped at that Level's own ceiling (0.2), never the Level beyond. Scaffolds: open analytical prompts, perspective-taking, synthesis frames. |

Beginner has one extension-up task and no extension-down (3 total); Proficient has two extension-down and no
extension-up (4); Intermediate and Advanced have one of each (4).

- **Anchor-driven:** the text is defined by the band's lower Level; avoid tier labels like "Foundation" or
  "Advanced."
- **Interdependent roles:** extension-down tasks establish the factual foundation, native tasks map the logical
  connections, extension-up tasks evaluate impact and weigh evidence, each strictly at its own ceiling.
- **Seamless collaboration:** every Level works the same passage and theme across both days, so students at
  different Levels can partner without breaking class cohesion.
- **Respectful Tiers** (Quality Standards §B) is a standing check on every Collaborative Evidence Matrix and every
  oral protocol: the lowest task Level's matrix cell includes a genuine, scaffolded interpretive or evaluative
  component (a simple opinion question with a word bank, not fact retrieval alone).

### 2-Day Lesson Structure & Detailed Flow

**DAY 1: COMPREHENSION & TEXT DECODING (75 MIN)**

*Phase 1: Pre-Reading & Activation (15 min)*
- Spark curiosity with visual prompts, open opinion questions, or a marked choice students then defend to a
  neighbor (Take a Side). Nothing that moves the class out of its seats (Quality Standards §D11).
  Keep question language at or near the anchor Level's ceiling; no abstract philosophical framing pitched higher.
- Skill Spotlight (0.8), immediately after or alongside the hook.
- Pre-teach 4-6 high-yield target keywords from the anchor text, inside the band's lower-Level vocabulary
  ceiling, using in-context paragraph matching.
- If the text carries an idiom or slang expression (0.4), introduce it here as a brief "Idiom/Slang Spotlight" on
  top of the 4-6 word budget; opaque idioms are glossed at every Level.

*Phase 2: Text Engagement & Strategy Execution (35 min)*
- Execute the chosen reading strategy with all of its structural elements (embedded stops, role guides,
  turn-taking markers).
- Clear paragraph letters (0.9) and explicit check-in frames.
- The anchor text must pass 0.3 before this phase is finalized.

*Phase 3: Day 1 Literal Comprehension & Vocab Context Check (25 min)*
- A rapid factual check pitched at the lesson's task Levels: a Fact Finder set for the lowest task Level, a Cause
  & Effect set for the band's native Level(s). Every item follows Quality Standards §C; a Level 1-2 Fact Finder
  set uses one 0.11 shape, not the same match item repeated. Each set's expected answers sit on `**Answer
  note:**` lines under their items, never in the item sentence or its parenthetical (§C9, §E2).
- A vocabulary context-completion exercise using Phase 1's target terms.

**DAY 2: DEEP ANALYSIS, EVALUATION & PRODUCTION (75 MIN)**

*Phase 1: Text Re-Engagement & Vocab Warm-Up (15 min)*
- 3-minute partner re-scan of the Day 1 text for key details, dates, and paragraph letters.
- Vocabulary Refresher Text (8-9 min) per 0.5, with its light task (for Levels 1-2, a 0.11 shape different from
  Day 1's).
- Spoken Vocabulary Mastery (3-4 min): oral word-form practice or oral scenario questions.

*Phase 2: Collaborative Multi-Level Investigation (30 min)*
- Collaborative Evidence Matrix in mixed-ability groups sized to the band's task-Level count (triads for
  Beginner, groups of 4 otherwise), one student per task Level.
- Each student completes their own Level's cell as rehearsal prep, then shares orally to combine knowledge (a
  Level 1-2 cell is one 0.11 shape, the form produced here only if it was not produced on Day 1).
- Every task stays at its own Level's ceiling (0.2); no unstated-premise or rhetorical-manipulation detection
  below Level 7. A cell's expected content goes on an `**Answer note:**` line under the cell prompt, never
  in the prompt (Quality Standards §C9).
- Preferred slot for the board-dependent moment (0.7): the shared organizer built live as groups report.

*Phase 3: Structured Oral Output Debate & Synthesis (30 min)*
- Shift all primary post-reading performance to oral communication; no standalone formal writing tasks.
- Choose a protocol per 0.10, rotating across cycles, with explicit sentence frames ("I agree with... because...",
  "On the other hand..."), 2-3 rotated prompts, and an active task for every outer-circle student.
- Role-specific stems mapped to every task Level, each inside its own Level's ceiling.
- Differentiated participation for the lowest task Level and a Foundation Support role where present (0.8).
- Closing Transfer Check ends Group Synthesis (0.8): every student, in pairs, out loud, one new instance of the
  spotlighted skill on this lesson's fresh object or scenario; two or three pairs cold-called. Nothing collected
  or graded.

### Style, Formatting, and Rotation

- Quality Standards §E applies: no em-dashes, an ASCII pacing diagram at the start of each day, the metadata line
  under the H1.
- **Oral focus:** prioritize spoken interaction and critical thinking over written grammar drills.
- **Rotation across cycles** (Quality Standards §D6 governs adjacency; these are the Reading banks):
  - Reading strategy: never the same strategy in two consecutive cycles (rotate across the Reading Execution
    Rules bank).
  - Phase 1 activation hook: Visual Inquiry, Take a Side, Mystery Quote, K-W-L Chart.
  - Phase 3 protocol: the five protocols in 0.10.
  - Genre: the band's bank in 0.6.
  - Board-dependent moment slot: vary which phase carries it (0.7).
  - Closing Transfer Check object or scenario: differs across every lesson in the Set (Quality Standards §D3);
    all four lessons of a Set are typically drafted together, so check them against each other directly.
