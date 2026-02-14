# Solar Node

Solar-betriebener Low-Power Node auf Basis von **Seeed Studio XIAO nRF52840** + **Wio-SX1262 (LoRa)**, ausgelegt für den Betrieb mit **LiFePO4 32700 (3.2V / 6000mAh)**.

**Hardware-Design (OSHWLab/EasyEDA):** https://oshwlab.com/continuum/solar-node

> Ziel: Autarker Outdoor-Knoten (Sensorik/Telemetrie/LoRa), robust, stromsparend und einfach reproduzierbar.

---

## Highlights

- ☀️ **Solar + Akku (LiFePO4 32700)** für autarken Betrieb
- 📡 **LoRa (SX1262)** via Wio-SX1262 Modul
- 🧠 **nRF52840** (XIAO Formfaktor) für Low-Power Anwendungen
- 🔌 Erweiterbar über **I²C / SPI / UART / GPIO** (je nach Layout/Bestückung)
- 🧾 Fertigungsdaten & Projektdateien über OSHWLab/EasyEDA

---

## Hardware

### Kernkomponenten
- **MCU:** Seeed Studio **XIAO nRF52840**
- **LoRa:** Seeed **Wio-SX1262**
- **Akku:** **32700 LiFePO4**, **3.2V**, **6000mAh**
- **Solar:** _[Panel-Spezifikation bitte ergänzen: z. B. 6V/1W]_
- **Laden/Power-Path/Regler:** _[bitte ergänzen – IC/Topologie]_
- **Sensoren:** _[optional – bitte ergänzen]_

### Stromversorgung (Kurzbeschreibung)
Solarpanel → Lade/Power-Management → LiFePO4 32700 → Regler/Power-Path → XIAO nRF52840 + Wio-SX1262

> Wenn du mir den Lade-IC/PMIC nennst, trage ich das sauber mit typischen Spannungen/Strömen ein.

---

## Repo-Struktur (Vorschlag)

```text
.
├─ hardware/
│  ├─ gerber/
│  ├─ bom/
│  ├─ pick-place/
│  └─ docs/               # Schaltplan, Renderings, Assembly Notes
├─ firmware/
│  ├─ config/             # config datei(en) für CLI
│  └─ tools/              # helper scripts (optional)
├─ docs/
│  └─ images/
└─ README.md
