# Academic Writing Student Print Formatting Prompt (v3.5)

Companion to the Academic Writing Lesson Generation Prompt. Takes one completed Academic Writing lesson (a 2-day
cycle, one position within a Beginner Set or an Intermediate/Advanced/Proficient Module Pair) and produces one
print-ready, black-and-white student handout for it: a single self-contained HTML document covering both days,
with every teacher-facing pedagogical term translated into plain instructions.

**Paste bundle:** run this prompt with `shared/Student_Packet_Style_Guide.md` alongside it. The Style Guide holds
every rule shared by all packet prompts: format constraints and the base stylesheet (§A-§C), the universal
teacher-to-student translations (§E), star ratings and lettered Tasks (§F), the rule that the packet is always a
regeneration of the Markdown (§G), this modality's delta classes (§H.3), and the shared packet self-check (§I).
This prompt states only what is specific to an Academic Writing packet.

**Current version: v3.5.** For the dated version history and the reasoning behind each change, see `Changelog.md`.

**Input:** which lesson is being formatted (Set position 1-4, Pair position 1-8 where applicable, global Lesson
number) and its content for both days in full: the grammar mini-lesson(s) with rule and examples, the
controlled-practice activities, the Leveled Mentor Ladder on the day it appears, prewriting materials, the
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
| Leveled Mentor Ladder / Mentor Text / Mentor Essay | Worked examples labeled only by star count ("★★★ Example"), never "Mentor," "Level," "ladder," or "set" (2.6). |
| Required feature | Stated as a plain instruction inside the task ("Include one comparison and one reason"). |
| Self-edit checklist / Peer Editing Form | "Check Your Own Work" / "Trade and Check" (2.8), with the actual items, no section numbers. |
| Editing a paragraph, confusable-pair drill, and other activity-type names | A plain instruction (how many errors to find; a forced choice), never the activity-type name. |
| Self-revision mechanism | A plain instruction to cross out (not erase) what changed and write the new version next to it. |
| Hand-off note (Pair position 4) | Plain continuation language ("You'll keep working on this piece soon"), never "finished" or "published" (2.7). |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One file per lesson, two masthead sections

Each lesson is one self-contained file covering both days, laid out as two masthead sections: `.masthead` for Day
1, `.masthead.masthead-later` for Day 2 (Style Guide §B), both under the same heading text, numbered by the
lesson's **Set position** (1-4, not its global number) and lettered by day: "Unit `{N}A`: `{Title}`" / "Unit
`{N}B`: `{Title}`". Never "Day 1"/"Day 2." Task lettering restarts at A in each section. The opening masthead
carries the modality label `Writing` and the lesson's Band plus its version code, where `<Lesson>` is the global
number (Style Guide §B). File name `{Topic}_{Band}_L{N}_Packet.html` in the lesson's folder (Conventions §D).

**Self-containment across a shared Scenario:** every lesson's packet stands alone. Reprint whatever shared
Scenario reference material (a Word Bank, a comparison table, an embedded image) either of this lesson's days actually
needs, so a teacher printing only Lesson 3 does not need Lesson 1's packet in hand. Lessons 3 and later reprint the
Draft Word Bank, not the practice object's Word Bank; Lesson 2 prints both, each directly before the first task
that uses it. The file's `{Topic}` and every Unit heading name the object that lesson writes about (the practice
object for Lessons 1-2, the draft object from Lesson 3 on).

### 2.2 Objective statement, under both mastheads

