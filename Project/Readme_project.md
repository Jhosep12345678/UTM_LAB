# Máquina Universal de Ensayo de Tracción de Bajo Coste

## 1. Información general del proyecto

|---|---|
| **Nombre del proyecto** | Máquina Universal de Ensayo de Tracción de Bajo Coste |
| **Cliente objetivo** | Laboratorio de materiales independiente |
| **Objetivo principal** | Diseñar y construir una máquina universal de ensayo de tracción de bajo coste para caracterizar materiales poliméricos. |
| **Fuerza máxima de ensayo** | 100 N |
| **Unidad de control** | Arduino UNO |
| **Alimentación** | Adaptador externo de 12 V con acondicionamiento de tensión |
| **Presupuesto máximo de fabricación** | S/ 300, sujeto a cotizaciones y disponibilidad de componentes |
| **Valor estimado del trabajo de ingeniería** | S/ 5 000, considerando el tiempo invertido y los conocimientos aportados por los integrantes |

## 2. Especificaciones técnicas y requisitos de diseño

## 2. Especificaciones técnicas y requisitos de diseño

| Categoría | Requisito | Criterio de cumplimiento |
|---|---|---|
| **Funcionalidad** | Diseñar y construir una máquina universal de ensayo de tracción de bajo coste para caracterizar materiales poliméricos. | Aplicar una fuerza de tracción controlada de hasta 100 N y registrar los datos del ensayo. |
| **Geometría** | Las dimensiones máximas del conjunto ensamblado, incluidos los componentes electrónicos, serán de 45 cm de longitud, 8 cm de ancho y 12 cm de altura. | Verificar las dimensiones exteriores de la máquina ensamblada. |
| **Cinemática** | El movimiento de las partes móviles deberá ser suave, estable y libre de obstáculos que provoquen atascamientos o vibraciones excesivas. | Comprobar el desplazamiento del mecanismo a lo largo de su recorrido de trabajo. |
| **Sistema mecánico** | La estructura deberá mantener la alineación del sistema móvil y de las mordazas durante el ensayo. | Verificar la estabilidad estructural y reducir las cargas laterales sobre la muestra y la celda de carga. |
| **Fuerza** | El sistema de accionamiento deberá permitir aplicar una fuerza de tracción de hasta 100 N mediante un motor paso a paso y un mecanismo de transmisión. | Comprobar que el sistema alcance la fuerza objetivo sin superar los límites mecánicos ni eléctricos de sus componentes. |
| **Resolución de desplazamiento** | El husillo deberá tener un avance por revolución menor o igual a 8 mm. | Verificar el avance lineal del husillo. La resolución real de posicionamiento dependerá también del motor, el controlador y la transmisión. |
| **Alimentación eléctrica** | El sistema funcionará mediante un adaptador externo de 12 V y una etapa de acondicionamiento que proporcione las tensiones necesarias para los componentes electrónicos. | Verificar la estabilidad de la alimentación de 12 V y 5 V bajo las condiciones de funcionamiento previstas. |
| **Fabricación** | El diseño priorizará materiales económicos y accesibles, como PLA, acrílico y madera, siempre que sean adecuados para las cargas previstas. | Evaluar la resistencia y rigidez de los materiales seleccionados antes de su utilización. |
| **Montaje y transporte** | La máquina deberá poder trasladarse y almacenarse con facilidad dentro de un laboratorio y entre instalaciones. | Comprobar que el conjunto pueda transportarse sin desmontajes complejos ni daños en sus componentes. |
| **Adquisición de datos** | Un microcontrolador gestionará la adquisición de datos de la celda de carga y la comunicación con el sistema de accionamiento. | Obtener mediciones periódicas de fuerza y desplazamiento durante el ensayo. |
| **Comunicación** | El Arduino UNO deberá comunicarse con una computadora para enviar los datos adquiridos. | Verificar la transmisión de datos y la continuidad del registro durante un ensayo completo. |
| **Control y software** | La máquina deberá contar con un software que permita iniciar y supervisar los ensayos mediante comunicación directa con el microcontrolador. | Implementar el inicio del ensayo, la visualización de datos y el almacenamiento de resultados. |
| **Visualización** | El software deberá generar gráficas en tiempo real durante la ejecución del ensayo. | Mostrar, como mínimo, las curvas de fuerza frente a elongación y, cuando se disponga de las dimensiones iniciales de la muestra, esfuerzo frente a deformación. |
| **Calibración** | El sistema de medición de fuerza deberá calibrarse utilizando cargas conocidas. El sistema de desplazamiento deberá verificarse mediante una referencia dimensional. | Registrar los procedimientos de calibración y los errores de medición observados. |
| **Seguridad** | El diseño deberá contemplar límites de recorrido, prevención de sobrecarga y un procedimiento para detener el movimiento ante una condición anormal. | Verificar el funcionamiento de los mecanismos de parada y protección antes de los ensayos. |
| **Validación** | El prototipo deberá evaluarse mediante ensayos de prueba con materiales conocidos o muestras de referencia apropiadas. | Documentar la repetibilidad, el comportamiento mecánico y la calidad de los datos obtenidos. |
