# Listening/Speaking Student Print Formatting Prompt (v2.0)

Companion to the Listening/Speaking Lesson Generation Prompt. Takes one completed lesson (both days) and produces a
single, print-ready, black-and-white student handout: one self-contained HTML document with every teacher-facing
pedagogical term translated into plain instructions, adapted for a lesson type where the "text" is a real
audio/video source the class plays together, not a printed passage.

**Paste bundle:** run this prompt with `shared/Student_Packet_Style_Guide.md` alongside it. The Style Guide holds
every rule shared by all packet prompts: format constraints and the base stylesheet (§A-§C), the universal
teacher-to-student translations (§E), star ratings and lettered Tasks (§F), the rule that the packet is always a
regeneration of the Markdown (§G), this modality's delta classes (§H.1), and the shared packet self-check (§I).
This prompt states only what is specific to a Listening/Speaking packet. A TOEFL Track Tier variant's rendering
is in `Generate_TOEFL_Track_Tier_Prompt_*.md` Section 2, applied on top of this prompt.

**Current version: v2.0.** For the dated version history and the reasoning behind each change, see `Changelog.md`.

**Input:** the completed lesson in full: the citation block, target vocabulary, both Skill Spotlights, the
differentiated Day 1 listening tasks and Day 2 speaking tasks, Background Notes, the note-taking organizer, the
oral-output protocol's prompts and stems, the pronunciation focus, and both Closing Transfer Checks. Pull all
content from the lesson; invent nothing; drop no task Level. The transcript file is never read into the packet.
Student version only.

## SECTION 1: LISTENING/SPEAKING-SPECIFIC TRANSLATIONS

Style Guide §E's rows apply. Add these:

| Teacher-facing term | Student-facing translation |
|---|---|
| Listening Skill Spotlight / Speaking Skill Spotlight | Each part's plain can-do objective statement (2.2). |
| Listening Closing Transfer Check / Speaking Closing Transfer Check | Plain closing activities (2.8, 2.12). |
| Background Note | A short "Good to Know" box (2.5). |
| Timestamp/segment markers (`[Segment N: ...]`) | Shown to students in plain form (2.3): a segment cue is a real navigational aid for finding a place in a recording during replay, unlike a paragraph letter. |
| "watch" vs. "listen" | Matched to the source's real, confirmed media type everywhere (2.3); never default to "watch"/"video." |

## SECTION 2: DOCUMENT STRUCTURE

### 2.1 One combined document, two parts

One shared document in two parts mirroring the lesson's halves: **Unit _A** (Listening) and **Unit _B**
(Speaking), each folded into its own section heading ("Unit 1A: New Bakery, Old Baking Method"), never "Day 1" or
"Day 2." Each part restarts its task lettering. The masthead carries the modality label `Listening & Speaking`
(Style Guide §B, §I item 5).

### 2.2 Objective statements

Immediately after each part's heading, that part's objective as a can-do statement from the Listening Skill
Spotlight (Unit _A) or Speaking Skill Spotlight (Unit _B), phrased as something the student can picture doing.

### 2.3 What You'll Watch/Listen To

A short `.citebox` citation: title, one clear sentence describing what it is about, and platform, without
academic-citation jargon (no runtime, no editor credits). Example: "You'll watch: 'New Bakery, Old Baking
Method,' a video from VOA Learning English about a bakery in Washington, D.C. that grinds its own grain." Never
add a line inviting students to ask their teacher for the link; students always have direct access to the media.

**Placement:** immediately before the point where students actually begin watching or listening (typically right
before the Listening Notes organizer), not at the top of the unit beside the objective.

