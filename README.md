# SunamiCadizStudio
Anallis Data Plan Cadiz

# 🌊 Tridente Cádiz — Sistema de Detección y Alerta Temprana de Tsunamis

[![Licencia: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Estado: Propuesta técnica](https://img.shields.io/badge/Estado-Propuesta%20t%C3%A9cnica-blue)](https://github.com/)
[![Tsunami Ready](https://img.shields.io/badge/Tsunami%20Ready-C%C3%A1diz%202026-00b4d8)](https://www.unesco.org/)
[![Hecho con HTML5](https://img.shields.io/badge/Hecho%20con-HTML5%20%2B%20SVG-orange)](https://developer.mozilla.org/es/docs/Web/HTML)

> **Documento técnico independiente y abierto para su consideración por el Ayuntamiento de Cádiz, Protección Civil y la Junta de Andalucía.**  
> No es un sistema oficial. Es una propuesta basada en fuentes verificables, física de tsunamis y tecnología probada.

---

## 📋 Resumen ejecutivo

Cádiz está expuesta a tsunamis generados en la falla Azores-Gibraltar. El evento de 1755 produjo olas de 10–15 m y el margen de reacción actual es de **42 minutos**. La ciudad ha avanzado con el plan PALMA, el reconocimiento *Tsunami Ready* y 3 sirenas, pero **carece de boyas DART** para confirmar un tsunami en mar abierto. Este proyecto propone una arquitectura multicapa —**Tridente**— que combina:

1. **3 boyas DART** en el Golfo de Cádiz (detección de presión en fondo marino).
2. **GNSS ionosférico** como capa de confirmación (8–32 min de ventaja).
3. **Difusión multicanal**: sirenas UHF, ES-Alert, radio y TV.

**Inversión estimada:** ~1,1 M€ (CapEx) + ~375 k€/año (OpEx).  
**Resultado:** protección operativa real, no solo formal.

---

## 🎯 Motivación

- La falla Azores-Gibraltar es una amenaza documentada (1755, 1969).
- España **no tiene ninguna boya DART** desplegada.
- Las 3 sirenas actuales no cubren toda la ciudad.
- El sistema ES-Alert falló en el simulacro de 2025 (retrasos de hasta 13 min).
- El cambio climático eleva el nivel del mar y agrava el impacto.

Este repositorio contiene un **estudio técnico visual e interactivo** (HTML + SVG) que analiza alternativas, descarta lo inviable y propone una arquitectura concreta.

---

## 🧠 ¿Qué contiene este repositorio?

- `index.html` — Estudio técnico completo, autocontenido, sin dependencias externas.
- `README.md` — Este documento.
- `LICENSE` — Licencia del proyecto (MIT para código, CC BY-SA 4.0 para documentación).
- `assets/` — (Opcional) Diagramas exportados, PDF, etc.

Puedes abrir `index.html` directamente en cualquier navegador moderno. No requiere servidor ni conexión a internet.

---

## 🏗️ Arquitectura propuesta: Sistema Tridente

### Capa 1 — Detección oceánica (DART)

| Componente | Especificación |
|------------|----------------|
| Sensor de fondo (BPR) | Resolución 1 mm, profundidad 1.500–4.900 m |
| Enlace fondo-superficie | Acústico 15–18 kHz, ~5.000 bps, latencia 10–13 s |
| Enlace superficie-tierra | Satélite Iridium (primario), 4G (respaldo) |
| Modo evento | Transmisión cada 15 s |
| Unidades propuestas | 3 boyas en el Golfo de Cádiz |

### Capa 2 — Confirmación ionosférica (GNSS)

- Reutiliza la red GPS existente.
- Detecta perturbaciones en la ionosfera por ondas de presión del tsunami.
- Ventaja: **8–32 minutos** antes de la llegada de la ola.
- Coste marginal bajo (~50.000 € de integración).

### Capa 3 — Difusión masiva resiliente

| Canal | Cobertura | Fiabilidad |
|-------|-----------|------------|
| Sirenas UHF (560 Hz) | 1 km por unidad | Alta (respaldo analógico) |
| ES-Alert / 4G | Toda la ciudad | Media (vulnerable a saturación) |
| Radio FM / TV | Regional | Alta |
| Altavoces en edificios públicos | Puntos estratégicos | Media |

---

## 🗺️ Mapa de despliegue propuesto

El estudio incluye un mapa SVG con la ubicación estimada de las 3 boyas DART, las fallas activas y las rutas de comunicación satelital. Las coordenadas son orientativas y deben validarse con estudios batimétricos de campo.

---

## 💰 Análisis de costes

| Concepto | Cantidad | Coste unitario | Coste total |
|----------|----------|----------------|-------------|
| Boya DART-4G | 3 | 250.000 € | 750.000 € |
| Mantenimiento anual | 3 | 125.000 €/año | 375.000 €/año |
| Sirenas adicionales | 12–15 | 15.000 € | ~200.000 € |
| Integración GNSS ionosférico | 1 | — | ~50.000 € |
| Centro de control y software | 1 | — | ~100.000 € |
| **TOTAL CapEx** | | | **~1.100.000 €** |

> El coste total es inferior al **0,5% del presupuesto anual del Ayuntamiento de Cádiz**.

---

## ✅ Tecnologías evaluadas y descartadas

| Tecnología | Veredicto | Razón |
|------------|-----------|-------|
| BLE subacuático | ❌ Descartado | Alcance de metros |
| WiFi en boya | ❌ Descartado | Alcance ~100 m |
| LoRa como enlace principal | ❌ No viable | Alcance máximo 1,4 km |
| Cable umbilical | ⚠️ Riesgo alto | Frágil ante arrastre y sismos |
| Luz/LED subacuático | ❌ Descartado | Atenuación exponencial |
| **DART + Iridium** | ✅ **Imprescindible** | Estándar probado, resolución 1 mm |
| **GNSS ionosférico** | ✅ Complementario | Bajo coste, 8–32 min de ventaja |
| **SMART Cable** | ⚠️ Largo plazo | +10–15% sobre cable telecom |

---

## 🚀 Cómo visualizar el estudio

1. Clona el repositorio:
   ```bash
   git clone https://github.com/raulcadiz/SunamiCadizStudio.git
