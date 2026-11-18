# Clean Point - privacy policy

Last updated: 18 November 2026.

Clean Point is a Forge app for Jira Cloud. It runs entirely on Atlassian's Forge platform ("Runs on Atlassian").

**What the app stores.** The 8D records people create: the complaint's part, defect, lots, quantity and
customer name as typed; what is recorded for each discipline (team members and owners as typed, containment and
corrective actions, root causes, evidence, dates); the sign-off state of each discipline with the Atlassian
account ID of the person who signed it off; a short change history with the Atlassian account ID of the person
who made each change. It also stores the plant data (tools, parts, lots, where each lot is) added by an admin -
the built-in sample plant is fictional - the app settings chosen by a site admin, and the result of the last
clock check.

**What it writes in Jira.** Containment and corrective-action work items in the project an admin chooses
(summary, description, labels, due date), linked to the complaint; comments on the complaint when a customer
clock is due soon or breached; the 8D report as an attachment (or a comment) when a user asks for it; and a
small work item property (stage, severity, counts) that makes 8Ds searchable in JQL.

**What it reads.** The complaint work item a user opens or names (summary, description, creation time), and
the projects and work item types the user is allowed to see.

**Rovo.** The 8D lead agent and its skills run in Atlassian Rovo. The app's actions answer Rovo with data from
the app's storage on the same site. The app itself calls no AI service.

**Where.** In Forge storage and in Jira, on Atlassian's infrastructure, inside the customer's site. The app
sends no data to servers outside Atlassian, uses no third-party services and no external analytics. The
developer does not copy customer data into any other system.

**Who sees it.** Users of the same Jira site who can see the complaint work item. Plant data and settings can
be changed only by Jira admins.

**Deletion.** Uninstalling the app removes its Forge storage according to Atlassian's Forge data retention
rules. Jira work items, comments and attachments stay in Jira like any other Jira data and can be deleted there.

**Contact.** [Open an issue](https://github.com/Fuze5k/clean-point/issues) in this repository.
