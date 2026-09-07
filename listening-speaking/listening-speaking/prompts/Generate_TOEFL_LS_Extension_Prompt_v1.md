# Listening/Speaking TOEFL Practice Extension Prompt (v1)

Companion to the Listening/Speaking Lesson Generation Prompt (v1.1). Generates an optional TOEFL
iBT Listening and Speaking practice packet from an already-completed Advanced or Proficient band
lesson, for the subset of students in a mixed class who want TOEFL preparation. Grounded in
`source/TOEFL_Listening_extracted_text.txt` and `source/TOEFL_Speaking_extracted_text.txt` - the
real TOEFL iBT task types, question types, timing, and scoring guides described there.

Use this prompt only after a lesson already exists for the Advanced (Levels 5-6, CEFR B2-B2+) or
Proficient (Levels 7-8, CEFR C1-C2) band. Do not use this prompt to generate a lesson, and do not
use the Lesson Generation Prompt to generate TOEFL task items: the two are separate tools with
separate inputs, the same relationship the Assessment Generation Prompt (v1) already has to the
lesson prompt. This prompt is the Listening/Speaking sibling of Passage Reading's
`Generate_TOEFL_Extension_Prompt_v1.md`, which the Lesson Generation Prompt's own header already
names as the pattern this feature follows.

Why this exists: some cohorts don't have enough TOEFL-interested students to run a standalone TOEFL
class. This prompt lets a single Advanced/Proficient section run one shared lesson (same real
source, same Day 1/Day 2 core, same module completion for everyone) while TOEFL-interested students
additionally receive a practice packet, drawn from that same source and topic, formatted as
authentic TOEFL Listening and Speaking practice. Non-TOEFL students are unaffected; nothing in the
base lesson changes.

**Two parts, two different grounding rules, both anchored in the same fair-use ceiling the base
lesson already observes.** Section 0.3 of the Lesson Generation Prompt caps direct quotation from a
real third-party source at one to two sentences at a time; the source lesson itself never quotes
more than that. TOEFL Listening's Academic Talk/Conversation/Announcement formats run 35-250 words,
well past that ceiling, so Part A cannot be a long verbatim quotation the way Passage Reading's
extension excerpts a real anchor text (Reading's anchor texts aren't bound by this same ceiling).
Instead, Part A is written in original wording that faithfully represents the real content,
sequence, and facts of the lesson's real source, reusing only the same short verbatim quotes the
base lesson already established (never a new one), exactly the way the lesson's own Closing
Transfer Check script is an invented-but-faithful passage rather than a quotation. Part B goes
further in the other direction: TOEFL Speaking's "Listen and Repeat" sentences and "Take an
Interview" questions are freshly authored in the real test itself, not excerpted from a longer
recording, so Part B authors fully original material grounded in the lesson's real topic,
vocabulary, and register. Neither part invents a new topic, source, or fact; apply "never invent
the topic or its real content" to both, and "never quote past the established ceiling" to Part A.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Band restriction

This prompt applies only to lessons built for the Advanced band (Levels 5-6, CEFR B2-B2+) or the
Proficient band (Levels 7-8, CEFR C1-C2). Do not generate a TOEFL packet from a Beginner or
Intermediate band lesson: TOEFL iBT assumes B2+ ability, and forcing either part's task types onto
a Level 1-4 lesson would break both the band's complexity ceiling (Section 0.2 of the Lesson
Generation Prompt) and the TOEFL tasks' own authenticity. If asked to do this for a Beginner/
Intermediate lesson, stop and say why, rather than producing a simplified TOEFL-style packet that
isn't actually TOEFL-representative.

### 0.2 Required inputs before generating

1. **The source lesson, in full:** its real source citation(s) (title, speaker/subject, platform,
   URL, runtime, segment labels/timestamps), its Phase 1 target vocabulary (4-6 words plus any
   idiom/slang spotlight), its Module, its Band, and its Day 1/Day 2 topic and theme. Pull all of
   this directly from the completed lesson file; do not invent a new source or a new topic.
2. **Which task-type mix to use for Part A** (see 1.2): determined by the source's real genre, not
   chosen freely - a two-speaker interview segment reads as a Conversation set, a single-speaker
   narrated/informational segment reads as an Academic Talk set, a notice-style clip reads as an
   Announcement set. Most Listening/Speaking sources (profiles, documentary segments, lectures)
   will land as Academic Talk. State which format was used and why in the packet header.
