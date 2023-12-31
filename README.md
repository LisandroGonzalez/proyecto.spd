# Integrantes
* Gonzalez, Lisandro
* De Luca, Rosio Gisel

## Parte 1: Contador de 0 a 99 con Display 7 Segmentos y Multiplexación

![parte1](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/c222b0e7-7eae-4caf-a593-00887fbd1ae0)

## Descripción
Diseño de un contador de 0 a 99 utilizando dos displays de 7 segmentos y tres botones para
controlar la cuenta, implementando la técnica de multiplexación para mostrar los dígitos
en los displays. El contador comienza en 0 y aumentar o disminuir su valor en una unidad con los botones.

#### Multiplexación
Su función es encaminar las señales binarias de 2n líneas posibles de entrada en una única línea de salida. 

En este proyecto se utiliza para compartir los 7 segmentos para los dos displays (unidad y de decena). 
Se utiliza esta modalidad porque no alcanzarían los pines del arduino para hacerlo en forma independiente.
Cuando se asignan en los 7 segmentos los bits necesarios para que se prenda el display de unidad se activa su pin analógico y se desactiva el de la decena. 
Cuando se envian los bits de la decena se realiza en forma inversa

## Función principal

En las primeras tres lineas (123-125) de la funcion se le asigna a tres variables el estado del boton asignado (1 -> presionado o 0 -> no presionado), 
luego mediante el uso de ifs (128-138) pregunta si el estado de cada uno de los botones fue pulsado, y de ser asi, pone en una variable asignada para 
el estado anterior un 1, y al final de la funcion (140-159), pregunta si el estado de las variables mencionadas al principio cambio respecto a su 
estado anterior, de ser asi, esto significaria que el boton termino de ser presionado, y por lo tanto, retorna la salida digital del boton que fue 
accionado.

```C
int controlDeBoton(){
  sube = digitalRead(SUBE);
  baja = digitalRead(BAJA);
  reset = digitalRead(RESET);
  
  if (sube){
    subeEstadoAnterior = 1;
  }
  if (baja){
    bajaEstadoAnterior = 1;
  }
  if (reset){
    resetEstadoAnterior = 1;
  }  
  if (sube == 0 && sube != subeEstadoAnterior){
    subeEstadoAnterior = sube;
    return SUBE;
  }
  if (baja == 0 && baja != bajaEstadoAnterior){
    bajaEstadoAnterior = baja;
    return BAJA;
  }
  if (reset == 0 && reset != resetEstadoAnterior){
    resetEstadoAnterior = reset;
    return RESET;
  }  
  return 0;
}
```


## Parte 2.1: Modificación con Interruptor deslizante y números primos

![parte2](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/59df4d1b-1e81-432e-8d68-f8f9d01502a0)

## Descripción
Diseño de un contador de 0 a 99 utilizando dos displays de 7 segmentos y un interruptor deslizante.

Si el interruptor se encuentra posicionado a la izquierda, el display muestra los números primos en el rango de 0 a 99.
En caso de que el display se encuentre hacia la derecha, el display muestra el contador de 0 a 99.

## Función principal

La funcion usa dos funciones, prenderDisplay() la cual se encarga de prender y apagar los visualizadores de la decena y la unidad según corresponda,
y prenderNumDisplay(), el cual para la parte de las decenas divide el contador por 10, lo cual resulta en un numero flotante, que al haber sido 
declarado un entero, corta la parte decimal que seria la parte de la unidad, y luego usa el resto de esta division, la cual seria el numero de la 
parte de la unidad.


```C
void mostrarNumeros(int numero){
  
  prenderNumDisplay(numero/10);
  prenderDisplay(DECENA);
  prenderDisplay(APAGADO);
  
  prenderNumDisplay(numero%10);
  prenderDisplay(UNIDAD);
  prenderDisplay(APAGADO);
}

```


## Parte 2.2: Modificación con motor de CC y sensor de temperatura

#### Motor de corriente continua

El motor de corriente continua o motor de corriente directa es una máquina con la capacidad de convertir energía eléctrica en movimiento o trabajo mecánico a través de fuerzas electromagnéticas.
Este dispositivo emplea un rotor con dos polos magnéticos que interactúan de manera constante con un estator con polo Norte y un fijo de polo Sur; el rotor gira sobre su eje y gracias a la repulsión y atracción de sus propios polos con los del estator, se produce un movimiento constante.

Funciona gracias al poder del magnetismo, aprovechando las fuerzas de atracción y repulsión de los polos con el fin de crear movimientos de rotación.
Sus partes fundamentales son las siguientes:

