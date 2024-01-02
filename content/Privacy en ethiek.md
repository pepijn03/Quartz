---
title: Privacy en ethiek
tags:
  - onderzoeks-rapport
  - analyse
---
Doordat er binnen mijn project duidelijk met gevoelige data gewerkt wordt, is het belangrijk dat er gekeken wordt naar hoe er op een verantwoordelijke manier om gegaan kan worden met deze data. Daarnaast is er recentelijk ook veel te doen over de ethiek van AI en dan voornamelijk generative AI, waar ik mee bezig ben. Hierdoor heb ik gekeken wat er binnen mijn gebruik van LLMs de beste manier is om er ethisch mee om te gaan binnen de context van mijn project. Verder belicht dit document onderdelen die samen een antwoord vormen op de deelvraag: 'Wat zijn ethische overwegingen bij het gebruik van AI in een creatief proces?'.

# Privacy
Een van de grootste redenen wat mijn stage opdracht relevant maakt is dat er momenteel nog geen manier is om een LLM te (laten) trainen door een derde partij die transparant om gaat met de data die je ernaar toe stuurt. Zo kan je bij ChatGPT wel zelf een versie van LLM trainen, maar het is nergens te vinden wat er gebeurt met de data waarop je het model traint. Hierdoor heb ik de keuze genomen om de gebruikte data alleen lokaal op te slaan in mijn applicatie. Deze data zal op dezelfde server komen als waar de applicatie-laag van de LLM (zie [[software-architectuur |software architectuur]]) op zou moeten draaien. Dit zou ervoor moeten zorgen dat de data alleen beschikbaar is voor/door de gebruikers van de 'AI toolbox', die allemaal werknemers van Handpicked Agencies zouden moeten zijn.

# Transparantie en Data
Om duidelijk te maken wat de bedoeling van de toolbox, gaat er een user's guide komen op de website. Hierin zal beschrijven worden hoe de tools zouden moeten werken en hoe je deze kan gebruiken. Daarnaast zal er bij elke een tool een korte beschrijving staan waar het specifieke doel van de desbetreffende tool staan. 

Daarnaast zal er ook per tool beschreven worden wat voor soort data goed presteert bij de bijbehorende tool. De kwaliteit van de data niet heel erg relevant binnen de context van mijn opdracht. Natuurlijk werkt sommige data beter dan andere, dus zodra er wordt gedefinieerd wat goed presterende data is zal iedereen de toolbox kunnen gebruiken met 'goede' resultaten. 

# Inclusiviteit en haatdragende actors
Het gespreksonderwerp van ethiek en AI is recentelijk erg relevant geworden. De link tussen AI en ethiek is op meerdere manieren te leggen, het ethisch gebruiken van een AI model en het gebruiken van ethisch verkregen data om een AI model te trainen. Binnen mijn project zal is vooral het ethisch gebruik maken van een relevant zijn, doordat de data alleen intern verkregen en gebruikt zal worden en ik geen invloed heb op de data waar de modellen origineel op getraind zijn. Onder het ethisch gebruiken van een AI model versta ik vooral dat de mogelijke generaties van een model in dit geval geen tekst genereert dat schadelijk kan zijn naar een bepaalde personen of groepen van mensen. Hiermee bedoel ik vooral dingen zoals; seksistische, racistische of discrimineerde teksten. 

Doordat ik in mijn applicatie werk met een soort template om vragen testellen, dit limiteert deels de vrijheid van de gebruiker waardoor er minder plek is om door middel van prompt engineering schadelijke teksten te kunnen generen. Daarnaast gaan er ook toegevoegd worden aan deze templates die specificeren dat er geen politiek geladen of schadelijke teksten zou moeten genereren. Hierdoor zou het dus zo goed als onmogelijk moeten zijn om schadelijke teksten te generen, zonder de generaties te filteren. Ik heb ervoor gekozen om geen filter in te bouwen, omdat dit buiten te scope van het project valt en dus te veel tijd gaat kosten. Daarnaast is het niet nodig om een ideaal product op te leveren doordat het einddoel van het project een Proof of concept is.

Uiteindelijk is het de bedoeling dat het LLM dat ik gebruik door generaties help met creatieve ideeën verzinnen voor Weekend, als een soort van klankbord.  Dit wekt de vraag op: "Wanneer is iets creatief?" of "Kan een AI creatief zijn?". Op de eerste vraag ga ik geen antwoord kunnen geven, maar op de tweede vraag zou ik dat wel kunnen. Zelf denk ik dat een AI model best 'creatieve' dingen kan genereren, omdat iets niet origineel hoeft te zijn om een creatief te zijn. Je gaat waarschijnlijk geen 100% unieke ideeën kunnen laten generen door een LLM, maar dat zou niet uit moeten maken als je op zoek bent naar inspiratie. Het doel van het gebruik binnen mijn opdracht is dus ook meer om te helpen op 'creatieve' ideeën te komen in plaats van ze kant en klaar te kunnen genereren. 