3. **Delivery context:** confirm this is being generated as an add-on for TOEFL-interested students
   working independently or in a small group (e.g. during a Day 1 or Day 2 extension slot, or as a
   homework packet) while the rest of the class continues the standard lesson. If not specified,
   default to this and note the assumption in the packet header.

### 0.3 What this prompt does NOT do

- Does not invent a new source, topic, or fact for Part A, and does not quote the real source
  beyond the one-to-two-sentence ceiling the base lesson itself already observes (Section 0.3 of
  the Lesson Generation Prompt). Every fact represented and every tested word traces back to the
  source lesson's actual real transcript/segments or Phase 1 vocabulary list.
- Does not alter the base lesson. The TOEFL packet is a separate document layered on top; the Day
  1/Day 2 lesson plan, its task Levels, and its oral output tasks are untouched and still apply to
  every student, TOEFL-track or not.
- Does not generate a "Listen and Choose a Response" item for Part A. That real TOEFL task type is
  a freestanding, invented short social exchange with no basis in a longer recording - unlike
  Conversation, Announcement, and Academic Talk, which excerpt real content, it has no real material
  in the lesson's own transcript to ground it in. Leave it out rather than fabricate one; this can
  be revisited if a future version finds a defensible grounding rule for it.
- Does not repeat a TOEFL item as a substitute for the lesson's own Phase 4 differentiated task or
  Phase 5 Closing Transfer Check. Those stay as originally generated for every student.
- Does not score or grade a student's spoken Part B responses itself. It produces the prompts and
  reproduces the real TOEFL Scoring Guide (adapted from `TOEFL_Speaking_extracted_text.txt`) for a
  teacher, peer, or the student themselves to score a live or recorded response against.

## SECTION 1: TASK STRUCTURE

### PART A: TOEFL LISTENING PRACTICE

#### 1.1 Writing a faithful, TOEFL-length passage from the lesson's real source

TOEFL's own Conversation/Announcement/Academic Talk formats run 35-250 words, well past the
one-to-two-sentence quotation ceiling the base lesson already observes (Section 0.3 of the Lesson
Generation Prompt). So this is not an excerpting task: write an original passage, sized to the
chosen task type's real range (per `TOEFL_Listening_extracted_text.txt`), that faithfully
represents the real sequence of events, facts, and figures from the lesson's real source:

- **Listen to a Conversation:** ~35-100 words, two speakers, followed by 2 questions.
- **Listen to an Announcement:** ~40-85 words, followed by 2 questions.
- **Listen to an Academic Talk:** ~175-250 words, followed by 4 questions.

Reuse only the short verbatim quotes the base lesson itself already established (its Source
citations/vocabulary/quoted lines) - never a new quotation pulled fresh from the real source - and
write everything else in original wording. Cover a real rhetorical unit from the source (an
example, a comparison, a stated cause and effect, a clear tonal shift) so Inference, Purpose,
Method, and Attitude questions (1.2) have real material to test. Cite the lesson's real segment
labels/timestamps that the passage draws on in the packet header, the same way the base lesson
does, and state plainly in the header that the passage is a faithful original account of the real
source, not a verbatim transcript excerpt.

#### 1.2 The six question types (apply the real TOEFL taxonomy)

Every excerpt's question set should draw from at least 3 of the 6 real question types, not repeat
one type across every item, matching how the real test mixes types within a set:

1. **Main Idea** - overall topic or primary point of the excerpt.
2. **Factual** - explicitly stated details, examples, or explanations.
3. **Inference** - a conclusion supported by, but not directly stated in, the excerpt.
4. **Purpose** - why the speaker says something, or the function of a specific comment.
5. **Method** - how the speaker organizes or presents information (comparison, sequencing,
   example).
6. **Attitude** - the speaker's tone, certainty, or opinion, signaled through word choice.

