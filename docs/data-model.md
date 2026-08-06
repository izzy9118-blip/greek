# Data Model

## 1. Purpose

The data model converts the curriculum into stable, validated learning objects. It separates source-derived curriculum data from learner-specific records and from application behavior.

All objects use UTF-8 and must preserve polytonic Greek accurately.

## 2. Common fields

Every curriculum object should include:

```yaml
id: stable identifier
type: object family
schema_version: schema version
status: draft | reviewed | validated | deprecated
title: human-readable label
source:
  work: Hansen and Quinn, Greek: An Intensive Course
  unit: unit number or null
  section: numbered section or null
  page: printed page or range
  note: optional source detail
created_at: ISO-8601 timestamp
updated_at: ISO-8601 timestamp
```

Derived or original material also includes:

```yaml
origin: source-derived | editorial | generated
```

## 3. Identifier convention

Identifiers are stable and never reused.

```text
UNT-001                 unit
SEC-0001                textbook section
VOC-000001              vocabulary entry
GRM-000001              grammar rule
PAR-000001              paradigm
EXR-000001              exercise item
REA-000001              reading reference
ASM-000001              assessment item
ATT-000000001           learner attempt
SKL-000001              assessable skill
```

The identifier does not encode mutable meaning beyond the object family.

## 4. Unit

A unit groups sections, vocabulary, drills, exercises, reviews, and readings.

Required fields:

```yaml
id: UNT-001
type: unit
number: 1
title: Unit 1
prerequisites: []
section_ids: []
vocabulary_ids: []
exercise_ids: []
reading_ids: []
skill_ids: []
```

The introduction may use `UNT-000` while retaining the same model.

## 5. Section

A section represents a numbered grammatical presentation.

```yaml
id: SEC-0013
type: section
number: 13
title: Nouns: Overview
unit_id: UNT-001
prerequisite_section_ids: []
concept_ids: []
rule_ids: []
paradigm_ids: []
```

A section record summarizes structure and references; it should not reproduce an entire copyrighted textbook section.

## 6. Vocabulary entry

```yaml
id: VOC-000001
type: vocabulary_entry
lemma: λόγος
normalized_lemma: λόγος
principal_forms:
  - λόγος
  - λόγου
part_of_speech: noun
gender: masculine
declension: second
glosses:
  - word
  - speech
  - story
first_unit: UNT-001
accent_class: persistent
notes: []
source_locations: []
skill_ids: []
```

Verb entries may include principal parts. Prepositions include governed cases. Irregular or exceptional information must be explicit rather than inferred silently.

## 7. Grammar rule

```yaml
id: GRM-000001
type: grammar_rule
title: Nominative case: subject use
statement: concise original formulation
scope:
  units: [UNT-001]
  sections: [SEC-0013]
prerequisites: []
examples: []
exceptions: []
skill_ids: []
```

The `statement` should be an original concise formulation unless a limited quotation is specifically justified and identified.

## 8. Paradigm

```yaml
id: PAR-000001
type: paradigm
title: Second-declension masculine noun
lemma_id: VOC-000001
features:
  part_of_speech: noun
  declension: second
  gender: masculine
forms:
  - surface: λόγος
    case: nominative
    number: singular
  - surface: λόγου
    case: genitive
    number: singular
```

Each form may also record stem, ending, accent explanation, alternate forms, and notes.

## 9. Skill

A skill is the smallest tracked competence.

```yaml
id: SKL-000001
type: skill
domain: morphology
name: Identify nominative singular second-declension masculine nouns
prerequisites: []
introduced_in: SEC-0015
```

Suggested domains:

- alphabet;
- pronunciation;
- accentuation;
- vocabulary;
- morphology;
- syntax;
- parsing;
- translation;
- composition;
- reading.

## 10. Exercise item

```yaml
id: EXR-000001
type: exercise_item
unit_id: UNT-001
section_ids: [SEC-0015]
exercise_kind: parse
prompt:
  display: λόγους
response_schema:
  required_features:
    - case
    - number
accepted_answers:
  - case: accusative
    number: plural
skill_ids: [SKL-000001]
feedback_rules: []
source_reference:
  kind: adapted-or-original
```

Exercise kinds may include:

- recognize;
- recall;
- parse;
- generate;
- transform;
- match;
- explain;
- translate;
- compose;
- read aloud.

Source-derived exercises should normally be referenced or transformed into original practice rather than copied wholesale.

## 11. Reading reference

```yaml
id: REA-000001
type: reading_reference
author: Plato
work: Gorgias
passage: 455a8-456c2
unit_id: UNT-016
text_storage: reference-only | licensed | public-domain | user-supplied
vocabulary_threshold: null
notes: []
```

The model distinguishes bibliographic reference from the legal basis for storing the text itself.

## 12. Assessment item

Assessment items may reuse exercise content but add scoring and mastery evidence.

```yaml
id: ASM-000001
type: assessment_item
exercise_id: EXR-000001
scoring:
  mode: feature-weighted
  maximum: 2
  features:
    case: 1
    number: 1
mastery_evidence:
  skill_ids: [SKL-000001]
```

## 13. Learner attempt

Learner attempts are not curriculum objects and belong in learner storage.

```yaml
id: ATT-000000001
learner_id: local-default
item_id: ASM-000001
started_at: ISO-8601 timestamp
submitted_at: ISO-8601 timestamp
response: {}
score: 0
maximum_score: 2
feature_results:
  case: incorrect
  number: correct
error_codes:
  - MORPH_CASE_CONFUSION
hints_used: 0
```

## 14. Mastery record

```yaml
learner_id: local-default
skill_id: SKL-000001
state: new | learning | review | mastered
confidence: 0.0
last_attempt_at: null
next_review_at: null
success_streak: 0
failure_count: 0
```

Mastery is evidence-based and reversible. A previously mastered skill may return to review after repeated failures.

## 15. Error taxonomy

Initial error families:

```text
ORTHOGRAPHY
ACCENT
BREATHING
VOCABULARY_MEANING
VOCABULARY_LEMMA
MORPH_CASE
MORPH_GENDER
MORPH_NUMBER
MORPH_TENSE
MORPH_VOICE
MORPH_MOOD
MORPH_PERSON
SYNTAX_FUNCTION
SYNTAX_AGREEMENT
TRANSLATION_OMISSION
TRANSLATION_RELATION
```

Specific codes may be added beneath these families.

## 16. Unicode policy

- store canonical Unicode text;
- validate normalization consistently;
- do not strip accents or breathings from authoritative forms;
- permit explicitly configured accent-insensitive practice only at the assessment layer;
- retain macrons or other pedagogical marks when the curriculum requires them;
- test final sigma, combining marks, iota subscript, diaeresis, and punctuation.

## 17. Validation rules

At minimum, validation must confirm:

1. identifier format and uniqueness;
2. schema version support;
3. valid controlled grammatical terms;
4. existence of referenced objects;
5. source information for source-derived content;
6. complete grammatical feature sets for paradigm forms;
7. valid learner-item references;
8. Unicode normalization policy;
9. nonnegative scoring totals;
10. prerequisite graphs without cycles.

## 18. First schema package

The first machine-readable schemas should be created for:

- `unit.schema.json`;
- `section.schema.json`;
- `vocabulary-entry.schema.json`;
- `grammar-rule.schema.json`;
- `paradigm.schema.json`;
- `exercise-item.schema.json`;
- `learner-attempt.schema.json`.
