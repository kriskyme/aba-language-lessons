# Listening/Speaking Lesson Generation Prompt (v2.5)

**Lesson type:** a **Listening/Speaking Lesson** is a fixed 2-day cycle (Day 1 Listening, Day 2 Speaking; two
75-minute periods) built around one shared real-world audio or video source (a talk, interview, news segment,
podcast, or similar), differentiated into band-scoped task Levels. Unlike a Passage Reading lesson, the two days
are not interchangeable: Day 1 builds a comprehension performance around the real source, Day 2 builds a
production performance modeled on it, mirroring `learningobjectives.csv`'s pairing of one Listening can-do
with one Speaking can-do at every Level.

**Paste bundle:** run this prompt with `shared/Program_Conventions.md` (taxonomy, task Levels by band, Sets,
version codes) and `shared/Generation_Quality_Standards.md` (every modality-neutral pedagogical and item-quality
rule, plus the shared self-check) alongside it. This prompt states only what is true of a real-source
listening/speaking lesson and points to those files for the rest. Conventions §E's CBI/TBLT framing applies with
the real source as the content vehicle.

**Current version: v2.4.** For the dated version history and the reasoning behind each change, see `Changelog.md`.

**Inputs:** a Module and a Band at minimum (e.g. "Advanced band, Module 2: Narrating"); a topic direction is
optional. Without a Module/Band pair, do not search for a source. Live web search is required to find and confirm
a real source (0.3).

**Output, three artifacts in order, one workflow action:** (1) the source's `<Slug>_Transcript.md` (0.3 item 7),
so every task is built against confirmed real text; (2) the teacher-facing lesson `.md`, with a metadata line
directly under its H1: `**Module:** ... | **Band:** ... | **Task Levels:** ... | **Version:**
<Module>.<Set>.<Lesson>.<Version>` (Conventions §G); (3) the student packet `.html`, by running the Student Packet
prompt against the finished `.md` (Style Guide §G). All three save to the same `Lesson_<N>_<Slug>/` folder
(Conventions §D). Any image the lesson embeds is fetched, cited in the `.md`, and added as a row to the Set's `Set<N>_<Band>_Image_Credits.md` in this same pass (Conventions §I); the packet prints no credit.

**Scope:** the core lesson only. A TOEFL-capable variant of a Set is generated afterward by
`Generate_TOEFL_Track_Tier_Prompt_*.md` against the finished base lessons, into a sibling `Set_<N>_T/` fork; a
normal lesson request produces no TOEFL content. A planned second-source synthesis/presentation-project extension
is not yet written. Assessments come from `Generate_Assessment_Prompt_*.md`; a Set is planned first with
`Generate_Module_Lesson_Plan_Prompt_*.md`.

---

## SECTION 0: SOURCE SELECTION AND CALIBRATION (READ AND APPLY BEFORE SEARCHING FOR A SOURCE)

### 0.1 Anchor level, task Levels, and the Module verb

**The real source is calibrated to the band's LOWER Level** (Conventions §A). That Level governs 0.2's runtime,
pace, and register ceiling. Every student listens to or watches the same source; only the task built on it
differs by Level. Task Levels by band: Conventions §B, one merged task per Level (Quality Standards §A).

Pull the Listening/Speaking objective for the band's lower Level and the requested Module from
`learningobjectives.csv` before searching. Quote the row's Description verbatim - it holds a Listening can-do
and a Speaking can-do in one statement - and use both halves: the Listening half governs Day 1's comprehension
tasks, the Speaking half governs Day 2's production tasks. Each task Level cites its own row the same way.

**The Module verb governs what kind of source to look for** (Quality Standards §A4), not just its difficulty. Do
not default to "any TED Talk":

- **Module 1 (Describing):** a speaker describing a person, place, or object (a walking tour, a home or studio
  tour, a product demo, a "meet my neighborhood" vlog).
