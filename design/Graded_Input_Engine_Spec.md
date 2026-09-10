# Graded Input Engine - Design Spec (v1.2)

> **This file states no rules and describes nothing that exists yet.**
>
> It is an unbuilt design proposal. Nothing here is enforced at generation time, no prompt cites
> it, and no lesson was generated against it. It lives in `design/` and **not** in `shared/`
> precisely so that the generalization pass described in `CLAUDE.md` does not sweep it into live
> prompts. A rule only becomes a rule by being written into `shared/Program_Conventions.md`,
> `shared/Generation_Quality_Standards.md`, or `shared/Student_Packet_Style_Guide.md` as its own
> deliberate decision.
>
> If you are here to change how lessons are generated, this file is not your authority.

---

## A. Problem statement and scope

### A1. The volume gap

Cambridge's guided-learning-hours estimates, cumulative from zero: A2 180-200 · B1 350-400 ·
B2 500-600 · C1 700-800 · C2 1,000-1,200. The B1-to-B2 transition alone is roughly 180-260 hours.
For L1 Korean/Japanese/Chinese/Arabic speakers, multiply by roughly 3-4x.

Against that, this program's actual listening contact: `Generate_Lesson_Prompt_v2.6.md` §0.2 sets
clip runtime at 30 sec-2 min (Level 1) rising to 10-18 min (Level 7), and the full clip is played
through **twice** per 2-day lesson (Day 1 Phases 2 and 4, since v2.6), with a handful of
short-excerpt replays and one covered-window replay in Phase 5. The worked Intermediate example
(`Lesson1_NewBakery`, a 4:31 VOA clip) delivers roughly 10-14 minutes of authentic audio across two
75-minute periods, and doubling the in-class plays does not change the order of magnitude of the
gap below.

No classroom program closes a 200-hour gap, and this is not a defect in the lesson design. Hours at
that scale come from out-of-class input. This program currently has none: there is no homework
prompt for Listening/Speaking, no listening log, no volume target, and no self-access library.

### A2. The threshold problem

Van Zeeland & Schmitt (2013) manipulated spoken passages to 90 / 95 / 98 / 100% known-vocabulary
coverage. Comprehension held at 95%, and they recommend 95% as the floor for listening because
below it comprehension becomes *erratic* rather than merely lower - some learners cope, most do
not. For reading, Laufer & Ravenhorst-Kalovski argue ~98% for precise comprehension, with 95%
giving only minimal understanding.

The consequence is a threshold effect, not a gradient: **a student below the coverage floor is not
getting a reduced share of the input, they are getting close to none of it.** This is the mechanism
behind the observation that prompted this spec - a beginner in an Intermediate class will listen
and not understand, and so will not progress, however attentive they are.

The program's current design pushes directly against this. `Program_Conventions.md` §A: *"Every
student in the room engages with the same band-calibrated centerpiece; only the task built on top
of it differs by task Level."* Differentiation is applied to the **task**, never to the **input**.
That is a defensible design for a class working from one shared authentic source, but it has no
answer for a student below the centerpiece's own floor.

### A3. The design goal

One falsifiable claim:

> For any student and any generated item, the student's lexical coverage of that item is computable
> **before** they encounter it.

No authentic-materials curriculum can do this, because the vocabulary of a found clip is not known
in advance and the learner's known-set is not tracked. A generated item built from a bounded
inventory against a tracked known-set makes it arithmetic.

### A4. Scope

**In scope:** an inventory of what a learner must meet, a coverage model over it, a generator that
schedules against the uncovered tail, audio and comprehension items, and the level mapping that
ties all of it to this program's 8 Levels.

**Out of scope:** replacing the existing authentic-source lessons. This is the *extensive* strand
beside the existing *intensive* one, not a substitute for it. The two do different jobs: the
authentic clip teaches coping with real speech at the band's ceiling; this engine builds the hours
and the automaticity underneath it.

---

## B. The five axes and their source datasets

