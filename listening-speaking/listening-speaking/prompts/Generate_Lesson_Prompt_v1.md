# Listening/Speaking Lesson Generation Prompt (v1)

**Lesson type:** this prompt generates a **Listening/Speaking Lesson** - a fixed 2-day cycle (Day 1 Listening,
Day 2 Speaking) built around one shared real-world audio or video source (a talk, interview, news segment,
podcast, or similar), differentiated into band-scoped task Levels. It is the Listening/Speaking counterpart to
the Passage Reading Lesson (a 2-day cycle around one invented anchor text), matching it in real class-day
length. Unlike Passage Reading, the two days here are not interchangeable: Day 1 builds a comprehension
performance around the real source, Day 2 builds a production performance modeled on it, mirroring
`learningobjectives.csv`'s own pairing of one Listening can-do with one Speaking can-do at every Level.

This is a first draft (v1), written the same way the Passage Reading prompt started: expect several rounds of
refinement once real lessons are generated against it and something doesn't fit a real classroom. Treat every
number below (runtimes, day count, phase minutes) as a reasoned starting point, not a fixed constant.

**Current version: v1.** Section 0's calibration and the day-by-day structure below reflect several corrections
made after reviewing real generated lessons; see `Changelog.md` for the history. Operational rules those
corrections put in place, still in force:

- Section 0.2's runtime ranges are a soft target for found sources, not a hard ceiling like Passage Reading's
  word counts: a source running somewhat past its band's range is a much smaller problem than an off-ceiling
  anchor text, since the source's own pace and register don't change. Flag the deviation in the self-check and
  keep the source if it's otherwise a strong fit.
- The Day 4 (Phase 5) Listening Closing Transfer Check must use an actual short invented script the teacher
  reads aloud, not an unspecified "new clip" left to improvisation; students do not see the script until after
  they've responded.