- **Module 2 (Narrating):** a personal-story talk, an oral-history clip, a storytelling-podcast episode.
- **Module 3 (Explaining):** a how-something-works explainer, a short science or history documentary.
- **Module 4 (Instructing):** a tutorial, a how-to video, a recipe or skill demonstration with sequential steps.
- **Module 5 (Evaluating):** a review (product, restaurant, film, place), a "worth it or not" segment.
- **Module 6 (Arguing):** an opinion talk, a debate clip, a persuasive talk, a panel disagreement.
- **Module 7 (Transacting):** a customer-service call or roleplay, a negotiation, a service-encounter clip.
- **Module 8 (Socializing):** a casual conversation, a friends/family vlog, a small-talk scene.

Before finalizing a source, check its actual content against the Description's verbs. A source that drifts into a
neighboring Module (a "review" that is really a narrated personal story) is replaced, not forced.

### 0.2 Source runtime, pace, and register ceiling by level

This program does not write the source; it finds real, publicly available audio or video. These targets describe
what to search for and verify. **A source must have a genuine, findable transcript or official captions** (the
platform's own captions, a published transcript page, or a well-established auto-caption track checkable against
the audio); never select a source with no way to verify what is said. Runtime ranges are a soft target: a source
running somewhat past its band's range is a much smaller problem than an off-ceiling anchor text, since its pace
and register do not change. Flag the deviation in the self-check and keep the source if it is otherwise a strong
fit.

**Level 1 (A1)**
- Runtime: 30 seconds to 2 minutes
- Source type: graded-listening clips for absolute beginners, simple labeled object or routine videos, a slow
  deliberate read-aloud
- Pace/register: very slow, deliberate enunciation; single-clause sentences; concrete high-frequency vocabulary;
  strong visual support (captions or matching on-screen visuals)
- Platforms: BBC Learning English (beginner), VOA Learning English (Level 1), elementary read-aloud channels

**Level 2 (A2)**
- Runtime: 1-3 minutes
- Source type: short graded-listening segments, simple vlogs with clear visual support
- Pace/register: slow to moderate, clear enunciation; short simple sentences, minimal subordination; 3-5
  unfamiliar words at most
- Platforms: BBC Learning English, VOA Learning English (Level 1-2), EnglishClass101 beginner clips

**Level 3 (B1)**
- Runtime: 2-4 minutes
- Source type: a graded-for-learners news segment, a TED-Ed short, a simple vlog or human-interest clip
- Pace/register: near-natural but clear; simple past/present backbone, light subordination; a real topic
- Platforms: VOA Learning English (Level 2/Intermediate), TED-Ed, Simple English News Daily

**Level 4 (B1+)**
- Runtime: 3-5 minutes
- Source type: a longer human-interest segment, a short documentary excerpt, a moderately-paced podcast clip
- Pace/register: natural pace with clear articulation; everyday abstract vocabulary; no dense academic register
- Platforms: VOA Learning English (Level 3), National Geographic Kids/Short Docs, local human-interest news

**Level 5 (B2)**
- Runtime: 5-8 minutes
- Source type: a standard (not simplified) TED Talk, an NPR or BBC feature segment, an interview clip
- Pace/register: natural native pace; mixed past/present, natural connectors, some idiom; not dense academic
- Platforms: TED.com (shorter standard talks), NPR News, BBC News features

**Level 6 (B2+)**
- Runtime: 7-12 minutes
- Source type: a standard TED Talk, a documentary excerpt, a longer interview or podcast segment
- Pace/register: full natural pace, idiom and register shifts present; not specialist-jargon-dense
- Platforms: TED.com, PBS or National Geographic documentary excerpts, mainstream podcasts

**Level 7 (C1)**
- Runtime: 10-18 minutes
- Source type: a full unedited TED Talk, a long-form interview, a university lecture excerpt
- Pace/register: full natural or fast pace, idiomatic and some academic register; audience reaction or
  cross-talk possible
- Platforms: TED.com (full talks), NPR long-form interview shows, OpenCourseWare lecture excerpts

**Level 8 (C2)**
- Runtime: 15-25+ minutes, or a multi-speaker panel or debate of similar length
- Source type: a dense academic talk, a panel or formal debate, long-form journalism with digressive or evasive
  speech
