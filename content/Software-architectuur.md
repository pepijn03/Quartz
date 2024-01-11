---
title: Software architectuur
tags:
  - app-design
  - onderzoeks-rapport
---
Om uiteindelijk goed onderhoudbare applicaties te maken is het belangrijk dat ze volgende een duidelijke gedachtegang in elkaar gezet zijn. Hierdoor ben ik dus gaan kijken naar bestaande manieren om applicaties met meerdere lagen vorm te geven en deze manieren toe te passen binnen mijn project. Daarnaast ben ik ook gaan kijken naar de structuur van elke 'laag' binnen mijn applicatie om de code hiervan overzichtelijk te maken. Uiteindelijk heb ik ook nog een plan over hoe ik de code wil gaan beheren op een Git repository.

# Architectuur
## Versie 1
Voor dit project wilde ik een JavaScript of Typescript framework gebruiken voor de front end van mijn applicatie, omdat in mijn ervaring dat best goed werkt met een gedistribueerde software architectuur. Daarnaast is mij vanuit mijn het Handpicked Lab aangeraden om express te gebruiken als middleware API. Toen ik wat onderzoek gedaan had kwam ik al heel snel bij de MEAN stack. Dit is iets wat goed in mijn applicatie structuur past. Persoonlijk had ik nog geen ervaring met JavaScript frameworks zoals Express of met NoSQL databases zoal MongoDB. Dit heeft mij niet tegen gehouden van het gebruik maken hiervan.

![Illustratie van de MEAN stack](Mean-stack.png)

## Versie 2
Doordat het gebied van taal modellen een onderdeel van data science bevat is er vooral ondersteuning voor het gebruik hiervan in Python. Hierdoor heb ik besloten om naast mijn Express applicatie nog een Flask API in Python te gebruiken, dit zorgt ervoor dat mijn Express app zich echt als middleware gedraagt tussen mijn web frontend en database of Python flask API. MongoDB heeft een gratis server waar je gratis databases kan hosten. Deze service heet Atlas.

![Illustratie van de applicatie structuur](ArchitectuurV2.png)

# Code styling en structuur
In een applicatie is het belangrijk om een duidelijke structuur en code styling aan te houden om de code onderhoudbaar en leesbaar te houden. Om dit duidelijk te maken zal ik per onderdeel van mijn applicatie de naamgeving, een voorbeeld van de styling en een beschrijven van de bestanden structuur met de functie van de verschillende bestanden geven. Daarna wil ik ook nog even een paar stukjes code belichten die niet vaak voorkomen, maar toevallig goede oplossingen waren in de context van het project.
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
    <html>          
	</html>  `,  
  styleUrls: ['./home.component.css'],  
})  
export class HomeComponent {  
  // code goes here   
  
  // get the tool list from the database through the tool service on page load  
  constructor() {}  
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
        const result = await axios.post(url,{data});  
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

# Stukjes code belichten
Er zijn een paar stukjes code waar ik tegenaan gelopen ben tijdens mij  stageopdracht. Deze zou ik graag nog even willen belichten en uitleggen hoe ik deze had opgelost.

## Redirect
Toen ik een sidebar wilde toevoegen die van de enige detail pagina naar de andere zou gaan liep ik tegen het probleem aan dat alleen de URL van de pagina veranderde, maar de content niet. De pagina zou van de ene tool naar de andere moeten gaan. Om te zorgen dat dit wel gebeurde had ik een functie aangemaakt die de content van de pagina opnieuw in ging laden of controleren of deze correct was. Toen dit gedaan werd de conctent gerefreshed voordat de url zich had veranderd. Dit zorgde er dus nog steeds voor dat de pagina niet de correcte content heeft liet zien. Om dit op te lossen was er eigenlijk alleen een timeout nodig van 0 milliseconden. Deze timeout die eigenlijk geen tijd zou moeten kosten zorgde ervoor dat de applicatie niet te refresh uitvoerde voordat de URL werd veranderd. De verandering van de URL en het refreshen van de content waren dus eerst aan het racen om veranderd te worden.

```ts
// refresh page
  refresh(): void {
    setTimeout(() => {
      window.location.reload();
    }, 0);
  }
```

## File upload (Frontend pop-up)
De file upload in de front-end bestaat uit twee verschillende components, de 'normale' component en de 'dialog' component. De 'normale' of 'hoofd' component is een angular bestand dat zich alleen bezig houdt met het importeren van de 'dialog' en een trigger hiervoor weergeeft door middel van een knop.
Dit zorgt ervoor dat het heel makkelijk is om de pop-up dialog te importeren en deze door middel van een knop op te laten komen. Hieronder zie je de structuur van de components en de code van de 'hoofd' component.

![[Components.png]]

```ts
@Component({
  selector: 'file-upload',
  standalone: true,
  template: `
    <button class="button-secondary justify-content-center" (click)="openDialog()">upload zelf een context</button>
  `,
  imports: [MatFormFieldModule, MatInputModule, FormsModule, MatButtonModule]
})

