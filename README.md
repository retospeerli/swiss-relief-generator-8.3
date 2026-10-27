## v8.3.11

- Gebäudedreiecke werden vor Vorschau/STL geometrisch dedupliziert.
- Doppelte, deckungsgleiche swissBUILDINGS³D-Schalen werden nicht mehr mehrfach ausgegeben.
- Keine neue Ruinen- oder Höhenlogik.

## v8.3.10

- kompletter swissBUILDINGS³D-Geometriepfad 1:1 aus v0.6.17 übernommen
- Gebäude nur bei Drehung 0°; dadurch keine Änderungen am stabilen Gebäudecode nötig
- Terrain-/Kachelstand bleibt aus v8.3.9

## v8.3.9

- Gebäudegenerierung vollständig auf den stabilen v8.1-Stand zurückgesetzt.
- Entfernt: Gebäude-Verbundlogik, Schwebe-Erkennung, automatische Objektabsenkung und Ruinen-Sonderbehandlung.
- Terrain-/Kachelwahl aus v8.3.8 bleibt erhalten.

## v8.3.8

- entfernt die fehlerhafte starre 1-km-Kachel-Z-Korrektur aus v8.3.6/v8.3.7
- pro swissALTI³D-Kachel wird genau eine deterministische Primärquelle gewählt
- bei Downloadfehlern wird dieselbe Quelle wiederholt; kein Wechsel auf älteren Jahrgang
- lieber Abbruch als Mischung verschiedener Terrainstände
- Gebäudelogik bleibt auf stabilem Stand v8.3.1

## v8.3.7

- Priorität normale Gebäude: Gebäudegenerierung vollständig auf stabilen Stand v8.3.1 zurückgesetzt.
- Sämtliche späteren Ruinen-Capping-/Kronen-Sonderalgorithmen entfernt.
- Kachelnaht-/Höhenkorrekturen aus v8.3.6 bleiben erhalten.

## v8.3.6

- robustere Primär-Kachelladung vor Jahrgangs-/Auflösungs-Fallback
- automatische Prüfung der 1-km-swissALTI³D-Kachelgrenzen auf systematische Höhenversätze
- nur konsistente vertikale Kacheloffsets werden starr korrigiert; keine globale Glättung
- geeignet auch für gedrehte Reliefausschnitte

## v8.3.5

- Mauerkronen werden topologisch statt per Delaunay-Heuristik geschlossen.
- Fundament- und Modellrandkanten werden ausgeschlossen; alle übrigen offenen Oberkanten muessen zu geschlossenen Kronenpolygonen werden.

## v8.3.4

- offene, parallele Mauerkronen von Ruinen werden nun als lokale Streifen trianguliert und geschlossen
- grosse Delaunay-Bruecken ueber Innenhoefe/getrennte Mauern werden per lokaler Kantenlaenge verworfen

## v8.3.3

- Ruinen: robuste starre Sockelkorrektur statt maximaler Absenkung
- verbleibende Fundamentunterschiede werden lokal ins Terrain verlaengert
- offene Mauerkronen werden gedeckelt
- normale Gebaeudegeometrie bleibt starr gekoppelt

## v8.3.1

Fix: Die komplette Seitenwand wird jetzt aus exakt denselben Randkanten wie die geclippte Terrainoberfläche erzeugt. Gerade Seiten und R=5-mm-Rundungen schliessen dadurch bis zur tatsächlichen Geländekante sauber und wasserdicht ab. Die Unterkante zur Druckplatte bleibt scharf.

## v8.3.1

- Vier vertikale Modellecken mit festem Radius 5 mm abgerundet.
- Radius bleibt unabhängig von Modellgrösse immer 5 mm.
- Terrainoberfläche und Seitenwand folgen derselben abgerundeten Grundform.
- Bodenfläche bleibt plan; die umlaufende Kante zur Druckplatte bleibt scharf (keine Fase, keine Bodenverrundung).
- 16 Segmente pro Viertelkreis für drucktaugliche Rundungen.

## v8.2.2

