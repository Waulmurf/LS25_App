# Hof Koprek · LS25-Spielstand-Manager

Web-App für den Kartoffelhof „Am Mittellandkanal“ (FS25, savegame2). Die App ist eine einzige Datei (`index.html`), ohne Server und ohne Build.

## Starten

1. `index.html` in **Chrome oder Edge** öffnen (Doppelklick genügt).
2. Auf **Synchronisieren** klicken und einmal den Ordner
   `Dokumente\My Games\FarmingSimulator2025\savegame2` wählen.
   Der Browser merkt sich den Ordner. Bei späteren Syncs fragt er höchstens noch nach der Leseberechtigung.

Andere Browser (Firefox) funktionieren auch. Dort wählst du den Ordner bei jedem Sync neu aus.

## Was die App kann

- **Übersicht:** Monat, Tag (T1–T4) und Jahr, mit Pfeilen zum Weiterschalten. Dazu die heute fälligen und die überfälligen Aufgaben, die Spieleinstellungen im Vergleich zum Plan, Kontostand, Rinder und die Früchte im Planjahr.
- **Arbeit:** Monatsweise Arbeitsübersicht aus dem Arbeitskalender des Betriebskonzepts. Die Felder rechnet die App je Planjahr selbst aus der Fruchtfolge aus. Du kannst eine ganze Aufgabe oder einzelne Felder abhaken, Notizen anlegen und eigene Aufgaben ergänzen (einmalig oder jedes Jahr).
- **Felder:** Linien A–C mit Gruppen und der Frucht in den nächsten vier Planjahren. Geschätzte Hektar kannst du korrigieren. Nach dem Sync steht dort auch, welche Felder dir gehören.
- **Ringtausch:** Je Rotationsjahr (1–4) wählst du ein NPC-Feld. Zur Auswahl stehen die Felder aus dem Spielstand, vorbelegt sind 103, 98, 32 und 33. Die Auswahl übernimmt die Arbeitsübersicht sofort (Übernahme, April legen, Mai Fungizid, Oktober roden, November Rückgabe).
- **Spielstand:** Ordnerwahl, ein Protokoll, welche Datei wofür gelesen wurde, eine Datumskorrektur und die Sicherung bzw. das Laden als JSON.

## Was der Sync liest

| Datei | Daten |
|---|---|
| `careerSavegame.xml` | Karte, Spielstandname, Wirtschaft, Steine. Warnt, wenn es nicht die Karte Mittellandkanal ist. |
| `environment.xml` | `currentDay` und `daysPerPeriod` → Monat, Tag, Jahr |
| `farms.xml` | Betriebsname, Kontostand |
| `farmland.xml` | eigene Felder und NPC-Felder (Auswahl für den Ringtausch) |
| `fields.xml` | Feldinfos, soweit vorhanden |
| `placeables.xml` | Rinder, Fahrsilo |
| `vehicles.xml` | Anzahl Fahrzeuge |
| Mod-Dateien (`*Leasing*`, `*Rotation*` …) | Einträge mit Feldbezug, z. B. Ringtausch-Verträge |

Aus dem Spielstand hakt die App automatisch ab:

- die Spieleinstellungen (4 Tage, Schwer, Steine aus)
- den Kauf von 10 Rindern
- das Fahrsilo
- die Ringtausch-Verträge
- die Übernahme und die Rückgabe der Ringtausch-Felder

Was der Spieler selbst abgehakt hat, überschreibt der Sync nie.

Was die App nicht erkennen kann: Saat, Ernte und Spritzungen stehen nicht in den XML-Dateien. Sie liegen in den Dichtekarten (.gdm). Diese Arbeiten hakst du von Hand ab.

## Daten

Häkchen, Notizen, eigene Aufgaben und die Ringtausch-Auswahl speichert der Browser (localStorage). Unter „Spielstand → Als JSON sichern“ kannst du sie als Datei sichern.
