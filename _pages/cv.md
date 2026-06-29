---
layout: page
title: cv
permalink: /cv/
nav: true
nav_order: 3
---

<div class="d-flex justify-content-center mb-4">
  <a href="https://1drv.ms/w/c/e7ee95718edb5e82/IQCCXtuOcZXuIIDn0jkAAAAAAV5g4qXEYIoaoTEOrYCkXyc?e=RiItJK" target="_blank" rel="noopener" class="btn btn-primary">
    <i class="fa-solid fa-file-word"></i> Download / View Full CV
  </a>
</div>

## Experience

**Senior Database Architect** · 10+ years  
Architecting reliable data platforms across SQL Server, cloud databases, and AI-integrated data systems.

- SQL Server performance tuning: query optimization, index strategy, execution plan analysis
- High availability design: Always On Availability Groups, Failover Clustering, log shipping
- Change Data Capture (CDC) ETL pipelines for real-time data integration
- Vector search implementation using FAISS and Azure SQL Vector datatype
- Cloud migrations: on-premises SQL Server → Azure SQL / Azure Synapse

## Publications

{% assign articles = site.data.articles %}
{% if articles %}
<ul>
  {% for article in articles %}
  <li>
    <strong><a href="{{ article.url }}" target="_blank" rel="noopener">{{ article.title }}</a></strong>
    <br><em>{{ article.platform }}</em>
  </li>
  {% endfor %}
</ul>
{% endif %}

## Skills

| Category | Technologies |
|---|---|
| Databases | SQL Server 2008–2022, Azure SQL, PostgreSQL |
| AI / Search | FAISS, Azure AI Search, Vector datatypes |
| Cloud | Azure SQL, ADF, Synapse Analytics |
| Languages | T-SQL, Python, PowerShell |
| HA / DR | Always On AG, FCI, Log Shipping, Replication |
