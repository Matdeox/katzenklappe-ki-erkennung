# Projekt: KI-basierte Zutrittsregelung für Katzen (Maus-Erkennung)

Dieses Repository enthält die Automations-Logik für eine intelligente Katzenklappe. Das System nutzt Bilderkennung (Vision AI), um zu verhindern, dass Beutetiere ins Haus gebracht werden.

## 1. Einordnung als Regelkreis
Entsprechend der steuerungstechnischen Anforderungen wurde das System als **geschlossener Regelkreis** realisiert:

* **Führungsgröße (Soll-Wert):** Hauszustand "mausfrei" / Zutritt nur ohne Beute.
* **Regelgröße (Ist-Wert):** Aktuelle Bildanalyse der Kamera (Katze mit/ohne Beute).
* **Regler:** Home Assistant Automation in Verbindung mit dem OpenAI GPT-4o-mini Modell.
* **Stellglied:** Verriegelungsmechanismus der Katzenklappe (Smart Plug / Servo).
* **Rückkopplung:** Kontinuierliche Bildanalyse bei erkannter Bewegung, bis der Soll-Zustand wiederhergestellt ist.

## 2. Enthaltene Dateien
* `automation_regelung.yaml`: Kernlogik der Bildanalyse und Sperrfunktion.
* `automation_wartung.yaml`: Systempflege zur automatischen Speicherbereinigung (Löschen alter Bilder).

## 3. Technische Spezifikation (Parameter)
* **KI-Modell:** gpt-4o-mini
* **Antwortformat:** JSON-Validierung zur Fehlerreduzierung.
* **Sperrdauer:** 15 Minuten (einstellbar), danach erfolgt eine erneute Freigabe (Soll-Zustand-Prüfung).
* **Datenhygiene:** Bilder werden nach 7 Tagen automatisch per Shell-Command gelöscht.

## 4. Installation & Sicherheit
Die YAML-Dateien dienen als Referenz. Private Daten (API-Keys, spezifische IDs) wurden durch Platzhalter wie `DEIN_PROVIDER_ID` ersetzt.
