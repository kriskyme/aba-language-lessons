# Listening/Speaking Student Print Formatting Prompt (v1)

Companion to the Listening/Speaking Lesson Generation Prompt (v1). Takes one completed lesson (all days) and
produces a single, print-ready, black-and-white student handout: one self-contained HTML document, with every
piece of teacher-facing pedagogical language translated into plain instructions. Mirrors Passage Reading's
Student Print Formatting Prompt (v1.2) closely - same translation principle, same base stylesheet, same
star-rating system for task Levels - adapted for a lesson type where the "text" is a real audio/video source the
class plays together, not a printed passage.

Use this prompt only after a lesson already exists in full. Do not use it to generate lesson content. This
produces the **student version only**.

## SECTION 0: SCOPE AND INPUTS

Required: the completed lesson (all days), supplied in full - the citation block, target vocabulary, Listening
Skill Spotlight and Speaking Skill Spotlight, the differentiated Days 2-4 listening tasks and Days 5-8 speaking
tasks, Background Notes, the oral output protocol's discussion prompts, and both Closing Transfer Checks. Pull
all content directly from the completed lesson; do not invent new vocabulary or tasks, and do not drop a task
Level present in the source lesson's band.

## SECTION 1: TRANSLATING TEACHER LANGUAGE TO STUDENT LANGUAGE

None of the left column may appear in the student-facing document.

| Teacher-facing term                                                | Student-facing translation                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Listening Skill Spotlight / Speaking Skill Spotlight               | A plain can-do objective statement (see 2.2), not narrated as "today we are practicing X."                                                                                                                                                                                                                             |
| Fishbowl / Town Hall / Concentric Circles / Jigsaw                 | A plain small-group discussion instruction: get into a group, here are your questions, take turns talking. Do not name the protocol. Fold any outer-circle/tracking task into the group's own task rather than dropping it - same print-medium reasoning as Passage Reading (a static page can't run a live rotation). |
| Task Level / Level (numeric)                                       | A star rating (★ to ★★★★), no numeric Level, no tier name.                                                                                                                                                                                                                                                             |
| Listening Closing Transfer Check / Speaking Closing Transfer Check | A plain closing-activity instruction (see 2.6, 2.9), not named as a check or referencing assessment language.                                                                                                                                                                                                          |
| Background Note                                                    | A short "Good to Know" box (see 2.5), not labeled as background knowledge scaffolding.                                                                                                                                                                                                                                 |
| Board-dependent moment                                             | Not shown to students at all - teacher-only classroom-management instruction.                                                                                                                                                                                                                                          |
| Differentiated participation / Foundation Support                  | Handled through the star system and task choice, never labeled or called out as a separate tier.                                                                                                                                                                                                                       |
| Timestamp/segment markers ([Segment N: ...])                       | These ARE shown to students, in plain form (see 2.3) - unlike a paragraph letter, a segment cue is a real navigational aid a student needs to find their place in a real recording during replay.                                                                                                                      |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One combined document, two parts

Produce a single shared document, not per-task-Level handouts. Structure it in two parts, mirroring the source
lesson's Listening half (Days 1-4) and Speaking half (Days 5-8): **Unit \_A** (Listening) and **Unit \_B**
(Speaking), each folded into its own section heading (e.g. "Unit 1A: New Bakery, Old Baking Method"), never
using "Day 1" or "Day 2" (the underlying lesson only has two now, but the packet still groups by Listening/Speaking
half, not by day). Each part restarts its own task lettering.

### 2.2 Objective statements, plain language, near the top of each part

Immediately after each part's heading, state that part's actual objective as a can-do statement pulled from the
Listening Skill Spotlight (Unit \_A) or Speaking Skill Spotlight (Unit \_B), phrased as something the student can
picture doing, not a process narration.

### 2.3 What You'll Watch/Listen To

Include a short boxed citation - title, one clear sentence describing what it's about, and platform - so
students know what they're about to watch, without academic citation jargon (no runtime, no editor/adapter
credits). Example: "You'll watch: 'New Bakery, Old Baking Method,' a video from VOA Learning English about a
bakery in Washington, D.C. that grinds its own grain." **Do not add a line inviting students to ask their
teacher for the link.** Students always have direct access to the media on the student side, so that line is
inaccurate, not just optional - flagged and corrected 2026-09-03. Where the source lesson uses segment labels,
carry the plain segment name (not "[Segment N:...]" bracket notation) into any task that references a specific
part of the recording, e.g. "Listen again to the part where Bethony talks about the taste."

