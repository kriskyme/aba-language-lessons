# Passage Reading Homework Generation Prompt (v2)

Companion to the Passage Reading Lesson Generation Prompt. Generates one homework assignment from a single
completed 2-day lesson, for the general (non-TOEFL) track: one section per task Level in the band, each keyed to
that Level's position (lowest, in between, highest) plus Foundation Support where applicable.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`
alongside it. Quality Standards §A-§C (task Levels, Respectful Tiers, item quality) govern every item and are not
restated. This prompt states only what is specific to Reading homework.

**Current version: v2.** History: `Changelog.md`.

**Input:** the completed lesson, Day 1 and Day 2 in full (anchor text with paragraph lettering, Phase 1
vocabulary and idiom list, Skill Spotlight, Module, Band), supplied directly. If none is provided, stop and ask.
Never generate lesson content from this prompt.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs

- The source lesson as above. Every word, topic, and skill comes from it; invent nothing.
- **Timing:** which point in the cycle the homework is assigned at. Default: after Day 1, due at the start of Day
  2 (0.2). State the assumption in the header.
- **Task-Level information:** which task Level each student or group is working at, or Foundation Support. Build
  each Level's homework from what that Level actually did in class.
- **Track:** general track only. TOEFL-track students use `Generate_TOEFL_Extension_Prompt_*.md` for the same
  cycle instead (1.4); never both.

### 0.2 Timing determines what content is available

**Default, after Day 1:** the anchor text, vocabulary, idioms, and the Skill Spotlight (named and practiced once
through Day 1's own items) are available. Day 2's refresher text, matrix, oral protocol, and Closing Transfer
Check are not; do not draw on them. Part 2 may still ask for a light written skill-application task, since the
skill was named and modeled on Day 1.

**Alternative, after Day 2:** Part 2 may build on or extend the student's own in-class Closing Transfer Check
response. State this timing in the header.

## SECTION 1: STRUCTURE

### 1.0 Target length: 15-20 minutes, one sitting

Light, individual reinforcement, not a scaled-down assessment, sized across both parts and all Levels to 15-20
minutes at the student's own Level (the same budget as the TOEFL extension packet, so both tracks stay
comparable).

### 1.1 Two parts, one section per task Level

One Part 1 / Part 2 section per task Level in the band, each grounded in its own CSV objective. The design
template is set by position: the **lowest** Level uses the most scaffolded design; the **highest** the most
independent; every Level **between** (both native Levels in a 4-Level band; the middle Level in Beginner) the
middle design, each with its own content; **Foundation Support** the non-verbal design.

**Part 1: Vocabulary & Idiom in Production.** 3-4 words or idioms from the Phase 1 list (a working subset, not
full coverage). Require original sentences, not fill-in-the-blank recognition; producing is a harder skill than
recognizing.
- **Lowest:** a word bank plus sentence starters or frames (reuse a frame family from the lesson). Credit any
  reasonable, correctly used sentence.
- **In between:** independent original sentences, one per word, no starter.
- **Highest:** combine 2-3 words into one connected short paragraph (3-5 sentences) on a topic of the student's
  choice.
- **Foundation Support:** point-and-name with a caregiver from 2-3 picture cards, match a word to a picture, or
  draw one target word, matching the in-class response mode.

**Part 2: Skill Practice.** Restate the Skill Spotlight in the exact plain language Day 1 used; never a
paraphrase or a broader skill. Ask the student to apply it to something in their own life or surroundings, new
content, never a re-analysis of the anchor text (Phase 3 already did that work in class). This is a light written
preview of the Closing Transfer Check's move: producing a new instance, not recognizing one.
- **Lowest:** 1-2 sentences with a frame mirroring the lesson's Closing Transfer Check design.
- **In between:** 2-3 independent sentences, no frame.
- **Highest:** 3-4 sentences including a brief explanation of why the chosen word or detail reveals what it
  does, the reasoning-about-craft standard the highest Level meets elsewhere.
- **After Day 2:** at every Level, a second, different example extending the in-class Closing Transfer Check
  response rather than repeating it.

### 1.2 Grading is light-touch

Checked for genuine attempt and correct use, not scored with the assessment's task-Level-internal percentage. A
short completion checklist per Level, 2-3 plain criteria ("used the word correctly," "sentence connects to the
named skill," "attempted independently"). The Set's assessment carries the graded weight.

### 1.3 Respectful Tiers

Quality Standards §B: the lowest Level's Part 2 is a genuine, simplified skill-application item, never vocabulary
practice alone.

### 1.4 TOEFL-track students

Use `Generate_TOEFL_Extension_Prompt_*.md` instead; it already produces a 15-20 minute packet from the same lesson.
Never both for one student in one cycle.

## SECTION 2: FORMAT

One document per assignment: a header naming the source lesson (Module, Band, topic), the timing (after Day 1 or
Day 2), and estimated completion time; Part 1 before Part 2; sections lowest Level first through highest, then
Foundation Support if applicable; the Skill Spotlight restated verbatim directly above Part 2; a completion
checklist per Level. No answer key. Style per Quality Standards §E; each Level's vocabulary and grammar inside the
same ceiling the lesson used for that Level.

## SECTION 3: SELF-CHECK BEFORE FINALIZING

Run `shared/Generation_Quality_Standards.md` §F first. Then:

1. Every Part 1 item traces to the lesson's Phase 1 list?
2. Part 2 uses the exact Skill Spotlight wording and asks for a new application, not anchor-text re-analysis?
3. Timing respected: after Day 1, no Day 2 content required?
4. Design template keyed to each Level's position; Foundation Support version generated where the lesson has the
   layer?
5. Grading a completion checklist, not a percentage system (1.2)?
6. Whole assignment about 15-20 minutes (1.0)?
7. General track confirmed; TOEFL-track students routed to the extension prompt (1.4)?
