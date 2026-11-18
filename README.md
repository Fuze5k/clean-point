# Clean Point

A Forge app for Jira: an 8D lead in Rovo for manufacturing quality teams.

When a customer finds a defective part, the supplier owes an 8D report on the customer's clock (often
containment in 24 hours, root cause in 10 days, closure in 60). Clean Point runs the eight disciplines with the
quality team, inside Jira and Rovo:

- **Start from the complaint.** The panel on the complaint work item reads the part, lots, quantity, customer
  and safety flag, and starts the customer's clocks from the time the customer reported it.
- **Suspect lots, by location.** From the plant's lot records: the last verified-good lot on the same tool,
  every lot made since, and where each one is now (stock, work in progress, in transit, at the customer), plus
  sister parts made on the same tool.
- **The 8D lead agent in Rovo.** Drafts each discipline with you, asks before every write, cites past 8Ds and
  the read-across they never got. It refuses "operator error" as a root cause and asks the next why.
- **Customer rejection check.** The app's own rules review the 8D the way a customer quality engineer would
  (person as root cause, no escape cause, unverified cause, a location not contained, no clean point, actions
  without verification, no read-across, effectiveness not proven). Blocking findings stop the sign-off; only a
  person signs a discipline off.
- **Routing and records.** Containment and corrective actions become linked Jira work items; clock reminders as
  comments; the 8D report attached to the complaint; JQL fields such as `eightDOpen = 1 AND eightDBreached > 0`.

Built for Codegeist 2026. Runs entirely on Atlassian Forge ("Runs on Atlassian"): no external servers, no
outside AI service (the language part is Rovo's).

## Reusable Rovo skills

The four skills the 8D lead uses are `rovo:skill` modules in the app, so any agent on the site can use them.
Their text is in [skills/](skills/):

- [ncr-triage](skills/ncr-triage/SKILL.md) - D0: severity, safety, emergency response, the customer's clocks.
- [containment-plan](skills/containment-plan/SKILL.md) - D3: suspect lots in every location and a clean point.
- [root-cause-analysis](skills/root-cause-analysis/SKILL.md) - D1, D2, D4: team, is / is-not, 5 Whys for the
  occurrence and the escape, verification.
- [corrective-action-plan](skills/corrective-action-plan/SKILL.md) - D5 to D8: actions that fix the cause,
  verification, read-across, PFMEA and control plan, effectiveness.

## Try it

1. Install the app on a Jira Cloud site with Rovo turned on, from the install link in the Devpost entry (site
   admin needed).
2. Jira > Apps > **Clean Point 8D** > **Plant data** > "Try it with sample data": pick a project, **Add sample
   data** (a fictional die-casting plant, three closed 8Ds and one complaint work item).
3. Open the complaint and its **Clean Point 8D** panel (icon under the summary): **Start 8D**.
4. **Work on it with the 8D lead**, or Rovo Chat > agent **8D lead**: "Which lots are suspect and where are they
   now?", "Have we had a defect like this before?", "Would the customer reject this 8D?"

All sample data (Kestrel Components, Arden Motors, people, parts, lots) is fictional.

## Privacy

See [PRIVACY.md](PRIVACY.md). Support: [open an issue](https://github.com/Fuze5k/clean-point/issues).
