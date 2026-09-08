# Passage Reading Assessment Student Print Formatting Prompt (v1.1)

Companion to the Assessment Generation Prompt (v4.1). Takes one completed Set assessment (four
Task-Level sections, each with its own Vocabulary & Idiom Mastery and Reading Comprehension
items) and produces a single, print-ready, black-and-white student handout: one self-contained
HTML document with every piece of teacher-facing language, and everything a student should never
see (source-lesson/Tests citation tags, CSV grounding quotes, item counts, the Scoring Guide's
point values and Not yet/Developing/Meets rubrics), removed. Mirrors the Student Print Formatting
Prompt (v1.7) closely - same translation principle, same star-rating system, same base
stylesheet - adapted for an assessment's shape (four self-contained Task-Level sections, no taught
Unit A/B split) rather than a taught lesson's. Also mirrors Listening/Speaking's
`Generate_Assessment_Student_Packet_Prompt_v1.md` and Writing's
`Generate_Assessment_Student_Packet_Prompt_v2.md`, this program's two existing assessment-packet
prompts.

Use this prompt only after an Assessment `.md` already exists in full (every Task Level present in
the source band). Do not use it to generate assessment content, invent new items, reweight
comprehension questions, or drop a Task Level present in the band. This produces the **student
version only**.

## SECTION 0: SCOPE AND INPUTS

Required: the completed Assessment `.md`, supplied in full - every Task Level's CSV grounding
quote, Vocabulary & Idiom Mastery items (one lesson-block per lesson), Reading Comprehension items
(each lesson's new passage, reprinted per Task Level, plus any cross-text synthesis item at the
highest Task Level), and the closing Scoring Guide. Pull all content directly from the completed
assessment; do not invent new vocabulary, passages, or items, and do not drop a Task Level present
in the source band.

**Never carry these into the student copy, under any heading or phrasing:** the `(Lesson N -
Tests: ...)` source-lesson/citation tag under every item, the CSV grounding quote's raw wording
(Section 1 translates it), item-count/scope metadata (the header block's Module/Band/Set/Task
Levels/item-count summary), any `(...see Scoring Guide.)` cross-reference, and the entire Scoring
Guide section (point tables and the Not yet/Developing/Meets rubrics for the comparison-and-reason,
extended-reasoning, and cross-text synthesis items). None of this is student-facing content - it is
the reason this is a separate prompt from the assessment itself rather than a formatting pass over
the same document.

**No self-check checklist substitute.** Unlike Listening/Speaking's Speaking Task cards (a
separately-submitted deliverable where a rubric-derived checklist gives real value before
submission), Reading's rubric-scored items are ordinary written comprehension questions answered on
the same page as everything else - consistent with how Passage Reading's own lesson packets never
show a rubric or a self-check list for an extended-response item, only answer space. Print these
items as plain numbered questions with answer space sized to what's asked (Section 2.6); do not
translate the rubric into any visible student-facing artifact.

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

None of the left column may appear in the student-facing document.

| Teacher-facing term | Student-facing translation |
| --- | --- |
| Task Level / Level (numeric) | A star rating (★ to ★★★★), shown as that page's running head - not a menu to choose from. An assessment is not student-choice the way a lesson's differentiated task block is; the teacher assigns each student one Task Level's pages. |
| CSV grounding quote (e.g. "...decoding both open-slot words... to identify the matching image") | A plain can-do objective statement near the top of that Task Level's pages, phrased the same way Section 2.2 of the Student Print Formatting Prompt (v1.7) phrases a lesson's objective - something the student can picture doing, not the CSV's internal wording. |
| `(Lesson N - Tests: ...)` citation tag | Not shown. Removed entirely (Section 0). |
| Item-count summary, "cumulative/full Set" scope framing | Not shown; a student does not need to know how many items exist or how the assessment was scoped before taking it. |
| `(...any reasonable, text-supported answer is credited - see Scoring Guide.)` | Not shown. Removed entirely; the question itself is already clear without a grading note. |
| Scoring Guide, point values, Not yet/Developing/Meets rubrics | Never shown, in table form or otherwise (Section 0). |
| "Cross-text synthesis" label | Not named as such; the item's own instruction already tells the student to compare both passages (Section 2.7). |
| Passage title reused across Task Levels ("new passage: ...") | Shown as a plain headline above the reprinted passage, the same treatment the lesson packet gives an anchor text's headline - "new passage" framing dropped. |

