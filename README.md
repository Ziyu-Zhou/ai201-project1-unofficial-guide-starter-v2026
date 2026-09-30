# The Unofficial Guide

Michael Zhou
Corpus: Campus_life

> **This file is your submission.** Fill it in as you go — most sections get
> written during the milestone that produces them, not at the end.
>
> How the starter works, and every command you'll need, is in `RUNNING.md`.
> Leave that file alone.
>
> **Paste everything as text.** No screenshots, no video. A typed table gets
> full credit; a picture of the same table gets none.
>
> Delete these instruction blocks as you replace them. The `<!-- -->` comments
> are notes to you and don't show up when the page renders — you can leave them
> or remove them.

---

# Unit 1

## What This Does

<!-- Three or four sentences. Which corpus you picked, and the kinds of
     questions your system answers. Write it for someone who has never seen
     this repo.

     Milestone 5. -->
     I choose the campus_life corpus, my system answer question that student may encouter from their day to day in college, it will give the most relevant answer and refuse to answer if nothing seems relevant enough.

## Chunking Strategy

**Chunk size:**
**Overlap:**

<!-- What about YOUR documents made you pick these numbers? Short posts and
     long sectioned guides don't want the same chunking, and "800 seemed
     reasonable" earns nothing. Point at something you noticed when you read
     the documents in Milestone 1.

     If you changed your mind partway through, say so and say why. That's worth
     more than pretending you got it right first time.

     Milestone 3. -->

## Sample Chunks

<!-- Five chunks, pasted as text. Label each one and name the file it came from
     AND the function that produced it — the grader checks your code against
     what you claim here.

     `python app.py chunks -n 5` prints all three for you. Copy them straight
     across.

     Milestone 3. -->

======================================================================
Chunk 1  |  source: admin_add_drop_deadline.txt#0  |  produced by: chunker.py::fallback_split
======================================================================
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.

======================================================================
Chunk 2  |  source: course_biol_160.txt#0  |  produced by: chunker.py::fallback_split
======================================================================
BIOL 160 Cell Biology

I lived here my sophomore year. Format is lecture three times a week with a weekly lab. Assessment: four unit tests and a cumulative final. Not curved.

Expect 9 to 11 hours a week, the heaviest first-year course by reputation.

The one piece of advice: the unit tests come fast, roughly every three weeks; falling behind once is very hard to recover from.

======================================================================
Chunk 3  |  source: course_hist_118_workload.txt#0  |  produced by: chunker.py::fallback_split
======================================================================
Workload for HIST 118 Modern World History

People keep asking so: a lot of reading, about 120 pages a week, but no problem sets. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.

======================================================================
Chunk 4  |  source: dining_pellew_dining_hall_followup.txt#0  |  produced by: chunker.py::fallback_split
======================================================================
Re: Pellew Dining Hall

Adding to what people have said about Pellew Dining Hall. The wait figure of 12 to 18 minutes at peak matches what I've seen. If you're trying to eat between classes, go before 11:45 and it's a different building entirely.

Also worth saying: the furthest hall from anywhere, next to the athletics centre. Nobody tells you this at orientation.

======================================================================
Chunk 5  |  source: housing_innisfree_hall.txt#0  |  produced by: chunker.py::fallback_split
======================================================================
Innisfree Hall — what it's actually like

Transferred in last year, so take this with a grain of salt. Built 1991, renovated 2022. Rooms are doubles arranged as pairs sharing one bathroom between two rooms.

The good: the shared-bathroom-between-two-rooms arrangement is the best compromise on campus.

The bad: no air conditioning, which matters for the first three weeks of September.

Laundry costs $1.75 wash, $1.75 dry, app-based. On noise: moderate; the building is L-shaped and the short wing is much quieter.

For each one, ask: could someone answer a question using only this,
without reading what came before or after?

## Sample Answer

**Question:** How much does one wash and one dry cost in Aldridge Hall, and what payment method is accepted?

**Answer:**

```text
One wash costs $1.75 and one dry costs $1.50, and only cards are accepted.

Sources: `housing_aldridge_hall_laundry.txt` and `housing_aldridge_hall.txt`

Sources retrieved: housing_aldridge_hall.txt, housing_aldridge_hall_laundry.txt, housing_calder_annexe_laundry.txt, housing_innisfree_hall_laundry.txt, housing_old_brewhouse_laundry.txt
```

