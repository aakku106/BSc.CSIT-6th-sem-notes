---
{"dg-publish":true,"permalink":"/readme/","tags":["gardenEntry"],"dg-note-properties":{}}
---

<div align="center">

# BSc.CSIT 6th Semester — Study & Practice Repository

**Batch 2080 · Studied 2083 BS · Tribhuvan University (TU), Nepal**

Personal knowledge base, past-paper collection, and .NET practice workspace

</div>

---

## About

This repository is a personal **study vault and practice workspace** for the **BSc.CSIT 6th semester** curriculum of **Tribhuvan University (TU), Nepal**, compiled by **Adarasha Gaihre (aakku106)**.

It brings together three things into a single organized space:

- **📚 Course notes & syllabi** — structured Obsidian notes per subject with official syllabus breakdowns.
- **🗂 Past exam papers (Old Sets)** — scanned/typed TU question papers organized by Nepali Bikram Sambat (BS) year.
- **💻 .NET practice code** — independent C# / .NET projects written while studying the _`.NET-Centric Computing`_ subject.

> **Note.** This is a **study/learning repository**, not a shipped application. The code here is teaching snippets and scratch practice. The repo may not contain notes for _every_ topic of _every_ subject — course content and syllabi evolve, and notes are not guaranteed to be current. The owner holds **no rights** to third-party content included (past question papers, syllabus sources, reference PDFs).

---

## Semesters & Subjects

The 6th semester covers **six subjects**, each with its own course directory and an Obsidian "hub" note at the repo root:

| Subject                            | Course Dir           | Root Hub Note                                          | Unit Count |
| ---------------------------------- | -------------------- | ------------------------------------------------------ | ---------- |
| **Compiler Design & Construction** | [`CDC/`](CDC/)       | [[CDC\|`CDC.md`]]                                     | 4          |
| **.NET-Centric Computing**         | [`DOTNET/`](DOTNET/) | [[DotNet\|`DotNet.md`]]                               | 9          |
| **E-Commerce**                     | [`E-Com/`](E-Com/)   | [[E-commerce\|`E-commerce.md`]]                       | 7          |
| **E-Government**                   | [`E-Gov/`](E-Gov/)   | [[E-government\|`E-government.md`]]                   | 6          |
| **Software Engineering**           | [`SE/`](SE/)         | [[Software Engenearing\|`Software Engenearing.md`]] | 10         |
| **Technical Writing**              | [`TW/`](TW/)         | [[Technical Writing\|`Technical Writing.md`]]       | 12         |

All hub notes link back to the master hub [[BSc.CSIT\|`BSc.CSIT.md`]]. Notes use Obsidian conventions (YAML frontmatter + `[[wikilinks]]`) — open the repo as an **Obsidian vault** to get the full cross-linked reading experience.

---

## The "What to Read" (Exam Analysis)

The highest-signal documents in the repo are the **exam-analysis notes** — topic-wise frequency analyses of every past exam set, with **priority tiers** that say _what to study first_. When reviewing the material, these are the best starting points:

- **Software Engineering** → [[SE/EXAM\|`SE/EXAM.md`]]
- **Technical Writing** → [`TW/EXXAM.md`](TW/EXXAM.md) _(note the intentional double-X filename)_
- **Compiler Design & Construction** → [[CDC/InternalExams/Exam\|`CDC/InternalExams/Exam.md`]]

---

## Repository Layout

```
├── BSc.CSIT.md                 # Master course hub note
├── CDC.md                      # Compiler Design hub
├── DotNet.md                   # .NET hub
├── E-commerce.md               # E-Commerce hub
├── E-government.md             # E-Government hub
├── Software Engenearing.md     # Software Engineering hub  (typo is intentional)
├── Technical Writing.md        # Technical Writing hub
│
├── CDC/                        # COMPILERS
│   ├── Syllabus.md             # Official syllabus, unit breakdown
│   ├── InternalExams/Exam.md   # Exam analysis (priority tiers)
│   └── Old_sets/               # 8 past papers (2075–2081 + Models)
│
├── DOTNET/                     # .NET-CENTRIC COMPUTING
│   ├── Syllabus.md
│   ├── Old_sets/               # 6 past papers (2076–2081 + Model)
│   ├── LAB/                    # Lab tasks: DOTNET_Labs_All.md, DOTNET_Labs_Code.md + PDF scans
│   ├── DB/ADO.NET.md           # ADO.NET course note
│   ├── Day1/  Day2/            # Console demo projects
│   ├── API/learnAPI/           # ASP.NET Core Web API + Swagger
│   ├── MVC/learnMVC/           # ASP.NET Core MVC web app
│   └── DB/LearnDB/             # EF Core + PostgreSQL console app
│
├── E-Com/                      # E-COMMERCE
│   ├── Syllabus.md
│   └── Old_sets/               # 5 past papers (2076–2081)
│
├── E-Gov/                      # E-GOVERNMENT
│   ├── Syllabus.md
│   ├── E-Governance-Maturity-Models.pptx
│   └── Old_sets/               # 7 past papers (2076–2082 + Model)
│
├── SE/                         # SOFTWARE ENGINEERING
│   ├── Syllabus.md
│   ├── EXAM.md                 # Exam analysis (priority tiers)
│   ├── *reference PDFs*
│   └── Old_sets/               # 7 past papers (2076–2081 + Models)
│
├── TW/                         # TECHNICAL WRITING
│   ├── Syllabus.md
│   ├── EXXAM.md                # Exam analysis (priority tiers)
│   ├── *reference PDFs*        # incl. owner's 6th-sem resume
│   └── Old_sets/               # 8 past papers (2074–2081 + Model)
│
├── AGENTS.md                   # Agent guidance (how to work in this repo)
├── README.md                   # This file
└── .obsidian/                  # Obsidian editor/themes config only
```

