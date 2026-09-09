# Generation Quality Standards (v1.10)

Shared, cross-modality quality rules for every generated lesson, homework assignment, and assessment,
plus the one output self-check every generation run applies before its own modality-specific check.
Paste this file alongside `Program_Conventions.md` and the lesson type's own prompt whenever running a
Lesson, Homework, Assessment, or Module Lesson-Plan prompt.

**Test for what belongs here:** if a rule stays true when "text" is swapped for "clip" or "scenario," it is
program-wide and lives in this file. A modality's own prompt states only what is true of its medium (a
word-count ceiling, a sourcing rule, a composition regime) and its concrete example of a rule below. No
prompt restates a rule from this file, and no prompt cites another modality's prompt for one - it points
here. A quality bug found while reviewing one modality's output is fixed here first if it passes the test
above, logged once in `shared/Changelog.md`, and only then reflected in a modality's own Changelog as a
one-line pointer.

Terms: "centerpiece" means the shared band-calibrated input every task Level works from - Reading's
anchor text, Listening/Speaking's real source clip, Writing's Scenario and Mentor Ladder. "Item" means any
discrete question, blank, match, or prompt a student answers.

## A. Task Levels

1. **Exactly the band's task Levels, no more, no fewer:** 3 for Beginner, 4 for Intermediate, Advanced,
   and Proficient, per `Program_Conventions.md` §B. One differentiated task per Level.
2. **Each task cites its own CSV row.** Every task Level's objective is pulled verbatim from that Level's
   row in `learningobjectives.csv` for the modality in question, never an invented difficulty curve or a
   paraphrase of a neighboring Level.
3. **Calibrated to its own Level's ceiling, never the Level beyond.** A borrowed Level (one lent from a
   neighboring band, see §B's band-distance invariant) still gets its full own-Level bar: an
   Intermediate-band lesson's Level 5 task reaches exactly the Level 5 ceiling, not Level 6's, and is not
   quietly simplified for being the band's "easy" or "hard" outlier either.
4. **Module verb alignment.** Every task, item, and prompt exercises the Module's own verb (Describing,
   Narrating, Explaining, Instructing, Evaluating, Arguing, Transacting, Socializing), not a neighboring
   Module's. A Describing lesson whose questions are mostly cause-and-effect has drifted into Explaining and
   is rewritten around genuine descriptive tasks. An assessment does not reproduce a source lesson's drift;
   it flags it back to the lesson.

## B. Respectful Tiers and Foundation Support

**Respectful Tiers (standing check on every differentiated task set, lesson or assessment):** every task
Level reaches the same essential understanding of the centerpiece and is equally engaging. None is "the
interesting one." The lowest task Level is never limited to rote fact-copying, scanning, or a single
copyable answer while only the higher Levels interpret, evaluate, or produce. It gets its own genuine,
simpler, more scaffolded interpretive or evaluative moment (an opinion with a word bank, a two-slot choice
with real stakes, a comparison worth making) and, on any production day, a genuine production role.

The test, applied before finalizing: would a student at the lowest task Level, having done only their own
Level's work, feel they did "the easy busywork" while everyone else did "the real thinking" or "the real
talking"? If yes, strengthen that Level's task rather than leave the imbalance in place.

**Differentiated participation in live oral work:** an easier sentence stem inside the same live, public
speaking turn is not differentiation - the demand of real-time public speech is roughly constant across a
stem's difficulty. The lowest task Level gets a different participation mode within the same protocol:
a rehearsed pair-share immediately before their turn, or a listening/tracking role with one fully prepared
line contributed at a natural pause.

**Foundation Support (below the lowest task Level):** for a student functioning below the band's own floor,
do not reuse the lowest Level's tasks at a slower pace. Provide non-verbal or minimally-verbal response
modes (matching a printed word in the packet to a printed picture or category, a two-choice circle, tracing
with a meaning check, teacher-scribed dictation) and, in oral work, a physical role (moving, holding up a word
the student wrote) rather than a spoken turn; never a card set the teacher has to make, and never a task that
needs the object in the room (D8). This is support
added on top of the lowest task Level, not a replacement for it; the lesson says where it plugs in. An
assessment for a lesson that used Foundation Support gives those students a lighter check in the same
response mode, scored as a completion checklist, not a percentage. If no lesson in scope used it, none is
invented.