This is the actual model response from the Milestone 4 run on September 22,
2026, using `--top-k 5 --threshold 0.64 --show-prompt`. Both cited Aldridge
files support the prices and card-only payment rule. The other retrieved
files describe different residences and were not used as sources in the answer.

**My relevance cutoff:** **0.64**, set in `config.py`.

With `campus_life`, `all-MiniLM-L6-v2`, cosine distance, and top-k = 5, the five
in-corpus best distances ranged from **0.141968 to 0.458602**. The five
out-of-scope best distances ranged from **0.824593 to 0.934011**. The gap is
between **0.458602 and 0.824593**; its midpoint is approximately **0.641597**,
so I chose **0.64**. This balances the margins to the two observed groups
instead of placing the cutoff close to either group's boundary.

The gate accepts only when the best distance is strictly below the cutoff.
Applying the actual gate function to these retrieved results accepted **5/5**
in-corpus questions and refused **5/5** out-of-scope questions. These are tuning
results on ten questions, not a guarantee for unseen questions.

| Question | In corpus? | Best distance |
|---|---|---|
| What is the deadline for adding a course, and when does dropping a course result in a W on your transcript? | Yes | 0.141968 |
| How much does one wash and one dry cost in Aldridge Hall, and what payment method is accepted? | Yes | 0.262994 |
| How often does the campus shuttle run on weekdays compared with weekends? | Yes | 0.458602 |
| How far in advance can students book group study rooms, and how many two-hour blocks can each person reserve per week? | Yes | 0.211249 |
| In CS 210, how many midterms and final exams are there, and which exams are curved? | Yes | 0.217425 |
| What is the capital of Mongolia? | No | 0.824593 |
| How do I change the oil in a diesel engine? | No | 0.934011 |
| Who won the 1994 World Cup? | No | 0.885860 |
| What is the recommended dosage of ibuprofen for a headache? | No | 0.844232 |
| How do I write a for loop in Rust? | No | 0.895998 |

**Retrieval review and top-k:** I printed and read all five returned chunks
for the first three test questions. The add/drop source directly answers the
first question; the withdrawal note is related but describes a different
process, while the remaining results are less relevant. For Aldridge laundry,
the first and fifth results support the answer; the middle three share laundry
wording but describe other residences. For shuttle frequency, only the first
result answers the question; the workload and dining results share timing
language but do not establish shuttle frequency.

I kept **TOP_K = 5** because the correct source ranks first for all five test
questions and the fifth Aldridge result provides corroborating information
that top-k = 4 would remove. This retains some irrelevant context, so grounding
still matters: passing the gate does not mean every returned chunk is relevant.
I have not established that five is optimal for unseen questions.

**Grounding review:** I inspected `GROUNDING_INSTRUCTION` and the assembled
prompt using `--show-prompt`. The instruction requires using only the supplied
documents, admitting missing information, and naming the source filename.
The generated sample used the correct Aldridge facts despite other halls in
the context, so I kept the instruction unchanged for now. One successful
sample does not establish that every generated answer will be grounded.

<details>
<summary>All retrieved sources and distances, ordered by rank</summary>

**What is the deadline for adding a course, and when does dropping a course result in a W on your transcript?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `admin_add_drop_deadline.txt` | 0.141968 |
| 2 | `admin_withdrawal_deadline.txt` | 0.439761 |
| 3 | `admin_pass_fail_option.txt` | 0.475467 |
| 4 | `admin_grade_appeals.txt` | 0.515115 |
| 5 | `admin_transcript_requests.txt` | 0.520325 |

**How much does one wash and one dry cost in Aldridge Hall, and what payment method is accepted?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `housing_aldridge_hall_laundry.txt` | 0.262994 |
| 2 | `housing_innisfree_hall_laundry.txt` | 0.436394 |
| 3 | `housing_calder_annexe_laundry.txt` | 0.441160 |
| 4 | `housing_old_brewhouse_laundry.txt` | 0.469109 |
| 5 | `housing_aldridge_hall.txt` | 0.472427 |

