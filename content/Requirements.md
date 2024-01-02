---
title: Requirements
tags:
  - project-plan
  - app-design
  - analyse
---
Voordat je iets gaat maken is het belangrijk dat je gaat uitzoeken wat je precies wil gaan maken. Dit ga ik in dit project doen aan de hand van user stories en/of use cases. De user stories werkt in dit geval als een vervanging van klassieke requirements. Daarnaast zijn er ook wat niet functionele vereisten aan het project, deze staan hier ook gedefinieerd.

# Use case en User stories
## Ideeën genereren

### user story
Als gebruiker wil ik ideeën kunnen generen te helpen met de overgang van concept naar design binnen het creatieve process van Weekend.

### Use cases

| **Naam** | UC-01: Upload een context |
| ---- | ---- |
| **Samenvatting** | De gebruiker maakt een embedding aan door een bestand te uploaden. |
| **Actor** | Medewerken binnen Handpicked agencies |
| **Aanname** |  |
| **Scenario** | <ol><li>De actor selecteerd een bestand om te uploaden.</li> <li> Het systeem maakt lokaal een embedding aan. </li> </ol> |
| **Uitzondering** |  |
| **Resultaat** | De actor heeft nu een idee gegeneerd. |

<br/>

| **Naam** | UC-02: Genereer een idee |
| ---- | ---- |
| **Samenvatting** | De gebruiker genereert een idee op basis van een brandstory. |
| **Actor** | Medewerken binnen Handpicked agencies |
| **Aanname** | Er is een context aangemaakt (UC-01) |
| **Scenario** | <ol><li>De actor voert het eindproduct en het soort bedrijf in.</li> <li> De actor selecteert een eerder geüploade brandstory als context </li> <li> Het systeem genereerd op basis van het de invoer een idee voor een design waar met extra context over eerder onderzoek van dit project. </li> </ol> |
| **Uitzondering** |  |
| **Resultaat** | De actor heeft nu een idee gegeneerd. |

<br/>

| **Naam** | UC-03: Genereer persona's |
| ---- | ---- |
| **Samenvatting** | De gebruiker genereert een paar persona's. |
| **Actor** | Medewerken binnen Handpicked agencies |
| **Aanname** |  |
| **Scenario** | <ol><li>De actor voert de doelgroep die de persona's moeten aannemen en het vraagstuk waarvoor de persona's bedoelt zijn.</li> <li>Het systeem genereerd op basis van het de invoer een lijst met een paar persona's die een naam, leeftijd, korte beschrijving en hun belangrijkste standpunten over het vraagstuk bevatten</li> </ol> |
| **Uitzondering** | De actor kan ook een bestaande context gebruiken voor het maken van persona's na stap 1 |
| **Resultaat** | De actor heeft nu een idee gegeneerd. |

<br/>

| **Naam**         | UC-04: Genereer een woordweb                                                                                                                                       |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Samenvatting** | De gebruiker genereert een woordweb op basis van een brandstory.                                                                                                   |
| **Actor**        | Medewerken binnen Handpicked agencies                                                                                                                              |
| **Aanname**      | Er is een brandstory geüpload als context (UC-01)                                                                                                                          |
| **Scenario**     | <ol><li>De actor selecteert een eerder geüploade brandstory.</li> <li> Het systeem genereerd nu een woordweb gebaseerd op de thema's in de brandstory. </li> </ol> |
| **Uitzondering** |                                                                                                                                                                    |
| **Resultaat**    | De actor heeft nu een idee gegeneerd.                                                                                                                              |

<br/>

| **Naam** | UC-05: Haal eerdere ideeën op |
| ---- | ---- |
| **Samenvatting** | De gebruiker genereert een idee op basis van een brandstory. |
| **Actor** | Medewerken binnen Handpicked agencies |
| **Aanname** |  |
| **Scenario** | <ol><li>De actor voert het eindproduct en het soort bedrijf in.</li> <li> een idee voor Het systeem genereerd op basis van het de invoereen design waar met extra context met concepten van brandstory . </li> </ol> |
| **Uitzondering** |  |
| **Resultaat** | De actor heeft nu een idee gegeneerd. |


## LLM
Er zullen meerdere eisen gesteld moeten worden aan het LLM wat ik ga gebruiken om ervoor te zorgen dat mijn eindproduct tot de eisen zal voldoen.

Het LLM model zal antwoorden moeten genereren die past bij het doel van de 'tool' op basis van de prompt en de meegegeven context.

Het LLM model zal Nederlands talige vragen moeten kunnen beantwoorden in het Nederlands.

Het LLM model zou de mogelijkheid moeten hebben om antwoorden te genereren die niet voor de hand liggen.

# Non-functional requirements
Dit is een lijst met eisen die gesteld zijn door de opdrachtgever of door mezelf. Deze lijst is belangrijk om duidelijk te krijgen wat er precies geëist wordt van het project buiten de functionaliteiten om. 

- NFR-01: De applicatie heeft een middleware laag in Express.js.
- NFR-02: De front end van de applicatie wordt gemaakt in TypeScript met Angular.
- NFR-03: De LLM is bereikbaar via een Python Flask API.
- NFR-04: De applicatie maakt gebruik van een MongoDB database.
- NFR-05 De applicatie moet responsive zijn in de meest gebruikte web browsers(MS Edge, Google Chrome, Firefox en Safari). 
