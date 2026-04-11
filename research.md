---
layout: default
title: Research
---

<div class="cv-page">
  <h1 style="font-size:2rem; margin-bottom:0.5rem;">Research</h1>
  <p style="color:#4a4a4a; margin-bottom:2.5rem;">How people understand the systems they use — and how those systems should be designed with that in mind.</p>

  <div class="research-grid">
    {% assign ongoing = site.research | where: "ongoing", true %}
    {% assign past = site.research | where: "ongoing", false | sort: "sort_year" | reverse %}
    {% assign sorted = ongoing | concat: past %}
    {% for project in sorted %}
      <a href="{{ project.url | relative_url }}" class="research-card">
        <p class="card-years">{{ project.years }}</p>
        <p class="card-title">{{ project.title }}</p>
        <p class="card-summary">{{ project.summary }}</p>
        <div class="collaborator">{{ project.collaborator }}</div>
      </a>
    {% endfor %}
  </div>
</div>
