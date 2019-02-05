---
layout: page
title: Archive
---
<div class="message">
  This is the list of all post published so far
</div>

{% for post in site.posts %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}