---
layout: wepubs
title: Zadanie3
sub_title: Zadanie 3 XML Schema XML XSL
image_path:
---



* ### Naším cieľom bolo
	* Analyzujte možnosti zápisu jednoduchej prezentácie v jazyku XML. Identifikujte základné súčasti prezentácie a navrhnite XML elementy pre ich označkovanie (metadátové, štrukturálne, inline). Dbajte na znovupoužiteľnosť a vyvarujte sa redundancií. Návrh elementov zrealizujte opísaním typu dokumentu pomocou vybraného jazyka (DTD, XSD, RELAX NG) spolu s vysvetlením účelu jednotlivých elementov. Vo vami navhrnutom jazyku vytvorte ukážkovú prezentáciu, ktorá bude demonštrovať možnosti tvorby prezentácií podľa definície typu dokumentu.

	* Navrhnite a vytvorte XSLT šablóny pre konverziu prezentácie z XML do XHTML+CSS a pre konverziu prezentácie z XML do PDF. Klaďte dôraz na znovupoužitie jednotlivých šablon pre viaceré výstupné formáty. Umožnite zadávanie parametrov transformácií.

	* opis typu dokumentu + opis účelu navrhnutých elementov - možnosť výberu (práve jedného) z variantov:
		* DTD (max 3 body)
		* XML Schema (max 4 body)
		* RELAX NG (max 4+1 bodov)
	* vytvorenie ukážkovej XML prezentácie demonštrujúcej možnosti definície typu dokumentu (max 2 body)
	* základný návrh XSL transformácií, ich vhodnosť, parametrizácia (max 3 body)
	* vytvorenie XSLT pre konverziu prezentácie z XML -> XHTML+CSS (max 3 body) 
		* každý slide bude v samostatnom XHTML súbore
	* vytvorenie XSLT pre konverziu prezentácie XML -> PDF (max 2 body)
	
	* #### Ako sme postupovali
	* Na začiatku sme identifikovali časti prezentácie. Určili si aké druhy slajdov budú dostupné, ako sa bude tvoriť úvodný slajd a obsah. Následne sme začali s tvorbou schémy.
* ### Opis typu dokumentu 
	* Pre vytvorenie opisu typu dokumentu sme použili XML Schema. Zaujala nás jej väčšia vyjadrovacia sila oproti DTD. Taktiež jej jednoduchosť a prehľadnosť.
	* #### Dôležité elementy
		* 
		```
			<xs:element name="presentation">
				<xs:complexType>
					<xs:sequence>
						<xs:element ref="headline"/>
						<xs:element ref="subHeadline" minOccurs="0"/>
						<xs:element ref="info"/>
						<xs:element ref="slide" minOccurs="0" maxOccurs="unbounded"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
		 ```
				
		
	* ##### presentation
		* je koreňový element prezentácie. Obsahuje názov prezentácie **headline** a aj podnadpis **subHeadline**. Ďalej obsahuje podrobnejšie informácie o prezentácii a slajdy.
		* ##### info
			* obsahuje **author**, ktorý obsahuje meno a priezvisko autora. Autorov môže byť maximálne 4. Odporúča sa pri väčšom počte autorov ako štvrtého uviesť **a kolektív**. Obsahuje **place**, tam môže používateľ zadať miesto konanie sa prezentácie. Má aj atribút hovoriaci o dátume prezentácie. Všetky dostupné informácie sa zobrazia na úvodnom slajde.
		* ##### slide
			* používateľ má na výber viacero druhov slajdov. 
			```
				<xs:element ref="bulletSlide"/>
				<xs:element ref="numberedSlide"/>
				<xs:element ref="imageSlide"/>
				<xs:element ref="columnSlide"/>
				<xs:element ref="themeSlide"/>
				<xs:element ref="sourcesSlide"/>
				<xs:element ref="endingSlide"/>
			```
			* **bulletSlide** je bežný odrážkový slajd. Obsahuje nadpis a odrážky v rozsahu 1 - 11. Veľkosť písma a riadkovania sa mení v závislosti od počtu odrážok. To isté platí aj pre číslované odrážky, ktoré sú k dizpozícii v **numberedSlide**. 
			* **imageSlide** slúži n avloženie obrázku a jeho popisu. Umožňuje zadať aj rozmery obrázku. 
			* **themeSlide** je slajd na uvedenie väčšieho celku alebo na ukázanie časti témy. Obsahuje nadpis a podnadpis. Podobný slajd je **endingSlide**, ktorý má naviac vo výslednom zobrazení pridaných autorov.
			* **sourcesSlide** slúži na uvedenie bibliografie prezentácie.  
			
