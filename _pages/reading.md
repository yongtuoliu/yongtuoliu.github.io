--- 
layout: archive 
title: "Reading" 
permalink: /reading/ 
author_profile: true 
--- 
{% include base_path %} 
{% for post in site.reading %} 
    {% include archive-single.html %} 
{% endfor %}
