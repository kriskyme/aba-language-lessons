# Passage Reading Index
_This is a living index, not a prompt - update it whenever a doc in the family is added, renamed, or synced to a
new lesson-prompt version, so it never falls out of date the way the individual prompts did before this project
started tracking them here. Version history lives in `Changelog.md`._

## What this document is

A single reference for everything in the Passage Reading prompt family: what each file does, whether it's in sync
with the current lesson-generation prompt, and the order to actually run them in to produce a Set of lessons.
"Passage Reading" is the lesson type these prompts generate: a fixed 2-day cycle built around one shared anchor
text. See `shared/Program_Conventions.md` §C for what a Set is; today that's **4 lessons** (4 x 2-day cycles),
since a Passage Reading lesson is a 2-day cycle - do not plan or expect 8 lessons per Set. Since Set size and
module size are numerically identical today, every Module/Band planned so far is that Module/Band's Set 1 - see
"Module 1 progress" below. A second lesson type, **Novel Reading**
(variable-length, multi-chapter), is planned as a sibling `../novel-reading/` folder with its own file family,
prompts, and rotation log - see `../Index.md` for the modality-level list of lesson types. Nothing here
currently supports it.

## File index

| File                                                              | What it does                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Sync status                        |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| `Generate_Lesson_Prompt_v3.5.md` | Generates one 2-day lesson: anchor text, tiered tasks, comprehension work. The current version. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; states only what is true of a passage-reading lesson (Section 0.2 ceilings, idioms, refresher text, genre bank, paragraph lettering and footnotes, Phase 3 protocols, the Reading Execution Rules and tiered framework) and points to the shared files for everything modality-neutral. Section 0.3's self-check is the shared Quality Standards §F list plus 11 Reading-only items. Section numbering 0.1-0.10 is unchanged from v2.10 so companion prompts' cross-references still hold. | Current (v3.5, 2026-09-09: room-neutral hooks and protocols - Panel Round, Rotating Partners, small-group discussion, K-W-L Chart, Take a Side - see `Changelog.md`) |
| `Generate_Module_Lesson_Plan_Prompt_v2.2.md` | Plans **one Set** (4 lessons: topics, genres, strategy/hook/protocol rotation, vocabulary themes, task-Level-to-objective mapping) before any lesson content is generated. Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; Rotation Log mechanics and the cross-Set / cross-Module adjacency rules now point to Conventions §F, and the prompt keeps only its own column list, log-entry template, the band-conditioned real-referent topic rule with its fabricated-quote guardrail, and the plan table's column definitions. Reading-modality objectives only. | Current (v2.2, 2026-09-09: room-neutral rotation banks) |
| `Rotation_Log.md`                                                  | Overview only as of the per-Band split: purpose, notes that apply across every Band (the miscount correction, the Sets-concept introduction), and links to each Band's own log. | N/A (data, not a prompt)           |
| `Rotation_Log_Beginner.md`                                         | Same, for the Beginner Band. Created 2026-09-10 with this Band's first Set. | N/A (data, not a prompt)           |
| `Rotation_Log_Intermediate.md`                                     | Running record of every approved Intermediate-Band Set's genre/strategy/hook/protocol/vocabulary/topic choices, one row per lesson, nested by Set. Read before planning a new Set; appended to after a plan is approved. | N/A (data, not a prompt)           |
| `Rotation_Log_Advanced.md`                                         | Same, for the Advanced Band. A new Band's file is created lazily the first time a lesson in that Band is generated. | N/A (data, not a prompt)           |
| `Rotation_Log_Proficient.md`                                       | Same, for the Proficient Band. Created 2026-09-10 with this Band's first Set. | N/A (data, not a prompt)           |
| `Changelog.md`                                                     | Version history for this prompt family. Not a prompt itself. | N/A (data, not a prompt)           |
| `Generate_Homework_Prompt_v2.3.md` | Generates one homework assignment (vocabulary/idiom production plus skill practice) from a single completed 2-day lesson, general track only, one section per task Level keyed to its position. Run with the two shared files pasted alongside; Respectful Tiers and item quality point to Quality Standards; Section 3 is Quality Standards §F plus 7 Reading items. | Current (v2.3, 2026-09-09: any exemplar on an `Answer note:` line, never in the item - see `Changelog.md`) |
| `Generate_TOEFL_Extension_Prompt_v1.1.md` | Generates an optional TOEFL iBT Reading task packet from a completed Advanced/Proficient lesson, working from the shared anchor text and Phase 1 vocabulary only. v1.1 adds Markdown heading syntax (it was the only prompt without any), a paste bundle, and pointers to Quality Standards §C for distractor quality; content unchanged. | Current (v1.1) |
| `Generate_Assessment_Prompt_v5.2.md` | Builds a differentiated assessment (one section per task Level plus study guides) from a completed Set (or an explicitly scoped checkpoint or multi-Set span). Run with `shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md` pasted alongside; keeps what is Reading-specific (Source/Tests tagging, lesson-blocks with one new passage per lesson and the skip-a-lesson procedure, task types by Level position, the Foundation Support check's format, the study guide, the Scoring Guide) and points to Quality Standards §C for item quality, which is where Reading's assessments now pick up the distractor-plausibility and padded-word-bank rules they never had. Section 3 is Quality Standards §F plus 11 Reading items. | Current (v5.2, 2026-09-09: embedded images cited in the `.md` and rowed into the Set's `Image_Credits.md`) |
| `Generate_Student_Packet_Prompt_v2.7.md` | Takes one completed 2-day lesson and produces a single, print-ready, black-and-white student handout (self-contained HTML) with every teacher-facing term translated to plain instructions. Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; states only what is specific to a Reading packet (Unit A/B labels, the worked-model box, the standing annotation key, Phrase Spotlight idiom rendering with `.idiom-tag`, refresher-text blocks, Reading's own translation rows) and points to the Style Guide for the translation table, star and lettered-Task rules, the regeneration rule, and the shared packet self-check. Section 5 is Style Guide §I plus 9 Reading items. Student version only. | Current (v2.6, 2026-09-09: room-neutral protocol translations; v2.5, same day: both masthead sections carry the meta stack; v2.3, same day: Answer notes stripped, stems carried without answer-stating parentheticals, stops printed as questions - see `Changelog.md`); every packet under `lessons/` was generated against v1.3-v1.12 and hand-swept to the shared conventions in earlier passes (see `Changelog.md`); all 8 carry the two-line `.masthead-meta` stack (modality `·` Module name, then Band and version code) on both mastheads as of 2026-09-09 |
| `Generate_Assessment_Student_Packet_Prompt_v2.0.md` | Takes one completed Assessment `.md` and produces the student handout: self-contained task-Level sections with page breaks, every tag and the Scoring Guide stripped, a per-Level `Objective:` statement, full passages reprinted per section, no checklist substitute for rubric-scored items. Run with `shared/Student_Packet_Style_Guide.md` pasted alongside; Section 5 is Style Guide §I plus 6 Reading items. | Current (v2.0) |
| `learningobjectives.csv` (project file)                           | Source of truth for every Learning Objective: 192 rows across 8 Levels x 3 Modalities x 8 Modules (Describing, Narrating, Explaining, Instructing, Evaluating, Arguing, Transacting, Socializing). Every prompt above pulls from this, never from an invented difficulty curve.                                                                                                                                                                                | N/A (data)                         |
| `TOEFL Reading.pdf` (project file)                                | Reference material for the TOEFL extension prompt.                                                                                                                                                                                                                                                                                                                                                                                                             | N/A (reference)                    |

## Module 1 progress, Intermediate Band (Describing, Intermediate) - Set 1 COMPLETE

Plan approved and logged to the Rotation Log as Set 1. **All 4 lessons of this Set are generated** - this is
the complete Set, not half of an 8-lesson plan:

| File                                                                      | Lesson # | Topic                                                                         | Status                       |
| -------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------ | ----------------------------- |
| `Module_1/Set_1/Lesson_1_Kitchen/Lesson1_Kitchen.md`               | 1        | A traditional wood-fired kitchen in a trullo home in Puglia, southern Italy   | Generated, self-check passed |
| `Module_1/Set_1/Lesson_2_YoyogiPark/Lesson2_YoyogiPark.md`         | 2        | A newly renovated section of Yoyogi Park in Tokyo                             | Generated, self-check passed |
| `Module_1/Set_1/Lesson_3_RunningShoes/Lesson3_RunningShoes.md`     | 3        | What podiatrists and running-shop staff recommend when choosing running shoes | Generated, self-check passed |
| `Module_1/Set_1/Lesson_4_WynwoodWalls/Lesson4_WynwoodWalls.md`     | 4        | A street artist describes painting a mural in Wynwood Walls, Miami            | Generated, self-check passed |

**Homework (Step 3), general track, one per lesson, all 4 complete:**

| File                                              | For lesson | Status                                           |
| -------------------------------------------------- | ---------- | ------------------------------------------------- |
| `Module 1 Homework - Lesson 1 (Kitchen).md`       | Lesson 1   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 2 (Park).md`          | Lesson 2   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 3 (Running Shoes).md` | Lesson 3   | Generated, self-check passed, after-Day-1 timing |
| `Module 1 Homework - Lesson 4 (Mural).md`         | Lesson 4   | Generated, self-check passed, after-Day-1 timing |

**Assessment (Step 5), covering all 4 lessons (Task Levels 2/3/4/5) - this is the full end-of-Set assessment,
not a partial cumulative one. Generated 2026-09-08 against `Generate_Assessment_Prompt_v4.1.md` - the first
real run of this prompt (the file names previously listed here, `Module 1 Assessment - Lessons 1-4
(Intermediate).md` plus 4 like-named study guides, never actually existed on disk; that was stale/aspirational
documentation left over from before the Set-folder migration, corrected here):**

| File                                                | Covers                         | Status                                             |
| ---------------------------------------------------- | ------------------------------- | ----------------------------------------------------- |
| `Module_1/Set_1/Set1_Intermediate_Assessment.md`             | Lessons 1-4, all 4 Task Levels | Generated, not yet given to a real class |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level2.md`      | Task Level 2                   | Generated                                          |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level3.md`      | Task Level 3                   | Generated                                          |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level4.md`      | Task Level 4                   | Generated                                          |
| `Module_1/Set_1/Set1_Intermediate_StudyGuide_Level5.md`      | Task Level 5                   | Generated                                          |
| `Module_1/Set_1/Set1_Intermediate_Image_Credits.md`          | Every image in Lessons 1-4's packets (4) | Image register, Conventions §D/§I; packets print no credit |

Every item is tagged with its source lesson and a Tests citation of the specific `learningobjectives.csv` row
it verifies, per Section 0.3. Unlike the stale table this replaces, passages are not shared/printed once - each
Task Level section is self-contained (per Section 2.1: "a visual banner or heading per section is recommended
for quick sorting when printing/distributing selectively"), so all four lesson passages are reprinted inside
each of the 4 Task-Level sections. No Foundation Support Check section - no lesson in this Set flagged a
Foundation Support student.

**Student-facing HTML packet: `Module_1/Set_1/Set1_Intermediate_Assessment_Packet.html`, generated 2026-09-08** against
the new `Generate_Assessment_Student_Packet_Prompt_v2.0.md` (first run of this prompt for Reading - see Pending
work, now resolved). One combined document, four Task-Level sections (★ through ★★★★), each with
`page-break-before: always` so a teacher can print one Level's pages alone; all four lesson passages reprinted
in full inside every Task-Level section, matching the source `.md`'s own self-contained-per-Level shape. Every
source-lesson/Tests tag, the item-count/scope metadata, and the entire Scoring Guide (point tables and all three
rubrics) are stripped; rubric-scored items (Level 4's comparison-and-reason items, Level 5's extended-reasoning
and cross-text synthesis items) print as plain numbered questions with answer lines sized to the expected
answer, with no self-check-checklist substitute - matching how the lesson packet already treats extended-response
items, rather than Listening/Speaking's Speaking-Task-card checklist treatment.

**Print formatting (Step 6), student version:** Lesson 1's packet (`Unit 1A`/`Unit 1B: A Grandmother's Kitchen`,
`Module_1/Set_1/Lesson_1_Kitchen/Kitchen_Intermediate_L1_Packet.html`) exists as a finished HTML file; its settled CSS
is now the base stylesheet in `shared/Student_Packet_Style_Guide.md`. **2026-09-09:** a raw photo was added to
`Lesson_1_Kitchen/` and renamed per the asset convention (`shared/Program_Conventions.md` §H) as
`Lesson1_Kitchen_Img_Hook.jpg`, the Phase 1 Visual Inquiry hook photo; embedded into the packet's "Before You Read"
as a base64 `<img class="photo">` (small portrait image, so capped at 250px tall and centered rather than full
width), replacing the "[TEACHER: insert photo ...]" placeholder. The photo shows a stone wood-fired oven, not a
trullo, so the caption and the lesson `.md`'s hook line were changed to match. In the same pass all four
Intermediate Set 1 packets had their "Finish the sentence" items reduced to one sized `.blank` (no trailing
`.ans-line-sm`), their Day 2 Task A/B frames printed once inline as the answer space ("Complete the frame: It is
___."), and the redundant `.starter` box that repeated the frame after Task A removed (Style Guide §B/§F). Lesson 2's packet
(`Unit 2A`/`Unit 2B: New Corner of Yoyogi Park`,
`Module_1/Set_1/Lesson_2_YoyogiPark/YoyogiPark_Intermediate_L2_Packet.html`) is current against the print prompt, and its
three discussion prompts match Lesson 1 and Lesson 2's own source docs. **2026-09-09:** a raw photo was added to
`Lesson_2_YoyogiPark/`, renamed per §H as `Lesson2_YoyogiPark_Img_Park.jpg` (the Day 2 Task A picture), and embedded
into the packet as a base64 `<img class="photo">` (downscaled to 720px wide for embedding; source unchanged; the §B
`.photo` rule added to this packet and Lesson 4's, neither of which had it), replacing
the "[TEACHER: insert photo ...]" placeholder; the `.md` Task A line now names the asset. Lesson 3's packet
(`Unit 3A`/`Unit 3B: How to Choose Running Shoes That Feel Comfortable`,
`Module_1/Set_1/Lesson_3_RunningShoes/RunningShoes_Intermediate_L3_Packet.html`) is the first packet generated
against v1.7, so it's also the first to carry the `.masthead-meta` tag stack (`Reading` /
`Intermediate 1.1.3.0`) on its opening masthead. Its source lesson's Town Hall section supplies only
one discussion prompt (pre-2.9-fallback case), so two additional prompts exploring different angles
of the same question were authored for the packet per Section 2.9's fallback; a Focus on the
Objective worked-model box was also added between Units 3A/3B per Section 2.7, since Day 1's tasks
don't yet test the comparison-plus-reason objective against the anchor text. **2026-09-08:** a raw
image was added to `Lesson_3_RunningShoes/` and renamed to match the asset-naming convention
(`shared/Program_Conventions.md` §H): `Lesson3_RunningShoes_Img_Shoe.jpg`, for Day 2 Phase 2's Level
2 picture-frame item ("Using a picture of a running shoe, complete: 'It is ___.'"). Embedded into
`RunningShoes_Intermediate_L3_Packet.html` as a base64 `<img class="photo">` (this was done in the
same session but not logged here until now - corrected); `Lesson3_RunningShoes.md` itself never
names the image file, only the generic "a picture of a running shoe" instruction, so it needs no
change. Lesson 4's packet
(`Unit 4A`/`Unit 4B: Painting Wynwood Walls`,
`Module_1/Set_1/Lesson_4_WynwoodWalls/WynwoodWalls_Intermediate_L4_Packet.html`; **2026-09-09:** its Day 2 Task A
placeholder replaced by the embedded `Lesson4_WynwoodWalls_Img_BirdMural.jpg`, same treatment as Lesson 2 above. The
mural photographed is a pink bird while the article and word bank say orange and blue; "bright"/"big" in the bank still
fit the photo, so only the `.md`'s example answer changed, "It is orange." to "It is bright.") is also current against
v1.7, carrying the `.masthead-meta` tag stack (`Reading` / `Intermediate 1.1.4.0`) on its opening
masthead. Its source lesson already supplies 2 discussion prompts (generated against v2.7), pulled
directly per Section 2.9 with no fallback needed; a Focus on the Objective worked-model box was
added between Units 4A/4B per Section 2.7, since Day 1's comprehension questions test the
comparison-plus-reason objective but don't yet model it worked-example style before Day 2's
independent tasks. Its annotation key carries the `!` mark, since its Level 5 (extension-up) task
asks students to identify an evaluative word choice - the first Intermediate-band packet to include
it, since Section 2.10's evaluative-language trigger is met here even though it's typically an
Advanced-and-up case.

**Phase 3 protocols (Section 0.10 compliant):** Lesson 1's Fishbowl gives the outer circle an explicit active
task (a running tally of kitchen preference plus a describing word) and rotates through three discussion
prompts. Lesson 2's Jigsaw splits three discussion questions across its mixed groups. Lesson 4's Concentric
Circles rotates through two prompts at each partner changeover and needs no outer-circle task by design (both
circles are paired and active). Word counts, task-Level mapping, vocabulary, and every other section match the
student print packets.

## Module 1 progress, Advanced Band (Describing, Advanced) - Set 1 COMPLETE

Plan approved and logged to the Rotation Log as Set 1, saved as `Module_1/Module1_Advanced_Lesson_Plan.md`. This
Set needs Lessons 1-4 total, not 1-8 (the original plan's Lessons 5-8 - Aoraki Mackenzie stargazing,
Shinkansen review, Plan Vélo bike lanes, Iron Gwazi roller coaster - are out of scope and dropped, matching how
Intermediate's Lessons 5-8 were handled). Lesson 1 was generated via `Generate_Lesson_Prompt_v2.7.md` (then at
v2.5; since renamed and updated in place). **All 4 lessons of this Set are generated:**

| File                                                                 | Lesson # | Topic                                                                              | Status                        |
| ---------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------ | ------------------------------ |
| `Module_1/Set_1/Lesson_1_SagradaFamilia/Lesson1_SagradaFamilia.md`           | 1        | La Sagrada Família, Antoni Gaudí's still-unfinished basilica in Barcelona, Spain    | Generated, self-check passed  |
| `Module_1/Set_1/Lesson_2_ForgeAtDawn/Lesson2_ForgeAtDawn.md`                 | 2        | A day inside a traditional Japanese swordsmith's forge, following the tamahagane steel-forging process | Generated against v2.7, self-check passed (18 items) |
| `Module_1/Set_1/Lesson_3_VinylComeback/Lesson3_VinylComeback.md`             | 3        | The real-world resurgence of independent vinyl record shops                       | Generated against v2.8, self-check passed (18 items) |
| `Module_1/Set_1/Lesson_4_PortlandHeadLight/Lesson4_PortlandHeadLight.md`     | 4        | A keeper's account of Portland Head Light, Maine                                  | Generated against v2.8, self-check passed (18 items) |

Anchor text calibrated to Level 5 (460 words, 6 paragraphs, B2), with task Levels 4 (extension-down), 5 and 6
(native), and 7 (extension-up, requiring the second comparison text per the plan's note). Lesson 1 used Fishbowl
as its Phase 3 protocol - a fully valid choice under v2.7; **patched 2026-09-08** for Section 0.10 compliance
(three rotating prompts, and a general outer-circle tally/vocabulary-tracking task for every outer-circle student,
layered underneath the existing Level 4 and Foundation Support roles - see `Changelog.md`). Lesson 2 (450 words, 6 paragraphs) was
generated directly against v2.7, so its Jigsaw Phase 3 already carries the current Section 0.10 scaffolding
(three discussion prompts split across the mixed groups). Lesson 3 (434 words, 6 paragraphs) was generated
against the current `Generate_Lesson_Prompt_v2.9.md`, carrying the required `**Version:**` header field
(new as of v2.8/§G; Lessons 1-2 predate this and stay unversioned by design), now at `1.1.3.1` after the
2026-09-10 §D11 pass; its Town Hall Phase 3 rotates through three discussion prompts across small groups
formed where students sit, and needs no listener task under Section 0.10.
Its two board-dependent moments sit in Day 1 Phase 1 (Mystery Quote guess-and-check) and Day 2 Phase 3 (Town
Hall report-back), rotating the required slot away from Lesson 2's Phase 1 + Phase 2 pairing. Lesson 4 (454
words of dialogue, 6 turn-blocks) was generated against `Generate_Lesson_Prompt_v2.9.md`, carrying `**Version:**
1.1.4.1` (bumped from `1.1.4.0` in the 2026-09-10 §D11 pass); it is formatted as a Reader's Theater interview script (Interviewer/Keeper speaker roles, stage
directions, rehearsal cues) rather than continuous prose, the first lesson in this Set to use a script-style
genre. Its Concentric Circles Phase 3 rotates through three discussion prompts at each partner changeover and
needs no outer-circle task under Section 0.10 (both circles are paired and active by design). Its two
board-dependent moments sit in Day 1 Phase 1 (Four-Corner Debate tally-and-check) and Day 2 Phase 2 (a live
Then/Now T-chart built from group report-backs), rotating the required slot away from Lesson 3's Phase 1 + Phase
3 pairing.

No homework, TOEFL extension, or assessment work has started yet for the Advanced band.

**Print formatting (Step 6), student version:** Lesson 1's student packet (`Unit 1A`/`Unit 1B: The Basilica That
Refuses to Be Finished`, `Module_1/Set_1/Lesson_1_SagradaFamilia/SagradaFamilia_Advanced_L1_Packet.html`; its hook
photo is credited in `Module_1/Set_1/Set1_Advanced_Image_Credits.md`, the Advanced Set's image register) exists as an HTML
file; its CSS is the base stylesheet in `shared/Student_Packet_Style_Guide.md`. Lesson 2's student packet (`Unit 2A`/`Unit 2B: The
Forge at Dawn`, `Module_1/Set_1/Lesson_2_ForgeAtDawn/ForgeAtDawn_Advanced_L2_Packet.html`) is current against the
print prompt. Both now carry the `.masthead-meta` stack on both mastheads as of 2026-09-09
(`Reading` / `Advanced` - Band only, no version code, since Lessons 1-2 stay unversioned by design; see
`Changelog.md`), backfilled from Lessons 3-4; the Module-name tag (`Describing`) was added between them 2026-09-09, as on every packet. Both use the 5-mark annotation key (Advanced band and up); Lesson 1 has no byline (short-story
genre), and Lesson 2's Task D (Level 7) embeds the lesson's second comparison text - a museum-placard passage
promoting swordsmithing demonstrations - inline on the page rather than as a separate handout, per the module
plan's note for this lesson's extension-up task. Lesson 2's discussion prompts (three, split across groups) came
straight from the source lesson. Lesson 2 also carries an L4 differentiated-participation tip line under the
sentence stems, mirroring the Level 4 tracking task from the lesson's own Phase 3 section; Lesson 1's packet
does not include this for its own Level 4 stem. Lesson 3's student packet (`Unit 3A`/`Unit 3B: The Vinyl Comeback
Is Real`, `Module_1/Set_1/Lesson_3_VinylComeback/VinylComeback_Advanced_L3_Packet.html`) is the first Advanced packet
generated against v1.7, so it's the first to carry the masthead `.masthead-meta` two-tag stack ("Reading",
"Advanced 1.1.3.0") on its opening masthead. Its idioms were also found reusing `.vocab-list`/`.vrow` ("Words to Know"'s own classes) instead of
either idiom class - corrected to the standard `.spotlight-box`/`.idiom-item` "Phrase Spotlight" treatment as
part of the v1.12 idiom sweep (see `Changelog.md`). It embeds Task D's second comparison text (an industry-report
pitch for vinyl-pressing investment) inline, with an L4 differentiated-participation tip line under the sentence
stems matching its own Phase 3 tracking task. Lesson 4's student packet (`Unit 4A`/`Unit 4B: Keeping the Light`,
`Module_1/Set_1/Lesson_4_PortlandHeadLight/PortlandHeadLight_Advanced_L4_Packet.html`) carries the `.masthead-meta` tag
stack ("Reading", "Advanced 1.1.4.0") and the 5-mark annotation key. Its Reader's Theater script format is
translated into plain speaker labels (`.speaker` spans, a new class added for this packet only, since the base
stylesheet has no prior speaker-label element) and italic stage directions (reusing plain `<em>`-equivalent
styling via a new `.stage-direction` class), per Section 1's "state the plain action, never the pedagogical name"
rule for a strategy not explicitly listed in that section's table. Its three discussion prompts (in a
simultaneous small-group format per Section 2.9, since a print page cannot orchestrate a live Concentric Circles
rotation) came straight from the source lesson, and it carries an L4 differentiated-participation tip line under
the sentence stems, matching its own Phase 3 tracking task. Task D embeds the lesson's second comparison text (a
visitor placard promoting Portland Head Light as a tourist destination) inline, matching Lessons 2-3's pattern.
**2026-09-08:** a raw image was added to `Lesson_1_SagradaFamilia/` and renamed to match the
asset-naming convention (`shared/Program_Conventions.md` §H): `Lesson1_SagradaFamilia_Img_Hook.jpg`,
for the Phase 1 Visual Inquiry hook photo. Embedded into `SagradaFamilia_Advanced_L1_Packet.html`'s
"Before You Read" section as a base64 `<img class="photo">`, replacing the text placeholder that was
there (mirroring how `Lesson3_RunningShoes_Img_Shoe.jpg` was embedded); the existing image caption
already matched the photo, so it was left unchanged. **Recompressed 2026-09-08** (same day, later
pass): the source file (294 KB at 750x750) was embedded as-is with no size reduction; re-embedded at
~98 KB, matching the recompress-before-embed practice found in Listening/Speaking's
`Backpack_Intermediate_L3_Packet.html`. The source `.jpg` on disk is unchanged; only the packet's
embedded copy was replaced - see `Changelog.md`.

All 4 Advanced Set 1 lessons' Closing Transfer Check activities (both the `.md` and packet wrapup) were
rewritten 2026-09-08 to use distinct concrete scenarios instead of the shared "something/one thing in
the room" framing - Lesson 1 a piece of clothing, Lesson 2 a piece of furniture, Lesson 3 a sound you
can hear, Lesson 4 something visible out the window - per the v2.10 Closing Transfer Check Variety rule;
see `Changelog.md`.

## Module 1 progress, Beginner Band (Describing, Beginner) - Set 1 COMPLETE

Plan generated against `Generate_Module_Lesson_Plan_Prompt_v2.2.md`, approved 2026-09-10, and saved as
`Module_1/Module1_Beginner_Lesson_Plan.md`. This is the first Set ever planned for this Band, so
`Rotation_Log_Beginner.md` was created with it (lazily, per `shared/Program_Conventions.md` §F) and the
cross-Set and cross-Module adjacency checks were skipped. **All four lessons were generated 2026-09-10**, two
at a time (1-2, then 3-4) and checked against each other for the §D6 adjacency rules, so each of the four
genres, strategies, hooks, and protocols is used exactly once across the Set.

| Lesson # | Topic | Genre | Strategy | Hook | Protocol | Version |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | The things in a school bag, labeled | Label set with embedded images | Teacher Read-Aloud with Interactive Stops | Visual Inquiry | Rotating Partners | 1.1.1.0 |
| 2 | A postcard about a sunny day at the beach and what the writer wore | Short personal note / postcard | Echo Reading | K-W-L Chart | Small-group discussion | 1.1.2.0 |
| 3 | Two friends at a fruit stand deciding which fruit to buy | Simple 2-4 line dialogue | Reader's Theater | Take a Side | Panel Round | 1.1.3.0 |
| 4 | A lost-and-found notice describing a lost cat | Short notice / simple sign | Partner / Shared Reading | Mystery Quote | Jigsaw Expert Panels | 1.1.4.0 |

**Generated so far:**

| File | Lesson # | Topic | Status |
| --- | --- | --- | --- |
| `Module_1/Set_1/Lesson_1_SchoolBag/Lesson1_SchoolBag.md` | 1 | Bag Check: a label set for a school bag, a book, and a pen | Generated, self-check passed (20 items), version 1.1.1.0 |
| `Module_1/Set_1/Lesson_1_SchoolBag/SchoolBag_Beginner_L1_Packet.html` | 1 | Student packet, three embedded photos | Generated |
| `Module_1/Set_1/Lesson_2_BeachPostcard/Lesson2_BeachPostcard.md` | 2 | A Postcard from the Sea: Ana writes about a hot day | Generated, self-check passed (20 items), version 1.1.2.0 |
| `Module_1/Set_1/Lesson_2_BeachPostcard/BeachPostcard_Beginner_L2_Packet.html` | 2 | Student packet, three embedded photos | Generated |
| `Module_1/Set_1/Lesson_3_FruitStand/Lesson3_FruitStand.md` | 3 | The Fruit Stand: Nina, Raj, and a seller compare an apple, a banana, and a pineapple | Generated, self-check passed (21 items), version 1.1.3.0 |
| `Module_1/Set_1/Lesson_3_FruitStand/FruitStand_Beginner_L3_Packet.html` | 3 | Student packet, three embedded photos | Generated |
| `Module_1/Set_1/Lesson_4_LostCat/Lesson4_LostCat.md` | 4 | Lost Cat: a lost-and-found notice for Pip, a black-and-white cat | Generated, self-check passed (21 items), version 1.1.4.0 |
| `Module_1/Set_1/Lesson_4_LostCat/LostCat_Beginner_L4_Packet.html` | 4 | Student packet, three embedded photos | Generated |
| `Module_1/Set_1/Set1_Beginner_Image_Credits.md` | - | Credits for all twelve Wikimedia photos | Created |

All four lessons and packets are done. Steps 3 to 5 are not started for this Band: no homework, no Set
assessment, no study guides. See Pending work.

Two things about this Band that differ from the two already generated:

- **Three task Levels, not four.** Beginner's are 1, 2, 3 (`shared/Program_Conventions.md` §B): native 1 and 2
  plus one extension up, and no extension down, because Level 1 is the scale's floor. Every lesson carries three
  differentiated sections, the packets print ★ / ★★ / ★★★ with no ★★★★, and the Set's eventual assessment gets
  three study guides rather than four.
- **Every lesson needs real embedded images.** All three Module 1 Reading objectives end in matching a decoded
  word or frame to an image, and Quality Standards §D8 forbids anything the teacher prepares, so each lesson's
  picture items must be built on Wikimedia Commons photos fetched at generation time (Conventions §I), embedded
  as base64 data-URIs, named at the point of use in the `.md`, and rowed into the Set's image-credits register, which Step 2 creates
  in `Module_1/Set_1/` under the `Set<N>_<Band>_Image_Credits.md` name Conventions §H gives it. The plan's last column names what each
  lesson needs. No packet is generated before its images exist.

The plan also fixes, per lesson, the §0.11 fixed-output shape for each slot and the Closing Transfer Check
object (pencil case / water bottle / jacket / phone, one per lesson, none repeated); Step 2 should follow that
table rather than re-deriving it.


## Module 1 progress, Proficient Band (Describing, Proficient) - Set 1 COMPLETE

Plan generated against `Generate_Module_Lesson_Plan_Prompt_v2.2.md`, approved 2026-09-10, and saved as
`Module_1/Module1_Proficient_Lesson_Plan.md`. First Set ever planned for this Band, so
`Rotation_Log_Proficient.md` was created with it (lazily, per `shared/Program_Conventions.md` §F) and the
cross-Set and cross-Module adjacency checks were skipped. **All 4 lessons of this Set are generated**, on
2026-09-10 against `Generate_Lesson_Prompt_v3.5.md`, in two passes (Lessons 1-2, then 3-4).

| File | Lesson # | Topic | Status |
| --- | --- | --- | --- |
| `Module_1/Set_1/Lesson_1_Hashima/Lesson1_Hashima.md` | 1 | The prescribed visitor route on Hashima Island (Gunkanjima), Nagasaki, described by a tour operator and by a reporter who took the same tour | Generated, self-check passed |
| `Module_1/Set_1/Lesson_2_CrystalPalace/Lesson2_CrystalPalace.md` | 2 | The Crystal Palace during the Great Exhibition of 1851, in an official catalogue account and a visitor's diary | Generated, self-check passed |
| `Module_1/Set_1/Lesson_3_EamesChair/Lesson3_EamesChair.md` | 3 | The Eames Lounge Chair (Herman Miller, 1956), described by a design historian and by a furniture restorer in the same podcast episode | Generated, self-check passed |
| `Module_1/Set_1/Lesson_4_Platskart/Lesson4_Platskart.md` | 4 | A third-class platskart carriage on the Trans-Siberian Railway, described by two narrators making the same journey | Generated, self-check passed |

Three things about this Band that differ from the others:

- **Four task Levels, but two of them borrowed downward.** Proficient's are 5, 6, 7, 8
  (`shared/Program_Conventions.md` §B): Levels 5 and 6 are both one band below, and 7 and 8 are native, because
  Level 8 is the scale's ceiling and there is nothing above to extend into. So the packets' stars land
  differently here than at Intermediate or Advanced: ★ and ★★ are both "one band below," and the native Levels
  are ★★★ and ★★★★.
- **The anchor is a paired text set, not a single passage.** Level 7 is this Band's anchor Level and its Reading
  objective requires two extended descriptions of the same subject, so each lesson carries two texts of roughly
  330-360 words (600-700 combined, Section 0.2's Level 7 row), lettered as one continuous sequence [A]-[D] and
  [E]-[H]. Levels 5 and 6 work the first text alone; comparing across texts is Level 7's own ceiling and is not
  pulled down into theirs. Level 8's extra demand (mapping register shifts, finding where literal description
  and real attitude diverge, and naming how a specified other audience would misread it) sits on the same pair
  rather than on a harder text, which is what keeps the band-distance invariant intact for the Level 5 student
  reading the same page.
- **No retired formation anywhere in the Set.** Hooks and protocols were chosen in their room-neutral forms
  (Quality Standards §D11) at planning time, so unlike Intermediate's and Advanced's Set 1 rows this Band's log
  needs no later Fishbowl/Concentric Circles/Four-Corner/K-W-L Walk rename.

**Lesson 1** (`Forty-Five Minutes on Battleship Island`, version 1.1.1.0) pairs an invented cruise operator's
long-read with an invented reporter's account of the same sailing, both covering the seawall, the apartment
blocks, and the parts of the island a visitor cannot reach, so the Level 7 comparison has like-for-like evidence
on the page (Quality Standards §C9). Anchor 692 words (363 + 329), 8 paragraphs, average sentence length 22.7
and 23.5. Its Visual Inquiry hook embeds a real Commons photo fetched in the same pass,
`Lesson_1_Hashima/Lesson1_Hashima_Img_Hook.jpg` (Conventions §I), credited in
`Module_1/Set_1/Set1_Proficient_Image_Credits.md` and nowhere else. Board moments sit in Day 1 Phase 1 and Day 2
Phase 2; Closing Transfer Check is today's shoes, described twice.

**Lesson 2** (`The Building of Glass`, version 1.1.2.0) pairs an invented passage in the register of the
Exhibition's official catalogue with an invented visitor's diary for 12 July 1851, both covering the light, the
crowd in the transept, and the exhibits. Anchor 686 words (352 + 334), 8 paragraphs, average sentence length
22.0 and 20.9. Real 1851 diaries of this visit survive (Queen Victoria's, Henry Cole's), so the fictional-subject
note states explicitly that neither text is an extract from or attributed to any of them; the diarist is
invented. No image is needed, since the hook is a printed quotation. Board moments move to Day 1 Phase 1 and Day
2 Phase 3, rotating the slot away from Lesson 1's pairing (Section 0.7).

**Lesson 3** (`Three Curves and Nothing Else`, version 1.1.3.0) pairs a design historian's turns with a
furniture restorer's turns from the same invented podcast episode, both covering the moulded shells, the leather
cushions, and the chair's proportions. Anchor 695 words (348 + 347), 8 turn-blocks, average sentence length 21.8
and 21.7. The chair's technical facts are real and were checked by live search (models 670/671, 1956, moulded
plywood with a face veneer, Brazilian rosewood withdrawn in the early 1990s, down cushions until foam from 1960,
rubber shock mounts); Charles and Ray Eames are named as the real designers, but the podcast, its host, and both
guests are invented and nothing is attributed to either Eames or to Herman Miller. Its Reader's Theater
performance builds a board tone map on Day 1 that Day 2 adds a second row to, so the board persists across the
two days. Closing Transfer Check is the last room you slept in.

**Lesson 4** (`Fifty-Four Berths`, version 1.1.4.0) pairs two invented short-story narrators on the same class
of carriage, both covering the bunks, the aisle, and the night hours. Anchor 683 words (350 + 333) excluding the
THINK-ALOUD markers, 8 paragraphs, average sentence length 21.9 and 20.8. Platskart's arrangement was checked by
live search (54 berths, bays of four plus single bunks along the windows, the carriage boiler, the attendant).
Its K-W-L chart is the §D11 printed-and-boarded form, with the L column deliberately left for Day 2 Phase 1.
Closing Transfer Check is the weather outside right now.

**Sentence-length calibration, worth knowing for the next Proficient Set:** Lessons 3 and 4 both failed Section
0.3 item 2 on the first draft and were rewritten before finalizing. A podcast transcript breaks naturally into
short conversational sentences (13.9 and 14.3 words average, well under Level 7's 20-25), and literary narration
runs the other way into long coordinated periods (34.9). Section 0.6 is explicit that genre changes form and
voice but never the ceiling, so the guests' answers were given the subordination C1 expects and the narrator's
periods were rebroken, in both cases without losing a phrase any item quotes. Count sentence length as well as
word count when a genre has a strong native rhythm.

No homework, TOEFL extension, assessment, or student packet exists for this Band yet. Step 6 (student packets)
for all four lessons is the natural next pass.

## Generation workflow (current)

This is the process for producing one Set's worth of lessons, in order (see `shared/Program_Conventions.md` §C
for what a Set is); today that's **4 lessons**.

**Step 1 - Plan the Set.** Run `Generate_Module_Lesson_Plan_Prompt_v2.2.md` for the
target Module, Band, and Set number. It reads the Rotation Log first (for cross-Set genre/strategy/vocabulary
checks against the most recent Set already planned for this Module/Band, or the previous module's last Set if
this is a new Module/Band's first Set), produces the 4-lesson plan table, and runs its self-check. Review the
plan and approve it before moving on - do not generate lesson content against an unapproved plan. Once approved,
append its Rotation Log entry to `Rotation_Log.md` per that prompt's Section 0.

**Step 2 - Generate lessons two at a time.** Run `Generate_Lesson_Prompt_v3.5.md` (pasted with
`shared/Program_Conventions.md` and `shared/Generation_Quality_Standards.md`) against the approved plan,
fetching and citing any image a lesson needs in this same step (`shared/Program_Conventions.md` §I),
generating two lessons per pass rather than one at a time or all four at once. Two at a time keeps each pass small
enough to actually check (word count, Section 0.2 band ceiling, the shared Quality Standards §F self-check, and
the Reading items in Section 0.3) before moving on, while still letting adjacent-lesson checks - no repeated genre
or reading strategy between consecutive lessons, and no repeated Closing Transfer Check object/scenario (Quality
Standards §D3) - happen naturally within a pass, since both lessons in a pair are visible at once.

Order within Step 2: Lessons 1-2, then 3-4.

**Step 3 - Generate homework per completed lesson.** Run `Generate_Homework_Prompt_v2.3.md`
against each completed lesson from Step 2, supplying both Day 1 and Day 2 in full. One homework assignment per
lesson, general track only; TOEFL-track students use Step 4 instead for the same cycle, never both. Default timing
is after Day 1, due at the start of Day 2 - if a class is a lesson or more ahead, homework can instead be generated
after Day 2 per that prompt's Section 0.2, but state which timing was used.

**Step 4 - TOEFL Track Extension.** Run `Generate_TOEFL_Extension_Prompt_v1.1.md` per completed
Advanced/Proficient-band lesson, as an optional add-on for TOEFL-interested students, replacing Step 3's
homework for that student on that cycle rather than adding to it.

**Step 5 - Assessment.** Run `Generate_Assessment_Prompt_v5.2.md` once a Set's lessons are complete (per its own
scope note, from a completed Set's worth of lessons, not a single one) - typically at the end of a Set (all 4
lessons), after Steps 2-4 have been run across the relevant lessons, not per lesson. Confirm scope (cumulative
vs per-lesson), the Set number, and which task Level each student/group actually completed before generating;
it produces one test section and one study guide per task Level in the band, plus a Foundation Support check
where applicable. A Set is 4 lessons, so the `Set1_Intermediate_Assessment.md` generated for Intermediate
Module 1 Set 1 (2026-09-08) is the complete end-of-Set assessment - there is no separate 8-lesson pass to run.

**Step 5a - Print formatting for the assessment.** Run `Generate_Assessment_Student_Packet_Prompt_v2.0.md`
immediately after Step 5's Assessment `.md` is complete, in the same session, to produce a single, print-ready,
black-and-white student handout as one self-contained HTML file - four Task-Level sections, each printable on
its own, with every source-lesson/Tests tag and the entire Scoring Guide stripped. Independent of Step 6 below
(a lesson's own print formatting), since an assessment has no taught Unit A/B to translate.

**Step 6 - Print formatting for students.** Run `Generate_Student_Packet_Prompt_v2.7.md` (pasted with
`shared/Student_Packet_Style_Guide.md`) against a completed 2-day lesson from Step 2 (both days, in full) to
produce a single, print-ready, black-and-white student handout as one self-contained HTML file, pulling its 2-3
discussion prompts directly from the source lesson. This step is
independent of Steps 3-5 and can run any time after Step 2 completes for that lesson. Deliver as an HTML
preview first; format feedback typically comes as scoped edits to that file rather than a full regeneration. No
teacher-facing formatted version exists yet - out of scope for this prompt.

## Pending work

- **Passage Reading has no §D12 beat (Quality Standards v1.17, 2026-09-10).** The new §D12 requires that any
  support carrying the answer arrive only after students commit a response, and that the lesson end with one
  unsupported re-encounter. Listening/Speaking's mechanics were built the same day (a second audio-only listen
  plus a bounded transcript window); Reading's were not, so the rule currently has no expression here.
  Reading's case is genuinely different, because the anchor text is on the page throughout, so the support that
  needs withholding is not the wording but the **location of the evidence**. The natural site is the lettered
  `[STOP & CHECK]` checkpoints: commit the answer first, then go back and cite the line it rests on, then
  answer one more item without the citation aid. Building it needs a Day 1 budget decision (currently Phase 1
  Pre-Reading 15 / Phase 2 Text Engagement 35 / Phase 3 Comprehension and Vocab Check 25, with no slack) and a
  `Generate_Lesson_Prompt_v3.5.md` bump plus a matching packet block. Not started; logged so §D12 does not
  quietly become a Listening/Speaking-only rule.

- **Resolved 2026-09-10 (packet prompt v2.7):** §2.9's annotation key is now band-conditioned. Two of the
  four default marks sit above the Level 1 ceiling ("circle a connector word: but, because, when" - a Beginner
  anchor carries at most "and" - and "bracket the sentence with the paragraph's main idea", which §0.2 gives
  no inference to support), so a Beginner packet prints three marks, substituting "circle a word that tells
  you about a thing". §2.9 states this the same way it already conditions the `!` mark on an evaluative
  objective, and forbids padding the key back to four for cross-band uniformity. All four Beginner packets
  already match. No Intermediate or Advanced packet changes: those bands support both contested marks.

- **Beginner Module 1 Set 1 has no homework, assessment, or study guides (2026-09-10).** All four lessons and
  their packets are generated, so the Set is ready for Steps 3 to 5. Outstanding for this Band: one homework
  per completed lesson via `Generate_Homework_Prompt_v2.3.md` (four files, none written); the Set assessment
  via `Generate_Assessment_Prompt_v5.2.md`, which at this Band produces **three** study guides, not four,
  since Beginner has three task Levels; and its student packet via
  `Generate_Assessment_Student_Packet_Prompt_v2.0.md`. The TOEFL extension does not apply below Advanced.
- **Day 1 Phase 3's native-Level set is named for the wrong Module (found 2026-09-10, not yet applied).**
  `Generate_Lesson_Prompt_v3.5.md`'s Day 1 Phase 3 bullet fixes the item-set shapes by name: "a Fact Finder set
  for the lowest task Level, a **Cause & Effect set** for the band's native Level(s)." Cause and effect is
  Module 3's verb, not Module 1's, so following that line literally in a Describing lesson produces exactly the
  drift Quality Standards §A4 forbids ("a Describing lesson whose questions are mostly cause-and-effect has
  drifted into Explaining"). It has already materialized once: Advanced
  `Module_1/Set_1/Lesson_3_VinylComeback/Lesson3_VinylComeback.md` carries a "Cause & Effect set" whose items
  ask why the writer says things, in a Describing lesson. Proficient Lessons 1-2 deliberately deviate, using a
  "Stated or signalled" set and a "Framing set" instead, and say so in their self-checks. **Fix:** the shape of
  the native-Level set follows the Module's verb (cause-and-effect for Explaining, comparison and framing for
  Describing, criteria and verdict for Evaluating, and so on), with Cause & Effect named as the Explaining case
  rather than as the default. That is a prompt bump (v3.6) plus this `Index.md`'s file-index and Step 2
  references, a `Changelog.md` line, and a sweep of the four generated Describing lessons that used the old
  label. Not done in this pass: `Generate_Lesson_Prompt_v3.5.md` was being used by a concurrent session
  generating Beginner Set 1 at the time, and renaming it mid-run would have broken that run. The rule itself
  needs no shared-file change, since §A4 already states it; only Reading's own prompt contradicts it.
  `Generate_Student_Packet_Prompt_v2.7.md` (Section 2.3's merge rule) and `shared/Student_Packet_Style_Guide.md`
  §E's strip-list also name "Cause & Effect set" and should be reworded in the same pass.

- **Resolved 2026-09-10 (Quality Standards §D11, room-neutral participation):** all seven affected lessons were
  rewritten, not backlogged. Advanced `Module_1/Set_1/Lesson_1_SagradaFamilia/` (a Fishbowl that arranged 5-6
  chairs -> a Panel Round from seats, listener tally task kept) and `Lesson_4_PortlandHeadLight/`
  (Four-Corner Debate -> Take a Side, Concentric Circles -> Rotating Partners, `1.1.4.0` -> `1.1.4.1`; its
  packet had told students "Your teacher will post a statement on the wall... Move to the corner of the room,"
  now a printed four-option choice they circle); Intermediate `Lesson_1_Kitchen/` (Fishbowl -> Panel Round)
  and `Lesson_4_WynwoodWalls/` (Four-Corner Debate -> Take a Side with the four options now printed in the
  packet, Concentric Circles -> Rotating Partners, packet Discuss It reworded to find-a-new-partner).
  `Lesson_3_VinylComeback/` set the room up "as a town hall with several discussion tables"; the groups now form
  where students sit (`1.1.3.0` -> `1.1.3.1`).
  `Lesson_2_ForgeAtDawn/` and `Lesson_2_YoyogiPark/` were renames only (K-W-L Walk -> K-W-L Chart): both
  already built the chart on the board with nobody leaving their seat. Both rotation logs and both Module
  lesson plans carry the new names.
- **Resolved 2026-09-09 (Conventions §I):** all five Reading images that had been supplied by hand were replaced with
  cited Wikimedia Commons files, each `.md` carrying an `Image:` citation line and each Set's
  `Set1_<Band>_Image_Credits.md` the credit (packet captions carry none since Style Guide v2.17, same day):
  Kitchen (bread in a wood-fired oven in Altamura, Puglia - a better match to the article than the old outdoor
  oven), YoyogiPark (a path in Yoyogi Park), WynwoodWalls (an orange-and-blue parrot mural, so the picture now
  matches the article; the `.md` example answer went back to "It is orange.", since superseded - see the
  2026-09-10 colour sweep in `Changelog.md`), RunningShoes, SagradaFamilia.
- **Resolved 2026-09-09 (Conventions v1.13 / Style Guide v2.17):** photo credits moved out of the five packets into
  Set-level registers, `Module_1/Set_1/Set1_Intermediate_Image_Credits.md` (4 images) and
  `lessons/advanced/Module_1/Set_1/Set1_Advanced_Image_Credits.md` (1); the packets keep their descriptive captions
  only - see `shared/Changelog.md`.
- **Stale masthead CSS in one packet (Style Guide §B, 2026-09-09):**
  `lessons/advanced/Module_1/Set_1/Lesson_1_SagradaFamilia/SagradaFamilia_Advanced_L1_Packet.html` still defines
  `.masthead .kicker` and `.masthead .sub`, classes §B has no equivalent for and §I item 5 bans from the markup
  (nothing in the file uses them). Its `.masthead*` rules are also split across two places in the `<style>`
  (around lines 49 and 180) and collapsed to one line each, unlike §B's one-declaration-per-line §C form. Delete
  the two dead rules and regroup the block when this packet is next regenerated.

- **Objective as a student can-do (Style Guide v2.10, 2026-09-08):** every existing packet's objective opens with
  a bare verb ("Objective: describe...", "Objective: listen for..."), the form the Style Guide retired in favor
  of "I can" plus the skill in the student's voice. Rewrite each as "I can ..." when its packet is next
  regenerated; this lesson type's packet prompt was not bumped for it and should state the §E form when next
  revised.
- **Self-contained rule backlog (Quality Standards §D8, 2026-09-08):** these packets still carry a "[TEACHER:
  insert photo ...]" note or a teacher-prepared prop, to be replaced by an embedded image or a real-object
  redesign when each is next touched (all three Intermediate photo notes were resolved 2026-09-09): the four Advanced Set 1 lesson `.md` files' Foundation
  Support blocks ("provide a picture card set").

- **Resolved 2026-09-08**: Advanced Module 1 Set 1's Closing Transfer Check repetition (all 4 lessons sharing
  "something/one thing in the room") and Lesson 1's Fishbowl (missing Section 0.10's multi-prompt/outer-circle-task
  requirements) were both fixed - see `Changelog.md`'s retroactive entry. `YoyogiPark_Intermediate_L2_Packet.html`
  (Intermediate, one band down) still shows the same Closing Transfer Check repetition pattern and remains
  unfixed - not in scope of that pass; take the opportunity to vary its object per Section 0.8/the Closing
  Transfer Check Variety rule if that lesson is revised for any other reason.
- **Module 1 Advanced Homework/TOEFL/Assessment** - not started; now that all 4 lessons of Set 1 are generated,
  this is the next work per Steps 3-5.
- **Print formatting for Advanced Set 1** - now complete for all 4 lessons (`SagradaFamilia_Advanced_L1_Packet.html`,
  `ForgeAtDawn_Advanced_L2_Packet.html`, `VinylComeback_Advanced_L3_Packet.html`,
  `PortlandHeadLight_Advanced_L4_Packet.html`); Set 1 Intermediate's print
  formatting is complete for all 4 lessons (`RunningShoes_Intermediate_L3_Packet.html`,
  `WynwoodWalls_Intermediate_L4_Packet.html`).
- **Teacher-facing formatted/print version** - not started; a possible future companion to the Step 6 prompt,
  noted but out of scope until requested.
- **Resolved 2026-09-08**: Reading now has an Assessment Student Packet prompt
  (`Generate_Assessment_Student_Packet_Prompt_v2.0.md`), matching Listening/Speaking's and Writing's own. First
  run produced `Module_1/Set_1/Set1_Intermediate_Assessment_Packet.html` from the existing
  `Set1_Intermediate_Assessment.md` the same session - see the Module 1 Intermediate section above.
- **Novel Reading lesson type** - not started. Will need its own lesson-generation prompt, its own Module
  Lesson-Plan-equivalent (or a shared one adapted to variable day-counts), and its own `../novel-reading/`
  folder (index, prompts, rotation log) rather than being folded into the tables above, since day-count is
  fixed for Passage Reading and variable for Novel Reading.
- **Resolved (was stale here until 2026-09-08):** the note above previously claimed
  `Lesson3_RunningShoes_Img_Shoe.jpg` was not yet wired into the packet HTML - it actually already was
  (see the print-formatting note above); this file just hadn't been updated to say so.
