# CDMP Study Agent

An adaptive exam coach for the **CDMP Associate** certification (DAMA International), built as a Claude Code skill.

It generates fresh practice questions one at a time in ExamTopics CDMP DMF style, tracks your performance per knowledge area, and adapts the difficulty based on your gaps — all inside your local Claude Code session.

---

## Why this exists

The CDMP passing score is 70%. Most study resources give you static question banks and generic explanations. This agent does the opposite:

- Questions are **generated fresh** each session — no repetition from a fixed pool
- After a wrong answer, you get a **dense breakdown** of all 5 options with DMBOK references, then an immediate reinforcement question on the same concept
- Performance is **tracked per domain and per concept**, so the agent biases toward your actual weak spots
- Option F ("I don't know this topic") is always present — it triggers a foundation explanation before testing you, instead of just marking you wrong

---

## What's inside

```
cdmp-study-agent/
├── skill/
│   ├── SKILL.md                    # The Claude Code skill — the coach itself
│   └── references/domains/         # Concept maps per domain (12 files)
│       ├── dg.md                   # Data Governance (11%)
│       ├── dq.md                   # Data Quality (11%)
│       ├── dm.md                   # Data Modelling & Design (11%)
│       ├── meta.md                 # Metadata Management (11%)
│       ├── mrd.md                  # Master & Reference Data (10%)
│       ├── dwbi.md                 # Data Warehousing & BI (10%)
│       ├── dii.md                  # Data Integration & Interoperability (6%)
│       ├── dcm.md                  # Document & Content Management (6%)
│       ├── da.md                   # Data Architecture (6%)
│       ├── ds.md                   # Data Security (6%)
│       ├── dso.md                  # Data Storage & Operations (6%)
│       └── bd.md                   # Big Data & Data Science (6%)
└── context/
    ├── study-context-template.md   # Your study profile (fill in, copy to vault)
    ├── tracker-schema.json         # Schema for domain performance tracker
    ├── ledger-schema.json          # Schema for question deduplication
    └── weak-concepts-schema.json   # Schema for concept gap tracking
```

---

## Requirements

- [Claude Code](https://claude.ai/code) — CLI or desktop app
- DMBOK 2nd Edition (recommended, not required to start)

---

## Setup

**1. Clone the repo**

```bash
git clone https://github.com/<your-username>/cdmp-study-agent.git
```

**2. Install the skill**

Copy the `skill/` folder to your Claude Code skills directory:

```bash
# macOS / Linux
cp -r skill ~/.claude/skills/cdmp

# Windows (PowerShell)
Copy-Item -Recurse skill "$env:USERPROFILE\.claude\skills\cdmp"
```

**3. Initialize your vault files**

Choose a folder for your study data (can be an Obsidian vault, any local folder, or a OneDrive/Dropbox path).

Create these files from the schemas in `context/`:

```
your-vault/
├── cdmp-tracker.json        # from context/tracker-schema.json
├── cdmp-ledger.json         # from context/ledger-schema.json
├── cdmp-weak-concepts.json  # from context/weak-concepts-schema.json
├── cdmp-last-session.txt    # create empty file
├── cdmp-study-context.md    # from context/study-context-template.md
└── cdmp-history.json        # create as empty array: []
```

**4. Set your vault path**

In `~/.claude/skills/cdmp/SKILL.md`, update the last line:

```
Vault path: `C:\path\to\your\vault\`
```

**5. Fill in your study context**

Edit `cdmp-study-context.md` in your vault with your baseline score, background, and exam deadline.

**6. Start a session**

In Claude Code, type `/cdmp` or just ask a question about CDMP/DAMA/DMBOK.

---

## Usage

| Command | What happens |
|---|---|
| `/cdmp` | Starts a session — loads your tracker, picks your weakest domain, fires Q1 |
| `/cdmp report` | Full diagnostic: weighted score estimate, per-domain table, gap analysis |
| Answer a letter (A–E) | Get instant feedback + DMBOK reference |
| Answer F | Get a foundation explanation, then a definitional question |
| "stop" / "encerrar" | Writes session summary to `cdmp-last-session.txt` |

---

## How questions work

Every question has 5 options (A–E) plus Option F.

**Option F is not a wrong answer.** It means "I've never seen this concept." The coach responds with a plain-language foundation explanation, then asks a definitional question to build the concept before testing you on it.

For wrong answers, you get a breakdown of all 5 options explaining why each is right or wrong, with the exact DMBOK chapter and concept. Then a reinforcement question on the same topic before moving on.

---

## Performance tracking

The agent maintains a per-domain score table. Every 5 questions you get a scorecard:

```
Domain                        | Score | Weight | Status
Data Governance               | 71%   | 11%    | 🟡
Data Quality                  | 67%   | 11%    | 🔴
Data Modelling & Design       | 100%  | 11%    | 🟢
...
Weighted exam estimate: 67% (target: 70%)
```

The agent prioritizes domains in this order: concepts you answered F → concepts you got wrong 2+ times → domains below 70% → domains not yet attempted.

---

## Domain weights (CDMP Associate exam)

| Domain | Weight |
|---|---|
| Data Governance | 11% |
| Data Quality | 11% |
| Data Modelling & Design | 11% |
| Metadata Management | 11% |
| Master & Reference Data | 10% |
| Data Warehousing & BI | 10% |
| Data Integration & Interoperability | 6% |
| Document & Content Management | 6% |
| Data Architecture | 6% |
| Data Security | 6% |
| Data Storage & Operations | 6% |
| Big Data & Data Science | 6% |

---

## Copyright note

Questions generated by this agent are created by the AI during your session based on DMBOK 2nd Edition concepts. They are not reproduced from any official DAMA exam or question bank. The DMBOK is a trademark of DAMA International — this project is an independent study tool and is not affiliated with or endorsed by DAMA.

---

## License

MIT