## C. Item quality

Every item set, at every task Level, in every lesson, homework, or assessment:

1. **Distinct.** No item tests what another item in the same Level's set already tests under a different
   format (a matching item that duplicates a comparison a free-response item already requires, a
   fill-in-the-blank restating a fact a multiple-choice item already checked). An item count is calibrated
   for balanced time-on-task (item 5), never padded with a redundant easy item. If two items would test the
   same thing, cut one or fold it into the other.
2. **Not trivially easy for the band.** Every item requires its Level's own ceiling. Where a Level's can-do
   calls for inference, summary, evaluation, or comparison, the item is engineered so an objective format
   still requires that judgment: multiple-choice options are all plausible-sounding paraphrases with only one
   accurate to the source, matching pairs a phrase to the stance or framing it signals (not a dictionary
   definition), a blank completes a cause-and-effect or comparison statement in the source's own language.
   Nothing at any Level is answerable by surface scan, by elimination, by general knowledge, or by one
   obviously-right option against absurd alternatives.
3. **Requires the centerpiece.** Every item is answerable only with the text, clip, or scenario in front of
   the student, never from memory of the lesson or of the original story. In an assessment, that means the
   assessment's own new passage or clip, printed or played in full, not the taught one. Reasoning items cite
   specific evidence (a paragraph letter, a quoted phrase, a segment).
4. **Plausible distractors and padded banks.** Every word bank or matching list carries 1-2 extra
   already-taught words beyond what its blanks or matches need, scaled to bank size (a 3-word bank gets +1, a
   5-word bank gets +2), each a genuine near-miss drawn from the same taught pool, never a new word, and
   never the correct answer to anything else in that item - so the last blank cannot be finished by
   elimination.
5. **Time-balanced across Levels.** Lower task Levels get more, individually shorter items; higher task Levels
   get fewer, individually deeper items, sized against rough per-item time (30-60 seconds for a circle or
   point item, up to 3-5 minutes for an extended composition or analysis item), so estimated time-on-task is
   roughly even across every task Level. The lowest Level must not finish in a fraction of the highest
   Level's time. Estimate the running total before finalizing; if a Level runs over its target, cut items
   rather than note the overage. "More items" never means the same item again: a Level whose output form is
   fixed gets its extra items in different activity shapes (D10).
6. **Counted, not estimated.** Every word count, sentence count, paragraph count, and item count a ceiling
   or minimum governs is verified by an actual count, never eyeballed. A count at or near a range's floor is
   a warning sign, not an acceptable minimum.
7. **Complete inline.** Every item's instruction is stated fully in the item itself, never left as a bare
   template sentence. Any word bank, model, sentence frame, or starter box a student needs sits immediately
   before the item(s) it serves, never after and never bundled at the end of the task.
8. **Traceable.** Every item is traceable to one task Level's CSV objective and, in an assessment, to a
   specific source lesson, so a lesson can be dropped from scope without editing any other lesson's items.
9. **Never contains its own answer.** A question stem, its parenthetical, and any material printed before it
   in the same task never state, list, or quote what the item asks the student to find: no "(the scene, then
   her background, then her philosophy)" after "summarize how the segment is organized," no "(like 'success
   story')" after "find one evaluative word," no "(from a measured tone to a regretful one)" after "locate one
   tonal shift," no "(a 'quiet little cafe')" after "what she originally planned." In a two-source comparison
   item, the material printed for each source is that source's own words or a neutral paraphrase of what it
   says, never a characterization of its tone or a statement of the contrast the question asks for. A
   parenthetical in a stem is limited to a format instruction ("2-3 sentences," "circle one"), a choice menu
   in which no option is the answer, or a gloss of a word the item does not test. A frame model at a
   fixed-form Level ("It is ___." shown once as "It is soft.") models the form, not the answer, and is not
   covered by this rule. The teacher's exemplar answer belongs on an `Answer note:` line (E2), never in the
   stem.

## D. Lesson shape

Rules shared by every 2-day lesson cycle in the program:

1. **Skill Spotlight (Day 1, at or right after the activation hook).** State the lesson's actual transferable
   skill in one or two plain, student-facing sentences, separate from the topic and tied to the Module's
   verb: "today we're practicing describing a place by comparing it to somewhere familiar," not "today we're
   reading about Ciudad Perdida." The Spotlight and the Closing Transfer Check name exactly the same skill.
   The statement names the skill, never the lesson's object, text, or clip ("describe something of your own by
   comparing it," not "describe your phone case"), and it is the same sentence for every task Level: never
   "some of you will also," "if you are at," or any other tier narration. A Level's own required feature (an
   implied attitude, an essay structure) lives inside that Level's task, not in the Spotlight.
