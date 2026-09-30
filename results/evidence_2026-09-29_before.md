# Supplemental retrieval and chunk evidence

Captured: 2026-09-29T22:16:00

Captured separately after the saved evaluation; no generation calls or pipeline changes.
Corpus: campus_life; top-k: 5; cutoff: 0.64; embedding: all-MiniLM-L6-v2.

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

### Rank 2: admin_withdrawal_deadline.txt#0

Distance: 0.439761; producer: `chunker.py::fallback_split`

```text
On the withdrawal deadline

Withdrawal is a different thing from dropping and has a different date. Dropping ends at week six. Withdrawal runs to week ten, requires an adviser signature, and puts a W on the transcript that doesn't affect GPA. The two dates appear on different pages of the registrar's site and this catches people every year.
```

### Rank 3: admin_pass_fail_option.txt#0

Distance: 0.475467; producer: `chunker.py::fallback_split`

```text
On the pass/fail option

Any course outside your major can be taken pass/fail, and — the part nobody mentions — you can declare it as late as week eight, after you've seen your midterm. A pass needs a C- or better. Two per year, maximum eight across a degree.
```

### Rank 4: admin_grade_appeals.txt#0

Distance: 0.515115; producer: `chunker.py::fallback_split`

```text
On the grade appeals

A grade appeal starts with the instructor and has to be raised within fifteen days of the grade posting. Only after that does it go to the department. Skipping the instructor step gets the appeal returned, which wastes most of the fifteen days.
```

### Rank 5: admin_transcript_requests.txt#0

Distance: 0.520325; producer: `chunker.py::fallback_split`

```text
On the transcript requests

Official transcripts cost $8 and take three business days electronically, or ten by post. Unofficial ones are free and instant from the student portal, and are accepted by most employers and by every graduate programme at the application stage.
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

### Rank 2: housing_innisfree_hall_laundry.txt#0

Distance: 0.436394; producer: `chunker.py::fallback_split`

```text
Laundry in Innisfree Hall

Machines take $1.75 wash, $1.75 dry, app-based. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 3: housing_calder_annexe_laundry.txt#0

Distance: 0.441160; producer: `chunker.py::fallback_split`

```text
Laundry in Calder Annexe

Machines take $2.00 wash, $1.75 dry, app-based. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 4: housing_old_brewhouse_laundry.txt#0

Distance: 0.469109; producer: `chunker.py::fallback_split`

```text
Laundry in Old Brewhouse

Machines take $1.50 wash, $1.50 dry, coin only, and the machines are old. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 5: housing_aldridge_hall.txt#0

Distance: 0.472427; producer: `chunker.py::fallback_split`

```text
Aldridge Hall — what it's actually like

I lived here my sophomore year. Built 1968, renovated 2019. Rooms are doubles with a shared bathroom per floor.

The good: closest building to the science quad, four minutes to a 9am lab.

The bad: the elevator is out roughly one week per semester.

Laundry costs $1.75 wash, $1.50 dry, card only. On noise: quiet floors on 3 and 4 are genuinely enforced.
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

### Rank 2: course_stat_150_workload.txt#0

Distance: 0.559362; producer: `chunker.py::fallback_split`

```text
Workload for STAT 150 Applied Statistics

People keep asking so: 5 to 6 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

### Rank 3: course_cs_210_workload.txt#0

Distance: 0.608923; producer: `chunker.py::fallback_split`

```text
Workload for CS 210 Data Structures

People keep asking so: 8 to 10 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

### Rank 4: dining_verrill_street_grill.txt#0

Distance: 0.609416; producer: `chunker.py::fallback_split`

```text
Verrill Street Grill

I'm a junior and I've done this twice now. Wait times: up to 30 minutes on Friday evenings, otherwise under 10. The thing worth going for is the burger, which is the only late-night hot food on campus. The thing to know is that one register, so the queue is a single line no matter how busy.

Hours are 11:00am to 1:00am daily during term. Costs declining balance, or cash after 11:00pm.
```

### Rank 5: course_econ_101_workload.txt#0

Distance: 0.609953; producer: `chunker.py::fallback_split`

```text
Workload for ECON 101 Introduction to Economics

People keep asking so: 4 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
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

### Rank 2: course_cs_340.txt#0

Distance: 0.494900; producer: `chunker.py::fallback_split`