**How often does the campus shuttle run on weekdays compared with weekends?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `transit_shuttle.txt` | 0.458602 |
| 2 | `course_stat_150_workload.txt` | 0.559362 |
| 3 | `course_cs_210_workload.txt` | 0.608923 |
| 4 | `dining_verrill_street_grill.txt` | 0.609416 |
| 5 | `course_econ_101_workload.txt` | 0.609953 |

**How far in advance can students book group study rooms, and how many two-hour blocks can each person reserve per week?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `study_group_rooms.txt` | 0.211249 |
| 2 | `course_cs_340.txt` | 0.494900 |
| 3 | `money_textbooks.txt` | 0.535110 |
| 4 | `course_cs_210.txt` | 0.542952 |
| 5 | `money_jobs.txt` | 0.544200 |

**In CS 210, how many midterms and final exams are there, and which exams are curved?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `course_cs_210_exams.txt` | 0.217425 |
| 2 | `course_cs_210.txt` | 0.375881 |
| 3 | `course_cs_340_exams.txt` | 0.393346 |
| 4 | `course_engl_205_exams.txt` | 0.476696 |
| 5 | `course_math_220_exams.txt` | 0.484556 |

**What is the capital of Mongolia?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `course_hist_118_exams.txt` | 0.824593 |
| 2 | `course_hist_118.txt` | 0.869272 |
| 3 | `housing_morrow_house.txt` | 0.890410 |
| 4 | `housing_morrow_house_laundry.txt` | 0.910530 |
| 5 | `course_hist_118_workload.txt` | 0.919347 |

**How do I change the oil in a diesel engine?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `admin_meal_plan_changes.txt` | 0.934011 |
| 2 | `course_econ_101_exams.txt` | 0.947412 |
| 3 | `housing_old_brewhouse_laundry.txt` | 0.954460 |
| 4 | `course_engl_205_exams.txt` | 0.964458 |
| 5 | `course_stat_150_exams.txt` | 0.967680 |

**Who won the 1994 World Cup?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `course_hist_118_exams.txt` | 0.885860 |
| 2 | `course_hist_118.txt` | 0.937370 |
| 3 | `admin_study_abroad.txt` | 0.947474 |
| 4 | `housing_innisfree_hall.txt` | 0.952119 |
| 5 | `course_engl_205_exams.txt` | 0.955027 |

**What is the recommended dosage of ibuprofen for a headache?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `money_textbooks.txt` | 0.844232 |
| 2 | `course_hist_118.txt` | 0.860232 |
| 3 | `course_econ_101.txt` | 0.864023 |
| 4 | `course_cs_340_exams.txt` | 0.865958 |
| 5 | `course_engl_205.txt` | 0.870331 |

**How do I write a for loop in Rust?**

| Rank | Source | Distance |
|---|---|---|
| 1 | `course_hist_118_exams.txt` | 0.895998 |
| 2 | `course_engl_205.txt` | 0.900157 |
| 3 | `course_engl_205_exams.txt` | 0.905611 |
| 4 | `course_hist_118.txt` | 0.914244 |
| 5 | `housing_calder_annexe_laundry.txt` | 0.917800 |

</details>

## How I Used AI

<!-- Two specific moments. For each: what you asked for, what came back, and
     what you changed about it.

     "I asked Claude to write the chunking function from my notes. It ignored
     the overlap, so I added that myself" is the level of detail we're after.
     "I used AI to help me code" is not.

     Milestone 5. -->

**1.**
I asked AI how the current chunking logic worked with campus_life and whether it needed changing. It found that all 88 documents already fit into individual chunks and recommended preserving each note whole. I chose a planned size of 600 characters with zero overlap, but left the existing code unchanged since the logic is coherent here.
**2.**

I asked AI how to measure retrieval distances for Milestone 4. It initially suggested a long Python script, so I asked for simpler commands that ran each question individually and inspected the results, then I give the results back to the AI and ask if these make sense to test if we got what we needed.

<!-- ── Stretch features ─────────────────────────────────────────────────────
     Doing one? Say so here BEFORE you start. A feature this README never
     claims earns nothing.
     ───────────────────────────────────────────────────────────────────────── -->

---

# Unit 2