- Pace/register: fast, idiomatic, possibly multiple speakers and accents; no register ceiling
- Platforms: university lecture archives, Intelligence Squared-style debates, long-form interview podcasts

### 0.3 Sourcing rules (verification, citation, fair use, transcript file)

1. **Never fabricate a source.** No invented title, speaker, platform, date, or transcript excerpt. Use live web
   search to find and confirm a real source first. If none fits the exact Module/Band/topic, broaden the topic
   within the Module rather than inventing.
2. **Cite it in full at the top of the lesson, before any activity content:** title, speaker or creator,
   platform, URL, approximate runtime, publish date if known. This is what lets the teacher play the source.
3. **Confirm the transcript before building tasks on it.** Quote or closely paraphrase only what the real
   transcript or captions say; never guess wording from a title or description. Target words and phrases are
   pulled from the real transcript, never invented.
4. **Fair-use ceiling inside the lesson `.md`:** never reproduce the full transcript there. Direct quotation is
   limited to short excerpts (one to two sentences at a time) for a specific task (a vocabulary-in-context item,
   a "listen for this line" cue, a quoted speaking-skill phrase). Everywhere else, paraphrase and point to the
   timestamp.
5. **Timestamp markers, not paragraph letters.** Every listening or watching task cites an approximate timestamp
   range ("[2:15-3:40]"), used consistently wherever a segment is referenced. Where a real timestamp cannot be
   verified, use the source's own internal structure (headed sections, chapter markers) as the segment label
   and say so; the teacher pencils in real elapsed times on first playthrough.
6. **Background Note (footnote equivalent).** When the source names a real person, place, event, or reference
   unlikely to be common knowledge at the band and not explained by the source itself, add a short, sourced
   "Background Note" callout (one or two plain sentences inside the Level's register ceiling). Occasional (1-3
   per lesson), informational only, never the basis of an item.