A vocabulary list alone will not deliver the claim in §A3. "The common things that are said" are
only partly single words: they are also formulaic chunks, grammatical structures, communicative
functions, and - for listening only - sound shapes. Five axes, five inventories.

| # | Axis | What it inventories | Dataset | Size |
|---|---|---|---|---|
| 1 | Lexis (spoken) | single words in speech | NGSL-Spoken v1.2 | 721 words -> 90% coverage of unscripted speech |
| 1 | Lexis (written) | single words in text | NGSL | 2,809 words -> 92% of general English |
| 1 | Lexis (levelled) | words tagged to CEFR sublevel | CEFR-J vocabulary profile | ~7,800 entries |
| 1 | Lexis (sense-level) | word *senses* and phrases by level | English Vocabulary Profile | ~7,000 headwords |
| 2 | Chunks | non-transparent multiword expressions | PHRASE List (Martinez & Schmitt 2012) | 505 |
| 3 | Grammar | grammatical structures by CEFR level | English Grammar Profile | ~1,200 |
| 4 | Functions | communicative functions / speech acts | Threshold 1990, Waystage 1990 (van Ek & Trim) | full notional-functional inventory |
| 5 | Connected speech | sound shapes of continuous speech | **none exists - must be built** (§G) | see §G |

### B1. Why NGSL-Spoken is the headline number

**721 words gives 90% coverage of unscripted spoken English.** That is the single most important
figure in this spec. A listening curriculum that guarantees coverage of "the common things that are
said" has a target list of roughly seven hundred items - small enough to cover exhaustively, track
per student, and verify. The goal is not aspirational; it is a finite list.

