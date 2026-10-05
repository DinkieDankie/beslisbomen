# Fiscale beslisbomen

Interactieve beslisbomen voor de schenk- en erfbelasting en het formele belastingrecht.
Per boom doorloop je de toetsvragen stap voor stap. Bij elk knooppunt staat de onderbouwing:
JUR (rechtspraak), WET (wetgeving), BELEID, LIT (literatuur), OVERIG (feitelijke informatie) of SPEC (oordeel van de specialist,
nog zonder bronverwijzing).

## Opbouw

```
index.html               de site (één bestand, geen build-stap)
data/index.json          menu: onderwerpen en de lijst van bomen
data/bomen/LB-xxx.json   één bestand per beslisboom (LB-001, LB-002, …)
.nojekyll                zorgt dat GitHub Pages de bestanden ongewijzigd serveert
```

De site leest `data/index.json` en daarna per boom het bestand onder `data/bomen/`.
Een boom openen via de URL: `…/#LB-001`.

## Nieuwe boom toevoegen

1. Zet het bestand in `data/bomen/`, bijv. `LB-002.json`.
2. Voeg de boom toe aan `bomen` in `data/index.json`:
   ```json
   { "id": "LB-002", "bestand": "data/bomen/LB-002.json",
     "onderwerp": "formeel-bezwaar", "trefwoorden": ["…"] }
   ```
   `onderwerp` verwijst naar een `id` uit `onderwerpen` (hoofd- of subonderwerp).
3. Nieuw onderwerp nodig? Voeg het toe onder `onderwerpen` (hoofdonderwerp met `sub`-lijst).

## Boom bijwerken

Pas het JSON-bestand aan, verhoog `versie`, zet `datum` (JJJJ-MM-DD) en voeg een regel toe
aan `versiegeschiedenis`. Versie en datum verschijnen automatisch in het menu en op de boom.
Een versie die met `0.` begint of `concept` bevat, wordt als concept getoond.

## Lokaal bekijken

De site laadt JSON via `fetch`, dus niet openen als bestand maar via een lokale server:

```
python3 -m http.server 8000
```

en ga naar http://localhost:8000.