7. **A two-source task prints both sources' words in the `.md`.** Where a task Level's objective needs two
   real sources on the same subject (Level 7's typically does), the `.md` itself carries each source's own
   words, paired subject by subject, in the quantity Quality Standards §C9 sets - not a sentence naming what
   each source covers, and never an instruction telling the student to go notice the evidence themselves. The
   packet is a regeneration of the `.md`, so whatever the `.md` omits here cannot appear in the packet. Both
   sources are verified and cited per items 1-2, and both are subject to item 4's fair-use ceiling.
8. **Standalone transcript file.** Save `<Slug>_Transcript.md` in the lesson's folder, holding the source's full
   real transcript or captions as close to verbatim as is obtainable, headed by the same citation block as the
   lesson. It is exempt from item 4's ceiling because it is a teacher-only working reference: never printed in,
   derived into, or surfaced in the student packet. If a genuine full transcript cannot be retrieved (only
   fragments, a partial auto-caption track, or an AI-summarized fetch are confirmable), save what was actually
   verified and state at the top what is missing and how the included content was confirmed. Never pad a gap
   with invented dialogue.

### 0.4 Rotation banks

Rotate genuinely across cycles per Quality Standards §D6 (no repeat of the immediately preceding lesson in any
bank; Conventions §F for the cross-Set rule). These banks are starting points and grow with use.

- **Listening strategies (Day 1, Phases 3-5):** Listen for Main Ideas/Gist; Recognize Examples; Listen for
  Signposting/Discourse Markers; Listen for Sequence Markers; Listen for Stated vs. Implied Opinion; Listen for
  Cause-and-Effect Language; Predict from Context Before Confirming; Listen for Contrastive/Concession Language.
- **Note-taking structures (Day 1, Phase 2), matched to the Module:** outline (idea plus indented examples),
  T-chart or Venn diagram (Describing), sequence chain (Narrating, Instructing), cause-and-effect chain
  (Explaining), criteria/verdict grid (Evaluating), two-column claims tracker (Arguing), and the equivalent for
  Transacting and Socializing.
- **Speaking skills (Day 2, Phases 1-2):** Agree/Disagree phrases; Giving Examples; Asking for Clarification;
  Sequencing Language; Hedging an Opinion; Making Comparisons; Turn-Taking and Interrupting Politely; Summarizing
  What Someone Said.
- **Pronunciation features (Day 2, Phase 3):** content-word stress; thought-group pausing; linking; rising and
  falling intonation for questions vs. statements; contrastive stress; reduced forms in fast speech
  (Advanced/Proficient only).
- **Phase 1 hooks:** Visual Inquiry, Take a Side, Mystery Quote, K-W-L Chart.
- **Oral output protocols (Day 2, Phase 4):** Town Hall, Panel Round, Rotating Partners, Jigsaw Expert Panels,
  small-group discussion; each with 2-3 rotated prompts and an active task for every non-speaker (Quality
  Standards §D7). Every hook and protocol runs from where students sit: no facing circles, corners, stations,
  or anything posted around the room (Quality Standards §D11).

### 0.5 Self-check before finalizing

Run `shared/Generation_Quality_Standards.md` §F first. Then, for the real source and the rules in this prompt:

1. **Source real and verifiable** (never fabricated), with a genuine transcript or captions confirmed before any
   task was built, and the full citation block first in the lesson (0.3 items 1-3)?
2. **Runtime, pace, and register** inside 0.2's ceiling for the band's lower Level, or the deviation flagged and
   justified (0.2)?
3. **Source content matches the Module's verb** per the CSV Description, not a neighboring Module (0.1)?
4. **Both halves of each Level's CSV row used:** the Listening half for Day 1 tasks, the Speaking half for Day 2
   tasks (0.1)?
5. **Target words and phrases (4-6) present in the real transcript**, correctly glossed, with any
   naturally-occurring opaque idiom glossed at every band?
6. **Direct quotation inside the `.md` within the fair-use ceiling** (one to two sentences at a time), the full
   transcript never reproduced there (0.3 item 4)?
7. **Every listen-for or watch-for task tagged with a consistent timestamp range** or, where unverifiable, the
   source's own segment structure (0.3 item 5)?
8. **Background Notes** occasional (1-3), factual, sourced, informational only, never tested (0.3 item 6)?
9. **Transcript file** present in the lesson folder with the same citation block, honest about any gap, and
   entirely absent from the student packet (0.3 item 7)?
10. **Day 1 Phase 5's Closing Transfer Check script** is a short invented paragraph written into the lesson (60-90
    words, unrelated topic, recycling most target words), read aloud by the teacher, printed for students only
    after the response space, never left as an unspecified "new clip"?
11. **Day 2 Phase 1's speaking skill** drawn from the real speakers' own language at a cited timestamp or, where
    the source genuinely lacks it, grounded in the source's real context and flagged here as a deviation, never
    quoting invented dialogue?
12. **Pronunciation feature** genuinely audible in the real source and modeled from its audio, not an invented
    example?
13. **Lowest task Level's fixed-frame items** carry a complete inline instruction (what to listen for, what fills
    the blanks), with a separate frame box only where a speak-it-aloud step anchors it?
14. **Fixed-output Levels (0.6; Quality Standards §D10):** where Level 1 or 2 is a task Level, its form (point,
    name, or the frame) is produced at most once per day, every other Level 1-2 item takes a different 0.6
    shape, no shape twice in this lesson or in the same slot as the previous lesson, and the frame is printed
    once per day?
15. **Answer notes:** every exemplar answer on an `Answer note:` line under its Level's task, and no task
    sentence or parenthetical stating what the item asks for (Quality Standards §F item 23)?

If any check fails, revise before finalizing; do not build any task on a source that failed items 1-3.

### 0.6 Fixed-output Levels (1-2): task shape bank and slot assignment

Quality Standards §D10 applies. Level 1's row is recognize-and-point or name a word; Level 2's is a one-slot
frame heard and produced. The form does not change, so the activity around it must. **The cap:** the student
produces the form (points to or names the image, says or completes the frame) at most once per lesson day; no
task says "three times." Every other Level 1-2 item in the lesson takes a different shape from this bank, and
no shape appears twice in one lesson or in the same slot as the previous lesson:

