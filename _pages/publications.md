---
title: "Publications"
permalink: /publications/
author_profile: true
---

<p class="pub-legend"><span class="pub-legend__star">*</span> Corresponding author &nbsp;·&nbsp; † Joint first authorship</p>

{% if author.googlescholar %}
<p class="pub-scholar">You can also find my articles on <a href="{{ author.googlescholar }}">my Google Scholar profile</a>.</p>
{% endif %}

{% include base_path %}

{% comment %} Newest-first by filename. Online-first papers (online_first: true)
   are pinned to a dedicated group at the very top; the rest are grouped by year
   read from the filename (2025-17.md -> "2025"). {% endcomment %}
{% assign pubs = site.publications | sort: 'slug' | reverse %}

{% comment %} ---- online-first / in-press group ---- {% endcomment %}
{% assign of_list = pubs | where: "online_first", true %}
{% if of_list and of_list.size > 0 %}
  <h2 class="pub-year pub-year--press">In press / Online first</h2>
  <div class="pub-year-group">
    {% for post in of_list %}
      {% include publication-card.html %}
    {% endfor %}
  </div>
{% endif %}

{% comment %} ---- year-grouped published papers ---- {% endcomment %}
{% assign current_year = "" %}
{% for post in pubs %}
  {% unless post.online_first %}
    {% assign fname = post.path | split: "/" | last %}
    {% assign post_year = fname | slice: 0, 4 %}
    {% if post_year != current_year %}
      {% unless current_year == "" %}</div>{% endunless %}
      <h2 class="pub-year" id="year-{{ post_year }}">{{ post_year }}</h2>
      <div class="pub-year-group">
      {% assign current_year = post_year %}
    {% endif %}
    {% include publication-card.html %}
  {% endunless %}
{% endfor %}
{% unless current_year == "" %}</div>{% endunless %}