<!-- These sections get ADDED to what's already above. Don't delete or rewrite
     unit 1 — the point is that someone can see what you said before you knew
     how it went. -->

## Run Log — Before

Raw three-pass evaluation: [saved answers and gate results](results/run_2026-09-29_2207_before.md),
produced by `run_eval.py::main` on September 29 at 22:07, with caching off.
This file was already committed in `57e1ebe`. This review uses those 15 saved
answers; it does not claim a new generation run. There is no `scorer.py`, so
answers were reviewed manually against `criteria.md` and the cited documents.

[Supplemental retrieval and chunk evidence](results/evidence_2026-09-29_before.md)
records three later retrieval passes and a separate inspection of source chunks,
with the same settings and no pipeline changes: `campus_life`, default index,
top-k 5, cutoff 0.64, chunk size 800, overlap 120. These checks made no model calls.
The original report stores retrieved source names and best distances but omits
chunk text; the supplement supplies that evidence. Its best distances and source
sets match the original report.

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 2. Every answer names a source | 5 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 3. Gate stops out-of-corpus questions | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 4. Chunks keep related answer facts together | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 5. Answers use facts from the correct campus subject | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |

Criterion 1 uses the saved source lists plus the supplemental retrieval checks.
Criterion 3 repeats the single deterministic gate measurement across columns.
Criterion 4 also repeats one deterministic inspection of the unchanged chunker;
it is independent of retrieval ranking. Criteria 2 and 5 assess each of the
15 generated answers separately. A target must hold in every run to be MET.

Manual question-level review (Q1–Q5 follow `questions.py`):

| Question | Complete facts in retrieved/source chunk (criteria 1 and 4) | Source named, runs 1/2/3 (criterion 2) | Correct, complete, supported answer, runs 1/2/3 (criterion 5) |
|---|---|---|---|
| Q1: Add/drop | End of second week to add; W after week two, in `admin_add_drop_deadline.txt#0` | Pass / Pass / Pass | Pass / Pass / Pass |
| Q2: Aldridge laundry | $1.75 wash, $1.50 dry, card only, in `housing_aldridge_hall_laundry.txt#0` | Pass / Pass / Pass | Pass / Pass / Pass |
| Q3: Shuttle | Every 20 minutes weekdays, 40 minutes weekends, in `transit_shuttle.txt#0` | Pass / Pass / Pass | Pass / Pass / Pass |
| Q4: Study rooms | Two weeks ahead, maximum two two-hour blocks per person per week, in `study_group_rooms.txt#0` | Pass / Pass / Pass | Pass / Pass / Pass |
| Q5: CS 210 | Two midterms, one final; midterms curved, final not, in `course_cs_210_exams.txt#0` | Pass / Pass / Pass | Pass / Pass / Pass |

All five relevant chunks retain the full cleaned source document, so no
answer-bearing sentence is cut at a boundary. Each ranks first in all three
supplemental retrieval passes. Q2 run 3 cites `housing_aldridge_hall.txt` rather
than the laundry-specific file; that existing document also supports all three
facts. Q4 runs 1 and 2 say "two blocks" without repeating "two-hour"; they answer
the requested count of two-hour blocks and give the booking window, so they pass.

### Criterion 1 — actual retrieved chunk

Supplemental retrieval pass 1, Q1, rank 1; `admin_add_drop_deadline.txt#0`,
distance 0.141968. Returned by `store.py::search`; produced by
`chunker.py::fallback_split` via `chunker.py::split_documents`.

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

### Criterion 2 — actual answer naming a source

Q2, run 1. Produced by `generate.py::answer_from_chunks`, called by
`run_eval.py::run_once` and saved by `run_eval.py::write_report`.

```text
In Aldridge Hall, one wash costs $1.75 and one dry costs $1.50, and it is card only (source: housing_aldridge_hall_laundry.txt and housing_aldridge_hall.txt).
```

### Criterion 3 — actual gate results

Copied from `run_eval.py::check_out_of_scope`, formatted by
`run_eval.py::write_report`; decisions come from `gate.py::check`.