Model question stems and answer-choice construction on the verbatim examples in
`TOEFL_Listening_extracted_text.txt` (e.g. "What is the main topic of the talk?"; "According to the
speaker, what..."; "What can be inferred about..."; "Why does the speaker mention..."; "How does
the speaker organize..."; "What is the speaker's attitude toward..."). Correct answers should
paraphrase the excerpt rather than quote it verbatim; distractors should be topically adjacent but
wrong (a real detail misattributed, a true-but-off-target statement, an overstated or reversed
claim) rather than randomly wrong, matching the real test's distractor design.

#### 1.3 Answer key and explanations (required)

For every item, state the correct answer and a short explanation in the source's own worked-example
style: point to specific wording in the excerpt to justify the correct choice, then briefly explain
why each distractor is wrong (misstates the excerpt, is true but doesn't answer the question, or
isn't supported by it). This is answer-key material for the instructor, not part of the
student-facing packet (see 2.1).

### PART B: TOEFL SPEAKING PRACTICE

#### 1.4 Listen and Repeat (7 original sentences)

Write 7 original sentences set in a short, plausible scenario connected to the lesson's real topic
(paralleling the source's own framing, e.g. "you are training a new coworker at..."), reusing the
lesson's pre-taught vocabulary where it fits naturally. Follow the real task's complexity
progression exactly:

- Sentences 1-2: short, 9-11 syllables, single independent clause, 8-second response window.
- Sentences 3-5: medium, 14-16 syllables, may add a prepositional phrase or dependent clause,
  10-second response window.
- Sentences 6-7: long, 19-23 syllables, multiple modifiers/clauses, 12-second response window.

State the syllable count for each sentence in the instructor document (not the student packet).

#### 1.5 Take an Interview (4 original questions)

Write 4 original questions tied to the lesson's real topic and theme, progressing from personal to
abstract/speculative per the real task's own category taxonomy:

- Questions 1-2 (personal): draw from Talk About Personal Experiences, Personal Plans/Goals/
  Desires, Personal Preferences/Interests, or Observations About People Close to You.
- Questions 3-4 (abstract/speculative): draw from Share Opinions on Current Topics/Trends,
  Speculate About the Future, or Answer Hypothetical Questions.

Each question gets a 45-second response target, no preparation time, matching the real task. State
which of the source's category types each question draws from in the instructor document.

#### 1.6 Scoring guides (reproduce, adapted from the source)

Because these are spoken responses, there is no correct-answer key; instead, reproduce the real
TOEFL Scoring Guides from `TOEFL_Speaking_extracted_text.txt`, adapted for a teacher, peer, or
self-assessment to score a live or recorded response against:

- **Listen and Repeat:** holistic 0-5 scale, Intelligibility and Accuracy as the two criteria
  (a response that is an exact, fully intelligible repetition scores 5; a response missing most of
  the prompt or largely unintelligible scores 1; no attempt or entirely unconnected content scores
  0).
- **Take an Interview:** holistic 0-5 scale, scored on Relevance, Elaboration, Delivery, and
  Language Use (a response that fully addresses the question with clear elaboration, natural pace,
  intelligible delivery, and accurate/varied grammar and vocabulary scores 5; a response only
  vaguely connected to the question, mostly unintelligible, or consisting of isolated words scores
  1; no attempt or entirely unconnected content scores 0).

Include enough of each rubric's descriptive detail (not just the numbers) that a teacher unfamiliar
with the real TOEFL Speaking rubric can still score consistently.

### 1.7 Item metadata (required, instructor document only, for future tracking)

A future goal is per-student tracking of which TOEFL item types a student consistently struggles
with, aggregated across many lessons. A single packet only has a few items per type, so that
pattern can only be seen by combining results across lessons, which requires every item to already
carry consistent, structured metadata the moment it's generated. Do not label question types on the
student-facing packet itself (see 0.3 and 2.2): the real TOEFL test never tells a student which
type of question they're looking at.

At the end of the instructor document, include one metadata table with one row per item:

- **Item ID:** `{BAND}-L{lesson number}-{TASK}-{ref}`, where BAND is ADV or PROF, TASK is CONV
  (Conversation), ANNC (Announcement), or ATALK (Academic Talk) for Part A, or LNR (Listen and
  Repeat) or TIV (Take an Interview) for Part B, and ref is Q1-Q4 (etc.) for Part A or the
  sentence/question number for Part B. Example: `ADV-L1-ATALK-Q3`, `ADV-L1-LNR-S5`.
- **Task Type:** Conversation / Announcement / Academic Talk / Listen and Repeat / Take an
  Interview.
- **Question/Item Type:** for Part A, one of the 6 question types (1.2); for Listen and Repeat,
  the sentence's complexity tier (Short/Medium/Long); for Take an Interview, the category it draws
  from (Personal Experience, Personal Plans/Goals, Personal Preferences, Observations About
  Others, Opinions/Trends, Speculate About the Future, Hypothetical).
- **Correct Answer:** the letter, for Part A items only (blank for Part B).
- **Pre-taught Vocabulary Overlap:** Yes/No, only where the item reuses one of the lesson's own
  pre-taught target words (blank otherwise).

## SECTION 2: FORMAT

### 2.1 Two documents: student packet and instructor document

Produce the student-facing packet (excerpt/prompts, instructions, answer choices where applicable,
no answers or scoring guides revealed) and a separate instructor document (full content plus Part
A's answer key/explanations, Part B's scoring guides, and the item metadata table from 1.7) as two
documents, the same separation the base program uses between a task and its answer key.

### 2.2 Required elements in the student packet

**Heard, not read.** Unlike Passage Reading's TOEFL extension (where showing the passage on the
page is the task itself), every TOEFL Listening and Speaking task is heard once, never read by the
test-taker - printing Part A's passage or Part B's sentences/questions in the student packet would
substitute a reading skill for the listening/speaking skill being practiced. So the student packet
never prints Part A's passage text or Part B's 7 sentences/4 questions; those stay in the instructor
document, for a teacher or partner to read aloud once, the same single-playback rule the real test
uses (and the same convention the base lesson's own Phase 5 Closing Transfer Check already
follows for its teacher-read-aloud script). The student packet holds only:

- A header naming the source lesson (Module, Band, lesson topic/title), which TOEFL task format
  Part A uses and why, and noting this is optional TOEFL practice extending that lesson, not a
  separate assessment of it.
- Part A: instructions that a teacher or partner will read the passage aloud once from the
  instructor copy, labeled with TOEFL's own task-format name (Listen to a Conversation / Listen to
  an Announcement / Listen to an Academic Talk) so students who go on to take the real test
  recognize the format, followed by the questions and their answer choices (the questions and
  choices themselves are fine to print - only the passage is read-aloud-only).
- Part B: instructions that a teacher or partner will read each Listen and Repeat sentence and each
  Take an Interview question aloud once from the instructor copy, followed by a numbered response
  slot per item showing only its response-time window (8/10/12 seconds, or 45 seconds), with no
  sentence or question text printed.
- An estimated completion time for the whole packet, sized to realistically fit a Day 1/Day 2
  extension slot or a homework assignment (roughly 20-25 minutes total across both parts).

### 2.3 Style constraints

Reuse the base program's constraints (`Student_Packet_Style_Guide.md` §A, reused wholesale): single
self-contained HTML file, black-and-white only, no em-dashes, print-safe layout. Part A's passage
and Part B's sentences/questions (instructor document only) follow the base program's own drafting
constraints (no em-dashes, clear language) the same as any other invented-but-faithful program text.

## SECTION 3: SELF-CHECK BEFORE FINALIZING

1. Is Part A's passage an original, faithful account of the source lesson's real events/facts,
   reusing only quotes the base lesson itself already established (never a new one pulled fresh
   from the real source), staying within the one-to-two-sentence ceiling, and does its task-format
   choice (Conversation/Announcement/Academic Talk) genuinely match the source's real genre rather
   than being forced?
2. Does Part A's question set draw from at least 3 of the 6 real question types?
3. Does every Part A vocabulary item tested come from the excerpt itself, and where possible,
   overlap with the lesson's own pre-taught word list?
4. Is Part A's answer key a separate document from the student packet, with an explanation (not
   just a letter) for every item?
