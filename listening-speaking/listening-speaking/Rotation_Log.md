# Listening/Speaking Rotation Log

Running record of every approved Listening/Speaking Set's content-format, listening-strategy, speaking-skill,
Phase 1 hook, Phase 3 protocol, vocabulary theme, and topic-direction choices - one row per lesson, one
subsection per Set, grouped under one section per Module/Band, in the order Sets were planned. Maintained by
the Listening Speaking Module Lesson-Plan Generation Prompt (v1): read in full before planning a new Set,
appended to (never overwritten) once a Set's plan is reviewed and approved. See that prompt's Section 0 for the
cross-Set and cross-Module adjacency/recency rules this log supports, and its Sets note for how a Module/Band
can hold more than one Set over time (a fresh rotation of topics for a semester where the module is retaught).

## Module 1: Describing, Intermediate Band

### Set 1 (planned 2026-09-01) - Generated

| Lesson # | Content Format                 | Listening Strategy                     | Speaking Skill           | Phase 1 Hook       | Phase 3 Protocol   | Vocabulary Theme               | Topic Direction                                         |
| -------- | ------------------------------ | -------------------------------------- | ------------------------ | ------------------ | ------------------ | ------------------------------ | ------------------------------------------------------- |
| 1        | Home/studio tour               | Listen for Main Ideas/Gist             | Making Comparisons       | Visual Inquiry     | Fishbowl           | Bread & baking sensations      | A real neighborhood bakery and its bread-making process |
| 2        | Walking-tour narration         | Recognize Examples                     | Giving Examples phrases  | Four-Corner Debate | Jigsaw             | Market sounds & smells         | A real open-air public market                           |
| 3        | Product demo/review            | Listen for Sequence Markers            | Sequencing Language      | Mystery Quote      | Town Hall          | Gear features & materials      | A real piece of outdoor/everyday gear                   |
| 4        | Profile/oral-history interview | Predict from Context Before Confirming | Asking for Clarification | K-W-L Walk         | Concentric Circles | Personality & character traits | A family elder or mentor                                |

### Set 2 (planned 2026-09-01) - Planned only, not yet generated

| Lesson # | Content Format                   | Listening Strategy                         | Speaking Skill                    | Phase 1 Hook       | Phase 3 Protocol   | Vocabulary Theme             | Topic Direction                                |
| -------- | -------------------------------- | ------------------------------------------ | --------------------------------- | ------------------ | ------------------ | ---------------------------- | ---------------------------------------------- |
| 5        | Nature description               | Listen for Stated vs. Implied Opinion      | Hedging an Opinion                | Visual Inquiry     | Fishbowl           | Animal features & habitat    | A real animal and its habitat                  |
| 6        | Craft-studio tour                | Listen for Signposting/Discourse Markers   | Summarizing What Someone Said     | Four-Corner Debate | Jigsaw             | Tools & materials of a craft | A potter's, weaver's, or woodworker's workshop |
| 7        | Museum/exhibit-guide description | Listen for Cause-and-Effect Language       | Turn-Taking/Interrupting Politely | Mystery Quote      | Town Hall          | Art & artifact description   | A real historical artifact or exhibit          |
| 8        | Travel/landmark description      | Listen for Contrastive/Concession Language | Agree/Disagree phrases            | K-W-L Walk         | Concentric Circles | Landscape & scenery          | A real natural landmark                        |

**Set 1 lessons:**

**Lesson 1 generated (2026-09-01):** real source found and confirmed - "New Bakery, Old Baking Method," VOA
Learning English (Jonathan Bethony, Seylou Bakery, Washington D.C.). See
`lessons/intermediate/Set_1/Lesson_1_NewBakery/Lesson1_NewBakery.md`. Runtime (4:31) ran slightly past the Level 3 target
(2-4 min) - noted in that lesson's self-check as an accepted minor deviation, not a rewrite trigger. Real video
timestamps could not be verified directly; the source's own five headed sections were used as segment labels
instead - see the Lesson Generation Prompt's addendum note.

