# Meshtastic: `solar_config.yaml` per CLI auf eine Node laden (Windows / PowerShell)

Dieses How-To zeigt dir, wie du unter **Windows** die **Meshtastic CLI** installierst und anschließend eine YAML-Konfiguration per  
`meshtastic --configure solar_config.yaml` auf deine Node schreibst.

> ⚠️ **Wichtig:** Die `solar_config.yaml` enthält **Beispielwerte**. Vor dem Import müssen **Location/Owner** angepasst werden, und der **privateKey** sollte über den Meshtastic Web Client **neu erzeugt** werden (siehe unten).

---

## Inhalt

- [Voraussetzungen](#voraussetzungen)
- [Repo-Struktur](#repo-struktur)
- [Installation (Windows PowerShell)](#installation-windows-powershell)
- [Wichtig: Platzhalter in der Config anpassen](#wichtig-platzhalter-in-der-config-anpassen)
- [Private Key neu erzeugen (Web Client)](#private-key-neu-erzeugen-web-client)
- [COM-Port finden](#com-port-finden)
- [Backup erstellen (empfohlen)](#backup-erstellen-empfohlen)
- [Konfiguration auf die Node schreiben](#konfiguration-auf-die-node-schreiben)
- [Überprüfen](#überprüfen)
- [Troubleshooting](#troubleshooting)

---

## Voraussetzungen

- Windows 10/11
- **Python 3** installiert
- Meshtastic-Node per **USB** verbunden (erscheint als **COM-Port**)
- Optional: Geräte-Manager (zum Port finden)

---

## Repo-Struktur

Empfohlene Struktur:

```text
.
├─ README.md
└─ configs/
   └─ solar_config.yaml
```

---

## Installation (Windows PowerShell)

Öffne **PowerShell** und prüfe zuerst, ob Python verfügbar ist:

```powershell
py --version
```

Aktualisiere `pip` und installiere die Meshtastic CLI:

```powershell
py -m pip install --upgrade pip
py -m pip install --upgrade meshtastic
```

Test:

```powershell
meshtastic --help
```

> Wenn `meshtastic` nicht gefunden wird, nutze in allen Befehlen stattdessen `py -m meshtastic ...` (siehe [Troubleshooting](#troubleshooting)).

---

## Wichtig: Platzhalter in der Config anpassen

In `configs/solar_config.yaml` müssen Nutzer **mindestens** folgende Werte anpassen.  
Die untenstehenden Werte sind **nur Beispiele**.

### Location anpassen

```yaml
location:
  lat: 56.0201728
  lon: 6.0030976
```

➡️ Trage hier deine **eigenen Koordinaten** ein.

### Owner / Owner Short anpassen

```yaml
owner: =[Please Change]=
owner_short: '0000'
```

➡️ Setze einen eindeutigen Namen/Kurzname pro Node, damit du Geräte im Mesh sauber unterscheiden kannst.

---

## Private Key neu erzeugen (Web Client)

Der `privateKey` sollte **nicht** aus einer Beispiel-Config übernommen werden. Er sollte **neu erzeugt** werden über den Meshtastic Web Client:

1. Öffne: https://client.meshtastic.org/messages/broadcast/0
2. Verbinde dich mit deiner Node
3. Öffne die **Security**-Einstellungen
4. Erzeuge einen neuen **Private Key** und speichere ihn auf der Node

> Hinweis: UI/Bezeichnungen können je nach Version leicht abweichen. Wichtig ist: **Private Key neu erzeugen**, nicht kopieren.

---

## COM-Port finden

### Option A: Geräte-Manager (empfohlen)

Geräte-Manager → **Anschlüsse (COM & LPT)** → Node auswählen → z. B. `COM5`

### Option B: PowerShell

```powershell
[System.IO.Ports.SerialPort]::getportnames()
```

---

## Backup erstellen (empfohlen)

Bevor du etwas änderst, exportiere die aktuelle Konfiguration:

```powershell
meshtastic --port COM5 --export-config > backup_config.yaml
```

Wenn du `meshtastic` nicht im PATH hast:

```powershell
py -m meshtastic --port COM5 --export-config > backup_config.yaml
```

---

## Konfiguration auf die Node schreiben

Wende die Config an (Pfad ggf. anpassen):

```powershell
meshtastic --port COM5 --configure .\configs\solar_config.yaml
```

Alternative (falls `meshtastic` nicht gefunden wird):

```powershell
py -m meshtastic --port COM5 --configure .\configs\solar_config.yaml
```

---

## Überprüfen

Exportiere danach die Konfiguration erneut und vergleiche sie:

```powershell
meshtastic --port COM5 --export-config > after_config.yaml
```

Alternative:

```powershell
py -m meshtastic --port COM5 --export-config > after_config.yaml
```

---

## Troubleshooting

### `meshtastic` wird nicht erkannt

Nutze:

```powershell
py -m meshtastic --help
```

Wenn das funktioniert, fehlt meistens nur der PATH-Eintrag für das Python-`Scripts`-Verzeichnis. Bis dahin kannst du dauerhaft `py -m meshtastic ...` verwenden.

### Keine Verbindung / falscher Port

- COM-Port im Geräte-Manager prüfen
- USB-Kabel/Port wechseln (Datenkabel!)
- Sicherstellen, dass nicht mehrere Clients gleichzeitig verbunden sind (Web Client/App/CLI)

