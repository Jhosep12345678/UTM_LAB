# Codigo de calibración de la celda de carga en ESP32

```
#include "HX711.h"

// Pines del HX711
const int LOADCELL_DOUT_PIN = 16;
const int LOADCELL_SCK_PIN = 4;

HX711 balanza;

const int N_masa = 3; //este el numero de masas en general que se usa en el experimento
const float N_masa_1 = N_masa;
// Masas de calibracion en gramos elegidas para el proyecto
const float masas[N_masa] = {
  0.0,
  1000.0,
  5000.0
};

// Lecturas ADC
long lecturas[N_masa];

// Parametros de calibracion
float pendiente = 0;
float offset = 0;


//funcion de espera
void esperarHX711() {
  while (!balanza.is_ready()) {
    delay(10);
  }
}

//funcion para obtener el promedio de las muestras
long obtenerPromedio(int muestras = 30) {
  esperarHX711();
  return balanza.read_average(muestras);
}

void setup() {

  Serial.begin(115200);
  delay(1000);

  Serial.println("\n================================");
  Serial.println(" CALIBRACION HX711 - 10 KG - ESP32 -");
  Serial.println("================================");

  balanza.begin(
    LOADCELL_DOUT_PIN,
    LOADCELL_SCK_PIN
  );

  //aqui el programa verifica si HX711 esta listo para entrar datos
  if (!balanza.is_ready()) {
    Serial.println("ERROR: HX711 no detectado");

    while (1) {
      delay(100);
    }
  }

  Serial.println("HX711 conectado correctamente");

  // Calibracion de tres puntos
  for (int i = 0; i < 3; i++) {

    Serial.println("\n--------------------------------");

    Serial.print("PUNTO ");
    Serial.println(i + 1);

    Serial.print("Coloca una masa de ");
    Serial.print(masas[i], 0);
    Serial.println(" gramos.");

    Serial.println("Presiona ENTER cuando este lista.");

    while (!Serial.available()) {
      delay(10);
    }

    while (Serial.available()) {
      Serial.read();
    }

    delay(1000);

    // Obtener promedio de 30 lecturas
    lecturas[i] = obtenerPromedio(30);

    Serial.print("Lectura ADC: ");
    Serial.println(lecturas[i]);
  }

  // Calcular regresion lineal:
  // ADC = pendiente * masa + offset  esta es la ecuacion de regresion lineal

  float sumaX = 0;
  float sumaY = 0;
  float sumaXY = 0;
  float sumaX2 = 0;

  for (int i = 0; i < 3; i++) {

    sumaX += masas[i];
    sumaY += lecturas[i];

    sumaXY += masas[i] * lecturas[i];

    sumaX2 += masas[i] * masas[i];
  }

  float n = N_masa_1; //este es el numero de masas colocadas en las celda

  //aqui estan los calculos estadisticos de la pendiente y el intercepto 

  pendiente = (n * sumaXY - sumaX * sumaY) /
              (n * sumaX2 - sumaX * sumaX);   

  offset = (sumaY - pendiente * sumaX) / n;

  Serial.println("\n================================");
  Serial.println(" RESULTADOS DE CALIBRACION");
  Serial.println("================================");

  Serial.print("Pendiente: ");
  Serial.println(pendiente, 6);

  Serial.print("Offset: ");
  Serial.println(offset, 2);

  Serial.println("\nEcuacion:");

  Serial.print("ADC = ");
  Serial.print(pendiente, 6);
  Serial.print(" * masa(g) + ");
  Serial.println(offset, 2);

  Serial.println("\nCalibracion terminada.");
  Serial.println("Iniciando mediciones...\n");
}

void loop() {

  if (balanza.is_ready()) {

    long adc = balanza.read_average(5);

    // Convertir ADC a gramos
    float peso = (adc - offset) / pendiente;

    Serial.print("ADC: ");
    Serial.print(adc);

    Serial.print(" | Peso: ");
    Serial.print(peso, 2);

    Serial.println(" g");
  }

  delay(200);
}

```




# Codigo del testeo del motor Nema 17



```

#include <AccelStepper.h>

#define STEP_PIN 18
#define DIR_PIN 19

AccelStepper stepper(AccelStepper::DRIVER, STEP_PIN, DIR_PIN);

const long pasosPorVuelta = 200;
unsigned long tiempoEspera;
bool esperando = false;

void setup() {
  stepper.setMaxSpeed(1000);
  stepper.setAcceleration(200);

  stepper.setCurrentPosition(0);
  stepper.moveTo(200);
}

void loop() {

  if (esperando) {

    if (millis() - tiempoEspera >= 1000) {
      esperando = false;
      stepper.moveTo(stepper.currentPosition() + pasosPorVuelta);
    }

  } else {

    stepper.run();

    if (stepper.distanceToGo() == 0) {
      esperando = true;
      tiempoEspera = millis();
    }
  }
}


```
