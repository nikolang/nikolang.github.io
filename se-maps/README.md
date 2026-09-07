# se-maps — Detailkarten für „Suborbital Express" (VRChat)

Dieses Repository liefert die Umfeld-Detailkacheln der Flughäfen für die
VRChat-Welt **Suborbital Express**. Die Welt lädt die Dateien zur Laufzeit
über `https://nikolang.github.io/se-maps/<IATA>_umfeld_2k.png` nach; im
Weltpaket selbst sind sie nicht enthalten.

## Inhalt

| Datei | Inhalt |
|---|---|
| `<IATA>_umfeld_2k.png` | 2048 × 2048, RGBA. **RGB** = Bodenalbedo des Flughafenumfelds (sRGB), **Alpha** = Nachtlichter (linear, Nachtkanal) |

30 Kacheln: ADD, AKL, AMS, BKK, CAI, CDG, CPH, DFW, DWC, FCO, FRA, GRU, HKG,
HND, IST, JED, JFK, LAX, LHR, MEX, MIA, ORD, PVG, SCL, SFO, SIN, SYD, TER,
TPE und weitere. Der geografische Rahmen jeder Kachel (Mittelpunkt, Ausdehnung)
liegt in der Welt selbst (`umfeld_rects.csv`), nicht in der Datei.

## Datenquellen und Nennungen

Die Kacheln sind **abgeleitete Werke** aus den folgenden offenen Datensätzen.
Die Nennungen sind Lizenzbedingung und gelten für jede Weiterverwendung dieser
Dateien.

### Bodenalbedo (RGB)

**Copernicus Sentinel-2 Level-2A** (Bodenreflexion, Sen2Cor), Aufnahmen 2023
und 2024, bezogen über AWS Open Data (`sentinel-cogs`, Katalog „Earth Search"
von Element 84). Mehrere wolkenfreie Aufnahmen je Kachel wurden zu einem
Median bzw. gewichteten Mittel zusammengesetzt und gegen eine Weltkarte
farblich geeicht.

> **Contains modified Copernicus Sentinel data 2023, 2024.**

Lizenz: *Legal notice on the use of Copernicus Sentinel Data and Service
Information* — freie, offene Nutzung einschließlich kommerzieller Nutzung und
abgeleiteter Werke, Nennung wie oben.

### Nachtlichter (Alpha)

**NASA Black Marble VNP46A2** (Suomi-NPP VIIRS Day/Night Band, BRDF-korrigiert,
lückengefüllt), bezogen über **NASA GIBS** (Global Imagery Browse Services),
Median über mehrere Nächte, auf die Kachel gerastert.

> Black Marble nighttime lights: Román, M.O. et al. (2018), *NASA's Black
> Marble nighttime lights product suite*, Remote Sensing of Environment 210,
> 113–143. Imagery provided by services from NASA's Global Imagery Browse
> Services (GIBS), part of NASA's Earth Observing System Data and Information
> System (EOSDIS).

NASA-Daten unterliegen keinem Urheberrecht; NASA bittet um die obige Nennung.

### Struktur- und Maskendaten in der Erzeugung

Bei der Erzeugung der Kacheln (Land/Wasser-Trennung, Belags- und Bebauungs-
masken, Orientierung) wurden außerdem verwendet:

* **OpenStreetMap** — © OpenStreetMap-Mitwirkende, Open Database License
  (ODbL). <https://www.openstreetmap.org/copyright>
* **ESA WorldCover 2021 v200** — © ESA WorldCover project 2021, CC BY 4.0.
  <https://esa-worldcover.org>

Diese beiden Datensätze sind in den Bilddateien nicht als solche enthalten,
haben aber die Erzeugung gesteuert; sie werden vorsorglich genannt.

### Geplant (noch nicht in diesem Repository)

* **Regionalkacheln** (Golf, Mittelmeer, Amazonas): dieselbe Sentinel-2-Quelle;
  offenes Wasser wird dort aus der Weltkarte der VRChat-Welt gefüllt — die
  Quelle dieser Weltkarte wird hier genannt, bevor diese Kacheln erscheinen.
* **Höhenkarten je Flughafen** aus **Copernicus DEM GLO-30**. Pflichtnennung
  dann: *„Copernicus DEM: © DLR e.V. 2010-2014 and © Airbus Defence and
  Space GmbH 2014-2018 provided under COPERNICUS by the European Union and
  ESA; all rights reserved."*

## Lizenz dieser Dateien

Die Kacheln selbst dürfen unter den Bedingungen der oben genannten Quellen
weiterverwendet werden; die Nennungen sind mitzuführen. Die Erzeugungs-
werkzeuge (Python, `detailkarte.py` u. a.) liegen im Projekt der Welt, nicht
hier.

## Technische Hinweise

* Die Alpha ist **kein Transparenzkanal**, sondern der Nachtkanal (0 = dunkel,
  1 = hellste Stadt). Bildbetrachter zeigen die Kacheln deshalb „durchsichtig".
* RGB ist sRGB-kodiert, Alpha linear — beim Herunterrechnen von 4096 auf 2048
  wurden beide getrennt gemittelt (Nachtmittel bleibt bis auf 0,00 % erhalten).
* Änderungen an Dateinamen brechen das Nachladen in der Welt: der Name ist
  `<IATA>_umfeld_2k.png`, exakt.

---
Stand: 2026-09-07. Fragen zur Welt: über das VRChat-Weltprofil von Suborbital Express.
