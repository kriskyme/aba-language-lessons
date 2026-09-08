# Listening/Speaking TOEFL Track Tier Prompt (v1)

**What this generates:** a TOEFL-capable variant of an already-generated Listening/Speaking Set. It threads
TOEFL-relevant skill practice through both days of each lesson (a teacher-narrated connection in Phases 1 and 3
of each day, three small in-class touchpoints, and one capstone task per day) so a mixed class can differentiate
by TOEFL interest as well as by ability: a student who wants TOEFL practice gets it woven through the cycle;
everyone else does every phase exactly as the base lesson already has it.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md`, `shared/Generation_Quality_Standards.md`,
and `shared/Student_Packet_Style_Guide.md` alongside it, plus the base lesson's `.md`, `.html`, and
`_Transcript.md` files. Section 1 produces the lesson-side content; Section 2 renders it in the packet.

**Current version: v1.** History: `Changelog.md` (this mechanism was Section 0.6 of the Lesson prompt through v1.10).

## SECTION 0: SCOPE

- **Band restriction.** Advanced (Levels 5-6) or Proficient (Levels 7-8) only; TOEFL iBT assumes B2+ ability.
  Refuse a Beginner/Intermediate request and say why, rather than producing a simplified, non-representative
  task.
- **Opt-in per Set.** Generate only when a TOEFL-capable variant of a Set is asked for; a normal lesson request
  produces no TOEFL content. A fork may hold as few as one of the base Set's lessons.
- **Grounded in:** `source/TOEFL_Listening_extracted_text.txt` (the real TOEFL iBT Listening section: 6 question
  types - Main Idea, Factual, Inference, Purpose, Method, Attitude) and `source/TOEFL_Speaking_extracted_text.txt`
  (the real TOEFL iBT Speaking section: Listen and Repeat, Take an Interview, their 0-5 scoring guides).
- **Where it lives (Conventions §D, §G).** A fork, never an in-place edit of the base files:
  `lessons/<band>/Module_<N>/Set_<N>_T/Lesson_<n>_<Slug>/`, same internal shape as `Set_<N>/`. Version code
  `<Module>.<Set>T.<Lesson>.<Version>` (e.g. `1.1T.1.0`), iteration bumped on a substantive revision. The base
  `Set_<N>/` files are never touched; a class with no TOEFL-track students keeps using them.
- **Three artifacts per forked lesson:** the lesson `.md`, the main student packet `.html`, and D's teacher-only
  homework file `<TopicSlug>_<Level>_L<n>_TOEFL_Homework.html` (same naming root, `_TOEFL_Homework` suffix),
  generated in the same pass immediately after the main packet, never appended into it. The base transcript file
  is reused, not duplicated.
- **Grounded in the lesson's real source and vocabulary throughout.** Never a fabricated topic; any wording quoted
  from the source stays inside the Lesson prompt's fair-use ceiling (0.3 item 4).

## SECTION 1: THE FOUR TOUCHPOINT KINDS (LESSON SIDE)

**A) Framing connections - teacher script only, whole class.** Under Day 1 Phases 1 and 3 and Day 2 Phases 1 and
3, add one short "TOEFL Connection" sentence naming which real TOEFL question type (Main Idea, Factual,
Inference, Purpose, Method, Attitude) or scoring criterion (Intelligibility, Accuracy, Relevance, Elaboration,
Delivery, Language Use) that phase's already-named listening strategy, speaking skill, or pronunciation feature
maps to. Teacher narration only, said aloud when TOEFL-track students are present; never printed in the packet;
the activity itself is not differentiated.

**B) In-class differentiated touchpoints - opt-in, on the class's shared pacing, no individual timing.**
- *Day 1 Phase 2 (organizer):* TOEFL-track students add one extra column to the same shared note organizer,
  tagging each note with which of the 6 question types it would answer.
- *Day 1 Phase 5 (Listening Closing Transfer Check):* after the teacher reads the script, TOEFL-track students
  answer one additional short question about it, written in one of the 6 real question types, alongside (not
  instead of) the partner retell.
- *Day 2 Phase 4 (oral output):* TOEFL-track students get one of their protocol turns reframed as a
  Take-an-Interview-style prompt (personal to abstract), still spoken live within the protocol's pacing.

**C) Capstone Listening task (Day 1 Phase 4) - same shared source, no separate passage, no separate listening.**
The band's highest task Level gains one additional, clearly labeled alternate task alongside (never replacing)
its existing task, answered from the same real source every student already heard together in Phase 2. Write
items in the real TOEFL question-type styles, drawing from at least 3 of the 6 types, referencing that shared
listening directly; never invent a new passage or request a second playback or reading. Correct answers paraphrase
the source rather than quote it; distractors are topically adjacent but wrong (Quality Standards §C2, §C4); any
stem or option that references specific wording stays inside the fair-use ceiling. Provide a full answer key with
an explanation per item (point to specific source content, debunk each distractor) in the lesson `.md` only.

**D) Capstone Speaking task (Day 2 Phase 2) - untimed in-class rehearsal plus teacher-recorded Teams homework.**
Real individually-timed TOEFL Speaking mechanics (Listen and Repeat's 8/10/12-second windows, Take an Interview's
45-second no-prep windows) cannot run live while the rest of a mixed class works a different task, so the timed
version is independent practice and the phase keeps an untimed rehearsal:
- *In class:* TOEFL-track students get an untimed paired rehearsal of same-shape practice content (practice
  sentences and questions in the same style as the real items, said aloud to a partner, no stopwatch, no
  scoring). A warm-up, not the scored version; different content from the real items below.
- *At home:* author the real 7 Listen and Repeat sentences, grounded in the lesson's real topic and vocabulary in
  a short plausible scenario, following the real progression (2 short, 9-11 syllables, 8 sec; 3 medium, 14-16
  syllables, 10 sec; 2 long, 19-23 syllables, 12 sec), and 4 original Take an Interview questions progressing
  personal to abstract/speculative (45 sec each, no prep). Reproduce the real TOEFL Scoring Guides (0-5,
  Intelligibility/Accuracy for Listen and Repeat; 0-5, Relevance/Elaboration/Delivery/Language Use for Take an
  Interview). **Delivery:** the teacher records one real audio playback per item from this script, matching each
  item's response window, and posts it to the class's Teams; each student listens once and records their spoken
  response there by an assigned date (the same Teams Speaking Progress recording mechanism the Assessment
  prompt's Part B uses). The teacher scores each recording against the guides.

**Heard, not read.** Every real TOEFL Listening/Speaking task is heard once, never read silently by the
test-taker. C's questions and answer choices may be printed (they are answered from the shared listening; there is
no separate passage to protect). D's real 7 sentences and 4 questions are absent from the main student packet
entirely; a student's only exposure to them is the teacher's recorded audio. The homework file prints them in
full because it is the teacher's own recording script and scoring guide, never given to or read by a student.

**Item metadata (lesson `.md` only, never the packet).** End the TOEFL section of the lesson `.md` with one
table row per item for cross-lesson tracking: Item ID (`{BAND}-L{lesson number}-{TASK}-{ref}`, TASK one of `LSN`
for C, `LNR`/`TIV` for D, `XFER` for the B Phase 5 question), Task Type, Question/Item Type (one of the 6 types
for C and the Phase 5 question; complexity tier for Listen and Repeat; personal/abstract category for Take an
Interview), Correct Answer (C and the Phase 5 question only). The Phase 2 organizer column and the Phase 4 reframed
turn need no rows.

**Lesson `.md` conventions.** Mark each touchpoint in place under its phase, labeled "(TOEFL)" inline; A's
sentences as teacher notes; C and D's in-class rehearsal as a sibling "Task D (TOEFL)" block after the regular
Task D content; the lesson's metadata line carries the `T` version code. Everything else in the base lesson is
carried over unchanged.

## SECTION 2: RENDERING IN THE STUDENT PACKET

Apply the Student Packet prompt in full, plus these additions. Translation rows (Style Guide §E principle):

| Teacher-facing term | Student-facing rendering |
|---|---|
| A framing connections | Never rendered; teacher-only narration. |
| B touchpoints | Each a plainly labeled "(TOEFL)" addition at its own location inside the existing structure it extends (2.1, 2.3, 2.6 below), never narrated as test-prep jargon. |
| C and D capstones | Each its own sibling `Task D (TOEFL)` block styled exactly like the regular lettered tasks (2.2, 2.4), never a "TOEFL Track option" callout nested inside the regular task. D's real items never appear in the main packet. |

**2.1 Note-organizer column (B).** Add one extra column to the same Listening Notes organizer table, headed
plainly ("TOEFL Question Type"), left blank for fill-in. Do not build a second organizer.

**2.2 Listening capstone (C).** Its own sibling `.task-block` immediately after the regular highest-Level task
block, styled exactly like the lettered tasks (`.instr-line` with `.exercise-label` and the same `.stars` as the
task it sits beside), headed `Task D (TOEFL)`. No explanatory paragraph: one top-of-task instruction line ("Circle
the best answer for each question below."), then the numbered items with answer choices via `.mc-list`/
`.mc-letter` (Style Guide §H.1).

**2.3 Extra transfer-check question (B).** One additional numbered `.qitem` directly after the regular Show What
You Noticed response space, tagged "(TOEFL)". It answers from the same script everyone heard; do not print a
second script or a second "don't read ahead" block.

**2.4 Speaking capstone, in-class rehearsal (D).** Its own sibling `.task-block` after the regular highest-Level
Practice It block, headed `Task D (TOEFL)` with the same star rating. Print a short scenario line (context only,
never implying a stopwatch or "the real thing"), then one explicit up-front roles instruction before either
practice list ("Take turns with a partner: one person reads, the other listens and repeats or answers. Switch
roles halfway through."), then the practice sentences ("Reader: read each line once. Listener: repeat it back.")
and practice questions ("Reader: ask each question. Listener: answer in a sentence or two."). No `.time-list`, no
response-time windows, no reference to the homework file.

**2.5 Teacher-only homework file (D).** A separate, self-contained HTML file named
`<TopicSlug>_<Level>_L<n>_TOEFL_Homework.html` in the lesson folder, reusing the base stylesheet, this modality's
§H.1 classes, its own `.masthead-meta` two-tag masthead (same Band and `T` version code) and print button. Inside
one `.reader-copy` box headed via `.reader-warn` with "Teacher use only - recording script and scoring guide. Do
not print or share with students.": brief instructions at the top (record one audio playback per item matching
its response window, post to Teams, have students record their response there by an assigned date, score with the
guide below); the scenario line for each half; the 7 sentences and 4 questions; a `.time-list` showing each
item's real response window (8/10/12 seconds; 45 seconds); the real TOEFL Scoring Guides beneath each half.
Never cross-referenced from the main packet.

**2.6 Reframed protocol turn (B).** One more prompt in the same Discuss It list, tagged "(TOEFL)", never singled
out into a separate box.

## SECTION 3: SELF-CHECK BEFORE FINALIZING

Run Quality Standards §F and the Lesson prompt's 0.5 on the forked lesson, and Style Guide §I plus the Student
Packet prompt's own list on the packet. Then:

1. All four touchpoint kinds present: A in Day 1 Phases 1 and 3 and Day 2 Phases 1 and 3; B's organizer column,
   Phase 5 question, and reframed Phase 4 turn; C on the same shared source with at least 3 of the 6 question
   types and a full explained answer key; D split into untimed rehearsal plus the recorded Teams homework?
2. Everything grounded in the lesson's real source and vocabulary; quoted wording inside the fair-use ceiling?
3. Main packet entirely free of D's real sentences and questions; A never rendered; each B touchpoint inside its
   existing structure with a "(TOEFL)" tag; C and D's rehearsal as sibling `Task D (TOEFL)` blocks with no
   explanatory paragraph, C holding only questions and choices, D's rehearsal with no `.time-list` and no
   pointer to the homework file?
4. Homework file present, teacher-only labeled, describing the record/post-to-Teams/student-records mechanism
   (never a "reading partner"), with `.time-list` and both scoring guides, never referenced from the packet?
5. Item metadata table present in the lesson `.md` for every C, D, and Phase 5 item, absent from the packet?
6. Files in `Set_<N>_T/` (lesson `.md`, main packet, homework file), version code `<Module>.<Set>T.<Lesson>.<Version>`,
   base `Set_<N>/` files untouched?
