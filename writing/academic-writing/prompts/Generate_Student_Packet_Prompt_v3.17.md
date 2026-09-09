# Academic Writing Student Print Formatting Prompt (v3.17)

Companion to the Academic Writing Lesson Generation Prompt. Takes one completed Academic Writing lesson (a 2-day
cycle, one position within a Beginner Set or an Intermediate/Advanced/Proficient Module Pair) and produces one
print-ready, black-and-white student handout for it: a single self-contained HTML document covering both days,
with every teacher-facing pedagogical term translated into plain instructions.

**Paste bundle:** run this prompt with `shared/Student_Packet_Style_Guide.md` alongside it. The Style Guide holds
every rule shared by all packet prompts: format constraints and the base stylesheet (§A-§C), the universal
teacher-to-student translations (§E), star ratings and lettered Tasks (§F), the rule that the packet is always a
regeneration of the Markdown (§G), this modality's delta classes (§H.3), and the shared packet self-check (§I).
This prompt states only what is specific to an Academic Writing packet.

**Current version: v3.15.** For the dated version history and the reasoning behind each change, see `Changelog.md`.

**Input:** which lesson is being formatted (Set position 1-4, Pair position 1-8 where applicable, global Lesson
number) and its content for both days in full: the grammar mini-lesson(s) with rule and examples, the
controlled-practice activities, prewriting materials, the
drafting task and each Level's 0.2 target, the self-edit checklist, the Peer Editing Form where the lesson runs
it, the Closing Transfer Check where the lesson has one, the Skill Spotlight's objective wording (even for a later
lesson), and the Set's shared Scenario material this lesson's days actually use (the Word Bank for the practice
object, the Draft Word Bank for the draft object, whichever each day uses). Pull everything from the lesson;
invent nothing; drop no task Level. Student version only.

**What this prompt does not change:** content, task Levels, and structure are fixed by the source lesson. This is
a presentation and translation layer; it may merge two adjacent practice activities into one exercise with
lettered sub-items, but never cuts content or changes a Level's difficulty.

## SECTION 1: WRITING-SPECIFIC TRANSLATIONS

Style Guide §E's rows apply. Add these:

| Teacher-facing term | Student-facing translation |
|---|---|
| Focus A / Focus B (Grammar Focus); Essay Focus A/B | No labels. Each grammar mini-lesson gets a plain topic name in its heading ("Grammar: Comparing Things"); essay-structure content gets its own plain-titled box ("How an Essay Is Built," "Writing Your Thesis"). |
| Scenario | Not named. Present the topic and stimulus (the student's own object, the prompt, an embedded image where the lesson uses one per Quality Standards §D8) directly, no framing about why it was chosen. Never "the picture your teacher shows you" and never an empty picture box. |
| Frame-regime / composition-regime / essay-regime | Never appears; the star rating and the task's own instruction carry the difference. |
| Leveled Mentor Ladder / Mentor Text / Mentor Essay | Not printed at all (2.6). The teacher presents the ladder; no "See How It's Done," no star-labeled examples, no task that refers to an example. |
| The part of the piece a Module drafts (Conventions §C) | Named plainly in the task: "Write your body paragraphs," "Write your introduction and conclusion," "Write your second paragraph"; never "the rest of your essay" or "finish your essay." |
| Required feature | Stated as a plain instruction inside the task ("Include one comparison and one reason"). |
| Self-edit checklist plus its revision / Peer Editing Form | "Check and Improve Your Writing" / "Trade and Check" (2.8), with the actual items as questions, no section numbers, never "fix." |
| Editing a paragraph, confusable-pair drill, and other activity-type names | A plain instruction (how many errors to find; a forced choice), never the activity-type name. |
| Self-revision mechanism | A plain instruction to cross out (not erase) what changed and write the new version next to it. |
| Hand-off note (Pair position 4) | Plain continuation language ("You'll keep working on this piece soon"), never "finished" or "published" (2.7). |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One file per lesson, two masthead sections

Each lesson is one self-contained file covering both days, laid out as two masthead sections: `.masthead` for Day
1, `.masthead.masthead-later` for Day 2 (Style Guide §B), both under the same heading text, numbered by the
lesson's **Set position** (1-4, not its global number) and lettered by day: "Unit `{N}A`: `{Title}`" / "Unit
`{N}B`: `{Title}`". Never "Day 1"/"Day 2." Task lettering restarts at A in each section. Both masthead
sections carry the same `.masthead-meta` stack: the modality label `Writing` and the lesson's Band plus its
version code, where `<Lesson>` is the global number (Style Guide §B). File name `{Topic}_{Band}_L{N}_Packet.html` in the lesson's folder (Conventions §D).

**Self-containment across a shared Scenario:** every lesson's packet stands alone. Reprint whatever shared
Scenario reference material (a Word Bank, a comparison table, an embedded image) either of this lesson's days actually
needs, so a teacher printing only Lesson 3 does not need Lesson 1's packet in hand. Lessons 3 and later reprint the
Draft Word Bank, not the practice object's Word Bank; Lesson 2 prints both, each directly before the first task
that uses it. The file's `{Topic}` and every Unit heading name the object that lesson writes about (the practice
object for Lessons 1-2, the draft object from Lesson 3 on).

