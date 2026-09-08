# Academic Writing Assessment Student Print Formatting Prompt (v4)

Companion to the Academic Writing Assessment Generation Prompt. Takes one completed Set's (Beginner) or Module
Pair's (Intermediate/Advanced/Proficient) assessment (Part A Grammar & Mechanics Check, Part B Writing Task) and
produces a single, print-ready, black-and-white student handout with every teacher-facing element removed or
translated: Part A's answer keys and point values; Part B's rubric. **The one exception:** a short self-check
checklist derived from Part B's rubric Meets column appears on each Writing Task card (2.5).

**Paste bundle:** run this prompt with `shared/Student_Packet_Style_Guide.md` alongside it (§A-§C format and
stylesheet, §E translations, §F task rules, §G regeneration, §H.3 this modality's delta classes and §H.4
`.checklist`, §I shared packet self-check). This prompt states only what is specific to a Writing assessment
packet.

**Current version: v4.** History: `Changelog.md`. Not yet run against a real Set or Pair.

**Input:** the completed Assessment `.md` in full: Part A's items across every task Level, and Part B's per-Level
tasks, Scenario, and rubrics. Pull all content from it; invent nothing; drop no task Level. Student version only.

**Never carry into the student copy:** any answer key or bracketed answer tag, point value, or holistic pass note;
the rubric's Not yet/Developing columns or table shape.

## SECTION 1: ASSESSMENT-SPECIFIC TRANSLATIONS

Style Guide §E applies, plus the Writing lesson packet's rows (no Focus A/B, Scenario, regime, or required-feature
language). Add these:

| Teacher-facing term | Student-facing rendering |
|---|---|
| Task Level | A star rating labeling which page a student was assigned, never a menu. |
| Answer keys, point values, pass notes | Not shown. |
| Rubric (Not yet/Developing/Meets) | A plain self-check checklist on that Level's Writing Task card (2.5), Meets-column language reworded to the student. |
| "Concrete, countable content requirements" framing | The task's plain instructions ("Include one comparison and one reason word"), never labeled as scored. |
| "New Scenario" / "transfer" framing; real-world form or Module verb names | Not named; the task says plainly what to write ("Write a paragraph comparing..."). |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One document, two sections, per-Level pages

One document in two sections mirroring the assessment: a **Grammar Check** section (Part A) and a **Writing
Task** section (Part B), labeled plainly, not "Unit" or by day. Within the Grammar Check, each task Level's
material is its own page-break section ("Grammar Check - ★★" as running head) containing only that Level's items,
`page-break-before: always` on each; never a merged choose-your-task block. No `.masthead-meta` stack, Name/Date
field, kicker, subtitle, or footer; the running head shows the assigned Level.

### 2.2 Grammar Check items

Each Level's items as lettered Tasks (`.task-block`/`.exercise-label`, Task A, B, ...) in source order, every
item numbered (Style Guide §F). Every item is fill-in-the-blank, choose-the-form, identify-sentence-type, or
combine-the-sentences. Answer space per Style Guide §I item 11: `.blank` inside a `.fillblank` sentence,
`.ans-line-sm` for a one-word or short answer on its own line, `.ans-line` rows for an original or combined
sentence; an editing-a-paragraph item uses a `.spotlight-box` for the paragraph plus a matched number of
`.ans-line` rows. No `.rule-table` or Grammar callout reviewing the rule unless the source item itself calls for
one; this is a check, not re-teaching. Never print an answer or point value.

### 2.3 Writing Task cards

For each task Level, an instruction card (`.spotlight-box`) with, in order: the Scenario in plain language; the
task's concrete, countable requirements as plain instructions; the target length; blank writing space
(`.ans-line` rows matching the target length, or a taller ruled block for essay-regime Levels); and a `.checklist`
titled "Before you submit, check:" with one item per rubric criterion, Meets-column language reworded directly to
the student. No rubric columns or table shape. Label the card with the Level's stars; print all Levels' cards on
one copy only when the teacher deliberately wants a multi-Level reference sheet.

### 2.4 Callouts and rules

Callouts reserved for Writing Task cards and a source-required editing paragraph; word banks use `.wordbank`; no
decorative rules.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Style Guide §A-§D, this modality's §H.3 classes (`.rule-table`, `.fillblank`, `.model-step`), and the shared
`.checklist` class (§H.4).

## SECTION 4: WORKFLOW

Style Guide §G: run immediately after the Assessment `.md` is complete, in the same session; the `.md` is the
source of truth; content changes go into it and regenerate.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

Run `shared/Student_Packet_Style_Guide.md` §I first. Then:

1. Every answer key, point value, and pass note absent (the rubric-derived checklist being the one deliberate
   exception)?
2. Sections labeled Grammar Check and Writing Task; each Level's Grammar Check on its own page-break section with
   only its items?
3. Every Grammar Check item numbered under lettered Tasks, in an objective format, with answer space per §I
   item 11 and no re-teaching callout?
4. Each Writing Task card: Scenario, plain requirements, target length, writing space sized to the Level, and a
   `.checklist` from the Meets column; nothing labeled as scored?
