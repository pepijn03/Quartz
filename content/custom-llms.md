---
title: Onderzoek custom LLMs
tags:
  - onderzoeks-rapport
---
Binnen het project van mijn stage bij Handpicked Lab, is mijn opdracht om een integratie te maken van een taal model, dat informatie moet bevatten van een bepaald bedrijf. Het is belangrijk om deze informatie op een veilige manier op te slaan. Verder is het belangrijk om rekening te houden met de prestaties van het taal model, het moet niet te lang duren voordat het model een antwoord genereerd. 

In dit onderzoeks-rapport wil ik de deelvraag; 'Welke AI technologieën bestaan al die kunnen toegepast worden voor deze ondersteuningen?' volledig beantwoorden en een deel van 'Hoe maak ik een applicatie/AI aangepast aan bepaalde toepassingen en gebruikers?' beantwoorden. 

Eerder binnen mijn stage heb ik uitgezocht waar de stakeholders binnen handpicked ondersteuning willen hebben door middel van LLMs. Daarna zou ben ik bezig gegaan met de 'Welke AI technologieën bestaan al die kunnen toegepast worden voor deze ondersteuningen?'. Deze beantwoord ik in het de eerste gedeeltes van dit verslag. Tijdens dit onderzoek ben ik op zoek gegaan om manieren te vinden om LLMs op bepaalde manieren te laten functioneren. Dit document is dus het onderzoek wat vanuit deze deelvraag ontstaan is

Daarnaast ben ik hier ook deels gaan nadenken over de deelvraag 'Hoe maak ik een applicatie/AI aangepast aan bepaalde toepassingen en gebruikers? '. Hiervoor heb ik onderzoek gedaan naar de verschillende manieren om LLMs te gebruiken, waarmee ik dus het deel over aangepaste AI beantwoord.
# Fine-tuning
Het proces van fine tuning bij een taalmodel, houdt in dat je een model op een bepaalde manier zich laat gedragen. Door een combinatie van prompt engineering en finetuning kan je heel snel een model krijgen die reageert op de manier die je het wil laten leren. Het fine tunen van een taalmodel kan ook met een verassend kleine corpus, dit komt doordat het model bij fine tunen het model eigenlijk een aantal voorbeelden geeft hoe het moet reageren op bepaalde prompts.

![Voorbeeld van een fine tuning dataset om een llm midjourney prompt te laten generen](fine-tuning-data.png)

Het fine tunen van een model kan erg waardevol zijn voor mijn einddoel, als ik erachter kom dat ik met prompt-engineering niet goed genoege resultaten kan krijgen. Het is de bedoeling dat er uiteindelijk een antwoord gegenereerd kan worden op basis van wat invulvelden, dit antwoord zou op een bepaalde vorm gegeven worden. Denk aan altijd een overzicht genereren van een aantal brainstorm ideeën.

# Vector stores/databases
Vector stores of databases zijn erg effectief om de knowledge base van een taal model te verbreden. De knowledge base is de data waarop een model getraind is, in het geval van vector stores wordt deze data ook echt verbreed zonder dat je het model hoeft te trainen. Een vector is een stukje data omgezet in een serie van nummers die dat stukje data representeer, in dit geval is dat stukje data een woord of stukje tekst. Wanneer je deze vectors opslaat kan een taal model deze opslag doorzoeken zonder daar op getraind hoeft te zijn, hierdoor kan je dus heel snel data toevoegen aan het model. De data in de vector store wordt ook niet opgeslagen in het model, het is dus veilig om gevoelige data hierin op te slaan zonder dat het model deze informatie in zich heeft.

![Hoe een vector store gebruikt wordt](Vector-stores.png)

