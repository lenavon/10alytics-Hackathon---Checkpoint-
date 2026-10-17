# Checkpoint — Lakeside Health Network

**10Alytics Students Hackathon 2026 · Focus Area 2: AI and the Future of Work**

Checkpoint is a clickable prototype of a human-in-the-loop AI tool for **discharge and readmission follow-up** at a fictional two-site hospital network (Lakeside General and Riverside Specialist).

The AI scores each discharged patient's readmission risk, and staff make every decision. The prototype shows how the model's output lands in front of three different roles, and how each role can approve the AI's suggestion, override it or route it to manual review.

> All data in the prototype is illustrative. These are not real patients.

**▶ Live demo:** open `index.html` in a browser, or view it on GitHub Pages once Pages is enabled for this repo (Settings → Pages → Deploy from branch `main`).

---

## The problem

Hospitals need to follow up with recently discharged patients to prevent avoidable readmissions, and follow-up teams have limited time. A risk model can help sort the worklist, but only if clinicians can see *why* a patient was flagged, correct the model when it's wrong and trust that the data underneath is clean.

## The solution: one tool, three roles

The header has a role switch with three views:

| Role | What they see | What they can do |
|---|---|---|
| **Follow-up nurse** | A worklist of discharged patients, each with a risk tier (High / Medium / Low / Unscored), model confidence and the top risk drivers in plain language | Approve the suggested follow-up, or override the tier with a reason and a note. Every action is logged with name and time |
| **Health Records steward** | Probable duplicate patient records across the two sites, with a match score | Confirm or reject merges so the model trains and scores on clean data |
| **Governance committee** | An oversight view of how the AI is being used: overrides, unscored cases and audit history | Monitor where humans disagree with the model and whether it is behaving safely |

### Key design decisions

- **Explainable by default.** Each score shows its drivers, for example "3 ED visits in the last 90 days" or "Lives alone, no confirmed support at home", colour-coded by how much each one contributes.
- **The human has the final say.** Nurses can override any tier. The override reason (such as *Clinical judgement*) and a free-text note are recorded.
- **Knows when not to guess.** When data is missing or model confidence falls below the review threshold, the patient is marked **Unscored** and routed to manual assessment instead of getting a low-confidence tier.
- **Auditability.** Approvals and overrides are timestamped and attributed, which gives the governance committee a trail to review.

## Tech

- A single self-contained `index.html` file: vanilla HTML, CSS and JavaScript with no build step
- IBM Plex Sans and IBM Plex Serif, loaded from Google Fonts
- Mock data is held in memory, so interactions reset when the page reloads

## Run it locally

```bash
git clone https://github.com/lenavon/10alytics-Hackathon---Checkpoint-.git
cd 10alytics-Hackathon---Checkpoint-
open index.html        # macOS. On Windows use: start index.html
```

## Skills demonstrated

Business analysis · stakeholder and role mapping · process design for human-in-the-loop AI · responsible AI and governance · data quality (record matching) · UX prototyping