### 2.2 Objective statement, under both mastheads

Immediately after each masthead's heading, the lesson's objective as one can-do sentence in the student's
voice, drawn from the Skill Spotlight and written as "I can" plus the skill ("Objective: I can describe
something of my own by comparing it to something else and giving a real reason for the comparison."),
prefixed with the bold `Objective:` label (Style Guide §B, §E). Never "You will," "To describe," or a bare
verb phrase. It names the skill, never the Scenario object ("my phone case," "one piece of my clothing"), and
it is the same sentence for every student: no second sentence for a higher Level, no "Some of you will also," no tier narration (Quality Standards
§D1; Style Guide §E). Identical under both sections, since Day 2's half may be handed out in a separate
session.

### 2.3 Section titles

A consistent section-title style appropriate to the day: a grammar day (Grammar, Try It), a drafting day (Get
Ready to Write, Write It, Share a Line), a closing day (Trade and Check, Fix It Up, Wrap It Up). Where two
controlled-practice activities on the same point would split into near-identical blocks, merge them into one Task
with sequential items.

### 2.4 Task label line

The Task label sits alone on its own line, never sharing a line with a star rating: either bare ("Task A.") when
the star-rated blocks beneath it are self-explanatory, or followed by one short, genuinely informative clause
tied to that task's content ("Task B. Read the essay below, then answer the question."). A star belongs only on
the instruction line of the individual activity block it differentiates. Everything else about stars, one star
per lettered Task, letter continuity, ascending order, and callouts is Style Guide §F. Where a frame-regime
Level's work is a fill-in-the-blank and a composition-regime Level's is an original paragraph, present each
star's actual instruction as written (a blank frame for ★/★★, a writing space for ★★★/★★★★). The frame is
printed once per masthead section, in the grammar box or the Word Bank; every frame-regime Task after it shows
only the blank line and its lead says "Complete the frame," never re-quoting it (Style Guide §F). If the
Markdown gives one star the same complete-the-frame task twice in a section, report it against Quality
Standards §D10 rather than printing it twice. Any Task with
more than one action or question is a one-sentence lead line then a numbered list, one action or question per
step, blanks and answer lines inside the step that needs them; never a paragraph of chained instructions
(Style Guide §F, instructions as steps). Carry each item's stem only: every `**Answer note:**` line and an
editing paragraph's error list stay in the `.md` (Style Guide §E), and no stem keeps a parenthetical that states
what the item asks for (Quality Standards §C9).

### 2.5 Grammar box translation

Each grammar mini-lesson renders under the heading "Grammar:" plus the plain name of the point ("Grammar:
Comparatives + Because"), the rule in one or two short sentences and 2-3 example sentences beneath it in the
source lesson's own format (a short `.rule-table` or a simple list of `.model-step` lines). No Focus A/B labels.
It is a teaching callout: no star tag anywhere in it, and it appears before every task that depends on it (Style
Guide §F). Essay-structure content (Essay Focus A/B) renders the same way under its own plain title.

### 2.6 The Mentor Ladder is not printed

The Leveled Mentor Ladder (the Mentor Texts and Essays) is the teacher's material: it is presented on the board
or read aloud on the day the lesson presents it (Lesson 1 Day 2; Lesson 5's second look) and never printed in
the packet. No "See How It's Done" section, no star-labeled examples, and no task that asks the student to find
or compare an example; the walkthrough and its partner talk stay in the Markdown as teacher facilitation. A
packet task models a form with its own frame or steps, not with a reprinted model text.

### 2.7 Closing activity: check hand-off vs. finale first

A Set's fourth lesson, Day 2 (Unit `4B`) has a closing section. **Before writing it, check which kind of Lesson 4
this is:**
- **A true finale (Beginner's Lesson 4; a Pair's Lesson 8):** the piece is finished and published. Translate the
  Closing Transfer Check into a plain "Wrap It Up" instruction applying the named objective to something new. For
  Pair position 8, also include the separate short task exercising Module N+1's own skill (Lesson prompt 0.8) as
  a second "Wrap It Up" prompt, not labeled as covering "a different Module."
- **A hand-off (a Pair's Lesson 4):** the piece is a complete, self-revised draft, not yet published. Never use
  "finished," "published," "share your piece," or any language implying the piece is done. The hand-off is one
  plain `.instr` line after the last Final Copy Task ("You'll keep working on this piece soon."), nothing more:
  no "Before It Moves On" section, no note, stem, or feature-marking Task. That line belongs to Lesson 4's
  hand-off only; no other unit ends with a "keep your piece" or "you'll keep working on it" wrap-up (Style
  Guide §E).
No stage directions about what the teacher will do next (Style Guide §E).

### 2.8 Trade and Check and Check and Improve Your Writing

Translate the self-edit checklist and the revision that acts on it into one section, "Check and Improve
Your Writing": under the section title, one plain line for anything every Level does (the cross-out rule,
"mark it as each line says"), then one lettered Task per star level, each with exactly one star tag, a
one-sentence lead ("Check your paragraph, then make it better."), and one numbered list: that level's check
items as questions (repeating the items the Levels share), continuing straight into its improvement steps
with their answer space (Style Guide §F, check-then-improve; instructions as steps). Say "improve," "make it
better," "make each change you marked," never "fix." Frame-regime Levels' oral check plus their frame
revision is its own one-star Task, not omitted. Never a check section followed by a separate revision
section. Never a star on a list item, never two stars on one line. Translate the Peer
Editing Form, where this lesson runs it, into "Trade and Check": partner instructions, the form's specific
questions, then space for one compliment and one suggestion. No "Finished early?" or other speed-gated
add-on anywhere in the packet; a heavier tier from the lesson is its own starred Task or is dropped.

### 2.9 Answer and writing space

Style Guide §I item 11, sized to the task Level's own 0.2 target for a drafting task: `.blank` for a mid-sentence
blank inside a `.fillblank` list, `.ans-line-sm` for a one-word or short-phrase answer on its own line below the
item, several `.ans-line` rows for a paragraph or essay draft. A drafting task states its target as a sentence
count only ("Aim for 3-6 sentences"); the word range and any "finish tomorrow" pacing stay in the Markdown
(Style Guide §E).

### 2.10 Opening of a drafting-day packet

A drafting lesson's Day 1 unit opens with the Draft Word Bank, then a section titled "Get Ready to Write"
holding one unstarred Task: the printed list of draft-object choices to circle, four to eight like things
("Pick one of these things to write about and circle it: my jacket, my hoodie, my sweater, my shirt, my
T-shirt, my dress, my scarf, my hat"), then the quick-plan action with its answer line ("Write three words
from the Word Bank that fit it"). Nothing else: no "look at it," no "put it on your desk" or borrowing fallback
(the object is a subject, not a prop, Style Guide §E), no questions, no "last time," no "your planning notes," no "the example from
earlier this week," and no re-look at Mentor Ladder examples (Quality Standards §D9, §E6). The unit heading
names the generic category ("Describing My Clothing"), not one item from the list.
Later in the same unit, a task that needs a list or plan builds it inside the task with its own lines. The
drafting task's lead line says "Write about the clothing" (the category), not "the thing you circled."

A drafting lesson's Day 2 unit opens directly with "Check and Improve Your Writing" (2.8), one Task per star
holding the check questions and then the improvement steps the lesson names, then the share section, with no
wrap-up line after it. No "Write It"
section, no "Finish your piece from last time," and no count-your-sentences task on Day 2; the draft was
completed on Day 1. A partner check says which part a word describes; it never points (Style Guide §E).

A drafting lesson's Write It tasks name the part the Module drafts: at Pair position 3 the essay Levels' task
is "Write your body paragraphs" (two or three, each with a topic sentence, under the working thesis you wrote in
Get Ready to Write), with no hook or conclusion step; at position 7 it is "Write your introduction and
conclusion" with the kept body paragraphs in hand; paragraph Levels write "one paragraph" at both positions.
Check and Improve Your Writing asks only about the part written that lesson (position 7's merged list also
re-checks the kept part's features by name).

A Pair position 4 lesson (Set position 4) prints no checklist at all. Its Day 1 unit is the Word Bank, then "A
Reader's Request" (one unstarred Task: trade pieces, read, write one thing you want to know more about on your
partner's page), then "Make It Stronger": one Task per star as steps, the before/after table under the
composition-regime Tasks. Its Day 2 unit is "Final Copy" (one Task per star: copy the chosen sentence, or copy
the paragraph cleanly, or copy your body paragraphs cleanly, then the one hand-off line, 2.7) and "Wrap It Up"
(the Closing Transfer Check). No "Last Look," no proofread pass, no counting, no hand-off section. A position 8
lesson's Day 2 unit is "Final Copy" of the assembled whole, then the publish/share step and "Wrap It Up."

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Style Guide §A-§D, plus this modality's delta classes in §H.3 (`.rule-table`, `.fillblank`, `.model-step`). Add
`.rule-table` to the packet's `@media print` page-break-avoid list.

## SECTION 4: WORKFLOW

Style Guide §G: run immediately after the lesson `.md` is complete; the `.md` is the source of truth; deliver for
review; content changes go into the `.md` and regenerate.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

Run `shared/Student_Packet_Style_Guide.md` §I first. Then:

1. Section 1's Writing rows applied: no Focus, Scenario, regime, Mentor, ladder, required-feature, or
   activity-type language anywhere?
2. One file, two masthead sections under one heading numbered by Set position, `Writing` label and global-number
   version code on both mastheads; shared Scenario material this lesson needs reprinted (2.1)?
3. `Objective:` statement under both mastheads (2.2)?
4. Every Task label alone on its own line, bare or with one informative clause; each star's instruction written
   as its own kind of task (2.4)?
5. Grammar and essay-structure boxes plainly titled, star-free, before the tasks that need them (2.5)?
6. No Mentor Ladder, worked example, or find-your-example task printed anywhere (2.6)?
7. Lesson 4/8 closing checked for hand-off vs. finale, with no "finished/published" language at a hand-off, the
   hand-off one line after Final Copy with no note section, and the Module N+1 task included at Pair position 8
   (2.7)?
8. Check Your Own Work and Trade and Check present with the lesson's actual items, oral equivalents printed for
   frame-regime Levels (2.8)?
9. `.blank` inside sentences, `.ans-line-sm`/`.ans-line` standalone, sized to the Level's target (2.9)?
10. `.rule-table` in the print page-break list; only §H.3 classes added (Section 3)?
11. Frame printed once per masthead section; later ★/★★ Tasks show only the blank line, leads never re-quote
    the frame, and no star has the same complete-the-frame Task twice (2.4; Style Guide §F, §I item 17)?
12. Every `Answer note:` and error key stripped; no stem parenthetical stating the answer (2.4)?
