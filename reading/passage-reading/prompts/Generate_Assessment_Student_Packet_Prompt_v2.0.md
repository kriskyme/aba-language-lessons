# Passage Reading Assessment Student Print Formatting Prompt (v2.0)

Companion to the Passage Reading Assessment Generation Prompt. Takes one completed Set assessment (one section per
task Level, each with Vocabulary & Idiom Mastery and Reading Comprehension items) and produces a single,
print-ready, black-and-white student handout with every teacher-facing element removed: source-lesson/Tests
tags, CSV grounding quotes, item counts, and the entire Scoring Guide.

**Paste bundle:** run this prompt with `shared/Student_Packet_Style_Guide.md` alongside it (§A-§C format and
stylesheet, §E translations, §F task rules, §G regeneration, §I shared packet self-check). This prompt states only
what is specific to a Reading assessment packet.

**Current version: v2.0.** History: `Changelog.md`.

**Input:** the completed Assessment `.md` in full: every task Level's CSV grounding quote, vocabulary items (one
lesson-block per lesson), comprehension items with each lesson's new passage, and the Scoring Guide. Pull all
content from it; invent nothing; drop no task Level. Student version only.

**Never carry into the student copy:** the `(Lesson N - Tests: ...)` tag under any item, the CSV quote's raw
wording (2.3 translates it), item-count and scope metadata, any `(...see Scoring Guide.)` note, and the whole
Scoring Guide (point tables and rubrics). **No self-check checklist substitute:** Reading's rubric-scored items are
ordinary written comprehension questions answered on the page; print them as plain numbered questions with sized
answer space (Style Guide §I item 11), the same way a lesson packet treats an extended-response item.

## SECTION 1: ASSESSMENT-SPECIFIC TRANSLATIONS

Style Guide §E applies. Add these:

| Teacher-facing term | Student-facing rendering |
|---|---|
| Task Level | A star rating shown as the section's running head, not a menu: the teacher assigns each student one Level's pages. |
| CSV grounding quote | A plain can-do `Objective:` statement at the top of that Level's pages. |
| `(Lesson N - Tests: ...)`, item counts, scope framing, grading notes, Scoring Guide | Not shown. |
| "Cross-text synthesis" | Not named; the item's own instruction already says to compare both passages. |
| "New passage: ..." | A plain headline above the reprinted passage, "new passage" framing dropped. |
| "Lesson N:" block labels | A plain `.subgroup-label` naming only the passage or topic. |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One document, self-contained task-Level sections

One document, one section per task Level in the band, each self-contained so a teacher can print or photocopy one
Level's pages: `page-break-before: always` on every section but the first.

### 2.2 Masthead and running heads

The assessment's plain title ("Module {M} Set {N} Assessment") as an `<h1>` in a `.masthead` once at the top. No
`.masthead-meta` stack: an assessment spans every Level in a band and has no single lesson version code (the same
as the other modalities' assessment packets). Each Level's section opens with a `.section-title`-style running
head showing only its stars (`★★`; no "Task Level," no "lowest/highest"). No Name/Date field, kicker, subtitle,
or footer.

### 2.3 Per-Level objective

Immediately after each running head, that Level's CSV grounding quote as a plain `.objective` paragraph with the
bold `Objective:` label, phrased as something the student can picture doing.

### 2.4 Vocabulary & Idiom Mastery

A `.section-title` ("Words & Phrases"), then one block per lesson in source order under a `.subgroup-label`.
Word-bank matching or fill-in-the-blank sets use the existing `.wordbank` (dashed rule) plus `.fillblank`/`.qlist`
pattern; banks sit before their items (Style Guide §F). Where a Level has no vocabulary item for a lesson, omit
the block with no placeholder.

### 2.5 Reading Comprehension

For each lesson's block: the plain passage headline (`.article .headline`), the passage with its lettered
paragraphs (`.para-letter`), then that lesson's items as a numbered `.qlist` in source order. No annotation key
and no footnote sidebar (lesson-only features). Reprint the full passage inside every Level's section that uses
it, even though the text is identical across Levels, so each section stays self-contained.

### 2.6 Answer space and item rendering

Style Guide §I item 11: `.blank` for a paragraph letter or a fill-in word inside the sentence; `.ans-line-sm` for a
word, phrase, or quote answered on its own line; two or more `.ans-line` rows for a sentence or multi-sentence
answer. The highest Level's cross-text item gets three to four `.ans-line` rows as the final numbered item in
that Level's comprehension section, after both passages it references, with no "Cross-text synthesis" label.
Circle-the-word and multiple-choice items print exactly as the source phrases them, choices inline, with no
grading note.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Style Guide §A-§D. No delta CSS: `.masthead`, `.section-title`, `.objective`, `.subgroup-label`, `.wordbank`,
`.fillblank`, `.qlist`/`.num`/`.qbody`, `.ans-line`/`.ans-line-sm`, `.blank`, `.article`/`.para-letter` are all
in the base stylesheet. The one behavioral addition is the per-section page break (2.1).

## SECTION 4: WORKFLOW

Style Guide §G: run immediately after the Assessment `.md` is complete, in the same session; the `.md` is the
source of truth; content changes go into it and regenerate.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

Run `shared/Student_Packet_Style_Guide.md` §I first. Then:

1. Every tag, item-count or scope line, grading note, and the entire Scoring Guide absent, with no checklist
   substituted for any item?
2. Title once at the top, no `.masthead-meta`; each Level's section headed only by its stars, with a page break
   before every section but the first?
3. Each section opens with a plain `Objective:` statement translated from its CSV quote?
4. Every lesson's passage reprinted in full inside every Level section that uses it, with no cross-reference back
   to an earlier printing?
5. Vocabulary blocks rendered with the existing `.wordbank`/`.fillblank`/`.qlist` pattern under plain topic
   labels, none invented for a lesson the Level omits?
6. Cross-text item last in its section with three to four lines and no label?
