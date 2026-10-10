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

## 3. Integrantes y Responsabilidades

| Integrante | Rol / Especialidad | Responsabilidades Principales |
| :--- | :--- | :--- |
| **Dante Aliguere Olivas Huaman**<img width="259" height="260" alt="Captura de pantalla 2026-10-08 223608" src="https://github.com/user-attachments/assets/ee8ed598-f00f-49eb-83c2-5f79cb81a661" /> | **Software y Plataforma Web** | Desarrollo de la arquitectura de software, adquisición de datos, conectarlos a la web, autenticación y perfiles en Supabase, agente de IA con Google Gemini, exportación local PDF/CSV y despliegue en Vercel. |
| **Jhosep A. Tineo Santa Cruz** | **Instrumentación y Sensores** | Acondicionamiento de señal para celda de carga de 10 kg, etapa de amplificación/digitalización, integración con Arduino, calibración metrológica y evaluación de estabilidad. |
| **Juan Jesus Agüero Ventura** | **Estructura Mecánica** | Modelado CAD 3D de la máquina, diseño y fabricación de pinzas de sujeción (mordazas), cálculo de tolerancias, soporte de guías y rigidez estructural. |
| **------RETIRADO------** | **Potencia y Accionamiento** | Selección del motor paso a paso NEMA 17, driver de potencia, dimensionamiento eléctrico, fuente de alimentación y control de velocidad/torque del actuador. |

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

