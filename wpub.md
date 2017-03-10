---
layout: page
title: WPub
permalink: /wpub/
---
Môžete sa tu dozvedieť detaili o zadaniach z predmetu Webové publikovanie.  Čo bolo zámerom a ako som ich vypracoval.

<ul class="wepub-headers">
	{% for wepub in site.wepubs %}
	  <li><h2><a href="{{ wepub.url  | prepend: site.baseurl }}">{{ wepub.title }}</a></h2></li>
	{% endfor %}
</ul>