**Placement (added 2026-09-03, after user review):** place this citebox immediately before the point in the
packet where students actually begin watching (typically right before the Listening Notes organizer or the
first "while you watch" instruction), not at the top of the unit alongside the objective. Students shouldn't be
told what they're about to watch several activities before they actually watch it.

### 2.4 No kicker lines, no metadata fields

Same as Passage Reading 2.4: no Name/Date field, no module/band kicker, no subtitle line, no footer note.

### 2.4a Every question gets a number (added 2026-09-03, after user review)

Any place in the packet where a student is asked to produce a specific, referenceable response - a written
answer, a guess, a prediction - gets a number, using the same `.num`/`.qbody` pattern as the star-rated tasks.
This applies outside the star-rated tasks too: Before You Watch/Listen's activation question(s), Show What You
Noticed's response, and any other standalone prompt with a response line. Where such a prompt sits outside a
`<ol class="qlist">` (a single question on its own, not part of a task list), use the `.qitem` class - a div
with the same flex/num/qbody layout as `.qlist li`, usable without an enclosing list - so it can be numbered "1."
even when nothing else on the page needs a "2." Multiple response lines under one prompt (e.g. a two-line
answer space) still count as one numbered question, not two. Two prompts separated by other content (e.g. a
guess before a clue and a second guess after it) are two separate numbered questions in sequence ("1." then
"2."), not one.

**What does not get a number:** fillable organizers (the Listening Notes table, a K-W-L chart) - these are
referenced by name ("the T-chart," "the K-W-L chart"), not by question number. Options within one question
(the four self-assessment statements under a single "which sounds like you" prompt, or a multiple-choice
item's parenthetical options) do not each get their own number - they belong to the one numbered question
that contains them, using plain bullets (`&bull;`) or inline parentheses, per 2.7's multiple-choice rules.

### 2.5 Good to Know boxes

Translate each Background Note into a short "Good to Know" callout box (spotlight-box styling). **Placement
(revised 2026-09-03, after user review):** place all of a unit's Good to Know boxes together at the very
beginning of Unit \_A, immediately after the objective statement - before the Before You Watch/Listen section and
well before the citebox, which sits later at the actual point students start watching or listening (see 2.3).
This replaced an earlier rule of placing each box near the task it's most relevant to; the earlier version
scattered informational content throughout the packet instead of front-loading context before any activity
begins. Keep to the source lesson's original count (typically 1-3); informational only, never the basis of a
question.

### 2.6 Listening Notes organizer

Where the source lesson's Day 1, Phase 2 note-taking structure is a comparison chart (the common case for
Describing), print it as a simple two-column fillable table with the source lesson's own row labels, positioned
before the star-rated listening tasks so students can fill it in while playing the source. For a different
organizer type (sequence chain, cause-and-effect chain, criteria grid, claims tracker), print the equivalent
simple fillable structure rather than forcing it into a two-column table.

**Match "watch"/"listen" wording to the source's real, confirmed media type (added 2026-09-03, after user
review).** Do not default to "watch"/"video" language. If the citebox (2.3) says "You'll listen to," every
related instruction - the Before You Watch/Listen heading, this organizer's instruction line, any task text
that references watching or listening - must say "listen" too, and vice versa for a confirmed video source.
Check the Lesson Generation Prompt's own citation block for how it describes the source before assuming either
way. Also: **do not add "(and watch again)" / "(and listen again)"** to this instruction line - it's implied
that students can replay the source, and spelling it out is redundant. "While you watch, fill in..." or "While
you listen, fill in..." is sufficient on its own.

### 2.7 Star-rated listening tasks

Merge the source lesson's Day 1, Phase 4 differentiated items (main ideas, details, and critical thinking, all
written as one task per Level under the current Lesson Generation Prompt) into one combined star-rated task per
Level, the same merge principle as Passage Reading 2.5: one Task per Level (A = ★ through D = ★★★★), sequential questions, using each Level's own actual items from the source
lesson rather than inventing new ones. Instruction to share with a different-task group goes before the task
list. No tier names, no "choose your own adventure" framing.

