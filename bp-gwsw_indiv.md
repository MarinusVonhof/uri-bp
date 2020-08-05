# URI-strategie linked-data-assets stedelijk water

## In het kort
<div style="color:gray;font-size:0.8em;">*Beschrijving van de best practice in iets langere bewoordingen*</div>
Een **best practice** voor het identificeren van individuen in linked-data vorm binnen de discipline stedelijk water.

Gebaseerd op het **Gegevenswoordenboek Stedelijk Water (GWSW)** zie [data.gwsw.nl](https://data.gwsw.nl)  
*en*  
Gebaseerd op de [NTA 8035](https://www.nen.nl/NEN-Shop/Norm/NTA-80352020-nl.htm), zie hoofdstuk 7.7.1 . 
Daarin worden de volgende bronnen aangehaald:
* [CEDR Interlink URI Strategie](https://www.roadotl.eu/static/media/INTERLINK_D4._Defining_the_Principles_9Okqubw.PDF), vanaf p. 84
* [Towards a NL URI Strategy](https://www.geonovum.nl/uploads/documents/D1-2013-09-19_Towards_a_NL_URI_Strategy.pdf) 
* Best Practices for Publishing Linked Data [[ld-bp]]
* Cool URIs for the Semantic Web [[cooluris]]

## Waarom
<div style="color:gray;font-size:0.8em;">*Beschrijft de reden waarom dit goed is om te doen*</div>

Het Gegevenswoordenboek Stedelijk Water (GWSW) wordt breed toegepast voor stedelijk water beheer in Nederland. Het GWSW is een ontologie, een speciale datastructuur die systemen en processen op het gebied van stedelijk water beschrijft. Het is een open datastandaard volgens het linked data principe die door Stichting RIONED namens de sector is ontwikkeld. Het is onderdeel van het Semantisch Web en is gemodelleerd in RDF/RDFS/OWL-2. 

Meer dan 80 gemeenten hebben al datasets opgebouwd conform het GWSW en gepubliceerd op de GWSW Server. Die datasets bevatten de assets en activiteiten op het gebied van stedelijk water. Die assets bestaan veelal uit putten en leidingen, ze worden in het algemeen "individuen" genoemd. Het verwijzen naar individuen met URI’s is essentieel binnen het linked-data principe, zeker nu er meer linked-data platforms verschijnen en de GWSW datasets steeds breder worden toegepast.

Een uniforme URI-strategie voor individuen in de "bebouwde omgeving" ontbreekt nog. 

## Beoogd resultaat
<div style="color:gray;font-size:0.8em;">*Beschrijft het beoogde resultaat*</div>

We willen komen tot een uniforme URI-strategie voor individuen in de bebouwde omgeving, om te beginnen met stedelijk water. Zodanig dat elk te onderscheiden individu met de URI uniek geïdentificeerd wordt. 

## Implementatie

<<<<<<< HEAD
<div style="color:gray;font-size:0.8em;">*Het "hoe": de implementatierichtingen, voorbeelden, concrete aanwijzingen etc. Het was de bedoeling bij de SDW-BP dat het 'waarom' en het 'beoogde resultaat' algemeen genoeg zijn om voorlopig overeind te blijven, terwijl wat beschreven staat onder 'mogelijke aanpak' veel concreter is, maar daardoor ook veranderlijker kan zijn en misschien ook vaker geactualiseerd moet worden.*</div>

**URI's van individuen binnen de discipline stedelijk water**

In de URI wordt de eigenaar van de gegevens (gemeente, samenwerkingsregio, waterschap, provincie) onderscheiden.
De algemene opbouw van de URI is:

&nbsp;&nbsp;&nbsp;**https://{domain}/{type}/{location}#{reference}** *(http wordt omgeleid naar https)*

* {domain}: Identiek aan het GWSW-model (data.gwsw.nl, zie requirements)
* {type}: Het betreft een individual, dus is het type een identifier "id".
* {location}: De organisatie/eigenaar/beheerder van het individu. Voor het organisatienummer (het identificeren van een lokaal pad) wordt conform de URI-strategie van het Digitaal Stelsel Omgevingswet de CBS-systematiek gehanteerd. Dit is de code van de overheidslaag (01 rijk, 02 uitvoeringsorgaan, 03 provincie, 04 waterschap, 05 gemeenschappelijke regeling, 06 gemeente) gevolgd door de viercijferige CBS-code van de overheidsinstelling. Voor bijvoorbeeld de gemeente Roosendaal betekent dit de code "0601674".
* {reference}: Als URL-fragment, de identificatie van het object (bijvoorbeeld een GUID).

<div class="note" title="Andere bronhouder">
Eigenaars van de stedelijk water voorzieningen zijn niet altijd in de overheidslaag onder te brengen, denk aan terreinriolering. Daarvoor zal een extra code nodig zijn.
</div>

<div class="example"><div class="example-title marker">De URI naar een specifieke rioolput in gemeente Roosendaal wordt daarmee:</div>
https://data.gwsw.nl/id/061674#b2ad189a-8c46-49f2-557ba07c49a2 
</div>

Het identificatiedeel van het individu wordt als fragment genoteerd, een paragraaf binnen het "bronhouder-document".
De individuen worden volledig beschreven in de GWSW-dataset (zijn daar al gedocumenteerd). De eigenaar van het individu kan wijzigen, bijvoorbeeld bij een gemeentelijke herindeling. Ook de bronhouder-code (en de URI van het individu) wijzigt in zo'n geval.

<div class="example"><div class="example-title marker"><span>Prefixes in een dataset</span></div>
<p>@prefix gwsw: &lt;https://data.gwsw.nl/1.5.1/totaal/&gt; .</p>
<p>@prefix indiv: &lt;https://data.gwsw.nl/id/061674#&gt; .</p>
</div>

De assets van elke bronhouder (gemeente, waterschap) staan in een aparte dataset (repository, SPARQL-endpoint). De prefix indiv: is dan bruikbaar voor alle in de dataset opgenomen individuen.

<div class="example"><div class="example-title marker"><span>De unieke naam binnen het rioleringsstelsel</span></div>
<p>indiv:b2ad189a-8c46-49f2-557ba07c49a2 rdfs:label “P123” . </p>
</div>

<div class="example"><div class="example-title marker"><span>Een synoniem kan, GWSW 1.n kent skos:altLabel</span></div>
<p>indiv:b2ad189a-8c46-49f2-557ba07c49a2 skos:altLabel “bv te gebruiken voor oude code INSP24442”.</p>
</div>

<div class="example"><div class="example-title marker"><span>Idem in een andere taal-context</span></div>
<p>indiv:b2ad189a-8c46-49f2-557ba07c49a2 skos:altLabel “gebrauch alter kode INSP24442”@de .</p>
</div>

<div class="example"><div class="example-title marker"><span>Typering van het individu</span></div>
<p>indiv:b2ad189a-8c46-49f2-557ba07c49a2	rdf:type gwsw:ExterneOverstortput .</p>
</div>

<div class="note" title="Ter overweging: Alternatieve notaties"> <!-- afgeleide titeltekst werkte niet voor remarks -->

BGT-ID
Zie de <a href="https://docs.geostandaarden.nl/imgeo/catalogus/bgt/">Basisregistratie Grootschalige Topografie</a>. De BGT-objectidentificatie (object-ID) hanteert de richtlijnen van NEN3610:2011. Aan elk object wordt een uniek identificatienummer toegekend, dat uit twee delen bestaat: een namespace en een identificatiecode. Zolang het object bestaat, mag dit ID niet ver­an­deren. Vanwege de samenhang tussen de BGT en IMGeo wordt één notatiewijze voor het object-ID voorgeschreven.

Een BGT-ID bestaat uit de namespace <b>NL.IMGeo</b> (Landcode + Sectormodel) gevolgd door een code voor de <b>Bronhouder</b> (5 posities) en een <b>UUID</b> (32 cijfers).
De notatiewijze voor het put-voorbeeld wordt dan:

Voor de discipline stedelijk water (zeker voor riolering) zijn de BGT-ID's niet over te nemen. Ondergrondse leidingen ontbreken in de BGT en van de putten zijn alleen de deksels in de BGT vastgelegd.

</div>

<div class="example"><div class="example-title marker"><span>De BGT-ID van de voorbeeld-put</span></div>
<p>NL.IMGeo:061674.b2ad189a-8c46-49f2-557ba07c49a2</p>
</div>

=======
>>>>>>> 2ff181a101b62b8fdd2a599b94f1910688c86592
## Testen 
<div style="color:gray;font-size:0.8em;">*Beschrijft hoe je kan toetsen of de best practice inderdaad geïmplementeerd is in een specifieke omgeving.*</div>

## Relevante requirements
<div style="color:gray;font-size:0.8em;">*In het SDW-BP document staan geen use cases en requirements; deze waren al in een apart document opgenomen [[SDW-UCR]]. Onder dit kopje 'relevante requirements' wordt verwezen naar de voor deze best practice relevante requirements.*</div>

### URI-strategie voor concepten in het GWSW Model

Om te verwijzen naar documentlocaties van GWSW-concepten gebruiken we:
&nbsp;&nbsp;&nbsp;**https://{domain}/{type}/{version}/{filter}/{reference}** *(http wordt omgeleid naar https)*

* {domain} is het web-domein: voor de GWSW-Ontologie is dit {locatie}.gwsw.nl. Het subdomein {locatie} voor de ontologie is "data".
* {type} is het soort resource: voor concepten / definities van een term is dat type "def". In de URI hoeft het type niet te worden opgenomen, het subdomein "data" verwijst impliciet naar het type "def".
* {version} is de versie: deze meest recente versie van de GWSW ontologie is "1.5.1".
* {filter} is het geldende filter ("view") op de GWSW ontologie: om alle concepten op te kunnen vragen geldt filter "Totaal".
* {reference} is de verwijzing naar het specifieke concept:
Het hanteren van begrijpbare namen voor concepten is een gangbare RDF praktijk en ook voor het GWSW heel bruikbaar. We gaan uit van camelCase en CamelCase notatie van de namen voor respectievelijk de properties (starten met lowercase) en de klassen (starten met uppercase).

Een externe overstortput is een GWSW concept (klasse) en heeft in GWSW versie 1.5.1 de URI https://data.gwsw.nl/1.5.1/Totaal/ExterneOverstortput.
De breedte van een put is een attribuut en heeft de URI https://data.gwsw.nl/1.5.1/Totaal/breedtePut.

### Datasets opbouwen conform GWSW-OroX definitie
Zie het document [GWSW-OroX Bestandsopbouw](https://apps.gwsw.nl/doc/GWSW.orox%20Beschrijving.pdf)

### Dataset via website op de GWSW Server publiceren
Zie de website met [GWSW Applicaties](https://apps.gwsw.nl)

### Dataset via GWSW API op de GWSW Server publiceren
Zie de [API Specificatie](https://apps.gwsw.nl/item_redoc) 

## Baten
<div style="color:gray;font-size:0.8em;">Het Data on the Web Best Practices [[dwbp]] document bevat een [bijlage](https://www.w3.org/TR/dwbp/#BP_Benefits) waarin een aantal baten worden beschreven die kunnen worden bereikt door het volgen van de best practices. Onder dit kopje 'baten' wordt dan verwezen naar de specifieke baten die worden gerealiseerd door deze specifieke best practice te volgen.*</div>