**Lesson 2 generated (2026-09-02):** real source found and confirmed - "Porto Food Tour," Rick Steves Classroom
Europe (guide Andre, Taste Porto Food Tours; narrated by Rick Steves). See
`lessons/intermediate/Set_1/Lesson_2_PortoFoodTour/Lesson2_PortoFoodTour.md`. Runtime not stated on the page, estimated rather
than confirmed - flagged as an open item. Topic direction broadened from "open-air public market" to a covered
historic market hall plus a short walking food tour past three nearby shops, since that is what the verified
real source actually shows - flagged, not silently substituted.

**Lesson 3 generated (2026-09-03):** real source found and confirmed - "How to Choose a Backpack," REI Co-op
Expert Advice (article + embedded companion video "How to Choose Backpacking Packs"). See
`lessons/intermediate/Set_1/Lesson_3_Backpack/Lesson3_Backpack.md`. Runtime not stated on the page, estimated at
3-5 minutes based on similar REI videos - flagged as an open item, same as Lesson 2. Register is a larger flagged
deviation than Lessons 1-2's runtime overshoots: REI's full written guide is not simplified for learners, so
this lesson draws only from its simpler sections (capacity, basic frame types, core fit advice) and leaves
denser technical vocabulary (e.g. "daisy chain," "crampon patch") out entirely rather than force-fitting it.
Module alignment also flagged: the source is titled as a "how to choose" guide (closer on its face to Module 4,
Instructing), but its actual content is feature description and comparison, used here for Module 1 (Describing)
with the source's own "first...then" language repurposed to teach this lesson's assigned Speaking Skill
(Sequencing Language) rather than a physical-action procedure - reasoning kept in the lesson file's self-check
rather than decided silently. Student packet generated in the same pass as the lesson, per the Lesson Generation
Prompt's third addendum (2026-09-03) on combined .md/.html generation.

