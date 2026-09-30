# Supplemental retrieval and chunk evidence

Captured: 2026-09-29T22:31:13

Captured independently while the after evaluation was running; no generation calls or additional pipeline changes.
Corpus: campus_life; top-k: 1; cutoff: 0.64; embedding: all-MiniLM-L6-v2.

Retrieval: `store.py::search`. Chunking: `chunker.py::split_documents`, which delegates to `chunker.py::fallback_split`.
Method: direct Python calls to these functions, three retrieval passes and one chunk inspection.

## Retrieval pass 1, Q1

What is the deadline for adding a course, and when does dropping a course result in a W on your transcript?

### Rank 1: admin_add_drop_deadline.txt#0

Distance: 0.141968; producer: `chunker.py::fallback_split`

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

## Retrieval pass 1, Q2

How much does one wash and one dry cost in Aldridge Hall, and what payment method is accepted?

### Rank 1: housing_aldridge_hall_laundry.txt#0

Distance: 0.262994; producer: `chunker.py::fallback_split`

```text
Laundry in Aldridge Hall

Machines take $1.75 wash, $1.50 dry, card only. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

## Retrieval pass 1, Q3

How often does the campus shuttle run on weekdays compared with weekends?

### Rank 1: transit_shuttle.txt#0

Distance: 0.458602; producer: `chunker.py::fallback_split`

```text
The campus shuttle

Runs a loop every 20 minutes from 7am to 11pm on weekdays and every 40 minutes on weekends. The published timetable is optimistic by about five minutes in the morning and accurate the rest of the day.

It's free with a student ID. The stop outside Fenwick Court is the one that gets skipped when the driver is behind, which is worth knowing if you live there.
```

## Retrieval pass 1, Q4

How far in advance can students book group study rooms, and how many two-hour blocks can each person reserve per week?

### Rank 1: study_group_rooms.txt#0

Distance: 0.211249; producer: `chunker.py::fallback_split`

```text
Booking a group study room

Rooms book two weeks ahead through the library site, in two-hour blocks, maximum two blocks per person per week. The limit is per person, so a group of four can chain together eight hours if they coordinate.

Rooms 210 and 211 have whiteboards that actually erase. The others don't and no amount of scrubbing helps.
```

## Retrieval pass 1, Q5

In CS 210, how many midterms and final exams are there, and which exams are curved?

### Rank 1: course_cs_210_exams.txt#0

Distance: 0.217425; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures — assessment

Two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Do the labs even though they're only 10% — the exams reuse the lab problems.
```

## Retrieval pass 2, Q1

What is the deadline for adding a course, and when does dropping a course result in a W on your transcript?

### Rank 1: admin_add_drop_deadline.txt#0

Distance: 0.141968; producer: `chunker.py::fallback_split`

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

## Retrieval pass 2, Q2

How much does one wash and one dry cost in Aldridge Hall, and what payment method is accepted?

### Rank 1: housing_aldridge_hall_laundry.txt#0

Distance: 0.262994; producer: `chunker.py::fallback_split`

```text
Laundry in Aldridge Hall

Machines take $1.75 wash, $1.50 dry, card only. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

## Retrieval pass 2, Q3

How often does the campus shuttle run on weekdays compared with weekends?

### Rank 1: transit_shuttle.txt#0

Distance: 0.458602; producer: `chunker.py::fallback_split`

```text
The campus shuttle

Runs a loop every 20 minutes from 7am to 11pm on weekdays and every 40 minutes on weekends. The published timetable is optimistic by about five minutes in the morning and accurate the rest of the day.

It's free with a student ID. The stop outside Fenwick Court is the one that gets skipped when the driver is behind, which is worth knowing if you live there.
```

## Retrieval pass 2, Q4

How far in advance can students book group study rooms, and how many two-hour blocks can each person reserve per week?

### Rank 1: study_group_rooms.txt#0

Distance: 0.211249; producer: `chunker.py::fallback_split`

```text
Booking a group study room

Rooms book two weeks ahead through the library site, in two-hour blocks, maximum two blocks per person per week. The limit is per person, so a group of four can chain together eight hours if they coordinate.

Rooms 210 and 211 have whiteboards that actually erase. The others don't and no amount of scrubbing helps.
```

## Retrieval pass 2, Q5

In CS 210, how many midterms and final exams are there, and which exams are curved?

### Rank 1: course_cs_210_exams.txt#0

Distance: 0.217425; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures — assessment

Two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Do the labs even though they're only 10% — the exams reuse the lab problems.
```