The written equivalent is larger (NGSL's 2,809 for 92%) but still bounded. The reading branch is a
bigger job than the listening branch, not a different one.

### B2. Licensing - verify before redistributing

This determines what can physically live in the repo and must be checked before any dataset is
committed:

- **CEFR-J via Open Language Profiles** - stated as free for research *and commercial* use with
  proper citation. This is the only axis-1 dataset currently confirmed redistributable, and it is
  therefore **the spine**. Its sublevels (A1.1 / A1.2 / A1.3 ...) are finer than CEFR proper at
  exactly the levels where this program's Beginner band sits, which is a second reason to prefer
  it.
- **NGSL / NGSL-S** - published for open pedagogical use; confirm the specific licence at
  newgeneralservicelist.org before committing the files.
- **English Vocabulary Profile / English Grammar Profile** - free to *access* (registration).
  Redistribution rights are **not** established. Treat as **consult-only**: use them to adjudicate
  edge cases and to source the grammar axis by reference, do not copy the databases into the repo
  until the licence is confirmed.
- **PHRASE List** - the list is published as an appendix to the *Applied Linguistics* article;
  confirm reuse terms.
- **Threshold 1990 / Waystage 1990** - Council of Europe, freely distributed PDF.

**Recommendation:** build v1 on CEFR-J + NGSL/NGSL-S as the committed data, cite EVP/EGP as external
references, and treat the grammar axis as a hand-curated subset derived from EGP rather than a copy
of it.

---

## C. Mapping external levels onto this program's 8 Levels

The hardest design problem here, and the one most likely to be fudged. The program's own mapping,
copied verbatim from `shared/Program_Conventions.md` §A:

| Band | Levels | CEFR |
|---|---|---|
| Beginner | 1-2 | A1-A2 |
| Intermediate | 3-4 | B1-B1+ |
| Advanced | 5-6 | B2-B2+ |
| Proficient | 7-8 | C1-C2 |

### C1. Three genuine mismatches

1. **8 Levels do not divide into 6 CEFR bands.** Levels 4 and 6 are "B1+" and "B2+" - labels with
   no counterpart in any CEFR-tagged dataset. No published word list will ever return a "B1+" set.
2. **Frequency stops discriminating at the top.** NGSL-S's 721 words are exhausted somewhere around
   Level 3. By Levels 7-8, what separates a C1 text from a C2 one is not word frequency but
   syntactic density, register, idiomaticity, and discourse structure. A frequency-driven coverage
   model is close to useless at Proficient.
3. **Frequency also under-determines the bottom.** At Level 1, `Generate_Lesson_Prompt_v3.5.md`
   §0.2 demands "decodable simple-phonics words" - a *phonics* constraint orthogonal to frequency.
   "Through" is high-frequency and undecodable; "cat" is lower-frequency and decodable.

### C2. Resolution - the two axes map differently

Built and verified against the datasets (`esl-inventory/inventory/levels.py`).

**Lexis is banded and cumulative.** No vocabulary dataset carries sublevels - CEFR-J's profile is
tagged A1/A2/B1/B2 and Octanove's C1/C2 - so program Levels 4 and 6 ("B1+", "B2+") genuinely have
no lexis of their own and share the assumed-known sets of Levels 3 and 5. This half of the original
objection stands.

| Level | Assumed-known bands | Headwords |
|---|---|---|
| 1 | A1 | 1,084 |
| 2 | A1+A2 | 2,356 |
| 3 | A1+A2+B1 | 4,530 |
| 4 | A1+A2+B1 (same as 3) | 4,530 |
| 5 | A1+A2+B1+B2 | 7,020 |
| 6 | A1+A2+B1+B2 (same as 5) | 7,020 |
| 7 | +C1 | 7,949 |
| 8 | +C2 | 8,845 |

**Grammar is per-Level, and dataset-backed.** The CEFR-J Grammar Profile *does* carry sublevels -
A1.1, A1.2, A1.3, A2.1, A2.2, B1.1, B1.2, B2.1, B2.2, C1, C2 - which partition all eight Levels
with no gap and no overlap: L1→A1.1-A1.2, L2→A1.3-A2.2, L3→B1.1, L4→B1.2, L5→B2.1, L6→B2.2,
L7→C1, L8→C2. **"B1+" and "B2+" are B1.2 and B2.2.** No workaround is needed.

**But the mapping is thin exactly where it was most needed.** Item counts per Level after loading:

| L1 | L2 | L3 | L4 | L5 | L6 | L7 | L8 |
|---|---|---|---|---|---|---|---|
| 99 | 96 | 78 | **13** | 75 | **11** | 30 | 9 |

Levels 4 and 6 receive roughly a sixth of the grammar items of Levels 3 and 5. The mapping is real
rather than invented, but it will not carry a Level's whole progression on its own, and any claim
of "full grammar coverage" at Level 4 or 6 is currently unsupportable.

**A data-quality caveat that must travel with any grammar figure.** Only **34%** of the profile's
500 rows carry a value in their own `CEFR-J Level` column. The rest resolve through a fallback
chain (`Core Inventory` 31%, `EGP` 15%, `GSELO` 2%) and **18% do not resolve at all**. The loader
reports this breakdown on every run rather than silently dropping the blanks, because a loader that
read only the obvious column would lose two thirds of the axis and appear to work.

**Frequency still stops discriminating at the top.** By Levels 7-8, what separates C1 from C2 is
syntactic density, register, idiomaticity and discourse structure rather than word frequency, so a
frequency-driven coverage figure is weakest exactly there.

**State the seam explicitly wherever it is used.** A coverage figure at Level 2 and a coverage
figure at Level 7 are not the same measurement, and a UI that presents them as one number is lying.

### C3. The decodability sub-filter (Level 1 only)

Level 1 needs a flag the published datasets do not carry: whether a word is decodable by simple
phonics. This is a small hand-built annotation over the Level 1 candidate set (a few hundred words
at most) and is listed here so it is not discovered late.

### C4. Target level vs. assumed-known set

These are different and must never be collapsed:

- **Target level** - the level of the items the artifact is *teaching*.
- **Assumed-known set** - everything the student is presumed to already hold, which is what §F
  computes coverage against.

`Program_Conventions.md` §A calibrates a centerpiece to the band's *lower* Level. That is a rule
about target level. It says nothing about a given student's known-set, which is per student and
tracked, not per band and assumed. Conflating the two reintroduces the exact problem in §A2.

---

## D. The coverage data model

### D1. Entities

```
item       { id, axis, form, level, source_dataset, notes }
artifact   { id, branch(listening|reading), target_level, text,
             audio_ref, questions[], item_ids[] }
encounter  { item_id, artifact_id, student_id?, timestamp }
student    { id, known_set_snapshot, level }
```

### D2. Coverage is a count, not a flag

Webb (2007) found substantial incidental gains at ~10 encounters in context, and noted that full
knowledge of a word may need more than ten. The wider literature ranges from 6 to 20+ depending on
how knowledge is measured.

So an item is never simply "covered." It has an **encounter count**, and "covered" is a threshold
over that count.

- **Proposed threshold: 10 encounters, in varied contexts.**
- Explicitly tunable, and expected to differ by axis - a grammatical structure and a single word
  almost certainly do not need the same number of exposures.
- "Varied contexts" needs an operational definition (propose: no more than 2 of the required
  encounters from any single artifact).

### D3. Two coverage views, never conflated

- **Program coverage** - has the corpus of generated artifacts covered the inventory? Drives the
  generator (§E).
- **Student coverage** - has *this* student met this item N times? Drives the game, the progress
  display, and the §F threshold check.

An item can be fully covered program-wide and at zero for a new student. Reporting one as the other
is the most likely source of a false "this student is ready" signal.

---

## E. The generator's selection rule

### E1. The failure mode this exists to prevent

Unconstrained generation over-samples the easy middle. Dialogue #400 is the sixtieth variation on
ordering coffee, while two hundred tail items sit at zero encounters. The corpus grows without the
coverage growing. This is the default outcome, not an edge case, and it is what would make the
"infinite list of listening practice" untrue in the way that matters.

### E2. The rule

**Select targets by lowest current encounter count. Topic is an output, not an input.**

Each generation request is seeded with:

1. **N under-covered target items**, drawn across the five axes, ordered by ascending program
   encounter count.
2. **The assumed-known set** for the target level (§C).
3. **A hard constraint** that every word outside the target set must come from the assumed-known
   set.
4. **A context requirement** - the situation must be one in which those particular targets co-occur
   naturally. If the drawn targets cannot plausibly co-occur, redraw rather than force them.

The topic of the dialogue falls out of (4). Nobody chooses it, which is the point: choosing topics
is how the tail never gets covered.

### E3. Guards

- **Naturalness ceiling.** A dialogue crammed with 15 low-frequency targets is not natural input,
  and Renandya & Farrell's argument cuts both ways - unnaturally dense material is its own failure.
  Cap targets per artifact; prefer more artifacts over denser ones.
- **Redraw on failure.** If the generated artifact fails §F, regenerate rather than patch.
- **Record what was actually used**, not what was requested. Encounters are logged from the
  finished text, since the generator will not always place every seeded target.

---

## F. Computing the coverage threshold

### F1. The computation

Given an artifact's text and a student's known-set:

```
coverage = known_tokens / total_tokens
```

- **Token-based, not type-based.** A learner processes running speech, not a word list; a single
  unknown word repeated eight times is eight moments of failure. Type-based coverage would score
  that as one gap.
- **Proper nouns** are excluded from the denominator when they are supported by context or by the
  glossary, and counted as unknown otherwise. Decide once and apply consistently; a spec that
  leaves this open produces incomparable numbers.
- **Numbers** are treated as known at all levels.
- **Inflected forms** resolve to their headword before lookup.

### F2. Different thresholds by branch

- **Listening: 95%** (Van Zeeland & Schmitt 2013).
- **Reading: 98%** (Laufer & Ravenhorst-Kalovski) for precise comprehension.

These are not interchangeable, and the reading branch is therefore the *stricter* one. This is
counterintuitive and worth stating loudly, because the instinct is to assume listening is harder
and so needs the higher bar. The reason it does not: a reader can regress, re-read, and take their
own time, so a higher proportion of known text converts into precise comprehension; a listener
cannot, so the threshold is set where comprehension stops being erratic rather than where it
becomes precise.

### F3. Action on failure

Either:
- **Regenerate** - preferred during corpus building; or
- **Gloss** the offending items pre-listening, moving them into the known-set for that artifact.

Never: ship the artifact and hope. That is exactly the current situation §A2 describes.

---

## G. The connected-speech axis (listening only)

### G1. Why this axis exists

Field (2003) locates L2 listening breakdown at **segmentation** - finding word boundaries in
continuous speech. A student who knows every word in *"What are you going to do?"* frequently
cannot recognise it as spoken: /wɒtʃəgənədu/.

**Lexical coverage does not deliver phonological coverage.** Without this axis, the engine could
certify a student as having full coverage of the spoken inventory while they remain unable to
follow ordinary speech - which would be a worse outcome than having no coverage claim at all,
because it would be a confident wrong answer.

This axis has **no counterpart in the reading branch**. It is where the two generators diverge
rather than share an engine.

### G2. The inventory

No published list is level-tagged for this purpose, so it is built here. The categories split by
whether synthesis can actually be made to produce them (§G4): edge-tts exposes no phoneme control,
so a category is targetable only if it has an **orthographic handle** - a spelling that makes the
neural voice produce the reduced form on its own.

**Targeted** - reliably producible, so encounters are counted toward coverage:

| Category | What varies | Handle | Examples |
|---|---|---|---|
| Weak forms | function words reduce to schwa | natural rate | to /tə/, of /əv/, and /ən/, can /kən/, are /ə/, was /wəz/ |
| Contractions | auxiliary + pronoun/negative fusion | spelling | I'll, we've, shouldn't, there's, that'll |
| Lexicalised reductions | fixed spoken forms | spelling | gonna, wanna, gotta, kinda, dunno, lemme, gimme, 'em |
| Flapping | /t/ between vowels | inherent to en-US voices | water, better, get up, a lot of |

**Observed, not targeted** - these occur in natural speech and a neural voice will produce some of
them, but there is no way to force a specific instance and no way to verify one per item. They are
not seeded, not counted, and no coverage claim is made about them:

| Category | What varies | Examples |
|---|---|---|
| Elision | segments dropped | next day /neksdeɪ/, most common /məʊskɒmən/ |
| Assimilation | segments change to match neighbours | ten bikes /tembaɪks/, good girl /gʊggɜːl/ |
| Linking & intrusion | boundaries erased or filled | far away /fɑːrəweɪ/, go on /gəʊwɒn/ |
| Stress-timing | unstressed syllable compression | the whole rhythmic contour, not a discrete item |

This split is a **tooling boundary, not a pedagogical judgement**. All eight matter to a listener.
Four of them are simply outside what the current pipeline can produce on demand and verify, and a
coverage claim over the other four is the honest one to make. A pipeline with phoneme control, or
recorded human audio, would move the second group back into the first.

### G3. The governing rule

> **A target item is never heard only in its citation form.**

A word introduced only in careful speech has been covered lexically and not phonologically. Its
encounter count should not reach threshold on citation-form exposures alone.

**What enforces it.** Every artifact renders at least twice - once at the target level's rate from
`LEVEL_SPEEDS`, once at natural rate (`+0%`) - and **an item's encounter count reaches threshold
only if at least one encounter came from a natural-rate pass.** Without the second clause the rule
is advisory, and the slowed pass alone would satisfy the counter while training the wrong forms.

This is the `rate_passes` field in the dialogue manifest, which validation requires to contain a
`+0%` entry.

### G4. What the audio pipeline can and cannot do

Research comparing TTS to human voices is reassuring on outcomes - comparable performance on
comprehension, dictation, and aural identification tasks - but naturalness ratings are consistently
unfavourable, and default TTS **over-articulates**. For most uses that is cosmetic. Here it is
disqualifying, because over-articulated audio trains recognition of precisely the citation forms
§G3 exists to avoid.

The pipeline is Python + [edge-tts](https://github.com/rany2/edge-tts) (Microsoft Edge's online
neural voices) + ffmpeg for stitching multi-speaker dialogue.

**Already solved, no work required:**

- **Voice variation.** `edge_tts.VoicesManager` + `find(Language="en")` returns every English voice
  the service offers, so recognition never attaches to a single voice.
- **Accent variation.** Those voices span en-US, en-GB, en-AU, en-IE, en-NZ, en-ZA, en-IN, en-CA and
  more - roughly a dozen English locales (322 neural voices across all languages). Run
  `edge-tts --list-voices` for the current set.
- **Rate control**, already mapped to CEFR level.
- **Multi-speaker dialogue**, already built: each line is synthesised separately and stitched with a
  configurable pause, which is exactly the shape a generated dialogue has.

**The hard limit: no phoneme control.** edge-tts does not support `<phoneme>` tags or arbitrary
SSML - Microsoft permits only a single `<voice>` tag containing a single `<prosody>` tag, and the
library removed custom SSML support deliberately. Only `rate`, `pitch`, and `volume` are
controllable. **A pronunciation cannot be forced with IPA.** This is what produces §G2's split.

**The route that does work: orthography.** A neural voice renders *gonna*, *wanna*, *dunno*,
*lemme*, *'em* as reduced forms because those are real spellings in its training data. Reduced forms
are therefore requested by **writing them**, not by marking them up - which means the generator (§E)
must be free to emit those spellings, and any prompt that "corrects" them to *going to* silently
destroys the axis.

**The tension in the rate mapping.** The pipeline's CEFR speed table slows the low levels hardest -
Pre-A1 -25%, A1 -20%, A2 -15%, B1 -10%. Slowing neural TTS pushes it toward citation forms, so the
mapping works hardest against this axis at exactly the levels where it is most aggressive. Slow
speech genuinely aids beginner segmentation, so this is a real trade-off rather than an error, and
§G3's two-pass requirement is how it is resolved: the slowed pass for access, the natural pass for
the phonological form.

**Still to verify empirically** (see the reduced-forms test): whether a slowed pass restores citation
forms outright. If it does, the two-pass rule is confirmed. If *both* passes over-articulate, §G2's
targeted group narrows further and this section needs revising again.

---

## H. Comprehension questions

### H1. Inherit the existing taxonomy

`learningobjectives.csv` already holds 192 rows - 8 Levels x 8 Modules x 3 Modalities - each a
"Can ..." statement with a worked example. Question templates should key to those rows so the
engine's items inherit the program's taxonomy rather than inventing a parallel one that later has
to be reconciled.

### H2. Questions are subject to §F

The question text is input too. A comprehension question that introduces above-level vocabulary
tests the wrong thing and silently breaks the coverage guarantee. **Run the §F computation over
the question set as well as the passage**, against the same known-set.

### H3. Item-writing constraints

- The answer must be recoverable from the audio/text alone - no outside knowledge, and no
  dependence on a previous session's work.
- Distractors must be plausible on the passage's own terms, not eliminable by length or oddity.
- At Levels 1-3, questions are concrete: no inference chains and no reflection prompts. This aligns
  with `shared/Generation_Quality_Standards.md` §E6, which already forbids reflection questions at
  Beginner/Intermediate.

---

## I. The retrofit - the inventory layer without the generator

**This section describes a possible follow-on, not a plan, and nothing here is approved.**

The inventory layer (§B, §C) is useful on its own, before any dialogue is generated, any audio is
made, or any code is written. Today this repo has **no vocabulary control of any kind**. Greps for
NGSL, English Vocabulary Profile, English Grammar Profile, CEFR-J, "word family", "vocabulary
profile", and "lexical coverage" return zero hits repo-wide. What exists instead:

- `reading/passage-reading/prompts/Generate_Lesson_Prompt_v3.5.md:82` - *"Vocabulary: concrete,
  high-frequency, decodable simple-phonics words; zero abstract nouns"*. Three of those four
  constraints are unverifiable prose adjectives with no list behind them.
- The same file line 100, whose four example words are the **entire** operational definition of the
  Level 3 lexical ceiling: *"no academic or abstract vocabulary ('extraordinary,' 'civilization,'
  'habitat,' 'preserved' are Level 5+)"*.
