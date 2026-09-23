# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
I chose 4 of 5 because the Aldridge laundry and CS 210 exam questions must distinguish their sources from similarly named notes about other halls and courses, leaving room for one retrieval mix-up. Requiring 5 of 5 would allow no such miss, while 3 of 5 would let the system fail on two questions whose answers are explicitly in the corpus.

**How to check:** Run the five QUESTIONS in questions.py and inspect the top
five retrieved chunks for each. Count a question as passing only if one chunk
contains the facts needed to answer every part of it.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
I require a source on every answer because the campus notes have document names that students can use to check prices, deadlines, and exam rules; allowing even one uncited answer would leave those details unverifiable. Requiring multiple sources per answer would be unnecessary because each of my five questions can be answered from one relevant document.

**How to check:** Inspect every non-refusal answer to the five QUESTIONS;
100% must name at least one existing corpus document. Refusals are evaluated
under criterion 3.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

<!-- The five questions are the ones in `OUT_OF_SCOPE` at the bottom of
     `questions.py`, and `run_eval.py` puts them through the gate and writes
     what happened into your run log. Swap them for your own if you'd rather —
     just keep five of them, or the "4 of 5" above has nothing to be 4 of. -->

**Why this target:**
I chose 4 of 5 because an out-of-scope Rust question could resemble the corpus’s computer science material, and the dosage question could resemble its health-center material even though the requested answers are absent. Requiring 5 of 5 leaves no room for one misleading similarity match, while 3 of 5 would allow two unsupported questions through the gate.

**How to check:** Run each OUT_OF_SCOPE question once. At least four must
be stopped by the gate and return the stated refusal without generation.

---

## 4. Chunks keep related answer facts together

For at least 4 of the 5 QUESTIONS in questions.py, at least one chunk from
its relevant source document must contain all facts needed to answer the
question, with no answer-bearing sentence cut off at either boundary.

**Why this target:**
I chose 4 of 5 because these short notes group related facts together, such as Aldridge’s wash price, dry price, and payment method, so a useful chunk should usually preserve a complete answer. Requiring 5 of 5 would rule out even one answer legitimately split across chunks, while 3 of 5 would tolerate fragmented context for two of these focused questions.

**How to check:** Inspect the chunks produced from the five relevant source
files, independently of retrieval ranking: admin_add_drop_deadline.txt,
housing_aldridge_hall_laundry.txt, transit_shuttle.txt, study_group_rooms.txt,
and course_cs_210_exams.txt. Record one pass or fail per question using the
rule above; at least four must pass.

---

## 5. Answers use facts from the correct campus subject

For at least 4 of the 5 QUESTIONS in questions.py, the answer must address
every part of the question, and every factual claim must be supported by a
cited document about the requested course, residence hall, service, or policy.
A refusal or an answer that mixes in another subject's facts fails.

**Why this target:**
I chose 4 of 5 because my questions ask for multiple details, such as weekday versus weekend shuttle frequency and which CS 210 exams are curved, so one omitted detail can make an otherwise grounded answer fail. Requiring 5 of 5 would demand complete coverage in every response, while 3 of 5 would permit incomplete or unsupported guidance on two everyday campus questions.

**How to check:** Compare each answer with its cited source text. Mark it as
passing only when every requested detail is present and every claim is
supported for the correct subject. A matching expects phrase alone does not
establish a pass.

---

## Review of all five criteria

The linked course self-check could not be accessed, so this is a local review
against the measurable-target guidance above, not a completed course self-check.
These are acceptance targets; no system results have been evaluated here.

| Criterion | Measurable target | Observable evidence |
| --- | --- | --- |
| 1. Retrieval | At least 4 of 5 questions | A top-five chunk contains every required answer fact. |
| 2. Sources | 100% of non-refusal answers | Each names an existing corpus document. |
| 3. Gate | At least 4 of 5 out-of-scope questions | Gate stops generation and returns the stated refusal. |
| 4. Chunk size | At least 4 of 5 questions | One source chunk retains all required facts and complete answer-bearing sentences. |
| 5. Correct subject and facts | At least 4 of 5 answers | All requested details appear and all claims have support in the cited sources for the correct subject. |

Each criterion has a defined check and a corpus-specific reason for its target.
Criteria 1 and 4 are distinct: criterion 1 checks what retrieval returns;
criterion 4 checks what chunking preserves before retrieval.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