If the source assessment uses a term or structure not listed above, apply the same principle: state
the plain content or instruction, never the assessment-writer's internal label for it.

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One combined document, four self-contained Task-Level sections

Produce a single shared document, not four separate files, matching the source assessment's own
shape: one section per Task Level (2 through 5, or whichever Task Levels the source band uses),
each self-contained enough that a teacher can print or photocopy just one Task Level's pages,
because a class assigns different students different Task Levels. Give each Task Level's section
`page-break-before: always` (except the first) so selective printing produces clean single-Level
printouts, the same print-safe pattern the lesson packet's Section 3 already establishes.

### 2.2 Masthead: title once, star rating per section

Carry the assessment's plain title ("Module {M} Set {N} Assessment") as an `<h1>` inside a
`.masthead` div at the very top of the document, once - not repeated per Task Level. Do not add a
`.masthead-meta` tag stack here: unlike a single lesson (which has one Band and one
`<Module>.<Set>.<Lesson>.<Version>` version code), one assessment document spans every Task Level in a
Band at once, so there is no single per-lesson version code to display: This deliberately matches
Listening/Speaking's and Writing's existing assessment-packet prompts, neither of which carries a
`.masthead-meta` stack either.

Each Task Level's own section opens with a `.section-title`-style running head showing only that
Level's stars (e.g. `★★`, no "Task Level," no "lowest"/"highest" label) so a teacher distributing
one Level's pages can identify them at a glance.

Beyond the one opening `<h1>` and each section's star running head, do not include: a Name/Date
field, a module/band kicker line, a subtitle line, or a footer note.

### 2.3 Per-Level objective statement

Immediately after each Task Level's star running head, before any items, state that Level's CSV
grounding quote as a plain `.objective` paragraph (`<strong>Objective:</strong>` + a can-do
sentence), phrased the way the lesson packet's Section 2.2 phrases an objective - not the CSV's
literal wording.

### 2.4 Vocabulary & Idiom Mastery

Render as a `.section-title` ("Words & Phrases" or equivalent), then one block per lesson in
source order. Where the source item is a word-bank match-to-meaning or fill-in-the-blank set, use
the same `.wordbank` (dashed-rule) + `.fillblank`/`.qlist` pattern the lesson packet's Task B
already establishes - no new class needed; a matching item (word bank matched to lettered
meanings) is structurally the same "word bank plus fill in the blank" shape. Label each lesson's
block with a plain `.subgroup-label` naming only the passage/topic (drop the "Lesson N:" numbering
- that is a rotation-tracking label, not something the student needs). Where a Task Level has no
vocabulary item for one lesson (as Level 5 has none for Lesson 3), simply omit that block; do not
add a placeholder or note explaining the gap.

### 2.5 Reading Comprehension

For each lesson's block, print the plain passage headline (`.article .headline`, "new passage"
framing dropped per Section 1), the passage itself with its lettered paragraphs (`.para-letter`),
and then that lesson's comprehension items as a numbered `.qlist`, in source order. No annotation
key and no footnotes sidebar: an assessment passage is read once to answer fixed questions, not
marked up during an instructional reading phase the way a lesson's anchor text is (Section 2.10 of
the Student Print Formatting Prompt is a lesson-only feature). Reprint the full passage inside
every Task Level's own section that uses it, even though the text is identical across Levels - this
is what keeps each Task Level's pages genuinely self-contained for selective printing (2.1), the
same reason the source `.md` itself reprints it.

### 2.6 Answer space, sized to what's asked

