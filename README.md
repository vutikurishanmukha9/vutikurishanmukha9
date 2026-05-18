<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:000000,30:0a0a0a,70:111111,100:1a1a1a&height=140&section=header&text=Shanmukha%20Vutikuri&fontSize=38&fontColor=ffffff&fontAlignY=55&desc=AI%20Engineer%20%C2%B7%20Full-Stack%20Developer%20%C2%B7%20Product%20Builder&descSize=14&descAlignY=78&animation=fadeIn" width="100%"/>

</div>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230A66C2.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shanmukha-vutikuri/)
[![Portfolio](https://img.shields.io/badge/Portfolio-%23000000.svg?style=for-the-badge&logo=vercel&logoColor=white)](https://shanmukhworld.netlify.app)
[![Email](https://img.shields.io/badge/Gmail-%23EA4335.svg?style=for-the-badge&logo=gmail&logoColor=white)](mailto:vutikurishanmukha9@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-%23181717.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/vutikurishanmukha9)

</div>

---

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║                                                                                  ║
║   "I don't build side projects. I build products that solve real problems        ║
║    — with real architecture, real tests, and real deployment pipelines."         ║
║                                                                                  ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## `$ whoami`

```yaml
name         : Shanmukha Vutikuri
role         : AI Engineer · Full-Stack Developer · Data Analyst
location     : Andhra Pradesh, India
status       : Actively seeking entry-level roles
education    : B.Tech ECE — Aditya Engineering College (2021–2025)
publication  : IEEE EAIC 2025 — IoT-Driven Occupancy Sensing for Smart Buildings
certifications:
  - AWS Certified Cloud Practitioner (2024)
  - Oracle AI Foundations Associate (2025)
  - IBM: Data Analysis with Python · SQL for Data Science · Python for Data Science
```

---

## `$ cat /career/philosophy`

I'm the kind of engineer who reads the architecture before writing the first line.  
Who writes tests before calling something done.  
Who deploys things, breaks them, fixes them, and ships again.

My GitHub is not a portfolio of experiments — it's a record of products I've carried from idea to production. Every repo here has a README written for the person who has to maintain it, not the one who built it.

---

## `$ ls -la /projects` — Production-Grade Work

---

### 📊 [GetReport](https://get-report.vercel.app/) — AI Data Analysis Platform
> **Turn raw CSV/Excel into publication-ready PDF reports with AI commentary.**

```
Problem  → Non-technical users drown in data. Analysis tools require expertise.
Solution → Two-stage pipeline with user-approved cleaning decisions before analysis runs.
Why it matters → The output feels earned, not just generated.
```

**Architecture that matters:**
- **Hybrid RAG Engine** — Dense vector search + BM25 sparse scoring in parallel. Not just embeddings, not just keyword matching. Both.
- **Async Celery Workers** — Heavy compute (analysis + PDF) runs off-thread. API stays non-blocking.
- **Security-first file handling** — Magic number validation (ZIP/OLE2 signatures), not just extension checking. Stops spoofed uploads cold.
- **Dual PDF Engine** — ReportLab in dev (no system deps), WeasyPrint in prod (styled output). Switchable via `PDF_ENGINE` env var.
- **Column Confidence Scores** — Every column graded on Completeness, Consistency, Validity, Stability before a single insight is generated.

```
Stack: FastAPI · GPT-4o · Polars (lazy execution) · Celery · Redis · PostgreSQL · AWS S3 · WeasyPrint · React + TypeScript
```

[![Live Demo](https://img.shields.io/badge/Live%20Demo-get--report.vercel.app-black?style=flat-square&logo=vercel)](https://get-report.vercel.app/)

---

### 💬 [HeartOut](https://github.com/vutikurishanmukha9/HeartOut) — Storytelling Platform
> **Anonymous, empathy-first space for authentic personal stories.**

```
Problem  → Social media is performative. People have nowhere safe to be honest.
Solution → Anonymous storytelling with empathetic reactions — no likes, no followers.
Scale    → 541+ automated tests. CI/CD on every push. Real production hardening.
```

**Engineering decisions that show up in interviews:**
- **HttpOnly Cookie Auth (v3.1)** — JWT stored in `HttpOnly` + `Secure` + `SameSite=None` cookies. XSS cannot touch these tokens. No localStorage anywhere near auth.
- **Gravity-based Feed Ranking** — Single SQL query using `score = points / (age_hours + 2)^1.8`. Hacker News algorithm adapted for emotional content. Replaced 6 category-specific algorithms with one clean formula.
- **Persistent Token Blocklist** — Database-backed logout. Refresh tokens can't be replayed after `POST /auth/logout`.
- **N+1 Eliminated** — `joinedload()` everywhere. Denormalized `support_count` and `comment_count` on the Post model. Zero extra queries for counts.
- **FastAPI Migration (v3.0)** — Full rewrite from Flask. Async SQLAlchemy 2.0 throughout. Pydantic v2 for strict field whitelisting.

```
Stack: FastAPI · SQLAlchemy 2.0 · Pydantic v2 · React 18 · TanStack Query · PostgreSQL · Redis
Tests: 327 pytest (backend) + 214 Vitest (frontend) = 541+ total · 70% backend coverage
CI/CD: GitHub Actions — backend tests · frontend build · Flake8 lint · Trivy security scan
```

[![Tests](https://img.shields.io/badge/Tests-541%2B-brightgreen?style=flat-square)](https://github.com/vutikurishanmukha9/HeartOut)
[![CI](https://github.com/vutikurishanmukha9/HeartOut/actions/workflows/ci.yml/badge.svg)](https://github.com/vutikurishanmukha9/HeartOut/actions/workflows/ci.yml)

---

### ⚔️ [AI Royal Rumble](https://github.com/vutikurishanmukha9/AI-Royal-Rumble) — Live AI Debate Platform
> **9 AI models compete in JAM and Group Discussion rounds. You vote for the winner.**

```
Problem  → AI model comparison is tedious, static, and boring.
Solution → Real-time broadcast format. Models compete. Humans judge.
Insight  → Voting opens during the stream — not after. One decision. Completely changes the feel.
```

**Architecture decisions:**
- **Redis Streams as event buffer** — Not process-local queues. Events replay after reconnects. `Last-Event-ID` resume supported. Multiple clients watch the same rumble without fragmentation.
- **Parallel JAM + Sequential GD** — JAM round runs all models via `asyncio.gather()`. GD round is sequential so each model reads the last argument before countering. Two different orchestration strategies, same pipeline.
- **SSE over WebSocket** — Stateless transport, proxy-friendly, no connection upgrade needed. `X-Accel-Buffering: no` header prevents platform-level response buffering.
- **IP-hash deduplication** — Raw IPs never stored. Hashed before Redis/PostgreSQL. PostgreSQL unique constraint on `(rumble_id, ip_hash)` enforces vote integrity at the database level.

```
Stack: FastAPI · Redis Streams · SSE · SQLAlchemy · Alembic · React 18 · Framer Motion · TypeScript · Docker Compose
```

---

### 📧 [HiHR](https://github.com/vutikurishanmukha9/HR_Cold_Email) — Smart HR Outreach Tool
> **Personalized bulk email campaigns with real open/click tracking. Built for my own job search.**

```
Origin   → I was cold-emailing 1,843 HR contacts. Every existing tool had terrible UX.
Solution → I built it in a weekend. Used it. It worked. Then hardened the architecture.
```

**Security and reliability engineering:**
- **AES-256-CBC credential encryption** — SMTP credentials encrypted at rest. Key rotation invalidates old creds, not app state.
- **SMTP Connection Pooling** — Connections cached and reused. 5–10× faster than reconnecting per email.
- **Open/Click Pixel Tracking** — 1×1 GIF pixel on open. Link rewriting with redirect proxy on click. Per-recipient tracking with timestamp.
- **JWT + Account Lockout** — 5 failed attempts = 30-minute lockout. Access tokens expire in 15 min. Refresh tokens in 7 days.
- **Batch Sending with Configurable Delay** — Configurable batch size and inter-batch delays. ISP rate limits respected by design.

```
Stack: React 19 · TypeScript · Node.js · Express · Prisma · PostgreSQL · Nodemailer · bcryptjs · Winston · Docker
```

---

### 🧠 [PromptBuddy](https://github.com/vutikurishanmukha9/PromptBuddy) — Multi-LLM Prompt Evaluator
> **Test prompts across GPT-4, Claude, Gemini, and Cohere simultaneously.**

```
Problem  → I was manually copy-pasting prompts between model interfaces. Everyone does this.
Solution → One interface. Four models. Side-by-side. Scored on 5 dimensions.
```

- 21 production-ready prompt templates across domains
- Keyword-based suggestion engine that recommends templates from partial input
- 5-dimension quality scorer: Clarity · Specificity · Context · Tone · Completeness
- Multi-LLM evaluation in parallel — OpenAI · Anthropic · Google · Cohere

```
Stack: Python · React · OpenAI API · Anthropic API · Gemini API · Cohere API
```

---

<details>
<summary><b>↓ More projects (click to expand)</b></summary>

<br>

**[SHL Assessment Recommender](https://github.com/vutikurishanmukha9)** — FastAPI backend with BM25 + semantic retrieval, 3-tier LLM failover (Premium → Free → Deterministic fallback), regex-based guardrails that bypass LLM entirely for off-topic queries. Deployed on Railway.

**[Ele-Visualize](https://github.com/vutikurishanmukha9/Ele-Visualize)** — 3D chemistry workbench with React Three Fiber, MediaPipe hand tracking, WebXR AR. Gesture state machine: open hand = rotate, pinch = zoom, fist = freeze. WebSocket backend on Node.js/Express.

**[AI Resume Analyzer](https://github.com/vutikurishanmukha9/Resume_App)** — Sentence Transformers + custom ATS scorer. Negation-aware keyword parsing ("NOT required" handled correctly). 86% semantic similarity accuracy. Fully stateless — no disk writes, works on ephemeral filesystems.

**[Team Task Manager](https://github.com/vutikurishanmukha9/project-focus)** — Django REST Framework SaaS. RBAC enforced at permission class + queryset + serializer layers (three layers, not one). Zero N+1 queries by design. Deployed: Railway + Vercel + Neon PostgreSQL.

**[Global Unicorn Dashboard](https://github.com/vutikurishanmukha9/unicorn-dashboard)** — Power BI analysis of 1,073 unicorn companies. Star schema (4 related tables), Power Query cleaning, DAX measures, dynamic slicers across 6 continents.

**[Jarvis](https://github.com/vutikurishanmukha9)** — PDF Q&A with LangChain + FAISS. Multi-provider LLM support (OpenAI, OpenRouter, custom endpoints). HuggingFace Sentence Transformers as local embedding fallback — provider-agnostic by design.

</details>

---

## `$ cat /skills/index`

```python
languages     = ["Python", "TypeScript", "JavaScript", "SQL", "C++", "Java"]

ai_ml         = ["OpenAI GPT-4o", "Anthropic Claude", "Google Gemini", "Cohere",
                 "LangChain", "RAG (Dense + Sparse Hybrid)", "Sentence Transformers",
                 "FAISS", "ChromaDB", "Prompt Engineering", "LLM Evaluation",
                 "YOLOv8", "scikit-learn", "Polars", "Pandas", "NumPy"]

backend       = ["FastAPI", "Django REST Framework", "Node.js", "Express",
                 "Celery", "SQLAlchemy 2.0", "Prisma", "Pydantic v2",
                 "Async Python", "REST API Design", "SSE", "WebSockets"]

frontend      = ["React 18/19", "TypeScript", "Vite", "Tailwind CSS",
                 "TanStack Query", "Framer Motion", "React Three Fiber",
                 "Shadcn/UI", "Radix UI"]

databases     = ["PostgreSQL", "SQLite", "MongoDB", "Redis (Streams + Cache)"]

cloud_devops  = ["AWS (EC2, S3, Lambda, RDS, CloudFormation)", "Docker",
                 "GitHub Actions CI/CD", "Jenkins", "Railway", "Render", "Vercel"]

data_tools    = ["Power BI", "Power Query", "DAX", "Star Schema", "EDA"]

security      = ["JWT + HttpOnly Cookies", "AES-256-CBC", "RBAC",
                 "Rate Limiting", "Magic Number Validation", "bcrypt"]
```

---

## `$ git log --stats`

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=vutikurishanmukha9&show_icons=true&theme=github_dark&hide_border=true&include_all_commits=true&count_private=true&ring_color=ffffff&title_color=ffffff&icon_color=aaaaaa&text_color=cccccc&bg_color=0d1117" height="165"/>
&nbsp;&nbsp;
<img src="https://github-readme-stats.vercel.app/api/top-langs?username=vutikurishanmukha9&layout=compact&theme=github_dark&hide_border=true&title_color=ffffff&text_color=cccccc&bg_color=0d1117" height="165"/>

</div>

<div align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=vutikurishanmukha9&theme=github-dark-blue&hide_border=true&stroke=0d1117&ring=ffffff&fire=ffffff&currStreakLabel=ffffff"/>

</div>

---

## `$ cat /certifications`

| Certification | Issuer | Year |
|---|---|---|
| AWS Certified Cloud Practitioner | Amazon Web Services | 2024 |
| Oracle AI Foundations Associate | Oracle | 2025 |
| Data Analysis with Python | IBM | 2025 |
| SQL for Data Science | IBM | 2025 |
| Python for Data Science | IBM | 2025 |

---

## `$ cat /research`

**Optimizing Energy Efficiency in Smart Buildings Through IoT-Driven Occupancy Sensing**  
*Published — IEEE EAIC 2025, NIT Jalandhar (Paper ID: 482)*

---

## `$ cat /internships`

**Cloud Computing Engineering Intern** — EXCELr EdTech *(Dec 2024 – Apr 2025)*
> Deployed and managed AWS infrastructure (EC2, S3, RDS). Automated provisioning via CloudFormation. Built CI/CD pipelines with Jenkins + GitHub Actions.

**Cloud Engineering Intern** — Brain O Vision *(Jun 2024 – Aug 2024)*
> Configured IAM roles, security policies, VPC architectures. Automated CloudFormation deployments. Improved system performance and operational efficiency.

---

## `$ cat /contact`

```bash
echo "Open to: AI Engineering · Full-Stack Development · Data Analytics"
echo "Location: India (Remote or Relocation)"
echo "Email: vutikurishanmukha9@gmail.com"
echo "LinkedIn: linkedin.com/in/shanmukha-vutikuri"
echo "Portfolio: shanmukhworld.netlify.app"
```

> If you're hiring for something interesting — let's talk.  
> I write clean code, I ship things that work, and I document what I build.

---

<div align="center">

<sub>This README was written the same way I write code — with intention, not just to fill space.</sub>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a1a1a,50:111111,100:000000&height=80&section=footer" width="100%"/>

</div>