```text
CS 340 Databases

I'm a junior and I've done this twice now. Format is lecture twice a week plus a project that runs the whole term. Assessment: one midterm and a final, both open-book. Lightly curved, usually two or three points.

Expect 6 hours a week early, 15 in the last three weeks when the project lands.

The one piece of advice: start the term project in week three, not week eight; everyone learns this the hard way.
```

### Rank 3: money_textbooks.txt#0

Distance: 0.535110; producer: `chunker.py::fallback_split`

```text
Textbooks without paying full price

The library holds one copy of most required texts on two-hour reserve. For courses where the text is used constantly that isn't enough, but for the reading-light courses it's genuinely all you need.

The campus store price-matches, which is not advertised anywhere and you have to ask at the counter with the other listing on your phone.
```

### Rank 4: course_cs_210.txt#0

Distance: 0.542952; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures

I'm a junior and I've done this twice now. Format is lecture with weekly labs; slides go up after class, not before. Assessment: two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Expect 8 to 10 hours a week outside class.

The one piece of advice: do the labs even though they're only 10% — the exams reuse the lab problems.
```

### Rank 5: money_jobs.txt#0

Distance: 0.544200; producer: `chunker.py::fallback_split`

```text
On-campus work

Library and dining jobs post in the first week of each semester and go fast. Pay is the same across departments — the difference is whether you can study during the shift. Library desk: usually yes. Dining: no.

Maximum is 20 hours a week during term. Most people find 10 to 12 is the point where it stops affecting coursework.
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

### Rank 2: course_cs_210.txt#0

Distance: 0.375881; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures

I'm a junior and I've done this twice now. Format is lecture with weekly labs; slides go up after class, not before. Assessment: two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Expect 8 to 10 hours a week outside class.

The one piece of advice: do the labs even though they're only 10% — the exams reuse the lab problems.
```

### Rank 3: course_cs_340_exams.txt#0

Distance: 0.393346; producer: `chunker.py::fallback_split`

```text
CS 340 Databases — assessment

One midterm and a final, both open-book. Lightly curved, usually two or three points.

Start the term project in week three, not week eight; everyone learns this the hard way.
```

### Rank 4: course_engl_205_exams.txt#0

Distance: 0.476696; producer: `chunker.py::fallback_split`

```text
ENGL 205 Writing for the Sciences — assessment

No exams; a portfolio of six revised pieces. Not curved.

The portfolio is graded on revision, so keep your drafts — you're marked on the distance travelled.
```

### Rank 5: course_math_220_exams.txt#0

Distance: 0.484556; producer: `chunker.py::fallback_split`

```text
MATH 220 Linear Algebra — assessment

Two midterms and a cumulative final. Curved to a b- median.

The problem sets are the course; the lectures make sense afterwards rather than during.
```

## Retrieval pass 2, Q1

What is the deadline for adding a course, and when does dropping a course result in a W on your transcript?

### Rank 1: admin_add_drop_deadline.txt#0

Distance: 0.141968; producer: `chunker.py::fallback_split`

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

### Rank 2: admin_withdrawal_deadline.txt#0

Distance: 0.439761; producer: `chunker.py::fallback_split`

```text
On the withdrawal deadline

Withdrawal is a different thing from dropping and has a different date. Dropping ends at week six. Withdrawal runs to week ten, requires an adviser signature, and puts a W on the transcript that doesn't affect GPA. The two dates appear on different pages of the registrar's site and this catches people every year.
```

### Rank 3: admin_pass_fail_option.txt#0

Distance: 0.475467; producer: `chunker.py::fallback_split`

```text
On the pass/fail option

Any course outside your major can be taken pass/fail, and — the part nobody mentions — you can declare it as late as week eight, after you've seen your midterm. A pass needs a C- or better. Two per year, maximum eight across a degree.
```

### Rank 4: admin_grade_appeals.txt#0

Distance: 0.515115; producer: `chunker.py::fallback_split`

```text
On the grade appeals

A grade appeal starts with the instructor and has to be raised within fifteen days of the grade posting. Only after that does it go to the department. Skipping the instructor step gets the appeal returned, which wastes most of the fifteen days.
```

### Rank 5: admin_transcript_requests.txt#0

Distance: 0.520325; producer: `chunker.py::fallback_split`

```text
On the transcript requests

