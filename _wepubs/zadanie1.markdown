---
layout: wepubs
title: Zadanie1
sub_title: Vytvorte webovú prezentáciu o sebe.
image_path:  jekyll-logo-black-red-transparent.png
---


* ### podstránky
	* Home
		* Úvod k stránke, čo obsahuje a načo je určená.
	* O mne
		* Ďalšie informácie o mne. Niečo z školy a niečo z voľného času.
	* Blog
		* Rôzne príspevky od bakalárky, cez dobrovoľníctvo po uvítací post.
	* Kontakt
	* WPub
		* Popis k zadaniam.
	* Posty a zadania z WPUB
* ### layout-y
	* page
		* používajú ho všetky hlavné stránky. Obsahuje názov stránky a časť určenú na obsah.
	* post
		* Obsahuje meta-dáta z príspevku, názov a na spodku šípky slúžiace na prepínanie medzi príspevkami. 
	* wepubs
		* Obsahuje na začiatku obrázok, ktorý ak nie je definovaný tak sa nahradí otáznikom. Ďalej je nadpis a časť so zadaním.
* ### premenné
	* použité v _config file 
		* Premenné použité vo footri a kontaktoch: title, email, author, description.
		* Umiestnenie obrázkov, využité pri každom načítavaní obrázku: image_base
	* použité v markdown súboroch
		* Názov príspevku: title
		* Podnázov alebo opis: sub_title
		* Cesta ku základnému obrázku príspevku: image_path
		* Dátum, ktorý chcem zobraziť ako metadáta príspevku: date
* ### kolekcie a dátové súbory
	* Dátové súbory používam na určenie fotiek, ktoré sa majú zobraziť v príspevkoch alebo na podstránkach. Je to jednoduchšie ako ich všetky vypisovať priamo na stránke, prípadne neskôr editovať. Obsahujú cestu k súboru a popis.
	* Kolekcie používam na zobrazenie zadaní z WPUB.
* ### filtre a tagy
	* Formátovanie dátumov pri zobrazení blogu: 
		* date_to_string, date_to_long_string
	* Rátanie počtu slov v príspevkoch:
		* number_of_words
	* Include v default layoute pre head, header a footer. Slúžia hlavne na prehľadnosť kódu a jednoduchšiu orientáciu pri upravovaní. 
	* Cyklus for: v header na vypísanie menu, na načítanie dátových súborov, vypísanie príspevkov blogu.
	* Podmienka if je použitá na to, aby odkaz na domovskú stránku nebol aj v pravom menu. 
	* Implementovaný je aj highlighter, ktorý je zatiaľ použitý v jednom z príspevkov o bakalárke. 
* ### pluginy
	* email-protect
		* využitý pri zobrazovaní emailov. Slúži na skrytie emailu pred spamovacími botmi. Zdroj: [https://github.com/vwochnik/jekyll-email-protect](https://github.com/vwochnik/jekyll-email-protect)
	* sitemap
		* Zdroj: [https://github.com/jekyll/jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap)

### Poznámky

* Ako inšpirácia mi poslúžila téma [polar bear](http://jekyllthemes.org/themes/polar-bear-theme/). Použil som z nej sass súbory. layout.scss je od 144 riadku úplne nový a predošlé riadky som upravoval. Syntax-highlighter som spravil nanovo podľa jekyll dokumentácie. Base a main som tiež pomenil. Inšpiroval som sa include-om častí head, header a navbar. Pluginy sú použité iba tie, čo som pridal ja. Myslím, teda, že okrem časti sass súborov a inšpirácia ohľadom struktúri priečinkov(ktorá je aj tak podľa dokumentácie) som nič iné nepoužil. 
