# proyecto.spd
# Integrantes
* De Luca, Rosio Gisel
* Gonzalez, Lisandro

## Parte 1: Contador de 0 a 99 con Display 7 Segmentos y Multiplexación
![parte1](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/9f059da6-56e7-4456-9627-6e0a4024267d)



## Descripción
Diseño de un contador de 0 a 99 utilizando dos displays de 7 segmentos y tres botones para
controlar la cuenta, implementando la técnica de multiplexación para mostrar los dígitos
en los displays. El contador comienza en 0 y aumentar o disminuir su valor en una unidad con los botones.


## Función principal

## Parte 2.1: Modificación con Interruptor deslizante y números primos

![parte2](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/e5d1e322-10c7-41c3-b83f-e7892876d1fa)

## Descripción
Diseño de un contador de 0 a 99 utilizando dos displays de 7 segmentos y un interruptor deslizante.
Si el interruptor se encuentra posicionado a la izquierda, el display muestra los números primos en el rango de 0 a 99.
En caso de que el display se encuentre hacia la derecha, el display muestra el contador de 0 a 99.

## Parte 2.2: Modificación con Interruptor deslizante, números primos, motor de CC y sensor de temperatura

#### Motor de corriente continua

El motor de corriente continua o motor de corriente directa es una máquina con la capacidad de convertir energía eléctrica en movimiento o trabajo mecánico a través de fuerzas electromagnéticas.
Este dispositivo emplea un rotor con dos polos magnéticos que interactúan de manera constante con un estator con polo Norte y un fijo de polo Sur; el rotor gira sobre su eje y gracias a la repulsión y atracción de sus propios polos con los del estator, se produce un movimiento constante.

Funciona gracias al poder del magnetismo, aprovechando las fuerzas de atracción y repulsión de los polos con el fin de crear movimientos de rotación.
Sus partes fundamentales son las siguientes:

* Estator: Es la carcasa de material ferromagnético y en su interior se encuentran distribuidos los polos inductores en número par con la intención de que el rotor gire.
* Entrehierro: Es el nombre que recibe el espacio que existe entre el estator y el rotor, esta distancia es imprescindible para evitar el desgaste de ambas piezas.
* Rotor: Es la pieza central del motor y está elaborado de acero y silicio barnizado; este elemento es el que gira y mantiene el movimiento en su propio eje para transformar la energía electromagnética en energía mecánica.
* Colector de legas: Esta pieza se encuentra montada sobre el eje de giro y cuenta con varias legas fabricadas en cobre de alta pureza y separadas por mica.
* Escobillas: Son los elementos que permiten el contacto eléctrico entre las delgas y el circuito de corriente continua, están compuestas por grafito y hacen que la presión y el contacto se mantengan constantes.
  
Este tipo de motores puede ser aprovechado en objetos que requieran movimiento, por ejemplo: juguetes, giradiscos, electrodomésticos, etc.; en el caso de la industria, se pueden aprovechar en compresores, máquinas de rotación y ascensores.

![motor](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/41f560b3-d3a6-4f46-95a5-9b39052f0c7e)


#### Sensor de temperatura

Un sensor de temperatura es un sistema que detecta variaciones en la temperatura y las transforma en una señal eléctrica que llega hasta un sistema electrónico.
Se componen principalmente de tres partes:
* Un elemento sensor
* Una vaina de material conductor en su interior
* Un cable que conecta al sistema electrónico en cuestión.
  
En Arduino, el sensor de temperatura proporciona una salida de voltaje proporcional a la temperatura, por lo tanto, es necesario convertir ese voltaje a grados Celsius. En este caso, esa conversión de temperatura se hizo utilizando la función map.

![sensor](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/3237a18b-1bfa-4b0a-bd70-d80cc26b90f8)


#### Aplicación en el proyecto

Una posible incorporación de ambos componentes en el proyecto sería, por ejemplo, utilizándolos en un ventilador. El sensor mediría la temperatura y cuando ésta es igual o mayor a los 30°C el motor se enciende. Si la temperatura es menor a 30°C el motor permanece apagado.

## Parte 3: Modificación usando una fotoresistencia



# Enlaces al proyecto
* [Parte 1](https://www.tinkercad.com/things/ajBtQkZgpyX-copy-of-primer-parcial-parte-1/editel?sharecode=kyloOgjOjRCKmidilat9jocpUBs_b18UxDfPWX8ttG4) 
* [Parte 2](https://www.tinkercad.com/things/ks8qoWAqN0g-primer-parcial-parte-2/editel?sharecode=6q1re_Cas0dJkWkAkpKIjD-2QozqC5lB7e4nQ291InQ) 
