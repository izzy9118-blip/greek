# Roadmap

## Stage 0 — Founding

- establish mission and governing principles;
- define architecture and production order;
- define source and copyright boundaries;
- establish identifiers, provenance, and validation requirements.

**Exit condition:** founding documents agree on scope, object families, and first implementation.

## Stage 1 — Data contract

- define `docs/data-model.md`;
- define controlled grammatical vocabulary;
- define stable identifier formats;
- create schemas for units, sections, vocabulary, paradigms, exercises, and learner responses;
- add schema validation tests.

**Exit condition:** representative objects validate and cross-reference correctly.

## Stage 2 — Introduction prototype

Build a small end-to-end learning path from the textbook's introduction:

- alphabet;
- breathings;
- vowel quantity and diphthongs;
- pronunciation;
- punctuation;
- accent terminology;
- pronunciation and accent drills.

This stage tests polytonic Greek input, answer comparison, feedback, and progress saving before the larger grammar curriculum is entered.

**Exit condition:** the learner can complete and resume an interactive introductory lesson.

## Stage 3 — Unit 1 curriculum

Represent Unit 1 as structured data:

- noun overview;
- gender, number, and case;
- first-declension nouns;
- second-declension nouns;
- article;
- word order;
- vocabulary;
- drills and exercises represented without reproducing unnecessary copyrighted text.

**Exit condition:** Unit 1 can be taught, practiced, assessed, and reviewed through the application.

## Stage 4 — Minimal learning application

- lesson navigation;
- prompt rendering;
- Greek input;
- structured parsing answers;
- feedback;
- attempt history;
- local persistence;
- cumulative review queue.

**Exit condition:** a user can study the introduction and Unit 1 without editing data files manually.

## Stage 5 — Units 2–3 and first cumulative review

- verb overview and principal parts;
- present, imperfect, future, and aorist indicative active;
- perfect and pluperfect;
- subjunctive and optative;
- purpose clauses and sequence of moods;
- cumulative review and examination model.

**Exit condition:** the first three units and their review cycle operate under the same schemas and engine.

## Stage 6 — Curriculum expansion

Enter and validate Units 4–10, then Units 11–20 in controlled batches. Each batch includes:

- source mapping;
- structured objects;
- tests;
- lesson flow;
- review integration;
- reading support.

## Stage 7 — Reading environment

- word-level reveal controls;
- parsing workspace;
- syntax notes;
- vocabulary thresholds;
- passage history;
- reduced-scaffolding modes;
- support for the textbook's progression toward unadapted Greek authors.

## Stage 8 — Advanced morphology and tutoring

- broader form generation and recognition;
- principal-part reasoning;
- error-pattern detection;
- adaptive prompt selection;
- guided questioning;
- explanation generation constrained by validated curriculum data.

## Immediate next production unit

Create `docs/data-model.md` and the first schema package. The first concrete objects should be:

1. unit;
2. section;
3. vocabulary entry;
4. grammar rule;
5. paradigm;
6. exercise item;
7. learner attempt.
