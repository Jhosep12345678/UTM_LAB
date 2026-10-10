# UTM Lab — Máquina Universal de Ensayos de Fuerza de Bajo Costo

> Sistema de instrumentación, adquisición de datos en tiempo real y caracterización mecánica de materiales (hasta 100 N) desarrollado con microcontrolador Arduino, celda de carga de 10 kg, accionamiento NEMA 17 y plataforma web moderna en Next.js / Supabase / Google Gemini / Vercel.

## 1. Introducción y Contexto

La **ciencia de materiales** estudia las propiedades mecánicas, físicas y químicas de los materiales para comprender su comportamiento bajo cargas externas y fundamentar aplicaciones tecnológicas. Entre las propiedades de mayor interés se encuentran la resistencia a la tracción, la deformación elástica/plástica y el módulo de Young.

Las **máquinas universales de ensayos (UTM)** industriales convencionales son equipos voluminosos, de costo elevado (miles de dólares) y con características excesivas para laboratorios de docencia o caracterización de probetas poliméricas a pequeña escala.

Ante esta necesidad, el proyecto propone el **diseño, construcción y validación de una máquina universal de ensayos de fuerza de bajo costo y dimensiones reducidas**, integrando componentes comerciales accesibles, acondicionamiento de señales de precisión, microcontrolador local y una aplicación web moderna para adquisición serial directa en el navegador, graficado en vivo y exportación local trazable sin costos de almacenamiento cloud.

---

## 2. Objetivos

### Objetivo Principal
**Diseñar, construir y validar un prototipo de máquina universal de ensayos de fuerza de bajo costo**, capaz de aplicar una fuerza controlada (con límite de seguridad de 100 N) y registrar la respuesta mecánica de probetas poliméricas.

### Objetivos Específicos
* **Estructura mecánica:** Diseñar y fabricar la estructura física, guías lineales y mordazas de sujeción para probetas.
* **Sistema de accionamiento:** Implementar el control de desplazamiento mediante un motor paso a paso NEMA 17 y su etapa de potencia.
* **Instrumentación y acondicionamiento:** Integrar y calibrar una celda de carga de 10 kg (~100 N) con conversor ADC de alta resolución (HX711 o similar).
* **Plataforma de software:** Desarrollar una interfaz web (UTM Lab) con Web Serial API, visualización en tiempo real y asistencia inteligente mediante Google Gemini.
* **Curvas esfuerzo–deformación:** Calcular en tiempo real $\sigma$ (esfuerzo) y $\varepsilon$ (deformación) a partir de los datos geométricos de la probeta y las lecturas calibradas.
* **Evaluación experimental:** Evaluar la resolución, repetibilidad y respuesta del prototipo con diferentes muestras poliméricas comerciales e impresas en 3D.

---  

## 3.1 Equipo y funciones

### Dante A. Olivas Huaman — Software y Plataforma Web
- Arquitectura Next.js y despliegue en Vercel.
- Web Serial API y adquisición serial en navegador.
- Autenticación de operadores con Supabase.
- Integración del agente Gemini.
- Cálculo de esfuerzo–deformación en tiempo real.
- Exportación local PDF/CSV.
- Integración software–firmware.

### Jhosep A. Tineo Santa Cruz — Instrumentación y Control
- Celda de carga de 10 kg y módulo HX711/ADC.
- Calibración metrológica y evaluación de estabilidad.
- Firmware Arduino y protocolo Serial v1 con CRC-16.
- Driver NEMA 17, fuente de alimentación y control de motor.
- Seguridad, finales de carrera y paro de emergencia.

### Juan Jesus Agüero Ventura — Estructura Mecánica
- Modelado CAD 3D de la máquina.
- Diseño y fabricación de mordazas de sujeción.
- Guías lineales, soportes y tolerancias.
- Ensamblaje, rigidez estructural y pruebas mecánicas.

---

## 3.2 Estado actual del proyecto — 10 de octubre de 2026

- **Inicio del proyecto:** 14 de septiembre de 2026.
- **Avance en software:** plataforma web en Next.js con Web Serial, Recharts, Supabase Auth, Gemini y exportación local PDF/CSV.
- **Avance en firmware:** protocolo Serial v1 con CRC-16, control de motor y bloqueos de seguridad.
- **Avance en mecánica:** diseño CAD preliminar/intermedio, mordazas y soportes en revisión.
- **Pendiente:** calibración experimental con masas patrón, fabricación definitiva de piezas CAD y ensayos de tracción con probetas poliméricas.
- **Fecha objetivo de cierre:** última semana de noviembre de 2026.