## Fix v8.2.2
Schwebe-Korrektur nur noch pro starrem Gebäudeverbund. Dach, Fassaden und Gebäudekörper werden bei überlappendem Grundriss gemeinsam verschoben; kein separates Absinken von Dachkomponenten mehr.


- Schwebende zusammenhängende swissBUILDINGS³D-Objekte werden robust erkannt.
- Bei deutlich über dem lokalen Terrain liegender Basis wird der gesamte Objektkörper starr abgesenkt.
- Besonders für Ruinen/offene Mauergeometrien: keine künstliche Verlängerung der Mauerhöhe.
- Objektform und relative Höhe bleiben unverändert.
- Technisches Log zeigt erkannte Basislücke und angewandte Absenkung.

# Swiss Relief STL Generator v8.1

## Neu in v8.1
- Auswahlrahmen direkt auf der Karte per Mittelpunkt-Griff verschieben
- Auswahlrahmen direkt auf der Karte mit ↻-Griff frei drehen
- Drehwinkel wird live ins Eingabefeld übernommen
- swissBUILDINGS³D wird auch bei gedrehten Ausschnitten in das lokale Reliefkoordinatensystem transformiert
- Randhäuser werden weiterhin am tatsächlichen Modellrand gekappt und geschlossen

Neue Hauptfunktion in Version 8:
- frei drehbarer Auswahlrahmen
- Auswahl als freies Rechteck, Quadrat oder festes Seitenverhältnis
- optional fixer Kartenmassstab
- Modellformat bereits bei der Auswahl definierbar
- weiterhin Quelle: swisstopo (swissALTI³D, swissALTIRegio, swissBUILDINGS³D)


Swiss Relief STL Generator v0.6.19

Daten: swissALTI³D · swissALTIRegio · swissBUILDINGS³D · Quelle: swisstopo

# Swiss Relief STL Generator

**Autor:** Reto Speerli

## v0.6 – Abdeckung und Kachelgrenzen

- STAC-Abfrage wird aus der tatsächlichen LV95-Modellfläche berechnet, nicht aus dem ursprünglichen Kartenrechteck.
- Automatischer Coverage-Recovery-Pass für fehlende Zielrasterpunkte.
- Exaktes LV95-Sampling auf nativen GeoTIFF-Pixeln.
- Werte auf gemeinsamen 1-km-Kachelgrenzen werden gemittelt statt von einem zufälligen Download überschrieben.
- Interpolation wird erst nach vollständigem Quellen-Fallback und nur für winzige isolierte NoData-Reste verwendet.
- Keine STL-Ausgabe, solange echte Lücken vorhanden sind.


Reine Browser-Web-App für 3D-druckbare Gelände-Reliefs aus **swissALTI³D** von swisstopo. Läuft ohne Backend auf GitHub Pages.

## Version 0.2 – Robustheits-/Performance-Update

- automatische Wahl zwischen 2-m- und 0,5-m-Quelle passend zur tatsächlichen Mesh-Auflösung
- 2-m-COGs werden als kompakte Komplettdatei geladen (~1 MB/Kachel statt ~26 MB bei 0,5 m)
- bis zu 6 Kacheln parallel
- Wiederholungsversuche bei Netzwerkfehlern
- Fallback auf ältere Jahrgänge derselben 1-km-Kachel
- Fallback auf alternative Auflösung
- kleine NoData-Restlücken werden interpoliert
- **keine STL bei verbleibenden Höhenlücken** – rechteckige Krater durch fehlende Kacheln werden nicht mehr exportiert
- korrigierte Berechnung der STL-Dreiecksanzahl/Puffergrösse (behebt `RangeError: Offset is outside the bounds of the DataView`)

## Installation auf GitHub Pages

1. Inhalt dieses Ordners in das Repository kopieren.
2. GitHub → Settings → Pages.
3. `Deploy from a branch`, Branch `main`, Ordner `/ (root)`.
4. Speichern.

Es ist kein Build-Schritt erforderlich.

## Bedienung

1. Rechteck auf der Karte aufziehen.
2. Modellbreite, Basis, Höhenüberhöhung und Mesh-Auflösung wählen.
3. `Automatisch – empfohlen` bei Quelldaten belassen.
4. Relief laden.
5. Nach erfolgreicher vollständiger Datenprüfung STL herunterladen.