Official transcripts cost $8 and take three business days electronically, or ten by post. Unofficial ones are free and instant from the student portal, and are accepted by most employers and by every graduate programme at the application stage.
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

### Rank 2: housing_innisfree_hall_laundry.txt#0

Distance: 0.436394; producer: `chunker.py::fallback_split`

```text
Laundry in Innisfree Hall

Machines take $1.75 wash, $1.75 dry, app-based. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 3: housing_calder_annexe_laundry.txt#0

Distance: 0.441160; producer: `chunker.py::fallback_split`

```text
Laundry in Calder Annexe

Machines take $2.00 wash, $1.75 dry, app-based. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 4: housing_old_brewhouse_laundry.txt#0

Distance: 0.469109; producer: `chunker.py::fallback_split`

```text
Laundry in Old Brewhouse

Machines take $1.50 wash, $1.50 dry, coin only, and the machines are old. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 5: housing_aldridge_hall.txt#0

Distance: 0.472427; producer: `chunker.py::fallback_split`

```text
Aldridge Hall — what it's actually like

I lived here my sophomore year. Built 1968, renovated 2019. Rooms are doubles with a shared bathroom per floor.

The good: closest building to the science quad, four minutes to a 9am lab.

The bad: the elevator is out roughly one week per semester.

Laundry costs $1.75 wash, $1.50 dry, card only. On noise: quiet floors on 3 and 4 are genuinely enforced.
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

### Rank 2: course_stat_150_workload.txt#0

Distance: 0.559362; producer: `chunker.py::fallback_split`

```text
Workload for STAT 150 Applied Statistics

People keep asking so: 5 to 6 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

### Rank 3: course_cs_210_workload.txt#0

Distance: 0.608923; producer: `chunker.py::fallback_split`

```text
Workload for CS 210 Data Structures

People keep asking so: 8 to 10 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

### Rank 4: dining_verrill_street_grill.txt#0

Distance: 0.609416; producer: `chunker.py::fallback_split`

```text
Verrill Street Grill

I'm a junior and I've done this twice now. Wait times: up to 30 minutes on Friday evenings, otherwise under 10. The thing worth going for is the burger, which is the only late-night hot food on campus. The thing to know is that one register, so the queue is a single line no matter how busy.

Hours are 11:00am to 1:00am daily during term. Costs declining balance, or cash after 11:00pm.
```

### Rank 5: course_econ_101_workload.txt#0

Distance: 0.609953; producer: `chunker.py::fallback_split`

```text
Workload for ECON 101 Introduction to Economics

People keep asking so: 4 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
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

### Rank 2: course_cs_340.txt#0

Distance: 0.494900; producer: `chunker.py::fallback_split`

```text
CS 340 Databases

I'm a junior and I've done this twice now. Format is lecture twice a week plus a project that runs the whole term. Assessment: one midterm and a final, both open-book. Lightly curved, usually two or three points.

Expect 6 hours a week early, 15 in the last three weeks when the project lands.

The one piece of advice: start the term project in week three, not week eight; everyone learns this the hard way.
```

### Rank 3: money_textbooks.txt#0

Distance: 0.535110; producer: `chunker.py::fallback_split`

```text
Textbooks without paying full price

The library holds one copy of most required texts on two-hour reserve. For courses where the text is used constantly that isn't enough, but for the reading-light courses it's genuinely all you need.

The campus store price-matches, which is not advertised anywhere and you have to ask at the counter with the other listing on your phone.
```

### Rank 4: course_cs_210.txt#0

Distance: 0.542952; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures

I'm a junior and I've done this twice now. Format is lecture with weekly labs; slides go up after class, not before. Assessment: two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Expect 8 to 10 hours a week outside class.

The one piece of advice: do the labs even though they're only 10% — the exams reuse the lab problems.
```

### Rank 5: money_jobs.txt#0

Distance: 0.544200; producer: `chunker.py::fallback_split`

```text
On-campus work

Library and dining jobs post in the first week of each semester and go fast. Pay is the same across departments — the difference is whether you can study during the shift. Library desk: usually yes. Dining: no.

Maximum is 20 hours a week during term. Most people find 10 to 12 is the point where it stops affecting coursework.
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

### Rank 2: course_cs_210.txt#0

Distance: 0.375881; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures

I'm a junior and I've done this twice now. Format is lecture with weekly labs; slides go up after class, not before. Assessment: two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Expect 8 to 10 hours a week outside class.

The one piece of advice: do the labs even though they're only 10% — the exams reuse the lab problems.
```

