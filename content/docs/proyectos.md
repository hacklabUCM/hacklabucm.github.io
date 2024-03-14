+++
title = "Proyectos"
draft = true
weight = 5
+++
## Digitalización
#### Fotogrametería de un cráneo
Ricardo Espinosa con fotos de Pablo de Arriba  
En este proyecto vamos a partir de 106 fotos realizaas a un modelo e un cráneo para posteriormente con [Meshroom](https://alicevision.org/#meshroom) conseguir un volumen que nos permita posteriormente imprimirlo. En esta tira de fotos puedes cuales han sido las posiciones de las tomas, en el apartado de digitalización encuentras más detalles a cerca del proceso:  
  
![Tira cráneo](http://www.ricardoespinosa.es/tira_craneo.jpg)  
  
Las imágnes de las que partimos estan en formato RAW para obtener la mejor resolución de partida, pero Meshroom no puede leer este tipo de archivo, por lo que hemos crado una acción en photoshop para pasar de 16 a 8 bits, y convertirlas a formato .TIF. En este enlace puedes descargar directamente las fotos ya convertidas, y en este optro encuentras las imágenes originales.  
Abrimos Meshroom e inciamos los isguientes pasos:  
1. Importamos en Meshroom las fotos (File>Import Images).
2. Guardamos el proyecto (File>Save)
3. En el menú inferior (Graph Editor) hacemos zoom en la caja de la izquierda, y con el botón derecho del ratón sobre el título "CameraInit" clicamos Compute, y luego en la parte superior clicamos el botón START. Veremos como en las cajas de Graph Editor se van procesando los pasos, y la linea verde que inidca un procesamiento correcto va avanzando de una caja a la siguiente.
