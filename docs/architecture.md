# Architecture

## 1. System boundary

Greek is divided into five cooperating layers:

1. curriculum data;
2. validation and reference services;
3. learning and assessment engines;
4. learner state;
5. user interface.

No layer should depend on page images or free-form textbook text at runtime.

## 2. Proposed repository layout

```text
greek/
├── README.md
├── docs/
│   ├── charter.md
│   ├── architecture.md
│   ├── roadmap.md
│   └── data-model.md
├── curriculum/
│   ├── units/
│   ├── vocabulary/
│   ├── grammar/
│   ├── paradigms/
│   ├── exercises/
│   └── readings/
├── data/
│   ├── schemas/
│   └── registries/
├── engine/
│   ├── tutor/
│   ├── assessment/
│   ├── morphology/
│   ├── scheduler/
│   └── progress/
├── app/
├── tests/
└── tools/
```

## 3. Curriculum layer

The curriculum layer stores immutable or versioned learning objects. It contains no learner-specific state.

Primary object families:

- unit;
- textbook section;
- vocabulary entry;
- grammar rule;
- paradigm;
- drill;
- exercise;
- reading passage reference;
- assessment item;
- answer key or scoring rule.

Each object must have a stable identifier, source reference, status, and schema version.

## 4. Validation and reference layer

This layer checks:

- required fields;
- identifier uniqueness;
- cross-reference integrity;
- valid grammatical labels;
- Unicode normalization;
- allowed answer variants;
- source-location formatting;
- dependency order between lessons.

It also exposes reference services for vocabulary, paradigms, grammatical terminology, and cross-unit dependencies.

## 5. Learning engine

The learning engine selects what the learner should do next. It should support:

- guided lesson mode;
- drill mode;
- cumulative review;
- weak-area practice;
- reading mode;
- examination mode.

Selection must be based on curriculum prerequisites and learner evidence, not only on unit completion.

## 6. Assessment engine

The assessment engine evaluates responses at the smallest meaningful level.

A parsing response may be scored separately for:

- lemma;
- part of speech;
- tense;
- voice;
- mood;
- person;
- number;
- case;
- gender;
- syntactic function;
- accent or spelling.

A partially correct answer should produce partial diagnostic evidence rather than a single undifferentiated failure.

## 7. Morphology service

The morphology service will begin as a controlled lookup and generation system driven by validated paradigms. A later version may perform broader morphological analysis.

Initial responsibilities:

- generate requested forms from a known lemma and paradigm;
- compare learner forms with accepted forms;
- identify features represented by endings;
- provide paradigm references;
- preserve irregular and exceptional forms explicitly.

## 8. Review scheduler

The scheduler records evidence of recall and selects future reviews. It must operate independently across knowledge dimensions. A learner may know a word's meaning but not its principal parts, accent, gender, or declension.

Review records should therefore attach to skills or features, not merely to whole vocabulary entries.

## 9. Learner state

Learner data must be separate from curriculum data.

It includes:

- lesson position;
- attempts;
- response history;
- error classifications;
- mastery estimates;
- scheduled reviews;
- reading history;
- preferences.

The first implementation may use local JSON or SQLite. The domain model should permit later migration without changing curriculum identifiers.

## 10. Interface

The first interface should be deliberately simple. A command-line or lightweight local web application is sufficient if it reliably supports:

- selecting a lesson;
- answering prompts;
- entering polytonic Greek;
- receiving precise feedback;
- reviewing mistakes;
- resuming progress.

Interface design must not determine the internal curriculum format.

## 11. Technology direction

The initial implementation should use Python 3.12 or later, typed domain models, JSON Schema or equivalent validation, pytest, and SQLite when persistent learner state is introduced.

Technology choices remain subordinate to curriculum correctness, Unicode handling, portability, and testability.

## 12. Test strategy

Tests will cover:

- schema validation;
- identifier uniqueness;
- Unicode normalization;
- paradigm generation;
- accepted-answer comparison;
- assessment scoring;
- prerequisite traversal;
- progress persistence;
- regression cases for Greek accents and breathings.