### Rank 3: course_cs_340_exams.txt#0

Distance: 0.393346; producer: `chunker.py::fallback_split`

```text
CS 340 Databases — assessment

One midterm and a final, both open-book. Lightly curved, usually two or three points.

Start the term project in week three, not week eight; everyone learns this the hard way.
```

### Rank 4: course_engl_205_exams.txt#0

Distance: 0.476696; producer: `chunker.py::fallback_split`

```text
ENGL 205 Writing for the Sciences — assessment

No exams; a portfolio of six revised pieces. Not curved.

The portfolio is graded on revision, so keep your drafts — you're marked on the distance travelled.
```

### Rank 5: course_math_220_exams.txt#0

Distance: 0.484556; producer: `chunker.py::fallback_split`

```text
MATH 220 Linear Algebra — assessment

Two midterms and a cumulative final. Curved to a b- median.

The problem sets are the course; the lectures make sense afterwards rather than during.
```

## Retrieval pass 3, Q1

What is the deadline for adding a course, and when does dropping a course result in a W on your transcript?

### Rank 1: admin_add_drop_deadline.txt#0

Distance: 0.141968; producer: `chunker.py::fallback_split`

```text
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

### Rank 2: admin_withdrawal_deadline.txt#0

Distance: 0.439761; producer: `chunker.py::fallback_split`

```text
On the withdrawal deadline

Withdrawal is a different thing from dropping and has a different date. Dropping ends at week six. Withdrawal runs to week ten, requires an adviser signature, and puts a W on the transcript that doesn't affect GPA. The two dates appear on different pages of the registrar's site and this catches people every year.
```

### Rank 3: admin_pass_fail_option.txt#0

Distance: 0.475467; producer: `chunker.py::fallback_split`

```text
On the pass/fail option

Any course outside your major can be taken pass/fail, and — the part nobody mentions — you can declare it as late as week eight, after you've seen your midterm. A pass needs a C- or better. Two per year, maximum eight across a degree.
```

### Rank 4: admin_grade_appeals.txt#0

Distance: 0.515115; producer: `chunker.py::fallback_split`

```text
On the grade appeals

A grade appeal starts with the instructor and has to be raised within fifteen days of the grade posting. Only after that does it go to the department. Skipping the instructor step gets the appeal returned, which wastes most of the fifteen days.
```

### Rank 5: admin_transcript_requests.txt#0

Distance: 0.520325; producer: `chunker.py::fallback_split`

```text
On the transcript requests

Official transcripts cost $8 and take three business days electronically, or ten by post. Unofficial ones are free and instant from the student portal, and are accepted by most employers and by every graduate programme at the application stage.
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

### Rank 2: housing_innisfree_hall_laundry.txt#0

Distance: 0.436394; producer: `chunker.py::fallback_split`

```text
Laundry in Innisfree Hall

Machines take $1.75 wash, $1.75 dry, app-based. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 3: housing_calder_annexe_laundry.txt#0

Distance: 0.441160; producer: `chunker.py::fallback_split`

```text
Laundry in Calder Annexe

Machines take $2.00 wash, $1.75 dry, app-based. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 4: housing_old_brewhouse_laundry.txt#0

Distance: 0.469109; producer: `chunker.py::fallback_split`

```text
Laundry in Old Brewhouse

Machines take $1.50 wash, $1.50 dry, coin only, and the machines are old. There are eight washers and six dryers for the building, which is the wrong ratio and means the dryers back up on Sunday evenings.

Best time to do laundry here is Tuesday or Wednesday morning. Sunday after 6pm you will wait.
```

### Rank 5: housing_aldridge_hall.txt#0

Distance: 0.472427; producer: `chunker.py::fallback_split`

```text
Aldridge Hall — what it's actually like

I lived here my sophomore year. Built 1968, renovated 2019. Rooms are doubles with a shared bathroom per floor.

The good: closest building to the science quad, four minutes to a 9am lab.

The bad: the elevator is out roughly one week per semester.

Laundry costs $1.75 wash, $1.50 dry, card only. On noise: quiet floors on 3 and 4 are genuinely enforced.
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

### Rank 2: course_stat_150_workload.txt#0

Distance: 0.559362; producer: `chunker.py::fallback_split`

```text
Workload for STAT 150 Applied Statistics

