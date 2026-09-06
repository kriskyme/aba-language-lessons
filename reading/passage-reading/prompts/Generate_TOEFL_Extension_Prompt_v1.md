Passage Reading TOEFL Track Extension Prompt (v1)

Companion to the Passage Reading Lesson Generation Prompt (v2.5, Band-Calibrated). Synced to v2.5: this prompt
never differentiated its own packet by task Level (it works from the shared anchor text and Phase 1 vocabulary,
which are band-level, not task-Level-specific), so the only changes here are terminology - Level/band references
now read Band, matching v2.5's dropped-Level request format - and one corrected cross-reference (see 1.5). It
applies equally whether the source lesson's band has 3 or 4 task Levels, since it never touched that table.
Generates a TOEFL iBT Reading-format task packet from an already-completed Advanced or Proficient band
lesson, for the subset of students in a mixed class who want TOEFL preparation.

Use this prompt only after a lesson already exists for the Advanced (Levels 5-6, CEFR B2-B2+) or Proficient
(Levels 7-8, CEFR C1-C2) band. Do not use this prompt to generate a lesson, and do not use the lesson prompt to
generate TOEFL task items: the two are separate tools with separate inputs, the same relationship the Passage
Reading Assessment Generation Prompt (v4) already has to the lesson prompt.

Why this exists: some cohorts don't have enough TOEFL-interested students to run a standalone TOEFL class. This
prompt lets a single Advanced/Proficient section run one shared lesson (same anchor text, same Day 1/Day 2 core,
same module completion for everyone) while TOEFL-interested students additionally receive a task packet, drawn from
that same anchor text, formatted as authentic TOEFL Reading practice. Non-TOEFL students are unaffected; nothing in
the base lesson changes.

SECTION 0: SCOPE AND INPUTS

0.1 Band restriction

This prompt applies only to lessons built for the Advanced band (Levels 5-6, CEFR B2-B2+) or the Proficient band
(Levels 7-8, CEFR C1-C2). Do not generate a TOEFL packet from a Beginner or Intermediate band lesson: TOEFL iBT
Reading assumes B2+ reading ability, and forcing the question types below onto a Level 1-4 anchor text would break
both the band's complexity ceiling (Section 0.2 of the lesson prompt) and the TOEFL task's own authenticity. If asked
to do this for a Beginner/Intermediate lesson, stop and say why, rather than producing a simplified TOEFL-style packet
that isn't actually TOEFL-representative.

0.2 Required inputs before generating

1. The source lesson: its anchor text in full, its Phase 1 target vocabulary list (4-6 words plus any idiom/slang
spotlight), its Module, and its Band. Pull all of this directly from the completed lesson; do not invent a new
topic or passage.
2. Which band tier of TOEFL question types to use (see 1.3): Advanced-band lessons default to Basic
Comprehension question types only; Proficient-band lessons default to Basic + Inferential. This can be overridden
by request (e.g. a strong Advanced-band class ready for inferential work), but state the default and apply it unless
told otherwise.
3. Delivery context: confirm this is being generated as an add-on for TOEFL-interested students working
independently or in a small group (e.g. during Day 2 Phase 3, or as an extension/homework packet) while the rest
of the class continues the standard Structured Oral Output Debate. If not specified, default to this and note the
assumption in the packet header.

0.3 What this prompt does NOT do

- Does not invent a new anchor text, topic, or vocabulary set. Every passage excerpt and every tested word must
trace back to the source lesson's actual anchor text or Phase 1 vocabulary list.
- Does not alter the base lesson. The TOEFL packet is a separate document layered on top; the Day 1/Day 2 lesson
plan, its task Levels, and its oral output tasks are untouched and still apply to every student, TOEFL-track or not.
- Does not shift the whole class into individual, silent, multiple-choice work. TOEFL iBT Reading is inherently a
different modality (silent, timed, MC) from this program's oral-first CBI/TBLT design; that mismatch is the reason
this exists as an optional add-on for a subset of students rather than a modification to the shared lesson.
- Does not repeat a TOEFL item type as a substitute for the lesson's own Phase 3 fact-check or Collaborative
Evidence Matrix. Those stay as originally generated for every student.

SECTION 1: TASK STRUCTURE

1.1 Excerpting the anchor text for TOEFL length

