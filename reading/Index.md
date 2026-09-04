# Reading Index

The Reading modality has one active lesson type, with a second planned:

- **Passage Reading** (`passage-reading/`) — a fixed 2-day cycle built around
  one shared anchor text. See `passage-reading/Index.md`.
- **Novel Reading** (`novel-reading/`) — planned, not yet started. Expected to
  be variable-length and multi-chapter (e.g. an 8-day format spanning what
  Passage Reading treats as two modules), different enough from Passage
  Reading's fixed 2-day/4-lesson-module shape that it needs its own prompt
  family, rotation log, and lesson content rather than reusing Passage
  Reading's. No folder exists for it yet — it gets created once real work on
  it starts.

Both lesson types share `learningobjectives.csv` (repo root) and the same
8-Level/8-Module taxonomy; each keeps its own prompts, rotation log, and
generated lessons separate since the lesson formats differ.
