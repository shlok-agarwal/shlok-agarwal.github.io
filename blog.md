---
layout: page
title: Blog
permalink: /blog/
---

# Blog

Welcome to my blog where I share insights about robotics, legged locomotion, and the journey of bringing advanced robotic systems from research to real-world deployment. Here you'll find technical deep-dives, industry perspectives, and lessons learned from years of working with cutting-edge robotic platforms.

> *Bridging the gap between robotics research and real-world deployment, one post at a time.*

---

## Latest Posts

{% for post in site.posts %}
### [{{ post.title }}]({{ post.url | relative_url }})
*{{ post.date | date: "%B %d, %Y" }}*

{{ post.excerpt | strip_html | truncatewords: 30 }}

{% endfor %}

---

*All opinions expressed in these posts are my own and do not necessarily reflect the views of my employer.*