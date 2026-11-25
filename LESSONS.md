# Lessons

## What broke, and what changed

| What broke | What changed |
|---|---|
| Agents said work was done when it wasn't | Done requires the file path and the time it was read back. The Grader opens every output. |
| One chat planned, built and graded itself | Split into a Chief of Staff chat, a Grader and a scheduled build run. The chat that talks can't change a job. |
| Decisions got lost between days | Every decision is a row in Decisions, written the same turn. Each new chat opens the record first. |
| Requests sat in a queue with no time on them | Every request gets a job and a time in the same turn. Finished work is delivered when it's done. |
| Too much of the budget went to running the system | Itemized costs by job, cheaper models for checks, one final senior check instead of several rounds. |
| Mistakes came back after being fixed | The Misses tab names the job or prompt that failed, and the fix goes into that step. |
| Dates were off by a day | Runs wrote UTC dates in the evening. Every row now uses the person's time zone. |

## What an independent review found

After the rebuild, a separate agent that didn't build the system checked two nights of runs against the record. In short:

- The control loop ran both nights, and every output named in the Runs rows existed. The second night was cleaner than the first.
- The weak spots were around the loop: a Jobs tab that had drifted from the live schedule, jobs still running on old wording, and running costs at the weekly cap.
- Jobs that didn't write Runs rows were never graded. Now every job does.
- Two limits disagreed (90% and 95%). One number now lives in one place.

## Research behind each part

- **Measuring:** Anthropic's guidance on evals (20 to 50 real failures, code checks, an "unknown" option) shaped the Grader and the Misses tab. Grading runs instead of run status came from Warp's write-ups.
- **Improving:** testing a change against the current version, one or two changes at a time, and rejecting token increases without a gain shaped the Sunday review. Research showing that adding process doesn't help shaped rule 7.
- **Long work:** Anthropic's long-running harness patterns (a progress file and a startup check) shaped the opening of every session. A strong lead with cheap helpers shaped which models make and which review.
- **Talking to the person:** the AI chief of staff read-back (outcome, done, guardrails, check-ins) shaped the read-back before every task.
