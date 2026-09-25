# nextpm-airgradient-openair — Firmware ESP32-C3

> Source unique des instructions projet. CLAUDE.md n'est qu'un renvoi vers ce fichier.

## Ce que c'est

Firmware pour carte OpenAir compatible AirGradient, équipée d'un **NextPM** (particules),
d'un **Senseair S8** (CO₂) et d'un **Sensirion SGP41** (TVOC/NOx). Publie vers le cloud
AirGradient et expose un tableau de bord web local avec API JSON.

Ex-`AIRGRADIENT-OPENAIR-NEXTPM`.

## Câblage (à ne pas deviner)

```
NextPM      UART1  115200 8E1   RX=GPIO0   TX=GPIO1
Senseair S8 UART0  9600 8N1     RX=GPIO20  TX=GPIO21
SGP41       I²C @ 0x59          SDA=GPIO7  SCL=GPIO6
```

Le NextPM fournit PM1 / PM2.5 / PM10 via le protocole simple `0x12` (moyenne 1 min),
et le comptage cumulé ≥ 0,3 µm en pcs/dL, transmis à AirGradient comme `pm003Count`.

## Structure

```
src/      — sources du firmware
sketch/   — croquis Arduino
```

## Branches

- `main` — la référence
- `feat/airsentinels-backend-switch` — bascule vers un backend AirSentinels, API de
  lecture au format OpenAQ pour ExpoTrack et les tiers

## Où il vit

`tera-sensor/nextpm-airgradient-openair`, branche `main`, **public**.
Clone : `Dev\tera-sensor\nextpm-airgradient-openair`.
