---
layout: page
title: O mne
permalink: /about/
---


<img class="about-foto"  src="/assets/images/me.JPG" alt="my portrait" />


Študujem na FIIT STU v BA. Som v 3. ročníku bakalárskeho štúdia. Na škole sme prešli veľa vecí a najviac z nich ma baví programovanie a softvérové inžinierstvo.

### Jazyky, čo aspoň trochu ovládam:

* C
* JAVA
* HTML, CSS, JS, PHP
* Bootstrap, Laravel
* Postgres, MySQL
* UML 2.0
* GIT
* Certificate CCNA 1 2016

### Viac o mne

Vo voľnom čase pôsobím aj ako animátor v saleziánskom stredisku na Mamateyovej v Petržalke. Ale viac o tom sa môžete dočítať v blogu.


<ul class="photo-gallery">
{% for photo in site.data.about_photos %}
  <li>
   		<img src="{{ site.image_base }}{{ photo.image_path }}" alt="{{ photo.title}}" />
  </li>
{% endfor %}
</ul>

### Ešte zopár podrobností 
* Autor: Mimo Stask
* Github: https://github.com/MimoStask
* Portfolio: https://mimostask.github.io/