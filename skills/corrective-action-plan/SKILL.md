---
name: corrective-action-plan
description: Plan and close the 8D (D5-D8) - one permanent corrective action per root cause with a measurable verification, implementation evidence, read-across and PFMEA / control plan updates, the effectiveness check and the 8D report.
allowed-tools: get-8d add-corrective-action record-implementation record-prevention record-effectiveness review-8d get-8d-report
---
# Fix, prevent, close (D5-D8)

## D5 corrective actions
1. For each root cause (occurrence and escape) propose one permanent action. Prefer, in order: remove the cause
   (design, tool, process parameter locked), error-proofing, automatic detection, a better check. Training or
   reminders alone are weak: say so and offer a stronger option.
2. Each action needs a verification with a number ("0 cracks in 500 parts, dye-penetrant"), an owner and a due
   date. Ask the user for owner and date; do not invent them.
3. Call `add-corrective-action` per action (`addresses` = occurrence or escape). Offer `createWorkItem: true` to
   open a linked Jira work item.

## D6 implementation
4. When the user reports an action done, call `record-implementation` with the action id and the evidence.

## D7 prevention
5. Read-across: which sister parts, cavities, tools, lines or plants can have the same cause? What was checked and
   found? Include lots from `find-suspect-lots` sister parts if known.
6. Documents: PFMEA (occurrence and detection ratings), control plan (the new check), work instructions, with
   revisions. Call `record-prevention`.

## D8 effectiveness and closure
7. The effectiveness check comes after the actions have run (the clock shows when). Record it with
   `record-effectiveness` (pass or fail, with the evidence). A fail means back to D4.
8. Call `review-8d`. If it is ready, call `get-8d-report` and give the user a short summary; the full report is
   in the panel (8D report). Tell the user to sign D8 off in the panel.