People keep asking so: 5 to 6 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

### Rank 3: course_cs_210_workload.txt#0

Distance: 0.608923; producer: `chunker.py::fallback_split`

```text
Workload for CS 210 Data Structures

People keep asking so: 8 to 10 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

### Rank 4: dining_verrill_street_grill.txt#0

Distance: 0.609416; producer: `chunker.py::fallback_split`

```text
Verrill Street Grill

I'm a junior and I've done this twice now. Wait times: up to 30 minutes on Friday evenings, otherwise under 10. The thing worth going for is the burger, which is the only late-night hot food on campus. The thing to know is that one register, so the queue is a single line no matter how busy.

Hours are 11:00am to 1:00am daily during term. Costs declining balance, or cash after 11:00pm.
```

### Rank 5: course_econ_101_workload.txt#0

Distance: 0.609953; producer: `chunker.py::fallback_split`

```text
Workload for ECON 101 Introduction to Economics

People keep asking so: 4 hours a week outside class. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
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

### Rank 2: course_cs_340.txt#0

Distance: 0.494900; producer: `chunker.py::fallback_split`

```text
CS 340 Databases

I'm a junior and I've done this twice now. Format is lecture twice a week plus a project that runs the whole term. Assessment: one midterm and a final, both open-book. Lightly curved, usually two or three points.

Expect 6 hours a week early, 15 in the last three weeks when the project lands.

The one piece of advice: start the term project in week three, not week eight; everyone learns this the hard way.
```

### Rank 3: money_textbooks.txt#0

Distance: 0.535110; producer: `chunker.py::fallback_split`

```text
Textbooks without paying full price

The library holds one copy of most required texts on two-hour reserve. For courses where the text is used constantly that isn't enough, but for the reading-light courses it's genuinely all you need.

The campus store price-matches, which is not advertised anywhere and you have to ask at the counter with the other listing on your phone.
```

### Rank 4: course_cs_210.txt#0

Distance: 0.542952; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures

I'm a junior and I've done this twice now. Format is lecture with weekly labs; slides go up after class, not before. Assessment: two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Expect 8 to 10 hours a week outside class.

The one piece of advice: do the labs even though they're only 10% — the exams reuse the lab problems.
```

### Rank 5: money_jobs.txt#0

Distance: 0.544200; producer: `chunker.py::fallback_split`

```text
On-campus work

Library and dining jobs post in the first week of each semester and go fast. Pay is the same across departments — the difference is whether you can study during the shift. Library desk: usually yes. Dining: no.

Maximum is 20 hours a week during term. Most people find 10 to 12 is the point where it stops affecting coursework.
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

### Rank 2: course_cs_210.txt#0

Distance: 0.375881; producer: `chunker.py::fallback_split`

```text
CS 210 Data Structures

I'm a junior and I've done this twice now. Format is lecture with weekly labs; slides go up after class, not before. Assessment: two midterms and a final, all drawn from lecture material rather than the textbook. Midterms are curved, the final is not.

Expect 8 to 10 hours a week outside class.

The one piece of advice: do the labs even though they're only 10% — the exams reuse the lab problems.
```

### Rank 3: course_cs_340_exams.txt#0

Distance: 0.393346; producer: `chunker.py::fallback_split`

```text
CS 340 Databases — assessment

One midterm and a final, both open-book. Lightly curved, usually two or three points.

Start the term project in week three, not week eight; everyone learns this the hard way.
```

### Rank 4: course_engl_205_exams.txt#0

Distance: 0.476696; producer: `chunker.py::fallback_split`

```text
ENGL 205 Writing for the Sciences — assessment

No exams; a portfolio of six revised pieces. Not curved.

The portfolio is graded on revision, so keep your drafts — you're marked on the distance travelled.
```

### Rank 5: course_math_220_exams.txt#0

Distance: 0.484556; producer: `chunker.py::fallback_split`

```text
MATH 220 Linear Algebra — assessment

Two midterms and a cumulative final. Curved to a b- median.

The problem sets are the course; the lectures make sense afterwards rather than during.
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