- A fixed-frame listening extraction item (the lowest task Level's frame-style task) needs a complete,
  self-contained instruction stated inline with the item - what the student listens for and what they fill in -
  not a bare template sentence. Add a separate unlabeled sentence-frame box only when the task also has a
  genuine speak-it-aloud step to anchor it to.
- Generate the .md lesson and its student-facing .html packet back-to-back, as one workflow action: run this
  prompt to produce the full teacher-facing .md, then immediately run the Student Print Formatting Prompt
  against that completed .md. The .md is the single source of truth; the .html is always a regeneration from it,
  never independently hand-edited for anything that changes lesson content (a student-facing wording or
  vocabulary change goes into the .md first, then the .html is regenerated) - the only edits made directly to
  the .html are pure print/formatting-layer fixes that don't change lesson content.
- Item counts per task Level must be calibrated so time-on-task is roughly balanced across all task Levels, not
  just item difficulty: give lower task Levels more, individually shorter items and higher task Levels fewer,
  individually deeper items. Rough time-per-item to plan against: a circle/point item is 30-60 seconds; a
  fill-in-the-blank or two-slot frame is 45-90 seconds; a freeform 2-3 sentence response is 2-3 minutes; an
  extended multi-sentence composition or analysis item is 3-5 minutes. Add or trim items per Level until
  estimated totals land in a similar range, applied when writing the Day 1 Phase 4, Day 2 Phase 2, and any other
  differentiated item set.

Scope note: this prompt generates the core Listening/Speaking Lesson only - one real source, one 2-day cycle.
A planned, not-yet-written extension will add an optional second source plus a synthesis/group-presentation
project (mirroring the content sample's Part 2 and Put It Together sections) as an add-on after a core lesson is
complete, the same way the TOEFL Track Extension sits on top of a completed Passage Reading lesson rather than
inside it. Nothing below generates that extension.

Adopt the same Content-Based Instruction (CBI) and Task-Based Language Teaching (TBLT) framework as the
Passage Reading program: listening and speaking are tools to explore real ideas and build critical thinking, with
language acquisition happening through meaningful communication, not isolated drills.

---

## SECTION 0: SOURCE SELECTION AND CALIBRATION (READ AND APPLY BEFORE SEARCHING FOR A SOURCE)

### 0.1 How to find the target band and task Levels

Bands and Levels are the same universal 1-8 scale used across the whole program (this is not a separate scale
for Listening/Speaking):

| Band         | Levels | CEFR   |
| ------------ | ------ | ------ |
| Beginner     | 1-2    | A1-A2  |
| Intermediate | 3-4    | B1-B1+ |
| Advanced     | 5-6    | B2-B2+ |
| Proficient   | 7-8    | C1-C2  |

**The real source is calibrated to the band's LOWER level**, exactly as Passage Reading calibrates its anchor text
(Level 3 for Intermediate, Level 5 for Advanced, Level 1 for Beginner, Level 7 for Proficient). This single Level
governs Section 0.2's runtime, pace, and register ceiling for the whole lesson. Every student in the room
listens to or watches the same source; only the task built on top of it differs by Level.

Always pull the actual Listening/Speaking-modality Learning Objective for the band's lower level and the target
Module from `learningobjectives.csv` before searching for a source: filter by Level = the band's lower level,
Modality = Listening/Speaking, Module = the requested module. Quote the row's Description verbatim - it
contains both a Listening can-do and a Speaking can-do in one statement - and use both halves: the Listening
half governs what the comprehension tasks (Days 1-4) must actually ask for, the Speaking half governs what the
production tasks (Days 5-8) must actually elicit.

**Task Levels by band:** identical table and identical reasoning to Passage Reading Section 0.1 (reused wholesale,
since the Level scale is universal, not modality-specific):

| Band         | Task Levels | Count |
| ------------ | ----------- | ----- |
| Beginner     | 1, 2, 3     | 3     |
| Intermediate | 2, 3, 4, 5  | 4     |
| Advanced     | 4, 5, 6, 7  | 4     |
| Proficient   | 5, 6, 7, 8  | 4     |

The band-distance invariant applies unchanged: every task Level is at most one band away from the source's own
calibrated band, which is what makes it safe to share one source across every task Level in the room.

**How to specify a lesson request:** every generation request must name at minimum a Module and a Band (e.g.
"Advanced band, Module 2: Narrating"); a topic direction is optional but recommended. Without a Module/Band
pair, the CSV lookup above cannot happen and there is no basis for calibration: do not search for a source until
both are known.

The Module objective governs what kind of source to look for, not just its difficulty. Do not default to "any TED
Talk" regardless of Module:

- **Module 1 (Describing):** look for a source where a speaker describes a person, place, or object (a walking
  tour, a home/studio tour, a product demo, a "meet my neighborhood" vlog) - not a source built around
  explaining a process or arguing a position.
- **Module 2 (Narrating):** a personal-story talk, an oral-history clip, a storytelling-podcast episode.
- **Module 3 (Explaining):** a how-something-works explainer, a science/history short documentary, a
  process-focused segment.
- **Module 4 (Instructing):** a tutorial, a how-to video, a recipe or skill demonstration with sequential steps.
- **Module 5 (Evaluating):** a review (product, restaurant, film, place), a "worth it or not" segment.
- **Module 6 (Arguing):** an opinion talk, a debate clip, a persuasive TED Talk, a panel disagreement.
- **Module 7 (Transacting):** a customer-service call/roleplay recording, a negotiation or transaction scenario,
  a service-encounter clip.
- **Module 8 (Socializing):** a casual conversation, a friends/family vlog, a social small-talk scene.
  Before finalizing a source, check its actual content against the CSV Description's verbs, the same way Passage
  Reading checks comprehension questions against the pulled objective. A source can drift into a neighboring
  Module's territory (a "review" video that is really a narrated personal story); if it does, keep searching rather
  than forcing comprehension tasks that don't match what the source actually does.

### 0.2 Source runtime, pace, and register ceiling by level

Unlike Passage Reading, this program does not write the source text - it finds real, publicly available audio or
video. These targets describe what to search for and verify, not what to author. **A source must have a genuine,
findable transcript or official captions** (the platform's own captions, a published transcript page, or a
well-established auto-caption track that can be checked against the audio) - do not select a source with no way
to verify what is actually said, since every task below is built from the real transcript.

**Level 1 (A1, Beginner floor)**

- Runtime: 30 seconds - 2 minutes
- Source type: graded-listening clips for absolute beginners, simple labeled object/routine videos, a slow
  deliberate read-aloud
- Pace/register: very slow, deliberate enunciation; single-clause sentences; concrete, high-frequency vocabulary
  only; strong visual support (captions or clear on-screen matching visuals) expected
- Example platforms to search: BBC Learning English (beginner segments), VOA Learning English (Level 1),
  elementary read-aloud channels
  **Level 2 (A2, Beginner ceiling; Intermediate's extension-down)**
- Runtime: 1-3 minutes
- Source type: short graded-listening segments, simple vlogs with clear visual support
- Pace/register: slow to moderate, clear enunciation; short simple sentences, minimal subordination; concrete
  high-frequency vocabulary, 3-5 unfamiliar words max
- Example platforms: BBC Learning English, VOA Learning English (Level 1-2), EnglishClass101 beginner clips
  **Level 3 (B1, Intermediate floor)**
- Runtime: 2-4 minutes
- Source type: a graded-for-learners news segment, a TED-Ed short, a simple vlog or human-interest clip
- Pace/register: near-natural but clear pace; simple past/present as the backbone, light subordination; a real
  topic, not a classroom-invented scenario
- Example platforms: VOA Learning English (Level 2/Intermediate), TED-Ed, Simple English News Daily
  **Level 4 (B1+, Intermediate ceiling)**
- Runtime: 3-5 minutes
- Source type: a longer human-interest news segment, a short documentary excerpt, a moderately-paced podcast
  clip
- Pace/register: natural pace with clear articulation; everyday abstract vocabulary appears; no dense
  academic register
- Example platforms: VOA Learning English (Level 3), National Geographic Kids/Short Docs, local news
  human-interest segments
  **Level 5 (B2, Advanced floor)**
- Runtime: 5-8 minutes
- Source type: a standard (not simplified-for-learners) TED Talk, an NPR or BBC feature segment, an interview
  clip
- Pace/register: natural native pace; mixed past/present, natural connectors, some idiomatic language; not yet
  dense academic register
- Example platforms: TED.com (standard talks, shorter end), NPR News, BBC News features
  **Level 6 (B2+, Advanced ceiling)**
- Runtime: 7-12 minutes
- Source type: a standard TED Talk, a documentary excerpt, a longer interview or podcast segment
- Pace/register: full natural pace, idiomatic language and register shifts present, not yet specialist/academic
  jargon-dense
- Example platforms: TED.com, PBS/National Geographic documentary excerpts, mainstream podcasts
  **Level 7 (C1, Proficient floor)**
- Runtime: 10-18 minutes
- Source type: a full unedited TED Talk, a long-form interview (NPR Fresh Air-style), a university lecture excerpt
- Pace/register: full natural or fast pace, idiomatic and some academic register, may include audience
  reaction/laughter or cross-talk
- Example platforms: TED.com (full talks), NPR long-form interview shows, OpenCourseWare lecture excerpts
  **Level 8 (C2, Proficient ceiling)**
- Runtime: 15-25+ minutes, or a multi-speaker panel/debate of similar total length
- Source type: a dense academic talk or lecture, a panel discussion or formal debate, a long-form journalism
  interview with digressive or evasive speech
- Pace/register: fast, idiomatic, possibly multiple speakers/accents/cross-talk; no register ceiling
- Example platforms: university lecture archives, Intelligence Squared-style debate programs, long-form
  interview podcasts

### 0.3 Sourcing rules (verification, citation, fair use)

1. **Never fabricate a source.** Do not invent a video title, speaker name, platform, publish date, or transcript
   excerpt. If live web search is available, use it to find and confirm a real source before writing anything else.
   If a suitable source genuinely cannot be found for the exact Module/Band/topic combination, broaden the topic
   within the same Module rather than inventing one.
2. **Cite it in full at the top of the lesson:** title, speaker/creator, platform, URL, approximate runtime, and
   publish date if known. This citation block is what lets the teacher actually pull up and play the source - it is
   not optional front matter.
3. **Confirm the transcript before building tasks on it.** Quote or closely paraphrase only what the real
   transcript/captions actually say. Do not guess at wording from a title or description alone.
4. **Fair use ceiling:** never reproduce the source's full transcript in the lesson document. Direct quotation from
   the transcript is limited to short excerpts (one to two sentences at a time) used for a specific task (a
   vocabulary-in-context item, a "listen for this line" cue, a quoted example of a speaking-skill phrase). Everywhere
   else, paraphrase or summarize in your own words and point the teacher/students to the real timestamp to hear
   it themselves.
5. **Timestamp markers, not paragraph letters.** Since there is no printed anchor text to letter (Passage
   Reading's Section 0.9, Part A), every listening/watching task instead cites an approximate timestamp range
   (e.g., "[2:15-3:40]") so the teacher can cue playback precisely. Use timestamps consistently everywhere a
   segment is referenced (Listen for Main Ideas, Listen for Details, the Listening Skill segment, the Speaking Skill
   segment).
6. **Background Note (footnote equivalent).** When the source names a real person, place, event, or reference
   that (a) is unlikely to be common knowledge at the target band and (b) the source itself doesn't explain, add a
   short, sourced "Background Note" callout (one or two plain sentences, capped at the level's own register
   ceiling) rather than leaving it unexplained or over-explaining everything. Keep it occasional (1-3 per lesson),
   informational only - never the basis of a comprehension question.

---

## Unit Architecture: 2-Day Source Cycle Model

**Corrected 2026-09-03, after user clarification.** Every unit of instruction spans **two class periods** (75
minutes each) built around one shared real source, calibrated per Section 0: **Day 1 is Unit A (Listening)**,
**Day 2 is Unit B (Speaking)** - this pairing is fixed across every lesson in the program. This replaces an
earlier 8-day version of this section, which spread the same content across four days per unit (300 minutes)
instead of one. The earlier version was wrong: a module's real day budget is 8 class periods total, which is 4
lessons at 2 days each, not 8 lessons at 8 days each - see the Module Lesson Plan's corrected day-count note.
The content below is not a trimmed-down version of the old 4-day structure; it is the same scope of activity
the student packets already reflect (the packets were always the correctly-sized, single-sitting version - the
old .md was the part that was wrong), reorganized to fit one real 75-minute period per unit.

**2-DAY SOURCE CYCLE OVERVIEW (approx. 150 MIN TOTAL)**

```
DAY 1 (Unit A - Listening)  |--Hook, Vocab & Purpose (20)--|--Watch & Notes (15)--|--Skill Instr. (10)--|--Task (20)--|--Transfer Check (10)--|
DAY 2 (Unit B - Speaking)   |--Skill Spotlight (15)--|--Differentiated Practice (20)--|--Pronunciation (10)--|--Oral Output (20)--|--Transfer Check & Wrap (10)--|
```

### DAY 1: Unit A - Listening (75 min)

_Phase 1: Hook, Good to Know & Vocabulary (20 min)_

- Open with a real-world hook tied to the source's actual topic (rotate hook types per Section 0.4/the approved
  plan) - not an abstract framing above the band's register.
- **Listening Skill Spotlight:** name the lesson's listening strategy in one or two plain, student-facing
  sentences (e.g., "Today we're practicing listening for examples - noticing when a speaker gives a specific
  case to support a bigger idea"). This is the exact skill this day's Closing Transfer Check asks students to
  reproduce.
- Present the full source citation (Section 0.3, item 2) and any Background Note(s) (Section 0.3, item 6; 1-3,
  brief, informational only) together, up front.
- Pre-teach 4-6 target words/phrases pulled from the real transcript (never invented), presented in context
  sentences paraphrased from what the source actually says. Gloss idioms per the transparency rule (transparent
  chunks lightly glossed from Level 2 up; opaque idioms get an explicit gloss or guided confirmation at every
  level).
  _Phase 2: Watch & Listening Notes (15 min)_
- Play the full source once (or, for Proficient-length sources, the first half with a clear timestamp cutoff).
- Students fill in a shared note-taking organizer while watching, matched to the Module's own organizer type
  (comparison T-chart for Describing, sequence chain for Narrating/Instructing, cause-and-effect chain for
  Explaining, criteria/verdict grid for Evaluating, two-column claims tracker for Arguing, and the equivalent
  for Transacting/Socializing).
- Set a differentiated listening purpose per task Level before playback (the lowest task Level gets a narrower,
  concrete listening-for question; the highest gets an open interpretive one).
  _Phase 3: Listening Skill Instruction (10 min)_
- Teach the named listening skill directly (rotate per Section 0.4 below) using a real, timestamped excerpt from
  the source as the model. Brief guided practice applying the skill to a second short excerpt.
  _Phase 4: Differentiated Listening Task, Choose One Level (20 min)_
- One merged, star-rated task per task Level - combine what main-idea, detail, and critical-thinking items would
  cover into a single sequential task per Level (the same merge principle the Student Print Formatting Prompt
  already applies for print; write it this way from the start rather than writing three separate un-merged
  passes and merging them later). The lowest task Level gets more, shorter items; the highest gets fewer, deeper
  items, per the balanced-duration rule above.
- **Board-dependent moment:** students who worked on different task Levels briefly compare and report into the
  shared notes organizer from Phase 2, so the completed picture exists only once multiple Levels have
  contributed.
- **Respectful Tiers check:** the lowest task Level's task must include a genuine, simplified interpretive
  component, not fact-retrieval alone.
  _Phase 5: Listening Closing Transfer Check (10 min)_
- **Default mechanism: a short, invented, teacher-read-aloud script - written into the lesson, not sourced, and
  not left to the teacher to improvise.** Write a short (roughly 60-90 word) original paragraph on a topic
  unrelated to the lesson's own source, recycling most of the lesson's target vocabulary in the new context.
  This script is invented, not found: its purpose is controlled vocabulary recycling and a clean skill-transfer
  test, not authentic new exposure.
- The teacher reads the script aloud. **Students do not read it themselves first** - print it in the student
  packet only after the response space, under a clear "don't read ahead" instruction (see the Student Print
  Formatting Prompt's matching section; also consider printing it upside-down as an added deterrent, per that
  prompt's Section 2.8).
- Students apply the Phase 1 Listening Skill Spotlight to what they heard (state the gist, predict what comes
  next, retell the order, etc. - whatever the specific named skill is), out loud, to a partner. The teacher
  cold-calls two or three pairs to share. Demonstration, not a self-report. After sharing, students may read the
  script themselves to check.

### DAY 2: Unit B - Speaking (75 min)

_Phase 1: Speaking Skill Spotlight (15 min)_

- Identify a moment where the real speaker(s) in the source actually use the target functional language (e.g.,
  agreeing/disagreeing, giving an example, sequencing steps, hedging an opinion, making a comparison) - the
  skill is drawn from authentic input, not invented in isolation, wherever the source allows it. Where a source
  genuinely does not contain the target functional language (a narrated profile with no dialogue, for example),
  ground the spotlight in the source's real, verified situational context instead and flag this openly in the
  lesson's self-check as a deviation, rather than quoting invented dialogue as if it were real. Name the skill in
  plain, student-facing language. This is the exact skill this day's Closing Transfer Check asks students to
  reproduce.
  _Phase 2: Differentiated Speaking Practice, Choose One Level (20 min)_
- One merged, star-rated production task per task Level (a fixed sentence frame for the lowest task Level; an
  open, register-appropriate production for the highest), matching the Student Print Formatting Prompt's
  Practice It tasks.
  _Phase 3: Pronunciation Mini-Focus (10 min)_
- Teach one pronunciation feature actually audible in the real source (content-word stress, thought-group
  pausing, linking, rising/falling intonation, contrastive stress) using the source's own audio as the model,
  not an invented example sentence. Students mark a short excerpt for the feature, check against the real audio,
  then apply it in brief paired rehearsal of their Phase 2 language.
  _Phase 4: Structured Oral Output (20 min)_
- Run one rotating discussion protocol (Town Hall, Fishbowl, Concentric Circles, Jigsaw - vary across cycles per
  Section 0.4) built on the source's actual topic, applying both the Module's functional skill and the day's
  speaking/pronunciation focus.
- **Differentiated participation:** the lowest task Level gets a genuinely different participation mode (a
  rehearsed pair-share before the public round, or a listening/tracking role with one prepared line), not just
  an easier stem inside the same live turn. Foundation Support (below the lowest task Level): non-verbal or
  minimally-verbal roles throughout.
- **Board-dependent moment:** a running board record of claims/points as they are actually spoken during the
  protocol, feeding the Closing Transfer Check.
  _Phase 5: Speaking Closing Transfer Check & Wrap (10 min)_
- Every student produces, in pairs and out loud, one new instance of the Phase 1 Speaking Skill Spotlight
  applied to a prompt other than the source's own topic. The teacher cold-calls two or three pairs to share.
  Demonstration, not self-report.
- **Respectful Tiers check:** across the whole cycle, does the lowest task Level get a genuine
  interpretive/evaluative task at some point (Day 1) and a genuine production role (Day 2), not fact-retrieval
  and silent participation only?
- Brief whole-class reflection on the cycle's topic and skills. If the optional Part 2/presentation-project
  extension (see Scope note above) is being used for this class, preview it here.

---

## 0.4 Listening strategy and speaking-skill rotation (starter bank)

Rotate genuinely across cycles; do not default to the same one or two entries. This bank is a starting point for
v1 and should grow with use, the way Passage Reading's genre bank did across its own versions.

**Listening strategies (Day 1, Phases 3-5 focus):** Listen for Main Ideas/Gist, Recognize Examples, Listen for
Signposting/Discourse Markers, Listen for Sequence Markers, Listen for Stated vs. Implied Opinion, Listen for
Cause-and-Effect Language, Predict from Context Before Confirming, Listen for Contrastive/Concession Language
("but," "even though," "on the other hand").

**Note-taking structures (Day 1, Phase 2):** Outline (idea + indented examples), T-chart/Venn diagram, sequence
chain, cause-and-effect chain, two-column claims tracker, criteria/verdict grid - matched to the Module per Day
1, Phase 2 above.

**Speaking skills (Day 2, Phases 1-2 focus):** Agree/Disagree phrases, Giving Examples phrases, Asking for
Clarification, Sequencing Language, Hedging an Opinion, Making Comparisons, Turn-Taking/Interrupting
Politely, Summarizing What Someone Said.

**Pronunciation features (Day 2, Phase 3):** Stress content words, thought-group pausing, linking between words,
rising/falling intonation for questions vs. statements, contrastive stress, reduced forms in fast natural speech
(Advanced/Proficient only).

**Oral output protocols (Day 2, Phase 4):** Town Hall, Fishbowl, Concentric Circles/Speed-Dating, Jigsaw Expert
Panels - same bank as Passage Reading, vary across cycles.

Do not repeat the same listening strategy, speaking skill, or oral output protocol in two consecutive lessons
within a module (adjacency rule, same as Passage Reading).

---

## Style & Formatting Constraints

- **Pacing Diagrams:** include a visual ASCII timeline at the start of each day (see the 2-Day overview diagram
  above for the format).
- **No Em-Dashes:** never use em-dashes anywhere in generated content. Use hyphens, colons, or parentheses.
- **Oral Focus:** prioritize spoken interaction over written grammar drills, consistent with Passage Reading.
- **Citation block first:** every lesson opens with the Section 0.3 citation block, before any activity content.
- **Timestamps, not paragraph letters:** every segment reference uses a timestamp range, never a paragraph or
  line number (there is no printed anchor text to letter).

---

## 0.5 Self-check before finalizing (apply to every generated lesson)

1. Is the source real and verifiable (not fabricated), with a genuine transcript/captions confirmed before any task
   was built on it? Is the full citation block present at the top?
2. Does the source's runtime, pace, and register match Section 0.2's ceiling for the band's lower level?
3. Does the source's actual content match the Module's verb (Describing/Narrating/Explaining/etc.), per Section
   0.1, rather than drifting into a neighboring Module?
4. Does the lesson include exactly the right number of task Levels for its band (3 Beginner, 4
   Intermediate/Advanced/Proficient), each one citing the correct CSV Level's Listening/Speaking objective -
   using the Listening half for Day 1 tasks and the Speaking half for Day 2 tasks?
5. Are the 4-6 target words/phrases actually present in the real transcript (never invented), correctly glossed,
   with any naturally-occurring opaque idiom glossed regardless of band?
6. Does any direct quotation from the transcript stay within the fair-use ceiling (one to two sentences at a time),
   with the full transcript never reproduced?
7. Is every listen-for-X or watch-for-X task tagged with a consistent timestamp range?
8. Are Background Notes (if any) occasional (1-3), factual, sourced, and informational only - never the basis of a
   comprehension question?
9. Does each day include a genuine board-dependent moment (co-constructed live or synthesizing distributed
   input), not a restatement of already-printed content?
10. Does Day 1 Phase 1 name a specific listening skill (Skill Spotlight), and does Day 1 Phase 5's Listening
    Closing Transfer Check have every student demonstrate that exact skill, out loud, with cold-calling (not a
    self-report/confidence vote)? Is the "new" input a teacher-delivered live description by default (not an
    unspecified "clip" the teacher has to somehow produce)?
11. Does Day 2 Phase 1 name a specific speaking skill drawn from the real source's own speakers (or, where
    flagged as unavailable, grounded honestly in the source's real context), and does Day 2 Phase 5's Speaking
    Closing Transfer Check have every student demonstrate that exact skill on a new prompt, out loud, with
    cold-calling?
12. Does Day 2 Phase 4's oral output protocol give the lowest task Level a genuinely different participation mode
    (not just an easier stem), with Foundation Support described for a student below the lowest task Level's
    floor?
13. Respectful Tiers: across the whole cycle, does the lowest task Level get a genuine interpretive/evaluative
    task at some point (Day 1) and a genuine production role (Day 2), not fact-retrieval and silent participation
    only?
14. Is the listening strategy, speaking skill, note-taking structure, and oral output protocol each different from
    the immediately preceding lesson in this module (no adjacent repeats)?
15. No em-dashes anywhere; ASCII pacing diagram present for each day.
16. Item-pacing check: do Day 1 Phase 4 and Day 2 Phase 2's differentiated item counts give lower task
    Levels more (but shorter) items and higher task Levels fewer (but deeper) items, so estimated time-on-task
    is roughly balanced across all task Levels rather than the lowest Level finishing in a fraction of the
    highest Level's time?
    If a lesson fails any check, revise it before finalizing. Do not build Day 3-8 tasks on a source that failed the
    Section 0.1-0.3 checks in step 1-3 above.
