# Academic Writing Student Print Formatting Prompt (v1.4)

Companion to the Academic Writing Lesson Generation Prompt (v3.4). Takes one completed Academic Writing lesson (an
8-day cycle) and produces a set of print-ready, black-and-white student handouts for it: one **Lesson Introduction
Page**, plus one **Unit** per day (Units 1-8, one source lesson day each), each its own self-contained HTML
document. Every piece of teacher-facing pedagogical language is translated into plain instructions a student (or
a parent glancing at the page) can act on without decoding jargon like "Focus A," "the Leveled Mentor Ladder," "task
Level," or "board-dependent moment."

**Current version: v1.4.** For the full dated version history and the reasoning behind each change, see
`Changelog.md`.

**Units, not segments:** Passage Reading lessons are a fixed 2-day cycle, so its print prompt
formats one whole lesson into one packet. Academic Writing lessons run 8 days. Printing all 8 days as one document
would either force a teacher to hand out a packet for content two weeks away, or produce an unwieldy
multi-section document that buries "what do I do today" under material for days the class hasn't reached yet. So
this prompt formats **one day at a time**: each source lesson day becomes its own **Unit**, numbered Unit 1
through Unit 8 in source-day order (Unit 1 = Day 1, Unit 2 = Day 2, and so on through Unit 8 = Day 8). A Unit is a
single, self-contained print file that a teacher can hand out on exactly the day it covers, with no other unit's
content bleeding into it.

**Continuation lettering (new in v1.2):** where a single source day's content is genuinely too long to lay out
cleanly on one Unit's page, or a teacher tells you they are splitting one lesson day across two class meetings,
split that Unit's content into **Unit Na** and **Unit Nb** (for example, Unit 4a and Unit 4b), each its own file,
each still covering only that one source day's content between the two of them, not spilling into the next day's
material. Use this only where it is genuinely needed; most days format cleanly as a single unnumbered Unit N.

**The Lesson Introduction Page (new in v1.2):** one additional file per lesson, generated once and meant to
precede all 8 Units. See the dedicated section below for its contents. It is not itself a Unit and carries no
Unit number.

Use this prompt only after the source lesson's relevant day(s) already exist. Do not use it to generate lesson
content, and do not use the lesson prompt to produce a student handout: the input is always an already-completed
lesson (or at minimum, the specific day or days being formatted), supplied in full, not a topic, Module, or Band
on its own. In practice, a generation request names the Unit (or "the Lesson Introduction Page") and supplies the
completed lesson directly ("format Unit 3 (Day 3) of this lesson for print," with the lesson text attached or
pasted in). If no completed lesson is provided, or the requested day's content is not present in what was
supplied, stop and ask before generating anything.

This prompt produces the **student version only**. A teacher-facing formatted version (with answer keys, timing
notes, and facilitation cues layered back in) is a plausible future companion but is out of scope here; do not
attempt to serve both audiences from one output.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs before generating

- Which Unit is being formatted (Unit 1-8, or a lettered continuation like Unit 4a/4b), or that the request is for
  the Lesson Introduction Page instead.
- The source lesson's content for that specific day in full: the grammar mini-lesson(s) with their rule and
  examples, the controlled-practice activities, the Leveled Mentor Ladder (on the day it appears), the prewriting
  materials, the drafting task and its Section 0.2 target for each task Level, the self-edit checklist, the Peer
  Editing Form, and the Closing Transfer Check (Day 8 only). Pull all content directly from the completed lesson;
  do not invent new activities, examples, or checklist items, and do not drop any task Level present in the
  source lesson's band.
- Module and Band, for internal reference only (they do not appear as labels in the student-facing output; see
  2.4).
- The Skill Spotlight's objective wording, needed for the Lesson Introduction Page and for every Unit's objective
  statement (2.2), even units generated well after Day 1.
- The Scenario setup and any teacher-provided reference material used across multiple days (a picture, a Word
  Bank, a comparison table), needed for the Lesson Introduction Page and for any Unit whose day actually uses it.

### 0.2 What this prompt does NOT change

