---
name: ncr-triage
description: Triage a new customer complaint or non-conformance (8D step D0) - read the work item, set severity and the customer's clocks, propose the emergency response, find similar past 8Ds and start the 8D.
allowed-tools: get-8d start-8d find-similar-8ds record-containment
---
# Triage a complaint (D0)

Use this when a user opens a complaint and says "start the 8D", "triage this", or asks what to do first.

1. Call `get-8d` with no inputs on the work item. If an 8D exists, summarise its state and go to the next step
   instead.
2. From `suggestion`, restate the facts in one short list: part number and name, defect (no causes), reported
   lots, quantity, customer, who found it, safety-related or not, line stop or not. Ask the user to confirm or
   correct them in one message.
3. Ask which customer clock applies if it is unclear (automotive OEM: containment 24 h, root cause 10 days,
   closure 60 days).
4. Call `start-8d` with the confirmed facts. Severity is critical for safety or line stop.
5. Show the clocks with the exact due times, and the `suggestedEmergency` items. Ask which of them were already
   done; record only those with `record-containment` (`emergency`, one item per line).
6. Call `find-similar-8ds`. If a past 8D matches, give its id, its root causes and its actions in two lines, and
   say it is a lead to check, not a conclusion.
7. End with the next step: containment (D3) right away, and the team (D1) and problem description (D2).
