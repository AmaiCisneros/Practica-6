# Practica-6
### INDICADOR DE NIVEL DE AGUA
Este repositorio muestra como podemos programar una ESP32 con el sensor Ultrasonico y conectar unos led´s de manera que nos sirva como un indicador visual del nivel de agua
## Introducción
 -Descripción
La Esp32 la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (Ultrasonico) para medir los litros de agua de un tanque ; Cabe aclarar que esta practica se usara un simulador llamado WOKWI.

-Material Necesario
Para realizar esta practica necesitas lo siguiente
WOKWI
Tarjeta ESP 32
HC-SR04 Ultrasonic Distance Sensor

## Instrucciones
Abrir la terminal de programación y colocar la siguente programación:
-CODIGO
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}

void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=0 && safetyDistance<=40)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=40 && safetyDistance<=150) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=150 && safetyDistance<=300) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=300 && safetyDistance<=398) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else if(safetyDistance>=399 && safetyDistance<=400) 
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else
{
 digitalWrite(led1,  LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}

Conexiones :
![](https://github.com/AmaiCisneros/Practica-6/blob/main/Captura%20de%20pantalla%202024-01-19%20185937.png)


- Instrucciónes de operación
Iniciar simulador.
Visualizar los datos en el monitor serial.
Colocar la distancia dando doble click al sensor Ultrasonico
Resultados
Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen;
![](https://github.com/AmaiCisneros/Practica-6/blob/main/Captura%20de%20pantalla%202024-01-19%20190110.png)


