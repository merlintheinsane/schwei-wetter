# Schweißwetter – Wetterstation

Wetterstation mit **Schweißampel** für Schutzgasschweißen im Freien: bewertet die nächsten 7 Tage danach, ob Wind, Böen und Regen das Arbeiten erlauben – auf Basis von vier Wettermodellen (ICON/DWD, ECMWF, GFS, Météo-France).

| Datei | Wofür |
|---|---|
| `index.html` | Desktop- bzw. Display-Version (1280 × 720, später auf dem Raspberry Pi 4) |
| `mobile.html` | Handy-Version (Hochformat, kann auf den Home-Bildschirm gelegt werden) |

## Funktionen

- **Schweißampel** (grün/gelb/rot) je Tag und Stunde für ein einstellbares Arbeitsfenster, mit Grenzwerten für Mittelwind und Böen, Windschutz-Option, Kondensat-Warnung (Taupunkt) und Angabe, wie einig sich die Modelle sind
- **Übersicht**: aktuelles Wetter, 24-Stunden-Diagramm mit Modellstreuung
- **Regenradar** des DWD mit 2-Stunden-Vorhersage auf einer Vektorkarte; die Regenbewegung zwischen den Radarbildern wird per optischem Fluss berechnet und stufenlos animiert

## Nutzung

Datei im Browser öffnen. Beim ersten Start den Ort (PLZ oder Name) in den Einstellungen wählen – er wird nur im Browser des jeweiligen Geräts gespeichert.

Ohne Internetverbindung (oder in eingeschränkten Vorschau-Umgebungen) startet automatisch ein Demo-Modus mit Beispieldaten.

## Datenschutz

- Keine Anmeldung, kein Tracking, keine Cookies, kein eigener Server – die Seite ist rein statisch.
- Einstellungen (Ort, Grenzwerte, ob das Intro gesehen wurde) bleiben im Browser des jeweiligen Geräts (`localStorage`) und werden nicht übertragen.
- Schriften (`fonts/`) und Kartenbibliothek (`lib/`) liegen im Repo, damit keine Anfragen an Google Fonts oder CDNs gehen.
- Für die Anzeige fragt der Browser direkt bei den unten genannten Datenquellen an; diese sehen dabei die IP-Adresse des Besuchers. Ausgeliefert wird die Seite über GitHub Pages.

## Datenquellen

- Wettermodelle: [Open-Meteo](https://open-meteo.com)
- Regenradar: [Deutscher Wetterdienst](https://www.dwd.de) (WMS `dwd:Niederschlagsradar`)
- Ortssuche: [Photon](https://photon.komoot.io) (OpenStreetMap)
- Karte: [OpenFreeMap](https://openfreemap.org), © OpenMapTiles, © OpenStreetMap-Mitwirkende, dargestellt mit [MapLibre GL JS](https://maplibre.org) (BSD-3, siehe `lib/MAPLIBRE-LICENSE.txt`)
- Schrift: Barlow / Barlow Condensed (SIL Open Font License, siehe `fonts/OFL-LICENSE.txt`)

## Geplant

- Raspberry Pi 4 im Kiosk-Modus mit Touch-Display, Auto-Update aus diesem Repo
- Push-Benachrichtigungen aufs iPhone
- Später: eigene Sensoren und Control Panel (läuft nur lokal auf dem Pi, nicht hier im Repo)
