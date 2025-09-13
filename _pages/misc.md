---
layout: page
permalink: /misc/
title: Miscellaneous
nav: true
nav_order: 6
---

<!-- {% include video.html path="assets/video/pexels-engin-akyurt-6069112-960x540-30fps.mp4" class="img-fluid rounded z-depth-1" controls=true %}

{% include video.html path="assets/video/pexels-engin-akyurt-6069112-960x540-30fps.mp4" class="img-fluid rounded z-depth-1" controls=true %}

{% include video.html path="assets/video/pexels-engin-akyurt-6069112-960x540-30fps.mp4" class="img-fluid rounded z-depth-1" controls=true %} -->

<!-- {% include video.html path="assets/maths_club/7 Bridges of Konigsberg.mp4" class="img-fluid rounded z-depth-1" controls=true %} -->

### Mathematics Club Sessions

I am the founder and was the head of Mathematics Club, Centre for Innovation, at IIT Madras. In my year-and-half stint, I had conducted fun and engaging sessions (mostly to undergrads) and you can find the links to some of them below. Some of the slides were made using [Manim](https://www.manim.community/).

{% for file in site.static_files %}
  {% if file.path contains "maths_club" -%}
     * [{{ file.basename }}]({{ site.baseurl }}{{ file.path }})
  {%- endif %}
{% endfor %}

#### Course Presentations

These include my presentations as part of course projects.

* [Lempel-Ziv Coding: Information Theory]({{ '/assets/pdf/Information_Theory_Presentation.pdf' | relative_url }})

* [Advanced Graph Algorithms Paper Presentation]({{ '/assets/pdf/Advanced_Graph_Algorithms_Paper_Presentation.pdf' | relative_url }})

* [Approximation Algorithms Paper Presentation]({{ '/assets/pdf/Approximation_Algorithms_Paper_Presentation.pdf' | relative_url }})

#### Quizzing

I participate in Quizzes on world knowledge occassionally. I consider this an opportunity to appreciate world art, culture, literature and science. I have also set quizzes for the Bombay Quiz Club and IIT Madras.