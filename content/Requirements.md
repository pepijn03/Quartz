---
title: Requirements
tags:
  - project-plan
  - app-design
  - analyse
---

Voordat je iets gaat maken is het belangrijk dat je gaat uitzoeken wat je precies wil gaan maken. Dit ga ik in dit project doen aan de hand van user stories en use cases. De user stories werkt in dit geval als een vervanging van klassieke requirements. Daarnaast zijn er ook wat niet functionele vereisten aan het project, deze staan hier ook gedefinieerd.
# Use case en User stories
## Ideeën genereren

### user story
Als gebruiker wil ik ideeën kunnen generen te helpen met de overgang van concept naar design binnen het creatieve process van Weekend.

### Use cases

| **Naam**         | UC-01.1: genereer een idee                                                                                                                                                                                                 |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Samenvatting** | De gebruiker genereert een idee op basis van eerdere ideeën.                                                                                                                                                               | 
| **User story**   | US-01                                                                                                                                                                                                                      |  
| **Actor**        | Medewerken van Weekend                                                                                                                                                                                                     |
| **Aanname**      |                                                                                                                                                                                                                            | 
| **Scenario**     | <ol><li>De actor voert het eindproduct en het soort bedrijf in.</li> <li>Het systeem genereerd op basis van het de invoer een idee voor een design waar met extra context met concepten van eerdere projecten. </li> </ol> |  
| **Uitzondering** |                                                                                                                                                                                                                            |
| **Resultaat**    | De actor heeft nu een idee gegeneerd.                                                                                                                                                                                      |

<br/>

| **Naam**         | UC-01.2: genereer een idee                                                                                                                                                                                                                                                                                                    |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Samenvatting** | De gebruiker genereert een idee op basis van eerdere ideeën.                                                                                                                                                                                                                                                                  | 
| **User story**   | US-01                                                                                                                                                                                                                                                                                                                         |  
| **Actor**        | Medewerken van Weekend                                                                                                                                                                                                                                                                                                        |
| **Aanname**      |                                                                                                                                                                                                                                                                                                                               | 
| **Scenario**     | <ol><li>De actor voert het eindproduct en het soort bedrijf in.</li> <li> De actor geeft bestanden mee over die betrekking hebben met het concept van het eindproduct <li>Het systeem genereerd op basis van het de invoer een idee voor een design waar met extra context over eerder onderzoek van dit project. </li> </ol> |  
| **Uitzondering** |                                                                                                                                                                                                                                                                                                                               |
| **Resultaat**    | De actor heeft nu een idee gegeneerd.                                                                                                                                                                                                                                                                                         |

# Non-functional requirements
Dit is een lijst met eisen die gesteld zijn door de opdrachtgever of door mezelf. Deze lijst is belangrijk om duidelijk te krijgen wat er precies geëist wordt van het project buiten de functionaliteiten om. 

- NFR-01: De applicatie heeft een middleware laag in Express.js.
- NFR-02: De front end van de applicatie wordt gemaakt in TypeScript met Angular.
- NFR-03: De LLM is bereikbaar via een Python Flask API.
- NFR-04: De applicatie maakt gebruik van een MongoDB database.
- NFR-05 De applicatie moet responsive zijn in de meest gebruikte web browsers(MS Edge, Google Chrome, Firefox en Safari). 
