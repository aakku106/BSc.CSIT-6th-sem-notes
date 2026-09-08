---
{"dg-publish":true,"permalink":"/agents/","dg-note-properties":{}}
---

# AGENTS.md

Personal **BSc.CSIT (6th sem, TU Nepal, Batch 2080, studied 2083 BS)** study-repo by Adarasha Gaihre (aakku106). It is an **Obsidian vault** of course notes (syllabi + past exam papers) mixed with **practice C#/.NET code** for the .NET-centric computing subject. It is a knowledge base and learning scratch space, **not a shipped application** — treat DOTNET code as teaching snippets, not production.

The repo may not hold every note for every subject; the **exam-analysis notes are the "what to read" pointers** for each course (see below). Course content/syllabus may change over time and notes are not guaranteed up to date. The owner holds **no rights** to any third-party content included (old question papers, syllabus sources, reference PDFs).

## Repo layout

- **Root `*.md` files** are Obsidian "hub" notes per course (link back to `[[BSc.CSIT]]`).
- **Per-course dirs** `CDC/` (Compilers), `DOTNET/`, `E-Com/`, `E-Gov/`, `SE/`, `TW/`. Each course dir has a `Syllabus.md`, an `Old_sets/` folder of past TU exam papers by BS year (e.g. `2076.md`), and its notes.
- **Exam analysis** = the highest-signal "what to read" per subject (topic-wise frequency over the old sets, with priority tiers):
  - `SE/EXAM.md`, `TW/EXXAM.md` (note double-X), `CDC/InternalExams/Exam.md`, plus old sets for the rest.
- **Notes are Obsidian**: use YAML frontmatter (`Course`, `Batch: "2080"`, `Year: "2083"`, `tags`) and `[[wikilink]]` cross-references (incl. anchors like `[[Syllabus#Unit X]]`). Match this style in new notes; do not convert links to plain markdown.
- **Code lives under `DOTNET/`** as multiple independent projects — there is **no `.sln`** and no shared root build.
- **Known filename typos are intentional and self-consistent** — don't "fix" them: `Software Engenearing.md` (hub), `EXXAM.md` (TW), `Mode_I.md` (SE set), `NotificationServive.cs`.

## .NET projects (each is its own csproj, `net10.0` target)

Run `dotnet build` **inside each project directory**; do not expect a single solution to build them all. `.claude/settings.local.json` already whitelists `dotnet build`.

| Project               | Type                             | Notes                                                                                                                               |
| --------------------- | -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `DOTNET/Day1`, `Day2` | console app (`Exe`)              | simple language demos                                                                                                               |
| `DOTNET/API/learnAPI` | ASP.NET Core Web API             | has Swagger; DI example (`AddScoped<INotificationService, SmsNotificationService>`)                                                 |
| `DOTNET/MVC/learnMVC` | ASP.NET Core MVC web             | Razor views; uses `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` (views compile at runtime) + `WebApplication.MapStaticAssets` |
| `DOTNET/DB/LearnDB`   | EF Core console + **PostgreSQL** | requires a running Postgres                                                                                                         |

Additional DOTNET content under `DOTNET/`:

- `Syllabus.md` + `Old_sets/` (6 sets across years)
- `LAB/` — lab task docs (`DOTNET_Labs_All.md`, `DOTNET_Labs_Code.md`) + `CSIT- Lab *.pdf` scanner copies; the `.md` files are the readable source, PDFs are paper scans
- `DB/ADO.NET.md` — course note on ADO.NET

### DB project quirk

`LearnDB/Program.cs` reads the connection string from the `POSTGRES_CONNECTION_STRING` env var, defaulting to `Host=localhost;Port=5432;Database=postgres;Username=$USER`. It uses `EnsureCreatedAsync` (no migrations) and calls `CanConnectAsync` to validate. Expect a "PostgreSQL connection failed" unless a local Postgres is running — falling back safely is intended, not a bug.

## Toolchain

- Requires **.NET 10 SDK** (`net10.0`); `dotnet --version` is `10.0.301` on this machine.
- Not an app-prod repo: no lint/test/CI config exists. Build is the only verification step.
- Obsidian vault: `.obsidian/` holds only editor settings/themes, no content; frontmatter conventions above are the style to match.

## Git

- Single `main` branch; remote `origin` (GitHub, `aakku106/Bec.CSit_6th_sem`).
- `bin/`, `obj/`, `*.dll` are gitignored — never commit build artifacts.
- Commit style from history: short imperative summaries per change (e.g. "Add StudentController and Student model").