- The same file §0.3 item 4 - *"**Vocabulary scan:** no word that would only appear two or more
  bands higher; replaced if found?"* - a self-check item that cannot actually be performed, because
  nothing defines which words belong to which band.
- `writing/academic-writing/Index.md:116` - *"**No word-count ceiling corpus yet.**"*
- `writing/academic-writing/prompts/Generate_Lesson_Prompt_v6.17.md:37` - *"not a verified corpus;
  recalibrate once real student output exists."*

There is a structural reason this matters most for Reading: unlike Listening/Speaking, **Reading's
anchor texts are written, not sourced.** §0.2 instructs *"**Write** toward the middle-to-upper part
of each range."* Nothing sources or cites a Reading passage, so its vocabulary is entirely at a
model's discretion - and equally, entirely controllable the moment a list exists. The one place
real lexical control exists today is an accident: Listening/Speaking borrows VOA Learning English's
published "Words in This Story" glossaries.

With the datasets present as data, §0.3 item 4 becomes mechanically checkable and the two admitted
"no verified corpus" gaps close.

**Why this is not proposed here.** Per `CLAUDE.md`, landing a rule like this in `shared/` triggers
the generalization pass: sweep every prompt in all three modalities, bump each restating prompt's
version, update every `Index.md` reference, add self-check items, and sweep already-generated
lessons. That is a large, repo-wide change and belongs behind its own decision, not smuggled in as
a side effect of a design document.

