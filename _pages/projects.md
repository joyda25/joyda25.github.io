---
layout: page
title: Project
permalink: /projects/
description: 
nav: true
nav_order: 4
display_categories: [work, fun]
horizontal: false
---
<!-- pages/projects.md -->
<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  {% assign categorized_projects = site.projects | where: "category", category %}

  <!-- Filter specific projects -->
  {% assign filtered_projects = categorized_projects | where_exp: "project", "project.filename == '1_project.md' or project.filename == '2_project.md' or project.filename == '3_project.md'" %}
  {% assign sorted_projects = filtered_projects | sort: "importance" %}
  

  
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}
  {% endif %}
</div>