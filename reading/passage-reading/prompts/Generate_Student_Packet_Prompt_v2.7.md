# Passage Reading Student Print Formatting Prompt (v2.7)

Companion to the Passage Reading Lesson Generation Prompt. Takes one completed 2-day lesson and produces a
single, print-ready, black-and-white student handout: one self-contained HTML document covering both days, with
every teacher-facing pedagogical term translated into plain instructions a student (or a parent glancing at the
page) can act on.

**Paste bundle:** run this prompt with `shared/Student_Packet_Style_Guide.md` alongside it. The Style Guide holds
every rule shared by all packet prompts: format constraints and the base stylesheet (§A-§C), the universal
teacher-to-student translations (§E), star ratings and lettered Tasks (§F), the rule that the packet is always a
regeneration of the Markdown (§G), delta classes (§H), and the shared packet self-check (§I). This prompt states
only what is specific to a Passage Reading packet.

**Current version: v2.7.** For the dated version history and the reasoning behind each change, see `Changelog.md`.

**Input:** an already-completed 2-day lesson, supplied in full (both days): the anchor text with its paragraph
lettering and footnotes, the Phase 1 target vocabulary and idiom list with each idiom's transparent/opaque
classification, the Skill Spotlight, the Day 2 refresher text, the Collaborative Evidence Matrix's task-Level
items, the 2-3 discussion prompts and per-Level stems, and the Closing Transfer Check. Module and Band for
internal reference only. If no completed lesson is provided, stop and ask. This prompt produces the **student
version only**; a teacher-facing formatted version is out of scope.

**What this prompt does not change:** the content, task Levels, and pedagogical structure are fixed by the source
lesson. This is a presentation and translation layer: it does not cut or reweight questions, change which task
Levels exist, or alter the anchor text. It may restructure presentation (merging two adjacent task-Level sections
into one exercise with lettered sub-items) without cutting content or changing any Level's difficulty.

## SECTION 1: READING-SPECIFIC TRANSLATIONS

Style Guide §E's rows apply. Add these for a Reading lesson:

| Teacher-facing term | Student-facing translation |
|---|---|
| Close Reading with Annotation, or any Phase 2 reading strategy | A short instruction plus the annotation key (2.9), never narrated as a named strategy; every packet gets the "Read & Mark It Up" treatment regardless of the strategy used in class. |
| Reciprocal Teaching roles (Summarizer, Questioner, ...) | A plain instruction line, not a role title. |
| Paragraph letters `[A]`, `[B]`, ... | Kept: a student needs them to find their place. Rendered as the bracketed letter before each paragraph. |
| Footnotes | Kept as numbered notes at the bottom of the text's page, plain sentences. |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One combined document; two Unit sections

