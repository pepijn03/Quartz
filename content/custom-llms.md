---
title: Custom LLMs
tags:
  - onderzoeks-rapport
---
Binnen het project van mijn stage bij Handpicked Lab, is mijn opdracht om een integratie te maken van een taal model, dat informatie moet bevatten van een bepaald bedrijf. Het is belangrijk om deze informatie op een veilige manier op te slaan. Verder is het belangrijk om rekening te houden met de prestaties van het taal model, het moet niet te lang duren voordat het model een antwoord genereerd.

# Fine-tuning
Het proces van fine tuning bij een taalmodel, houdt in dat je een model op een bepaalde manier zich laat gedragen. Door een combinatie van prompt engineering en finetuning kan je heel snel een model krijgen die reageert op de manier die je het wil laten leren. Het fine tunen van een taalmodel kan ook met een verassend kleine corpus, dit komt doordat het model bij fine tunen het model eigenlijk een aantal voorbeelden geeft hoe het moet reageren op bepaalde prompts.

![Voorbeeld van een fine tuning dataset om een llm midjourney prompt te laten generen](fine-tuning-data.png)

Het fine tunen van een model is erg waardevol voor mijn einddoel in dit project. Het is de bedoelen dat er uiteindelijk antwoorden kan generen op basis van wat invulvelden, dit antwoord zou op een bepaalde vorm gegeven worden. Denk aan altijd een overzicht genereren van een aantal brainstorm ideeën.

# Vector stores/databases
Vector stores of databases zijn erg effectief om de knowledge base van een taal model te verbreden. De knowledge base is de data waarop een model getraind is, in het geval van vector stores wordt deze data ook echt verbreed zonder dat je het model hoeft te trainen. Een vector is een stukje data omgezet in een serie van nummers die dat stukje data representeer, in dit geval is dat stukje data een woord of stukje tekst. Wanneer je deze vectors opslaat kan een taal model deze opslag doorzoeken zonder daar op getraind hoeft te zijn, hierdoor kan je dus heel snel data toevoegen aan het model. De data in de vector store wordt ook niet opgeslagen in het model, het is dus veilig om gevoelige data hierin op te slaan zonder dat het model deze informatie in zich heeft.

![Hoe een vector store gebruikt wordt](Vector-stores.png)

