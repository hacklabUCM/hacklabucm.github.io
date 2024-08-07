+++
title = "Proyectos"
draft = false
weight = 5
+++
## Digitalización
#### Fotogrametería de un cráneo
**[Ricardo Espinosa Ruiz](https://www.ucm.es/directorio?id=30024) y Rafael Parrilla con fotos de [Pablo de Arriba](https://www.ucm.es/directorio?id=8570)**  
En este proyecto vamos a partir de las fotos realizadas a un modelo e un cráneo para posteriormente con [Meshroom](https://alicevision.org/#meshroom) conseguir un volumen que nos permita posteriormente imprimirlo. En esta tira de fotos puedes ver cuales han sido las posiciones de las tomas, y en el apartado de digitalización encuentras más detalles a cerca del proceso:  
  
![Tira cráneo](http://www.ricardoespinosa.es/tira_craneo.jpg)  
  
Las imágenes de las que partimos están en formato RAW para obtener la mejor resolución de partida, pero Meshroom no puede leer este tipo de archivo, por lo que hemos creado una acción en photoshop para pasar de 16 a 8 bits, y convertirlas a formato .TIF.  
Abrimos Meshroom e inciamos los isguientes pasos:  
1. Importamos en Meshroom las fotos (File>Import Images).
2. Guardamos el proyecto (File>Save)
3. En el menú de la parte superior clicamos el botón START. Veremos como en las cajas de Graph Editor se van procesando los pasos, y la linea verde que inidca un procesamiento correcto va avanzando de una caja a la siguiente.  ![Cráneo importado](http://www.ricardoespinosa.es/craneo-importado.jpg) 
4. Buscamos la carpeta en la que hemos guardado el proyecto, y vemos como se ha creado dentro una con nombre 'MeshroomCache'. Dentro de ella, en la capeta 'Meshing' tenemos el .OBJ creado. Este archivo lo conservamos, pero tiene mucha resolución, por lo que para imprimirlo posteriormente vamos a reducir le densidad de la malla. 
5. Inniciamos Blender e importamos el .OBJ que se ha creado en la carpeta MeshroomCache>Meshing.
6. En el panel lateral derecho despues de seleccionar el cuerpo 3D, malla , etc un icono de llave inglesa nos deja activar modificadores. Escogemos "Decimate" o "decimar" depende del idioma que tenga.


## Modelado 3D
#### Redondear esquinas con OpenScad
**[Ricardo Espinosa Ruiz](https://www.ucm.es/directorio?id=30024)**  
Vamos a modelar con [OpenScad](https://openscad.org/) una pieza que nos va a servir de base para apoyar unas vias de tren en una maqueta. Este ejercicio esta basado en la idea de como redondear piezas utilzando la función 'offset' que se explica en este [fantástico tutorial](https://learn.cadhub.xyz/docs/definitive-beginners/your-openscad-journey). Comenzamos abriendo un nuevo archivo en OpenSacad y guardándolo en la carpeta correspondiente. Nos va  aresultar muy útil hacer un boceto con todas la mediadas que necesitemos. Una vez tenemos las medidas, las incluimos como variables para poder utlizarlas en nuesto modelado:  
  
![Boceto](images/IMG_20240417_202328.jpg) 
  
~~~
xBase=28;
yBase=15;
xTop=19;
yTop=11;
alturabase=54;
alturaTop=1.5;
redondeo=2;
~~~  
Una vez incluidas, vamos a comenzar modelando la base y para ello dibujamos el cuadrado que la determine. la función "square" crea un cuadrado, y entre parténsis indicamos las mediadas 'x' e 'y':  
~~~
xBase=28;
yBase=15;
xTop=19;
yTop=11;
alturabase=54;
alturaTop=1.5;
redondeo=2;

square([xBase,yBase]);
~~~
Posteriormente hacemos une extrusión con la altura deseada:
~~~
xBase=28;
yBase=15;
xTop=19;
yTop=11;
alturabase=54;
alturaTop=1.5;
redondeo=2;

linear_extrude(alturabase)  
square([xBase,yBase]);
~~~
Ahora hacemos lo mismo con la parte superior
~~~
xBase=28;
yBase=15;
xTop=19;
yTop=11;
alturabase=54;
alturaTop=1.5;
redondeo=2;

linear_extrude(alturabase)  
square([xBase,yBase]);

linear_extrude(alturaTop)
square([xTop,yTop]);
~~~
No vemos la pieza que hemos llamado 'Top' porque está oculta dentro de la base, para desplazarla y que podamos verla incluimos la función translate:  
~~~
xBase=28;
yBase=15;
xTop=19;
yTop=11;
alturabase=54;
alturaTop=1.5;
redondeo=2;

linear_extrude(alturabase)  
square([xBase,yBase]);

translate([0,0,alturabase])
linear_extrude(alturaTop)
square([xTop,yTop]);
~~~
Ambos cuadrados cudrados comienzan a dibujarse desde el centro de coordenadas, pero incluyendo 'center=true' en cada uno de ellos, podemos hacer que se dibujen desde su centro:  
~~~
xBase=28;
yBase=15;
xTop=19;
yTop=11;
alturabase=54;
alturaTop=1.5;
redondeo=2;

linear_extrude(alturabase)  
square([xBase,yBase], center=true);

translate([0,0,alturabase])
linear_extrude(alturaTop)
square([xTop,yTop], center=true);
~~~
Por útltimo y para conseguir el redondeo, lo hacemos tal y como viene explicado en [esta web](https://learn.cadhub.xyz/docs/definitive-beginners/adding-fillets), quedando de la siguiente manera:  
~~~
xBase=28;
yBase=15;
xTop=19;
yTop=11;
alturabase=54;
alturaTop=1.5;
redondeo=2;

linear_extrude(alturabase){
    offset(redondeo)offset(-redondeo*2)offset(redondeo){
    square([xBase,yBase], center=true);
    }
}

translate([0,0,alturabase]){
        linear_extrude(alturaTop){
        offset(redondeo)offset(-redondeo*2)offset(redondeo){
        square([xTop,yTop], center=true);
        }
    }
}
~~~
Como hemos modelado la pieza de manera paramétrica, ahora basta con modificar alguna variable para que se ajuste todo el modelo. Una vez tenemos la pieza con las medidas deseadas, basta con renderizar la pieza y descargar el .STL.  