2. **Closing Transfer Check (end of Day 2).** Every student applies the spotlighted skill to something new
   (not the centerpiece), produces it out loud or on a small card, and the teacher cold-calls two or three
   pairs to share. Evidence is a demonstration, never a declaration: no thumbs-up/sideways/down, no show
   of hands, no "who feels confident?" A visible whole-class confidence vote converges on "yes" regardless
   of whether the skill transferred. Nothing is collected or graded. Where the closing input is a new text,
   clip, or prompt, it is written into the lesson, never left for the teacher to improvise.
3. **Closing Transfer Check variety.** The concrete object, person, or scenario used in the Closing Transfer
   Check differs across every lesson in the same Set, checked against the Set's other lessons before
   finalizing. Any illustrative pattern in a prompt shows the grammatical shape only; do not reuse its
   example object, or a trivial variant of it, lesson after lesson.
4. **One board-dependent moment per day.** Each day includes at least one activity for which the shared
   board is structurally necessary, with at least one of these properties: co-constructed live from student
   responses in real time; synthesizes distributed input scattered across students or task Levels into one
   visible whole no single handout contains; or persists from Day 1 and is deliberately built on in Day 2.
   Writing up target words or copying a prompt already printed on a handout is transcription, not a
   board-dependent moment. Vary which slot carries it across lessons.
5. **Teaching precedes the practice that depends on it.** Trace every practice activity back to the
   teaching content it assumes (a grammar table, a strategy explanation, a worked distinction) and confirm
   that content appears earlier in the lesson's own sequence, not later and not only modeled inside an
   example text. Both pieces being present somewhere is not enough; the bug is order. Move the teaching
   earlier, not the practice later.
6. **No adjacent repeats.** A lesson's strategy, hook, oral-output protocol, and genre or format each differ
   from the immediately preceding lesson in the Set, and a Set's first lesson from the previous Set's last
   (see `Program_Conventions.md` §F). Adjacency is the rule; full-history non-repetition is not required.
   For the task shape of a fixed-output Level, D10 applies instead: no shape twice in a lesson and no shape in
   the same slot in consecutive lessons.
7. **Oral output is scaffolded for everyone.** Any live discussion protocol supplies 2-3 distinct rotated
   prompts (never one static prompt for the whole window), explicit sentence stems per task Level inside
   each Level's own ceiling, and an explicit active task for every student not currently speaking.