The underlying content, task Levels, and pedagogical structure are fixed by the source lesson. This prompt is a
presentation and translation layer, not a content-generation step: it does not add, cut, or reweight activities or
checklist items, does not change which task Levels exist, and does not alter the Mentor Ladder or drafting targets.
Where the source lesson's structure genuinely does not translate to a clean print layout (see Section 1), this
prompt may restructure _presentation_ (for example, merging two adjacent controlled-practice activities into one
shared exercise with lettered sub-items) without cutting content or changing the difficulty of any task Level's
work.

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

Every generated student handout must pass this translation before anything else. None of the terms in the left
column may appear in the student-facing document. Replace each with the plain-language instruction that tells
the student what to actually do, silently, without narrating the pedagogy behind it.

| Teacher-facing term (lesson prompt)                                                                          | Student-facing translation                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Focus A / Focus B (Grammar Focus)                                                                            | No "Focus A/B" labels shown. Each grammar mini-lesson gets a plain topic name in the section heading (e.g. "Comparing Things," "Joining Sentences") instead.                        |
| Scenario                                                                                                     | Not named as a "Scenario." Present the writing topic and stimulus directly (the picture, the prompt) with no framing language about why it was chosen.                              |
| Task Level / Level (numeric); frame-regime / composition-regime                                              | A star rating (★ to ★★★★, more stars = more challenging), with no numeric Level shown, no regime language, and no tier name ("Foundation," "Extension," etc.).                      |
| Leveled Mentor Ladder / Mentor Text                                                                             | Presented as worked examples labeled only by star count ("★★★ Example," not "Level 4 Mentor Text"), with no reference to a "ladder" or "set."                                       |
| Skill Spotlight                                                                                              | A plain can-do objective statement near the start of the packet (see 2.2), not narrated as "today we are practicing X."                                                             |
| Closing Transfer Check                                                                                       | A closing activity instruction (see 2.8), without naming it as a "check" or referencing assessment/evidence language.                                                               |
| Required feature                                                                                             | Not named as a "required feature." State it as a plain instruction inside the task itself (e.g. "Include one comparison and one reason," not "this task's required feature is..."). |
| Board-dependent moment                                                                                       | Not shown to students at all; this is a teacher-facing classroom-management instruction with no student-facing artifact.                                                            |
| Foundation Support                                                                                           | Handled per 2.9, not labeled or called out as a separate tier anywhere a student can see it.                                                                                        |
| Self-edit checklist / Peer Editing Form                                                                      | Presented under plain section headings ("Check Your Own Work," "Trade and Check") with the actual checklist/question items, never referencing Section numbers or "regime."          |
| Editing a paragraph (controlled-practice type)                                                               | A plain instruction stating how many errors to find, no reference to "controlled practice" or activity-type jargon.                                                                 |
| Confusable-pair drill                                                                                        | A plain forced-choice exercise with its own instruction line; do not label it "confusable pair" anywhere.                                                                           |
| Self-revision mechanism (strikethrough/insertion, 0.4a)                                                      | A plain instruction to cross out (not erase) what changed and write the new version next to it; no reference to "self-revision evidence" or Section 0.4a.                           |
| Essay Focus A/B (essay structure, hook types, thesis construction, topic sentences, outlining) (new in v1.1) | Its own plain-titled callout box (e.g. "How an Essay Is Built," "Writing Your Thesis"), formatted and positioned per 2.11 below - not labeled "Essay Focus" anywhere.               |

If a source lesson uses a term or mechanism not listed above, apply the same principle: state the plain action the
student takes, never the pedagogical name for it.

## SECTION 2: DOCUMENT STRUCTURE

### 2.0 The Lesson Introduction Page

Generate this once per lesson, as its own file, meant to be handed out before Unit 1 (a syllabus-style cover page,
not something reprinted alongside every unit). It contains, in this order, and nothing else:

