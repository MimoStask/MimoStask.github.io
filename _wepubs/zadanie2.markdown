---
layout: wepubs
title: Zadanie2
sub_title: Spracovanie vybraného dokumentu (ideálne bakalárskeho projektu) z pôvodného ľubovoľného (Word, OpenOffice, LaTeX, …) formátu do formátu DocBook a vygenerovanie cieľového tvaru v PDF.
image_path:
---



* ### členenie textu,
	* text je členený na kapitoli a podkapitoli... Obsahuje prílohu, obsah, zoznam obrázkov a tabuliek.  	
* ### zvýraznenie slov, zvýraznenie členenia textu odrážkami alebo číslovaním,
	* kurzíva je použitá na strane 17-18, na zvýraznenie názvov častí faktúri.
	* odrážky na stranách 17, 19
* ### odkazy na iné časti vlastného dokumentu,
	* V úvode sú odkazi na časti dokumentu napríklad: V prvej časti, položky faktúry, prehľad systémov
* ### zoznam použitej literatúry a zdrojov vrátane ich citácie v texte,
	* citácia v texte je tvorená pomocou odkazov na id zdrojov napríklad
	{% highlight xml %}
	<xref linkend="bib.29cite" />
	{% endhighlight %}
* ### vloženie obrázku a tabuliek, odkazy na ne v texte; zoznam obrázkov a tabuliek v úvode alebo závere textu,
	* pre vytvorenie zoznamu obrázkov a tabuliek bolo nutné upraviť nasledujúcu časť kódu v thesis.xsl
	{% highlight xml %}
	<xsl:param name="generate.toc">
		book      title,toc,figures,tables
	</xsl:param>	
	{% endhighlight %}
* ### vytvorenie registra pojmov
	* na vytvorenie registra pojmov je použitý IndexTerm
* ### ďalšie úpravy xsl
	* v atribúte normal.para.spacing sme pridali riadok pre zväčšenie riadkovania na 1,5em
	{% highlight xml %}
	<xsl:attribute name="line-height">1.5em</xsl:attribute>
		{% endhighlight %}
* odstránili sme načítavanie nedostupného dokumentu "kizik.pdf" 
{% highlight xml %}
<fo:block xmlns:fo="http://www.w3.org/1999/XSL/Format" space-before="12pt" space-after="1cm" text-align="center">
    <fo:external-graphic src="url(kizi.pdf)" width="2cm" content-width="scale-to-fit"/>
</fo:block>
{% endhighlight %}
