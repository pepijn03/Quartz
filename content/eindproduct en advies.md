---
title: Eindproduct en advies
tags:
---
# Eindproduct
Om mijn stage af te sluiten is het belangrijk om goed te beschrijven wat ik precies gemaakt om een duidelijk beeld te schetsen van mijn eindproduct. Daarnaast wil ik ook een stukje advies geven over waar je naar zou kunnen kijken als je dit project door wilt gaan zetten of als je een soortgelijk project wil gaan doen. Het einddoel van dit project was een proof of concept en zal dus nog geen compleet product zijn.

## Onderdelen van het eindproduct
Er zijn een paar manieren waarop ik wil laten zien wat ik gemaakt heb dit semester. Eerst wil ik een toer geven door de applicatie om duidelijk de functionaliteiten te laten zien door middel van screenshots. Daarna wil ik nog wat dieper in gaan op hoe de applicatie nu uiteindelijk in elkaar zit. Dit zal wel ver overeen komen met hoe ik het gedefinieerd heb in het [[software-architectuur |software ontwerp,]] maar graag zou ik nog wat kleine stukjes code willen belichten die los staan van het architectuur ontwerp. Dit zal vooral gaan over de Python Flask API waarmee ik via een LLM teksten kan genereren. 

## Toer van applicatie
Om goed duidelijk te laten zien wat de functionaliteiten van mijn eindproduct zijn ga ik stap voor stap een tour geven door de applicatie. 

### Homepage
Het eerste wat je ziet wanner je een website bezoekt is de homepagina. Dit is de plek van waar je kan navigeren naar wat je nodig hebt. Ik heb er voor gekozen om hier een korte welkom bericht te plaatsen en een overzicht te laten zien van alle tools in de toolbox

![[Homepage.png]]

### Detail pagina
vanuit de homepagina klik je een tool aan en dan kom je op de detail pagina. Op deze pagina ga je echt de tool gebruiken en/of een embedding aanmaken. Op de pagina gebruik ik de naam context als alias voor embedding, omdat ik niet verwacht dat iedereen weet wat een embedding inhoudt.

![[details-page.png]]

### Embedding aanmaken
Als je een context/embedding wilt aanmaken doe je dat via de detail pagina van een tools. De embeddings zijn wel beschikbaar voor alle tools, dit leek mij handiger dan het afschreiden per tool voor wanneer je een embedding op meerdere tools wilt gebruiken.

![[embeddings.png]]

### Ideeën genereren
Een van de Tools in de toolbox is de ideeën doos. Hier kan je op basis van bestanden zoals een brandstory een lijstje met ideeën genereren voor een bepaalde uitwerking als je deze en het product van de klant invoert.

![[Pasted image 20240103130621.png]]

### Persona's genereren



## LLM API


# Advies
Stel dat er verder gebouwd zou moeten worden op mijn eindproduct of dat er een zelfde soort project gedaan gaat worden, zijn er een paar punten belangrijk om mee te nemen in dat project. 

## Belangrijke punten
Op de manier zoals de applicatie nu staat is het erg makkelijk om nieuwe tools toe te voegen aan de applicatie. Dit zou ervoor moeten zorgen dat wanneer er nieuwe use cases voor bedacht worden, dat die meteen doorgevoerd kunnen worden aan de applicatie. Er zitten wel een paar limitaties aan wat er allemaal makkelijk toegevoegd kan worden. Momenteel wordt de context verdeeld in stukjes, het is dus moeilijk om een context als geheel gebruiken. Daarnaast is het systeem nu ingericht op alleen maar het generen van tekst, het zou dus geen afbeeldingen kunnen generen. Wel is het mogelijk om code te generen of svg bestand. Svg bestanden zijn wel mogelijk doordat dit eigenlijk een stukje code is wat omgezet wordt naar een plaatje maar geen plaatje zelf is.

Tijdens deze stage heb ik erg veel onderzoek gedaan naar open source LLMs. Uiteindelijk was de kwaliteit van deze modellen niet goed genoeg om te gebruiken, maar dat is alleen op dit moment. Ik neem aan dat deze modellen verder ontwikkeld gaan worden in de toekomst. Het zal dus op een gegeven moment weer waardevol worden om naar open source alternatieven te gaan kijken in plaats van OpenAI's ChatGPT te blijven gebruiken. Natuurlijk zal ChatGPT zich ook verder ontwikkelen, maar deze was nu al op niveau en hoeft dus niet per se nog beter te worden om goede resultaten op te leveren.

## Volgende stappen
Een van de dingen die ik zou aanbevelen om te doen is het gebruik maken van het fine tunen van je eigen ChatGPT model. Dit zou niet heel veel schelen in performance maar wel een hoop in kosten. Momenteel heb je best veel tokens nodig aan instructies om te zorgen dat je tekst genereerd in een bepaald format. Door het model aan te leren alleen in dat bepaalde format te reageren, zou je deze instructies weg moeten kunnen laten en hierdoor minder tokens gebruiken. 

Momenteel is OpenAI bezig met het maken van hun GPT service. Deze service zou ook nog erg van toepassing kunnen zijn voor de tools in de toolbox. Ze zouden ervoor kunnen zorgen dat de modellen veel meer gespecialiseerd zijn op onderwerpen of net zoals bij het fine tunen een format kunnen aanhouden. Het is mogelijk dat je fine tunen zou kunnen vervangen door GPTs, maar dat is nog niet zeker doordat ik ze niet in de praktijk heb kunnen testen.

