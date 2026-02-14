# Solar Node

Solar-betriebener Low-Power Node auf Basis von **Seeed Studio XIAO nRF52840** + **Wio-SX1262 (LoRa)**, ausgelegt für den Betrieb mit **LiFePO4 32700 (3.2V / 6000mAh)**.

**Hardware-Design (OSHWLab/EasyEDA):** https://oshwlab.com/continuum/solar-node

---

## Highlights

- ☀️ **Solar + LiFePO4 32700** für autarken Outdoor-Betrieb
- 🔋 **TP5000** LiFePO4 Solar-Laderegler (1S)
- ⚡ **TI TPS61023DRLR** Boost-Regler (**5V aus Akku-Spannung**)
- 🔌 **Power-Schalter**: deaktiviert den TPS61023DRLR → **5V-Schiene aus** → MCU/LoRa aus
- 📡 **LoRa (SX1262)** via Wio-SX1262 Modul
- 🧠 **nRF52840** (XIAO Formfaktor)
- 🔌 **I²C-Erweiterungsanschluss** (ausgeführt)
- 🧩 **SMD-Design**

---

## Hardware

### Kernkomponenten
- **MCU:** Seeed Studio **XIAO nRF52840**
- **LoRa:** Seeed **Wio-SX1262**
- **Akku:** **32700 LiFePO4**, **3.2V**, **6000mAh**
- **Solar-Laderegler:** **TP5000** (1S LiFePO4)
- **5V-Regler:** **TPS61023DRLR** (Boost, 5V)
- **Erweiterung:** **I²C** (Header/Anschluss auf PCB)
- **Assembly:** **SMD**

### Stromversorgung (exakt)

```text
Solarpanel
   │
   ▼
TP5000  (LiFePO4 Charger, 1S)
   │
   ▼
LiFePO4 32700 (3.2V)
   │
   ▼
TPS61023DRLR  (Boost -> 5V)
   │
   ├─► 5V Rail ──► XIAO nRF52840
   │              └─► Wio-SX1262 (SX1262)
   │
   └─► [Schalter: deaktiviert TPS61023DRLR → 5V Rail OFF → MCU/LoRa OFF]