| Shape | What the student does | Slot |
|---|---|---|
| Point or name | Point to the embedded image the heard word or frame names, or say the word; the Day 1 production | Day 1 Phase 4 |
| Choose what was heard | From the target-word list, circle the words the clip actually said and cross out the ones it did not | Day 1 Phase 2 (listen-for purpose) |
| Fix the wrong word | A printed line from the clip with one word changed or misspelled; cross out, write or say the right one | Day 1 Phase 4 (alongside the production) or Day 2 Phase 1 |
| Say from sound | A partner says a target word; the student repeats it and points to or writes it, then checks | Day 2 Phase 2 or Phase 3 |
| Better of two | Two printed frame lines about the clip's object; circle the one that fits and say the word that makes it fit | Day 2 Phase 2 |
| A partner's object | Say the frame about a partner's belonging, not the clip's; the Day 2 production | Day 2 Phase 2 or Phase 4 |
| Transfer | The form once, on the lesson's fresh prompt (Quality Standards §D3) | Day 1 Phase 5 and Day 2 Phase 5 |

The frame is printed once per day, in the first task that uses it; later tasks say "the frame." A Set's Module
Lesson-Plan names the slot-to-shape assignment per lesson so the same shape does not land in the same slot
twice running.

---

## Unit Architecture: 2-Day Source Cycle Model

Every unit spans two 75-minute periods built around one shared real source: **Day 1 is Unit A (Listening), Day 2
is Unit B (Speaking).** Item counts per task Level follow Quality Standards §C5 (lower Levels more, shorter items;
higher Levels fewer, deeper items; time-on-task balanced) and every item set follows §C1-C8.

**2-DAY SOURCE CYCLE OVERVIEW (approx. 150 MIN TOTAL)**

```
DAY 1 (Unit A - Listening)  |--Hook, Vocab & Purpose (20)--|--Watch & Notes (15)--|--Skill Instr. (10)--|--Task (20)--|--Transfer Check (10)--|
DAY 2 (Unit B - Speaking)   |--Skill Spotlight (15)--|--Differentiated Practice (20)--|--Pronunciation (10)--|--Oral Output (20)--|--Transfer Check & Wrap (10)--|
```

### DAY 1: Unit A - Listening (75 min)

_Phase 1: Hook, Good to Know & Vocabulary (20 min)_
- A real-world hook tied to the source's actual topic (rotate per 0.4 and the approved plan), not abstract
  framing above the band's register.
