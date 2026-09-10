---
{"dg-publish":true,"permalink":"/dotnet/exam/","tags":["exam","dotnet","analysis"],"dg-note-properties":{"Subject":"[[DotNet]]","Topic":"Important Questions Analysis","Sets Analyzed":["[[DOTNET/Old_sets/2081|2081]]","[[DOTNET/Old_sets/2080|2080]]","[[DOTNET/Old_sets/2079|2079]]","[[DOTNET/Old_sets/2078|2078]]","[[DOTNET/Old_sets/Model|Model]]","[[DOTNET/Old_sets/2076|2076]]"],"tags":["exam","dotnet","analysis"]}}
---


# .NET — Topic-wise Frequency Analysis & Priority List

Based on 5 relevant old question sets. Unit references link to [[DOTNET/Syllabus\|Syllabus]].

> ⚠️ **[[DOTNET/Old_sets/2076\|2076]] is excluded from the counts below.** It tests classic **ASP** (VBScript, ADO classic, IIS, request/session/application/server objects) — a completely different, outdated technology stack that does not appear anywhere in the current [[DOTNET/Syllabus\|Syllabus]] (which is entirely ASP.NET **Core** / C# / EF Core / MVC). Treat 2076 as historical only — don't spend prep time on it.

## Tier 1 — Most Important (recurring practical/coding + conceptual staples, 4–5 of 5 sets)

| Topic | Unit / Syllabus Topic | Appeared In | Count | Typical Ask |
|---|---|---|---|---|
| State Management (Session, TempData, Cache, Cookies, Hidden Fields, stateless HTTP) | [[DOTNET/Syllabus#Unit 6. State Management on ASP.NET Core Application (4 Hrs.)\|Unit 6 – Server-side & Client-side Strategies]] | [[DOTNET/Old_sets/2078\|2078]] (×2), [[DOTNET/Old_sets/2079\|2079]] (×2), [[DOTNET/Old_sets/2080\|2080]] (×2), [[DOTNET/Old_sets/2081\|2081]], [[DOTNET/Old_sets/Model\|Model]] (×2) | 5/5 | Explain stateless HTTP handling; differentiate Session/TempData/Cache; manage session state with an example |
| Controllers, Razor Views, Tag Helpers, Model Binding (MVC building blocks) | [[DOTNET/Syllabus#Unit 4. Creating ASP.NET core MVC applications (10 Hrs.)\|Unit 4 – Controllers and Actions, Razor Syntax, Tag Helpers, Model Binding]] | [[DOTNET/Old_sets/2079\|2079]], [[DOTNET/Old_sets/2080\|2080]] (×2), [[DOTNET/Old_sets/2081\|2081]], [[DOTNET/Old_sets/Model\|Model]] (×2) | 5/5 | Create a controller; explain Razor/tag helpers; explain model binding & validation |
| Database Access — Entity Framework Core & ADO.NET (CRUD, ORM, Connection/Command/Reader/Adapter) | [[DOTNET/Syllabus#Unit 5. Working with Database (6 Hrs.)\|Unit 5 – ADO.NET Basics, Entity Framework Core, ORM]] | [[DOTNET/Old_sets/2078\|2078]] (×2), [[DOTNET/Old_sets/2079\|2079]], [[DOTNET/Old_sets/2080\|2080]] (×2), [[DOTNET/Old_sets/2081\|2081]] (×2), [[DOTNET/Old_sets/Model\|Model]] | 5/5 | Write EF Core CRUD code; write ADO.NET program; explain ORM/EF advantages over ADO.NET |
| C# Language Constructs (exceptions, structs/enums, collections/generics, abstract/sealed/interface, polymorphism, delegates/events) | [[DOTNET/Syllabus#Unit 1. Language Preliminaries (8 Hrs.)\|Unit 1 – Language Preliminaries]] | [[DOTNET/Old_sets/2078\|2078]] (×3), [[DOTNET/Old_sets/2079\|2079]] (×3), [[DOTNET/Old_sets/2080\|2080]] (×3), [[DOTNET/Old_sets/2081\|2081]] (×3), [[DOTNET/Old_sets/Model\|Model]] (×5) | 5/5 | Write a program using exceptions/structs/generics/inheritance; differentiate two OOP constructs |
| Client-side Validation & SPA (jQuery form validation, Angular/React) | [[DOTNET/Syllabus#Unit 7. Client-side Development in ASP.NET Core (4 Hrs.)\|Unit 7 – JQuery, Forms and Validation, SPA Frameworks]] | [[DOTNET/Old_sets/2078\|2078]], [[DOTNET/Old_sets/2079\|2079]] (×2), [[DOTNET/Old_sets/2080\|2080]], [[DOTNET/Old_sets/2081\|2081]], [[DOTNET/Old_sets/Model\|Model]] | 5/5 | Write jQuery form-validation code; compare Angular vs React for SPA |
| Hosting & Deployment (deploy .NET core app, IIS/Nginx/Kestrel, Docker, Azure) | [[DOTNET/Syllabus#Unit 9. Hosting and Deploying ASP.NET Core Application (2 Hrs.)\|Unit 9 – Hosting Models, Docker, Publish to Azure]] | [[DOTNET/Old_sets/2078\|2078]] (×2), [[DOTNET/Old_sets/2079\|2079]] (×2), [[DOTNET/Old_sets/2080\|2080]], [[DOTNET/Old_sets/2081\|2081]] (×2), [[DOTNET/Old_sets/Model\|Model]] (×3) | 5/5 | Explain steps to deploy a .NET core app; discuss Docker/containerization |
| Web Security Vulnerabilities (SQL Injection, XSS, CSRF, Open Redirect) | [[DOTNET/Syllabus#Unit 8. Securing in ASP.NET Core Application (5 Hrs.)\|Unit 8 – Common Vulnerabilities]] | [[DOTNET/Old_sets/2078\|2078]] (×3), [[DOTNET/Old_sets/2079\|2079]] (×2), [[DOTNET/Old_sets/2080\|2080]] (×2), [[DOTNET/Old_sets/2081\|2081]] | 4/5 | Write a program showing/preventing SQL injection; define CSRF or open redirect attack |
| HTTP, MVC Pattern & ASP.NET Core Architecture | [[DOTNET/Syllabus#Unit 3. HTTP and ASP.NET Core (3 Hrs.)\|Unit 3 – HTTP, MVC Pattern, ASP.NET Core Architecture]] | [[DOTNET/Old_sets/2078\|2078]], [[DOTNET/Old_sets/2079\|2079]], [[DOTNET/Old_sets/2080\|2080]], [[DOTNET/Old_sets/Model\|Model]] | 4/5 | Explain request/response format; describe importance/role of MVC pattern |

## Tier 2 — Important (moderate repetition, 3 of 5 sets)

| Topic | Unit / Syllabus Topic | Appeared In | Count | Typical Ask |
|---|---|---|---|---|
| Authorization (Roles, Claims, Policies) & Authentication (Identity) | [[DOTNET/Syllabus#Unit 8. Securing in ASP.NET Core Application (5 Hrs.)\|Unit 8 – Authentication, Authorization]] | [[DOTNET/Old_sets/2079\|2079]], [[DOTNET/Old_sets/2080\|2080]], [[DOTNET/Old_sets/2081\|2081]], [[DOTNET/Old_sets/Model\|Model]] | 4/5 | Distinguish roles vs policies; explain ASP.NET Core Identity |
| Dependency Injection & IoC Container | [[DOTNET/Syllabus#Unit 4. Creating ASP.NET core MVC applications (10 Hrs.)\|Unit 4 – Dependency Injection and IOC Containers]] | [[DOTNET/Old_sets/2079\|2079]], [[DOTNET/Old_sets/2080\|2080]], [[DOTNET/Old_sets/2081\|2081]] | 3/5 | Explain DI/IoC container; describe service registration/lifecycle |
| .NET Framework Comparisons (.NET vs .NET Core vs Mono vs ASP.NET) & Architecture/Design Principles | [[DOTNET/Syllabus#Unit 2. Introduction to ASP.NET (3 Hrs.)\|Unit 2 – .NET and ASP.NET Frameworks, Architecture and Design Principles]] | [[DOTNET/Old_sets/2078\|2078]], [[DOTNET/Old_sets/2079\|2079]], [[DOTNET/Old_sets/Model\|Model]] | 3/5 | Differentiate frameworks; explain CLI/MSIL/CLR compilation process |
| URL Routing | [[DOTNET/Syllabus#Unit 4. Creating ASP.NET core MVC applications (10 Hrs.)\|Unit 4 – URL Routing and Features]] | [[DOTNET/Old_sets/2078\|2078]], [[DOTNET/Old_sets/2080\|2080]] | 2/5 | Explain URL routing / list its features |

## Tier 3 — If Time Remains (appeared once or twice)

| Topic | Unit / Syllabus Topic | Appeared In | Typical Ask |
|---|---|---|---|
| Async/Await Pattern | [[DOTNET/Syllabus#Unit 1. Language Preliminaries (8 Hrs.)\|Unit 1 – Asynchronous Programming]] | [[DOTNET/Old_sets/Model\|Model]] | Explain async/await with a simple example |
| Indexers vs Properties | [[DOTNET/Syllabus#Unit 1. Language Preliminaries (8 Hrs.)\|Unit 1 – Indexers]] | [[DOTNET/Old_sets/Model\|Model]] | Explain indexers with an example |
| Attributes (Named & Positional Parameters) | [[DOTNET/Syllabus#Unit 1. Language Preliminaries (8 Hrs.)\|Unit 1 – Attributes]] | [[DOTNET/Old_sets/2078\|2078]], [[DOTNET/Old_sets/2081\|2081]] | Explain named vs positional attribute parameters |
| TempData vs Session vs ViewData | [[DOTNET/Syllabus#Unit 6. State Management on ASP.NET Core Application (4 Hrs.)\|Unit 6 – TempData]] | [[DOTNET/Old_sets/Model\|Model]] | Differentiate the three and when to use TempData |
| Method Hiding vs Method Overriding | [[DOTNET/Syllabus#Unit 1. Language Preliminaries (8 Hrs.)\|Unit 1 – Method Hiding and Overriding]] | [[DOTNET/Old_sets/Model\|Model]] | Short note distinguishing the two |
| Action Result Types & Web API Controllers | [[DOTNET/Syllabus#Unit 4. Creating ASP.NET core MVC applications (10 Hrs.)\|Unit 4 – Action Results Types, Web API Applications]] | [[DOTNET/Old_sets/Model\|Model]] | Design an API controller with GET/POST/PUT/DELETE returning JSON |

## Study Priority Summary

1. **Master first:** State Management ([[DOTNET/Syllabus#Unit 6. State Management on ASP.NET Core Application (4 Hrs.)\|Unit 6]]), Controllers/Razor/Tag Helpers/Model Binding ([[DOTNET/Syllabus#Unit 4. Creating ASP.NET core MVC applications (10 Hrs.)\|Unit 4]]), Database access via EF Core & ADO.NET ([[DOTNET/Syllabus#Unit 5. Working with Database (6 Hrs.)\|Unit 5]]), core C# language constructs — exceptions, generics, OOP features ([[DOTNET/Syllabus#Unit 1. Language Preliminaries (8 Hrs.)\|Unit 1]]), jQuery validation & SPA frameworks ([[DOTNET/Syllabus#Unit 7. Client-side Development in ASP.NET Core (4 Hrs.)\|Unit 7]]), Hosting/Deployment ([[DOTNET/Syllabus#Unit 9. Hosting and Deploying ASP.NET Core Application (2 Hrs.)\|Unit 9]]), Security vulnerabilities — especially SQL injection ([[DOTNET/Syllabus#Unit 8. Securing in ASP.NET Core Application (5 Hrs.)\|Unit 8]]), and HTTP/MVC Pattern basics ([[DOTNET/Syllabus#Unit 3. HTTP and ASP.NET Core (3 Hrs.)\|Unit 3]]) — every one of these appears in 4–5 of the 5 relevant papers.
2. **Then cover:** Authorization/Authentication (Unit 8), Dependency Injection & IoC (Unit 4), .NET framework comparisons and architecture (Unit 2), URL routing (Unit 4).
3. **Last, if time remains:** Async/await, indexers, attributes, TempData vs Session vs ViewData, method hiding vs overriding, and Web API action result types — these are newer additions (mostly from the Model set) that may signal where upcoming exams are heading, but haven't repeated across older years yet.

> Note: This subject leans heavily on **hands-on coding questions** (write a program / create a class / write EF Core or ADO.NET code / write jQuery validation) rather than pure theory — practice writing actual C#/Razor/jQuery snippets for each Tier 1 topic instead of only memorizing definitions. Also note the Model set introduces several topics not seen in 2078–2081 (async/await, indexers, TempData, Web API Action Results, method hiding vs overriding) — these look like likely additions for the upcoming exam given the syllabus already covers them in detail.

---

Related: [[DOTNET/Syllabus\|Syllabus]] · [[DOTNET/Old_sets/2076\|2076]] · [[DOTNET/Old_sets/2078\|2078]] · [[DOTNET/Old_sets/2079\|2079]] · [[DOTNET/Old_sets/2080\|2080]] · [[DOTNET/Old_sets/2081\|2081]] · [[DOTNET/Old_sets/Model\|Model]]
