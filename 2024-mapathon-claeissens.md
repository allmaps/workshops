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

Als we het hebben over 'een IIIF kaart georefereren', dan bedoelen we dat we aan de hand van een aantal 'grond controle punten' een link zullen maken tussen de pixels van de afbeelding en de geografische coordinaten van een kaart. De informatie die daarvoor nodig is kan worden opgeslagen in een zogenaamde **Georeferentie Annotatie**: een ander klein (online) bestandje dat verwijst naar het IIIF Manifest dat het annoteert, en dat als informatie over dit manifest de controle
punten bevat (telkens een pixel coordinaat en een lat-lon coordinaat), alsook een masker (het deel van de afbeelding waar het over gaat).

Allmaps omvat meerdere tools. De belangrijkste voor ons zijn:

- **Allmaps Editor**: hiermee kunnen IIIF-kaarten, aangeduid via hun IIIF Manifest, gegeorefereerd worden. Aan de hand van deze applicatie kunnen we dus Georeferentie Annotaties maken of bewerken ('editeren', vandaar de naam).
- **Allmaps Viewer**: hiermee kunnen Georeferentie Annotaties worden weergegeven. Deze applicatie leest de controle punten en het masker, vraagt de nodige delen van de afbeelding op via het IIIF Manifest, en geeft de afbeelding vervormd weer op een interactieve kaart.