8. **Self-contained: no teacher-prepared media.** A lesson, homework, or assessment never depends on the
   teacher preparing, bringing, printing, finding, or showing anything before class beyond the lesson's own
   two files (the Markdown and the packet) and, for Listening/Speaking, the cited real source. No props to
   bring, no picture cards to make, no photo to find, no "your teacher will show you." Where an objective
   calls for a picture or object prompt (CSV Levels 1-3), satisfy it in this order: (1) the student's own
   belonging (their own phone, bag, shoe); (2) an object visible in the room; (3) only when neither can
   carry the task (a Beginner label set of unrelated nouns, a "prompted by two pictures" objective), a real
   image embedded in the packet at generation time as a data-URI `<img>`, saved as an asset per Conventions
   §H and named in the lesson or assessment `.md` at the point of use (`Lesson<N>_<Slug>_Img_<Purpose>.<ext>`;
   `Set<N>_<Band>_Assessment_Img_<Purpose>.<ext>` for an assessment), so the packet step knows what to embed
   and the Index can track a missing file; the image is sourced and cited per Conventions §I in the same pass,
   recorded as a row in the Set's `Set<N>_<Band>_Image_Credits.md`, and never left for the teacher or a
   reviewer to find. The packet caption carries no credit (Style Guide §F); the register does. A hook that compares two things uses two students' belongings or two things in the room. Foundation
   Support uses printed words from the packet and the student's own drawing.
   Never print a placeholder ("[TEACHER: insert photo]", an empty picture box) and never write "the picture
   your teacher shows you." **The object is a subject, not a prop:** no task requires the belonging to be
   physically present. The student describes their own belonging from what they know of it, so never "look at
   it," "point to the part," "hold it up," "put it on your desk," or "take out your..."; a partner check asks
   the student to *say* which part a word describes, never to point to it.

**D9. Self-contained across lessons.** A lesson's tasks require nothing a student produced in an earlier
lesson except the one piece a Set carries forward (a Writing draft from position 3 on; Reading and
Listening/Speaking carry nothing). Whatever a day's tasks need (the object, a word bank, a quick plan, a model
of the form) is reprinted or rebuilt in that lesson's own packet, in that lesson's own minutes. No task says
"last time," "your planning notes," or "the example from earlier this week"; an earlier lesson's prewriting or
warm-up is rehearsal, never an input. Where a lesson offers a choice of object, the choices are printed as a
short list the student circles. The test: a student who was absent, or lost the earlier packet, can start every
task in this one.

**D10. Fixed-output Levels rotate the activity, not the output.** Where a Level's CSV row fixes its output
form (a word spelled into a frame, a pointed-to image, a single labeled word), the form stays fixed, but the
activity that produces it changes shape from phase to phase and lesson to lesson within a Set. Repeating a
fixed form is never a design choice: when a page needs filling, add a shape, not a round. The rule in full:

