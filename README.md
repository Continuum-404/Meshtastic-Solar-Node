# Solar Node

Solar-betriebener Low-Power Node auf Basis von **Seeed Studio XIAO nRF52840** + **Wio-SX1262 (LoRa)**, ausgelegt für den Betrieb mit **LiFePO4 32700 (3.2V / 6000mAh)**.

**Hardware-Design (OSHWLab/EasyEDA):** https://oshwlab.com/continuum/solar-node

---

## Highlights

- ☀️ **Solar + LiFePO4 32700** für autarken Outdoor-Betrieb
- 🔋 **TP5000** LiFePO4 Solar-Laderegler (1S)
- ⚡ **TI TPS61023DRLR** Boost-Regler (**5V aus Akku-Spannung**)
- 📡 **LoRa (SX1262)** via Wio-SX1262 Modul
- 🧠 **nRF52840** (XIAO Formfaktor) für stromsparende Anwendungen
- 🔌 **I²C-Erweiterungsanschluss** (ausgeführt) für Sensoren/Peripherie
- 🧩 **SMD-Design** (für einfache Fertigung/Assembly)

---

## Hardware

### Kernkomponenten
- **MCU:** Seeed Studio **XIAO nRF52840**
- **LoRa:** Seeed **Wio-SX1262**
- **Akku:** **32700 LiFePO4**, **3.2V**, **6000mAh**
- **Solar-Laderegler:** **TP5000** (1S LiFePO4)
- **5V-Regler:** **TPS61023DRLR** (Boost, 5V)
- **Erweiterung:** **I²C** (Header/Anschluss auf PCB)

### Stromversorgung (Übersicht)
Solarpanel → TP5000 (Laden/Power) → LiFePO4 32700 → TPS61023 (5V) → Verbraucher (z. B. Sensoren/Peripherie)  
MCU/LoRa laufen je nach Auslegung direkt am Akku/Reglerpfad.

> Wenn du mir sagst, ob MCU/LoRa **direkt an VBAT** hängen oder über einen separaten Regler, kann ich das Diagramm exakt machen.

---

## Komponentenliste / Kosten

Eine laufende Liste der benötigten Komponenten inkl. Bezugsquellen:
- Google Sheet: https://docs.google.com/spreadsheets/d/10DE-c9x9UDSqj9JYPvdJV23CFt0LOcdHYuGjifVPPIo/edit?usp=sharing :contentReference[oaicite:1]{index=1}

**Hinweis:** Im Sheet ist aktuell eine Gesamtsumme von **142,51 €** aufgeführt (Stand der Liste). :contentReference[oaicite:2]{index=2}

---

## Fertigung

- **SMD:** ja
- **Gerber Export:** über OSHWLab/EasyEDA (Fabrication Output → Gerber)
- **BOM / Pick&Place:** optional (falls du im Repo ablegen willst: `hardware/bom/` und `hardware/pick-place/`)

Empfohlene Repo-Struktur:
```text
.
├─ hardware/
│  ├─ gerber/
│  ├─ bom/
│  ├─ pick-place/
│  └─ docs/
├─ firmware/
│  ├─ config/
│  └─ tools/
├─ docs/
│  └─ images/
└─ README.md
