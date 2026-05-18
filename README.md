<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://capsule-render.vercel.app/api?type=rect&color=0:0a0a0a,100:111111&height=4&section=header" width="100%"/>
  <source media="(prefers-color-scheme: light)" srcset="https://capsule-render.vercel.app/api?type=rect&color=0:e8e4ff,100:c4b5fd&height=4&section=header" width="100%"/>
  <img src="https://capsule-render.vercel.app/api?type=rect&color=0:e8e4ff,100:c4b5fd&height=4&section=header" width="100%"/>
</picture>

</div>

<br>

<table width="100%" border="0" cellspacing="0" cellpadding="0">
<tr>
<td width="60%" valign="top">

## Shanmukha Vutikuri

**AI Engineer · Full-Stack Developer · Data Engineer**

```
B.Tech ECE  ·  AWS Certified  ·  Oracle AI Certified
IEEE Published  ·  Andhra Pradesh, India
Open to: AI Eng / Full-Stack / Data Analytics roles
```

I don't have a collection of tutorials I followed.<br>
I have **six production-grade systems** I built, broke, fixed, and shipped.<br>
This GitHub is the evidence.

<br>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Shanmukha_Vutikuri-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shanmukha-vutikuri/)
[![Portfolio](https://img.shields.io/badge/Portfolio-shanmukhworld.netlify.app-8B5CF6?style=flat-square&logo=vercel&logoColor=white)](https://shanmukhworld.netlify.app)
[![Email](https://img.shields.io/badge/Email-vutikurishanmukha9@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:vutikurishanmukha9@gmail.com)
[![Views](https://komarev.com/ghpvc/?username=vutikurishanmukha9&style=flat-square&color=8B5CF6&label=profile+visits)](https://github.com/vutikurishanmukha9)

</td>
<td width="40%" valign="top" align="right">

<img src="https://github-readme-stats.vercel.app/api?username=vutikurishanmukha9&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=true&hide_title=true" width="100%"/>

</td>
</tr>
</table>

---

## The Career Map

> GitHub profiles are progress reports. Here's what mine says about where I am and where I'm going.

```
FOUNDATION                    CURRENT                        NEXT
──────────────────────────────────────────────────────────────────────
ECE → Data Analytics     →   AI + Full-Stack Products   →  Senior Engineer
SQL · Python · Power BI  →   FastAPI · RAG · React 18   →  System Architect
IEEE Research (IoT)      →   GetReport · HeartOut        →  AI Product Owner
EXCELr Internship        →   HiHR · PromptBuddy          →  ML Infra / Platform
AWS Certification        →   Celery · Redis · Docker      →  Cloud-Native Systems
```

**What I'm looking for:** An entry-level role where architecture decisions matter, where I can own things end-to-end, and where "it works on localhost" isn't the finish line.

---

## Six Systems, Six Problems Solved

> Each project below answers a real question. I've written the architecture the way I'd explain it in an interview.

---

### ◈ GetReport — AI Data Analysis Platform

**Live:** [get-report.vercel.app](https://get-report.vercel.app/)

**The problem:** Non-technical teams drown in CSVs. BI tools need expertise. Consultants are expensive.

**The answer:** Upload a CSV or Excel file → a two-stage AI pipeline profiles it, scores data quality column-by-column, gets your approval on cleaning decisions, then generates a publication-ready PDF report with commentary.

**The architecture decisions that actually matter:**

| Decision | What I did | Why it matters |
|---|---|---|
| File validation | Magic number checks (ZIP/OLE2 signatures), not extension checks | Stops spoofed uploads that bypass naive `.endswith(".csv")` guards |
| Data pipeline | Polars with lazy execution | Deferred compute chains — only materializes what's needed, handles files that exceed RAM |
| AI context retrieval | Hybrid RAG: dense vector search + BM25 sparse scoring in parallel | Neither alone handles domain-specific terminology reliably. Both together does. |
| API responsiveness | Celery async workers for analysis + PDF generation | HTTP layer never blocks. Heavy compute runs off-thread. |
| PDF rendering | Dual engine: ReportLab (dev) / WeasyPrint (prod), switchable via `PDF_ENGINE` env var | Dependency-free local dev. Styled CSS-driven output in production. |
| Data quality | Column Confidence Score: Completeness + Consistency + Validity + Stability | Every insight is earned. No black-box outputs. |

**Stack:** `FastAPI` `GPT-4o` `Polars` `Celery` `Redis` `PostgreSQL` `AWS S3` `WeasyPrint` `React` `TypeScript`

---

### ◈ HeartOut — Storytelling Platform

**Repo:** [github.com/vutikurishanmukha9/HeartOut](https://github.com/vutikurishanmukha9/HeartOut) · ![CI](https://github.com/vutikurishanmukha9/HeartOut/actions/workflows/ci.yml/badge.svg)

**The problem:** Social media is performative. People have nowhere honest and anonymous to speak.

**The answer:** An empathy-first platform for anonymous storytelling. No follower counts, no likes — five emotional reaction types, a gravity-based feed, and integrated mental health resources.

**The engineering decisions that show up in interviews:**

| Decision | What I did | Why it matters |
|---|---|---|
| Auth hardening (v3.1) | JWT in `HttpOnly + Secure + SameSite=None` cookies | XSS cannot read these tokens. Zero localStorage exposure to auth state. |
| Feed algorithm | `score = points / (age_hours + 2)^1.8` — single SQL query | Replaced 6 category-specific algorithms with one clean Hacker News formula adapted for emotional content. |
| Logout integrity | Database-backed refresh token blocklist | Tokens can't be replayed after `POST /auth/logout`. Stateless JWTs made stateful where it matters. |
| N+1 elimination | `joinedload()` everywhere + denormalized `support_count` / `comment_count` on Post model | Zero extra queries for counts. Profiled and verified. |
| Migration (v3.0) | Full rewrite: Flask → FastAPI, async SQLAlchemy 2.0, Pydantic v2 | Strict field whitelisting. Async throughout. Not a patch — a ground-up rebuild. |

**Stats:** `541+ automated tests` · `327 pytest (backend)` · `214 Vitest (frontend)` · `70% backend coverage`<br>
**CI/CD:** Backend tests · Frontend build · Flake8 lint · Trivy security scan — on every push

**Stack:** `FastAPI` `SQLAlchemy 2.0` `Pydantic v2` `React 18` `TanStack Query` `PostgreSQL` `Redis` `GitHub Actions`

---

### ◈ AI Royal Rumble — Live Multi-Model Debate Platform

**Repo:** [github.com/vutikurishanmukha9/AI-Royal-Rumble](https://github.com/vutikurishanmukha9/AI-Royal-Rumble)

**The problem:** Comparing AI models is tedious. You copy-paste prompts between interfaces, lose context, and compare vague impressions.

**The answer:** 9 AI models compete live — JAM rounds and Group Discussion rounds. You vote for the winner mid-stream, not after.

**The architectural ideas that are genuinely interesting:**

| Decision | What I did | Why it matters |
|---|---|---|
| Event transport | Redis Streams as event buffer (not process-local queues) | Events replay on reconnect via `Last-Event-ID`. Multiple clients watch the same rumble without fragmentation. |
| Orchestration split | JAM = `asyncio.gather()` (parallel) · GD = sequential | In GD, each model reads the last argument before countering. Two fundamentally different strategies, same pipeline. |
| Transport choice | SSE over WebSocket | Stateless, proxy-friendly, no connection upgrade. `X-Accel-Buffering: no` prevents platform buffering. |
| Vote integrity | IP-hash deduplication + PostgreSQL `UNIQUE(rumble_id, ip_hash)` | Raw IPs never stored. Database-enforced vote uniqueness. |

**Stack:** `FastAPI` `Redis Streams` `SSE` `SQLAlchemy` `Alembic` `React 18` `Framer Motion` `TypeScript` `Docker Compose`

---

### ◈ HiHR — Smart HR Outreach Tool

**Repo:** [github.com/vutikurishanmukha9/HR_Cold_Email](https://github.com/vutikurishanmukha9/HR_Cold_Email)

**The origin:** I was cold-emailing 1,843 HR contacts. Every tool I tried had terrible UX or no tracking. So I built it.

**The security engineering:**

| Feature | Implementation |
|---|---|
| Credential security | AES-256-CBC encryption at rest. Key rotation invalidates credentials, not application state. |
| Send performance | SMTP connection pooling — 5–10× faster than reconnecting per email |
| Tracking | 1×1 GIF pixel embed (open) + link rewriting with redirect proxy (click) — per-recipient timestamps |
| Auth hardening | JWT + 5-attempt lockout = 30-minute block. Access tokens: 15 min. Refresh: 7 days. |
| Rate control | Configurable batch size + inter-batch delay — ISP rate limits respected by design, not accident |

**Stack:** `React 19` `TypeScript` `Node.js` `Express` `Prisma` `PostgreSQL` `Nodemailer` `bcryptjs` `Winston` `Docker`

---

### ◈ PromptBuddy — Multi-LLM Prompt Evaluator

**Repo:** [github.com/vutikurishanmukha9/PromptBuddy](https://github.com/vutikurishanmukha9/PromptBuddy)

**The problem:** I kept manually copy-pasting prompts between GPT, Claude, Gemini, and Cohere to compare outputs. Everyone does this.

**The answer:** One interface. Four models in parallel. Scored on 5 dimensions: Clarity · Specificity · Context · Tone · Completeness. 21 production-ready templates across domains, with a keyword-based suggestion engine that recommends templates from partial input.

**Stack:** `Python` `React` `OpenAI API` `Anthropic API` `Gemini API` `Cohere API`

---

<details>
<summary><b>▸ More projects — click to expand</b></summary>

<br>

**[SHL Assessment Recommender](https://github.com/vutikurishanmukha9)** — FastAPI backend with BM25 + semantic hybrid retrieval. 3-tier LLM failover (Premium → Free → Deterministic fallback). Regex-based guardrails that bypass the LLM entirely for off-topic queries. Deployed on Railway.

**[Team Task Manager](https://github.com/vutikurishanmukha9/project-focus)** — Django REST Framework SaaS with RBAC enforced at three independent layers: permission class, queryset, and serializer. Zero N+1 queries by design. Deployed on Railway + Vercel + Neon PostgreSQL.

**[Ele-Visualize](https://github.com/vutikurishanmukha9/Ele-Visualize)** — 3D chemistry learning workbench with React Three Fiber + MediaPipe hand tracking + WebXR AR. Gesture state machine: open hand = rotate, pinch = zoom, fist = freeze. WebSocket backend on Node.js/Express. Local JSON-backed session store.

**[AI Resume Analyzer](https://github.com/vutikurishanmukha9/Resume_App)** — Sentence Transformers + custom ATS scorer with 5 weighted components (keywords 35%, skills 25%, experience 20%, education 10%, formatting 10%). Negation-aware keyword parsing — handles "NOT required" correctly. 86% semantic similarity accuracy. Fully stateless — zero disk writes, runs on ephemeral filesystems.

**[Global Unicorn Dashboard](https://github.com/vutikurishanmukha9/unicorn-dashboard)** — Power BI analysis of 1,073 unicorn companies. Star schema (4 related tables), Power Query cleaning, DAX measures, dynamic slicers across 6 continents.

**[Jarvis PDF Q&A](https://github.com/vutikurishanmukha9)** — LangChain + FAISS. Multi-provider LLM support (OpenAI, OpenRouter, custom endpoints). HuggingFace Sentence Transformers as local embedding fallback — provider-agnostic by design.

**[Multimodal AI System](https://github.com/vutikurishanmukha9/multimodal_ai_project)** — YOLOv8 + BLIP (Salesforce) for object detection, image captioning, and visual Q&A. Streamlit interface with four themes and session-based image history.

</details>

---

## What I Actually Know

> Not a keyword list. A map of depth.

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DEEP                           SOLID                    LEARNING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Python (async, Pydantic)       TypeScript / JS          Rust
  FastAPI + SQLAlchemy 2.0       Node.js / Express        Kubernetes
  React 18/19 + TanStack Query   Django REST Framework    LangGraph
  RAG (dense + sparse hybrid)    Celery + Redis           Fine-tuning
  PostgreSQL (query opt, N+1)    MongoDB                  Vector DBs (advanced)
  JWT auth (HttpOnly, blocklist) Docker                   eBPF
  AWS (EC2, S3, RDS, Lambda)     GitHub Actions CI/CD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  AI/ML: GPT-4o · Claude · Gemini · Cohere · Sentence Transformers
         FAISS · ChromaDB · YOLOv8 · scikit-learn · Polars · Pandas
  Data:  Power BI · DAX · Star Schema · EDA · SQL (advanced)
  Sec:   AES-256-CBC · RBAC · Rate limiting · Magic number validation
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Credentials & Research

<table width="100%" border="0">
<tr>
<td width="50%" valign="top">

**Certifications**

| Credential | Issuer | Year |
|---|---|---|
| AWS Cloud Practitioner | Amazon Web Services | 2024 |
| Oracle AI Foundations Associate | Oracle | 2025 |
| Data Analysis with Python | IBM | 2025 |
| SQL for Data Science | IBM | 2025 |
| Python for Data Science | IBM | 2025 |

</td>
<td width="50%" valign="top">

**Research**

**Optimizing Energy Efficiency in Smart Buildings Through IoT-Driven Occupancy Sensing**

Published at **IEEE EAIC 2025**, NIT Jalandhar · Paper ID: 482

Sensor fusion pipeline (PIR + CO₂ + thermal) feeding an ML occupancy model. Real-time HVAC scheduling with Raspberry Pi edge inference. The IEEE-reviewed version is in the repo.

</td>
</tr>
</table>

---

## Experience

**Cloud Computing Engineering Intern — EXCELr EdTech** *(Dec 2024 – Apr 2025)*

Deployed and managed AWS infrastructure across EC2, S3, and RDS. Automated provisioning via CloudFormation templates. Built and maintained CI/CD pipelines with Jenkins and GitHub Actions. Worked on data analytics projects using Python, SQL, and Power BI — including regression modeling and EDA on real datasets.

**Cloud Engineering Intern — Brain O Vision** *(Jun 2024 – Aug 2024)*

Configured IAM roles, security policies, and VPC architectures. Automated CloudFormation deployments. Improved system performance and operational efficiency across cloud infrastructure.

---

## GitHub Activity

<div align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=vutikurishanmukha9&theme=tokyonight&hide_border=true" width="49%"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs?username=vutikurishanmukha9&layout=compact&theme=tokyonight&hide_border=true" width="38%"/>

</div>

<div align="center">

[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=vutikurishanmukha9&theme=tokyo-night&hide_border=true&area=true)](https://github.com/vutikurishanmukha9)

</div>

---

## The One Paragraph

I'm a B.Tech ECE graduate who pivoted hard into AI and full-stack engineering — not by taking courses, but by building systems that actually had to work. GetReport has a production RAG pipeline and async Celery workers. HeartOut has 541 tests and a CI pipeline that runs on every push. HiHR has AES-256 encryption and SMTP pooling because I was the first user and I needed it to be reliable. That's the pattern: I find a real problem, I build the right architecture for it, and I don't stop until it's something I'd put in front of a user.

I'm looking for an entry-level role in **AI engineering**, **full-stack development**, or **data analytics** where that approach is valued. India or remote. Available immediately.

---

<div align="center">

**[linkedin.com/in/shanmukha-vutikuri](https://www.linkedin.com/in/shanmukha-vutikuri/)** · **[shanmukhworld.netlify.app](https://shanmukhworld.netlify.app)** · **vutikurishanmukha9@gmail.com**

<br>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://capsule-render.vercel.app/api?type=rect&color=0:111111,100:0a0a0a&height=4&section=footer" width="100%"/>
  <source media="(prefers-color-scheme: light)" srcset="https://capsule-render.vercel.app/api?type=rect&color=0:c4b5fd,100:e8e4ff&height=4&section=footer" width="100%"/>
  <img src="https://capsule-render.vercel.app/api?type=rect&color=0:c4b5fd,100:e8e4ff&height=4&section=footer" width="100%"/>
</picture>

</div>