---

## J. Open questions and deferred decisions

1. **Where the built system lives.** Separate repo (it is software, and `CLAUDE.md` states this is
   a content repo with no code) versus a lesson type under each modality. Currently the repo
   contains zero code: no `.py`/`.js`/`.sh`/`.json`, no `scripts/` or `tools/`, one `.mp3`, and an
   empty `.claude/`. **Partly settled in practice:** the audio tooling is Python + edge-tts +
   ffmpeg and already exists outside this repo, so at minimum the audio layer lives outside it. That
   does not decide where the inventory, generator, and coverage store live.
2. ~~**Can the existing audio script produce reduced forms?**~~ **Resolved** - partly, and the
   partial answer reshaped §G. Orthographic reductions and flapping yes; elision, assimilation and
   linking no, because edge-tts exposes no phoneme control. See §G4. One empirical check remains:
   whether a slowed pass restores citation forms (the reduced-forms test).
3. **How is a student's initial known-set established?** There is no placement mechanism anywhere
   in this repo. Task Levels are self-selected with no rule for who assigns them or on what
   evidence. §F is arithmetic over a known-set that nothing currently produces.
4. **Per-student or per-class tracking?** Per-student is what makes §A3 true; per-class is what is
   administratively feasible. This is the main scope fork.
5. **Is the game a distinct product, or homework attached to existing lessons?** Bears on §H's
   relationship to `learningobjectives.csv`.
