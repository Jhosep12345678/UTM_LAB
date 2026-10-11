# Máquina Universal de Ensayo de Tracción de Bajo Coste

## Información general del proyecto



| - | - |
|---|---|
| **Nombre del proyecto** | Máquina Universal de Ensayo de Tracción de Bajo Coste |
| **Cliente objetivo** | Laboratorio de materiales independiente |
| **Objetivo principal** | Diseñar y construir una máquina universal de ensayo de tracción de bajo coste para caracterizar materiales poliméricos. |
| **Fuerza máxima de ensayo** | 100 N |
| **Unidad de control** | Arduino UNO |
| **Alimentación** | Adaptador externo de 12 V con acondicionamiento de tensión |
| **Presupuesto máximo de fabricación** | S/ 300, sujeto a cotizaciones y disponibilidad de componentes |
| **Valor estimado del trabajo de ingeniería** | S/ 5 000, considerando el tiempo invertido y los conocimientos aportados por los integrantes |


## Especificaciones técnicas y requisitos de diseño

| Categoría | Requisito | Criterio de cumplimiento | Responsable |
|---|---|---|---|
| **Funcionalidad** | Diseñar y construir una máquina universal de ensayo de tracción de bajo coste para caracterizar materiales poliméricos. | Aplicar una fuerza de tracción controlada de hasta 100 N y registrar los datos del ensayo. | JUAN |
| **Geometría** | Las dimensiones máximas del conjunto ensamblado, incluidos los componentes electrónicos, serán de 45 cm de longitud, 8 cm de ancho y 12 cm de altura. | Verificar las dimensiones exteriores de la máquina ensamblada. | JUAN |
| **Cinemática** | El movimiento de las partes móviles deberá ser suave, estable y libre de obstáculos que provoquen atascamientos o vibraciones excesivas. | Comprobar el desplazamiento del mecanismo a lo largo de su recorrido de trabajo. | JUAN |
| **Sistema mecánico** | La estructura deberá mantener la alineación del sistema móvil y de las mordazas durante el ensayo. | Verificar la estabilidad estructural y reducir las cargas laterales sobre la muestra y la celda de carga. | JUAN |
| **Fuerza y accionamiento** | El sistema deberá permitir aplicar una fuerza de tracción de hasta 100 N mediante un motor paso a paso y un mecanismo de transmisión. | Comprobar que el sistema alcance la fuerza objetivo sin superar los límites mecánicos ni eléctricos de sus componentes. | JHOSEP |
| **Resolución de desplazamiento** | El husillo deberá tener un avance por revolución menor o igual a 8 mm. | Verificar el avance lineal del husillo y determinar la resolución real de posicionamiento. | JUAN |
| **Alimentación eléctrica** | El sistema funcionará mediante un adaptador externo de 12 V y una etapa de acondicionamiento que proporcione las tensiones necesarias, incluyendo 5 V. | Verificar la estabilidad de las tensiones de alimentación bajo las condiciones de funcionamiento previstas. | JHOSEP |
| **Fabricación** | El diseño priorizará materiales económicos y accesibles, como PLA, acrílico y madera, siempre que sean adecuados para las cargas previstas. | Evaluar la resistencia y rigidez de los materiales seleccionados. | JUAN |
| **Montaje y transporte** | La máquina deberá poder trasladarse y almacenarse con facilidad dentro de un laboratorio y entre instalaciones. | Comprobar que el conjunto pueda transportarse sin desmontajes complejos ni daños en sus componentes. | JUAN |
| **Instrumentación y adquisición de datos** | Un microcontrolador gestionará la lectura de la celda de carga y la comunicación con el sistema de accionamiento. | Obtener mediciones periódicas de fuerza durante el ensayo. | JHOSEP |
| **Comunicación electrónica** | El Arduino UNO deberá comunicarse con una computadora para transmitir los datos adquiridos. | Verificar la transmisión de datos y la continuidad del registro durante un ensayo completo. | JHOSEP |
| **Control del motor** | El sistema electrónico deberá controlar el movimiento del motor paso a paso según las condiciones establecidas para el ensayo. | Verificar el sentido de giro, la velocidad y el desplazamiento del mecanismo. | JHOSEP |
| **Control y software** | La máquina contará con un software que permita iniciar y supervisar los ensayos mediante comunicación con el microcontrolador. | Implementar el inicio del ensayo, la visualización de datos y el almacenamiento de resultados. | DANTE |
| **Visualización de resultados** | El software deberá generar gráficas en tiempo real durante la ejecución del ensayo. | Mostrar las curvas de fuerza frente a elongación y de esfuerzo frente a deformación, cuando se disponga de los datos geométricos necesarios. | DANTE |
| **Calibración de fuerza** | El sistema de medición de fuerza deberá calibrarse utilizando cargas conocidas. | Registrar el procedimiento de calibración y los errores de medición observados. | JHOSEP |
| **Verificación del desplazamiento** | El desplazamiento del mecanismo deberá verificarse mediante una referencia dimensional. | Comparar el desplazamiento medido con el desplazamiento de referencia. | JUAN |
| **Seguridad mecánica y eléctrica** | El diseño deberá contemplar límites de recorrido, prevención de sobrecarga y un procedimiento para detener el movimiento ante una condición anormal. | Verificar el funcionamiento de las protecciones antes de realizar ensayos. | JUAN |
| **Validación del prototipo** | El prototipo deberá evaluarse mediante ensayos de prueba con materiales conocidos o muestras de referencia apropiadas. | Documentar la repetibilidad, el comportamiento mecánico y la calidad de los datos obtenidos. | JUAN |


## Plan de trabajo / Cronograma de Actividades

Entrar al siguiente link para visualizar el PDF

------------->   **[Ir al repositorio de Software]([https://github.com/LordPercival241/maquina-de-ensayos-esfuerzo-deformacion](https://github.com/Jhosep12345678/UTM_LAB/blob/main/Project/Plan_de_trabajo.pdf))**   <-------------------



-------