---

## 3.3 Planificación semanal propuesta — 14 sep al 29 nov 2026

> **Leyenda:** Completado ·  En curso · ⏳ Pendiente

### Semana 1 — 14 al 20 de septiembre de 2026
- **Dante:** Configuración del repositorio, arquitectura Next.js, Supabase Auth y vistas iniciales.
- **Jhosep:** Selección de celda de 10 kg, HX711 y Arduino; pruebas de lectura.
- **Juan:** Bocetos CAD, dimensiones, selección de guías y mordazas.
- **Hito/estado:**  Kickoff y BOM preliminar.

### Semana 2 — 21 al 27 de septiembre de 2026
- **Dante:** Web Serial API, parser serial, Recharts y maqueta UI.
- **Jhosep:** Firmware base: lectura ADC, motor paso a paso y finales de carrera.
- **Juan:** CAD 3D preliminar, soporte de motor y guías.
- **Hito/estado:**  Primer prototipo software/firmware.

### Semana 3 — 28 de septiembre al 4 de octubre de 2026
- **Dante:** Auth Supabase, perfiles, exportación CSV/PDF y Gemini.
- **Jhosep:** Protocolo Serial v1 con CRC-16, seguridad y control de velocidad.
- **Juan:** CAD de mordazas, tolerancias y planos de fabricación.
- **Hito/estado:**  Protocolo y CAD intermedio.

### Semana 4 — 5 al 11 de octubre de 2026
- **Dante:** Integración Web Serial + gráfica en vivo; despliegue en Vercel.
- **Jhosep:** Calibración inicial con masas patrón; repetibilidad.
- **Juan:** Revisión CAD, impresión 3D y prototipado de mordazas.
- **Hito/estado:**  Avance actual: software y CAD funcional.

### Semana 5 — 12 al 18 de octubre de 2026
- **Dante:** Pruebas de conexión real Arduino–navegador; corrección de errores.
- **Jhosep:** Acondicionamiento final, calibración fina y pruebas de carga.
- **Juan:** Fabricación/ajuste de piezas y ensamblaje parcial.
- **Hito/estado:**  Sistema mínimo integrado.

### Semana 6 — 19 al 25 de octubre de 2026
- **Dante:** Curva σ-ε en vivo, ingreso de geometría y reporte PDF.
- **Jhosep:** Firmware final: límites de carrera, paro de emergencia y control de motor.
- **Juan:** Ensamblaje de estructura, alineación de guías y mordazas.
- **Hito/estado:**  Firmware y UI listos para integración.

### Semana 7 — 26 de octubre al 1 de noviembre de 2026
- **Dante:** Integración completa software–firmware; registro de sesión y pruebas.
- **Jhosep:** Calibración documentada; incertidumbre y trazabilidad.
- **Juan:** Montaje final, pruebas de rigidez y alineación.
- **Hito/estado:**  Máquina ensamblada y calibrada.

### Semana 8 — 2 al 8 de noviembre de 2026
- **Dante:** Ajustes de UI, exportación PDF/CSV y validación de datos.
- **Jhosep:** Pruebas con probetas poliméricas; repetibilidad.
- **Juan:** Ajustes mecánicos, cambio de mordazas y seguridad.
- **Hito/estado:**  Primeros ensayos de tracción.

### Semana 9 — 9 al 15 de noviembre de 2026
- **Dante:** Post-ensayo: E, σy, UTS y εr; reportes.
- **Jhosep:** Ensayos comparativos, análisis de ruido y calibración final.
- **Juan:** Ensayos de fatiga mecánica y mantenimiento.
- **Hito/estado:**  Curvas experimentales completas.

### Semana 10 — 16 al 22 de noviembre de 2026
- **Dante:** Documentación, manual de usuario y preparación de demo.
- **Jhosep:** Validación metrológica e informe de instrumentación.
- **Juan:** Planos finales y manual de montaje.
- **Hito/estado:**  Validación técnica y documentación.

### Semana 11 — 23 al 29 de noviembre de 2026
- **Dante:** Presentación final, despliegue definitivo y demo en vivo.
- **Jhosep:** Demo de calibración y ensayos en vivo.
- **Juan:** Demo mecánica y mantenimiento.
- **Hito/estado:**  Cierre y entrega final.