## Retrieval pass 3, Q1

What is the deadline for adding a course, and when does dropping a course result in a W on your transcript?

### Rank 1: admin_add_drop_deadline.txt#0

Distance: 0.141968; producer: `chunker.py::fallback_split`

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

## Retrieval pass 3, Q2

How much does one wash and one dry cost in Aldridge Hall, and what payment method is accepted?

### Rank 1: housing_aldridge_hall_laundry.txt#0

Distance: 0.262994; producer: `chunker.py::fallback_split`

```text
Laundry in Aldridge Hall

Machines take $1.75 wash, $1.50 dry, card only. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

## Retrieval pass 3, Q3

How often does the campus shuttle run on weekdays compared with weekends?

### Rank 1: transit_shuttle.txt#0

Distance: 0.458602; producer: `chunker.py::fallback_split`

```text
The campus shuttle

Runs a loop every 20 minutes from 7am to 11pm on weekdays and every 40 minutes on weekends. The published timetable is optimistic by about five minutes in the morning and accurate the rest of the day.

It's free with a student ID. The stop outside Fenwick Court is the one that gets skipped when the driver is behind, which is worth knowing if you live there.
```

## Retrieval pass 3, Q4

How far in advance can students book group study rooms, and how many two-hour blocks can each person reserve per week?

### Rank 1: study_group_rooms.txt#0

Distance: 0.211249; producer: `chunker.py::fallback_split`

```text
Booking a group study room

Rooms book two weeks ahead through the library site, in two-hour blocks, maximum two blocks per person per week. The limit is per person, so a group of four can chain together eight hours if they coordinate.

Rooms 210 and 211 have whiteboards that actually erase. The others don't and no amount of scrubbing helps.
```

## Retrieval pass 3, Q5

In CS 210, how many midterms and final exams are there, and which exams are curved?

### Rank 1: course_cs_210_exams.txt#0

Distance: 0.217425; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures — assessment

Two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Do the labs even though they're only 10% — the exams reuse the lab problems.
```

## Source chunks, inspected independently of retrieval

### admin_add_drop_deadline.txt#0

Produced by `chunker.py::fallback_split` through `chunker.py::split_documents`.

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

### course_cs_210_exams.txt#0

Produced by `chunker.py::fallback_split` through `chunker.py::split_documents`.

```text
CS 210 Data Structures — assessment

Two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Do the labs even though they're only 10% — the exams reuse the lab problems.
```

### housing_aldridge_hall_laundry.txt#0

Produced by `chunker.py::fallback_split` through `chunker.py::split_documents`.

```text
Laundry in Aldridge Hall

Machines take $1.75 wash, $1.50 dry, card only. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### study_group_rooms.txt#0

Produced by `chunker.py::fallback_split` through `chunker.py::split_documents`.

```text
Booking a group study room

Rooms book two weeks ahead through the library site, in two-hour blocks, maximum two blocks per person per week. The limit is per person, so a group of four can chain together eight hours if they coordinate.

Rooms 210 and 211 have whiteboards that actually erase. The others don't and no amount of scrubbing helps.
```

### transit_shuttle.txt#0

Produced by `chunker.py::fallback_split` through `chunker.py::split_documents`.

```text
The campus shuttle

Runs a loop every 20 minutes from 7am to 11pm on weekdays and every 40 minutes on weekends. The published timetable is optimistic by about five minutes in the morning and accurate the rest of the day.

It's free with a student ID. The stop outside Fenwick Court is the one that gets skipped when the driver is behind, which is worth knowing if you live there.
```

## Gate refusal text

Produced by `gate.py::check` and `gate.py::REFUSAL`; no model calls.

What is the capital of Mongolia?

```text
best distance 0.825 is over the 0.64 cutoff — refusing
I don't have enough information about that.
```

How do I change the oil in a diesel engine?

```text
best distance 0.934 is over the 0.64 cutoff — refusing
I don't have enough information about that.
```

Who won the 1994 World Cup?

```text
best distance 0.886 is over the 0.64 cutoff — refusing
I don't have enough information about that.
```

What is the recommended dosage of ibuprofen for a headache?

```text
best distance 0.844 is over the 0.64 cutoff — refusing
I don't have enough information about that.
```

How do I write a for loop in Rust?

```text
best distance 0.896 is over the 0.64 cutoff — refusing
I don't have enough information about that.
```
