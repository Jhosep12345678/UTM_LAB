DIMENSIONAMIENTO


| Subsistema | Componente | Especificación | Función |
|:---|:---|:---|:---|
| Alimentación | Adaptador AC/DC | 12 V, 5 A, 60 W | Alimentación principal |
| Regulación | Convertidor buck | 5 V, 3 A, 15 W nominales | Alimentar la lógica |
| Control | ESP32 | Lógica de 3,3 V | Control, adquisición y comunicación |
| Accionamiento | NEMA 17 bipolar | 0,72 N·m; 1,7 A/fase; 1,8° | Generar movimiento |
| Driver | DRV8825 | Alimentación de motor de 12 V | Controlar corriente y pasos |
| Transmisión | Husillo T8 | 300 mm de longitud; avance declarado de 8 mm/rev | Convertir rotación en traslación |
| Fuerza | Celda de carga | 10 kg; sensibilidad nominal de 1,0 mV/V | Medir la carga |
| Conversión | HX711 | ADC para puente extensométrico | Digitalizar la señal de la celda |
| Posición | Conteo de pasos | Resolución teórica de 0,04 mm/paso completo | Estimar el movimiento del carro |
| Estructura | PLA impreso en 3D | Tornillos y uniones metálicas | Soportar y alinear el conjunto |
| Comunicación | USB serie | Web Serial API y CRC-16 | Transmitir comandos y datos |
| Software | Aplicación web | Gráfica, registro y exportación local | Supervisión y análisis |

______   ________________   _____________   _______________

| Voltaje DC | Componente / Sub-sistema | Voltaje de operación | Corriente estimada (pico/máx.) | Potencia estimada |
|:---|:---|:---:|:---:|:---:|
| **12 V** | Motor NEMA 17 + Driver DRV8825 | 12 V | 2,2 A | 26,4 W |
| **5 V** | Microcontrolador ESP32 | 5 V | 0,500 A | 2,50 W |
| **5 V** | Celda de carga (10 kg) + HX711 | 5 V | 0,015 A | 0,075 W |
| **5 V** | Driver DRV8825 | 5 V | 0,015 A | 0,075 W |
| **Alimentación total** | **12 V** | **5 A** | **60 W** | |
| **Porcentaje utilizado por el prototipo (teórico)** | **45,4 %** | | | |


Link de planos / mecanica

![Link_Planos]([https://github.com/USUARIO/REPOSITORIO](https://github.com/Jhosep12345678/UTM_LAB/blob/main/Resources/Mec%C3%A1nica/DIMENSIONAMIENTO%20DE%20LAS%20PIEZAS%20CON%20SUS%20RESPECTIVAS%20VISTAS.pdf))
