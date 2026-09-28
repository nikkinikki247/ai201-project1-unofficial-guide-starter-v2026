# The Unofficial Guide

<!-- Replace this line with your name and which corpus you picked. -->

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

     I picked the campus life corpus. My system answers specific questions related to common topics like dining, housing, and transportation. In addition, the system can answer questions about these specific courses: Stat 150, Phys 130, Engl 205, Hist 118, Econ 101, CS 210, CS 340, and Biol 160.

## Chunking Strategy

**Chunk size:**
600
**Overlap:**
100

<!-- What about YOUR documents made you pick these numbers? Short posts and
     long sectioned guides don't want the same chunking, and "800 seemed
     reasonable" earns nothing. Point at something you noticed when you read
     the documents in Milestone 1.

     If you changed your mind partway through, say so and say why. That's worth
     more than pretending you got it right first time.

     Milestone 3. -->

The documents processed were shorter than 800 characters, which allowed each document's text to qualify as a single chunk. To optimize the chunking process, a chunk size slightly greater than the character count of each document was selected. This approach ensures that all relevant information is captured without exceeding the character limit.

## Sample Chunks

<!-- Five chunks, pasted as text. Label each one and name the file it came from
     AND the function that produced it — the grader checks your code against
     what you claim here.

     `python app.py chunks -n 5` prints all three for you. Copy them straight
     across.

     Milestone 3. -->

**Chunk 1** — source: source: admin_add_drop_deadline.txt#0 `— produced by:` chunker.py::fallback_split

```
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

**Chunk 2** — source: course_biol_160_exams.txt#0`— produced by:` chunker.py::fallback_split

```
BIOL 160 Cell Biology — assessment

Four unit tests and a cumulative final. Not curved.

The unit tests come fast, roughly every three weeks; falling behind once is very hard to recover from.
```

**Chunk 3** — source: course_math_220_exams.txt#0`— produced by:` chunker.py::fallback_split

```
MATH 220 Linear Algebra — assessment

Two midterms and a cumulative final. Curved to a b- median.

The problem sets are the course; the lectures make sense afterwards rather than during.
```

**Chunk 4** — source: dining_the_ridgeway_cafe.txt#0 `— produced by:` chunker.py::fallback_split

```
The Ridgeway Café

Second-year here. Wait times: 10 to 15 minutes at 12:30, none after 2:00. The thing worth going for is the only place on campus with real espresso. The thing to know is that seating is tight; about 40 seats for a building of 900.

Hours are 7:00am to 4:00pm weekdays only. Costs declining balance only, no meal swipes.

```

**Chunk 5** — source: housing_morrow_house.txt#0 `— produced by:` chunker.py::fallback_split

```
Morrow House — what it's actually like

Just finished a year in this building. Built 1954, partially renovated 2008. Rooms are singles and doubles, hall bathrooms.

The good: cheapest housing tier by about $900 a year, and the singles are real singles.

The bad: known damp problem on the ground floor; two rooms were taken offline in 2024.

Laundry costs $1.50 wash, $1.25 dry, coin or card. On noise: loud until about 1am on weekends, no enforced quiet hours.
```

## Sample Answer

<!-- One complete question and answer, pasted as text, with the source line
     visible. Milestone 4. -->

**Question:**
What is the deadline to add a course?
**Answer:**

```
You can add a course through the end of the second week (admin_add_drop_deadline.txt).

Sources retrieved: admin_add_drop_deadline.txt, admin_pass_fail_option.txt, advising_registration.txt
```

**My relevance cutoff:**
0.61

I took the averages for each group and calculated the middle number.

<!-- The number you set in config.py, and how you got there.

     You ran five questions your corpus covers and the five in OUT_OF_SCOPE
     that it clearly doesn't, and wrote down the best distance for each. What
     did those two groups look like? Where was the gap? Put the actual numbers
     here — the table below wants all ten rows.

     Milestone 4. -->

| Question                                                                    | In corpus? | Best distance |
| --------------------------------------------------------------------------- | ---------- | ------------- |
| What is the deadline to add a course?                                       | Y          | 0.329         |
| What times is the Ridgeway Café open?                                       | Y          | 0.331         |
| What do students say about the workload for STAT 150 Applied Statistics?    | Y          | 0.301         |
| When does the campus shuttle run?                                           | Y          | 0.402         |
| What do students say about the format of ENGL 205 Writing for the Sciences? | Y          | 0.377         |
| What is the capital of Mongolia?                                            | N          | 0.825         |
| How do I change the oil in a diesel engine?                                 | N          | 0.934         |
| Who won the 1994 World Cup?                                                 | N          | 0.886         |
| What is the recommended dosage of ibuprofen for a headache?                 | N          | 0.844         |
| How do I write a for loop in Rust?                                          | N          | 0.896         |

## How I Used AI

<!-- Two specific moments. For each: what you asked for, what came back, and
     what you changed about it.

     "I asked Claude to write the chunking function from my notes. It ignored
     the overlap, so I added that myself" is the level of detail we're after.
     "I used AI to help me code" is not.

     Milestone 5. -->

**1.**

1. I asked Github Copilot to help me come up with two more test questions. It gave me a few example questions I could use. I changed a question that it gave related to chunking size. I changed the value ranges to match the corpora I chose. I used Gemini to understand more about picking chunk sizes and writing the function. I got back information that told me different contexts and what chunk strategies correlated with them.
   **2.**
   I used AI to diagnose a faulty criterion question and to create a new one to replace the faulty one.

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

<!-- Your five criteria, three runs each. `python run_eval.py --label before`
     runs the questions, puts the OUT_OF_SCOPE ones through the gate, and
     writes it all into results/ for you. Targets come from criteria.md; the
     verdict column is your call.

     Criterion 3 is measured in one deterministic pass rather than three, so
     the same number goes in all three run columns. That's correct, not lazy.

     Milestone 1. -->

| Criterion                              | Target | Run 1 | Run 2 | Run 3 | Verdict |
| -------------------------------------- | ------ | ----- | ----- | ----- | ------- |
| 1. Retrieved chunk contains the answer | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 2. Every answer names a source         | 5 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 3. Gate stops out-of-corpus questions  | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 4. Chunk size is >= 50 and <= 600      | 5 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 5. Overlap size is 100                 | 5 of 5 | N/A   | N/A   | N/A   | N/A     |

<!-- Underneath, paste the REAL output for each criterion from one of your
     runs — the actual text your system produced, not a description of it.
     Name the file and function that produced it. -->

Produced by: `run_eval.py::main`
Retrieval: `store.py::search`, chunks from `chunker.py::split_documents`

1. What is the deadline to add a course?

```
You can add a course through the end of the second week (admin_add_drop_deadline.txt).
```

2. What times is the Ridgeway Café open?

```
The Ridgeway Café is open from 7:00am to 4:00pm, weekdays only.