6. **Licence verification for every dataset** before anything is committed (§B2).
7. **Encounter thresholds per axis** (§D2) - 10 is a starting point drawn from vocabulary research,
   not a finding about grammar or functions.
8. **Does the extensive strand feed back into the intensive lessons at all**, or run fully parallel?
9. **Are the slowed pass and the natural pass one artifact or two?** §G3 requires both. If they are
   two artifacts, §D's encounter model counts them separately and a student could meet only one; if
   one artifact with two renderings, the encounter is atomic but the model needs a per-rendering
   flag to enforce "at least one natural-rate encounter." The second is probably right, but it
   changes the schema in §D1.
10. **Is per-speaker rate variation within a dialogue worth having?** The pipeline currently applies
    one rate to every line of a dialogue. Real conversation does not work that way, and a
    faster interlocutor is a realistic difficulty lever - but it complicates the manifest and makes
    the §G3 two-pass rule ambiguous at line granularity.

---

## K. Sources

**Hours and levels**
- Cambridge English, [How long does it take to learn a language?](https://www.cambridge.org/elt/blog/2018/10/11/how-long-learn-language/)
- Cambridge English, [Guided learning hours](https://support.cambridgeenglish.org/hc/en-gb/articles/202838506-Guided-learning-hours)

**Lexical coverage thresholds**
- Van Zeeland, H. & Schmitt, N. (2013). [Lexical Coverage in L1 and L2 Listening Comprehension: The Same or Different from Reading Comprehension?](https://academic.oup.com/applij/article-abstract/34/4/457/199564) *Applied Linguistics* 34(4), 457-479.
- Laufer, B. & Ravenhorst-Kalovski, G. C. (2010). Lexical threshold revisited. *Reading in a Foreign Language* 22(1).

**Word and phrase inventories**
- Browne, C., Culligan, B. & Phillips, J. [The New General Service List](https://www.newgeneralservicelist.org/) and [NGSL-Spoken](https://www.newgeneralservicelist.org/new-general-service-list-project-18); rationale in [A New General Service List: The Better Mousetrap We've Been Looking For?](http://vli-journal.org/issues/03.2/vli.v03.2.browne.pdf) *Vocabulary Learning and Instruction* 3(2).
- [CEFR-J datasets, Open Language Profiles](https://github.com/openlanguageprofiles/olp-en-cefrj) - free for research and commercial use with citation.
- [English Profile](https://www.englishprofile.org/) (English Vocabulary Profile, English Grammar Profile).
- Martinez, R. & Schmitt, N. (2012). [A Phrasal Expressions List](https://www.lextutor.ca/tests/pvst/martinez_schmitt_2012.pdf). *Applied Linguistics* 33(3), 299-320.
- van Ek, J. A. & Trim, J. L. M. [Threshold 1990](https://ealta.eu/documents/resources/Threshold-Level_CUP.pdf) and *Waystage 1990*. Council of Europe.

**Listening perception**
- Field, J. (2003). [Promoting perception: lexical segmentation in L2 listening](https://academic.oup.com/eltj/article/57/4/325/455304). *ELT Journal* 57(4), 325-334.
- Renandya, W. A. & Farrell, T. S. C. ["Teacher, the tape is too fast!" Extensive listening in ELT](https://www.researchgate.net/publication/249252935_'Teacher_the_tape_is_too_fast'_Extensive_listening_in_ELT). *ELT Journal*.

**Encounters and extensive practice**
- Webb, S. (2007). [The Effects of Repetition on Vocabulary Knowledge](https://academic.oup.com/applij/article-abstract/28/1/46/174744). *Applied Linguistics* 28(1), 46-65.
- Karlin, O. & Karlin, S. [Developing L2 listening comprehension through extensive and intensive listening](https://benjamins.com/catalog/aila.22015.kar). *AILA Review*.

**Synthesis**
- [Text-to-Speech in High-Variability Phonetic Training](https://callej.org/index.php/journal/article/download/713/485/4137). *CALL-EJ*.

---

## Changelog

**Current version: v1.2.** Created 2026-09-10. Non-normative design proposal; states no rules.

- **v1.2** (2026-09-10) - inventory built. §C2 rewritten against the real CEFR-J datasets:
  grammar sublevels give Levels 4 and 6 a genuine mapping, but a thin one (13 and 11 items),
  and only 34% of grammar rows carry their own level. Lexis confirmed banded.

- **v1.1** (2026-09-10) - audio tooling supplied and inspected. §G2 split into targeted vs
  observed categories; §G3 gained the two-pass enforcement mechanism; §G4 rewritten around
  edge-tts's real capabilities and its phoneme limit; §J item 2 closed, items 9-10 added.
- **v1.0** (2026-09-10) - initial draft.
