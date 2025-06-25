---
layout: page
permalink: /misc/
title: Miscellaneous
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

#### Course Presentations
These include my presentations as part of course projects.

* [Advanced Graph Algorithms](assets/pdf/Advanced_Graph_Algorithms_Paper_Presentation.pdf)
* [Lempel-Ziv Coding: Information Theory](assets/pdf/Information_Theory_Presentation.pdf)
* [Approximation Algorithms Paper Presentation](assets/pdf/Approximation_Algorithms_Paper_Presentation.pdf)