# Verschillende modellen
Op het gebied van taal modellen worden er elke dag grote stappen gezet, maar een probleem waar je snel tegen aan loopt is dat deze stappen vooral gezet worden op taal modellen in het Engels. Er komen steeds meer modellen op die ook ondersteuning bieden voor talen zoals Spaans, Frans of zelfs Koreaans. Als je op [huggginface](https://huggingface.co), de grootste hub voor open-source taal modellen, dan vind je dat van de 47 duizend text generatie modellen er maar 120 zijn die aangeven dat ze onder andere ook geschikt zijn voor de Nederlandse taal. Doordat de voertaal binnen de stakeholders Nederlands is, lijkt het mij belangrijk dat er ook modellen gebruikt worden die in het Nederlands tekst genereren en dus ook Nederlands talige embeddings kunnen gebruiken. 

## Grootte
Verder is het interessant om te gaan kijken naar verschillende groottes van modellen, de grootte van een model heeft te maken met het aantal parameters die het in zich heeft. Deze parameters zorgen ervoor dat een model text kan genereren op een manier die bijna menselijk lijkt. Het aantal parameters verschilt enorm per model. Zo heeft een wat kleiner model zoals GPT-2 maar 2 miljard parameters terwijl GPT-4 er al 1 biljoen parameters. Dit houdt in dat er erg veel kleine kleine onderdelen van het model bestaan waar je aan zou kunnen sleutelen om de meest passende uitkomst te krijgen. 

## Parameters
parameters zijn waardes die je ergens aan mee kan geven waarmee een applicatie berekeningen op kan uitvoeren. In het geval van LLMs is het erg interessant om te spelen met de parameters, hierdoor zou je met hetzelfde model hele andere generaties kunnen krijgen zodra een beetje gaat spelen met de parameters. Als je een open source model hebt zou je zelfs prompt engineering kunnen vervangen door parameter tuning. Een goed voorbeeld van parameters is een de temperature parameter.

![Voorbeeld van temperature; een parameter van een LLM](temparature.png)

# LLM selecteren
Voor mijn specifieke context is het belangrijk dat een model de Nederlandse taal kan begrijpen en ook antwoorden kan genereren. Er zijn een paar modellen waarvan bekent is dat ze Nederlands kunnen, daarnaast zijn er nog een paar modellen die minimaal getraind zijn op Nederlandse tekst, ik zal moeten onderzoeken of dit kleine beetje al genoeg is of niet.

## Open source modellen
"Iedereen kent ChatGPT" is tegenwoordig geen hele rare stelling. ChatGPT is nou eenmaal het bekendste LLM, maar het is zeker niet de enigste. Er worden dagelijks nieuwe open-source modellen geüpload naar platformen zoals Huggingface en deze modellen worden ook dagelijks gedownload en gebruikt. Om te kijken of deze modellen voldoende kwaliteit leveren voor mijn specifieke context ben ik onderzoek gaan doen naar wat precies het standaard van kwaliteit is voor open-source modellen. 

Een van de eerste problemen waar ik tegenaan liep was inderdaad dat de meeste modellen niet op niveau zijn om volledige en kloppende Nederlands talige zinnen te generen. Via Huggingface heb ik een kleine selectie aan modellen uitgeprobeerd. De modellen die ik uitgeprobeerd heb zou je kunnen splitsen in twee groepen; bekende, bewezen modellen zoals Llama, Falcon of Orca en niche, goed presterende modellen volgens [open source llm leaderboard](https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard) zoals Mistral, Mythical destroyer en OpenHermes.

De bewezen modellen presteerde over het algemeen goed genoeg om simpele antwoorden te geven, maar vaak hadden deze modellen moeite met consistent creatieve ideeën en/of vloeiende 'mensachtige' antwoorden generen. Vaak waren antwoorden erg kort en alleen informationeel, er zat weinig gevoel achter. Dit komt waarschijnlijk dat deze modellen niet gefinetuned zijn om menselijke antwoorden te geven wanneer de modellen bevraagd worden.

Daarnaast had ik een algemeen probleem met het lokaal gebruiken van open source modellen, dit was performance. Het was erg moeilijk om te zorgen dat modellen binnen een redelijke tijd een stukje bruikbare tekst te genereren op basis van een embedding. Het beantwoorden van simpele vragen ging best soepel en snel, je had binnen 15 seconden antwoord op de vraag: "Wie is de koning van Nederland"

![[llama-1.png]]

Het probleem lag het vooral in het bevragen van een model met de context van een embedding. Hier duurde een bevraging al snel meerdere minuten bij verschillende modellen. De eerste keren dat ik probeerde te generen met een embedding duurde een generatie van 250 tokens (1 token = ~4 letters) als snel rond 250 tot 260 seconden. Dit is natuurlijk veel te lang. Om dit te verhelpen ben ik gaan kijken naar parameters van de libraries die ik gebruik. Zo heb ik het maximale aantal cpu threads die mijn llm mag gebruiken maximaal gemaakt en de similarity search van mijn vectorstore async gemaakt, waardoor meerdere delen van de embedding tegelijk doorzocht kunnen worden. Dit hielp om uiteindelijk naar een generatie tijd van ongeveer twee minuten te komen voor in dit voorbeeld een kerst bericht van een bedrijf te genereren. 

![[mythical-destroyer.png]]

Deze tekst was met een model genaamd [Mythical destroyer](https://huggingface.co/Sao10K/Mythical-Destroyer-V2-L2-13B) gegenereerd, die erg hoog scoorde op de hiervoor genoemde llm leaderboard. Bij wat langer bestaande en bewezen modellen duurde het generen korter, dit komt waarschijnlijk door interne optimalisatie van de modellen. De duur van de generaties duurde nog steeds te lang. Zo deed een verbeterd model van Microsoft hun Orca model er een stuk korter over, maar was de generatie ook van een stuk mindere kwaliteit.

![[orca-4.png]]

Dit was iets waar ik voor nu geen oplossing op kon bedenken en na wat overleg met mijn stagebegeleiders van Handpicked Lab hebben we besloten om toch ChatGPT te gaan gebruiken door de kwaliteit en performance van het model.


## OpenAI's ChatGPT
De problemen en limitaties waar ik tegenaan liep bij het experimenteren met open source-modellen waren niet aanwezig als ik derde partij oplossingen zou gebruiken. De bekendste hiervan is natuurlijk ChatGPT, de meest gebruikte LLM van dit moment. Wat belangrijk was te onderzoeken is hoe ChatGPT om gaat met de data die je ernaar toe stuurt. Gelukkig is het regelement van OpenAI erg duidelijk op het gebied van hun data opslag. Alle data die via de API binnenkomt wordt niet gebruikt of opgeslagen door OpenAI, alleen data die via hun eigen chat interface binnenkomt. 

ChatGPT gebruiken met je eigen data is erg simpel. Je kan via de API je embeddings creëren en hoeft ze alleen nog maar lokaal op te slaan om te kunnen gebruiken. Daarnaast kun je ook gemakkelijk een wat geavanceerde prompt maken door middel van het gebruik van een afgescheiden instructie wat de LLM zou moeten doen en een vraag die het zou moeten beantwoorden. Daarnaast kan je ook de embeddings toevoegen aan de instructie. Dit kan het best via het uitvoeren van een Similarity search, een manier om tekst te doorzoeken en alleen de relevante stukken hiervan te gebruiken. Dit zorgt voor een meer gerichte versie van de embedding die ook kleiner is voor performance en kosten.

Er wordt vaak gebruik gemaakt van fine-tuning wanneer er gebruik wordt gemaakt van ChatGPT via de OpenAI API. Dit komt doordat het erg makkelijk is om een eigen model te creëren waar de instructie er al standaard in zit wanneer je iets wilt genereren. Je kan dus heel makkelijk hét meest gebruikte LLM model op een manier laten reageren die je zelf specifiek kan aangeven. Momenteel is OpenAI bezig met een nieuwe feature van ChatGPT dit het maken van LLMs voor specifieke use cases nog makkelijker maakt. Deze feature heet GPTs. Zo promoten ze een GPTs die gefocust is op het uitleggen van bordspelletjes of een die helpt met tech support vraagstukken. Momenteel is deze feature nog niet beschikbaar voor iedereen en moet je wachten tot je toegang krijgt via een wachtlijst. Hierdoor kan ik deze feature nog niet zelf testen maar het zou wel erg handig geweest kunnen zijn voor mijn project.

## Conclusie
Er zijn dus verschillende manieren om een LLM te maken die werkt met een zelf toegevoegde context. De manieren die relevant zijn voor de context van mijn opdracht zijn fine tuning en embeddings door middel van vector stores. Zelf volledig een LLM maken was vanaf het begin al geen optie, omdat dit te lang duurt en ver boven mijn capaciteiten gaat. Hierdoor ben ik gaan kijken naar verschillende oplossingen waar ik LLM modellen vandaan kan halen. Zo kwam ik al snel bij twee plekken uit, het open LLM leaderboard waar de meeste open source modellen getest en gerangschikt worden en OpenAI's ChatGPT wat momenteel het meest gebruikte LLM model is wereldwijd. 

Na wat onderzoek en handmatig testen bleek dat open source modellen nog niet op niveau zijn voor de Nederlandse taal en is het ook moeilijk om een antwoord op een vraag te generen in minder dan een minuut, zeker als je het moet combineren met het doorzoeken van documenten om de context uit te breiden. Uiteindelijk heb ik ervoor gekozen om ChatGPT te gebruiken via hun API. Dit zorgde meteen voor betere resultaten en betere performance. Dit loste dus veel van de minpunten van open-source modellen op.

# Bronnen
AI Jason. (2023, July 9). “okay, but I want GPT to perform 10x for my specific use case” - Here is how. YouTube. https://www.youtube.com/watch?v=Q9zv369Ggfk

Ehab, M. (2023, July 30). The Secrets of Large Language Models Parameters: How They Affect the Quality, Diversity, and. Michael Ehab. .. Medium. https://michaelehab.medium.com/the-secrets-of-large-language-models-parameters-how-they-affect-the-quality-diversity-and-32eb8643e631

Enterprise privacy. (n.d.). https://openai.com/enterprise-privacy

Introducing GPTs. (n.d.). https://openai.com/blog/introducing-gpts

Open LLM Leaderboard - A Hugging Face space by HuggingFaceH4. (n.d.). https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard

OpenAI | 🦜️🔗 Langchain. (n.d.). https://python.langchain.com/docs/integrations/llms/openai
Schwaber-Cohen, R. (n.d.). What is a Vector Database & How Does it Work? Use Cases + Examples. 

Pinecone. https://www.pinecone.io/learn/vector-database/

Vector stores | 🦜️🔗 Langchain. (n.d.). https://python.langchain.com/docs/modules/data_connection/vectorstores/

What is LLM Parameters. (2023, August 14). Deepchecks. https://deepchecks.com/glossary/llm-parameters/

Wikipedia contributors. (2023a, December 26). Fine-tuning (deep learning). Wikipedia. https://en.wikipedia.org/wiki/Fine-tuning_(deep_learning)

Wikipedia contributors. (2023b, December 31). Large language model. Wikipedia. https://en.wikipedia.org/wiki/Large_language_model