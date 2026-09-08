# Listening/Speaking Assessment Student Print Formatting Prompt (v2.1)

Companion to the Listening/Speaking Assessment Generation Prompt. Takes one completed Set assessment (Part A
Listening, Part B Speaking) and produces a single, print-ready, black-and-white student handout with every
teacher-facing element removed or translated: Part A's answer keys, point values, and pass notes; Part B's rubric
and any submission-mechanism information. **The one exception:** a short self-check checklist derived from Part
B's rubric Meets column appears on each Speaking Task card (2.7).

**Paste bundle:** run this prompt with `shared/Student_Packet_Style_Guide.md` alongside it (§A-§C format and
stylesheet, §E translations, §F task rules, §G regeneration, §H.1 this modality's delta classes and §H.4
`.checklist`, §I shared packet self-check). This prompt states only what is specific to a Listening/Speaking
assessment packet.

**Current version: v2.1.** History: `Changelog.md`.

**Input:** the completed Assessment `.md` in full: Part A's citation block per clip and segment labels, every task
Level's items (vocabulary is inside each Level's item set, not a separate list), and Part B's per-Level speaking
prompts and rubrics. Pull all content from it; invent nothing; drop no task Level. Student version only.

**Never carry into the student copy:** any `[Answer: ...]` tag, point value, or holistic pass note; the rubric's
Not yet/Developing columns or table shape; any submission-mechanism information (platform name, submit-by date,
re-recording note, live-delivery note), which is teacher-communicated logistics.

## SECTION 1: ASSESSMENT-SPECIFIC TRANSLATIONS

Style Guide §E applies. Add these:

| Teacher-facing term | Student-facing rendering |
|---|---|
| Listening or speaking strategy names | Not named; the item asks its question. |
| Task Level | A star rating labeling which page a student was assigned, never a menu. |
| Answer tags, point values, pass notes | Not shown. |
| Rubric (Not yet/Developing/Meets) | A plain self-check checklist on that Level's Speaking Task card (2.7), Meets-column language reworded to the student. |
| "Emphasizes [skill]" framing | Folded into the task's own wording ("Compare the two rooms, then explain the order you'd show them"), never named as a measured skill. |
| Teams Speaking Progress, submission date, re-record or live-delivery notes | Not shown anywhere. |
| Segment labels | Shown in plain form, as in the lesson packet. |
| "New, unseen source" / "transfer" framing | Not named; the student sees the citation box and the test. |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One document, two sections, per-Level pages

One document in two sections mirroring the assessment: a **Listening Test** section (Part A) and a **Speaking
Task** section (Part B), labeled plainly as what they are, not "Unit" or by day. Within the Listening Test, each
task Level's material is its own page-break section ("Listening Test - ★★" as running head) containing only that
Level's items, `page-break-before: always` on each, so a teacher distributes selectively; never a merged
choose-your-task block. No `.masthead-meta` stack, no Name/Date field, kicker, subtitle, or footer; the running
head shows the assigned Level.

### 2.2 What You'll Listen To

One `.citebox` per clip (the assessment uses 2-3), same content rules as the lesson packet's citebox (title, one
plain sentence, platform; no runtime, credits, or "ask your teacher for the link"), all placed together at the top
of the Listening Test section immediately before the first Level's items. Carry plain segment names into any item
that references part of a clip.

### 2.3 No vocabulary list, no notes organizer

The assessment tests vocabulary only inside numbered items and has no notes phase. Do not add a Words to Know
list or a `.notes-table`; their absence is correct.

### 2.4 Listening Test items

Each Level's items as plain numbered questions (`.qlist`), in source order. Every item is multiple choice,
fill-in-the-blank, or matching; no open-ended line to size. Style Guide §F governs layout: options inline with
one top-of-page `.task-instr` line, embedded images for picture items (never an empty box), banks before their items, matching via
`.match-list`/`.match-row`. A predict-then-confirm item stays one numbered item with both circles in one
instruction. Never print an item's answer, point value, or strategy.

### 2.5 Speaking Task cards

For each task Level, an instruction card with, in order: the topic in plain language; the task's concrete,
countable content requirements (the actual instructions); the target length; and a `.checklist` titled "Before
you submit, check:" with one item per rubric criterion, its Meets-column language reworded directly to the
student ("Both rooms described using the fixed frame"). No rubric columns or table shape; no submission
information anywhere. Label the card with the Level's stars; print all Levels' cards on one student's copy only
when the teacher deliberately wants a multi-Level reference sheet (flag as a teacher decision).

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Style Guide §A-§D, this modality's §H.1 classes (`.citebox`, `.task-instr`, `.pic-options`/`.pic-option`,
`.match-list`/`.match-row`, `.qitem`), and the shared `.checklist` class (§H.4). Do not include `.notes-table` or
`.vocab-list` CSS; their sections do not exist here.

## SECTION 4: WORKFLOW

Style Guide §G: run immediately after the Assessment `.md` is complete, in the same session; the `.md` is the
source of truth; content changes go into it and regenerate.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

Run `shared/Student_Packet_Style_Guide.md` §I first. Then:

1. Every answer tag, point value, and pass note absent (the rubric-derived checklist being the one deliberate
   exception)?
2. Sections labeled Listening Test and Speaking Task; each Level's Listening Test on its own page-break section
   with only its items?
3. A citebox for every clip, together at the top of the Listening Test, with no "ask your teacher" line?
4. No vocabulary list and no notes organizer anywhere (2.3)?
5. Every item objective-format, laid out per Style Guide §F, with predict-then-confirm as one item?
6. Each Speaking Task card: topic, countable requirements, target length, `.checklist` from the Meets column; no
   skill named as measured; no submission information anywhere?
