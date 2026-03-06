# Solar Node

Solar-betriebener Low-Power Node auf Basis von **Seeed Studio XIAO nRF52840** + **Wio-SX1262 (LoRa)**, ausgelegt für den Betrieb mit **LiFePO4 32700 (3.2V / 6000mAh)**.

> [!NOTE]
>  Hardware-Design (OSHWLab/EasyEDA): https://oshwlab.com/continuum/solar-node

> [!IMPORTANT]
> Bitte beachtet die "Zusätzliche Komponenten" in der [Stückliste.md](https://github.com/Continuum-404/Meshtastic-Solar-Node/blob/c3fc9a9dcc2af69ebf1b37c7b7867563f2b57b59/St%C3%BCckliste.md)

---

## Überblick

Die **Solar Node** ist primär eine autarke **Meshtastic-Node** für den Outdoor-Einsatz. Die Versorgung stellt ein Solarpanel sicher, das über einen **TP5000** einen **LiFePO₄-Akku (32700)** lädt (BMS). Der **TI TPS61023DRLR** erzeugt daraus eine stabile **5-V-Versorgung** für den **XIAO nRF52840** und den **Wio-SX1262**. Über einen Power-Schalter lässt sich die 5-V-Schiene (und damit die Meshtastic-Hardware) deaktivieren.

> [!TIP]
> Zusätzliche Sensorik kann optional über **I²C** angebunden werden.

Zur Überwachung der Solar Versorgung bzw der Batteriespannung werden zwei **INA219** verwendet:
- **INA219 (0x40):** misst **Ladespannung** und **Ladestrom** (Solar/TP5000 → Akku).
- **INA219 (0x41):** misst **Batteriespannung** sowie den **Stromverbrauch der Meshtastic-Hardware**.

Der **interne Laderegler** des **XIAO nRF52840** wird **nicht** genutzt; entsprechend bleibt auch der **Batterieanschluss** am XIAO unbenutzt. Akkudaten stammen ausschließlich aus den Messwerten der **INA219**.


---

## Features

- ☀️ Solar + Akku (LiFePO4 32700) für autarken Betrieb
- 🔋 **TP5000** LiFePO4 Solar-Laderegler (1S)
- ⚡ **TI TPS61023DRLR** Boost-Regler (**5V aus Akku-Spannung**)
- 🔌 **Power-Schalter**: deaktiviert TPS61023DRLR → **5V OFF** → MCU/LoRa OFF
- 📡 **Seeed Wio-SX1262**
- 🧠 **Seeed XIAO nRF52840**
- 🔌 **I²C-Erweiterungsanschluss** (ausgeführt)
- 🧩 **SMD-Design**

---

## Stromversorgung (Power Path)

```text
Solarpanel
   │
   ▼
TP5000  (LiFePO4 Charger, 1S)
   │
   ▼
LiFePO4 32700 (3.2V / 6000mAh inkl. BMS)
   │
   ▼
TPS61023DRLR  (Boost -> 5V)
   │
   ├─► 5V Rail ──► XIAO nRF52840
   │              └─► Wio-SX1262 (SX1262)
   │
   └─► Power-Schalter: deaktiviert TPS61023DRLR → 5V Rail OFF → MCU/LoRa OFF
