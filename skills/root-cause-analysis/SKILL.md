---
name: root-cause-analysis
description: Lead the 8D team through the problem description (D2, is / is-not) and 5 Whys for both root causes (D4) - why the defect was made (occurrence) and why it was not caught (escape) - and reject root causes that blame people.
allowed-tools: get-8d find-similar-8ds record-problem record-root-cause review-8d
---
# Find the root causes (D1, D2, D4)

## D1 team and D2 problem
0. Call `get-8d` (no inputs on the work item) to see what is already recorded and the root-cause clock.
1. Ask for the team (name and role, at least quality, production and engineering or maintenance) and a champion.
2. Build the problem description with facts only: what (measured), where found, when it started (lots, dates),
   how many of how many, and is / is-not (where it is NOT seen: other cavity, other tool, other shift, older lots).
   Is-not narrows the cause; ask for it explicitly.
3. Confirm, then call `record-problem`.

## D4 root causes
1. Call `find-similar-8ds`. Past root causes are leads: ask the team to check them (for example a die's fillet
   radius and shot count), never assume them.
2. Occurrence: ask "why?" from the symptom down, one step at a time, at least three steps, until the answer is a
   process, tool, method or material weakness that can be switched on and off.
3. Escape: ask why inspection or testing did not stop the defect: was there a check for this feature, at what
   frequency, with what method, and could that method see the defect?
4. If an answer blames a person (operator error, lack of training, not following the instruction), do not record
   it as the root cause. Ask why the process allowed it.
5. Ask how the cause was verified (switch it on and off, measurement, data). Set `verified` only when the user
   confirms the proof.
6. Call `record-root-cause` once for `occurrence` and once for `escape`, with `whys` one per line. The `evidence` is
   what the user reported (measurements, tests, records they named), in their words; never add document
   revisions or records they did not mention.
7. Call `review-8d` and report the D4 findings. When none is blocking, tell the user to sign D4 off in the panel.
