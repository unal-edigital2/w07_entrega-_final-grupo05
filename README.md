# W07_Entrega-_final
[![N|Solid](https://www.universidadesvirtuales.com.co/logos/original/logo-universidad-nacional-de-colombia.png)](https://www.universidadesvirtuales.com.co/logos/original/logo-universidad-nacional-de-colombia.png)

* >Jose Alvaro Celis Lopez
* >Julian David Pulido Castañeda
* >Esteban Landino
* >Julian Escobar

## INTRODUCCIÓN
Ha inicio del semestre 2020-2, se planteo el desarrolo de un System on Chip (SoC) para un sistema autónmo capaz de navegar y trazar un laberinto al mismo tiempo que procese imagenes de objetos por color.

Durante la primeras semanas, con ayuda del profesor y otros grupos de la misma materia se llego al siguiente esquema para el SoC:

![DIAGRAMA1](/docs/figure/SoC.png)

Por cuestiones de tiempo y logsitica se trabajaron e implementaron los siguientes dispositivos:

* Camara (Procesamiento y VGA)
* Radar (Ultrasonido y Servomotor)
* Motores Pasa a Paso
* Infrarojo

Ahora procedemos a explicar cada uno.

## Camara
La camara usada fue la OV7670, sus caracteristicas principales son:

* Es una camara de video
* No posee memoria de almacenamiento 
* La imagen se puede ajustar atraves de una serie de registros internos que se comunican mediante el protocolo I2C (del inglés Inter-Integrated Circuit)

El driver camara esta compuesto por:

### buffer_ram_dp.v 

Como se dijo anteriormente, la camar no posee memoria por lo que toca crearla.

Para conocer las dimensiones de mi memoria, primero necesito conocer la dimensiones y caracteristicas de la imagen que queremos. En nuestro caso nosostros queremos una imagen:

* 160 X 120 Pixeles
* Formato RGB444 (12 bits)

###Radar
Para el radar se utilizan dos dispositivos un servo motor(SG90)  y un ultrasonido( HC - SR04 )  el objetivo es usar el  servo motor con  tres grados de libertad( 0  grados ,90 gradas y 180 grados) para tomar la  distancia con el ultrasonido ( al frente, izquierda y derecha )   luego en software  se usara esa información  para la navegación.
