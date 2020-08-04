# Best practice: URI-strategie linked-data-assets stedelijk water

## In het kort
Een **best practice** voor het identificeren van individuen in linked-data vorm binnen de discipline stedelijk water.

Gebaseerd op de [NTA 8035](https://www.nen.nl/NEN-Shop/Norm/NTA-80352020-nl.htm), zie hoofdstuk 7.7.1 .
Daarin worden de volgende bronnen aangehaald:
* [CEDR Interlink URI Strategie](https://www.roadotl.eu/static/media/INTERLINK_D4._Defining_the_Principles_9Okqubw.PDF), vanaf p. 84
* [Towards a NL URI Strategy](https://www.geonovum.nl/uploads/documents/D1-2013-09-19_Towards_a_NL_URI_Strategy.pdf) 
* Best Practices for Publishing Linked Data [[ld-bp]]
* Cool URIs for the Semantic Web [[cooluris]]

## Waarom
Beschrijft de reden waarom dit goed is om te doen

## Beoogd resultaat
Beschrijft het beoogde resultaat

## Implementatie

<div style="color:gray">Het "hoe": de implementatierichtingen, voorbeelden, concrete aanwijzingen etc. Het was de bedoeling bij de SDW-BP dat het 'waarom' en het 'beoogde resultaat' algemeen genoeg zijn om voorlopig overeind te blijven, terwijl wat beschreven staat onder 'mogelijke aanpak' veel concreter is, maar daardoor ook veranderlijker kan zijn en misschien ook vaker geactualiseerd moet worden.</div>

### Uitgangspunt: URI's van concepten in het GWSW Model

Om te verwijzen naar documentlocaties van GWSW-concepten gebruiken we:
https://{domain}/{type}/{version}/{filter}/{reference}

{domain} is het web-domein: voor de GWSW-Ontologie is {locatie}.gwsw.nl. Het subdomein {locatie} voor de ontologie is "data".

{type} is het soort resource: voor concepten / definities van een term is dat type "def". In de URI hoeft het type niet te worden opgenomen, het subdomein "data" verwijst impliciet naar het type "def".

{version} is de versie: voor deze GWSW ontologie is dat "2.0".

{filter} is het geldende filter ("view") op de GWSW ontologie: om alle concepten op te kunnen vragen geldt filter "Totaal".

{reference} is de verwijzing naar het specifieke concept:
Het hanteren van begrijpbare namen voor concepten is een gangbare RDF praktijk en ook voor het GWSW heel bruikbaar. We gaan uit van camelCase en CamelCase notatie van de namen voor respectievelijk de properties (starten met lowercase) en de klassen (starten met uppercase).

Een externe overstortput is een GWSW concept (klasse) en heeft in GWSW versie 1.5.1 de URI http://data.gwsw.nl/1.5.1/Totaal/ExterneOverstortput.
De breedte van een put is een attribuut en heeft de URI http://data.gwsw.nl/1.5.1/Totaal/breedtePut.







De unieke naam binnen het rioleringsstelsel
https://data.gwsw.nl/id/061674#b2ad189a-8c46-49f2-557ba07c49a2 rdfs:label “P123” . 

Een synoniem kan, GWSW 1.n kent skos:altLabel:
https://data.gwsw.nl/id/061674#b2ad189a-8c46-49f2-557ba07c49a2 skos:altLabel “bv te gebruiken voor oude kode INSP24442” .

Idem in een andere taal-context:
https://data.gwsw.nl/id/061674#b2ad189a-8c46-49f2-557ba07c49a2 skos:altLabel “gebrauch alter kode INSP24442”@de .



## Testen 
Beschrijft hoe je kan toetsen of de best practice inderdaad geïmplementeerd is in een specifieke omgeving.

## Relevante requirements
In het SDW-BP document staan geen use cases en requirements; deze waren al in een apart document opgenomen [[SDW-UCR]]. Onder dit kopje 'relevante requirements' wordt verwezen naar de voor deze best practice relevante requirements. 

## Baten
Het Data on the Web Best Practices [[dwbp]] document bevat een [bijlage](https://www.w3.org/TR/dwbp/#BP_Benefits) waarin een aantal baten worden beschreven die kunnen worden bereikt door het volgen van de best practices. Onder dit kopje 'baten' wordt dan verwezen naar de specifieke baten die worden gerealiseerd door deze specifieke best practice te volgen.
