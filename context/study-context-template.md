# CDMP Study Context — Template

> Copy this file to your vault as `cdmp-study-context.md` and fill in your details.
> The coach reads this only when you ask for background context.

---

## Profile

| Attribute | Detail |
|---|---|
| Background | `<your data background — e.g., BI, Data Engineering, Data Governance>` |
| Target certification | CDMP Associate — DAMA |
| Target score | ≥ 70% (passing score) |
| Exam deadline | `<YYYY-MM-DD>` |
| Study material | DMBOK 2nd Edition |

---

## Study Method

```
1. One question at a time — ExamTopics CDMP DMF style
2. Wait for answer
3. If CORRECT → next question
4. If WRONG → dense breakdown with DMBOK reference + reinforcement question on same topic
5. Track performance per knowledge area silently
6. Report gaps when asked
```

**Question style:**
- Exact DMBOK terminology
- Plausible, close distractors
- "NOT true", direct definitions, technical exceptions
- English (exam language)

---

## Baseline Score (official mock exam)

`<X>%` — Gap to passing score: `<70 - X>` points

---

## Identified Gaps

| Knowledge Area | Wrong Questions | Specific Topic |
|---|---|---|
| `<domain>` | `<question IDs>` | `<what confused you>` |

---

## Study Priority

### High (biggest gap + highest exam weight)
1. **Data Quality** — complete cycle, quality dimensions (Ch. 13)
2. **Data Modelling** — key types, recursive relationships, measures additivity (Ch. 5)
3. **DW/BI** — CDC, operational vs DW, incremental release management (Ch. 11)
4. **Metadata** — EDI, metadata standards, repository models (Ch. 12)
5. **Master & Reference Data** — System of Record, Golden Record, Source vs Consuming System (Ch. 10)

### Medium
6. Data Architecture (Ch. 4)
7. Data Integration & Interoperability (Ch. 8)
8. Data Security (Ch. 7)

---

## Domain Weights

| Knowledge Area | Weight | DMBOK 2 Chapter |
|---|---|---|
| Data Governance | 11% | Ch. 3 |
| Data Quality | 11% | Ch. 13 |
| Data Modelling & Design | 11% | Ch. 5 |
| Metadata Management | 11% | Ch. 12 |
| Master & Reference Data | 10% | Ch. 10 |
| Data Warehousing & BI | 10% | Ch. 11 |
| Data Integration & Interoperability | 6% | Ch. 8 |
| Document & Content Management | 6% | Ch. 9 |
| Data Architecture | 6% | Ch. 4 |
| Data Security | 6% | Ch. 7 |
| Data Storage & Operations | 6% | Ch. 6 |
| Big Data & Data Science | 6% | Ch. 14 |

---

## Session Initialization Prompt

```
You are a CDMP certification coach (DAMA).

Full context is in vault/cdmp-study-context.md.

Baseline score: <X>% | Target: 70% | Deadline: <YYYY-MM-DD>
Background: <your background>

Resume from high-priority sequence:
1. Data Quality — Plan→Deploy→Monitor→Act cycle
2. Data Modelling — key types, recursive, measures additivity
3. DW/BI — CDC, operational vs DW
4. Metadata — EDI, repository
5. Master Data — System of Record vs Golden Record

Rules:
- One question at a time, ExamTopics CDMP DMF style (English, DMBOK terminology)
- Wait for answer before revealing the correct one
- If wrong: dense breakdown with DMBOK reference + reinforcement question
- If correct: next question
- Track performance silently; report gaps when asked
```