export class FileUploadComponent {
  constructor(
    public dialog: MatDialog,
  ) {}
  
  openDialog(): void {
    const dialogRef = this.dialog.open(FileUploadDialogComponent);
  }
}
```

## File upload (API handling)
Om de bestanden ook echt te uploaden moet je de bestanden ook goed kunnen ontvangen. Om dit goed te doen heb ik een package gebruikt waarmee bestanden opgeslagen kunnen worden in de RAM van de computer. Dit zorgt ervoor dat alle bestanden makkelijk worden door gegeven zonder ze lokaal op te slaan op de schijf van de computer.

```js
const storage = multer.memoryStorage({
    filename: function (req, file, cb) {
        cb(null, Date.now() + '.txt') //Appending .txt
    }
});
```

## Test endpoint
Om dingen beter en sneller te kunnen testen op de Python backend, vond ik het handig om een endpoint te hebben waar ik wat code kon testen zonder een endpoint om te moeten bouwen. Hiervoor heb ik een wrapper gebouwd die ervoor zorgt dat een endpoint alleen beschikbaar is wanneer de applicatie in debug modus opgestard wordt.

```python
# Decorator to make endpoints only accessible in debug run  
def debug_only(f):  
    @wraps(f)  
    def wrapped(**kwargs):  
        if not current_app.debug:  
            abort(404)  
  
        return f(**kwargs)  
  
    return wrapped  
  
  
# Endpoint used for testing specific function, will abruptly change over time, only accessible when run in debug mode  
@app.route("/test")  
@debug_only  
def debug_info():  
    return function(some parameter)
```

## Wordcloud
Een van de tools in de toolbox is het creëren van een woordweb op basis van een context en specifiek onderwerp. Om dit te doen laat ik door een LLM een lijst met woorden genereren op basis van deze context en onderwerp heb ik een scriptje gemaakt die van de woordenlijst omzet in een html img tag die een png maakt op basis van een base64 string. Dit zorgt ervoor dat er geen bestanden heen en weer gestuurd hoeven te worden en alles makkelijk terug wordt gestuurd. Doordat het eigenlijk een html object is hoeft deze alleen nog op de frontend ingeladen te worden. 

```python
def create_wordcloud(wordlist):  
	wordlist = words.split(",")
    word_could_dict = Counter(wordlist)  
    wordcloud = WordCloud(some parameters).generate_from_frequencies(word_could_dict)  
  
    plt.figure(figsize=(15, 8))  
    plt.imshow(wordcloud)  
    plt.axis("off")  
  
    # Save it to a temporary buffer.  
    buf = BytesIO()  
    plt.savefig(buf, format="png", bbox_inches='tight')  
    # Embed the result in the html output.  
    data = base64.b64encode(buf.getbuffer()).decode("ascii")  
    return f"<img src='data:image/png;base64,{data}'/>"
```


# Versiebeheer
De Git voor het project zelf zal op een trunk-based manier worden vorm gegeven. Dit houdt in dat er een 'trunk branch' is, dit wordt in mijn geval de Master branch, vanuit deze master branch worden er andere branches aangemaakt voor features die van korte levensduur die daarna weer mergen met de master branch, daarbuiten komt er ook een aparte release branch waar de release-ready applicatie naartoe wordt gepusht. 

![[Trunk-development.png]]

Binnen mijn Git omgeving zal ik op twee plekken CI/CD toepassen. Zodra er iets gepusht of gemerget wordt naar de Trunk, gaat een CI/CD kijken of die applicatie wel gebuilt kan worden voordat deze push/merge geaccepteerd wordt. Daarnaast zal er op de release branch de applicatie een CD pipeline ontstaan die automatisch de applicatie pusht naar de plek waar die gehost wordt, zodat de meest recente release versie ook online staat.

Verder ben ik van plan voor elke laag van mijn applicatie een eigen repo te gebruiken. Deze keuze heb ik gemaakt, omdat ik persoonlijk geen fan ben van de monorepo structuur. Deze structuur levert voor mij vaak problemen op bij het integreren van een CI/CD pipeline terwijl ik het voordelen die een monorepo met zich mee neemt amper gebruik, denk aan herbruikbare componenten in de front end.

# Bronnen
Atlassian. (n.d.). Trunk-based development | Atlassian. https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development

Express Tutorial Part 4: Routes and controllers - Learn web development | MDN. (2023, October 18). MDN Web Docs. https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/routes

Lo, V. (2020, August 29). Build a REST API with Node.js: Routes and Controllers. Articles by Victoria Lo. https://lo-victoria.com/build-a-rest-api-with-nodejs-routes-and-controllers

MongoDB. (n.d.). What is the MEAN Stack? Introduction & examples. https://www.mongodb.com/mean-stack

Paul-Hammant. (n.d.). Trunk based development. Trunk Based Development. https://trunkbaseddevelopment.com/