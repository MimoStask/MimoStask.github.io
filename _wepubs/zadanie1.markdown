---
layout: wepubs
title: Zadanie1
sub_title: Vytvorte webovú prezentáciu o sebe.
image_path:  octojekyll.png
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
		* používajú ho všetky hlavné stránky. Obsahuje názov stránky a časť určenú na content.
	* post
		* Obsahuje meta dáta z príspevku, názov a na spodu šípky slúžiace na prepínanie medzi príspevkami. 
	* wepubs
		* Obsahuje na začiatku obrázok, ktorý ak nie je definovaný tak sa nahradí defaultným. Ďalej je nádpis a časť so zadaním.
* ### premenné
	* použité v _config file 
		* Premenné použité v footri a kontaktoch: title, email, author, description.
		* Umiestnenie obrázkov, využité pri každom načitávaní obrázku: image_base
	* použité v markdown súboroch
		* Názov príspevku: title
		* Podnázov alebo opis: sub_title
		* Cesta ku základnému obrázku príspevku: image_path
		* Dátum, ktorý chcem zobraziť ako metadáta príspevku: date
* ### kolekcie a dátové súbory
	* Dátové súbory používam na určenie fotiek, ktoré sa majú zobraziť v príspevkoch alebo na podstránkach. Je to jednoduchšie ako ich všetky vypisovať priamo na stránke, prípadne neskôr editovať. Obsahuju cestu k súboru a popis.
	* Kolekcie používam na zobrazenie zadaní z WPUB.
* ### filtre a tagy
	* Formátovanie dátumov pri zobrazení bolgu: 
		* date_to_string, date_to_long_string
	* Rátanie početu slov v príspevkoch:
		* number_of_words
	* Includ v default layoute pre head, header a footer. Slúžia hlavne na prehľadnosť kódu a jednoduchšiu orientáciu pri upravovaní. 
	* Cyklus for: v header na vypísanie menu, na načítanie dátových súborov, vypísanie príspevkov blogu.
	* Podmienka if je použitá na to, aby link na domovskú stránku nebol aj v pravom menu. 
	* Implementovaný je aj highlighter, ktorý je zatiaľ použitý v jednom z príspevkov o bakalárke. 
* ### pluginy
	* email-protect
		* využitý pri zobrazovaní emailov. Slúži na skrytie emailu pred spamovacími botmi. Zdroj: [https://github.com/vwochnik/jekyll-email-protect](https://github.com/vwochnik/jekyll-email-protect)
	* sitemap
		* Zdroj: [https://github.com/jekyll/jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap)

