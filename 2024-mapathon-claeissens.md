# Mapathon 1571 - verbind het Brugse Vrije met vandaag

> 14 en 15 maart, 2024
> 
> Stadsarchief Brugge
> 
> [mappingpourbus.ugent.be](https://mappingpourbus.ugent.be)

## Over deze workshop

Tijdens deze workshop georefereren we samen *Antonius Claeissens’* geschilderde kaart van het *Brugse Vrije*.

De kaart is gedigitaliseerd en werd opgedeeld in een honderdtal tegels. Elke deelnemer zal individueel in één of meerdere tegels op zoek gaan naar referentiepunten.

Deze tekst dient als handleiding bij het gebruik van de applicatie *Allmaps Editor*, die we daartoe zullen hanteren. 

## Over Allmaps

[Allmaps](https://allmaps.org/) is een set tools die specifiek ontwikkeld zijn om **IIIF-kaarten** te georefereren, en gegeorefereerde kaarten weer te geven. Deze 'IIIF-kaarten' zijn digitale scans van historische kaarten die online beschikbaar zijn via het [IIIF Framework](https://iiif.io/). 

IIIF op zijn beurt is het **International Image Interoperability Framework** dat werd ontwikkeld om hoge resolutie afbeeldingen (dat kunnen scans van kaarten zijn, maar ook scans van oude boeken of foto's uit de medische beeldvorming) op een werkbare manier online bruikbaar te maken. Via deze standaard kunnen computers een deel van zo'n afbeelding (bijvoorbeeld enkel links-boven) en een bepaald zoom-niveau (bijvoorbeeld 8x ingezoomd) opvragen. Zo wordt hoge resolutie afbeeldingen weergeven mogelijk zonder dat de volledige afbeelding (die soms meerdere gigabytes groot is) bij de gebruiker moet worden gedownload. Het IIIF Framework maakt dit mogelijk door een afbeelding te beschrijven in een zogenaamd **IIIF Manifest**: een klein documentje dat online beschikbaar is en uitlegt welke zoom-niveau's kunnen worden opgevraagd en wat de meta-data is (zoals de grootte en de titel).

Als we het hebben over 'een IIIF kaart georefereren', dan bedoelen we dat we aan de hand van een aantal 'Grond Controle Punten' een link zullen maken tussen de pixels van de afbeelding en de geografische coordinaten van een kaart. De informatie die daarvoor nodig is kan worden opgeslagen in een zogenaamde **Georeferentie Annotatie**: een ander klein (online) bestandje dat verwijst naar het IIIF Manifest dat het annoteert, en dat als informatie over dit manifest de controlepunten bevat (telkens een pixel coordinaat en een lat-lon coordinaat), alsook een masker (het deel van de afbeelding waar het over gaat).

Allmaps omvat meerdere tools. De belangrijkste voor ons zijn:

- **Allmaps Editor**: hiermee kunnen IIIF-kaarten, aangeduid via hun IIIF Manifest, gegeorefereerd worden. Aan de hand van deze applicatie kunnen we dus Georeferentie Annotaties maken of bewerken ('editeren', vandaar de naam).
- **Allmaps Viewer**: hiermee kunnen Georeferentie Annotaties worden weergegeven. Deze applicatie leest de controle punten en het masker, vraagt de nodige delen van de afbeelding op via het IIIF Manifest, en geeft de afbeelding vervormd weer op een interactieve kaart.

Er zijn nog andere Allmaps tools die je kan ontdekken op [allmaps.org](https://allmaps.org/). Zo is er bijvoorbeeld [Allmaps Here](https://here.allmaps.org/) dat op basis van je GPS locatie reeds gegeorefereerde kaarten uit je buurt voorstelt en je locatie erop aanduidt.

## Een kaart georefereren in Allmaps Editor

Ga naar de [Allmaps Editor](https://editor.allmaps.org/) applicatie in je browser. Die stelt voor om te starten van een IIIF Manifest via een link, of een kaart te selecteren uit één van de voorgestelde archieven. Wij zullen vandaag werken aan een welbepaalde kaart, beschikbaar via dit IIIF Manifest. Kopieer deze link, plak ze in de Editor en druk op 'Enter'.

```
https://dam.museabrugge.be/iiif/3/18761/manifest.json
```

Of open de Editor [rechtstreeks](https://editor.allmaps.org/images?url=https%3A%2F%2Fdam.museabrugge.be%2Fiiif%2F3%2F18761%2Fmanifest.json) op deze IIIF Manifest.

### De afbeelding selecteren

Nu zie je een pagina met vier tabs: *Images*, *Draw Mask*, *Georeference* en *Results*.

In de *Images* kan je uit het manifest een afbeelding selecteren. Een IIIF Manifest kan namelijk meerdere afbeeldingen bevatten. Ons manifest bevat er slechts één. Dubbel-klik op de enige afbeelding die voorgesteld wordt.

### Het masker

Nu ben je in de *Draw Mask* tab. Moest je zelf een IIIF Manifest hebben gevonden en willen georefereren, dan was je taak hier om het deel van de afbeelding te tekenen waar de kaart zich bevind. We noemen dit het 'masker'. Dat is niet altijd de hele afbeelding: soms staat er ook tekst of andere kaarten op een afbeelding, of is er een grote rand die ontstond tijdens het inscannen van de kaart.

Voor de opdracht van vandaag, met zo'n uitzonderlijk grote scan, hebben we de afbeelding **al in meerdere kaarten (of 'maskers' of 'tegels') opgedeeld**. Je kan deze 114 tegels zien op de afbeelding, en je kan een tegel selecteren via één van de knoppen rechts onderaan.

- Er is de *info-knop* <img src="img/info.svg" alt="Info" width="16"/>: hier zie je de meta-data over onze kaart die in het IIIF Manifest omschreven staat.
- Er is de *list-knop* <img src="img/list.svg" alt="List" width="16"/>: hier zie je de 114 reeds aangemaakte tegels. **Je kan een tegel selecteren** door op de naam 'Map 1', 'Map 2' etc te klikken.
- Er is de *code-knop* <img src="img/code.svg" alt="Code" width="16"/>: hier kan je de Georeferentie Annotatie zien die we aan het maken zijn.
- Er is de *export-knop* <img src="img/export.svg" alt="Export" width="16"/>: hier kan je de Georeferentie Annotatie en andere dingen exporteren.
- Er is de *settings-knop* <img src="img/settings.svg" alt="Settings" width="16"/>: hier kan je de achtergrond van de kaart straks instellen.

**Selecteer dus je tegel** door bij de de *list-knop* <img src="img/list.svg" alt="List" width="16"/> op de overeenkomstige naam te klikken. Er wordt automatisch ingezoomd op te tegel. Controleer dat het de juiste is door zijn locatie in de rijen en kolommen na te gaan.

> ⚠️ **Let op: Verander het masker niet**
> 
> Selecteer een masker/tegel via de *list-knop* <img src="img/list.svg" alt="List" width="16"/>. Klik daartoe niet op de afbeelding op een specifiek masker/tegel. Dit is hoe je een nieuw maskers zou maken of een bestaand masker zou veranderen. Voor deze opdracht laten we de maskers echter zoals ze zijn voorgesteld. Als je per ongeluk een masker aanpast, licht een begeleider in.
>
> (Indien nodig kan je een punt van een masker verwijderen door erop te klikken terwijl je de `shift` toets ingedrukt houdt).

### Georefereren

Eens je de juiste tegel hebt geselecteerd navigeer je naar de *Georeference* tab. Hier zullen we het meeste tijd spenderen: we gaan zo veel mogelijk controle punten ingeven die de afbeelding en de kaart linken.

- Links zie je de afbeelding van de **historische kaart en je masker**. Rechts zie je een **interactieve kaart** het de huidige dorpen en straten.
- **Zoek nu een punt** dat je kan terugvinden op beiden. Bijvoorbeeld een dorpskerk, kruispunt, de bocht van een rivier. Geef dit in als controlepunt door zowel op de afbeelding als op de interactieve kaart op de overeenkomstige plek te klikken. Er verschijnt een punt met hetzelfde nummer, zodat je weet dat deze twee punten gekoppeld zijn.
- In de *list-knop* <img src="img/list.svg" alt="List" width="16"/> onderaan kan je nagaan dat er voor jouw kaart nu (naast de vier standaard punten die we voor elke kaart ingaven) nu **een nieuw punt in het lijstje** staat. Het heeft pixel coordinaten én geografische coordinaten. Je kan op het icoontje van de verschillende punten klikken om ernaar te navigeren. (Je zal zien dat de vier standaard punten buiten jou tegen liggen: het zijn de hoekpunten van de volledige afbeelding!). 
- Als je een punt wil **wissen** kan je de vuilbak-knop <img src="img/bin.svg" alt="Bin" width="16"/> gebruik. Vraag een begeleider om dit te komen doen. (Als je per ongeluk op de vuilbak-knop naar je kaart klikt kan je al je punten in één keer wissen en moet je helemaal opnieuw beginnen!) (Als de nummers doorheen raken na het wissen van een punt, kan je best de pagina herladen).
- Het kan handig zijn om de historische **kaart beter te draaien**. Dit kan door `option-shift` (op mac) of `alt-shift` (op windows) in te drukken terwijl je de kaart afbeelding versleept.
- Het kan handig zijn om een **andere achtergrond laag** in te laden op de interactive kaart. Via de *settings-knop* <img src="img/settings.svg" alt="Settings" width="16"/> kan je bijvoorbeeld een satelliet-kaart instellen. Voor dit gebied zijn er ook een paar specifieke geavanceerde kaarten die beschikbaar gesteld worden door de Vlaamse Overheid. Je kan één van de links hieronder kopiëren en plakken in het 'Custom XYZ layer' veld. Via 'Load' laadt je deze kaart in. Wis de link weer en klik opnieuw op 'Load' om opnieuw de kaartlaag uit 'Background map' weer te geven.

> 🗺️ **Andere achtergrond kaarten**
> 
> Ferrariskaart (1777)
> ```
> https://geo.api.vlaanderen.be/HISTCART/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=ferraris&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```
>
> Atlas der Buurtwegen (ca 1840)
> ```
> https://geo.api.vlaanderen.be/HISTCART/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=abw&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```
>
> Popp-kaart (1842-1879)
> ```
> https://geo.api.vlaanderen.be/HISTCART/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=popp&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```
>
> Digitaal Hoogtemodel Vlaanderen II, multidirectionale hillshade 0,25 m
> ```
> https://geo.api.vlaanderen.be/DHMV/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=DHMV_II_HILL_25cm&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```

Voeg nu zo veel mogelijk controle punten toe!

### Het resultaat inspecteren

In de *Results* tab kan je het resultaat van de georeferentie inspecteren. Als je een aantal controle punten hebt ingegeven kan je hier zien hoe de historische kaart, aan de hand van je punten, vervormd wordt weergegeven op de huidige interactieve kaart. Dat kan je zien voor jou tegel én alle andere tegels.

- In deze tab kan je niets veranderen, enkel het resultaat weergeven. Dat kan handig zijn om te kijken of er geen foutjes in slopen. Als je bijvoorbeeld ziet dat je kaart op een gekke, onverwachte manier wordt uitgerokken, dan controleer je best nog eens je controle punten.
- De resultaten sluiten waarschijnlijk nog niet perfect aan. Geen zorgen, hier zorgen we later voor als we alles samenvoegen.
- Je kan het resultaat ook openen in Allmaps Viewer. Klik hiervoor op de *export-knop* <img src="img/export.svg" alt="Export" width="16"/>, selecteer 'Current Map' en klik naast 'View in Allmaps Viewer' op het springplank icoontje <img src="img/jump.svg" alt="Jump" width="16"/>.

### Het resultaat weergeven Allmaps Viewer

Allmaps Viewer biedt nog iets meer functionaliteiten aan om het resultaat weer te geven:

- Via de `spatie`-toets kan je de kaart doorzichtig maken.
- Via de `B`-toets of de rechter knop kan je de achtergrond kleur deels verwijderen.
- Via de `M`-toets kan je het masker weergeven.
- Via de `T`-toets kan je het transformatie algoritme veranderen.
- Via de `G`-toets kan je een grid weergeven over de afbeelding.
- Via de `D`-toets kan je distorties (vervorming) weergeven: oppervlakte vervorming, hoekvervorming of geen vervorming.
- Via de `[` en `]`-toetsen kan je door de verschillende kaarten bladeren.
- Via een rechter muisklik kan je de volgorde van de kaartlagen aanpassen.

Het kan handig zijn om naast de Editor in een ander venster het resultaat in de Viewer weer te geven. Mogelijk moet je dat venster opnieuw laden om aanpassingen te zien.

### Bonus: een kijkje nemen naar de Georeferentie Annotatie

Als je dat wil kan je in de *code-knop* <img src="img/code.svg" alt="Code" width="16"/> een kijkje nemen naar de Georeferentie Annotatie die we samen aan het maken zijn.

- Onderaan zie je `All images`, `Current image`, `Current map`. Selecteer hier `Current map` zodat je enkel het resultaat van jou tegel ziet (anders zie je ook alle data van alle andere 113 kaarten, en dat wordt teveel).
- In de code kan je nu op zoek gaan naar de volgende elementen.
  1) Een referentie naar de IIIF Resource die we annoteren (onder `source`).
  2) Een masker dat beschrijft over welk deel van de afbeelding het gaat (onder `selector`).
  3) De controle punten (onder `features`).
- Dit bestand is conform de standaard beschreven in de [Georeference Extension](https://iiif.io/api/extension/georef/), een open standaard om bronnen te beschrijven ('annoteren') met georeferentie informatie. Daardoor is de informatie in dit bestand leesbaar voor alle programma's die met deze standaard overweg kunnen.

De annotatie die we vandaag maken wordt online opgeslagen in een open database. Later zullen we de informatie uit alle tegels aan elkaar plakken en één grote annotatie maken die de hele afbeelding beschrijft!

## Afronden

Eens je op alle plaatsen waar je een overeenstemming ziet een controle punt hebt toegevoegd, kan je je tegel terugbrengen en eventueel een nieuwe nemen.

Later zullen we alle tegels en hun controle punten samenvoegen tot één grote continue gegeorefereerde kaart.

Heb je vragen over Allmaps, vandaag of morgen, aarzel niet ons te contacteren. Dat kan via email op [hello@allmaps.org](mailto:hello@allmaps.org).

Bedankt voor je deelname vandaag!

> ⏰ **Later zelf aan de slag**
> 
> Als je na vandaag de smaak te makken hebt kan je op zoek gaan naar andere kaarten (bijvoorbeeld uit [de kaart-collectie van de Musea Brugge](https://www.museabrugge.be/collecties/doorzoek?subject=topografie)). Als je doorklikt op een afbeelding en het IIIF Manifest vindt, kan je hetzelfde proces als vandaag doorlopen om je zelf-gekozen IIIF kaart te georefereren!
