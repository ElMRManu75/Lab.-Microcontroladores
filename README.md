# Lab.-Controladores y Microcontroladores Programables
# Bascula Digital para Bobinas de Impresion 3D
## Integrantes del Equipo
| Nombre | Matricula | Carrera |
| :--- | :--- | :--- |
| Juan Manuel Ramos Obregon | 1948696 | ITS |
| América Lizeth Domínguez Ramírez | 1950087  | ITS |
| Luis Guillermo De La Cruz Flores | 1914216 | ITS |

# Báscula Digital para Bobinas de impresion 3D (Simulación)

Este proyecto es un prototipo funcional, simulado en Tinkercad, de una báscula digital diseñada para pesar bobinas de filamento de impresión 3D y calcular el material restante.

## 1. ¿Qué hace el proyecto?

Resuelve el problema de la incertidumbre al calcular el filamento restante en una bobina. El dispositivo permite al usuario pesar su bobina y saber con precisión cuántos gramos de material le quedan, evitando impresiones fallidas por falta de filamento.

## 2. Arquitectura y Funcionamiento

El sistema funciona siguiendo un flujo de Entrada-Procesamiento-Salida.

<img width="921" height="501" alt="image" src="https://github.com/user-attachments/assets/4a47e036-3333-45d2-884e-e1be43362b16" />


### Tecnologías Usadas

* **Hardware (Simulado):**
    * Arduino Uno R3
    * Pantalla LCD I2C 16x2
    * Sensor de Fuerza (FSR)
    * Resistencia 10kΩ
* **Software:**
    * Autodesk Tinkercad
    * Lenguaje Arduino (C++)

### Diagrama Esquemático

El siguiente diagrama muestra las conexiones técnicas de los componentes.

<img width="921" height="475" alt="image" src="https://github.com/user-attachments/assets/76a84d3e-222c-4e86-9ae5-01bdabb35639" />


## 3. Requisitos e Instalación
Requesitos:
1x Arduino Uno R3

1x Pantalla LCD I2C 16x2

1x Sensor de Fuerza (FSR)

1x Resistencia de 10 kΩ

Librerias para el codigo:
Wire.h (Para la comunicación I2C)
LiquidCrystal_I2C.h (Para el control de la pantalla)

Puesta en Marcha (Cómo Probar)
## 4. ¿Cómo Usarlo?

1.  Abre el proyecto en Tinkercad: `https://www.tinkercad.com/things/8eLf0fXbOwz/editel?returnTo=%2Fdashboard&sharecode=PoYVCAh_cT4Vr7H8XVxGOpCPJ13DE1lWH0dfBpBoHGE`
2.  Haz clic en el botón verde **"Iniciar Simulación"**.
3.  Haz clic sobre el componente **Sensor de Fuerza (FSR)**.
4.  Mueve el deslizador que aparecerá para simular la aplicación de peso.
5.  Observa cómo el "Peso Simulado" se actualiza en tiempo real en la pantalla LCD.

## 5. Componentes del Proyecto

Esta es la descripción detallada de cada componente usado.


| Foto | Nombre | Descripción |
| :--- | :--- | :--- |
| <img width="333" height="282" alt="image" src="https://github.com/user-attachments/assets/697e8a87-6cd9-4c4c-bc75-0e12b8587b95" /> | **Arduino Uno R3** | Es el cerebro del proyecto. [cite_start]Recibe la señal analógica del sensor de fuerza (en el pin A0), la convierte en un valor de peso y envía el resultado a la pantalla LCD. |
| <img width="338" height="173" alt="image" src="https://github.com/user-attachments/assets/b460976c-9fbd-4dcb-a5e2-6362aabbea7c"/> | **Pantalla LCD I2C 16x2** | Muestra el peso simulado en gramos. Es la interfaz de usuario. [cite_start]Se conecta por I2C, por lo que solo necesita 4 cables: GND (Tierra), VCC (5V), SDA y SCL. |
| <img width="336" height="108" alt="image" src="https://github.com/user-attachments/assets/663e5079-43bc-4824-b919-5cec8b2799d3" /> | **Sensor de Fuerza (FSR)** | Este componente simula la báscula (célula de carga). Es una resistencia que cambia su valor cuando se le aplica presión. [cite_start]Se conecta con una pata a 5V y la otra al pin A0. |
| <img width="108" height="242" alt="image" src="https://github.com/user-attachments/assets/d40000ad-0bd8-417f-b5e9-d40bfd70e8db" /> | **Resistencia de 10 kΩ** | Es una resistencia "pull-down" crucial. Se conecta desde el pin A0 a GND (Tierra). [cite_start]Su trabajo es estabilizar la lectura del sensor de fuerza, asegurando que el Arduino lea "0" cuando no hay peso. |
| <img width="333" height="217" alt="image" src="https://github.com/user-attachments/assets/ebdd566c-d1bd-4d0d-9c76-efe7ba7b8b40" /> | **Placa de Pruebas (Protoboard)** | Es la base donde se montan y conectan todos los componentes temporalmente, sin necesidad de soldar. Los rieles laterales se usan para distribuir la energía (5V y GND) fácilmente. |

## 6. FAQ (Preguntas Frecuentes)
**P: ¿Por qué este proyecto es una simulación y no un circuito físico?** R: Este proyecto se desarrolló en Tinkercad como un prototipo para validar el concepto. La simulación nos permite probar la lógica del programa (leer un sensor, convertir el dato y mostrarlo) y verificar todas las conexiones eléctricas de forma segura y sin costo, antes de invertir en los componentes físicos.

**P: ¿Por qué se usa un "Sensor de Fuerza" (FSR) y no una "Célula de Carga" real?** R: La biblioteca de componentes de Tinkercad es limitada y no incluye la "Célula de Carga" (Load Cell) ni el módulo amplificador HX711, que son los componentes estándar para básculas de precisión. El Sensor de Fuerza (FSR) es el componente más cercano disponible en el simulador que nos permite emular la lógica de leer un peso.

**P: Si construyo esto en la vida real, ¿qué necesito cambiar?** R: Deberás reemplazar dos componentes:
El Sensor de Fuerza (FSR) se reemplaza por una Célula de Carga (de 1kg, 5kg, etc.).
La Resistencia de 10kΩ se reemplaza por un módulo HX711. El resto del circuito (Arduino y Pantalla LCD I2C) y la lógica de mostrar los datos serían idénticos.

P: **¿Para qué sirve la Resistencia de 10kΩ en el circuito?** R: Actúa como una resistencia "pull-down". Su trabajo es darle al pin analógico A0 un camino estable hacia GND (Tierra). Sin ella, el pin A0 estaría "flotando", dando lecturas aleatorias y ruidosas. Con la resistencia, nos aseguramos de que cuando el sensor no está presionado, la lectura sea 0.