**Lesson 3 revised (2026-09-03), after user review of the student packet:** three fixes applied. (1) Day 1's
Mystery Quote hook was rebuilt around a single cropped photo of one backpack detail (the hip belt), with students
describing what they see and guessing before any clue is given, replacing a version that named "liters" and
"hips" up front and gave the answer away - a .md-level content change. (2) Differentiated item counts across
Days 2-6 were rebalanced (more short items at Level 2, fewer but deeper items at Level 5) so time-on-task is
roughly even across all four task Levels - also a .md-level content change, then regenerated into the .html.
(3) The student packet's Closing Transfer Check script is now printed upside-down (CSS `transform:
rotate(180deg)`) as a physical deterrent against reading ahead, and the "Unit 1A/1B" labeling bug was corrected
to "Unit 3A/3B" - both applied directly to the .html only, since neither changes what the lesson actually asks
students to do.

**Lesson 4 generated (2026-09-03):** real source found and confirmed - "Great-Grandmother Proves It Is Never
Too Late to Learn," VOA Learning English (Setsuko Takamizawa, 91, learning English from her granddaughter
Natsuko to volunteer at the Tokyo Olympics; reported for Reuters by Jack Tarrant, adapted by John Russell). See
`lessons/intermediate/Set_1/Lesson_4_GreatGrandmother/Lesson4_GreatGrandmother.md`. Runtime 4:01,
1 second past the Level 3 target - negligible, consistent with the established soft-target treatment. Two
genuine deviations flagged rather than silently forced: (1) the plan's vocabulary theme is "Personality &
character traits," but the source's real glossary is family-relationship and general vocabulary; the
character-trait angle is delivered through the Day 4/8 inference tasks instead of the word list. (2) the plan's
speaking skill is "Asking for Clarification," but this narrated profile contains no quotable clarification
exchange; the Day 5 Speaking Skill Spotlight is grounded in the source's real teaching context (daily new
words/phrases) rather than a directly quoted moment - flagged as the lesson's most significant open item.
Student packet generated in the same pass, applying every formatting convention established during Lesson 3's
review cycle (Good to Know at the top, citebox at the point of watching, compact inline multiple-choice, real
picture placeholders, word banks positioned right before their items, balanced task-duration item counts, and
the upside-down treatment extended to this lesson's own predict-from-context pause point in the Closing
Transfer Check).

---

## Module 1: Describing, Advanced Band

### Set 1 (planned 2026-09-01) - 2 of 4 lessons generated

| Lesson # | Content Format                          | Listening Strategy                       | Speaking Skill                    | Phase 1 Hook       | Phase 3 Protocol   | Vocabulary Theme                | Topic Direction                                                       |
| -------- | --------------------------------------- | ---------------------------------------- | --------------------------------- | ------------------ | ------------------ | ------------------------------- | --------------------------------------------------------------------- |
| 1        | Chef profile (home/studio tour)         | Listen for Stated vs. Implied Opinion    | Hedging an Opinion                | Mystery Quote      | Town Hall          | Culinary technique & atmosphere | A real chef's restaurant kitchen and cooking philosophy               |
| 2        | Architecture/preservation feature       | Recognize Examples                       | Summarizing What Someone Said     | Visual Inquiry     | Fishbowl           | Architecture & restoration      | A real historic building's restoration project                        |
| 3        | Nature/conservation documentary segment | Listen for Cause-and-Effect Language     | Turn-Taking/Interrupting Politely | Four-Corner Debate | Jigsaw             | Conservation & habitat          | A real conservation program protecting an endangered species' habitat |
| 4        | Fine-art craft-studio tour              | Listen for Signposting/Discourse Markers | Making Comparisons                | K-W-L Walk         | Concentric Circles | Technique & artistic vision     | A real glassblower's or sculptor's studio and process                 |

### Set 2 (planned 2026-09-01) - Planned only, not yet generated

| Lesson # | Content Format                   | Listening Strategy                         | Speaking Skill           | Phase 1 Hook       | Phase 3 Protocol   | Vocabulary Theme                 | Topic Direction                                                |
| -------- | -------------------------------- | ------------------------------------------ | ------------------------ | ------------------ | ------------------ | -------------------------------- | -------------------------------------------------------------- |
| 5        | Urban-planning walking tour      | Predict from Context Before Confirming     | Giving Examples phrases  | Mystery Quote      | Town Hall          | Urban design & public space      | A real city's public-space or waterfront redevelopment project |
| 6        | Museum/exhibit-guide description | Listen for Sequence Markers                | Sequencing Language      | Visual Inquiry     | Fishbowl           | Provenance & display language    | A real museum's flagship or famous exhibit                     |
| 7        | Behind-the-scenes facility tour  | Listen for Contrastive/Concession Language | Asking for Clarification | Four-Corner Debate | Jigsaw             | Scientific equipment & discovery | A real research facility or observatory, behind the scenes     |
| 8        | Atelier/workshop profile         | Listen for Main Ideas/Gist                 | Agree/Disagree phrases   | K-W-L Walk         | Concentric Circles | Precision & couture design       | A real fashion designer's or luxury craftsman's atelier        |

**Open items, flagged 2026-09-03, resolved in part 2026-09-04:** Lessons 1-2 were generated under the
pre-correction 8-day cycle and had not received the retroactive 2-day restructure that Intermediate Set 1 got.
**Restructured 2026-09-04:** both lessons rewritten to the current Day 1 (Unit A)/Day 2 (Unit B) architecture,
using the Lesson Generation Prompt's fifth-addendum mapping table - no task, quote, vocabulary item, or
differentiated activity was cut, only reorganized, matching Intermediate Set 1's own restructure precedent.
Both lessons' student packets were also rebuilt from scratch to match every current Student Print Formatting
Prompt convention (Good to Know at the top, citebox at the point of watching, compact inline multiple-choice,
real picture placeholders, word banks positioned before their items, multi-source Task D layout for Level 7,
upside-down Closing Transfer Check script) - see `lessons/advanced/Set_1/Lesson_1_LostKitchen/Lesson1_LostKitchen.md`
and `lessons/advanced/Set_1/Lesson_2_LivingTextbooks/Lesson2_LivingTextbooks.md`, and their
matching `..._Packet.html` files in each lesson's own folder. **Still open:** Set 1 remains incomplete - only 2 of its 4 lessons
exist (Lessons 3-4, Nature/conservation and Fine-art craft-studio per the table above, are not yet generated).
This was a deliberate scope decision (per user direction 2026-09-04: restructure what exists, don't generate
what's missing in the same pass) rather than an oversight - generate Lessons 3-4 whenever Advanced Band work
next resumes, the same way Set 1 (Lessons 1-2) was generated originally.

**Lesson 1 generated (2026-09-01), restructured (2026-09-04):** two real sources - primary: PBS NewsHour, "It
was supposed to be a 'quiet little cafe' in Maine. It turned into a culinary phenomenon" (Erin French, The Lost
Kitchen, Freedom, Maine); secondary (Level 7 only, excerpt): Radio Cherry Bombe podcast interview with Erin
French. See `lessons/advanced/Set_1/Lesson_1_LostKitchen/Lesson1_LostKitchen.md`.

**Lesson 2 generated (2026-09-02), restructured (2026-09-04):** two real sources - primary: PBS NewsHour
Weekend, "What's behind an effort to preserve mid-century modern architecture in Phoenix" (Alison King/Modern
Phoenix, Robrt Pela, Adam Millsap, Rashad Shabazz, Craig DeMarco, Tyler Sternberg); secondary (Level 7 only,
excerpt): Modern Phoenix's Beadle Archive page on the White Gates Residence. See
`lessons/advanced/Set_1/Lesson_2_LivingTextbooks/Lesson2_LivingTextbooks.md`.

---

**Day-count correction, applied program-wide (2026-09-03):** the Lesson Generation Prompt's Unit Architecture
was corrected from an 8-day cycle (Unit A across Days 1-4, Unit B across Days 5-8, 600 minutes per lesson) to
the real 2-day cycle (Day 1 = Unit A, Day 2 = Unit B, 75 minutes each, 150 minutes per lesson) - see that
prompt's fifth addendum. Practical effect: one module's 8-day real budget is 4 lessons at 2 days each, not 8
lessons at 8 days each. All four Intermediate Module 1 lessons already generated (Lessons 1-4: New Bakery,
Porto Food Tour, How to Choose a Backpack, Great-Grandmother Learns English) were retroactively rewritten into
the corrected Day 1/Day 2 structure - no task, vocabulary item, quote, or differentiated activity was cut in
any of them, only reorganized into two real class periods instead of eight, per each file's own restructure
note and updated self-check. The Module 1 Intermediate Lesson Plan's day-count note was corrected to match.
Advanced Module 1 Lessons 1-2 received the same restructure treatment on 2026-09-04 (see above), completing the
day-count correction across every lesson generated so far in this family.
**Reserve bank decision (resolved; terminology superseded by the Sets note below - kept as "reserve bank" here
since that's what it was called at the time):** rows 5-8 of that plan's table stay in as what is now called Set
2, for when Module 1 is retaught with fresh material, rather than being trimmed - Lessons 1-4 (Set 1) already
fill the module's real 8-day allocation on their own.

**Second review pass (2026-09-03), Lessons 1-2 checked against the fully updated prompts:** comparing Lessons
1-2 against the current Lesson Generation Prompt and Student Print Formatting Prompt (both had accumulated
fixes since these two lessons were first built) found two things. (1) Lesson 1's original day-count retrofit had
silently dropped two items - Level 2's "why do people keep coming back to Seylou" fact-check and Level 5's
evaluative-language item about Bethony's closing quote - both restored. Lesson 2 came through its retrofit with
content intact. (2) Neither lesson's item counts had ever been rebalanced per the fourth addendum (which
postdates both lessons' original builds); both are now calibrated the same way Lessons 3-4 already are. Both
lessons' `.html` packets were rebuilt from scratch to match every Student Print Formatting Prompt convention
established during Lesson 3's review cycle (Good to Know at the top, citebox at the point of watching with no
"ask your teacher" line, compact inline multiple-choice, real picture placeholders, word banks positioned right
before their items, no redundant "(Choose Your Task)" label, Learn the Phrase frames inside the spotlight box,
and the upside-down treatment for each lesson's Closing Transfer Check script) - unlike the day-count
restructure, these two packets genuinely had not been touched since their original 2026-09-01/09-02 builds and
needed the full update, not just a check. This is the same review-and-rebuild pattern later applied to Advanced
Lessons 1-2 on 2026-09-04.

**Sets concept introduced (2026-09-03).** A Module/Band can now hold more than one rotation of lessons over
time - a fresh batch of topics for a semester where the module is retaught, without discarding what was taught
before. Each such rotation is a **Set**: 4 lessons, matching the corrected module size. Lesson numbering stays
global within a Module/Band, continuing across Sets rather than restarting (Set 2 continues at Lesson 5, Set 3
would start at Lesson 9, and so on). This log's existing 8-row tables for both Module 1 sections above were
retroactively split into Set 1 (Lessons 1-4) and Set 2 (Lessons 5-8) subsections to match - see the Module
Lesson-Plan Generation Prompt's Sets note for the full rule, including how cross-Set adjacency works (a new
Set's Lesson 1 is checked against the most recent existing Set's final lesson, one level narrower than the
cross-Module check). A Set is not tied to a semester in the plan itself; note an actual teaching term against a
Set only once it's been assigned to one.

**Assessment Generation Prompt introduced (2026-09-04).** A new prompt in this family
(`Generate_Assessment_Prompt_v1.md`) generates a per-Set Listening assessment (Part A, new unseen source,
task-Level tiered) and a per-Set Speaking assessment (Part B, mechanism split by band: Teams recording as the
default and formal assessment for Beginner/Intermediate, with a same-task teacher-approved live-delivery option;
live presentation as the default for Advanced/Proficient, with a same-task Teams-recording alternate always also
generated). First assessment generated 2026-09-04 against Module 1 Intermediate Set 1 - see
`lessons/intermediate/Set_1/Set1_Intermediate_Assessment.md`. Not yet run for Advanced Band, since
Advanced Set 1 is not yet complete (see open items above).

**Intermediate Set 1 assessment regenerated (2026-09-06), replacing the corrupted stub.** Part A (Listening)
uses a real, verified source, "Visitors Laugh Away Troubles at the HaHaHouse Museum" (VOA Learning English,
Andrea Golubic's laughter museum in Zagreb, Croatia), distinct from all 4 taught sources, with tiered items
covering all four of the Set's listening strategies (Main Ideas/Gist, Recognize Examples, Sequence Markers,
Predict from Context). Part B (Speaking) is a Teams Speaking Progress solo recording (Intermediate's default
mechanism), emphasizing Making Comparisons and Sequencing Language, with the same-task live-delivery option
noted. See `lessons/intermediate/Set_1/Set1_Intermediate_Assessment.md`.

---

**Format for the next Set's entry** (append below this line, do not overwrite anything above):

```
## Module N: <Name>, <Band> Band

### Set S (planned <date>)
| Lesson # | Content Format | Listening Strategy | Speaking Skill | Phase 1 Hook | Phase 3 Protocol | Vocabulary Theme | Topic Direction |
|---|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... | ... | ... |
```

(Lesson # continues the global numbering for this Module/Band across every Set already planned - do not restart
at 1 for Set 2 onward. If this Module/Band's section already exists above, append this Set as a new subsection
under it rather than creating a duplicate `## Module N` heading.)
