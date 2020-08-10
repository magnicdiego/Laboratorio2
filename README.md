# Laboratorio2
Codigo Circuito Entrada Analógica Salida Digital

/*
  Entrada analógica, con 2 Salidas analógicas, 2 salidas en serie 

  Se lee un pin de entrada analgica correspondiente a un potenciometro,
  donde sera asignado un valor entre los rangos de 0 a 255, con este
  resultado logra esteblecer un PWM, con el cual se logra encender
  el LED. Estos resultados seran presentaran en un monitor.

  Circuito:
  * El potenciometro se conectado con sus pines del extremo
    en el positivo +5V y en negativo GND de la placa arduino
    correspondientemente. Mientras que el pin central es aquel
    que va conectado con el pin analogico A0.
  * 2 LED conectados al pin 6 y 9, ambos conectado al pin GND
    para el negativo.
  * 2 resistencias usadas para cada LED, ambas de mismas similares
    220 Ohm.

  created 29 Dec. 2008
  modified 10-08-2020
  by Diego Magnic

  Este codigo de ejemplo es de dominio publico.
*/

int sensorValue = 0;

int outputValue = 0;

void setup()
{
  pinMode(A0, INPUT);
  pinMode(9, OUTPUT);
  pinMode(6,OUTPUT);
  Serial.begin(9600);
// Se definen los pines que seran utilizados y para que seran usados.
}

void loop()
{
  // Se define el pin en donde sera leida la entrada analogica:
  sensorValue = analogRead(A0);
  // Encontrar el valor para el rango de la salida analogica del sistema:
  outputValue = map(sensorValue, 0, 1023, 0, 255);
  // cambiar el valor de la señal analogica para encender el LED:
  analogWrite(9, outputValue);
  analogWrite(6, outputValue);
  // Imprimir los resultados en la pantalla del dispositivo conectado con el Arduino:
  Serial.print("Regulación del potenciómetro = ");
  Serial.print(sensorValue);
  Serial.print("Energia Recibida por el LED = ");
  Serial.println(outputValue);
  // Se configuraran 2 milisegundos antes de la siguiene lectura
  // para que el sistema tenga tiempo para la transformacion de señales
  // y el ususario tenga tiempo de leer estos antecendentes.
  delay(2); // Esperar 2 milisegundos
}