# Passage Reading TOEFL Track Extension Prompt (v1.1)

Companion to the Passage Reading Lesson Generation Prompt. Generates a TOEFL iBT Reading-format task packet from
an already-completed Advanced or Proficient band lesson, for the subset of a mixed class who want TOEFL
preparation: the class runs one shared lesson (same anchor text, same Day 1/Day 2 core) and TOEFL-interested
students additionally receive a packet drawn from that same anchor text, formatted as authentic TOEFL Reading
practice. The base lesson is unchanged for everyone. The packet works from the band-level anchor text and Phase 1
vocabulary, so it is not differentiated by task Level.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`
alongside it (§C's item-quality rules apply to every item here).

**Current version: v1.1.** History: `Changelog.md`.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Band restriction

Advanced (Levels 5-6, B2-B2+) or Proficient (Levels 7-8, C1-C2) only. TOEFL iBT Reading assumes B2+ ability;
forcing its question types onto a Level 1-4 text breaks both the band's ceiling and the task's authenticity.
Refuse a Beginner/Intermediate request and say why.

### 0.2 Required inputs

1. The source lesson: its anchor text in full, its Phase 1 vocabulary list (4-6 words plus any idiom spotlight),
   Module, and Band. Invent no topic or passage.
2. Which tier of question types (1.3): Advanced defaults to Basic Comprehension only; Proficient to Basic plus
   Inferential. Overridable by request; state the default and apply it unless told otherwise.
3. Delivery context: default an add-on for TOEFL-interested students working independently or in a small group
   (during Day 2 Phase 3, or as a 15-20 minute extension or homework packet) while the rest of the class runs the
   Structured Oral Output; note the assumption in the header. A TOEFL-track student uses this instead of the
   Homework prompt's packet for the same cycle, never both.

### 0.3 What this prompt does not do

- Invent an anchor text, topic, or vocabulary set; every excerpt and tested word traces to the source lesson.
- Alter the base lesson, its task Levels, or its oral-output tasks.
- Shift the whole class into silent, timed, multiple-choice work; that modality mismatch with the program's
  oral-first design is why this is an optional add-on for a subset.
- Substitute a TOEFL item for the lesson's own Phase 3 fact-check or Collaborative Evidence Matrix.

## SECTION 1: TASK STRUCTURE

### 1.1 Excerpting the anchor text for TOEFL length

Real TOEFL passages are shorter than this program's Advanced/Proficient anchor texts (about 200 words for an
Academic Passage, 70-100 for Complete the Words). Do not shorten or rewrite the text; excerpt real, continuous,
self-contained spans:

- **Read an Academic Passage:** a continuous 180-220 word span that opens and closes on whole ideas and needs no
  outside content, preferably containing a full rhetorical unit (an example, a comparison, a cause-and-effect) so
  Rhetorical Purpose and Inference items have material.
- **Complete the Words:** one 70-100 word paragraph used whole; first sentence intact; thereafter blank the second
  half of every second word (10 words total), mixing content and function words.
- **Read in Daily Life:** only when the anchor text's genre is itself a practical or informal format (an email or
  message exchange, a notice). When the genre does not fit, generate only the two task types above and say so in
  the header; never force an academic or narrative text into an email format.

### 1.2 Task types and item counts

- **Complete the Words:** one paragraph, 10 blanks, 10 items; no answer choices.
- **Read in Daily Life** (when applicable): 2-3 multiple-choice items per short text (main purpose, inference from
  informal language, scanning for a practical detail).
- **Read an Academic Passage:** 5 multiple-choice items per excerpt from the types in 1.3, drawing on at least 3
  distinct types.

### 1.3 Question types by band

**Basic Comprehension** (Advanced default; included for Proficient):
1. Factual / Negative Factual (at least one NOT/EXCEPT item per set).
2. Vocabulary, meaning in context; prefer one of the lesson's pre-taught words when the excerpt contains one, but
   do not force it.
3. Select the Sentence: which of 4 sentences in a paragraph serves a stated function (definition, example,
   cause/effect, comparison, evidence).
4. Sentence Simplification: paraphrase recognition on one genuinely complex sentence.
5. Reference: the referent of a pronoun or demonstrative.

**Inferential Comprehension** (Proficient default; optional for Advanced):
6. Inference: a conclusion supported by, but not stated in, the excerpt.
7. Rhetorical Purpose: why the author included a specific example, comparison, or detail.
8. Insert Text: where in a marked paragraph (4 candidate locations) an extra sentence best fits, by cohesive
   devices, pronouns, and synonyms.

Distractors follow Quality Standards §C2 and §C4: plausible near-misses, never one obviously right option against
absurd alternatives.

### 1.4 Answer key and explanations

For every item, the correct answer and a short explanation pointing to specific wording in the excerpt for why the
correct choice is right and why each incorrect choice is wrong (misstates, contradicts, or falls outside the
excerpt). Instructor-only.

### 1.5 Item metadata (answer key only)

For future per-student tracking of missed question types across lessons, end the answer key with one metadata
table, one row per item. Never label question types on the student packet; recognizing the type is part of the
skill.

- **Item ID:** `{BAND}-L{lesson number}-{TASK}-{ref}` (BAND: ADV or PROF; TASK: CTW, RDL, or RAP; ref: W1-W10 for
  Complete the Words, Q1-Q5 otherwise), e.g. `ADV-L1-RAP-Q3`.
- **Task Type:** Complete the Words / Read in Daily Life / Read an Academic Passage.
- **Question Type:** one of the 8 types in 1.3; for Complete the Words, Word Class (Content or Function).
- **Correct Answer:** the letter or word.
- **Source Text:** "Single," or "Text 1" / "Text 2" for a dual-text Proficient lesson (Lesson prompt 0.2, Level 7).
- **Pre-taught Vocabulary Overlap:** Yes/No for Vocabulary items only.

Keep the format identical across every packet so a tracker (a spreadsheet or an import) never re-derives it.

## SECTION 2: FORMAT

### 2.1 Two documents

A student-facing task packet (excerpts, instructions, blanks and questions, answer choices, no answers) and a
separate instructor answer key (1.4 plus the 1.5 table).

### 2.2 Required elements in the student packet

- A header naming the source lesson (Module, Band, topic), stating that this is optional TOEFL Reading practice
  extending that lesson, not an assessment of it, and an estimated completion time (one Academic Passage set plus
  one Complete the Words paragraph runs roughly 15-20 minutes).
- Each excerpt reproduced in full as its own labeled section, followed immediately by its task.
- Task-type labels matching TOEFL's own naming, so students recognize the format on the real test.

### 2.3 Style

Quality Standards §E. Excerpt text is quoted verbatim from the anchor text and is never re-edited for register.

## SECTION 3: SELF-CHECK BEFORE FINALIZING

Run `shared/Generation_Quality_Standards.md` §F's item-quality items (6-9, 12). Then:

1. Every excerpt verbatim from the source anchor text, no rewriting?
2. Every tested vocabulary item from the excerpt, overlapping the pre-taught list where possible?
3. Question-type tier correct for the band, any override stated in the header?
4. The Academic Passage set draws on at least 3 distinct types?
5. Read in Daily Life generated only when the genre supports it?
6. Complete the Words keeps its first sentence intact and blanks exactly 10 words, mixing content and function?
7. Answer key a separate document with an explanation for every item?
8. Header states this is optional extension work on an unchanged shared lesson?
9. Metadata table complete in the answer key and absent from the student packet?