| Out-of-scope question | Best distance | Gate |
|---|---|---|
| What is the capital of Mongolia? | 0.825 | refused |
| How do I change the oil in a diesel engine? | 0.934 | refused |
| Who won the 1994 World Cup? | 0.886 | refused |
| What is the recommended dosage of ibuprofen for a headache? | 0.844 | refused |
| How do I write a for loop in Rust? | 0.896 | refused |

The supplemental check also captured the refusal text from `gate.py::REFUSAL`
for each blocked question:

```text
I don't have enough information about that.
```

### Criterion 4 — actual source chunk

Separate chunk inspection, `study_group_rooms.txt#0`. Produced by
`chunker.py::fallback_split`, called through `chunker.py::split_documents`.
The booking window, block length, and weekly limit remain in one complete sentence.

```text
Booking a group study room

Rooms book two weeks ahead through the library site, in two-hour blocks, maximum two blocks per person per week. The limit is per person, so a group of four can chain together eight hours if they coordinate.

Rooms 210 and 211 have whiteboards that actually erase. The others don't and no amount of scrubbing helps.
```

### Criterion 5 — actual answer about the correct subject

Q5, run 1. Produced by `generate.py::answer_from_chunks`, called by
`run_eval.py::run_once` and saved by `run_eval.py::write_report`.
Both cited CS 210 documents support the exam counts and curve rules.

```text
In CS 210, there are two midterms and a final exam. The midterms are curved, but the final is not.

Source: `course_cs_210_exams.txt` (also found in `course_cs_210.txt`)
```

## Verdicts

<!-- MET or MISSED for each of the five, against the target you wrote last
     unit — not a new one. Plus a sentence on how you decided. That sentence
     matters most where it was close.

     If your target said 4 of 5 and your runs came out 4, 3, 4, that's a MISS.
     The target has to hold, not show up occasionally.

     Milestone 2. -->

| # | Criterion | Verdict | How I decided |
|---|---|---|---|
| 1 | Retrieval | MET | All five questions have a top-five chunk containing every required fact; the supplemental checks place each relevant source first. |
| 2 | Sources | MET | All 15 non-refusal answers name at least one existing corpus document. |
| 3 | Gate | MET | All five out-of-scope questions were refused at cutoff 0.64; the lowest best distance was 0.825. |
| 4 | Chunk completeness | MET | All five relevant source chunks preserve complete answer-bearing sentences and all requested facts, independently of retrieval. |
| 5 | Correct subject and facts | MET | Each of the 15 answers covers every requested detail with support in its cited documents, including Q2's alternate citation and Q4's shorter wording discussed above. |

## Diagnoses

<!-- For each miss: which stage caused it, and how. The stage alone isn't
     enough — you need the mechanism.

     Not a diagnosis: "Question 3 didn't work."
     A diagnosis:     "Question 3 asks about laundry costs. The answer is in
                       one sentence that got split across two chunks, so
                       neither chunk on its own contains it."

     The five stages: loading → chunking → embedding → retrieval → generation.

     Look for a pattern. If three misses all ask about numbers, that's one
     problem, not three.

     Missed nothing? Say so, then say honestly whether your targets were set
     low, and which one you'd tighten and to what.

     Milestone 3. -->

## The Improvement

**What I changed:**

**Why I picked it:**

<!-- Connect it to a specific diagnosis above in one sentence. If you can't,
     you picked a fix because it sounded impressive. -->

### Run Log — After

<!-- Same format, same five criteria, three runs each.
     `python run_eval.py --label after` -->

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 |  |  |  |  |
| 2. Every answer names a source | 5 of 5 |  |  |  |  |
| 3. Gate stops out-of-corpus questions | 4 of 5 |  |  |  |  |
| 4. | | | | | |
| 5. | | | | | |

**Did it help?**

<!-- Say plainly whether it did, and how you know. If it made things worse,
     say that — a change that backfired, honestly reported, earns full credit
     and is more interesting than one that worked. What matters is that you can
     tell.

     Milestone 4. -->

## What's Still Broken

<!-- For each criterion still missed after your fix: what you'd do about it,
     and why you stopped where you did.

     "I ran out of time" is fine if it's true. Pretending nothing is left is
     not.

     Milestone 5. -->

## What I'd Do Differently

<!-- Knowing what you know now — which of your five criteria would you write
     differently, and why?

     Milestone 5. -->
