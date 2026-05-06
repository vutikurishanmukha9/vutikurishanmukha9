<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f0c29,50:302b63,100:24243e&height=120&section=header&animation=fadeIn" width="100%"/>

# Shanmukha Vutikuri

**AI Engineer · Full-Stack Developer · Data & Cloud**

*I build things that ship — not just things that run on localhost.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shanmukha-vutikuri/)
[![Portfolio](https://img.shields.io/badge/Portfolio-111827?style=flat-square&logo=vercel&logoColor=white)](https://shanmukhworld.netlify.app)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:vutikurishanmukha9@gmail.com)
[![Profile Views](https://komarev.com/ghpvc/?username=vutikurishanmukha9&style=flat-square&color=6366f1&label=profile+views)](https://github.com/vutikurishanmukha9)

</div>

---

## About

B.Tech ECE graduate who builds AI-powered full-stack products — from the RAG pipeline to the deployed UI. I care about architecture decisions, clean APIs, and shipping things that actually work in production.

Right now I'm looking for entry-level roles in **AI engineering**, **full-stack development**, or **data analytics**.

- 🔭 Latest project: **HeartOut** — a storytelling platform with 541+ automated tests and CI/CD
- 📄 Research published at **IEEE EAIC 2025**
- ☁️ Certified: **AWS Cloud Practitioner** · **Oracle AI Foundations Associate**
- 🧠 Interests: RAG architectures, LLM evaluation, async Python, product engineering

---

## Projects

These are the four I'd walk an interviewer through:

### [GetReport](https://get-report.vercel.app/) — AI Data Analysis Platform
> Upload CSV/Excel → get a clean, publication-ready PDF report with AI commentary.

Two-stage pipeline: inspection phase (data profiling + quality scoring) → analysis phase (approved cleaning + stats + PDF generation). The interesting engineering is in the hybrid RAG engine — dense vector search combined with sparse keyword scoring for context retrieval that actually answers domain-specific questions.

**Stack:** FastAPI · GPT-4o · Polars (lazy execution) · Celery · Redis · PostgreSQL · AWS S3 · WeasyPrint  
**What I'd highlight:** Magic number file validation to prevent extension spoofing, async Celery workers to keep the API non-blocking, and a dual PDF engine (ReportLab for dev, WeasyPrint for prod) switchable via env var.

---

### [HeartOut](https://github.com/vutikurishanmukha9/HeartOut) — Storytelling Platform
> Anonymous, empathy-first space for sharing personal stories.

Production-grade FastAPI backend (migrated from Flask in v3.0) with async SQLAlchemy, HttpOnly cookie auth (immune to XSS token theft), and a smart gravity-based ranking algorithm for the feed. CI/CD pipeline runs on every push.

**Stack:** FastAPI · SQLAlchemy 2.0 · React 18 · TanStack Query · PostgreSQL · Redis  
**Stats:** 541+ automated tests (327 pytest + 214 Vitest) · 70% backend coverage · GitHub Actions CI

---

### [HiHR](https://github.com/vutikurishanmukha9/HR_Cold_Email) — HR Email Outreach Tool
> Bulk personalized email campaigns with real-time tracking.

Built JWT auth with account lockout (5 attempts = 30-min block), AES-256-CBC credential encryption, SMTP connection pooling for 5–10× send performance, and a click/open tracking pipeline with 1×1 pixel embeds and redirect proxying. Kept local due to SMTP constraints on free tiers — but the architecture is production-ready.

**Stack:** React 19 · TypeScript · Node.js · Express · Prisma · PostgreSQL · Nodemailer · Winston

---

### [PromptBuddy](https://github.com/vutikurishanmukha9/PromptBuddy) — Multi-LLM Prompt Evaluator
> Test your prompts across GPT-4, Claude, Gemini, and Cohere simultaneously.

21 prompt templates, a keyword-based suggestion engine, and a 5-dimension quality scorer (clarity, specificity, context, tone, completeness). Useful for comparing how different models handle the same instruction — built this because I kept doing this manually.

**Stack:** Python · React · OpenAI API · Claude API · Gemini API · Cohere API

---

<details>
<summary><strong>Other projects</strong> — click to expand</summary>
<br>

**[Team Task Manager](https://github.com/vutikurishanmukha9/project-focus)** — Full-stack SaaS with Django REST Framework, role-based access control enforced at permission class + queryset + serializer layers, deployed on Railway + Vercel + Neon PostgreSQL. Zero N+1 queries by design.

**[Ele-Visualize](https://github.com/vutikurishanmukha9/Ele-Visualize)** — 3D chemistry learning workbench with React Three Fiber, MediaPipe hand tracking, and WebXR AR. Premium dark-mode scientific UI with a command palette, gesture state machine (open hand = rotate, pinch = zoom, fist = freeze), and a local JSON-backed session store.

**[AI Resume Analyzer](https://github.com/vutikurishanmukha9/Resume_App)** — Sentence Transformers + custom ATS scorer with 5 weighted components (keywords 35%, skills 25%, experience 20%, education 10%, formatting 10%). Negation-aware keyword parsing ("NOT required" handled correctly). Fully stateless, no disk writes — works on ephemeral filesystems.

**[Global Unicorn Dashboard](https://github.com/vutikurishanmukha9/unicorn-dashboard)** — Power BI analysis of 1,073 unicorn companies. Star schema with 4 related tables, Power Query cleaning, DAX measures, and dynamic slicers across 6 continents.

**[Multimodal AI System](https://github.com/vutikurishanmukha9/multimodal_ai_project)** — YOLOv8 + BLIP (Salesforce) for object detection, image captioning, and visual Q&A. Streamlit interface with four color themes and session-based image history.

</details>

---

## Tech Stack

**Languages:** Python · TypeScript · JavaScript · C++ · Java  

**AI / ML / Data:**  
`OpenAI` `Anthropic` `Google Gemini` `Cohere` `LangChain` `Sentence Transformers` `YOLOv8` `Polars` `Pandas` `scikit-learn` `Power BI`

**Backend:**  
`FastAPI` `Django REST Framework` `Node.js / Express` `Celery` `Redis` `SQLAlchemy` `Prisma`

**Frontend:**  
`React 18/19` `TypeScript` `Vite` `Tailwind CSS` `TanStack Query` `React Three Fiber`

**Databases & Infra:**  
`PostgreSQL` `SQLite` `MongoDB` `Redis` `Docker` `AWS S3` `Railway` `Render` `Vercel`

---

## GitHub Stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=vutikurishanmukha9&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=true" height="160"/>
&nbsp;
<img src="https://github-readme-stats.vercel.app/api/top-langs?username=vutikurishanmukha9&layout=compact&theme=tokyonight&hide_border=true" height="160"/>

</div>

<div align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=vutikurishanmukha9&theme=tokyonight&hide_border=true"/>

</div>

---

## Certifications & Research

| | |
|---|---|
| AWS Cloud Practitioner | Amazon Web Services, 2024 |
| Oracle AI Foundations Associate | Oracle, 2024 |
| IEEE EAIC 2025 | Research paper published and presented |

---

## Get In Touch

I'm actively looking for entry-level roles in AI engineering, full-stack development, or data analytics.

If you're building something interesting or have a role that fits — I'd like to hear about it.

**LinkedIn:** [shanmukha-vutikuri](https://www.linkedin.com/in/shanmukha-vutikuri/) · **Portfolio:** [shanmukhworld.netlify.app](https://shanmukhworld.netlify.app)

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=80&section=footer" width="100%"/>

</div>
