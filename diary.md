---
layout: default
permalink: /gunluk/
---

<div class="large-6 medium-6 hide-for-small columns adjust dn-odd-parent"></div>
<div class="large-6 medium-6 hide-for-small columns adjust dn-even-parent"></div>
<div class="small-12 columns adjust dn-single-column"></div>

{% for post in site.posts %}
  {% if post.is_diary_post == true %}
  <article class="large-12 medium-12 small-12 columns post dn-post-entry adjust dn-no-sps">
    <header class="post-header">
      <div class="large-12 medium-12 small-12 columns no-sp dn-date">
        <div class="dn-head-meta dn-date-share">
          <time datetime="{{ post.date | date: "%b %-d, %Y" }}">
          {% assign month = post.date | date: "%-m" %}
          {{ post.date | date: "%-d" }}
          {% case month %}
              {% when '1' %}Ocak
              {% when '2' %}Şubat
              {% when '3' %}Mart
              {% when '4' %}Nisan
              {% when '5' %}Mayıs
              {% when '6' %}Haziran
              {% when '7' %}Temmuz
              {% when '8' %}Ağustos
              {% when '9' %}Eylül
              {% when '10' %}Ekim
              {% when '11' %}Kasım
              {% when '12' %}Aralık
          {% endcase %}
          {{ post.date | date: "%Y" }}
          </time></div>
      </div>
    </header>
    <section class="large-12 medium-12 small-12 columns no-sp dn-post-excerpt">
      <h2 class="post-title"><a href="{{ post.url | prepend: site.baseurl }}" class="dn-post-link">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </section>
  </article>
  {% endif %}
{% endfor %}