- The title (2.2's title, same wording used on every Unit).
- The objective statement (2.2), stated once here in full.
- The Scenario, presented directly (the picture, the object, the prompt) exactly as 2.2/Section 1 already require
  for any Scenario content: no framing language about why it was chosen.
- Any teacher-provided reference material genuinely shared across multiple days (a Word Bank, a comparison table,
  and similar) - the canonical copy lives here; individual Units still reprint it themselves wherever that unit's
  own day actually uses it (2.0a), so a Unit handed out on its own stays self-contained, but this page is where a
  teacher sees the whole set at once.
- A short roadmap: one line per Unit (Unit 1 through Unit 8, in order) naming in plain language what that day
  covers - not a detailed activity list, just enough for a teacher or student to see the shape of the whole
  lesson at a glance (for example: "Unit 3: Learn to join two sentences into one."). Do not use teacher-facing
  phase names or Day numbers in this roadmap; describe each unit the same way its own Unit heading does.
  No stars, no tasks, no answer space, and no callout boxes appear on this page - it is orientation only, not
  content the student works through.

### 2.0a One file per Unit, not per-task-Level handouts

Each Unit (one source lesson day) is its own single, self-contained file covering the whole class, not separate
handouts per task Level. Every task Level present in the source lesson's band, for that day, appears inside the
one Unit file as a self-selected star-rated option, not as a separately distributed sheet. Reprint, inside the
Unit file itself, whatever shared reference material (Word Bank, comparison table, picture) that day's own
activities actually need, even though the canonical copy also lives on the Lesson Introduction Page - a teacher
who prints only Unit 4 should not need Unit 1 or the intro page in hand to run it.

### 2.1 Continuation units (Unit Na / Unit Nb)

Apply this only where a single day's content is genuinely too long for one clean page-set, or where a teacher
says they are splitting one lesson day across two class meetings. Split that day's content between two files,
Unit Na and Unit Nb, letting the natural phase boundary in the source lesson (e.g. after the grammar mini-lesson
and before controlled practice) decide where the split falls. Both halves still belong to that one source day;
never let Unit Nb content bleed into the next day's material or vice versa. Label each half's heading "Unit Na:
Title (continued)" for the second half (see 2.3). Most days do not need this; do not split by default.

### 2.2 Objective statement, stated in plain language, near the top, every unit

Immediately after the title, before any warm-up content, state the lesson's actual learning objective as a
can-do statement, not narrated as "today we're practicing..." Pull the wording from the source lesson's Skill
Spotlight and the Writing-modality objective it was built from, but phrase it as something the student can
already picture doing (for example: "describe something familiar by comparing it to something else and giving a
real reason for the comparison"), not as a process narration. Restate this same objective at the top of every
unit's file, not only Unit 1's or the Lesson Introduction Page's, since a teacher printing Unit 6 will not
necessarily have the intro page or an earlier unit in hand.

### 2.3 One heading per Unit, numbered by day

Give each Unit file a single heading, numbering it by its position in the 8-day cycle (Unit 1 for Day 1, Unit 2
for Day 2, and so on through Unit 8 for Day 8), never using the words "Day 1" through "Day 8" anywhere in the
student-facing text. Fold the label directly into the heading text itself, followed by a short plain-language
title for that day's actual content (e.g., "Unit 1: Comparing Things," "Unit 5: Write Your Description"),
left-aligned. Where a continuation applies (2.1), the heading reads "Unit Na: Title" for the first half and
"Unit Na: Title (continued)" - keep it "Na," not renumbering as its own Unit - for the second half. Task/exercise
lettering starts fresh at Task A within each Unit file (each file is now fully self-contained, covering exactly
one source day), rather than continuing across files.

### 2.4 Modality label, top-right; no other kicker lines or metadata fields

Every file's single masthead - the Lesson Introduction Page and every Unit file alike, since each is handed out
and handled as its own standalone packet - carries a `.masthead-tag` span reading exactly `Writing`, alongside
the `h1`, per `shared/Student_Packet_Style_Guide.md` §B. Nothing else: no Level/Band, no "Class" or "Packet"
suffix.

Beyond that one tag, do not include: a Name/Date field, a subject/module/band kicker line under the title (e.g.
"Writing Packet · Describing"), a subtitle line under any heading, or a footer note at the bottom of the
document. The title, its `.masthead-tag`, and the objective statement are the only material above the first
section, on both the Lesson Introduction Page and every Unit.

### 2.5 Section and task labeling

- Use a consistent section-title style for each named block appropriate to that unit's day: for a grammar-focused
  day, something like Grammar, Try It; for a drafting day, Get Ready to Write, Write It, Share a Line; for a
  closing day, Trade and Check, Fix It Up, Wrap It Up.
- Within a unit, label individual exercises with letters (Task A, Task B, Task C...) so the teacher can
  reference them verbally in class. Use "Task," not "Exercise" or "Activity."
- Where the source lesson's controlled-practice activities would otherwise split into two near-identical blocks
  covering the same grammar point, merge them into one combined Task with sequential numbered items rather
  than two separate task labels, if doing so does not drop any content.
- **Task label line (revised in v1.1): the Task label sits alone on its own line, never sharing a line with a
  star rating.** Either leave it bare ("Task A.") when the differentiated activities beneath it are
  self-explanatory, or follow it with one short, genuinely informative clause tied to that task's actual content
  (e.g. "Task B. Read the essay below, then answer the question."). Never use a generic placeholder like
  "Complete the activity for your level" - it tells the student nothing they don't already know from seeing
  star-rated blocks beneath the label, and reads as filler. A star rating belongs only on the instruction line of
  the individual activity block it differentiates, never on the Task-label line itself, even when a task serves
  only one star level.
- **Ascending star order within a task (new in v1.1):** where a task contains more than one star-rated activity
  block, the blocks must appear in ascending order (★ first, then ★★, and so on up to ★★★★), regardless of the
  order the source lesson happens to list them in.

### 2.6 Star ratings for differentiated tasks

Where the source lesson's task ladder assigns different task Levels, represent difficulty with a star rating
instead of a Level number or regime name: the lowest task Level in the band gets ★, and each step up the band's
Task Levels row adds one star, to a maximum of ★★★★ for the highest task Level. Show only filled stars (★, ★★,
★★★, ★★★★), never a filled-vs-empty display out of a fixed total. Do not label the tiers ("beginner," "solid
challenge," "advanced") and do not frame the choice as "choose your own adventure" or "pick your challenge" -
state only the section heading (e.g. "Write It") and let the star count speak for itself; which star rating a
student works at is decided live by the teacher, not narrated on the page. Where a frame-regime task Level's
work is fundamentally a fill-in-the-blank and a composition-regime task Level's work is an original paragraph,
present each star rating's actual instruction as written (a blank frame for ★/★★, a blank writing space for
★★★/★★★★); do not paper over the difference in kind with identical instruction wording across all four stars.

### 2.7 The Leveled Mentor Ladder as star-labeled worked examples

**Include this section only on the unit whose day presents it, and only where it adds something that unit's own
tasks do not already model (revised in v1.1).** If the same unit's tasks already embed and work with a shared
model text at multiple star levels (for example, an essay-analysis task that has students read and question a
shared model essay), a second, separate showcase of finished writing at every level can read as redundant bulk
rather than a genuine spotlight, and should be omitted. Where it does add real value, present the source lesson's
Mentor Ladder as a short run of worked examples, one per task Level, labeled only by star count and shown in
ascending order (★ example, then ★★, then ★★★, then ★★★★). Do not use the words "Mentor," "Level," or "ladder"
anywhere near them; a plain heading such as "See How It's Done" is sufficient, ideally with one lead-in sentence
saying why it's there (e.g. "you won't draft your own until later this unit - these are here so you can see what
you're working toward"), so it reads as purposeful rather than a random dump of finished writing. Students are
not instructed to read only their own star rating's example; presenting the whole ascending run is the point
(see the source lesson's own rationale for this), so include all of them without a note explaining why. Keep the
section proportionate: where a higher Level's Mentor Essay runs to several full paragraphs, an opening excerpt
plus one paragraph containing any single genuinely load-bearing moment (e.g. a self-revision demonstration
called out elsewhere in the source lesson) is enough, with a short bracketed note bridging to the ending, rather
than reproducing the entire essay. A later unit that wants to point back to an earlier unit's worked examples
(rather than reprint them) may do so with a brief plain-language pointer (e.g. "look back at the examples in
Unit 1") instead of reproducing the set again.

### 2.8 Closing activity (Unit 8 only)

Only Unit 8 (the final source lesson day) includes a closing section. Translate the source lesson's Closing
Transfer Check into a plain closing instruction (section heading: "Wrap It Up" or equivalent) that has the
student apply the exact named objective to something new, stated as directly as possible (what to pick, what to
do with it), without describing it as a check, an assessment, or referencing "what you practiced this week." Do
not add stage directions like "say it out loud" or "your teacher may call on a few pairs to share" unless the
source lesson's mechanism specifically requires a public share step the page must instruct the student to
perform; default to omitting narration of what the teacher will do next.

### 2.9 Trade and Check (Peer Editing) and Check Your Own Work (self-edit)

Translate the self-edit checklist into a plain "Check Your Own Work" list the student runs against their own
draft: short, direct items pulled from the source lesson's checklist, phrased as things to look for, not
Section-numbered rules. Translate the Peer Editing Form into a "Trade and Check" section: partner instructions,
then the specific questions from the source lesson's form, then space for one compliment and one suggestion.
Where the source lesson gives frame-regime task Levels an oral equivalent instead of a written checklist/form,
print that as its own short instruction line rather than omitting those task Levels from the page.

### 2.10 Grammar box translation

Present each grammar mini-lesson under the heading "Grammar," followed by a colon and the plain-language name of
the point being taught (e.g. "Grammar: Comparatives + Because," "Grammar: Simple and Compound Sentences"), with
the rule stated in one or two short sentences and 2-3 example sentences beneath it, formatted the same way the
source lesson's own grammar box is (a short table or a simple list), stripped of any "Focus A/Focus B" labeling
per Section 1.

### 2.11 Callout boxes are reserved for genuine callouts

Bordered call-out containers are reserved for content that is genuinely a spotlight moment: the "Grammar"
grammar box, any essay-structure teaching box translated from Essay Focus A/B content (new in v1.1: e.g. "How an
Essay Is Built," "Writing Your Thesis"), and, where included per 2.7, the "See How It's Done" worked-example set.
Do not put a border around ordinary content like a word bank, a plain instruction paragraph, or a checklist -
those render as plain text or a simple unbordered list.

**Two rules for every teaching-content callout (Grammar and essay-structure boxes; new in v1.1):**

- **No star tag on the callout title, ever.** This content is delivered to the whole room in one sitting (see the
  lesson prompt's "Grammar is a teaching moment, not a practice moment" principle), not to one star tier, so a
  star next to its title misrepresents it as tiered content. Stars belong only on the individual task activities
  that follow.
- **Position it immediately before the task(s) that require the concept it teaches, never after.** Before placing
  any task, confirm every concept that task's instructions assume (a rule, a distinction like direct/indirect, a
  structural pattern) has already been taught by a callout box appearing earlier in the document. If a source
  lesson's own day-by-day order would place the teaching content after a task that needs it, that is a sequencing
  problem in the source lesson itself (see the lesson generation prompt's own "teaching content must precede
  practice" principle) - flag it rather than silently reordering the document to paper over it, unless the
  reorder is confirmed to still match the source lesson's actual teaching sequence.

### 2.12 Answer and writing space

Add blank writing lines wherever a task demands a written answer, sized to the expected answer length: a single
short inline line (e.g. `.ans-line-sm`, roughly 300px, inline after the item) for a one-word blank or a short
phrase; several full-width lines (e.g. `.ans-line`, roughly 20-24px tall each) sized to the task Level's own
Section 0.2 sentence-count target for a drafting task. Do not add answer space to items with no written-response
component (a purely discuss-aloud prompt, or a fill-in-the-blank item that is itself the answer space).

### 2.13 Redundant rules and dividers

Do not add a horizontal rule between adjacent sections, headings, or blocks by default. Only include one where
it is load-bearing for readability (for example, separating a dense block of running text from a clearly distinct
block immediately below it with no other visual separation, such as a heading or box border). When in doubt,
omit it.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

**Moved to a shared, cross-modality doc:** paste `shared/Student_Packet_Style_Guide.md` alongside
this prompt when generating. It holds the universal format constraints (single self-contained
file, black-and-white, no em-dashes, print-safe layout), the base stylesheet (including the
`.ans-line`/`.ans-line-sm` classes 2.12 above already assumes), and the HTML markup conventions.
Reuse the base stylesheet unmodified; add a new class only for a structural element genuinely not
covered there (e.g. the essay-structure teaching boxes in 2.11), following the same rule-formatting
conventions (`shared/Student_Packet_Style_Guide.md` §C). Before this note, this section had no
actual CSS or stylesheet reference at all - a gap masked only by the fact that no Academic Writing
packet has been generated yet (see `Changelog.md`).

## SECTION 4: WORKFLOW

### 4.1 HTML preview first, iterate before finalizing

Generate the student packet as an HTML file and deliver it for review before treating it as final. Layout and
formatting decisions in this program are refined through direct visual review, not specified in enough advance
detail to get exactly right on the first pass. Apply feedback as scoped, targeted edits rather than regenerating
the whole document each round.

### 4.2 When this prompt's guidance runs out

Where a source lesson includes a structural element not explicitly covered above, apply Section 1's general
principle (plain instruction over jargon) and this section's general defaults (no color, no unnecessary rules,
callout boxes reserved for genuine spotlights, answer space matched to expected answer length) rather than
inventing new decorative structure.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

**On the Lesson Introduction Page specifically (v1.2):**

- Does it carry the title, the objective, the Scenario, any cross-day reference material, and a one-line-per-unit
  roadmap (Unit 1 through Unit 8), in that order, and nothing else - no stars, no tasks, no answer space, no
  callout boxes?
- Does the roadmap describe each unit the same plain way its own Unit heading does, with no teacher-facing phase
  names and no "Day 1" through "Day 8"?
  **On every Unit file:**
- Does every term in Section 1's left column appear nowhere in the student-facing text?
- Is the file a single self-contained document for the one requested Unit (one source lesson day, or one half of
  a lettered continuation), covering every task Level in the source lesson's band for that day, not separate
  per-task-Level handouts?
- Does the objective appear as a plain can-do statement near the top of this unit's file specifically (not
  assumed to have been seen already, whether or not the Lesson Introduction Page exists), before any task content?
- Is the unit presented under one heading numbered by its position in the 8-day cycle (Unit 1 through Unit 8, or
  "Unit Na" / "Unit Na ... (continued)" for a lettered continuation), never using "Day 1" through "Day 8," folded
  into the heading text itself alongside a short plain-language title for that day's content?
- Does task/exercise lettering start fresh at Task A within this unit file, rather than continuing from another
  unit's lettering?
- Does this unit reprint, for itself, whatever shared reference material (Word Bank, comparison table, picture)
  its own day's activities actually need, rather than assuming the Lesson Introduction Page or an earlier unit is
  also in hand?
- Does this file's masthead carry a `.masthead-tag` reading exactly "Writing" (no Level/Band, no "Class" or
  "Packet" suffix)? Beyond that tag, are there no Name/Date fields, no module/band kicker line, no subtitle
  lines, and no footer note?
- Are all exercises labeled with letters ("Task A," "Task B"...) rather than "Exercise" or "Activity," with labels
  inline with their instruction text?
- Do differentiated tasks show only filled stars (★ up to ★★★★), with no numeric Level, no regime language, no
  tier name, and no "choose your own adventure" framing?
- If this unit's day includes the Leveled Mentor Ladder, are the worked examples shown in ascending star order with
  no "Mentor," "Level," or "ladder" language anywhere near them?
- Is the closing activity ("Wrap It Up") present only on Unit 8, and does it connect back to the same objective
  stated at the top?
- Are the self-edit and peer-editing sections presented as "Check Your Own Work" and "Trade and Check," with
  no Section-number references and no jargon like "self-revision evidence"?
- Are callout boxes reserved for genuine spotlights ("Grammar," any essay-structure teaching box, and "See How
  It's Done" where included) and not used for ordinary content like word banks or checklists?
- Does every Task label sit alone on its own line, never sharing a line with a star rating, and is it either bare
  or followed by one short clause that adds real information (never a generic "complete the activity for your
  level" placeholder)? (v1.1)
- Within each task, do the star-rated activity blocks appear in ascending order (★ before ★★ before ★★★ before
  ★★★★)? (v1.1)
- Does every teaching-content callout (Grammar box, and any essay-structure box) appear before every task that
  depends on the concept it teaches, with no star tag on the callout's own title? (v1.1)
- If this unit includes "See How It's Done," does it add something this unit's own tasks do not already model,
  rather than being included by default? (v1.1)
- Does every item requiring a written answer have appropriately sized writing space, sized to the task Level's
  own target where relevant, and no writing space where none is needed?
- Has every decorative, non-load-bearing horizontal rule been removed?
- Is the whole document black-and-white only, with no color-dependent meaning?
- Is the document free of em-dashes?
- Is the output a single self-contained HTML file with no external resource dependencies besides the print
  trigger?