# Een model kiezen
Op het gebied van taal modellen worden er elke dag grote stappen gezet, maar een probleem waar je snel tegen aan loopt is dat deze stappen vooral gezet worden op taal modellen in het Engels. Er komen steeds meer modellen op die ook ondersteuning bieden voor talen zoals Spaans, Frans of zelfs Koreaans. Als je op [huggginface](https://huggingface.co), de grootste hub voor taal modellen, dan vind je dat van de 47 duizend text generatie modellen er maar 120 zijn die aangeven dat ze onder andere ook geschikt zijn voor Nederlands. Doordat de voertaal binnen de stakeholders Nederlands is, lijkt het mij belangrijk dat er ook modellen gebruikt worden die in het Nederlands tekst genereren en dus ook Nederlands talige embeddings kunnen gebruiken. 

## Grootte
Verder is het interessant om te gaan kijken naar verschillende groottes van modellen, de grootte van een model heeft te maken met het aantal parameters die het in zich heeft. Deze parameters zorgen ervoor dat een model text kan genereren op een manier die bijna menselijk lijkt. Het aantal parameters verschilt enorm per model. Zo heeft een wat kleiner model zoals GPT-2 maar 2 miljard parameters terwijl GPT-4 er al 1 biljoen parameters. Dit houdt in dat er erg veel kleine kleine onderdelen van het model bestaan waar je aan zou kunnen sleutelen om de meest passende uitkomst te krijgen. 

## Parameters
parameters zijn waardes die je ergens aan mee kan geven waarmee een applicatie berekeningen op kan uitvoeren. In het geval van LLMs is het erg interessant om te spelen met de parameters, hierdoor zou je met hetzelfde model hele andere generaties kunnen krijgen zodra een beetje gaat spelen met de parameters. Als je een open source model hebt zou je zelfs prompt engineering kunnen vervangen door parameter tuning. Een goed voorbeeld van parameters is een de temperature parameter.

![Voorbeeld van temperature; een parameter van een LLM](temparature.png)

# Model selecteren
Voor mijn specifieke context is het belangrijk dat een model de Nederlandse taal kan begrijpen en ook antwoorden kan genereren. Er zijn een paar modellen waarvan bekent is dat ze Nederlands kunnen, daarnaast zijn er nog een paar modellen die minimaal getraind zijn op Nederlandse tekst, ik zal moeten onderzoeken of dit kleine beetje al genoeg is of niet.

De modellen waarvan bekent is dat ze goed met de Nederlandse taal om kunnen gaan zijn: Llama(2), Bert en GPT (4). Dit zijn dus ook de modellen die ik als eerst wil gaan testen. Het testen zal ik gaan doen in verschillende rondes. De eerste test zal een erg feitelijke vraag zijn, hiervoor heb ik gekozen voor de  vraag: "Wie is de koning van Nederland?" , daarnaast wordt er ook aan de modellen een subjectieve vraag gesteld: "Wat is de beste kleur?". 

Daarna worden de modellen die een goed genoeg antwoord gaven op de eerste vraag ook getest met een embedding als context. Hierna zal er gekeken worden naar wat de prestatie van een model, hier zal gekeken worden of het model wel snel genoeg is om te gaan gebruiken op een API. Om duidelijk te zijn met wat snel genoeg is heb ik hiervoor richtlijnen opgezet. Model deployment zou idealistisch korter dan 10 seconden duren, dit zou in de praktijk uit mogen lopen tot 20 seconden mits dat de snelheid van een vraag verwerken snel genoeg is. De richtlijn voor een vraag verwerken zou idealistisch onder de 20 seconden zitten, dit zou mogen uitlopen tot 40 seconden. Het is de bedoeling dat het complete process niet langer duurt dan maximaal 50 seconden, het doel is natuurlijk om het process uit te kunnen voeren in ongeveer 30 seconden.

De modellen zullen getest worden op mijn locale machine in een python omgeving met behulp van [Langchain](https://python.langchain.com/docs/get_started/introduction). 

## Llama
Llama is een familie van LLM modellen van Meta. Deze modellen zijn van vrij hoge kwaliteit binnen de open-source modellen die nu steeds meer in opkomst zijn. 

De eerste test was deels geslaagd, als het op iets specifieks en feitelijks aan komt kwam er een goed volledig Nederlandstalig antwoord uit. Zodra het wat subjectiever werd, was het meteen moeilijker voor het model om een volledig Nederlands antwoord te genereren. 
### Prompting
Het model reageert wel goed op een hele feitelijke vraag zoals: "Wie is de koning van Nederland?".

![[llama-1.png]]

Het model kan het alleen niet aan als het neerkomt op een zweverige vraag. Je merkt bij dit resultaat ook dat het model heer raar reageert en tegen zichzelf gaat praten. Dit komt waarschijnlijk doordat Llama een model is dat gemaakt is voor gebruik als een chatbot.

![[Pasted image 20231107164836.png]]

Deze uitkomsten zijn niet ideaal maar, het is lijkt me het wel waard om verder te gaan experimenteren voor mijn project.

### Embeddings


### Performance


## Bert


## ChatGPT
Doordat ChatGPT de grootste en het meest gebruikte LLM model is kwam ik er ook al snel achter dat OpenAI, de makers van ChatGPT, een eigen service aanbieden waar je een eigen versie van hun modellen kan trainen. Er zitten voor en nadelen aan dit platform. Het platform is makkelijk in gebruik en heeft makkelijke aansluitingen op de Langchain package. Verder komt er wel een prijs bij kijken zodra je gebruik wil gaan maken van OpenAI's API en weet je niet precies wat er gebeurt met de data die je naar OpenAI stuurt. Dit platform is dus niet geschikt voor de specifieke context van deze opdracht.

## Falcon
Dit model is een van de modellen dat niet aan geeft dat het de Nederlandse taal begrijpt, maar het is wel een klein beetje getraind op Nederlandse taal. Hierdoor vind ik het een interessant experiment om te kijken hoeveel begrip op de Nederlandse taal genoeg is voor mijn casus. 

![[falcon-1.png]]

Het platform waar ik andere modellen getest heb werkte niet goed voor Falcon, hierdoor ben ik door gaan zoeken en heb ik gevonden dat er een preview van de model gehost wordt op de [Huggingface pagina van Falcon](https://huggingface.co/tiiuae/falcon-7b-instruct) 

![[falcon-2.png]]

Hieruit kon ik concluderen dat het Falcon model het niet waard is om verder mee te gaan experimenteren. Voor een model dat Geraint is op 3 miljard Nederlandse vectors, vind ik dit een best slechte uitkomst.

## Orca
Orca is een familie van LLMs die gebaseerd is op llama en bekent staan om hun kracht tegenover hun compactheid. Het Orca-mini model is ook het model wat ik vooral gebruikte bij het testen van mijn applicatie en eigenlijk had ik het model afgeschreven voor uiteindelijk gebruik, omdat het model geen Nederlandse taal kon verwerken. Dit is veranderd sinds de release van de derde versie van het Orca model. Deze modellen zijn gebaseerd op de nieuwe Llama-3 modellen en kunnen nu ook met Nederlandse taal omgaan. Hierdoor leek het mij leuk om te kijken wat er uit dit model zou komen.

### Prompting
Bij de standaardvraag over wie de koning van Nederland is gaf het model een kort en bondig antwoord

![[orca-1.png]]

Verder kan het model ook omgaan met een erg subjectieve vraag: "Wat is de mooiste kleur?". Het verbaasde mij een beetje dat het model een mening had over wat de mooiste kleur was. Verder vroeg ik me ook af of de term 'sereen' kwam vanuit een vertaling, omdat dit geen veelgebruikt Nederlands woord is.

![[orca-2.png]]

Het model geeft dus verbazingwekkend goede antwoorden op verschillende soorten vragen en ook nog compleet in correct Nederlands. Het model is het dus waard om mee door te gaan testen ookal was het een model waar ik persoonlijk niet al te veel vertrouwen in had.

### Embeddings
