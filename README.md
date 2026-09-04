# Barcode-etiketten maker

Een zelfstandige webpagina om **Avery-etiketvellen** te vullen met per etiket een
**productnaam** (tekst) en een **scanbare barcode** die een GTIN-, RVG- of ZI-nummer
bevat. Het resultaat is een **Word-bestand (.docx)** dat je direct kunt printen.

Alles draait lokaal in je eigen browser — er wordt niets verstuurd of geüpload.

Het is **één enkel bestand** (`index.html`). Je hoeft niets te installeren, geen
map bij elkaar te houden en geen internet te hebben. Je kunt het gerust op je
bureaublad zetten, kopiëren of mailen.

## Gebruiken

1. **Dubbelklik `index.html`**. De pagina opent in je browser (Chrome of Edge werkt
   het best).
2. **Producten** (stap 1): vul per product de naam in en de nummers die je hebt
   (GTIN / RVG / ZI). Kies bij *"Barcode bevat"* welk nummer als barcode geprint
   moet worden en geef het aantal etiketten op. Met **+ Product toevoegen** maak je
   meerdere producten in één vel.
3. **Avery-template** (stap 2): kies je etiket in het menu. Standaard staat
   **L6140** ingesteld. Alle maten zijn aan te passen en je kunt een eigen template
   **opslaan** (blijft bewaard voor een volgende keer) of **exporteren/importeren**
   als `.json` om op een andere computer te gebruiken.
4. **Barcode-opties** (stap 3): standaard **Code128** (werkt voor alle drie de
   nummertypes). Je kunt het nummer onder de barcode tonen en, om de uitlijning te
   testen, tijdelijk de etiketranden laten meeprinten.

   De productnaam wordt standaard **automatisch passend gemaakt**: hij wordt eerst
   verkleind (tot de ingestelde minimumgrootte) en over maximaal het ingestelde
   aantal regels afgebroken; past hij dan nóg niet, dan wordt hij netjes ingekort
   met een "…". Zet je "Naam automatisch passend maken" uit, dan wordt de gekozen
   lettergrootte altijd gebruikt.
5. Rechts zie je een **schaalgetrouw voorbeeld** van het eerste vel.
6. Klik op **Genereer Word (.docx)**. Het bestand wordt gedownload; open het in
   Word en print het op je Avery-vel.

## Barcodetypes

| Type | Geschikt voor | Opmerking |
|------|---------------|-----------|
| **Code128** | GTIN, ZI én RVG (ook met letters) | Aanrader — werkt altijd |
| **EAN-13 / GTIN** | Geldig 13-cijferig GTIN | Alleen 12/13 cijfers |
| **Code39** | Cijfers + hoofdletters | Breder dan Code128 |

Ongeldige invoer (bijv. een te kort GTIN bij EAN-13) wordt vóór het genereren
gemeld, met vermelding van welk product het betreft.

## Belangrijk: doe eerst een testprint

Printers verschuiven de afdruk soms een paar millimeter. Print daarom eerst één vel
en leg het tegen een echt Avery-vel. Klopt de uitlijning niet helemaal, pas dan in
stap 2 de **marge boven** / **marge links** (en eventueel de tussenruimtes) met
kleine stapjes aan. Zet **"Etiketranden tonen"** aan om de vakjes zichtbaar te maken
tijdens het testen. Print in Word op **100% / werkelijke grootte** (niet
"passend maken").

De ingebouwde standaardmaten benaderen de Avery-specificaties; kleine correcties per
printer zijn normaal.

## Meegeleverde templates

- **Avery L6140** — 45,7 × 25,4 mm, 4 × 10 = 40 per vel
- **Avery L7160 / J8160** — 63,5 × 38,1 mm, 3 × 7 = 21 per vel
- **Avery L7651** — 38,1 × 21,2 mm, 5 × 13 = 65 per vel
- **Avery L7163** — 99,1 × 38,1 mm, 2 × 7 = 14 per vel
- **Aangepast** — vul je eigen maten in en sla ze op

## Technisch

Alles zit in dat ene `index.html`-bestand: de gebruikersinterface, de logica en de
twee meegeleverde bibliotheken (**JsBarcode 3.11.6** voor de barcodes en **docx
8.5.0** voor het Word-bestand) staan er rechtstreeks in verwerkt. Geen build-stap,
geen externe afhankelijkheden, werkt offline.

De barcodes worden als afbeelding op hoge resolutie gerenderd en samen met de
productnaam in een Word-tabel geplaatst waarvan de kolombreedtes, rijhoogtes en
paginamarges exact op het gekozen Avery-vel zijn afgestemd.