* Estator: Es la carcasa de material ferromagnético y en su interior se encuentran distribuidos los polos inductores en número par con la intención de que el rotor gire.
* Entrehierro: Es el nombre que recibe el espacio que existe entre el estator y el rotor, esta distancia es imprescindible para evitar el desgaste de ambas piezas.
* Rotor: Es la pieza central del motor y está elaborado de acero y silicio barnizado; este elemento es el que gira y mantiene el movimiento en su propio eje para transformar la energía electromagnética en energía     mecánica.
* Colector de legas: Esta pieza se encuentra montada sobre el eje de giro y cuenta con varias legas fabricadas en cobre de alta pureza y separadas por mica.
* Escobillas: Son los elementos que permiten el contacto eléctrico entre las delgas y el circuito de corriente continua, están compuestas por grafito y hacen que la presión y el contacto se mantengan constantes.
  
Este tipo de motores puede ser aprovechado en objetos que requieran movimiento, por ejemplo: juguetes, giradiscos, electrodomésticos, etc.; en el caso de la industria, se pueden aprovechar en compresores, máquinas de rotación y ascensores.

![motor](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/b0eb2ded-5772-4c06-8799-9bf6bc69dee8)

#### Sensor de temperatura

Un sensor de temperatura es un sistema que detecta variaciones en la temperatura y las transforma en una señal eléctrica que llega hasta un sistema electrónico.

Se componen principalmente de tres partes:
* Elemento sensor: Esta es la parte central del sensor que responde a los cambios de temperatura.
* Carcasa: Protege el sensor de influencias ambientales, como la humedad, la suciedad y la corrosión. La carcasa también puede ayudar a mejorar la transferencia de calor entre el elemento sensor y el objeto cuya temperatura se está midiendo.
* Cableado: El sensor está conectado a un cable que lleva la señal eléctrica desde el elemento sensor hasta el dispositivo de lectura o control. 
  
En Arduino, el sensor de temperatura proporciona una salida de voltaje proporcional a la temperatura, por lo tanto, es necesario convertir ese voltaje a grados Celsius. En este caso, esa conversión de temperatura se hizo utilizando la función map.

![sensor](https://github.com/LisandroGonzalez/proyecto.spd/assets/123898318/415ef590-c398-476c-9462-e86f19f067b7)

#### Aplicación en el proyecto

Una posible incorporación de ambos componentes en el proyecto sería, por ejemplo, utilizándolos en un ventilador. El sensor mediría la temperatura y cuando ésta es igual o mayor a los 30°C el motor se enciende. Si la temperatura es menor a 30°C el motor permanece apagado.

## Parte 3: Modificación usando una fotoresistencia

Modificación agregando una fotoresistencia, que, en caso de que la misma registre una instensidad de luz baja, es decir, que sea de noche, se apague el motor previamente incorporado. 
Caso contrario funcione normalmente.

## Fotoresistencia

Una fotorresistencia es un componente eléctrico, el cual posee una resistencia capaz de variar su magnitud al estar en contacto con distintas magnitudes de intensidad lumínica.

La base del funcionamiento de una fotorresistencia radica en su componente principal, el sulfuro de cadmio (CdS). Este componente químico es un semiconductor que tiene la capacidad de variar su resistencia según la 
cantidad de luz que en él incida.

Cuanto mayor intensa es la luz que incide sobre el sulfuro de cadmio, más baja es la resistencia, es decir mayor facilidad de los electrones para moverse. Vale saber que la variación de la resistencia cuando hay cambios de luminosidad repentinos no sigue la misma velocidad, sino que tiene retardo.

En el proyecto la incorporacion de este componente, podria ser para apagar el motor cuando la intensidad de la luz este en un rango bajo (la noche).

# Enlaces al proyecto
* [Parte 1](https://www.tinkercad.com/things/ajBtQkZgpyX-copy-of-primer-parcial-parte-1/editel?sharecode=kyloOgjOjRCKmidilat9jocpUBs_b18UxDfPWX8ttG4) 
* [Parte 2](https://www.tinkercad.com/things/ks8qoWAqN0g-primer-parcial-parte-2/editel?sharecode=6q1re_Cas0dJkWkAkpKIjD-2QozqC5lB7e4nQ291InQ)
* [Parte 3](https://www.tinkercad.com/things/c9kb8OdQaMW-parcial-parte-3/editel?sharecode=JPhjVLiG8jJhXO5oJdAV1lXkmzuCIp-hAc5aM2Ll31E)
* [Parte 4](https://www.tinkercad.com/things/ihOWWs1Ng1s-copy-of-parcial-parte-3/editel?sharecode=1M0Dcy88cuqK1oT6K73U-3KSAPFG2hNJ61njnZN8YFs)