Apply the same rule as the lesson packet's Section 2.13: a single short inline line
(`.ans-line-sm`) for a one-word or short-phrase answer or a quoted phrase; two or more full-width
lines (`.ans-line`) for a "write one sentence" or "in 2-3 sentences" answer. An item asking for a
paragraph letter or a fill-in-the-blank word gets only the inline `.blank`/`.ans-line-sm` space the
answer itself needs, not additional lines. The highest Task Level's cross-text synthesis item
("in 3-4 sentences, compare... and explain which change...") gets three to four `.ans-line`s to
match its longer expected answer, printed as the final numbered item in that Level's Reading
Comprehension section (after both passages it references have already appeared earlier in that same
section) - do not label it "Cross-text synthesis"; its own instruction sentence already tells the
student what to do (Section 1).

### 2.7 Circle-the-word and multiple-choice items

Print exactly as the source phrases them (e.g. "Circle the word that best shows..."), with the two
choices given inline, matching the lesson packet's compact multiple-choice formatting. Do not
append any grading note about which answers are credited (Section 0).

### 2.8 Callout boxes, redundant rules

Same defaults as the lesson packet's Sections 2.12 and 2.14: no bordered callout box for ordinary
content (a passage, a plain item list), word banks keep the dashed-rule exception, and no
decorative horizontal rule between adjacent sections unless it is load-bearing for readability.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Identical to the lesson packet's Section 3: paste `shared/Student_Packet_Style_Guide.md` alongside
this prompt when generating. It holds the universal format constraints (single self-contained file,
black-and-white, no em-dashes, print-safe layout), the base stylesheet, and the HTML markup
conventions. This prompt has no Reading-specific delta CSS of its own - every element an assessment
packet needs (`.masthead`, `.section-title`, `.objective`, `.subgroup-label`, `.wordbank`,
`.fillblank`, `.qlist`/`.num`/`.qbody`, `.ans-line`/`.ans-line-sm`, `.article`/`.para-letter`) is
already defined in the base stylesheet or already established by the Student Print Formatting
Prompt. The one addition beyond the base stylesheet is behavioral, not a new class: give each Task
Level's section `page-break-before: always` (2.1).

## SECTION 4: WORKFLOW

**Generation timing:** run this prompt immediately after an Assessment `.md` is complete, in the
same session/request - not as a separately-requested later step, the same same-session pairing rule
the Lesson Generation Prompt's third addendum established for lessons and their packets, and that
Listening/Speaking's own Assessment Student Packet Prompt applies to its modality. An assessment
request produces both files together: the `.md` first, then this prompt run against that finished
`.md` to produce the `.html`.

**The `.md` is the single source of truth; this prompt's output is always a regeneration, never a
standalone edited artifact.** If a review round asks for a change that affects what students
actually see as an item, passage, or instruction, apply the change to the source Assessment `.md`
first, then re-run this prompt to produce a fresh `.html`. The only edits safe to apply directly to
the `.html` are pure formatting/translation-layer fixes that don't change assessment content.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

- Does every left-column term from Section 1 appear nowhere in student-facing text?
- Is every `(Lesson N - Tests: ...)` tag, item-count/scope metadata line, and
  `(...see Scoring Guide.)` note absent from the document?
- Is the entire Scoring Guide (point tables, all three rubrics) absent, with no self-check
  checklist substituted in its place for any item (Section 0)?
- Does the document carry the plain title once at the top, with no `.masthead-meta` stack, and does
  each Task Level's section show only its star rating as a running head (no "Task Level," no
  "lowest"/"highest" label)?
- Does each Task Level's section open with a plain `.objective` statement translated from that
  Level's CSV grounding quote?
- Does each Task Level's section carry `page-break-before: always` (except the first) so it can be
  printed selectively on its own?
- Is every lesson's passage reprinted in full inside every Task Level section that uses it, with no
  cross-reference back to an earlier printing?
- Are vocabulary/matching items rendered with the existing `.wordbank`/`.fillblank`/`.qlist`
  pattern, with no vocabulary block invented for a lesson the source Task Level omits?
- Is answer space sized to what's asked (inline for a word/phrase/quote, full lines for a sentence
  or multi-sentence answer), with the highest Task Level's cross-text item getting three to four
  lines and no "Cross-text synthesis" label anywhere?
- Is the document black-and-white, em-dash-free, a single self-contained HTML file, reusing the
  existing base stylesheet with no new CSS classes?