* ### Ukážková prezentácia
	* vytvorili sme ukážkovú prezentáciu. Obsahuje každý druh slajdu, ktorý je dostupný, rôzny počet odrážok na slajdoch, číslovaný slajd a aj slajd s dvoma stĺpcami. 
* ### Návrh XSLT pre konverziu do XHTML + CSS
	* podarilo sa nám vytvoriť transformáciu na XHTML. Aby sme mohli generovať slajdy do samostatných súborov sme použili verziu xslt 2.0. Na začiatku načítame parametre, ktoré určujú, či bude číslovanie na slajdoch a v akej forme a v akej farebnej schéme bude výsledná prezentácia. Vygeneruje sa úvodný slajd. Následne ak prezentácia obsahuje slajdy sa vygeneruje obsah prezentácie. Obsah obsahuje odkazy na slajdy a teda je možné sa priamo dostať na žiadaný slajd. 
	```
		<body>
			<header>
				<h1><xsl:value-of select="presentation/headline"/></h1>
			</header>
			<div class="title_page">
				<div class="info">
					<p class="meta_info"><xsl:value-of select="presentation/info/place"/><br/><xsl:value-of select="presentation/info/@dateOfPres"/></p>
					<p class="authors">
						<xsl:for-each select="presentation/info/author">
								<xsl:value-of select="name"/>&#xA0;<xsl:value-of select="surname"/>,
						</xsl:for-each>
					</p>
				</div>
			</div>
			<footer>
				<xsl:if test="$page_num &gt; 0">
					<a href="0.html" class="next_link">&gt;</a> 
				</xsl:if>
			</footer>
		</body>
	```
	* následne v cykle for sa prejdú všetky slajdy, na ktoré sa aplikujú rozloženia (ag. template). 
	* CSS súborov je definovaný priamo v XSL súbore z dôvodu zmeny na základe premených. Sme si vedomí, že by sa to dalo meniť aj priamo pri elementoch nastavovaním atribútov, ale radšej máme CSS na jednom mieste. Veľkosť textu odrážok a ich riadkovanie sa určuje pomocou predefinovaných tried v CSS. Pred vypísaním odrážok sa podľa ich počtu určí aká trieda bude priradená ich rodičovskému elemetu. Ukážku môžete vidieť nižšie. 
	
	```
	<xsl:variable name="line_num" select="count(plainText)"/>
		<xsl:attribute name="class">
		  <xsl:choose>
		        <xsl:when test="$line_num &gt; 8">
		        	<xsl:value-of select="normalize-space('font_xsm')" />
		        </xsl:when>
		        <xsl:when test="$line_num &gt; 6">
		        	<xsl:value-of select="normalize-space('font_sm')" />
		        </xsl:when>
		        <xsl:when test="$line_num &gt; 4">
		        	<xsl:value-of select="normalize-space('font_md')" />
		        </xsl:when>
		        <xsl:otherwise>
		        	<xsl:value-of select="normalize-space('font_lg')" />
		        </xsl:otherwise>
		    </xsl:choose>
		</xsl:attribute>
	```
	
	* v dolnej časti slajdu sa nachádzajú šípky slúžiace na navigáciu medzi slajdami. Pod nimi je voliteľné číslovanie strán. 

* ###	Konverzia XML na PDF
	* Z dôvodu časovej tiesene sme nestihli dokončiť XSLT transformáciu a preto ju neprezentujeme.

