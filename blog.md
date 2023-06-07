---
layout: default 
title: Blog 
---
<h1>最近の落書き</h1>
<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{post.url}}">
        {{post.title}}
      </a>
      - {{post.date | date_to_string}}
    </h2>
    </li>
  {% endfor %}
</ul>

<br><br><br><br><br>
<h1>カテゴリー別</h1>
<br>

{% for category in site.categories %}
  <h1>{{category[0]}}</h1>
  <ul>
    {%for post in category[1]%}
      <li>
        <h2><a href="{{post.url}}">
          {{post.title}}
            </a>
          - {{post.date | date_to_string}}
        </h2>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