## Warum Automatik?

swissALTI³D wird in 1-km²-Kacheln angeboten. Eine 0,5-m-COG-Kachel ist laut swisstopo ungefähr 26 MB gross, eine 2-m-COG-Kachel ungefähr 1 MB. Bei grossflächigen Druckreliefs liegt der Abstand der STL-Meshpunkte meist deutlich über 2 m in der Realität; dann liefert 0,5 m keine zusätzliche druckbare Geometrie, verursacht aber ein Vielfaches an Datenverkehr.

Daten: © swisstopo, swissALTI³D.


## v0.3 – Kachelnaht-Fix
- GeoTIFF-Kacheln werden nicht mehr separat auf Teilraster skaliert.
- Jeder Zielpunkt wird an seiner exakten LV95-Koordinate bilinear aus nativen Rasterpixeln berechnet.
- 1-km-Kachelgrenzen erhalten eine gezielte, gradientenerhaltende Nahtkorrektur; kein globaler Blur.

## Grenzgebiete (v0.6)
Wenn swissALTI3D am Landesrand keine Daten mehr liefert, ergänzt die App fehlende Rasterpunkte automatisch aus swissALTIRegio (10 m, LV95). Bereits vorhandene hochauflösende swissALTI3D-Punkte werden nicht überschrieben. swissALTIRegio reicht mindestens 100 km über die Schweizer Landesgrenze hinaus.


## Neu in v0.6 – optionale Gebäude

- Checkbox **Gebäude darstellen (swissBUILDINGS³D)**.
- Die Checkbox wird nur freigeschaltet, wenn der Druckmassstab für Gebäude sinnvoll ist (standardmässig bis etwa 1:15'000) und die gewählte Fläche nicht zu gross ist.
- Quelle: offizieller 3D-Tiles-Dienst `ch.swisstopo.swissbuildings3d.3d`.
- Gebäude werden an das bereits berechnete Terrain angeglichen und zusammen mit dem Relief in dieselbe STL geschrieben.
- Bei kleinen Druckmassstäben wird die Gebäudehöhe druckgerecht verstärkt, damit typische Gebäude nicht unter der praktisch druckbaren Höhe verschwinden.
- Bei ungeeignetem Massstab oder zu grosser Fläche deaktiviert die App die Checkbox automatisch und nennt den Grund.

Die Gebäudefunktion ist für Orts-, Quartier- und kleinere Landschaftsmodelle gedacht. Für Kantons- oder Grossregionsmodelle bleibt sie bewusst deaktiviert.


## v0.6.9
Gebäude an Hanglagen werden nicht mehr punktweise an das Gelände verformt. Die Gebäudehöhe bleibt geometrisch stabil; untere Fassadenkanten werden lokal bis leicht unter die Terrainoberfläche verlängert, damit keine schwebenden Häuser/Sockel entstehen.


## v0.6.19
- Gebäude werden nicht mehr mit der Gelände-Höhenüberhöhung gestreckt.
- Jeder zusammenhängende Gebäudekörper bleibt geometrisch starr und erhält nur einen konstanten Z-Versatz passend zur lokalen Terrain-Überhöhung.
- Fundamente werden weiterhin nur nach unten ins Gelände verlängert.


## v0.6.19
Randgebäude werden nicht mehr dreiecksweise abgeschnitten. Jeder zusammenhängende Gebäudekörper, der den Reliefrahmen überschreitet, wird vollständig ausgelassen. Dadurch entstehen am Modellrand keine offenen Gebäude-Meshes.

## v8.2.2
- schwebende Gebäudeverbünde werden nur anhand ihrer tatsächlichen unteren Hülle ausgerichtet
- Dach/Fassade/Körper bleiben starr gekoppelt
- Relief-Überhöhung wird einmal pro Gebäudeverbund angewendet
- die erkannte Fundament-Unterkante wird im fertigen Modell vollständig um 0.18 mm ins lokale Terrain eingebettet
