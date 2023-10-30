---
title: Software architectuur
tags:
  - app-design
  - onderzoeks-rapport.
---

# Architectuur
## Versie 1
Voor dit project wilde ik een JavaScript of Typescript framework gebruiken voor de front end van mijn applicatie, omdat in mijn ervaring dat best goed werkt met een gedistribueerde software architectuur. Daarnaast is mij vanuit mijn het Handpicked Lab aangeraden om express te gebruiken als middleware API. Toen ik wat onderzoek gedaan had kwam ik al heel snel bij de MEAN stack. Dit is iets wat goed in mijn applicatie structuur past. Persoonlijk had ik nog geen ervaring met JavaScript frameworks zoals Express of met NoSQL databases zoal MongoDB. Dit heeft mij niet tegen gehouden van het gebruik maken hiervan.
![Illustratie van de MEAN stack](Mean-stack.png)


## Versie 2
Doordat het gebied van taal modellen een onderdeel van data science bevat is er vooral ondersteuning voor het gebruik hiervan in Python. Hierdoor heb ik besloten om naast mijn Express applicatie nog een Flask API in Python te gebruiken, dit zorgt ervoor dat mijn Express app zich echt als middleware gedraagt tussen mijn web frontend en database of Python flask API. MongoDB heeft een gratis server waar je gratis databases kan hosten. Deze service heet Atlas.
![Illustratie van de applicatie structuur](ArchitectuurV2.png)

# Code styling en structuur
In een applicatie is het belangrijk om een duidelijke structuur en code styling aan te houden om de code onderhoudbaar en leesbaar te houden. Om dit duidelijk te maken zal ik per onderdeel van mijn applicatie de naamgeving, een voorbeeld van de styling en een beschijven van de bestanden structuur met de functie van de verschillende bestanden geven.
## Angular front end
### Naamgeving
Om een uniforme naamgeving te krijgen heb ik ervoor gekozen om zo veel mogelijk camelCase te gebruiken. Hier heb ik wel een uitzondering gemaakt voor de namen van klassen, dit is zodat de export classes worden aangeroepen en niet per sé de componenten zelf.
Bestanden: camelCase
Klassen: PascalCase
Functies: camelCase
Variabelen: camelCase
### Structuur
De kracht van Angular ligt bij het segmenteren van een web pagina in componenten. Deze componenten zorgen ervoor dat je een soort modulaire opmaak neerzet, je kan verschillende onderdelen in elkaar zetten meerdere keren gebruiken. Deze onderdelen hebben best een groot aantal bestanden nodig om goed te functioneren. Je hebt een HTML template, CSS stylesheet en TypeScript export klasse voor de logica. Ik heb er voor gekozen om mijn HTML template te verwerken in mijn TypeScript klasse zodat mijn bestandmap niet te groot wordt. Dat ziet er dus als volgt uit:
```ts
@Component({  
  selector: 'app-home',  
  standalone: true,  
  imports: [  
    CommonModule,  
    ToolComponent  
  ],  
  // html code for the home page  
  template: `  
    <section class="results">      
	    <app-tool        
		    *ngFor="let tool of toolList"  
	        [tool]="tool" >      
	    </app-tool>    
	</section>  `,  
  styleUrls: ['./home.component.css'],  
})  
export class HomeComponent {  
  // initialize the tool list to show on page  
  toolList: Tool[] = [];  
  
  // initialize the tool service  
  toolService: ToolService = inject(ToolService);  
  
  // get the tool list from the database through the tool service on page load  
  constructor() {  
    this.toolService.getAllTools().then((toolList: Tool[]) => {  
      this.toolList = toolList;  
    });  
  }  
}
```

## Express.js API
### Naamgeving
Normaal gesproken zou ik voor alle naamgeving camelCase gebruiken, maar doordat de naamgeving van sommige bestanden met een afkorting heb ik ervoor gekozen om de bestanden in PascalCase te gebruiken.
Bestanden: PascalCase
Functies: camelCase
Variabelen: camelCase
### Voorbeeld styling
```js
function helloWorld(word1, word2) {  
  if(word1 == "Hello" && word2 == "World!"){
	  return word1 + word2
  }
  else{
	  return null;
  }  
}
```
### Structuur
Binnen de Express.js gebruik gebruik ik een Route en Controller structuur. Dit houdt in dat er Route bestanden bestaan die alleen functies vanuit een controller moet aanroepen. Hieronder zie een code snippet van een endpoint in een route bestand.
```js
router.post('/generate', generate);
```

Doordat dit expess project een middleware API is houdt dat in dat deze functioneert als een soort doorgeefluik tussen de verschillende lagen van de applicatie. De controller doet daarom ook niet veel anders dan het doorgeven van ontvangen requests naar een andere API. Hieronder zie je een code snippet van een functie in een controller.
```js
module.exports = {  
    generate: async function(req, res) {  
        const result = await axios.post(baseURL,{  
            topic: req.body.topic,  
            product: req.body.product  
        });  
        console.log(result.data);  
        res.send(result.data);  
    },  
}
```


## Flask API
### Naamgeving
Binnen Python is het standaard om alle naamgeving te doen in snake_case, dit zal ik dus ook aanhouden.
### Voorbeeld styling
```python
def hello_world(word1, word2) :  
  if word1 == "Hello" && word2 == "World!":
	  return word1 + word2
 
  else:
	  return null;
```
### Structuur
De Flask API maakt gebruik van dezelfde routes en controllers structuur als mijn expess.js project. Er bestaat wel een extra laag in de Flaks app. Deze laag is de service, het werkpaard van de applicatie. In de routes staan alleen de endpoints, de controllers roepen de functies aan in de service. Deze service klassen bevatten logica die ervoor zorgt dat er operaties plaats kunnen vinden op een taal model. 

Verder heb ik erover nagedacht waar je de modellen zou opslaan als je het project gebruikt, ik heb gekozen om hiervoor een specifiek mapje aan te maken waar deze opgeslagen moeten worden. Het opslaan van bestaande embeddings voor de LLMs worden ook opgeslagen in een apart mapje zodat er niet elke keer een nieuwe embedding gegenereerd wordt op hetzelfde stukje tekst, dit bespaard tijd bij het bevragen van een LLM met embeddings.

# Versiebeheer
De Git voor het project zelf zal op een trunk-based manier worden vorm gegeven. Dit houdt in dat er een 'trunk branch' is, dit wordt in mijn geval de Master branch, vanuit deze master branch worden er andere branches aangemaakt voor features die van korte levensduur die daarna weer mergen met de master branch, daarbuiten komt er ook een aparte release branch waar de release-ready applicatie naartoe wordt gepusht. 

![[Trunk-development.png]]

Binnen mijn Git omgeving zal ik op twee plekken CI/CD toepassen. Zodra er iets gepusht of gemerget wordt naar de Trunk, gaat een CI/CD kijken of die applicatie wel gebuilt kan worden voordat deze push/merge geaccepteerd wordt. Daarnaast zal er op de release branch de applicatie een CD pipeline ontstaan die automatisch de applicatie pusht naar de plek waar die gehost wordt, zodat de meest recente release versie ook online staat.

Verder ben ik van plan voor elke laag van mijn applicatie een eigen repo te gebruiken. Deze keuze heb ik gemaakt, omdat ik persoonlijk geen fan ben van de monorepo structuur. Deze structuur levert voor mij vaak problemen op bij het integreren van een CI/CD pipeline terwijl ik het voordelen die een monorepo met zich mee neemt amper gebruik, denk aan herbruikbare componenten in de front end.
