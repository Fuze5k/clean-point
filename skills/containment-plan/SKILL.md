---
name: containment-plan
description: Plan and record 8D containment (D3) - find every suspect lot since the last lot verified good, by location (stock, work in progress, in transit, at the customer), propose quarantine and sort actions, sister-part lots and a clean point.
allowed-tools: get-8d find-suspect-lots record-containment
---
# Contain the defect (D3)

Use this as soon as an 8D is started, and whenever the user asks which parts are suspect.

1. Call `get-8d` (no inputs on the work item) to see the containment clock and what is already recorded, then
   call `find-suspect-lots` (no inputs on the work item).
2. Show the suspect window: the last known good lot and how it was verified, then every suspect lot grouped by
   location with quantities and the total. Name the tool and its shot count.
3. Propose one containment action per location that holds suspect parts:
   - finished stock and work in progress: quarantine (block in the system and tag), then sort 100%;
   - in transit: stop the shipment or sort on arrival, name the shipment number;
   - at the customer: sort at the customer's site (own staff or a third-party sorter), name the lots.
   Use the test that finds the defect (for cracks: dye-penetrant, not visual).
4. If `sisterLots` is not empty, say these lots of other parts came from the same tool and may have the same cause.
   Ask whether to contain them too; they belong in the read-across (D7) in any case.
5. Propose a clean point: the first lot made after a verified fix (or after 100% inspection starts) and how
   certified parts are marked.
6. Ask the user to confirm, then call `record-containment` with `actions` (one per line), `covered` (the
   locations), and `cleanPoint`. Record sort results (`sortedQty`, `rejectsFound`) when the user has them.
7. Remind the user of the containment clock and that the panel can open one Jira work item per containment
   action. Tell them to sign D3 off in the panel once no blocking finding is left.