---

## 📘 Subject Highlights

### Compiler Design & Construction (`CDC/`)

Covers the classic compiler pipeline: introduction, **lexical analysis** (the bulk of the syllabus), **symbol table & runtime storage**, and **intermediate code generation / optimization / case studies**. Includes 8 past-paper sets and an exam analysis with priority tiers.

### .NET-Centric Computing (`DOTNET/`)

The most hands-on subject. The syllabus spans language preliminaries → ASP.NET Core → MVC → databases → state management → client-side development → security → hosting. The code directory contains five independent projects used to practice these concepts (see [.NET Projects](#-net-projects) below), plus lab task descriptions and code.

### E-Commerce (`E-Com/`)

E-commerce fundamentals: business models, **electronic payment systems**, building e-commerce systems, **security**, digital marketing, and optimization. Includes 5 past-paper sets.

### E-Government (`E-Gov/`)

Concepts and **models of e-governance**, infrastructure development, security, **data warehousing/mining in government**, and case studies. Includes 7 past-paper sets (the latest, 2082, plus a model set).

### Software Engineering (`SE/`)

A full 10-unit sweep: processes, **agile**, requirements engineering, **system modeling**, architecture, design, **testing**, evolution, and management. Ships with a detailed exam-analysis document and 7 past-paper sets.

### Technical Writing (`TW/`)

Practical writing across 12 units: audience & purpose, the writing process, **brief correspondence**, document design, web writing, **employment communication**, presentations, recommendation reports, proposals, and workplace ethics. Includes 8 past-paper sets.

---

## 💻 .NET Projects

Each project is an **independent `.csproj`** targeting `net10.0`. There is **no solution file (`.sln`)** and no shared root build.

```bash
# Build a single project (run from inside its directory)
cd DOTNET/Day1 && dotnet build
```

| Project               | Type                 | Highlights                                                                      |
| --------------------- | -------------------- | ------------------------------------------------------------------------------- |
| `DOTNET/Day1`         | Console app          | Language / OOP demos                                                            |
| `DOTNET/Day2`         | Console app          | Delegates, `Action`/`Func`/`Predicate` demos                                    |
| `DOTNET/API/learnAPI` | ASP.NET Core Web API | Swagger, DI example (`AddScoped<INotificationService, SmsNotificationService>`) |
| `DOTNET/MVC/learnMVC` | ASP.NET Core MVC     | Razor views with runtime compilation + `MapStaticAssets`                        |
| `DOTNET/DB/LearnDB`   | EF Core console      | **PostgreSQL** backend (requires a running Postgres)                            |

> **DB note.** `LearnDB/Program.cs` reads the connection string from the `POSTGRES_CONNECTION_STRING` env var (defaulting to `Host=localhost;Port=5432;Database=postgres;Username=$USER`), uses `EnsureCreatedAsync` (no migrations), and validates via `CanConnectAsync`. A "PostgreSQL connection failed" warning is **expected** unless a local Postgres is running — the safe fallback is intentional, not a bug.

---

## 🧰 Toolchain & Requirements

- **.NET 10 SDK** (`net10.0` target). The repo was developed on `dotnet --version` `10.0.301`.
- **Build** is the only verification step — there is **no lint / test / CI** configuration in this repo.
- **Obsidian Vault** — for best note-navigation experience, open the repo root in [Obsidian](https://obsidian.md/).

---

## 🗂 Past Exam Papers (Old Sets)

- Organized in each course's `Old_sets/` directory, **named by BS year** (e.g. `2076.md` → exam from 2076 BS).
- Some folders include **Model papers** (`Model.md`, `Model_I.md`, `Model_II.md`) — practice sets modeled on the real exam format.
- Papers typically follow the TU structure of **Section A / Section B** questions.

---

## 🤝 Contributing

This is a **personal study repository**. Direct pull requests are not expected — but if you spot a genuine correction or have notes for a missing topic, feel free to open an **issue**. Forking for your own studies is welcome.

---

## ⚖️ Disclaimer

- This is a **personal learning resource**, not an official TU publication.
- **Syllabi and course content may change**; the notes reflect the 2083 BS (2026) semester and are not guaranteed up to date.
- The owner holds **no rights** to any third-party content included (past question papers, official syllabus text, or reference PDFs).

---

<div align="center">

**Made with ☕ and a lot of 6th-semester pressure**

_Adarasha Gaihre (aakku106) — Batch 2080 · 2083 BS_

</div>
