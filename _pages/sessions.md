---
layout: page
permalink: /sessions/
title: Sessions
description: I've taken a lot of sessions, mostly in my year-and-a-half stint as head of mathematics club. You can find slides/resources for most of them below!
nav: true
nav_order: 5
---

<!-- {% include video.html path="assets/video/pexels-engin-akyurt-6069112-960x540-30fps.mp4" class="img-fluid rounded z-depth-1" controls=true %}

{% include video.html path="assets/video/pexels-engin-akyurt-6069112-960x540-30fps.mp4" class="img-fluid rounded z-depth-1" controls=true %}

{% include video.html path="assets/video/pexels-engin-akyurt-6069112-960x540-30fps.mp4" class="img-fluid rounded z-depth-1" controls=true %} -->

<!-- {% include video.html path="assets/maths_club/7 Bridges of Konigsberg.mp4" class="img-fluid rounded z-depth-1" controls=true %} -->

### Mathematics Club Sessions

{% for file in site.static_files %}
  {% if file.path contains "maths_club" -%}
     * [{{ file.basename }}]({{ site.baseurl }}{{ file.path }})
  {%- endif %}
{% endfor %}

#### Course Presentation
These include my presentations as part of course projects.

* [Approximation Algorithms Paper Presentation](/assets/pdf/Approximation Algorithms Course Presentation.pdf)