# Duurzaamheid
 De impact die LLMs kunnen hebben op het milieu is totaal afhankelijk van hoeveel stroom er verbruikt wordt. LLMs zijn best zwaar om te draaien op een server doordat ze continu de volgende letter, woorden en zinnen moeten voorspellen. Het gebruiken van een LLM als individu heeft weinig impact op het milieu, maar die kleine beetjes stapelen op. Daarnaast moeten modellen getraind worden en dit is waar vaak de helft van de energieverbruik van de levensduur van een LLM vandaan komt, zoals bij Hugging face hun model BLOOM. Het gebruik van een bestaand LLM is meer milieu verantwoord, maar nog zeker ver van CO2 neutraal. 

# Toekomst
Je ziet de eerste effecten van LLMs zijn al te zien. Zo staat ChatGPT al een beetje bekent als iets wat misinformatie en bevooroordeelde informatie genereerd. Dit betekent dat er steeds meer misinformatie ontstaat op het internet. Dit kan niet alleen een negatieve impact hebben op mensen, maar ook op de LLM zelf. Een populaire theorie is dat LLM zichzelf gaat opeten door onder andere dit fenomeen. Vaak wordt deze theorie ook de LLM ouroboros genoemd, een ouroboros een symbool in verschillende mythologieën van een slang die zichzelf op eet. De slang symboliseert de circulariteit van dingen en in de mythologie vooral de circulariteit van de natuur. 

Een andere reden waarom deze theorie veel besproken heeft te maken met hoe er momenteel inkomsten genereerd worden via het internet. De informatie die een LLM gebruikt moet door iemand geschreven worden. Voor LLMs komt deze informatie meestal  van journalisten en schrijvers die artikelen schrijven op het internet. Deze artikelen verdienen nu geld via advertenties en het aantal keer dat daar op gelikt wordt, zodra een LLM alle informatie van deze artikelen opneemt is er geen reden meer om naar de originele artikel te gaan en dan zie je dus ook de advertentie niet. Dit zou ervoor kunnen zorgen dat er steeds minder artikelen gratis te bekijken zijn en steeds meer alleen te bekijken zijn met een account of zelf premium account.

# Impact
Doordat de opdracht een verzameling is van use-case specifieke manieren om een LLM te gebruiken op een low level zonder dat je veel hoeft te weten over hoe je een LLM moet aansturen om goede antwoorden te krijgen. De toolbox maakt het dus makkelijker voor mensen die minder technisch aan zijn gelegd toch nieuwe technologieën te kunnen gebruiken. De toolbox gaat alleen maar binnen mijn stageplek gebruikt worden dus de hoeveelheid impact die het kan hebben is erg groot maar, alleen op een geselecteerd aantal mensen.

# Human values
Een van de use-cases van de toolbox is het creëren persona's. Dit zijn vrij simpele persona's maar kunnen ook erg snel gegenereerd worden. Zo heb je dus binnen 30 seconden een lijstje met persona's. Dit betekent dat je in een meeting ze zou kunnen generen als snelle opzet om op door te gaan en meteen een beter idee te kunnen schetsen. Dit zou ook kunnen werken met het generen van ideeën of het linkjes leggen naar eerdere project. Hierdoor zou je dus erg snel proof of concepts op kunnen zetten om meteen te kunnen bespreken. 



# Bronnen
Top 5 risks of large language models. (2023, August 14). Deepchecks. https://deepchecks.com/top-5-risks-of-large-language-models/

Burke, J. (2023, September 11). Assessing the environmental impact of large language models. Enterprise AI. https://www.techtarget.com/searchenterpriseai/tip/Assessing-the-environmental-impact-of-large-language-models

Dash, S. (2023, September 12). Exploring ethics and privacy in the world of advanced language models. Analytics Vidhya. https://www.analyticsvidhya.com/blog/2023/08/ethics-and-privacy-in-advanced-language-models/

Iqbal, M. (2023, November 15). The carbon footprint of large language models: unmasking the environmental impact. Scientia. https://scientiamag.org/the-carbon-footprint-of-large-language-models-unmasking-the-environmental-impact/

Tackling the ethical dilemma of responsibility in Large Language. (2023, May 5). University of Oxford. https://www.ox.ac.uk/news/2023-05-05-tackling-ethical-dilemma-responsibility-large-language-models

Technology Impact Cycle Tool. (n.d.). Technology Impact Cycle Tool. https://tict.io/