Er zijn nog andere Allmaps tools die je kan ontdekken op [allmaps.org](https://allmaps.org/). Zo is er bijvoorbeeld [Allmaps Here](https://here.allmaps.org/) dat op basis van je GPS locatie reeds gegeorefereerde kaarten uit je buurt voorstelt en je locatie erop aanduidt. In de toekomst bouwen we ook [Allmaps Explore](https://explore.allmaps.org/) verder uit: een tool om doorheen alle gegeorefereerde kaarten te zoeken.

## Een kaart georefereren in Allmaps Editor

Ga naar de [Allmaps Editor](https://editor.allmaps.org/) applicatie in je browser. Die stelt voor om te starten van een IIIF Manifest via een link, of een kaart te selecteren uit één van de voorgestelde archieven. Wij zullen vandaag werken aan een welbepaalde kaart, beschikbaar via dit IIIF Manifest. Kopieer deze link, plak ze in de Editor en druk op 'Enter'.

```
https://manuelclaeysbouuaert.be/claeissens/tiled-manifest.json
```

Of open de Editor [rechtstreeks](https://editor.allmaps.org/images?url=https%3A%2F%2Fmanuelclaeysbouuaert.be%2Fclaeissens%2Ftiled-manifest.json) op deze IIIF Manifest.

.

> 🛟 **Backups**:
> 
> We voorzien nog enkele backup manifests, voor het geval er iets fout loopt. **Gebruik deze niet**, tenzij de begeleiders het aangeven.
>
> Backup 1: `https://manuelclaeysbouuaert.be/claeissens/manifest.json`
> 
> Backup 2: `https://dam.museabrugge.be/iiif/3/18761/manifest.json`

### De afbeelding selecteren

Nu zie je een pagina met vier tabs: *Images*, *Draw Mask*, *Georeference* en *Results*.

In de *Images* tab kan je uit het manifest een afbeelding selecteren. Een IIIF Manifest kan namelijk meerdere afbeeldingen bevatten.

Voor de opdracht van vandaag, met zo'n uitzonderlijk grote scan, hebben we (ook uitzonderlijk) de afbeelding op voorhand in meerdere 'tegels' opgedeeld. Zo kunnen we met meerderen tegelijk aan dezelfde grote kaart werken. Je kan deze 114 tegels zien onder de *Images* tab. Later zullen we de resultaten van de verschillende tegels weer samenvoegen.

Om verder te gaan, **dubbel-klik op de tegel die je werd toegewezen**.

### Het masker

Nu ben je in de *Draw Mask* tab. Moest je zelf een IIIF Manifest hebben gevonden en willen georefereren, dan was je taak hier om het deel van de afbeelding te tekenen waar de kaart zich bevindt. We noemen dit het 'masker'. Dat is niet altijd de hele afbeelding: soms staat er ook tekst of andere kaarten op een afbeelding, of is er een grote rand die ontstond tijdens het inscannen van de kaart.

In ons geval hebben we deze stap al automatisch uitgevoerd: de hele afbeelding werd geselecteerd als masker. Je kan dus deze stap overslaan en meteen aan de 'Georeference' tab gaan.

### Georefereren

In deze tab zullen we het meeste tijd spenderen: we gaan zo veel mogelijk controle punten ingeven die de historische kaart en de interactieve kaart linken.

Links zie je de afbeelding van de **historische kaart** en je masker. Rechts zie je een **interactieve kaart** het de huidige dorpen en straten.

Er zijn ook enkele knoppen rechts onderaan:

- Er is de *info-knop* <img src="img/info.svg" alt="Info" width="16"/>: hier zie je de meta-data over onze kaart die in het IIIF Manifest omschreven staat.
- Er is de *list-knop* <img src="img/list.svg" alt="List" width="16"/>: hier zie je het automatisch toegekende masker van jou afbeelding, en **vier reeds automatisch toegekende grond controle punten**. Dankzij deze vier punten kon het programma al een transformatie van links naar rechts uitvoeren, en zo je masker ook in het rechtse scherm tekenen. Zo weet je waar te beginnen.
- Er is de *code-knop* <img src="img/code.svg" alt="Code" width="16"/>: hier kan je de Georeferentie Annotatie zien die we aan het maken zijn.
- Er is de *export-knop* <img src="img/export.svg" alt="Export" width="16"/>: hier kan je de Georeferentie Annotatie en andere zaken exporteren.
- Er is de *settings-knop* <img src="img/settings.svg" alt="Settings" width="16"/>: hier kan je de achtergrond van de interactieve kaart straks instellen.

#### Hoe gaat het georefereren in zijn werk?

- **Zoek nu een punt** dat je kan terugvinden op beiden schermen. Bijvoorbeeld een dorpskerk, kruispunt, de bocht van een rivier. Geef dit in als 'grond controle punt' door zowel op de afbeelding als op de interactieve kaart op de overeenkomstige plek te klikken. Er verschijnt een punt met hetzelfde nummer, zodat je weet dat deze twee punten gekoppeld zijn.
- In de *list-knop* <img src="img/list.svg" alt="List" width="16"/> onderaan rechts kan je nagaan dat er voor jouw tegel nu (naast de vier standaard punten die we voor elke tegel ingaven) **een nieuw punt in het lijstje** staat. Het heeft pixel coordinaten én geografische coordinaten. Je kan op het icoontje van de verschillende punten klikken om ernaar te navigeren. (Je zal zien dat de vier standaard punten buiten jou tegen liggen: het zijn de hoekpunten van de volledige afbeelding!). 
- Als je een punt wil **wissen** kan je de vuilbak-knop <img src="img/bin.svg" alt="Bin" width="16"/> gebruik. (Moesten de nummers doorheen raken na het wissen van een punt, kan je best de pagina herladen).
- Het kan handig zijn om de **historische kaart beter te draaien** in dezelfde oriëntatie als de interactieve kaart. Dit kan door `option-shift` (op mac) of `alt-shift` (op windows) in te drukken terwijl je de afbeelding links versleept.
- Het kan handig zijn om een **andere achtergrond laag** in te laden op de interactive kaart. Via de *settings-knop* <img src="img/settings.svg" alt="Settings" width="16"/> kan je bijvoorbeeld een satelliet-kaart instellen. Voor dit gebied zijn er ook een paar specifieke geavanceerde kaarten die beschikbaar gesteld worden door de Vlaamse en Nederlandse Overheid. Je kan één van de links hieronder kopiëren en plakken in het 'Custom XYZ layer' of 'Background Georeference Annotation' veld. Via 'Load' laadt je deze kaart in. Wis de link weer en klik opnieuw op 'Load' om opnieuw de kaartlaag uit 'Background map' weer te geven.

> 🗺️ **Andere achtergrond kaarten**
> 
> Ferrariskaart (1777) - YYZ - BE
> ```
> https://geo.api.vlaanderen.be/HISTCART/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=ferraris&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```
>
> Atlas der Buurtwegen (ca 1840) - XYZ - BE
> ```
> https://geo.api.vlaanderen.be/HISTCART/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=abw&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```
>
> Popp-kaart (1842-1879) - XYZ - BE
> ```
> https://geo.api.vlaanderen.be/HISTCART/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=popp&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```
>
> Digitaal Hoogtemodel Vlaanderen II, multidirectionale hillshade 0,25 m - XYZ - BE
> ```
> https://geo.api.vlaanderen.be/DHMV/wmts?SERVICE=WMTS&VERSION=1.0.0&REQUEST=GetTile&LAYER=DHMV_II_HILL_25cm&STYLE=&FORMAT=image/png&TILEMATRIXSET=GoogleMapsVL&TILEMATRIX={z}&TILEROW={y}&TILECOL={x}
> ```
>
> Topografische Militaire Kaart (1850) - Background Georeference Annotation - NL
> ```
> https://raw.githubusercontent.com/bmmeijers/iiif-annotations/main/series/tmk/20231124.json
> ```

Voeg nu zo veel mogelijk controle punten toe!

### Het resultaat inspecteren

In de *Results* tab kan je het resultaat van de georeferentie inspecteren. Als je een aantal controle punten hebt ingegeven kan je hier zien hoe de historische kaart, aan de hand van je punten, vervormd wordt weergegeven op de huidige interactieve kaart. Dat kan je zien voor jou tegel én alle andere tegels.

- In deze tab kan je niets veranderen, enkel het resultaat weergeven. Dat kan handig zijn om te kijken of er geen foutjes in slopen. Als je bijvoorbeeld ziet dat je kaart op een gekke, onverwachte manier wordt uitgerokken, dan controleer je best nog eens je controle punten.
- De resultaten sluiten waarschijnlijk nog niet perfect aan met naburige tegels. Geen zorgen, hier zorgen we later voor als we alles samenvoegen.
- Je kan het resultaat ook **openen in Allmaps Viewer**. Klik hiervoor op de *export-knop* <img src="img/export.svg" alt="Export" width="16"/>, selecteer `Current Image` (om enkel jou tegel te zien) of `All Images` (om alle tegels te zien) en klik naast 'View in Allmaps Viewer' op het springplank icoontje <img src="img/jump.svg" alt="Jump" width="16"/>.

### Het resultaat weergeven Allmaps Viewer

Allmaps Viewer biedt nog iets meer functionaliteiten aan om het resultaat weer te geven:

- Via de `spatie`-toets kan je de kaart doorzichtig maken.
- Via de `B`-toets of de rechter knop kan je de achtergrond kleur deels verwijderen.
- Via de `M`-toets kan je het masker weergeven.
- Via de `T`-toets kan je het transformatie algoritme veranderen.
- Via de `G`-toets kan je een grid weergeven over de afbeelding.
- Via de `D`-toets kan je distorties (vervorming) weergeven: oppervlakte vervorming, hoekvervorming of geen vervorming.
- Via de `[` en `]`-toetsen kan je door de verschillende kaarten bladeren.
- Via een rechter muisklik op een kaart kan je de volgorde van de kaartlagen aanpassen.

Het kan handig zijn om naast de Editor in een ander venster het resultaat in de Viewer weer te geven. Mogelijk moet je dat venster opnieuw laden om aanpassingen te zien.

### Bonus: een kijkje nemen naar de Georeferentie Annotatie

Als je dat wil kan je in de *code-knop* <img src="img/code.svg" alt="Code" width="16"/> een kijkje nemen naar de Georeferentie Annotatie die we samen aan het maken zijn.

- Onderaan zie je `All images`, `Current image`, `Current map`. Selecteer hier `Current image` zodat je enkel het resultaat van jou tegel ziet (anders zie je ook alle data van alle andere 113 kaarten, en dat wordt teveel).
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