### Semana 12* — 30 de noviembre al 6 de diciembre de 2026
- **Dante:** Correcciones menores e informe final.
- **Jhosep:** Ajustes finales de calibración.
- **Juan:** Ajustes mecánicos menores.
- **Hito/estado:** *Semana de holgura opcional.*

> **Nota:** El cronograma está sujeto a ajustes por disponibilidad de laboratorio, impresión 3D, tiempos de calibración y ensayos experimentales.
---

## 4. Arquitectura del Sistema

El sistema opera bajo un modelo desacoplado: **el firmware local garantiza la seguridad física y la temporización crítica**, mientras que **el navegador web visualiza, procesa y genera los reportes**.

<p align="center">
  <img src="Resources/Software/Imagenes/grafico_flujo.png" alt="Diagrama de flujo del sistema" width="620">
</p>

```text
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                                 CAPA DE CONTROL LOCAL                                  │
│                                                                                        │
│   [ Celda de Carga 10 kg ] ──> [ ADC / Acondicionamiento ]                             │
│                                           │                                            │
│   [ Finales de carrera / Paro ] ────────> [ Microcontrolador Arduino ]                 │
│                                           │ (Uno / Nano - ATmega328P)                  │
│   [ Driver de potencia ] <────────────────┘                                            │
│            │                                                                           │
│   [ Motor NEMA 17 + Tornillo ] ──> [ Desplazamiento mecánico ]                         │
└───────────────────────────────────────────┬────────────────────────────────────────────┘
                                            │ Cable USB (Protocolo Serial v1 con CRC-16)
                                            ▼
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                              CAPA DE SOFTWARE (UTM LAB)                                │
│                                                                                        │
│   Navegador del Operador (Chrome / Edge)                                               │
│   ├── Web Serial API (Lectura bidireccional local, detección de saltos de seq)         │
│   ├── Motor de cálculo en vivo (Esfuerzo en MPa, Deformación de ingeniería)            │
│   ├── Interfaz gráfica React 19 / Recharts (Curva sin datos sintéticos)                │
│   └── Asistente de Operación flotante (Chat contextual con Google Gemini)              │
│                                                                                        │
│   Servicios en la Nube                                                                 │
│   ├── Vercel (Alojamiento Edge/Serverless con HTTPS obligatorio)                       │
│   ├── Supabase Auth (Acceso seguro por correo y contraseña de operadores)              │
│   └── Google Gemini API (Respuestas contextualizadas mediante Gemini)        │
│                                                                                        │
│   * Cero Consumo de Almacenamiento Cloud: Todos los datos de ensayos (curvas,          │
│     muestras completas y reportes PDF/CSV) se generan en el navegador del operador     │
│     y se descargan directamente a su equipo local.                                     │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

 
 

- [x] Definición conceptual y parámetros de diseño (límite 100 N).
- [x] Distribución de responsabilidades entre los cuatro integrantes.
- [x] Adquisición de componentes clave (Arduino, celda 10 kg, motor NEMA 17, driver).
- [x] Desarrollo de la plataforma web en Next.js con soporte Web Serial, Recharts y Google Gemini.
- [x] Autenticación de operadores en Supabase con RLS y exportación local de reportes PDF/CSV (cero consumo cloud).
- [x] Implementación completa del firmware en Arduino con protocolo Serial v1, CRC-16/CCITT y bloqueos de seguridad ([`firmware/utm_controller/utm_controller.ino`](Resources/Software/firmware/utm_controller/utm_controller.ino)).
- [x] Validación de compilación y preparación para despliegue en Vercel.
- [ ] Calibración experimental con masas patrón de la celda de carga de 10 kg.
- [ ] Fabricación de piezas CAD definitivas (mordazas y soportes de guías).
- [ ] Ensayos de tracción con probetas poliméricas (PLA, PETG, ABS) y trazado experimental de curvas.

---

## 11. Documentación Complementaria

* [Firmware para Arduino Uno / Nano](Resources/Software/firmware/utm_controller/utm_controller.ino)
* [Guía de puesta en marcha rápida](Resources/Software/docs/SETUP.md)
* [Migración de base de datos para Supabase](Resources/Software/supabase/migrations/202609180001_initial.sql)
* [Documento de Estado del Arte](Resources/Software/Estado%20del%20arte_Olivas_Tineo_Ag%C3%BAero_%20Sanchez.pdf)

