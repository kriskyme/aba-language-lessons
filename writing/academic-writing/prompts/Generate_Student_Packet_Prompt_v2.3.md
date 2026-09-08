# Academic Writing Student Print Formatting Prompt (v2.2)

Companion to the Academic Writing Lesson Generation Prompt (v4). Takes one completed Academic Writing lesson (a
2-day cycle, one of 4 in a Set) and produces one print-ready, black-and-white student handout for it: a single
self-contained HTML document covering both of that lesson's days. Every piece of teacher-facing pedagogical
language is translated into plain instructions a student (or a parent glancing at the page) can act on without
decoding jargon like "Focus A," "the Leveled Mentor Ladder," "task Level," or "board-dependent moment."

**Current version: v2.2.** For the full dated version history and the reasoning behind each change, see
`Changelog.md`. (v2 adopts Passage Reading's one-file, two-masthead-section packet shape - see
`shared/Program_Conventions.md` §C and `Changelog.md`'s 2026-09-08 entry, matching the same day this lesson type's
generation prompt was restructured from one 8-day document into 4 separate 2-day lessons per Set. The "Lesson
Introduction Page" concept from v1.2-v1.6 is retired: a 2-day lesson is short enough not to need a roadmap page,
the same reason Reading's own packets have never had one.)

**One file per lesson, two masthead sections, matching Reading exactly:** each of a Set's 4 lessons gets its own
single HTML packet covering both of that lesson's days, laid out as two masthead sections in one document -
`.masthead` for Day 1, `.masthead.masthead-later` for Day 2 - headed "Unit `{N}A`: `{Title}`" and "Unit `{N}B`:
`{Title}`" (same title both halves, per `shared/Student_Packet_Style_Guide.md` §B; `N` is this lesson's position
within its Set, 1-4, not its global Lesson #). File name: `{Topic}_{Band}_L{N}_Packet.html`, in
`Set_{S}/Lesson_{N}_{Topic}/`, exactly Reading's own naming convention.

**Self-containment across a shared Scenario:** because all 4 lessons in a Set share one Scenario
(`shared/Program_Conventions.md` §C), each lesson's packet must still stand alone - a teacher who prints only
Lesson 3's packet should not need Lesson 1's or 2's packet in hand. Reprint whatever shared Scenario reference
material (a comparison table, a word bank, a picture) that lesson's own content actually needs, the same
self-containment principle Reading's own multi-lesson Sets already follow for anything a later lesson's
activities reuse.

Use this prompt only after the source lesson's content already exists. Do not use it to generate lesson content,
and do not use the lesson prompt to produce a student handout: the input is always an already-completed lesson,
supplied in full, not a topic, Module, or Band on its own. In practice, a generation request names the lesson
(by its Set position or global Lesson #) and supplies the completed lesson directly. If no completed lesson is
provided, or its content is not present in what was supplied, stop and ask before generating anything.

This prompt produces the **student version only**. A teacher-facing formatted version (with answer keys, timing
notes, and facilitation cues layered back in) is a plausible future companion but is out of scope here; do not
attempt to serve both audiences from one output.

## SECTION 0: SCOPE AND INPUTS

### 0.1 Required inputs before generating

- Which lesson is being formatted: its Set position (1-4) and global Lesson # (`Generate_Lesson_Prompt_v4.md`'s
  "The Four-Lesson Set" table).
- The source lesson's content for both of its days in full: the grammar mini-lesson(s) with their rule and
  examples, the controlled-practice activities, the Leveled Mentor Ladder (on the day it appears), the prewriting
  materials, the drafting task and its Section 0.2 target for each task Level, the self-edit checklist, the Peer
  Editing Form, and the Closing Transfer Check (Lesson 4, Day 2 only). Pull all content directly from the
  completed lesson; do not invent new activities, examples, or checklist items, and do not drop any task Level
  present in the source lesson's band.
- Module and Band, for internal reference only (they do not appear as labels in the student-facing output; see
  2.4).
- The Skill Spotlight's objective wording, needed for this lesson's objective statement (2.2) on both of its
  days, even for Lesson 3 or 4, generated well after Lesson 1.
- The Set's shared Scenario setup and any teacher-provided reference material this lesson's own days actually use
  (a picture, a Word Bank, a comparison table) - see 2.0a on reprinting it so this lesson's packet stays
  self-contained even though the Scenario itself was established back in Lesson 1.

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

### 2.0a One file per lesson, two masthead sections, not per-task-Level handouts

Each lesson (2 source days) is its own single, self-contained file covering the whole class, not separate
handouts per task Level and not separate files per day. Every task Level present in the source lesson's band
appears inside the one file as a self-selected star-rated option, not as a separately distributed sheet. Reprint,
inside this lesson's own file, whatever shared Scenario reference material (Word Bank, comparison table, picture)
either of its two days' activities actually need - a teacher who prints only Lesson 3 should not need Lesson 1's
or 2's packet in hand to run it, even though the Scenario itself was only established once, back in Lesson 1
(0.1).

### 2.1 Two masthead sections, Day 1 and Day 2, in one file

Every lesson's packet is a single HTML document with two masthead sections in sequence, matching
`shared/Student_Packet_Style_Guide.md` §B's `.masthead` / `.masthead.masthead-later` pattern exactly the way
Passage Reading's own 2-day packets already do: the first masthead (with its `.masthead-meta` block, see 2.4)
covers Day 1's content, the second (`masthead-later`, no meta block) covers Day 2's, both under the same heading
text (2.3). Nothing about a lesson's content is split across two files.

### 2.2 Objective statement, stated in plain language, near the top of both masthead sections

Immediately after each masthead's heading, before any warm-up content, state the lesson's actual learning
objective as a can-do statement, not narrated as "today we're practicing..." Pull the wording from the source
lesson's Skill Spotlight and the Writing-modality objective it was built from, but phrase it as something the
student can already picture doing (for example: "describe something familiar by comparing it to something else
and giving a real reason for the comparison"), not as a process narration. Prefix the sentence with a bold
`Objective:` label per `shared/Student_Packet_Style_Guide.md`'s `.objective`/`.objective strong` rule
(`<p class="objective"><strong>Objective:</strong> describe...</p>`) — every modality's packets carry this label;
omitting it is a defect, not a stylistic choice. Restate this same objective under both the Day 1 and Day 2
masthead sections, since a teacher handing out only this file's Day 2 half in a second class session will not
necessarily have re-read Day 1's.

### 2.3 One heading text, two lettered sections, numbered by Set position

Give the lesson's two masthead sections the same heading text, numbered by the lesson's **position within its
Set** (1-4, not its global Lesson #) and lettered by day: "Unit `{N}A`: `{Title}`" for Day 1, "Unit `{N}B`:
`{Title}`" for Day 2 (e.g., "Unit 1A: Comparing Things" / "Unit 1B: Comparing Things"), never using the words
"Day 1"/"Day 2" anywhere in the student-facing text. Task/exercise lettering starts fresh at Task A within each
lettered section (A and B each cover one source day and should read as self-contained within that day), rather
than continuing across the A/B boundary.

### 2.4 Modality/Band/Version stack, top-right, on the opening masthead only; no other kicker lines or metadata fields

Only the file's opening masthead (Unit `{N}A`, Day 1 - never the later `masthead-later` Unit `{N}B` heading)
carries a `.masthead-meta` block, alongside the `h1`, per `shared/Student_Packet_Style_Guide.md` §B: two stacked
`.masthead-tag` lines, the first reading exactly `Writing`, the second combining this lesson's Band and its
version code as one string (`<Band> S<Set>.<Lesson>.<Iteration>` per `shared/Program_Conventions.md` §G - here
`<Lesson>` is this lesson's own **global** Lesson #, not its 1-4 Set position). Nothing else on that stack: no
"Class" or "Packet" suffix.

Beyond that one block, do not include: a Name/Date field, a subject/module kicker line under the title (e.g.
"Writing Packet · Describing"), a subtitle line under either heading, or a footer note at the bottom of the
document. The title, its `.masthead-meta` block (opening masthead only), and the objective statement (both
mastheads) are the only material above each section's own first content block.

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

**One star rating per lettered Task, always (new in v2.2), and letters advance one per Task, never reused.** A
lettered Task (`Task A`, `Task B`...) never carries more than one `<span class="stars">` tag - where the source
lesson's task ladder puts two task Levels under one shared activity, split it into two consecutive Task letters
instead (the lower star count first), even when the two tiers' instructions are otherwise identical (repeat the
instruction text; where it has a tier-specific clause, such as a differing word-count target, split the clause
along with the letter, keeping each half's own single star tag). The same rule also rules out the mirror mistake:
several single-star task-blocks in a row (e.g. one activity per task Level, four blocks total) must NOT all reuse
`Task A` - each gets its own advancing letter (A, B, C, D), the same as if they had been one combined task that
got split. Reletter every subsequent Task within that same Day so the sequence stays continuous with no gaps or
repeats (Task A, B, C, D, E...). Do not reorder a Day's existing sequence of
activities to force one global ascending run by star count across the whole Day - a Day's pedagogical sequence
(for example, a lighter task placed deliberately next to a heavier one on the same concept, as a receptive bridge)
stays exactly where it is; only the letters change, growing longer as splits are inserted. This rule governs
lettered Tasks specifically - it does not apply to unlettered content, such as a Check Your Own Work / Trade and
Check item (2.9) that genuinely belongs to two adjacent tiers at once (e.g. both tiers wrote a full paragraph and
share the identical self-check item): there, one item combining two star tags together is fine, since there is no
letter implying it is a single, indivisible task.

### 2.7 The Leveled Mentor Ladder as star-labeled worked examples

**Include this section only on the lettered section (Unit `{N}A` or `{N}B`) whose day presents it, and only where
it adds something that section's own tasks do not already model.** If the same section's tasks already embed and
work with a shared model text at multiple star levels (for example, an essay-analysis task that has students read
and question a shared model essay), a second, separate showcase of finished writing at every level can read as
redundant bulk rather than a genuine spotlight, and should be omitted. Where it does add real value, present the
source lesson's Mentor Ladder as a short run of worked examples, one per task Level, labeled only by star count
and shown in ascending order (★ example, then ★★, then ★★★, then ★★★★). Do not use the words "Mentor," "Level," or
"ladder" anywhere near them; a plain heading such as "See How It's Done" is sufficient, ideally with one lead-in
sentence saying why it's there (e.g. "you won't draft your own until later this lesson - these are here so you
can see what you're working toward"), so it reads as purposeful rather than a random dump of finished writing.
Students are not instructed to read only their own star rating's example; presenting the whole ascending run is
the point (see the source lesson's own rationale for this), so include all of them without a note explaining why.
Keep the section proportionate: where a higher Level's Mentor Essay runs to several full paragraphs, an opening
excerpt plus one paragraph containing any single genuinely load-bearing moment (e.g. a self-revision
demonstration called out elsewhere in the source lesson) is enough, with a short bracketed note bridging to the
ending, rather than reproducing the entire essay. A later lesson that wants to point back to an earlier lesson's
worked examples (rather than reprint them) may do so with a brief plain-language pointer (e.g. "look back at the
examples from earlier this week") instead of reproducing the set again.

### 2.8 Closing activity (Lesson 4's Day 2 / Unit 4B only)

Only the Set's fourth lesson, Day 2 (Unit `4B` - the final source lesson day of the whole Set) includes a closing
section. Translate the source lesson's Closing Transfer Check into a plain closing instruction (section heading:
"Wrap It Up" or equivalent) that has the student apply the exact named objective to something new, stated as
directly as possible (what to pick, what to do with it), without describing it as a check, an assessment, or
referencing "what you practiced this week." Do not add stage directions like "say it out loud" or "your teacher
may call on a few pairs to share" unless the source lesson's mechanism specifically requires a public share step
the page must instruct the student to perform; default to omitting narration of what the teacher will do next.

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

- **No star tag anywhere inside a teaching-content callout, title or body, ever.** This content is delivered to
  the whole room in one sitting (see the lesson prompt's "Grammar is a teaching moment, not a practice moment"
  principle), not to one star tier, so a star anywhere in it - on the title or on a line inside it - misrepresents
  part of the callout as skippable for anyone not "in" that tier, when every student needs to hear all of it.
  Stars belong only on the individual task activities that follow the callout, never inside it. Where the source
  lesson's grammar or essay-structure content genuinely does vary by task Level (e.g. which frame a student uses,
  or a rule that only matters once sentences reach a certain complexity), state both/all variants as plain
  sentences or bullet points inside the callout, with no star tag and no "one-star/two-star/three-star" wording -
  which variant a given student actually applies is handled downstream, by the star-tagged practice tasks that
  follow, not by flagging it inside the shared teaching moment.
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

**On every lesson packet (one file, two masthead sections):**

- Does every term in Section 1's left column appear nowhere in the student-facing text?
- Is the file a single self-contained document covering both of this lesson's days, each lettered section (A/B)
  covering every task Level in the source lesson's band for that day, not separate per-task-Level handouts and
  not separate files per day?
- Does the objective appear as a plain can-do statement near the top of both the A and B sections, before any
  task content in either?
- Do both sections share one heading text, numbered by this lesson's Set position (1-4, not its global Lesson #)
  and lettered by day ("Unit `{N}A`: `{Title}`" / "Unit `{N}B`: `{Title}`"), never using the words "Day 1"/"Day 2"
  anywhere in the student-facing text?
- Does task/exercise lettering start fresh at Task A within each lettered section, rather than continuing across
  the A/B boundary?
- Does this lesson's packet reprint, for itself, whatever shared Scenario reference material (Word Bank,
  comparison table, picture) either of its two days' activities actually need, rather than assuming an earlier
  lesson's packet is also in hand?
- Does only the opening masthead (Unit `{N}A`) carry a `.masthead-meta` block with two stacked tags - "Writing,"
  then this lesson's Band and its `S<Set>.<Lesson>.<Iteration>` version code combined as one string (`<Lesson>`
  its global number) - with the later `masthead-later` heading (Unit `{N}B`) carrying no meta block, per
  `shared/Student_Packet_Style_Guide.md` §B? Beyond that one block, are there no Name/Date fields, no
  subject/module kicker line, no subtitle lines, and no footer note?
- Are all exercises labeled with letters ("Task A," "Task B"...) rather than "Exercise" or "Activity," with labels
  inline with their instruction text?
- Do differentiated tasks show only filled stars (★ up to ★★★★), with no numeric Level, no regime language, no
  tier name, and no "choose your own adventure" framing?
- If this lesson's Leveled Mentor Ladder content is included, are the worked examples shown in ascending star
  order with no "Mentor," "Level," or "ladder" language anywhere near them, and only where it adds something the
  lesson's own tasks don't already model?
- Is the closing activity ("Wrap It Up") present only on the Set's Lesson 4, Unit 4B, and does it connect back to
  the same objective stated at the top?
- Are the self-edit and peer-editing sections presented as "Check Your Own Work" and "Trade and Check," with
  no Section-number references and no jargon like "self-revision evidence"?
- Are callout boxes reserved for genuine spotlights ("Grammar," any essay-structure teaching box, and "See How
  It's Done" where included) and not used for ordinary content like word banks or checklists?
- Does every Task label sit alone on its own line, never sharing a line with a star rating, and is it either bare
  or followed by one short clause that adds real information (never a generic "complete the activity for your
  level" placeholder)?
- Within each task, do the star-rated activity blocks appear in ascending order (★ before ★★ before ★★★ before
  ★★★★)?
- Does every teaching-content callout (Grammar box, and any essay-structure box) appear before every task that
  depends on the concept it teaches, with no star tag on the callout's own title?
- Does every item requiring a written answer have appropriately sized writing space, sized to the task Level's
  own target where relevant, and no writing space where none is needed?
- Has every decorative, non-load-bearing horizontal rule been removed?
- Is the whole document black-and-white only, with no color-dependent meaning?
- Is the document free of em-dashes?
- Is the output a single self-contained HTML file with no external resource dependencies besides the print
  trigger?
