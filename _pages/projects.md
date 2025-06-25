---
layout: page
title: Projects
permalink: /projects/
description: Interesting things I've worked on over the past two years
nav: true
nav_order: 4
display_categories: [course, research]
horizontal: false
---

<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
    <h2 class="category">{{ category }}</h2>
    {%- assign categorized_projects = site.projects | where: "category", category -%}
    {%- assign sorted_projects = categorized_projects | sort: "importance" %}
    <ul>
      {%- for project in sorted_projects -%}
        <li>
          <strong>{{ project.title }}</strong>
          {%- if project.description %}
            – {{ project.description }}
          {%- endif %}
        </li>
      {%- endfor %}
    </ul>
  {%- endfor %}
{%- else -%}
  <!-- Display projects without categories -->
  {%- assign sorted_projects = site.projects | sort: "importance" -%}
  <ul>
    {%- for project in sorted_projects -%}
      <li>
        <strong>{{ project.title }}</strong>
        {%- if project.description %}
          – {{ project.description }}
        {%- endif %}
      </li>
    {%- endfor %}
  </ul>
{%- endif -%}
</div>
