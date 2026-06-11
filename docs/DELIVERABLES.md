# Submission Deliverables Checklist

**File naming:** `ALU_Connect_Formative_Assignment1` (adjust group name if required by course).

## Required items

| # | Deliverable | Status | Location / action |
|---|-------------|--------|-------------------|
| 1 | **PDF report (≤ 3 pages)** | Draft ready | Export `docs/ALU_Connect_Formative_Assignment1_REPORT.md` → PDF |
| 2 | **GitHub repository** | Pending push | Create remote; push `main` + 4 member branches |
| 3 | **Demo video (10–15 min)** | To record | Each member presents their section in `docs/DEMO_VIDEO_SCRIPT.md` (~2–3 min each) |
| 4 | **Contribution tracker** | Pending link | Copy [course template](https://docs.google.com/spreadsheets/d/1placeholder) → paste link in `TEAM_CONTRIBUTIONS.md` |

## PDF export options

```bash
# Option A: Open REPORT.md in VS Code / Cursor → Print → Save as PDF (set margins: narrow)

# Option B: Pandoc (if installed)
cd docs
pandoc ALU_Connect_Formative_Assignment1_REPORT.md -o ALU_Connect_Formative_Assignment1.pdf \
  -V geometry:margin=0.75in -V fontsize=10pt
```

## GitHub setup (team of 4)

```bash
# One person creates repo on GitHub, then:
git remote add origin https://github.com/YOUR_ORG/alu_connect.git
git push -u origin main

# Each member pushes their branch with real commits:
git checkout aime && git push -u origin aime
git checkout aurele && git push -u origin aurele
git checkout emmanuel && git push -u origin emmanuel
git checkout shakira && git push -u origin shakira
```

**Important:** Every member needs **visible commits** on their branch. Split remaining work (polish, report, video edits) before final submission.

## Team (current)

| Member | Branch | Focus areas |
|--------|--------|-------------|
| Aime | `aime` | Auth, onboarding, navigation, repo, integration |
| Aurele | `aurele` | Home, Explore, campus selector |
| Emmanuel | `emmanuel` | Events, RSVP, SQLite, database |
| Shakira | `shakira` | Create/edit posts, clubs, splash, animations |

*Mildred is no longer on the team — branch `mildred` can be archived or deleted on remote.*

## Before you submit

- [ ] PDF ≤ 3 pages with citations  
- [ ] Repo link in PDF  
- [ ] Video link in PDF or cover page  
- [ ] Contribution tracker link in PDF and `TEAM_CONTRIBUTIONS.md`  
- [ ] App runs on emulator/device (not web-only)  
- [ ] All 4 members have commits on their branches  