Source: `dining_the_ridgeway_cafe.txt`
```

3. What do students say about the workload for STAT 150 Applied Statistics?

```
Students say to expect 5 to 6 hours a week outside of class, which is real time rather than optimistic time. They also note that the workload is front-loaded, meaning the first month is heavier than the rest.

Sources: `course_stat_150_workload.txt` and `course_stat_150.txt`
```

4. When does the campus shuttle run?

```
The campus shuttle runs a loop every 20 minutes from 7 am to 11 pm on weekdays, and every 40 minutes on weekends.

Source: transit_shuttle.txt
```

5. What do students say about the format of ENGL 205 Writing for the Sciences?

```
Students say the format of ENGL 205 Writing for the Sciences is a workshop format where you write every week and peers read it, and it is front-loaded with the first month being heavier partly because you are learning the format.

Sources: `course_engl_205.txt` and `course_engl_205_workload.txt`
```

## Verdicts

<!-- MET or MISSED for each of the five, against the target you wrote last
     unit — not a new one. Plus a sentence on how you decided. That sentence
     matters most where it was close.

     If your target said 4 of 5 and your runs came out 4, 3, 4, that's a MISS.
     The target has to hold, not show up occasionally.

     Milestone 2. -->

| #   | Criterion                                                  | Verdict | How I decided                                                                                               |
| --- | ---------------------------------------------------------- | ------- | ----------------------------------------------------------------------------------------------------------- |
| 1   | Retrieved chunk contains the answer                        | MET     | I checked to see if the chunk contained the expects value for each question.                                |
| 2   | Every answer names a source                                | MET     | I checked to see if each output listed at least one source.                                                 |
| 3   | Gate stops out-of-corpus questions                         | MET     | I checked to see if each out-of-corpus question was refused by seeing if the distance was under the cutoff. |
| 4   | Chunk size is >= 50 and <= 600                             | MET     | I counted the characters for each output to check that it was in between the boundaries.                    |
| 5   | Overlap size is 100                                        | N/A     | This couldn't be measured because it requires access to consecutive chunks.                                 |
| 6   | Chunks preserve the full content of the original documents | MET     | I compared the chunks to the content in the original document to see if the ideas were the same.            |

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

     I would tighten the second criterion to include that the sources has to be listed last after the main chunk content rather than in parentheses in the text. Also, I think I would tighten the third criterion (about the chunk size) by reducing the max size because none of my chunks were close to 600 characters.

## The Improvement

**What I changed:**
I changed my chunking strategy by reducing the chunk size to 400 and overlap to 80.
**Why I picked it:**
The previous chunk size was too large.

<!-- Connect it to a specific diagnosis above in one sentence. If you can't,
     you picked a fix because it sounded impressive. -->

### Run Log — After

<!-- Same format, same five criteria, three runs each.
     `python run_eval.py --label after` -->

| Criterion                                                     | Target | Run 1 | Run 2 | Run 3 | Verdict |
| ------------------------------------------------------------- | ------ | ----- | ----- | ----- | ------- |
| 1. Retrieved chunk contains the answer                        | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 2. Every answer names a source                                | 5 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 3. Gate stops out-of-corpus questions                         | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 4. Chunk size is >= 50 and <= 600                             | 5 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 5. Chunks preserve the full content of the original documents | 5 of 5 | 5/5   | 5/5   | 5/5   | MET     |

**Did it help?**

<!-- Say plainly whether it did, and how you know. If it made things worse,
     say that — a change that backfired, honestly reported, earns full credit
     and is more interesting than one that worked. What matters is that you can
     tell.

     Milestone 4. -->

     It didn't change the scores or improve the responses.

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

I would pick a more unique chunking strategy to see how things would've changed like splitting on paragraphs even though the current chunking strategy worked.
