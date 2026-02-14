# Solar Node

Solar-betriebener Low-Power Node auf Basis von **Seeed Studio XIAO nRF52840** + **Wio-SX1262 (LoRa)**, ausgelegt für den Betrieb mit **LiFePO4 32700 (3.2V / 6000mAh)**.

- Hardware-Design (OSHWLab/EasyEDA): https://oshwlab.com/continuum/solar-node
- Bitte beachtet die "Zusätzliche Komponenten" Liste

---

## Überblick

**Solar Node** ist ein autarker Outdoor-Knoten für Sensorik/Telemetrie über LoRa. Energie kommt von einem Solarpanel, geladen über **TP5000** in einen **LiFePO4 32700** Akku. Ein **TI TPS61023DRLR** erzeugt daraus eine **5V-Schiene**, an der **XIAO nRF52840** und **Wio-SX1262** hängen. Über einen Power-Schalter kann der Boost-Regler deaktiviert werden, wodurch **MCU + LoRa vollständig stromlos** sind.

---

## Features

- ☀️ Solar + Akku (LiFePO4 32700) für autarken Betrieb
- 🔋 **TP5000** LiFePO4 Solar-Laderegler (1S)
- ⚡ **TI TPS61023DRLR** Boost-Regler (**5V aus Akku-Spannung**)
- 🔌 **Power-Schalter**: deaktiviert TPS61023DRLR → **5V OFF** → MCU/LoRa OFF
- 📡 **LoRa (SX1262)** via **Wio-SX1262**
- 🧠 **nRF52840** via **Seeed XIAO nRF52840**
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
LiFePO4 32700 (3.2V / 6000mAh)
   │
   ▼
TPS61023DRLR  (Boost -> 5V)
   │
   ├─► 5V Rail ──► XIAO nRF52840
   │              └─► Wio-SX1262 (SX1262)
   │
   └─► Power-Schalter: deaktiviert TPS61023DRLR → 5V Rail OFF → MCU/LoRa OFF
