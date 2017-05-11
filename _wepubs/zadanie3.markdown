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
		*{% highlight xsd %}
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
		{% endhighlight %}
		
		* ##### presentation 
			* je koreňový element prezentácie. Obsahuje názov prezentácie **headline** a aj podnadpis **subHeadline**. Ďalej obsahuje podrobnejšie informácie o prezentácii a slajdy.
		* ##### info
			* obsahuje **author**, ktorý obsahuje meno a priezvisko autora. Autorov môže byť maximálne 4. Odporúča sa pri väčšom počte autorov ako štvrtého uviesť **a kolektív**.