One shared document for the whole class, every task Level inside it as a star-rated option. Label the two sessions
Unit 1A and Unit 1B (or the lesson's own number: Unit 2A/2B, ...), folded into the section heading text itself
("Unit 1A: The Basilica That Refuses to Be Finished"), left-aligned, never as a separate divider. Task lettering
restarts in Unit 1B. Each masthead section carries the modality label `Reading` in its
`.masthead-meta` stack (Style Guide §B, §I item 5).

### 2.2 Objective statement

Immediately after the title, before any warm-up content, the lesson's objective as a can-do statement drawn from
the Skill Spotlight and the Reading objective it was built from, phrased as something the student can picture
doing ("describe a place by noting specific features and comparing them to something more familiar, and identify
the words a writer uses to show admiration or judgment without stating it directly").

### 2.3 Section titles

A consistent section-title style for each named block: Before You Read, Read & Mark It Up, Check Your
Understanding, Warm-Up, Investigate the Text, Discuss It, Wrap It Up (or the equivalent set). Where Day 1's
comprehension items would split into two near-identical blocks (a Fact Finder set and a Cause & Effect set on the
same content), merge them into one Task with sequential numbered questions; a vocabulary-in-context exercise stays
its own Task. Carry each item's stem only: every `**Answer note:**` line stays in the `.md` (Style Guide §E), a
`[STOP & CHECK]` prints as its question alone, and no stem keeps a parenthetical that states what the item asks
for (Quality Standards §C9).

### 2.4 Worked model before independent application

If the objective is first tested only in Unit 1B's independent tasks (nothing between Phase 1's vocabulary work and
the differentiated task set demonstrates the skill on the anchor text), insert a short worked-model callout after
Unit 1A's core comprehension task and before Unit 1B. Use real sentences from the anchor text to walk through the
reasoning the objective requires, under a plain heading such as "Focus on the Objective." State each example
directly; no framing sentences like "here's how this works." Work the model on sentences no printed task then
asks about, so it never pre-answers an item (Quality Standards §C9).

### 2.5 Closing activity

Translate the Closing Transfer Check into a plain "Wrap It Up" instruction that has the student apply the exact
named objective to something new, stated as directly as possible (what to pick, what to do with it). If the
closing offers different sentence-starter difficulty, present those as star-rated options in the same list style
as the discussion stems. No stage directions ("say it out loud," "your teacher may call on a few pairs") unless the
source mechanism specifically requires a public share step.

### 2.6 Discussion section

Translate the oral-output protocol into its room-neutral student instruction (Style Guide §E, Quality Standards
§D11): Rotating Partners prints as find-a-new-partner-as-you-go, every other protocol as small groups that all
discuss simultaneously. Pull the
source lesson's 2-3 distinct prompts directly; if an older lesson supplies only one, write 1-2 more that explore a
different angle of the same core question and note in your working notes that the lesson should be regenerated
against the current Lesson prompt. Fold any Panel Round listener task into one of the group prompts rather than
dropping it. List prompts left-aligned, regular weight, unquoted. Provide star-coded stems below them, keyed to the
source lesson's per-Level stems, stems only (Style Guide §F).

### 2.7 Vocabulary and idioms

"Words to Know" renders as the `.vocab-list` table. "Idioms to Know" always renders as the `.spotlight-box`
"Phrase Spotlight" treatment, each entry an unnumbered `.idiom-item` paragraph (`<span class="idiom-phrase">phrase
</span>: gloss.`), regardless of how many idioms there are; never a table, never numbered, and never labeled. The
lesson doc's transparent/opaque classification is for the teacher and does not appear on the page.

### 2.8 Callout boxes and word banks

Bordered `.spotlight-box` containers are reserved for genuine spotlights: the Phrase Spotlight and the 2.4 worked
model. Ordinary content (a vocabulary list, an instruction paragraph) renders plain. The one exception: a word
bank gets a light dashed rule above and below, not a full border, and sits immediately before the question(s) or
sentence frame it supplies (Style Guide §F).

### 2.9 Annotation key: a standing default

Every packet includes a "Read & Mark It Up" section with a floated annotation-key sidebar that the article text
wraps around, beside the first paragraph or two of the anchor text, regardless of the strategy used in class. In
print the student reads independently, so an annotation habit substitutes for every interactive strategy.

```
underline    a word you don't know
( circle )   a connector word: but, because, when
[ bracket ]  the sentence with the paragraph's main idea
?            next to anything that surprises you
```

Add a fifth mark, `!` next to a word that feels like the writer's opinion, only when the lesson's task Levels
include an evaluative-language objective (in practice Advanced and up). An unused mark is worse than no mark.

**The key is band-conditioned by that same rule.** The four marks above are the Intermediate-and-up default.
A Beginner anchor is calibrated to Level 1, whose ceiling (Lesson prompt 0.2) allows one memorized frame, at
most a single coordinator, and literal picture matching with no inference: there is no connector to circle
beyond "and," and no main-idea sentence to bracket that the Level's own comprehension demand would support.
A Beginner packet therefore prints three marks, substituting the mark its text can actually carry:

```
underline    a word you do not know
( circle )   a word that tells you about a thing
?            next to anything that surprises you
```

Never print a mark the band's anchor text cannot support, and never pad the key back to four to make packets
across bands look alike.

### 2.10 Refresher and secondary text blocks

The Day 2 vocabulary refresher, or a second comparison text attached to a task, gets a plain bordered text block,
visually distinct from the anchor text but not a callout box. Include a rule between it and surrounding content
only where it aids readability.

### 2.11 Photos

A Visual Inquiry hook photo, and the Level 1-2 picture task's picture, embed the lesson's own named `_Img_` asset
per Style Guide §F ("Embedded photos"): one `<img class="photo">` data URI with its `.image-caption` (descriptive only, never a credit; credits live in the
Set's `Image_Credits.md`), sized per §F.
If the lesson `.md` calls for a picture but names no asset file, stop and report it as a source-document gap
rather than printing a placeholder or a teacher note.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Style Guide §A-§D. A Passage Reading packet has no delta CSS of its own (Style Guide §H.2); the base stylesheet is
the whole of what it needs.

## SECTION 4: WORKFLOW

Style Guide §G: run immediately after the lesson `.md` is complete, in the same session; the `.md` is the source
of truth; deliver the HTML for review; content changes go into the `.md` and regenerate.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

Run `shared/Student_Packet_Style_Guide.md` §I first. Then:

1. Section 1's Reading rows applied: no strategy or role names; paragraph letters and footnotes carried through?
2. Unit 1A / Unit 1B labels folded into the headings, both masthead sections carrying the label `Reading` (2.1)?
3. Objective as a can-do statement before any warm-up, and Wrap It Up connecting back to it (2.2, 2.5)?
4. Fact Finder and Cause & Effect merged into one Task where they covered the same content (2.3)?
5. Worked-model box present between the Units if the objective is first tested in Unit 1B, stating its examples
   directly (2.4)?
6. Discuss It as simultaneous small groups with 2-3 unquoted, left-aligned prompts, any outer-circle task folded
   in, stems only (2.6)?
7. Idioms as the Phrase Spotlight, unnumbered and unlabeled (2.7)?
8. Annotation key present, floated beside the first paragraphs, `!` mark only when an evaluative-language
   objective exists (2.9)?
9. Refresher text as a plain bordered block, not a callout (2.10)?
10. Every hook or task photo embedded from the lesson's named asset, none placeholdered (2.11)?
11. Every `Answer note:` stripped, stops printed as questions only, no stem parenthetical stating the answer, and
    the worked model on sentences no task asks about (2.3, 2.4)?