**Fixed-frame items need a complete, self-contained instruction.** Where the lowest task Level is a fixed-frame
listening extraction (e.g. "It is **_ and _**."), state inline, in the item itself, what the student listens for and
what goes in the blanks (with a word bank if needed). Do not also add a separate, unlabeled sentence-frame box
repeating the same frame with no instruction attached - that reads as a random fragment. Reserve a standalone
frame/"starter" box (2.10) for a task that has a genuine speak-it-aloud step to anchor it to.

**Multiple-choice items stay on one compact line (added 2026-09-03, after user review).** Fold the options
directly into the question as a parenthetical list embedded in the sentence itself - e.g. "This guide is about
backpacks for (school / hiking trips / shopping)." - rather than restating an instruction verb ("Circle:",
"Choose:") on every single item, and rather than breaking each option onto its own line. Both of those read as
repetitive and burn vertical space across a multi-item task. Instead, give one instruction line at the top of
the task block covering the whole set (e.g. "Circle the correct answer for each question below."), styled as a
short italic line above the numbered items, then let every item read as a single sentence with its options
inline.

**Picture-based items get real placeholders, not just words standing in for the image (added 2026-09-03).**
Where an item asks a student to identify or circle a picture rather than a word (e.g. "What does this guide
help you choose?"), print an actual placeholder box for each option - a small dashed-border box labeled for the
teacher with what photo belongs there (e.g. "[ photo: a backpack ]"), laid out side by side with a plain-text
label under each - not the object's name doing double duty as its own image. Reserve this treatment for
genuinely picture-based items; ordinary text-based multiple choice stays inline per the rule above rather than
being converted into picture placeholders unnecessarily.

**Word banks (and similar reference lists, e.g. a set of capacities or measurements) sit immediately before the
item(s) they serve, not bundled at the end of the task after every item (added 2026-09-03).** If a bank serves
only one item, place it directly above that item, inside the item's own block, not in a shared block at the
task's end. If it serves a short consecutive run of items that all draw from it, place it once, immediately
before the first item in that run. Never place a word bank after the last item that needs it - a student
reaching it only after answering has already lost the benefit.

**Multi-source star tasks (Advanced/Proficient Level 7, when the lesson's top task Level compares two real
sources).** Present both sources' relevant material directly inside that task block, in a labeled two-part
"compare" layout (a plain source label - e.g. "The TV Reporter's Version" / "In Her Own Words" - above each
short excerpt), not as a separate section elsewhere in the packet. Keep every excerpt within the lesson's own
fair-use ceiling (one to two sentences per source, paraphrase the rest); never print a full transcript excerpt
longer than what the source lesson itself quotes. Ask the comparison question after both excerpts, and if a
later Discuss It prompt also references the comparison, point back to this task by name ("the two descriptions
from Task D") rather than re-citing the sources again.

### 2.8 Show What You Noticed (Listening close)

Translate the Listening Closing Transfer Check into a plain paired activity built around the source lesson's
baked-in read-aloud script (Lesson prompt Section on Day 1 Phase 5): tell students their teacher will read a
short paragraph aloud, they should not read it themselves yet, and after saying the main idea out loud to a
partner (with response space to write it) they may read the script to check. Print the script itself using the
`.refresher.refresher-noline` block, positioned AFTER the response space, under its own "Check What You Heard"
label with an explicit "read this only after you've answered" instruction - never above or beside the response
space, where a student would see it before listening. No self-report framing, no naming it a check.

**Print the script upside-down (added 2026-09-03, after user review).** Add an `.upside-down` class to the
refresher block (`transform: rotate(180deg)`) as a physical deterrent against reading ahead, on top of the
position and instruction above - a curious student flipping ahead now has to physically turn the page around to
read it, which is a stronger deterrent than position and instruction alone. Update the instruction line to say
the text is upside-down on purpose and tell students not to turn the page around until they've answered (e.g.
"This is printed upside-down on purpose. Don't turn the page around until you've said and written your answer
above.").

### 2.9 Learn the Phrase (Speaking Skill Spotlight)

Open Unit \_B with the real modeled language from the source (the actual phrase(s) the real speaker used),
presented as a short "Learn the Phrase" spotlight-box, with the sentence frames the source lesson teaches
**inside the same box**, not as a separate list floating below it (fixed 2026-09-03, after user review - an
earlier version left the frame list outside the box, which read as a disconnected fragment rather than part of
the same spotlight). Do not invent new modeled language beyond what the source lesson already quotes.

**Never name a source component the student packet hasn't introduced.** A source page sometimes carries more
than one component behind the single citation given to students - e.g. a video plus its own on-page text
version, used as the transcript when generating the lesson. If Section 2.3's citation box only tells students
about one component (typically "You'll watch [the video]"), every quote anywhere in the packet - Learn the
Phrase included - must be attributed to that same thing ("In the video, ...") even if the lesson's internal
sourcing notes trace a particular line to the written transcript specifically. Do not surface a second label
("the article," "the transcript," "the interview") that was never introduced to students; it reads as an
unexplained new source dropped in mid-packet. If the packet genuinely wants students to know about a second
component (e.g. a written version they can also read), introduce it explicitly in the citation box first.

### 2.10 Star-rated speaking tasks (Practice It)

Same merge/star principle as 2.7, applied to the Day 2, Phase 2 differentiated production tasks (guided
practice plus any pronunciation marking exercise folded in as a short bonus line under the relevant task, not a
separate section). The multiple-choice formatting, picture-placeholder, and word-bank-placement rules in 2.7
apply here too - a fixed-frame speaking item with picture cues (e.g. ordering step-pictures) needs the same real
placeholder-box treatment, not words standing in for the images.

### 2.11 Discuss It

Same as Passage Reading 2.9: the oral output protocol's 2-3 rotated prompts, unquoted, regular weight, plus
star-coded sentence stems. Fold any outer-circle/tracking task into one of the prompts. **Number each prompt
using `.qitem` (added 2026-09-03, after user review), not a plain div with an inline "N." prefix** - the prompts
are questions like any other in the packet and should look like one: bold number, same font size and spacing as
every other numbered question (2.4a), not a separately-sized, separately-styled block.

### 2.12 Wrap It Up (Speaking close)

Translate the Speaking Closing Transfer Check into a plain paired closing activity, same style as Passage
Reading 2.8.

### 2.13 Callout boxes, answer space, redundant rules

Same rules as Passage Reading 2.12-2.14: callouts reserved for genuine spotlights (Good to Know, Learn the
Phrase, the citation box), word banks get the dashed-rule exception only, answer space matched to expected
answer length, no decorative rules.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

**Moved to a shared, cross-modality doc:** paste `shared/Student_Packet_Style_Guide.md` alongside
this prompt when generating. It holds the universal format constraints (single self-contained
file, black-and-white, no em-dashes, print-safe layout), the base stylesheet, and the HTML markup
conventions. **Reuse that base stylesheet unmodified** - the two exceptions this prompt used to
patch on top of it (broadening `.qlist .num` to a plain `.num` rule, and dropping the separate
`.discuss-block .prompt` font-size rule) are now folded into the shared stylesheet itself, so no
exception needs tracking here anymore.

For visual consistency across the whole program, this lesson type adds only the following classes
on top of the shared base stylesheet, following the same rule-formatting conventions
(`shared/Student_Packet_Style_Guide.md` §C):

```css
.citebox {
  border: 1px solid var(--ink);
  padding: 12px 16px;
  margin: 10px 0 16px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
}
.citebox strong {
  font-weight: 700;
}

.notes-table {
  width: 100%;
  border-collapse: collapse;
  margin: 10px 0 20px;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13.5px;
}
.notes-table th,
.notes-table td {
  border: 1px solid var(--rule);
  padding: 8px 10px;
  text-align: left;
  vertical-align: top;
}
.notes-table th {
  font-weight: 700;
  background: #f2f2f2;
}
.notes-table td {
  height: 38px;
}

.upside-down {
  transform: rotate(180deg);
}

.task-instr {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 13px;
  font-style: italic;
  color: var(--ink-soft);
  margin: 0 0 10px;
}

.pic-options {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
  margin: 8px 0 4px 4px;
}
.pic-option {
  width: 110px;
}
.pic-option .pic-box {
  border: 2px dashed var(--ink);
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 10.5px;
  color: var(--ink-soft);
  padding: 6px;
}
.pic-option .pic-label {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 12.5px;
  text-align: center;
  margin-top: 5px;
}

.match-list {
  margin: 8px 0 4px 4px;
}
.match-row {
  margin-bottom: 14px;
}
.match-row .match-label {
  display: block;
  font-weight: 700;
  margin-bottom: 3px;
}

.qitem {
  display: flex;
  gap: 10px;
  margin-bottom: 9px;
  font-size: 14.5px;
}
```

Added 2026-09-03, after user review: `.upside-down` (2.8's Closing Transfer Check script), `.task-instr` (the
single top-of-task instruction line, 2.7), `.pic-options`/`.pic-option` (picture-placeholder items, 2.7/2.10),
`.match-list`/`.match-row` (matching items, one pair per line rather than compressed arrow notation). `.match-row`
revised 2026-09-03 (second pass): label on its own line, followed by a full-width `.ans-line` (not `.ans-line-sm`)
below it, rather than a compact side-by-side "label: short blank" row - matches the same full-width-answer-line
standard used everywhere else in the packet, and gives enough room for longer matched phrases. `.qitem` added
2026-09-03 (third pass): a standalone numbered question outside any `<ol class="qlist">`, for Before You
Watch/Listen and Show What You Noticed prompts - see 2.4a.

## SECTION 4: WORKFLOW

**Generation timing (per Lesson Generation Prompt v1, third addendum, 2026-09-03):** run this prompt
immediately after the .md lesson is complete, in the same session/request - not as a separately-requested later
step. A lesson request produces both files together: the .md first, then this prompt run against that finished
.md to produce the .html. Deliver the .html for review before treating it as final.

**The .md is the single source of truth; this prompt's output is always a regeneration, never a standalone
edited artifact.** If a review round asks for a change that affects what students actually read as a task,
instruction, or vocabulary item, do not patch the .html directly - apply the change to the source .md first (the
Lesson Generation Prompt's output), then re-run this prompt against the updated .md to produce a fresh .html.
Hand-editing the .html for a content change leaves the .md silently out of sync with what's actually being
taught, and the two documents will drift apart over later regenerations.

The only edits that may be applied directly to the .html without touching the .md are pure formatting/translation-
layer fixes that don't change lesson content - a styling issue, a missed Section 1 translation, spacing/layout -
since these are properties of this prompt's output, not of the underlying lesson. When in doubt about which side
an edit belongs on, ask: would a teacher reading the .md need to know this changed? If yes, it's a .md edit
followed by regeneration; if no, it's safe to apply here directly.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

- Does every left-column term from Section 1 appear nowhere in student-facing text?
- Two parts (Unit \_A Listening / Unit \_B Speaking), each with its own plain objective statement and its own
  restarted task lettering?
- Are all of a unit's Good to Know boxes placed together at the very beginning of Unit \_A, right after the
  objective, rather than scattered near individual tasks?
- Does the "What You'll Watch" citation box sit right before the point students actually begin watching (e.g.
  right before the Listening Notes organizer), not at the top of the unit - and does it avoid inviting students
  to ask their teacher for the link, since students always have direct access to the media?
- Is there a fillable Listening Notes organizer, positioned before the star-rated listening tasks?
- Does every standalone question with a response line (Before You Watch/Listen, Show What You Noticed, any
  other prompt outside the star-rated tasks) carry a number via `.qitem`, rather than sitting unnumbered or
  using a bare bullet?
- Do both star-rated task blocks (listening and speaking) show only filled stars, no numeric Level, no tier name,
  with the share-with-a-different-group instruction before the list?
- Do multiple-choice items stay on one compact line each (options folded in as a parenthetical list, one
  top-of-task instruction line instead of a repeated verb on every item), with genuinely picture-based items
  given real labeled placeholder boxes instead of words standing in for images?
- Is every word bank (or similar reference list) placed immediately before the item(s) it serves, never bundled
  at the end of the task after every item has already been answered?
- Does Unit \_B open with the real modeled language from the source before the practice tasks?
- Is Discuss It built as simultaneous small groups with 2-3 unquoted prompts, any outer-circle task folded in?
- Are both closing activities (Show What You Noticed, Wrap It Up) plain paired instructions, no self-report/check
  framing, and is the Closing Transfer Check script printed upside-down in addition to sitting after the
  response space?
- Are Background Notes translated into Good to Know boxes, informational only?
- Is the document black-and-white, em-dash-free, single self-contained HTML file, reusing
  `shared/Student_Packet_Style_Guide.md`'s base stylesheet plus only the classes documented in Section 3 above?