- The student produces the fixed form at most once per Level per lesson day (a guided round, a draft, a
  reader's addition, a Transfer Check are each one production). No task says "N times" except the single
  guided round where the CSV row itself calls for several words (one word per group, in one task).
- Every other item for that Level takes a different shape from this bank: choose the item that fits the
  object and cross out the ones that do not; fix the wrong or misspelled item in a printed example; produce
  from sound (a partner says it, the student writes or says it, then checks against the list); choose the
  better of two printed examples and say what makes it better; sort the list into its groups before
  producing; produce about a partner's object.
- No shape is met twice in one lesson, and no shape sits in the same slot in consecutive lessons of a Set.
- The fixed form is shown once per day as a model, then referred to ("the frame," "the label"), never
  re-taught in every task.
- Homework follows the same rule: one production of the form plus items in other shapes, never "more rounds."
  An assessment produces the form once per Level and never repeats an item shape for that Level.

A Level that repeats one shape has been given filler, not practice, however many items it prints. Each lesson
type's own prompt states the bank in its own terms and assigns a shape to each slot of its cycle.

## E. Style constraints for generated Markdown

1. **No em-dashes** anywhere in generated content. Use hyphens, colons, or parentheses.
2. **Teacher-facing vs student-facing.** The Markdown lesson, homework, or assessment document is the
   teacher's document: answer keys, timing, rationale, and facilitation cues belong there. The student
   packet is a regeneration of it (see `Student_Packet_Style_Guide.md` §G) and never the other way around.
   Inside a lesson or homework document, an exemplar or expected answer for an item sits on its own line
   directly under that item, labeled `**Answer note:**`, never inside the item's own sentence or
   parenthetical (C9), so the packet regeneration has a labeled line to strip rather than a sentence to
   copy. An assessment keeps its separate answer-key section as its own prompt specifies.
3. **Pacing diagram.** Each day opens with an ASCII timeline of its phases and minute allocations.
4. **Metadata line.** The document opens with `**Module:** ... | **Band:** ... | **Task Levels:** ... |
   **Version:** <Module>.<Set>.<Lesson>.<Version>` per `Program_Conventions.md` §G.
5. **Plain, instruction-first prose.** Clear instructions over decorative language; each task Level's
   vocabulary and grammar stay inside the same ceiling the source lesson used for that Level.
6. **Concrete prompts at Beginner and Intermediate.** Every student-facing prompt is a concrete action on the
   object, text, or clip with a visible product: circle, point, underline, write three words, copy the
   sentence, finish "Next time I will add ___." Never a question about the student's own process, plan, or
   feelings about the task, and never "what does the model do that yours needs to do." A self-check is a list
   of yes/no items each answered by a mark on the page. Teacher-facing staging questions belong in the
   Markdown as facilitation cues (E2) and are never printed. Advanced and Proficient may ask one bounded
   reflection question tied to a named sentence of the student's own.

## F. Shared self-check (apply before finalizing any lesson, homework, or assessment)

Run this list first, then the modality's own list. If any item fails, revise before finalizing.

1. Exactly the band's task Levels, each citing its own CSV row verbatim? (A)
2. Every task at its own Level's ceiling, borrowed Levels included, not simplified and not escalated? (A)
3. Every task and item exercising the Module's own verb, not a neighbor's? (A)
4. Respectful Tiers: does the lowest task Level get genuine interpretive or evaluative work, and on a
   production day a genuine production role? (B)
5. Live oral work: does the lowest task Level get a different participation mode, not just an easier stem,
   and is Foundation Support described where it plugs in? (B)
6. No item duplicates another item in its Level's set under a different format? (C1)
7. No item answerable by scan, elimination, general knowledge, or one obviously-right option; judgment
   Levels engineered to require the judgment? (C2)
8. Every item answerable only with the centerpiece in front of the student, never from memory? (C3)
9. Every word bank or matching list padded with 1-2 near-miss taught words? (C4)
10. Time-on-task roughly balanced across task Levels, estimated per item, over-length Levels cut? (C5)
11. Every governed count actually counted, none at or near a floor? (C6)
12. Every instruction complete inline; every bank, frame, or model placed before the items it serves? (C7)
13. Skill Spotlight on Day 1, naming the skill (not the object or text) in one sentence that is the same for
    every Level with no tier narration, and a matching Closing Transfer Check on Day 2 that demonstrates,
    never self-reports, on an object or scenario not used elsewhere in this Set? (D1-D3)
14. A genuine board-dependent moment each day? (D4)
15. Every practice activity preceded by the teaching it depends on? (D5)
16. No strategy, hook, protocol, or genre repeated from the immediately preceding lesson? (D6)
17. Oral protocol has 2-3 rotated prompts, per-Level stems, and a task for every non-speaker? (D7)
18. No em-dashes; pacing diagram per day; metadata line present with the correct version code? (E)
19. Self-contained: no prop, picture, card, or photo the teacher must prepare or show; every picture or object
    prompt met by the student's own belonging, an object in the room, or an image embedded in the packet and
    named, sourced, and cited by asset file in the `.md` with a row in the Set's `Image_Credits.md`
    (Conventions §I), and no credit text in the packet; no placeholder anywhere; and no task that needs the belonging physically present (no "look at it," "point
    to," "hold it up")? (D8)
20. Self-contained across lessons: no task needs anything a student made in an earlier lesson except the
    carried piece; every plan, bank, model, and object choice rebuilt or reprinted here? (D9)
21. Concrete prompts: at Beginner and Intermediate, every student-facing prompt is an action with a visible
    product, no process or reflection question, and the self-check is yes/no items with marks? (E6)
22. Fixed-output Levels: the form produced at most once per Level per day (the single guided round the only
    "several words" task), no activity shape met twice in one lesson or in the same slot as the previous
    lesson, the form shown once as a model, every other item in a rotated shape, and homework holding one
    production plus other shapes? (D10)
23. No stem, parenthetical, or pre-printed source material states what its item asks the student to find,
    and every exemplar answer sits on an `Answer note:` line under its item? (C9, E2)

## Changelog

**Current version: v1.10.** See `Changelog.md` in this folder.