Real TOEFL iBT Reading passages run shorter than this program's Advanced/Proficient anchor texts (400-520 words
and 600-900 words respectively, per Section 0.2 of the lesson prompt, versus TOEFL's own ~200-word Academic
Passage and ~70-100-word Complete the Words paragraph). Do not shorten or rewrite the anchor text to fit; instead,
excerpt real, continuous, self-contained spans directly from it:

- Read an Academic Passage excerpt: a continuous ~180-220 word span from the anchor text that reads as
self-contained (does not open or close mid-idea, does not require content from outside the excerpt to make sense).
Prefer a span that includes a full rhetorical unit (an example, a comparison, a stated cause-and-effect) so
Rhetorical Purpose and Inference questions (1.3) have real material to test.
- Complete the Words excerpt: one ~70-100 word paragraph from the anchor text, used whole. Keep the first
sentence fully intact (per the official format); blank the second half of every second word thereafter (10 words
total), mixing content words (nouns, verbs, adjectives) and function words (prepositions, conjunctions, articles),
consistent with the worked example in the TOEFL guide.
- Read in Daily Life set: only generate this task type if the anchor text's genre (per Section 0.6 of the lesson
prompt) is itself a practical/informal format, an email/message exchange, notice, or similar. Genre rotation means
this will happen naturally on some cycles and not others; do not force an academic/narrative anchor text into an
email format just to complete the set. When the genre doesn't fit, generate only the two task types above and say
so in the packet header, rather than fabricating a mismatched text.