- **Listening Skill Spotlight** (Quality Standards §D1): name the lesson's listening strategy in one or two plain
  student-facing sentences ("Today we're practicing listening for examples - noticing when a speaker gives a
  specific case to support a bigger idea"). This is the exact skill Phase 5 asks students to reproduce.
- Present the full citation block (0.3 item 2) and any Background Notes (0.3 item 6) together, up front.
- Pre-teach 4-6 target words or phrases from the real transcript, in context sentences paraphrased from what the
  source actually says. Transparent chunks lightly glossed from Level 2 up; opaque idioms get an explicit gloss or
  guided confirmation at every Level.

_Phase 2: Watch & Listening Notes (15 min)_
- Play the full source once (for Proficient-length sources, the first half with a clear timestamp cutoff).
- Students fill a shared note-taking organizer matched to the Module (0.4) while watching.
- Set a differentiated listening purpose per task Level before playback: the lowest Level a narrow, concrete
  listen-for question (for Levels 1-2, a 0.6 shape such as choose-what-was-heard); the highest an open
  interpretive one.

_Phase 3: Listening Skill Instruction (10 min)_
- Teach the named strategy directly using a real, timestamped excerpt as the model; brief guided practice on a
  second short excerpt.

_Phase 4: Differentiated Listening Task, Choose One Level (20 min)_
- One merged, star-rated task per task Level: what main-idea, detail, and critical-thinking items would cover,
  written as a single sequential item set per Level from the start (the same merge the packet prompt applies).
  A Level 1-2 set produces its form once and fills the rest with 0.6 shapes, never the same point-or-name item
  repeated. The exemplar answer for any item (the segment's organization, the evaluative word, the two facts,
  the tonal shift, the unstated interest) goes on an `**Answer note:**` line under that Level's task, never in
  the task sentence or its parenthetical (Quality Standards §C9, §E2).
- **Board-dependent moment** (Quality Standards §D4): students from different task Levels compare and report
  into the shared Phase 2 organizer, so the complete picture exists only once several Levels have contributed.
- **Respectful Tiers** (Quality Standards §B): the lowest task Level's task includes a genuine, simplified
  interpretive component, not fact-retrieval alone.

_Phase 5: Listening Closing Transfer Check (10 min)_
- **Mechanism: a short invented script the teacher reads aloud**, written into the lesson (roughly 60-90 words, a
  topic unrelated to the source, recycling most of the lesson's target vocabulary). Invented, not found: its
  purpose is controlled vocabulary recycling and a clean skill-transfer test.
- Students do not read it first; it is printed in the packet only after the response space, under a "don't read
  ahead" instruction (and upside-down, per the packet prompt).
- Students apply the Phase 1 strategy to what they heard (gist, prediction, retold order - whatever the named
  skill is), out loud to a partner; two or three pairs cold-called. Demonstration, not self-report (Quality
  Standards §D2). After sharing, students may read the script to check.

### DAY 2: Unit B - Speaking (75 min)

_Phase 1: Speaking Skill Spotlight (15 min)_
- Identify a moment where the real speaker(s) actually use the target functional language (agreeing and
  disagreeing, giving an example, sequencing, hedging, comparing) at a cited timestamp; the skill is drawn from
  authentic input wherever the source allows. Where the source genuinely lacks it (a narrated profile with no
  dialogue), ground the spotlight in the source's real, verified situational context and flag the deviation in
  0.5, never quote invented dialogue as real. Name the skill in plain student-facing language; this is the exact
  skill Phase 5 asks students to reproduce.

_Phase 2: Differentiated Speaking Practice, Choose One Level (20 min)_
- One merged, star-rated production task per task Level: at the lowest Level the Level's frame, produced once,
  with its other items in 0.6 shapes; an open register-appropriate production at the highest, matching the
  packet prompt's Practice It tasks.

_Phase 3: Pronunciation Mini-Focus (10 min)_
- Teach one feature actually audible in the source (0.4 bank) using the source's own audio as the model. Students
  mark a short excerpt for the feature, check against the real audio, then apply it in brief paired rehearsal of
  their Phase 2 language.

_Phase 4: Structured Oral Output (20 min)_
- One rotating protocol (0.4) built on the source's actual topic, applying the Module's functional skill and the
  day's speaking and pronunciation focus, with 2-3 rotated prompts and an active task for every non-speaker.
- **Differentiated participation** (Quality Standards §B): the lowest task Level gets a different participation
  mode (a rehearsed pair-share before the public round, or a listening/tracking role with one prepared line);
  Foundation Support gets non-verbal or minimally-verbal roles throughout.
- **Board-dependent moment:** a running board record of claims or points as they are actually spoken, feeding
  Phase 5.

_Phase 5: Speaking Closing Transfer Check & Wrap (10 min)_
- Every student produces, in pairs and out loud, one new instance of the Phase 1 Speaking Skill Spotlight on a
  prompt other than the source's topic, fresh for this lesson (Quality Standards §D3); two or three pairs
  cold-called. Demonstration, not self-report.
- **Respectful Tiers check across the cycle:** the lowest task Level had a genuine interpretive task on Day 1 and a
  genuine production role on Day 2, not fact-retrieval and silent participation.
- Brief whole-class reflection on the cycle's topic and skills.

---

## Style & Formatting Constraints

Quality Standards §E applies (no em-dashes, ASCII pacing diagram per day in the overview's format, the metadata
line, oral focus over written drills). Listening/Speaking-specific:

- **Citation block first:** every lesson opens with the 0.3 citation block before any activity content.
- **Timestamps, not paragraph letters:** every segment reference uses a timestamp range or, where unverifiable,
  the source's own section labels; never a paragraph or line number.
- **The transcript file is never read into the packet.**
