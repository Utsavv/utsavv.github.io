---
layout: default
title: SQL Server Performance & Internals
permalink: /sql-server-performance/
description: Performance tuning and internal mechanics for SQL Server environments that demand reliability and speed.
keywords: SQL Server performance tuning, SQL Server internals
---

<section class="pillar-hero hero">
  <p class="eyebrow">Pillar: SQL Server Performance</p>
  <h1>Performance and internals playbooks for serious SQL Server teams.</h1>
  <p>Execution plans, indexing, TempDB, and locking strategies combined with real tuning case studies.</p>
  <div class="cta">
    <a class="button primary" href="/blog/">Read the performance library</a>
    <a class="button primary" href="https://1drv.ms/w/c/e7ee95718edb5e82/IQCCXtuOcZXuIIDn0jkAAAAAAV5g4qXEYIoaoTEOrYCkXyc?e=RiItJK" target="_blank" rel="noopener">Book a chat</a>
  </div>
</section>

<section class="section" id="execution-plans">
  <h2>Execution plans explained</h2>
  <p>Execution plans describe how SQL Server transforms a query into operators. I teach teams to read the estimated vs actual row counts, spot costly operators, and capture plan regressions from the plan cache.</p>
  <p>Visualizing missing index recommendations and wait stats alongside the plan surface helps prioritize tuning decisions.</p>
</section>

<section class="section" id="indexing-strategies">
  <h2>Indexing strategies</h2>
  <p>Indexes must be modern: filtered indexes for multi-tenant filters, columnstore indexes for analytics layers, and maintenance scripts that rebuild or reorganize based on fragmentation thresholds. Covering and included columns keep OLTP queries lean.</p>
  <p>Every change is validated with metrics so regressions are detected before they reach production.</p>
</section>

<section class="section" id="tempdb">
  <h2>TempDB architecture</h2>
  <p>TempDB contention kills throughput. I standardize on multiple data files (aligned to CPU), consistent auto-growth steps, optimized trace flags, and centralized monitoring so that allocation waits are rare.</p>
  <p>Changes ship with readouts from DMVs like `sys.dm_db_file_space_usage` and `sys.dm_os_wait_stats`.</p>
</section>

<section class="section" id="locking">
  <h2>Locking and blocking</h2>
  <p>Understanding isolation levels, optimistic concurrency, and lock escalation is essential. We prefer snapshot isolation for high-concurrency work and preemptively monitor blocking chains.</p>
  <p>Deadlock graphs feed into automation that captures statements + plans for quick remediation.</p>
</section>

<section class="section" id="case-studies">
  <h2>Real tuning case studies</h2>
  <p>Case studies show wait-time reductions, throughput gains, and plan stabilization. Metrics accompany every story so leaders see the before (+ after) numbers.</p>
  <p>These stories get retold in the supporting posts and in internal documentation.</p>
</section>

<section class="section" id="supporting-articles-performance">
  <h2>Supporting deep dives</h2>
  <ul>
    <li>Interpreting SQL Server execution plans in production</li>
    <li>Indexing strategy for multi-tenant tables</li>
    <li>TempDB sizing and contention diagnostics</li>
    <li>Lock escalation and mitigation in heavy OLTP</li>
    <li>Tracking wait stats growth over time</li>
  </ul>
  <p>Each of these posts will reference the architecture pillar and link back here to reinforce the performance narrative.</p>
</section>

<section class="section" id="faq">
  <h2>FAQ</h2>
  <div class="faq">
    <article>
      <h3>How do you approach execution plan regressions?</h3>
      <p>Capture plans before/after, compare estimated vs actual rows, and correlate wait stats to spot operators with exploding costs.</p>
    </article>
    <article>
      <h3>When should we add TempDB files or change auto-growth?</h3>
      <p>Monitor `PAGELATCH` waits, track file usage from the DMVs, and adjust files/auto-growth in a controlled rollout to avoid allocation stalls.</p>
    </article>
  </div>
</section>

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How do you approach execution plan regressions?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Capture plans before/after, compare estimated vs actual rows, and correlate wait stats to spot operators with exploding costs."
      }
    },
    {
      "@type": "Question",
      "name": "When should we add TempDB files or change auto-growth?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Monitor PAGELATCH waits, track file usage from the DMVs, and adjust files/auto-growth in a controlled rollout to avoid allocation stalls."
      }
    }
  ]
}
</script>