1.2 Task types and item counts (per TOEFL's own structure)

- Complete the Words: one paragraph, 10 blanked words, scored as 10 items. No answer choices; students supply
the missing letters, as in the real task.
- Read in Daily Life (when applicable, see 1.1): 2-3 multiple-choice items per short text, testing main
purpose, inference from informal language, or scanning for a practical detail (date, deadline, request).
- Read an Academic Passage: 5 multiple-choice items per excerpt, drawn from the question types in 1.3.

1.3 Question types by band (default split, overridable per 0.2)

Basic Comprehension (default for Advanced band, Levels 5-6, and included for Proficient):
1. Factual / Negative Factual - stated information; at least one item per set should be a Negative Factual
(NOT/EXCEPT) item.
2. Vocabulary - meaning-in-context of a word from the excerpt. Prefer testing one of the lesson's own 4-6
pre-taught target words when the excerpt contains one, but do not force it; testing other in-context vocabulary is
authentic to the real task and is fine.
3. Select the Sentence - identify which of 4 sentences in a specified paragraph serves a stated function
(definition, example, cause/effect, comparison, supporting evidence).
4. Sentence Simplification - paraphrase-recognition item on one genuinely complex sentence from the
excerpt (the anchor text's own grammar ceiling per Section 0.2 of the lesson prompt sets how complex that
sentence can be).
5. Reference - identify the referent of a pronoun or demonstrative in the excerpt.

Inferential Comprehension (default addition for Proficient band, Levels 7-8; optional add-on for Advanced band per
0.2):
6. Inference - a conclusion supported by, but not stated in, the excerpt.
7. Rhetorical Purpose - why the author included a specific example, comparison, or piece of information.
8. Insert Text - given an extra sentence, identify where in a marked paragraph (4 candidate locations) it best
fits, using the same content-clue/language-clue logic (cohesive devices, pronouns, synonyms) as the TOEFL
guide's own strategy section.

Every Read an Academic Passage set (5 items) should draw from at least 3 distinct question types, not repeat the
same type 5 times, matching how the real test mixes types within a set.

1.4 Answer key and explanations (required)

For every item, provide the correct answer and a short explanation in the same style as the TOEFL guide's own
worked examples: state why the correct choice is right by pointing to specific wording in the excerpt, and briefly say
why each incorrect choice is wrong (misstates the text, contradicts it, or is outside the excerpt's scope). This is
answer-key material for the instructor, not part of the student-facing packet (see 2.1).

1.5 Item metadata (required, answer key only, for future tracking)

A future goal is per-student tracking of which TOEFL question types a student consistently misses, aggregated across
many lessons. A single packet only has 1-2 items per question type, so that pattern can only be seen by combining
results across lessons, which requires every item to already carry consistent, structured metadata the moment it's
generated. Do not label question types on the student-facing packet itself (see 0.3 and 2.2): the real TOEFL test
never tells a student which type of question they're looking at, and recognizing the type from the question's own
wording is part of the skill being tested. This metadata is answer-key-only, generated every time, whether or not a
tracking system exists yet to consume it.

At the end of the instructor answer key, include one metadata table with one row per item:

- Item ID: a stable identifier, built as {BAND}-L{lesson number}-{TASK}-{ref}, where BAND is ADV or PROF, TASK is
CTW (Complete the Words), RDL (Read in Daily Life), or RAP (Read an Academic Passage), and ref is W1-W10 for
Complete the Words (word position) or Q1-Q5 (etc.) for the other two task types. Example: ADV-L1-RAP-Q3.
- Task Type: Complete the Words / Read in Daily Life / Read an Academic Passage.
- Question Type: one of the 8 types in 1.3 (Factual, Negative Factual, Vocabulary, Select the Sentence, Sentence
Simplification, Reference, Inference, Rhetorical Purpose, Insert Text). For Complete the Words items, which aren't
one of the 8 comprehension types, use Word Class (Content or Function) instead.
- Correct Answer: the letter, or the word, for that item.
- Source Text: which anchor text the item draws from. Almost always "Single" (one anchor text); use "Text 1" /
"Text 2" for a dual-text Proficient lesson (per Section 0.2 of the lesson prompt's Level 7 form guidance -
corrected from a Section 0.1 reference in earlier drafts of this prompt).
- Pre-taught Vocabulary Overlap: Yes/No, only for Vocabulary-type items; whether the tested word is one of the
lesson's own 4-6 pre-taught target words (blank for all other rows).

This table is what a future tracker reads, whether that means a teacher copying rows into a spreadsheet by hand or
an automated import; keep the format consistent across every packet so nothing has to be re-derived from prose
explanations later.

SECTION 2: FORMAT

2.1 Two documents: student packet and answer key

Produce the student-facing task packet (excerpts, instructions, blanks/questions, answer choices, no answers
revealed) and a separate instructor answer key (correct answers plus the explanations from 1.4, plus the item
metadata table from 1.5) as two documents, the same separation the base program uses between a test and its scoring
guide.

2.2 Required elements in the student packet

- A header naming the source lesson (Module, Band, lesson topic/title) and noting this is optional TOEFL
Reading practice extending that lesson, not a separate assessment of it.
- Each excerpt reproduced in full as its own labeled section (e.g. "Read an Academic Passage Excerpt"), followed
immediately by its task.
- Clear task-type labels matching TOEFL's own naming (Complete the Words / Read in Daily Life / Read an
Academic Passage) so students who go on to take the real test recognize the format.
- An estimated completion time, sized to the item counts in 1.2 (a single Academic Passage set plus one Complete
the Words paragraph should run roughly 15-20 minutes; note this in the header so it fits realistically into a Day 2
Phase 3 extension slot or a homework assignment).

2.3 Style constraints

Reuse the base program's constraints: no em-dashes, clear instructions over decorative language. Excerpt text itself
is quoted verbatim from the anchor text and is exempt from the lesson prompt's own drafting constraints (Section
0.2's vocabulary/grammar ceilings governed the anchor text at the time it was written; do not re-edit the excerpt to
change its register).

SECTION 3: SELF-CHECK BEFORE FINALIZING

1. Does every excerpt trace back verbatim to the source lesson's actual anchor text, with no rewriting?
2. Does every tested vocabulary item come from the excerpt itself, and where possible, overlap with the lesson's
own pre-taught word list?
3. Is the question-type split correct for the band (Basic only for Advanced by default, Basic + Inferential for
Proficient by default), and if overridden, is the override stated in the header?
4. Does the Read an Academic Passage set draw from at least 3 distinct question types?
5. Was a Read in Daily Life set generated only when the anchor text's genre actually supports it (1.1), never forced?
6. Does the Complete the Words excerpt keep its first sentence intact and blank exactly 10 words, mixing content
and function words?
7. Is the answer key a separate document from the student packet, with an explanation (not just a letter) for every
item?
8. Does the packet header make clear this is optional extension work layered on an unchanged shared lesson, not
a replacement for any part of the Day 1/Day 2 cycle?
9. Does the answer key end with a complete item metadata table (1.5), one row per item, with consistent Item IDs,
Task Type, Question Type (or Word Class for Complete the Words), Correct Answer, Source Text, and Pre-taught
Vocabulary Overlap where applicable? Is this table absent from the student-facing packet?