5. Do Part B's 7 Listen and Repeat sentences follow the real complexity progression (2 short/9-11
   syllables, 3 medium/14-16 syllables, 2 long/19-23 syllables) and reuse the lesson's real
   vocabulary/topic rather than an unrelated one?
6. Do Part B's 4 Take an Interview questions progress personal to abstract/speculative, tied to the
   lesson's real theme, each with a stated 45-second target and no preparation time?
7. Are the real TOEFL Scoring Guides (Listen and Repeat: Intelligibility/Accuracy; Take an
   Interview: Relevance/Elaboration/Delivery/Language Use) reproduced with enough descriptive detail
   to score consistently, in the instructor document only?
8. Does the packet header make clear this is optional extension work layered on an unchanged shared
   lesson, not a replacement for any part of the Day 1/Day 2 cycle?
9. Does the instructor document end with a complete item metadata table (1.7), one row per item
   across both parts, with consistent Item IDs? Is this table absent from the student-facing packet?
10. No em-dashes anywhere; Part A's passage cites timestamp/segment-label references, never
    paragraph letters, consistent with the source lesson's own citation style.
11. Is the student packet free of Part A's passage text and Part B's sentence/question text (2.2's
    "heard, not read" rule) - printing only instructions, response-time windows, and (for Part A)
    the questions and answer choices themselves?
