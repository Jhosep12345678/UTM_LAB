# UTM Lab — Máquina Universal de Ensayos de Fuerza de Bajo Costo

> Sistema de instrumentación, adquisición de datos en tiempo real y caracterización mecánica de materiales (hasta 100 N) desarrollado con microcontrolador Arduino, celda de carga de 10 kg, accionamiento NEMA 17 y plataforma web moderna.

##Carrera de Ingeniería Física - Universidad Nacional de Ingeniería

## 1. Planteamiento del problema

La ciencia e ingeniería de materiales requieren la caracterización experimental de las propiedades mecánicas para comprender el comportamiento de los materiales sometidos a cargas externas y evaluar su potencial en distintas aplicaciones tecnológicas. Entre las propiedades de interés se encuentran la resistencia a la tracción, el módulo de Young, el límite elástico y la deformación hasta la rotura. Para la determinación de estas propiedades se requieren equipos de ensayo y procedimientos de medición adecuados.

Las máquinas universales de ensayos (Universal Testing Machines, UTM) permiten realizar pruebas mecánicas controladas; sin embargo, los equipos comerciales pueden representar una barrera económica y logística para actividades de docencia, experimentación y desarrollo de prototipos. En determinados entornos académicos, el acceso a estos equipos también puede estar condicionado por la disponibilidad del laboratorio, la programación de ensayos y las condiciones de uso.

En la Universidad Nacional de Ingeniería (UNI), por ejemplo, se dispone de infraestructura para realizar ensayos de tracción de materiales. No obstante, el acceso a estos equipos puede estar sujeto a las condiciones de uso del laboratorio. Asimismo, se identifica la necesidad de contar con un equipo compacto y de menor costo que permita realizar ensayos de tracción en muestras pequeñas de polímeros, especialmente cuando se requiere desarrollar pruebas preliminares, validar prototipos o efectuar experimentos de manera más rápida y accesible.

### Solución propuesta

Ante esta necesidad, el proyecto propone diseñar, construir y validar una máquina de ensayos de tracción de bajo costo y dimensiones reducidas, con una capacidad máxima de fuerza de 100 N, orientada a la caracterización mecánica de muestras pequeñas de polímeros. El sistema integrará componentes mecánicos y electrónicos comerciales, un sistema de medición de fuerza y desplazamiento, circuitos de acondicionamiento de señales, un microcontrolador para la adquisición de datos y una aplicación web para visualizar, registrar y procesar los resultados experimentales en tiempo real.

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

| **Foto** | **Nombre** | **Rol** | **Funciones** |
| -------- | ---------- | ----- | ------------ |
| <img src="https://github.com/user-attachments/assets/517e716a-ff18-42a9-9790-07db12ab48b6" width="100"> | **Dante A. Olivas Huaman** | Software y Plataforma Web | - Arquitectura Next.js y despliegue en Vercel.<br>- Web Serial API y adquisición serial en navegador.<br>- Autenticación de operadores con Supabase.<br>- Integración del agente.<br>- Cálculo de esfuerzo–deformación en tiempo real.<br>- Exportación local a PDF/CSV.<br>- Integración software–firmware. |
| — | **Jhosep A. Tineo Santa Cruz** | Instrumentación y Control | - Celda de carga de 10 kg y módulo HX711/ADC.<br>- Calibración metrológica y evaluación de estabilidad.<br>- Firmware Arduino y protocolo Serial v1 con CRC-16.<br>- Driver NEMA 17, fuente de alimentación y control del motor.<br>- Seguridad, finales de carrera y paro de emergencia. |
| — | **Juan Jesus Agüero Ventura** | Estructura Mecánica | - Modelado CAD 3D de la máquina.<br>- Diseño y fabricación de mordazas de sujeción.<br>- Guías lineales, soportes y tolerancias.<br>- Ensamblaje, rigidez estructural y pruebas mecánicas. |

---













## 11. Documentación Complementaria

* [Firmware para Arduino Uno / Nano](Resources/Software/firmware/utm_controller/utm_controller.ino)
* [Guía de puesta en marcha rápida](Resources/Software/docs/SETUP.md)
* [Migración de base de datos para Supabase](Resources/Software/supabase/migrations/202609180001_initial.sql)
* [Documento de Estado del Arte](Resources/Software/Estado%20del%20arte_Olivas_Tineo_Ag%C3%BAero_%20Sanchez.pdf)