**Media-type wording:** if the citebox says "You'll listen to," every related instruction (the Before You
Watch/Listen heading, the organizer's instruction line, any task text) says "listen" too, and vice versa for a
confirmed video. Do not add "(and watch again)" / "(and listen again)"; replay is implied.

**Segment cues:** carry the plain segment name into any task that references a specific part of the recording
("Listen again to the part where Bethony talks about the taste"), not bracket notation.

**Never name a source component the packet has not introduced.** A source page may carry a video plus its own
on-page text version used as the transcript. If the citebox tells students about one component ("You'll watch
[the video]"), every quote anywhere in the packet is attributed to that same thing ("In the video, ..."), never a
second label ("the article," "the transcript") never introduced to students. If the packet genuinely wants
students to know about a second component, introduce it in the citebox first.

### 2.4 Numbering and placement

Style Guide §F: every standalone question (Before You Watch/Listen, Show What You Noticed, any prompt with a
response line) is numbered via `.qitem`; fillable organizers are referenced by name, not numbered; word banks and
reference lists sit immediately before the items they serve; a starter/frame box renders before any instruction
that refers back to it.

### 2.5 Good to Know boxes

Translate each Background Note into a short "Good to Know" `.spotlight-box`. Place all of a unit's Good to Know
boxes together at the very beginning of Unit _A, immediately after the objective statement, before Before You
Watch/Listen and well before the citebox, so context is front-loaded before any activity. Keep the source lesson's
count (1-3); informational only.

### 2.6 Listening Notes organizer

Print the source lesson's Day 1 Phase 2 note-taking structure as a simple fillable `.notes-table` with the lesson's
own row labels (a two-column table for a comparison chart; the equivalent simple structure for a sequence chain,
cause-and-effect chain, criteria grid, or claims tracker), positioned before the star-rated listening tasks so
students fill it in while the source plays. "While you watch, fill in..." or "While you listen, fill in..." is the
whole instruction.

### 2.7 Star-rated listening tasks

Merge the lesson's Day 1 Phase 4 differentiated items into one combined star-rated Task per Level (A = ★ through
D = ★★★★), sequential questions, each Level's own items. Style Guide §F governs stars, the share instruction,
lettering, multiple-choice layout (options inline, one `.task-instr` line at the top of the block), picture items
(real `.pic-options` placeholders), and word-bank placement. Two Listening/Speaking specifics:

- **Fixed-frame items need a complete, self-contained instruction.** Where the lowest task Level is a fixed-frame
  extraction ("It is ___ and ___."), state inline what the student listens for and what goes in the blanks (with
  a word bank if needed). Do not add a separate unlabeled frame box repeating the frame; reserve a standalone
  frame/"starter" box (2.10) for a task with a genuine speak-it-aloud step.
- **Multi-source tasks (Level 7, when the top task compares two real sources):** present both sources' material
  inside that task block in a labeled two-part "compare" layout (a plain source label above each short excerpt),
  each excerpt within the lesson's fair-use ceiling, the comparison question after both. A later Discuss It
  prompt that references the comparison points back to this Task by name rather than re-citing the sources.

### 2.8 Show What You Noticed (Listening close)

Translate the Listening Closing Transfer Check into a plain paired activity around the lesson's read-aloud
script: tell students their teacher will read a short paragraph aloud, they should not read it themselves yet,
and after saying the main idea to a partner (with a numbered response space) they may read it to check. Print
the script in a `.refresher.refresher-noline.upside-down` block positioned AFTER the response space under its own
"Check What You Heard" label, with an explicit instruction that it is printed upside-down on purpose and not to
turn the page around until they have said and written their answer. No self-report framing; never named a check.

### 2.9 Learn the Phrase (Speaking Skill Spotlight)

Open Unit _B with the real modeled language from the source (the actual phrase(s) the speaker used) in a short
"Learn the Phrase" `.spotlight-box`, with the sentence frames the lesson teaches **inside the same box**, not as a
separate list below it. Invent no modeled language beyond what the lesson quotes.

### 2.10 Star-rated speaking tasks (Practice It)

Same merge and star principle as 2.7, applied to the Day 2 Phase 2 production tasks, with any pronunciation
marking exercise folded in as a short bonus line under the relevant task. The same multiple-choice,
picture-placeholder, and placement rules apply; a fixed-frame speaking item with picture cues needs real
placeholder boxes. A standalone frame/"starter" box, where a speak-it-aloud step justifies one, renders before any
instruction that refers to it.

### 2.11 Discuss It

The oral-output protocol's 2-3 rotated prompts as simultaneous small groups (Style Guide §E), each prompt numbered
via `.qitem`, unquoted, regular weight, any outer-circle or tracking task folded into a prompt, plus star-coded
stems (stems only, Style Guide §F).

### 2.12 Wrap It Up (Speaking close)

Translate the Speaking Closing Transfer Check into a plain paired closing activity. **Closing-loop headings stay
jargon-free:** if Phase 5 revisits a named Phase 1 organizer to close the loop, the heading says "Finish the
Chart," never the protocol or organizer's name ("K-W-L").

### 2.13 Callout boxes, answer space, rules

Style Guide §F and §I: callouts reserved for genuine spotlights (Good to Know, Learn the Phrase, the citebox, an
idiom Phrase Spotlight rendered the same way as Reading's, `.idiom-tag` on transparent chunks only); word banks
get the dashed-rule exception only; answer space matched to expected length; no decorative rules.

## SECTION 3: FORMAT AND STYLE CONSTRAINTS

Style Guide §A-§D, plus this modality's delta classes in §H.1 (`.citebox`, `.notes-table`, `.upside-down`,
`.task-instr`, `.pic-options`/`.pic-option`, `.match-list`/`.match-row`, `.qitem`, `.mc-list`/`.mc-letter`,
`.time-list`, `.reader-copy`/`.reader-warn`). Add `.refresher` and `.notes-table` to the packet's `@media print`
page-break-avoid list.

## SECTION 4: WORKFLOW

Style Guide §G: run immediately after the lesson `.md` is complete, as the third artifact of the lesson's
generation pass; the `.md` is the source of truth; deliver for review; content changes go into the `.md` and
regenerate.

## SECTION 5: SELF-CHECK BEFORE FINALIZING

Run `shared/Student_Packet_Style_Guide.md` §I first. Then:

1. Two parts (Unit _A / Unit _B), each with its own objective and restarted lettering; masthead label
   `Listening & Speaking` (2.1, 2.2)?
2. Good to Know boxes together at the very start of Unit _A, right after the objective (2.5)?
3. Citebox right before the point students begin watching or listening, not at the top; no "ask your teacher for
   the link"; watch/listen wording matched to the real media type throughout; no second source component named
   that the citebox never introduced (2.3)?
4. Fillable Listening Notes organizer before the star-rated listening tasks (2.6)?
5. Fixed-frame items with a complete inline instruction; multi-source Level 7 task in a labeled compare layout
   within fair use (2.7)?
6. Show What You Noticed: response space first, then the script upside-down under "Check What You Heard" with the
   don't-turn-the-page instruction (2.8)?
7. Unit _B opens with Learn the Phrase carrying the real modeled language and its frames in one box (2.9)?
8. Discuss It prompts numbered via `.qitem`, unquoted, outer-circle task folded in (2.11)?
9. Closing-loop heading in plain language, no organizer or protocol name (2.12)?
10. `.refresher`/`.notes-table` in the print page-break list; only §H.1 classes added (Section 3)?
