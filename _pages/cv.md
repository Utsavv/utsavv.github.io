---
layout: page
title: cv
permalink: /cv/
description: >
  CV of Utsav Verma — AI Architect & Senior Database Architect. 21+ years in
  SQL Server, data platforms, DataOps, and applied AI. 2 AI patents filed.
nav: true
nav_order: 3
---

<div class="d-flex justify-content-center mb-4">
  <a href="https://1drv.ms/w/c/e7ee95718edb5e82/IQCCXtuOcZXuIIDn0jkAAAAAAV5g4qXEYIoaoTEOrYCkXyc?e=RiItJK" target="_blank" rel="noopener" class="btn btn-primary">
    <i class="fa-solid fa-file-word"></i> Download / View Full CV
  </a>
</div>

## Summary

**21+ years** of experience as a Senior Database Architect, Data Platform Leader, and Applied AI Innovator. Specialising in SQL Server, Azure cloud platforms, DataOps, and AI-driven engineering solutions. 2 patents filed for AI framework implementations. 7 published articles on SQLServerCentral. Multiple awards including Employee of the Year.

---

## Professional Experience

### Sr Database Architect / Sr Manager — Aristocrat Technology India
**Jun 2014 – Present** · Gaming domain

**Project: nVision (DWH)** *(Jun 2024 – Present)*
- Led architecture and migration of a 4–5 billion row data warehouse for a large-scale loyalty platform
- Cut migration time and risk by 60–70% using a balance-delta-driven ingestion strategy
- Delivered 100% balance accuracy across legacy and next-gen systems via automated reconciliation
- Tech: SQL Server 2022, SSIS, MicroStrategy, PowerShell

**Project: Loyalty Suite — Sr Database Architect** *(Mar 2017 – Present)*
- Promoted to Sr Architect; organisation-wide leader for innovation and quality
- Conceived and built the master data management framework and MakeDb — an automated build/deploy DataOps suite
- Spearheaded load testing of the entire suite (36 products); introduced UT frameworks and code review processes
- Mentored 10 senior DB developers; led upgrade path to SQL Server 2022, AWS Cloud, AWS RDS
- Contributed towards new product acquisitions
- Tech: SQL Server 2022, SSRS, C#, ASP.NET

**Project: Oasis 360 — Associate Database Architect** *(Jun 2014 – Mar 2017)*
- Optimised a large, tightly coupled system spanning 30+ products in a new gaming domain
- Performance analysis, production issue resolution, HLD design, and cross-team collaboration
- Tech: SQL Server, SSIS, SSRS, C#, ASP.NET

---

### Consultant Engineer — GlobalLogic
**Mar 2011 – Jun 2014** · CRM domain

---

### Analyst — Royal Bank of Scotland, India
**Jan 2009 – Mar 2011** · Investment Banking domain

---

### Developer (Band S2) — Satyam Computer Services
**Oct 2007 – Jan 2009** · Car Finance domain

---

### Senior Software Engineer — Nucleus Software
**Jun 2006 – Oct 2007** · Banking domain

---

### Software Engineer — UBICS Enterprise Solutions
**Jan 2005 – Jun 2006** · e-Governance domain

---

## Key AI Projects

| Project | Highlights |
|---|---|
| **Reusable AI Content & Video Generation Framework** *(Patent Filed)* | Domain-agnostic AI engine for script, audio, image, and video generation; 2 patents applied |
| **AI-Powered Audio-Visual Help for EGMs** | Converted text-heavy EGM help screens into AV explanations using the AI framework |
| **Offline AI Rule Builder for Loyalty Systems** | Natural-language rule engine using offline ~1B parameter LLM on CPU-only systems |
| **AI Scrum Master for Engineering Execution** | Python system to parse Zoom emails, enrich via Git metadata, generate executive summaries |
| **AI-Generated Migration Automation Utility** | Compressed development timelines from ~2 months to ~1 week using AI-generated framework |

---

## Publications

{% assign articles = site.data.articles %}
{% if articles %}
<ul>
  {% for article in articles %}
  <li>
    <a href="{{ article.url }}" target="_blank" rel="noopener">{{ article.title }}</a>
    <br><em>{{ article.platform }}</em>
  </li>
  {% endfor %}
</ul>
{% endif %}

---

## Skills

| Category | Technologies |
|---|---|
| **Databases** | SQL Server 2005–2022, Azure SQL, AWS RDS, PostgreSQL |
| **AI / LLMs** | RAG, Prompt Engineering, Codex CLI, Ollama, GitHub Copilot, ChatGPT |
| **Vector / Search** | FAISS, Azure SQL Vector, Azure AI Search |
| **Cloud** | Azure SQL, ADF, Synapse Analytics, AWS Cloud |
| **ETL / BI** | SSIS, SSRS, MicroStrategy, Dimensional Modeling |
| **Languages** | T-SQL, Python, C#, PowerShell |
| **HA / DR** | Always On AG, FCI, Log Shipping, Replication |
| **DataOps** | Automated build/deploy pipelines, MakeDb framework, Git |

---

## Achievements

- 2 patents applied for AI framework implementations
- 7 articles published on SQLServerCentral.com
- Multiple awards worth ₹15 Lakhs, including Employee of the Year
- Contributed towards new product acquisitions at Aristocrat
- Winner of internal innovation competition
- Conducted 10+ internal training sessions
