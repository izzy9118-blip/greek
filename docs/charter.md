# Greek Repository Charter

## 1. Founding purpose

Greek exists to build a durable program through which the learner can acquire Ancient Greek systematically and ultimately read original texts with independence, precision, and confidence.

The repository is both a software project and a curriculum project. It must preserve the structure of the source curriculum while converting that structure into validated, interactive learning objects.

## 2. Governing source

The foundational curriculum is Hardy Hansen and Gerald M. Quinn, *Greek: An Intensive Course*.

The first implementation follows the book's own progression: pronunciation and accentuation, noun morphology, verbal systems, moods and voices, participles, syntax, review examinations, and passages from Greek authors.

The repository may later support other grammars and texts, but additions must not silently alter or replace the Hansen–Quinn curriculum.

## 3. Educational objective

The program shall train the learner to:

1. read and pronounce polytonic Greek;
2. recognize and produce vocabulary forms;
3. identify stems and endings;
4. decline nouns, adjectives, pronouns, and articles;
5. conjugate verbs across tense, voice, mood, person, and number;
6. parse every form fully;
7. explain syntactic relationships;
8. translate accurately while preserving grammatical accountability;
9. compose controlled Greek appropriate to the learner's stage;
10. progress from drills to unadapted passages.

## 4. Pedagogical principles

### 4.1 Active production before passive disclosure

The program should ask the learner to retrieve, parse, transform, explain, or translate before presenting the complete answer.

### 4.2 Form-by-form accountability

A correct translation without grammatical understanding is incomplete. The learner must be able to account for significant forms and constructions.

### 4.3 Mastery with continued review

Completion of a lesson does not remove its material from study. Vocabulary, morphology, and syntax return through cumulative review.

### 4.4 Immediate use of new material

New morphology and syntax should be practiced using already familiar vocabulary whenever possible, following the textbook's stated drill method.

### 4.5 Reading as the governing end

Vocabulary, paradigms, and exercises are means toward reading Greek texts. The program must progressively reduce scaffolding.

### 4.6 Error as evidence

Incorrect answers are not merely marked wrong. They are classified so that the system can detect whether the difficulty concerns vocabulary, morphology, accentuation, syntax, or translation.

## 5. Repository principles

### 5.1 Source fidelity

Curriculum data must preserve the source's unit, section, drill, exercise, and reading organization. Derived explanations must be marked as derived rather than represented as textbook text.

### 5.2 Stable identity

Every lesson, section, vocabulary entry, paradigm, exercise, prompt, reading passage, and assessment item must receive a stable identifier.

### 5.3 Provenance

Every source-derived object must record its source location. Every generated or editorial object must record its origin and status.

### 5.4 Structured data before automation

The engine must operate on validated curriculum objects rather than unstructured page text.

### 5.5 Additive and reviewable development

Substantial changes should be committed in discrete production units. Existing validated data must not be silently rewritten.

### 5.6 Separation of concerns

Curriculum data, tutoring logic, learner records, user interface, and validation rules must remain independently testable.

### 5.7 Unicode correctness

Polytonic Greek must be preserved accurately. Normalization, accents, breathings, iota subscripts, macrons, and punctuation must be handled deliberately and tested.

## 6. Scope of the first system

The first complete system will support:

- the introduction and Units 1–20;
- vocabulary and vocabulary notes;
- paradigms and grammar rules;
- drills and exercises represented as structured prompts;
- parsing and transformation practice;
- cumulative review;
- learner progress and error history;
- guided reading passages.

The first version need not provide automatic free-form translation grading or a complete computational morphology engine. Those features may be added after the underlying curriculum and assessment model are stable.

## 7. Copyright boundary

The repository will not function as an unauthorized reproduction of the textbook. It will store only material that may lawfully be stored, user-authored study data, structured references, original explanations, and limited source excerpts where permitted. Source locations may be recorded without copying entire copyrighted sections.

## 8. Success condition

The project succeeds when the learner can work through the curriculum, receive precise feedback, retain earlier material through cumulative review, and approach original Greek passages with decreasing dependence on translation aids.

## 9. Founding status

This charter governs the initial design. It may be revised through explicit, versioned changes when experience with the curriculum or program reveals a genuine need.