Immediately after each masthead's heading, the lesson's objective as a can-do statement drawn from the Skill
Spotlight and the Writing objective it was built from ("describe something familiar by comparing it to something
else and giving a real reason for the comparison"), prefixed with the bold `Objective:` label (Style Guide §B).
Restated under both sections, since Day 2's half may be handed out in a separate session.

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
star's actual instruction as written (a blank frame for ★/★★, a writing space for ★★★/★★★★).

### 2.5 Grammar box translation

Each grammar mini-lesson renders under the heading "Grammar:" plus the plain name of the point ("Grammar:
Comparatives + Because"), the rule in one or two short sentences and 2-3 example sentences beneath it in the
source lesson's own format (a short `.rule-table` or a simple list of `.model-step` lines). No Focus A/B labels.
It is a teaching callout: no star tag anywhere in it, and it appears before every task that depends on it (Style
Guide §F). Essay-structure content (Essay Focus A/B) renders the same way under its own plain title.

### 2.6 The Leveled Mentor Ladder as star-labeled worked examples

Include this section only on the lettered section whose day presents the ladder, and only where it adds
something that section's own tasks do not already model (if a task already works with a shared model text at
multiple star levels, omit the separate showcase). Present it as a short run of worked examples, one per task
Level, labeled only by star count, in ascending order, under a plain heading such as "See How It's Done" with one
lead-in sentence saying why it is there. Include the whole run; do not tell students to read only their own
star's example. Keep it proportionate: for a multi-paragraph Mentor Essay, an opening excerpt plus one paragraph
containing the genuinely load-bearing moment, with a short bracketed bridge to the ending. A later lesson may
point back ("look back at the examples from earlier this week") instead of reprinting.

### 2.7 Closing activity: check hand-off vs. finale first

A Set's fourth lesson, Day 2 (Unit `4B`) has a closing section. **Before writing it, check which kind of Lesson 4
this is:**
- **A true finale (Beginner's Lesson 4; a Pair's Lesson 8):** the piece is finished and published. Translate the
  Closing Transfer Check into a plain "Wrap It Up" instruction applying the named objective to something new. For
  Pair position 8, also include the separate short task exercising Module N+1's own skill (Lesson prompt 0.8) as
  a second "Wrap It Up" prompt, not labeled as covering "a different Module."
- **A hand-off (a Pair's Lesson 4):** the piece is a complete, self-revised draft, not yet published. Never use
  "finished," "published," "share your piece," or any language implying the piece is done. Frame the hand-off
  plainly ("You'll keep working on this piece soon").
No stage directions about what the teacher will do next (Style Guide §E).

### 2.8 Trade and Check and Check Your Own Work

Translate the self-edit checklist into "Check Your Own Work": under the section title, one plain line for
anything every Level does (the cross-out rule, "mark it as each line says"), then one lettered Task per star
level, each with exactly one star tag and its own complete list of short, direct items phrased as things to
look for, repeating the items the Levels share (Style Guide §F). Frame-regime Levels' oral check is its own
one-star Task, not omitted. Never a star on a list item, never two stars on one line. Translate the Peer
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
T-shirt, my dress, my scarf, my hat"), then the quick-plan action with its answer line ("Look at it. Write
three words from the Word Bank that fit it"). Nothing else: no "put it on your desk" or borrowing fallback
(the teacher's, Style Guide §E), no questions, no "last time," no "your planning notes," no "the example from
earlier this week," and no re-look at Mentor Ladder examples (Quality Standards §D9, §E6). The unit heading
names the generic category ("Describing My Clothing"), not one item from the list.
Later in the same unit, a task that needs a list or plan builds it inside the task with its own lines.

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
   version code on the opening masthead only; shared Scenario material this lesson needs reprinted (2.1)?
3. `Objective:` statement under both mastheads (2.2)?
4. Every Task label alone on its own line, bare or with one informative clause; each star's instruction written
   as its own kind of task (2.4)?
5. Grammar and essay-structure boxes plainly titled, star-free, before the tasks that need them (2.5)?
6. Mentor Ladder shown only where it adds something, star-labeled, ascending, proportionate (2.6)?
7. Lesson 4/8 closing checked for hand-off vs. finale, with no "finished/published" language at a hand-off, and
   the Module N+1 task included at Pair position 8 (2.7)?
8. Check Your Own Work and Trade and Check present with the lesson's actual items, oral equivalents printed for
   frame-regime Levels (2.8)?
9. `.blank` inside sentences, `.ans-line-sm`/`.ans-line` standalone, sized to the Level's target (2.9)?
10. `.rule-table` in the print page-break list; only §H.3 classes added (Section 3)?
