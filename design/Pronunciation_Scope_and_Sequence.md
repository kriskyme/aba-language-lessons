# Pronunciation Scope and Sequence - Design Spec (v1.0)

**Status:** non-normative design proposal. It states no rules and is wired into no prompt.
It exists so that a later fold-in pass has something to fold in.

**Companion document:** `Graded_Input_Engine_Spec.md` §G builds a connected-speech inventory
for the *listening* side. This document is its productive counterpart and deliberately reuses
its category names. Where the two touch, §G is authoritative on what the audio pipeline can
produce and this document is authoritative on what gets taught.

---

## A. Why this exists

Pronunciation is already running in every Listening/Speaking lesson. It is not missing; it is
unsequenced.

`listening-speaking/listening-speaking/prompts/Generate_Lesson_Prompt_v2.6.md` §0.4 holds a
**six-feature rotation bank** (content-word stress; thought-group pausing; linking; rising and
falling intonation; contrastive stress; reduced forms in fast speech, the last gated to
Advanced/Proficient). Day 2 Phase 3 gives it ten minutes on a three-sentence specification
(that prompt's lines 374-377). Self-check item 12 requires only that the feature be audible in
the real source. Every `Rotation_Log_<Band>.md` tracks which feature each lesson used.

A bank rotated for novelty answers "what did we not do last time," never "what comes next."
Three consequences, all observable in the generated content:

**A1. The bank has no entries below Level 3 or above Level 6.** Placing its six features on the
program's scale (§E below) puts content-word stress at Level 3, thought-group pausing / rising
and falling / list intonation at Level 4, contrastive stress at Level 5, and linking / reduced
forms at Level 6. Nothing exists for Levels 1-2 or 7-8.

**A2. Eight generated lessons therefore sit outside their band's task-Level range**
(`Program_Conventions.md` §B: Beginner 1-3, Intermediate 2-5, Advanced 4-7, Proficient 5-8):

| Lesson | Band (task Levels) | Feature taught | Its Level | Off by |
|---|---|---|---|---|
| `beginner/.../Lesson_1_WhatIsIt` | Beginner (1-3) | rising and falling intonation | 4 | +1 |
| `beginner/.../Lesson_3_FamilyPhotos` | Beginner (1-3) | thought-group pausing | 4 | +1 |
| `beginner/.../Lesson_4_HowAboutThis` | Beginner (1-3) | contrastive stress | 5 | **+2** |
| `intermediate/Module_1/Set_1/Lesson_3_Backpack` | Intermediate (2-5) | linking | 6 | +1 |
| `intermediate/Module_1/Set_2/Lesson_7_RosettaStone` | Intermediate (2-5) | linking | 6 | +1 |
| `advanced/Module_1/Set_2/Lesson_6_GodsAndGoddesses` | Advanced (4-7) | content-word stress | 3 | -1 |
| `proficient/.../Lesson_3_PapaHemingway` | Proficient (5-8) | rising and falling intonation | 4 | -1 |
| `proficient/.../Lesson_4_BeninPlaque` | Proficient (5-8) | thought-group pausing | 4 | -1 |

`Lesson_4_HowAboutThis` breaks the band-distance invariant outright: contrastive stress is two
bands above the Beginner centerpiece. And because the bank stops at Level 6, **the Proficient
band has never been taught a pronunciation feature at its own Levels**, in any lesson.

**A3. The bank is entirely prosodic.** Six features, zero segmentals. No sound, contrast,
cluster, or articulation has ever been taught in this program. Every one of the six comes from
the Sentence Focus and Thought Groups sections of the source in §C; that source's Units 1-5
(syllables and word stress) and Units 10-14 (every consonant) have never been touched.

Two assets go unused. `listening-speaking/listening-speaking/source/Pronunciation.txt` is
referenced by nothing. And `Generation_Quality_Standards.md` §D12's window-choice rule already
reaches for phonological criteria ("a word boundary, a weak form, a reduced auxiliary, a
flapped consonant") with no taxonomy to name them from. §E below is that taxonomy.

---

## B. The intelligibility-priority filter

Stated before any content, because it decides what is in this document at all.

> **A feature earns a place in the sequence only if getting it wrong makes a speaker harder to
> understand. A feature that only makes a speaker sound foreign is not taught.**

This is intelligibility work, not accent reduction. The distinction is not a courtesy; it is
what makes the sequence finite and what makes it defensible in a mixed-L1 room where no single
accent is the target.

Three consequences that bite:

**B1. Prosody outranks segmentals, so it is taught first.** Misplaced stress and missing
thought groups break a listener's ability to segment the stream at all; a substituted consonant
usually survives context. This is why the sequence in §E is prosody-first, and it is the same
argument `Graded_Input_Engine_Spec.md` §G1 makes from the listening side.

**B2. Some famous contrasts do not make the cut, and some unglamorous ones do.** A dental
fricative substituted with /t/ or /s/ ("tink," "sink" for "think") almost never causes a real
breakdown, because no English sentence hinges on it. A misplaced word stress ("*com*puter" for
"com*pu*ter") reliably does: the listener searches for a different word and finds none. The
sequence weights accordingly, and §E puts word stress at Level 1 while the dental fricatives
arrive at Level 3 as part of a voicing lesson rather than as a target in their own right.

**B3. What is dropped is dropped on purpose.** Features excluded by this filter and therefore
absent from §E: vowel quality matching to any single regional standard; /θ/ and /ð/ as accuracy
targets; the flap as a production target (it is taught for *perception* at Level 6, since
students must decode it, but never required in their own speech); rhoticity as a target; any
"sounds more natural" polish with no comprehension consequence.

**B4. The listener is half the system.** Level 8 includes listener-side intelligibility across
accents, because in a mixed classroom the students are each other's most frequent
interlocutors, and a program that only trains production has trained half the problem.

---

## C. What the source contains

`listening-speaking/listening-speaking/source/Pronunciation.txt` is the OCR'd scope and
sequence of Judy Gilbert's *Clear Speech*: 15 units, 3 appendices, 2 Extra Practice sections.

Its organizing decision is **prosody first**: syllables, then word stress, then sentence focus,
then consonants, then thought groups. Individual sounds come fourth, deliberately. That
ordering is the same claim B1 makes and is kept as the spine of §E.

| Section | Units | Concepts |
|---|---|---|
| Syllables | 1 | Counting syllables; syllable count in `-ed` and `-s` forms; silent letters |
| Vowels and Word Stress | 2-5 | Alphabet vs relative vowel sounds; the Two Vowel Rule and One Vowel Rule; stress and vowel length; clear vowels vs schwa; stress patterns for two-syllable words, word endings, two-syllable verbs, and compound nouns |
| Sentence Focus | 6-9 | Focus words; focus and content words; focus and structure words; Focus Rules 1-7; contractions and reductions; focus in conversation; disagreeing and correcting; emphasizing structure words |
| Consonants | 10-14 | Continuants and stops (/s/ and /t/; /r/ and /d/; /l/ and /d/); the /rd/ and /ld/ combinations; voicing (/s/-/z/, /f/-/v/, voiced and voiceless `-th-`); syllable length before a voiced consonant; aspiration; sibilants (/s/-/ʃ/, /z/-/ʒ/, /s/-/θ/, /ʃ/-/tʃ/, /dʒ/-/j/) and their effect on syllable count |
| Thought Groups | 15 | Chunking; signaling the end of a group with a pause; signaling it with falling pitch; Thought Group Rules 1 and 2; either/or questions; a series of items |
| Appendices | A-C | Parts of the mouth; tongue shapes for /s/ /z/ /t/ /d/ /θ/ /ð/ /r/ /l/; how often the vowel rules actually work |
| Extra Practice 1 | 8 parts | /r/-/l/; /n/-/l/; /v/-/w/; /v/-/b/; /f/-/p/; /θ/-/t/; silent and reduced `-t-`; linking |
| Extra Practice 2 | 3 parts | Advanced word stress; advanced sentence focus; advanced thought groups |

Two cross-cutting strands in the source are pedagogy rather than content, and both are adopted
in §F:

- **"Music of English"** - a short memorized exchange said as one chunk, carrying the unit's
  melody. The point is that a prosodic feature is a property of a whole phrase, so it is
  rehearsed as a whole phrase and never assembled word by word.
- **"Vowel Work"** - a spelling-to-sound pattern drilled alongside whatever else the unit
  teaches, so orthography is chipped at continuously rather than in one block.

---

## D. What is missing, and has to be added

*Clear Speech* is an intelligibility course of an older lineage and shows it in three ways. It
routes almost all vowel teaching through **spelling rules** rather than through the vowel
system (its own Appendix C concedes the rules only work so often). It treats connected speech
as a single Extra Practice afterthought. And it stops at the sentence: there is no
discourse-level prosody anywhere in it.

Twenty-two additions. Each is placed at a Level in §E; none is orphaned.

### D.1 Segmental

1. **The vowel system as a system.** The tense/lax pairs /iː/-/ɪ/, /uː/-/ʊ/, /ɛ/-/æ/,
   /ɑ/-/ʌ/-/ɔ/, and the diphthongs /eɪ aɪ ɔɪ aʊ oʊ/ as one closed set. *Why:* the Two and One
   Vowel Rules stay useful, but as spelling support underneath the system, not as the system
   itself. A student who only has the rules cannot place a vowel they meet in speech first.
2. **R-colored vowels** /ɚ ɝ/ and the vowel+/r/ set (car, care, cure, here, four). *Why:*
   essentially absent from the source, and a first-rank intelligibility feature in North
   American English, where a great many high-frequency words carry one.
3. **Consonant clusters as a system.** Initial s-clusters (/sp st sk spr str skr/), final
   clusters (/-sts -kts -lfθs/), and the two repair strategies learners actually use:
   **epenthesis** (inserting a vowel: "bus-uh," "es-tudent") and **deletion** (dropping a
   consonant). *Why:* naming the two repairs is what lets a student hear their own, and the
   source treats clusters only incidentally.
4. **The `-ed` rule (/t/ /d/ /ɪd/) and the `-s` rule (/s/ /z/ /ɪz/) as voicing-keyed
   pronunciation rules.** *Why:* the source has these only as syllable-count facts. Taught as
   voicing consequences they cost nothing extra, because voicing is already being taught, and
   they generalize to every regular verb and plural in the language.
5. **Glides /w/ and /j/, /h/** (both dropping and hypercorrective inserting), and **/ŋ/ vs /n/
   vs /ŋɡ/** (singer, finger, `-ing`). *Why:* a gap in the source's consonant coverage, and
   /ŋ/ is the one consonant English spelling genuinely cannot disambiguate.
6. **The American /t/ as one rule set:** flap (water, better), glottal stop (button, mountain),
   unreleased final, and deleted in a cluster. *Why:* the source has only "silent and reduced
   `-t-`" in Extra Practice. Taught as one set it becomes a *decoding* skill, which is where
   almost all of its value is.
7. **Dark /l/ vs clear /l/, and syllabic consonants /n̩ l̩/** (button, little). *Why:* a
   frequent source of a whole syllable being misheard or invented.
8. **Final-consonant release**, and unreleased stops before another consonant. *Why:* the
   production side of addition 3; the counterpart to epenthesis at the end of a word.

### D.2 Prosodic

9. **Intonation contours as a taught system**, beyond the source's two thought-group rules:
   falling on statements and wh-questions, rising on yes-no questions, non-final rise for
   continuation, rise-fall-rise for hedging and politeness, tag questions (rise means
   genuinely asking, fall means confirming). *Why:* the source teaches falling pitch as a
   boundary marker and stops. Contour choice carries speech-act meaning, and getting it wrong
   changes what was said, not how it sounded.
10. **Pitch key and range.** High key opens a topic, low key marks an aside. *Why:*
    load-bearing in a mixed classroom, where a transferred narrow range is heard as bored or
    rude. This gets misread as attitude rather than as accent, which makes it more costly than
    most segmental errors and almost never taught.
11. **Rhythm as stress-timing**, with **weak forms** taught as a closed list (to, for, of, and,
    a, can, was, have, been, him, her, them). *Why:* the source covers contractions but never
    inventories the weak forms, and a closed list is learnable in a way "reduce your function
    words" is not.
12. **Connected-speech processes as a unit:** linking C-V, C-C (the same consonant held once),
    V-V with /w/ and /j/ glides; **assimilation**; **elision**. *Why:* the source scatters
    these across one Extra Practice part. Together they are the single largest cause of
    listening breakdown (`Graded_Input_Engine_Spec.md` §G1).
13. **Contrastive and corrective stress** and the meaning shifts it produces (*I* didn't say
    that / I didn't say *that*). *Why:* the source's Focus Rules approach this and stop at
    "disagreeing and correcting" as a function, without the meaning-shift demonstration that
    makes the feature stick.
14. **Rate, pausing for effect**, and the accuracy-versus-fluency tradeoff. *Why:* students
    who slow down to be accurate often become *less* intelligible, because slowing destroys
    the rhythm a listener is using to segment. Naming this prevents a common self-inflicted
    injury.
15. **Discourse prominence:** given versus new information, and how the focus word moves
    across a paragraph rather than within a sentence. *Why:* the ceiling the source does not
    reach, and the difference between a Level 7 speaker and a Level 5 one.

### D.3 Pedagogy and meta

16. **A stated position on IPA.** *Why:* the source uses a partial in-house symbol key and the
    program has no position at all. See §H: a 12-symbol working set from Level 3, not the
    chart.
17. **Perception before production**, as an explicit principle: a contrast is discriminated
    (same/different, odd-one-out) before it is ever produced. *Why:* the highest-leverage
    single thing missing from the current Phase 3, which goes straight from marking to
    producing. A student who cannot hear a contrast cannot be drilled into it; the drill just
    reinforces the substitution.
18. **Diagnostic and progress measurement:** one repeatable read-aloud plus free-speech probe,
    scored for intelligibility and never for accent. *Why:* `Graded_Input_Engine_Spec.md` §J
    already records that no placement mechanism exists anywhere in this repo and that task
    Levels are self-selected. See §G.
19. **Self-monitoring and repair:** noticing mid-utterance, self-correcting, and the
    clarification routines that recover a breakdown ("sorry, *thirty*, three-zero"). *Why:*
    the only pronunciation skill that keeps working after the course ends.
20. **Spelling-to-sound beyond the vowel rules:** the `-ough` family, silent letters as a
    system, stress-shifting homographs. *Why:* extends the source's "Vowel Work" strand to the
    patterns its two rules do not reach.
21. **Paper-and-voice-safe articulatory technique.** The proprioceptive tests that need no
    mirror, no handout, and no device: hand on the throat for voicing, breath on the back of
    the hand for aspiration, jaw drop for vowel height, humming for nasals, a stretched-arm
    gesture for vowel length, a finger under the chin for syllable count. *Why:* this is what
    lets the strand survive `Generation_Quality_Standards.md` §D8 in a room whose only
    resources are a voice, a projector, paper, and a partner. The source's Appendices A and B
    assume mouth diagrams and mirrors; these are the replacements.
22. **The intelligibility-priority filter** (§B), stated before any content. *Why:* in a
    mixed-L1 room this is what governs whether a feature makes the sequence at all, and it is
    what keeps the strand from drifting into accent reduction.

---

## E. The sequence: 8 Levels, prosody first

One focus per Level, on the program's existing scale (`Program_Conventions.md` §A) so the
strand differentiates by task Level exactly the way every other task already does. Because a
band draws the task Levels §B assigns it, a Beginner lesson draws from Levels 1-3, an
Intermediate lesson from 2-5, an Advanced lesson from 4-7, a Proficient lesson from 5-8. The
pronunciation focus differentiates *within* a lesson; it is not one feature for the room.

Each Level carries a **prosodic focus** (the spine) and a **segmental focus** chosen so that
the sounds being worked are the ones that Level's prosody makes audible. Segmentals ride along
throughout rather than being banked into one late block, but they are never the organizing
principle.

### E.0 Summary

| Level | Band | Prosodic focus | Segmental focus |
|---|---|---|---|
| 1 | Beginner | **The beat.** Syllable counting; two-syllable word stress; the stressed syllable is longer, and length is the signal | Vowel length only: long versus short, no vowel quality yet |
| 2 | Beginner | **Clear vowel versus schwa.** Unstressed means reduced; the Two and One Vowel Rules as spelling support | Final consonants are pronounced: no added vowel, no dropped consonant. The `-s` and `-ed` three-way rules |
| 3 | Intermediate | **Sentence focus I.** Content versus structure words; one focus word per group; the weak-form list | Voicing: /s/-/z/, /f/-/v/, voiced and voiceless `-th-` |
| 4 | Intermediate | **Thought groups.** Chunking; pause and falling pitch at the end; list and either/or contours; yes-no versus wh-question contours | Continuants and stops (/s/-/t/, /r/-/d/, /l/-/d/); aspiration; vowel length before a voiced consonant |
| 5 | Advanced | **Sentence focus II.** Choosing the focus word in conversation; contrastive and corrective stress; emphasizing structure words | Sibilants (/s ʃ z ʒ tʃ dʒ/); r-colored vowels; initial s-clusters and final clusters |
| 6 | Advanced | **Connected speech.** Linking (C-V, C-C, V-V glides); assimilation; elision; contractions in the stream. Word-stress patterns: suffixes, compound nouns, noun/verb pairs | The American /t/ set (flap, glottal, unreleased, deleted); dark /l/; syllabic /n̩ l̩/ |
| 7 | Proficient | **Discourse prosody.** Given versus new; focus movement across a paragraph; non-final rise; rise-fall-rise for hedging; tag questions; pitch key | The vowel system consolidated: tense/lax pairs and the diphthong set |
| 8 | Proficient | **Register and repair.** Prosodic register shift; stance through pitch range; real-time self-monitoring and repair | Residual polish on the individual student's own remaining blockers; listener-side intelligibility across accents |

**Why this order.** Levels 1-2 buy the *rhythm* that lets a listener find word boundaries at
all. Levels 3-5 buy *prominence*, which tells a listener where the information is. Level 6
buys the ability to *decode* fast speech, which is a listening gain at least as much as a
speaking one. Levels 7-8 are the paragraph- and stance-level features that separate
"understood" from "persuasive." Every Level's contents were filtered through §B first
(addition 22): the ordering above is what that filter leaves once accent-only features are
removed.

**Where the current bank lands.** Content-word stress is Level 3. Thought-group pausing,
rising and falling intonation, and list intonation are Level 4. Contrastive stress is Level 5.
Linking and reduced forms are Level 6. All six sit in the L3-L6 middle, which is the whole of
§A1 restated: the bank cannot serve Beginner or Proficient because it contains nothing they
should be taught.

### E.1 Level 1 (Beginner) - The beat

- **Prosodic focus.** Words have a beat. Every word has a number of syllables, and in a
  two-syllable word one of them is stronger. The strong syllable is mainly *longer*, and length
  is the signal a listener uses.
- **Segmental focus.** Vowel length only, long versus short. No vowel quality at this Level:
  the student is learning that duration carries meaning before learning which vowel is which.
- **Perception target.** Given two spoken words, say how many beats each has. Given a
  two-syllable word said twice with the stress moved, say which one sounded like a real word.
- **Production target.** Say a known two-syllable word with the strong syllable clearly longer.
- **Technique.** A finger under the chin counts syllables, because the jaw drops once per
  syllable and a student can feel it without hearing it. A stretched-arm gesture shows length:
  the arm opens wide on the long syllable and stays closed on the short one. Both are silent,
  need nothing, and give the teacher a visible read of the whole room at once.
- **Rationale.** Syllable count and stress placement are the two errors that most reliably make
  a known word unrecognizable, because a listener searching the lexicon uses both as the index.
- **Music of English.** A two-line greeting exchange whose words are all one or two syllables,
  rehearsed as one chunk (addition 21's arm gesture on each strong syllable).
- **Engine-spec mapping.** Stress-timing (§G2, *observed*).
- **Traces to.** Source Unit 1, Unit 3. Addition 21 (both gestures).

### E.2 Level 2 (Beginner) - Clear vowel versus schwa

- **Prosodic focus.** The unstressed syllable is not just quieter, it is a *different vowel*.
  Schwa is the sound of not being stressed. The Two Vowel Rule and One Vowel Rule arrive here
  as spelling support for predicting which vowel a stressed syllable takes, not as the system.
- **Segmental focus.** Final consonants are pronounced: no vowel added after them, no consonant
  dropped from them. The `-s` rule (/s/ /z/ /ɪz/) and `-ed` rule (/t/ /d/ /ɪd/), taught as
  consequences of what the preceding sound does rather than as lists.
- **Perception target.** Hear whether a final consonant was there. Hear whether `-ed` added a
  syllable.
- **Production target.** Say a two-syllable word with a real schwa in the weak syllable, and a
  regular past-tense verb without adding a syllable that is not there.
- **Technique.** The arm gesture from Level 1 collapses to nothing on the schwa syllable. For
  final consonants, the student says the word, then says it again with the partner holding a
  hand up to stop them the instant they add a vowel: epenthesis is easier to hear in someone
  else than in yourself, which is why it is a partner task.
- **Rationale.** Schwa is the most frequent vowel in English, and epenthesis is the single most
  common source of a listener hearing an extra syllable and losing the word.
- **Music of English.** A spelling exchange in the source's own shape ("How do you spell
  'easy'? E-A-S-Y"), which forces the `-y` reduction into a memorized chunk.
- **Engine-spec mapping.** Stress-timing (§G2, *observed*).
- **Traces to.** Source Units 1, 2, 4. Additions 3 (epenthesis and deletion, named), 4, 8.

### E.3 Level 3 (Intermediate) - Sentence focus I

- **Prosodic focus.** A sentence has content words and structure words. The content words carry
  the meaning and are said long and clear; the structure words shrink. One word per group is the
  focus, and it is the longest, highest, and loudest thing in the group. The **weak-form list**
  is taught here as a closed set: to, for, of, and, a, can, was, have, been, him, her, them.
- **Segmental focus.** Voicing, as one idea covering three pairs: /s/-/z/, /f/-/v/, and voiced
  versus voiceless `-th-`. The `-s` and `-ed` rules from Level 2 are revisited here and are now
  *explained* rather than listed, because voicing is the explanation.
- **Perception target.** In a played stretch of the cited clip, mark which word was the focus.
  Hear a weak form and write the citation-form word it came from.
- **Production target.** Say a prepared sentence with exactly one focus word and visibly
  shrunken structure words.
- **Technique.** A hand flat on the throat: voiced sounds buzz, voiceless ones do not, and the
  student feels the difference on /sssss/ versus /zzzzz/ held for three seconds. For focus, the
  student taps the desk once, hard, on the focus word only.
- **Rationale.** Prominence is how a listener finds the information. A speaker who stresses
  everything has stressed nothing, and is harder to follow than one with several wrong
  consonants.
- **Music of English.** A two-turn exchange where the focus word moves between turns, said as
  two chunks.
- **Engine-spec mapping.** **Weak forms** (§G2, *targeted*).
- **Traces to.** Source Units 6, 7, 12. Additions 11, 21.

### E.4 Level 4 (Intermediate) - Thought groups

- **Prosodic focus.** Speech comes in groups, not in words. A group ends with a small pause and
  a falling pitch, and where the groups fall changes the meaning. Contours arrive as a set:
  falling on statements and wh-questions, rising on yes-no questions, the list contour (rise,
  rise, rise, fall), and either/or.
- **Segmental focus.** Continuants versus stops (/s/-/t/, /r/-/d/, /l/-/d/), aspiration, and
  the length of a vowel before a voiced versus voiceless consonant.
- **Perception target.** Mark the group boundaries on a printed stretch while listening to the
  clip. Hear whether a question was yes-no or wh-.
- **Production target.** Read a prepared sentence in correct groups, and ask both question types
  with the right contour.
- **Technique.** A slash drawn on the page at each boundary while listening: the mark is the
  answer, so the task is scoreable on paper with no speech. Breath on the back of the hand
  distinguishes aspirated from unaspirated stops. Vowel length before a voiced consonant reuses
  Level 1's arm gesture, now on "bat" versus "bad."
- **Rationale.** Wrong chunking is the prosodic error listeners find hardest to repair, because
  it corrupts the word boundaries themselves rather than a single word.
- **Music of English.** A three-item list said as one chunk with the list contour, then the same
  items as an either/or question.
- **Engine-spec mapping.** Stress-timing (§G2, *observed*).
- **Traces to.** Source Units 10, 11, 13, 15. Addition 9.

### E.5 Level 5 (Advanced) - Sentence focus II

- **Prosodic focus.** The focus word is now *chosen*, not assigned by a rule. Focus in
  conversation, disagreement and correction, contrastive stress and the meaning shifts it
  produces, and the case where a structure word takes the focus.
- **Segmental focus.** Sibilants as a set (/s ʃ z ʒ tʃ dʒ/); r-colored vowels /ɚ ɝ/ and the
  vowel+/r/ series; initial s-clusters and final clusters, with epenthesis and deletion named
  from Level 2 and now diagnosed.
- **Perception target.** Hear which of six readings of one sentence was said, and say what each
  one meant. Discriminate the sibilant pairs.
- **Production target.** Correct a partner's deliberately wrong statement using contrastive
  stress alone, with no added words.
- **Technique.** One printed sentence, six numbered readings, the partner says one and the
  listener writes the number and the meaning. This is a pure discrimination task on paper and is
  the clearest instance of addition 17 in the whole sequence.
- **Rationale.** Contrastive stress is where prosody stops being delivery and becomes grammar:
  the same words carry different propositions, and a speaker without it cannot disagree
  precisely.
- **Music of English.** A correction exchange ("Our copier isn't working." / "Our *what's* not
  working?"), which is the source's own example and carries the feature exactly.
- **Engine-spec mapping.** None directly; this is a productive feature with no receptive
  counterpart in §G2.
- **Traces to.** Source Units 8, 9, 14, Extra Practice 1 parts 1-6. Additions 2, 3, 13.

### E.6 Level 6 (Advanced) - Connected speech

- **Prosodic focus.** Words are not separated in speech. Linking C-V, C-C (the same consonant
  held once, not said twice), and V-V with an intruding /w/ or /j/. Assimilation and elision.
  Contractions and lexicalised reductions as they actually occur in the stream. Word-stress
  patterns are consolidated here: stress by suffix, compound nouns, and the noun/verb pairs
  (*a* **su**spect / *to* sus**pect**).
- **Segmental focus.** The American /t/ as one rule set: flap, glottal stop, unreleased final,
  deleted in a cluster. Dark versus clear /l/. Syllabic /n̩ l̩/. The glides /w/ and /j/ (already
  present as the intrusion in V-V linking) and /h/ dropping. And /ŋ/ versus /n/ versus /ŋɡ/,
  which belongs here because the `-ing` reduction is itself a connected-speech fact.
- **Perception target.** This Level is mostly receptive. Hear /wɒtʃəgənədu/ and write "What are
  you going to do?" Hear a flapped /t/ and identify the citation word.
- **Production target.** Link across a prepared phrase, and use contractions in the stream.
  **The flap and the glottal stop are not production targets** (§B3): the student must decode
  them, never produce them.
- **Technique.** The student writes the citation form under a heard reduced form. This is the
  single highest-yield paper task in the sequence, and the Day 1 §D12 verification window
  already provides its material.
- **Rationale.** Field (2003), cited in `Graded_Input_Engine_Spec.md` §G1: L2 listening
  breakdown is at segmentation. A student who knows every word in a sentence often cannot
  recognize it spoken. This Level is where that is directly attacked.
- **Music of English.** A fast casual exchange containing three lexicalised reductions, learned
  as sound first and decoded to spelling afterwards.
- **Engine-spec mapping.** **Contractions**, **lexicalised reductions**, **flapping** (§G2,
  *targeted*); **elision**, **assimilation**, **linking and intrusion** (§G2, *observed*).
- **Traces to.** Source Unit 5, Extra Practice 1 parts 7-8, Extra Practice 2 part 1. Additions
  5, 6, 7, 12.

### E.7 Level 7 (Proficient) - Discourse prosody

- **Prosodic focus.** Prominence across a paragraph rather than a sentence: given information
  de-accents, new information takes the focus, and the focus therefore *moves* as a topic
  develops. Non-final rise for continuation. Rise-fall-rise for hedging and politeness. Tag
  questions, where a rise genuinely asks and a fall confirms. Pitch key: high opens a topic, low
  marks an aside.
- **Segmental focus.** The vowel system consolidated at last: the tense/lax pairs /iː/-/ɪ/,
  /uː/-/ʊ/, /ɛ/-/æ/, /ɑ/-/ʌ/-/ɔ/, and the diphthongs as a closed set. The Two and One Vowel
  Rules from Level 2 are re-presented here as what they are, useful spelling heuristics over a
  system the student now hears.
- **Perception target.** Across a paragraph of the cited clip, mark where the focus moves and
  say what became new. Distinguish an asking tag from a confirming one.
- **Production target.** Deliver a prepared paragraph in which the focus moves correctly, and
  hedge a claim with rise-fall-rise rather than with added words.
- **Technique.** A printed paragraph with each content word in a box, the student ticking the
  boxes that were prominent while the clip plays, then comparing to a partner's ticks. Pitch
  contour is drawn as a line above the text.
- **Rationale.** This is where prosody carries stance and information structure rather than
  word identity. A speaker at this Level is intelligible already; what they lack is the ability
  to signal what matters and how sure they are.
- **Music of English.** A hedged disagreement in rise-fall-rise, and the same content said flat,
  so the pair demonstrates the meaning difference.
- **Engine-spec mapping.** None directly; §G2 has no discourse tier.
- **Traces to.** Source Extra Practice 2 parts 2-3. Additions 1, 9, 10, 15, 20.

### E.8 Level 8 (Proficient) - Register and repair

- **Prosodic focus.** Prosodic register: the same content delivered as a presentation, as a
  meeting contribution, and as a casual aside, with the pitch range, rate, and pausing that each
  calls for. Stance and attitude through range. Real-time self-monitoring: noticing an error
  mid-utterance and repairing it without stopping.
- **Segmental focus.** Residual polish, and this is the one Level whose segmental content is
  **individual**: the student works on their own remaining blockers, identified by the §G
  diagnostic, not on a class-wide list. Plus listener-side intelligibility across accents.
- **Perception target.** Hear a recorded speaker and say which register they are in and what
  signalled it. Understand a classmate whose L1 is not yours, and identify what made a
  particular stretch hard.
- **Production target.** Deliver one piece of content in two registers. Repair a self-detected
  error in flight using a clarification routine ("sorry, *thirty*, three-zero").
- **Technique.** Register pairs are produced back to back and a partner names the difference
  from a printed list of four features (rate, range, pausing, focus density). Repair is
  rehearsed as a fixed routine so it is available under pressure.
- **Rationale.** Self-monitoring is the only pronunciation skill that keeps improving after
  instruction stops, and register control is what an advanced speaker is usually being judged
  on. The listener-side work is here for §B4's reason: in a mixed classroom the students are
  each other's most frequent interlocutors.
- **Music of English.** No fixed chunk at this Level. The student's own repair routine is the
  memorized phrase.
- **Engine-spec mapping.** None; §G2 is receptive and level-neutral.
- **Traces to.** No source unit. Additions 10, 14, 19, and the individual half of 18.

---

## F. How to teach it: the five-move micro-cycle

Taught on its own, one focus is one cycle of five moves in 8-12 minutes. The cycle is shaped to
satisfy the constraints the program already imposes, so it folds into Day 2 Phase 3 unchanged.

1. **Notice.** The feature is heard first, in the lesson's own cited clip, through the
   classroom speakers. Students mark what they heard on paper: which of these two did she say,
   where did her voice fall, how many beats. **No rule has been stated yet.**
2. **Rule.** One sentence, said once, with the physical test attached ("voiced sounds buzz, put
   a hand on your throat"). Never a chart, never a diagram.
3. **Discriminate.** Same/different or odd-one-out on printed minimal pairs, a partner reading
   and the listener marking. This is addition 17 and it is the move the current Phase 3 skips
   entirely: it goes straight from marking to producing, which drills a substitution the
   student cannot yet hear.
4. **Produce as a chunk.** The source's "Music of English" move. A short memorized exchange
   carrying the feature, said whole rather than assembled word by word, because a prosodic
   feature is a property of the phrase.
5. **Transfer.** The feature is carried into the speaking output the lesson was already going
   to produce, and a partner checks it against **one** printed yes/no criterion. Never a grade,
   never a whole-class confidence vote.

### F.1 Why this shape clears the existing rules

- **`Generation_Quality_Standards.md` §D12.** Moves 1, 3, and 5 are exactly Commit, Verify, and
  Return unsupported. Move 1 commits with no rule and no support on the page; move 3 reveals
  the contrast bounded to the stretch the task turned on; move 5 re-encounters it with the
  support withdrawn, inside the lesson's own output. Nothing has to be bolted on.
- **§D8, self-contained.** Moves 1 and 4 need only the cited clip and the teacher's voice; move
  3 needs paper and a partner; moves 2 and 5 need neither. No prop, no picture card, no device,
  nothing prepared before class. This is what addition 21 exists to guarantee, and it is why the
  source's mirror-and-mouth-diagram appendices are not adopted.
- **§D11, room-neutral.** Every move runs from where students sit.
- **§E6, concrete prompts at Beginner and Intermediate.** Every move produces a visible product:
  a mark, a number, a circled option, a said chunk. No move asks a student how they feel about
  their pronunciation.
- **§D5, teaching precedes practice.** Move 2 precedes moves 3-5. Move 1 deliberately precedes
  move 2, which is not a violation: move 1 is input, not practice of a taught thing.

### F.2 What a standalone pronunciation lesson looks like

Three or four cycles back to back, ordered so that a perception-heavy cycle alternates with a
production-heavy one, on features from adjacent Levels rather than one Level. The existing
10-minute Day 2 Phase 3 is exactly one cycle, which is the reason this document recommends
folding in rather than building a separate lesson type.

---

## G. Diagnostic

Addition 18. `Graded_Input_Engine_Spec.md` §J open question 3 records that **no placement
mechanism exists anywhere in this repo** and that task Levels are self-selected. This does not
solve that in general; it gives the pronunciation strand a probe it can run in the room.

**Two parts, roughly six minutes per student, run once at intake and once mid-year.**

- **Part 1, read-aloud.** A fixed 60-word passage, the same one every time, written to contain
  each of the sequence's Level markers at least once: two-syllable stress pairs, a schwa-heavy
  polysyllable, three weak forms, a two-group sentence, one contrastive pair, one consonant
  cluster, one linking site.
- **Part 2, free speech.** Ninety seconds on a fixed prompt requiring narration, so rhythm is
  not being read off a page.

**Scoring is intelligibility, never accent.** The rater marks only:

1. **Breakdown count.** How many times did the rater have to re-listen or guess? Nothing else
   on the form matters as much as this number.
2. **What caused each breakdown**, coded to a Level from §E.0. Three breakdowns all coded to
   Level 1 places the student differently from three spread across Levels 4-6.
3. **The highest Level at which the student is already reliable.** Placement is the Level
   *above* it.

There is no accent scale, no five-point "nativeness" rating, and no comparison to a model
speaker. A student who is fully intelligible with a strong accent scores clean, which is the
whole point of §B.

**Placement back into §E.** The diagnostic's output is one Level per student. In a band whose
task Levels span 2-5, this is what decides which of those four a given student's pronunciation
task should sit at, rather than the self-selection every other task in the program currently
uses.

---

## H. The IPA working set

Addition 16. The position: **twelve symbols, introduced from Level 3, not the full chart.**

A symbol earns a place only when English spelling cannot disambiguate the sound. Where
spelling is reliable (`ch` is always /tʃ/, `j` is always /dʒ/, `sh` is almost always /ʃ/), the
spelling is used and the symbol is not taught.

| | Symbol | Anchor word | Why it is needed |
|---|---|---|---|
| 1 | /ə/ | *about* | The most frequent vowel in English and the one with no spelling of its own. Level 2's entire focus. |
| 2 | /ɪ/ | *sit* | Contrasts with 3; spelling `i` covers both. |
| 3 | /iː/ | *seat* | Contrasts with 2. |
| 4 | /ɛ/ | *bed* | Contrasts with 5; spelling `e`/`a` overlaps. |
| 5 | /æ/ | *bad* | Contrasts with 4. |
| 6 | /ʌ/ | *cup* | Spelling `u`, `o`, `ou` all reach it. |
| 7 | /ɚ/ | *teacher* | The r-colored vowel; no spelling predicts it. Level 5. |
| 8 | /θ/ | *think* | `th` spells both 8 and 9. |
| 9 | /ð/ | *this* | Contrasts with 8. |
| 10 | /ʃ/ | *she* | Needed only to anchor 11. |
| 11 | /ʒ/ | *measure* | Has no spelling at all. |
| 12 | /ŋ/ | *sing* | `ng` spells both /ŋ/ and /ŋɡ/ (singer versus finger). |

Deliberately excluded: /uː ʊ ɑ ɔ/ (handled by anchor words: book, boot, father, thought),
/tʃ dʒ/ (spelling is reliable), and every diphthong (taught as a set at Level 7 by anchor word,
not by symbol). Length marks are shown but not drilled.

**Constraint from the engine spec.** `Graded_Input_Engine_Spec.md` §G4 records that the audio
pipeline exposes no phoneme control and that a pronunciation cannot be forced with IPA. The
symbols in this table are therefore a *notation for students and teachers on paper*, never an
input to synthesis. Every audio model in the strand comes from the cited human clip or the
teacher's voice.

---

## I. L1-issue appendix

A teacher reference, consulted per student. It is deliberately **outside §E**: the sequence is
ordered by universal intelligibility load so that it works in a mixed classroom, and folding
L1-specific content into it would make the sequence wrong for everyone not in that group.

Use this to predict which students will struggle at which Level, not to change what is taught.

| L1 family | Rhythm transfer | Predicted trouble, by §E Level |
|---|---|---|
| East Asian (Mandarin, Cantonese) | Syllable-timed; tone-language pitch transfer | L1 syllable count; L2 final consonants (deletion), `-s`/`-ed`; L4 contours read as tone; L6 clusters |
| Japanese, Korean | Mora- or syllable-timed | L2 **epenthesis** (the signature issue: "bus-uh"); L3 /f/-/v/; L5 /r/-/l/, s-clusters; L1 syllable count inflated by inserted vowels |
| Romance (Spanish, Portuguese, Italian) | Syllable-timed | L2 schwa (resists reduction, all vowels stay clear); L3 weak forms; L5 initial s-clusters ("es-tudent"); L7 /iː/-/ɪ/ |
| French | Syllable-timed, phrase-final stress | L1 word stress (placed at the end by default); L3 focus; L5 /h/ dropping; L7 /iː/-/ɪ/ |
| Slavic (Russian, Polish) | Stress-timed already | L3 voicing (final devoicing: "bed" as "bet"); L4 contours flattened; articles absent from weak-form work |
| South Asian (Hindi, Urdu, Bengali, Tamil) | Syllable-timed | L1 stress placement; L4 retroflex stops and aspiration; L7 pitch range narrow; often highly fluent and still misheard, which makes L3 focus the high-yield Level |
| Arabic | Stress-timed | L2 vowel epenthesis into clusters; L3 /p/-/b/; L7 the three-vowel system expanding to English's set |
| Southeast Asian (Vietnamese, Thai) | Syllable-timed, tonal | L2 final consonants (unreleased or dropped); L4 contours read as tone; L6 clusters |

Two standing notes. First, **stress-timed L1s are not exempt**: they transfer their own
rhythm's details and often flatten English contours. Second, in a genuinely mixed room the
**listener-side work at Level 8 (§B4) matters more than any row of this table**, because the
students hear each other far more than they hear a model speaker.

---

## J. Open questions for the fold-in pass

Named so the boundary of this document is explicit.

1. **Replace §0.4's flat bank with §E.0's per-Level table**, and bump
   `Generate_Lesson_Prompt_v2.6.md` to v2.7. The bank's six features map onto Levels 3-6 as
   §E.0 states, so the mapping does not need re-deriving.
2. **Rewrite the three-sentence Phase 3 spec as §F's five-move cycle**, with the per-band
   scaffolding the current spec has none of.
3. **Codify "Say It Like a Native Speaker."** All 24 packets print it as a `.spotlight-box`,
   and it is defined in no prompt and no style guide.
   `Generate_Student_Packet_Prompt_v2.7.md` §2.11 describes something different (a "short bonus
   line under the relevant task") that no packet actually does. This needs a Style Guide §H.1
   entry, a delta class for a minimal-pair or contour-marking item, and matching §I self-check
   items. The heading itself is also worth revisiting against §B: "like a native speaker" names
   a target this document explicitly rejects.
4. **Does any of this belong in `shared/`?** Run CLAUDE.md's swap test then, not now. The
   sound-symbol layer plausibly generalizes: Reading's CSV Level 1-3 rows are decoding rows and
   Writing's are "spell from sound," so §H's working set and Level 2's `-s`/`-ed` rules may be
   program-wide facts rather than Listening/Speaking ones. The prosodic spine almost certainly
   is not.
5. **Should the CSV taxonomy gain phonological objectives?** No row in
   `learningobjectives.csv` names one today, which is why the strand has no can-do statement to
   cite and self-check item 12 can only ask whether the feature was audible.
6. **Retrofit the eight out-of-band lessons in §A2.** Not mechanical: each needs a
   Level-appropriate feature chosen against what its own cited clip actually contains, then the
   `.md` Phase 3 rewritten and the packet regenerated. Do it when each lesson is next touched,
   folding it into the §D12 pass those lessons are already queued for.
7. **Where does the diagnostic (§G) run?** It is not a lesson, not homework, and not a Set
   assessment. It may need a fourth artifact type, or it may attach to the Module Lesson Plan
   as an intake step.

---

## K. Sources

- Gilbert, J. B. *Clear Speech* (scope and sequence extracted at
  `listening-speaking/listening-speaking/source/Pronunciation.txt`). The prosody-first
  ordering, the Focus Rules, the Two and One Vowel Rules, and the "Music of English" and
  "Vowel Work" strands are its.
- Field, J. (2003). *Promoting perception: lexical segmentation in L2 listening*. ELT Journal
  57(4), 325-334. Cited via `Graded_Input_Engine_Spec.md` §G1 for the segmentation claim that
  Level 6 rests on.
- Jenkins, J. *The Lingua Franca Core*. The basis for §B's filter and for the exclusions in
  §B3.
- `Graded_Input_Engine_Spec.md` §G (connected-speech inventory, receptive) and §G4 (the
  no-phoneme-control constraint).

---

## Changelog

**Current version: v1.0.** Created 2026-09-10. Non-normative design proposal; states no rules.

- **v1.0** (2026-09-10) - initial draft. Extracts the `Pronunciation.txt` inventory (§C),
  adds the 22 gaps it leaves (§D), sequences all of it across the program's 8 Levels (§E),
  and states the teaching model (§F), the diagnostic (§G), the IPA position (§H), and the
  mixed-classroom L1 appendix (§I). Documents the three defects in the current arrangement
  that motivated it: no progression, eight out-of-band lessons, and zero segmental content
  (§A). Reconciles category names with `Graded_Input_Engine_Spec.md` §G2.
