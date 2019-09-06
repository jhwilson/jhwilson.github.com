---
layout: full-width
title: home
order: 1
# Note that this index page uses a full-width layout!
---


Greetings, I am **Justin H. Wilson** a postdoctoral researcher at [Rutgers](https://www.physics.rutgers.edu) with Prof. Jed Pixley.
I do theoretical research on cold atomic and condensed matter systems.

<script type="text/javascript">
<!--
var arxiv_authorid = "wilson_j_3";
var arxiv_format = "arxiv";
var arxiv_includeComments = 0;
var arxiv_includeSubjects = 0;
//--></script>
<script type="text/javascript" src="https://arxiv.org/js/myarticles.js"></script>

<div class="row">

  <div class="column">
  <h1 class="content-listing-header sans">Quantum Observations</h1>
  <ul class="content-listing ">
    {% for post in site.posts %}
        <li class="listing">
          <hr class="slender">
          <a href="{{ post.url | prepend: site.baseurl }}"><h3 class="contrast">{{ post.title }}</h3></a>
          <br><span class="smaller">{{ post.date | date: "%B %-d, %Y" }}</span>  <br/>
          <!-- <div>{{ post.excerpt }}</div> -->
        </li>
    {% endfor %}
  </ul>

  </div>

  <div class="column">
    <div id="arxivfeed"></div>
  </div>
</div>
