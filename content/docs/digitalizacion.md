+++
title = "Digitalización"
draft = true
weight = 3
+++
Todo proceso de fabricación digital parte de un archivo digital, como su propio nombre indica.

## Fotogrametría

*25 de octubre de 2023*

La **fotogrametería** es una técnica que permite obtener un volumen digital tridimensional de un objetos físico, así como información sobre su color y textura. Para ello se utilizará una serie de fotografías tomadas alrededor de la pieza desde diferentes ángulos y alturas que permitan una visión lo más detallada y homogénea posible del objeto en si. Aunque esta técnica de digitalización es muy útil, debemos tener en cuenta que puede tener algunos límites, como las dificultades que puede tener el conseguir buenos resultados de objetos que sean especialmente brillantes, o que estén en movimiento. No obstante existen recursos para intentar eliminar dichos límites, como veremos más adelante.  
El material necesario para poder realizar el proceso es el siguiente: 
1) **Cámara de fotos** como veremos a continuación, partir de una buena imagen será fundamental, por lo que a priori, es recomendable usara una buena cámara. Algunos teléfonos móviles disponen, además de la cámara, de sensores que pueden facilitar la toma de datos.
2) Es recomendable usar un **trípode** para favorecer la nitidez de las imágenes.
3) Es recomendable utilizar una **mesa rotatoria** ya que será más sencillo hacer girar la pieza y dejar fija la cámara, que no girar con la cámara alrededor del objeto. En este caso hemos utilizado una mesa automatizada que está sincronizada con los disparos de la cámara, de manera que hace un disparo, gira la mesa 15 grados, y realiza el siguiente disparo, hasta completar el giro completo de la pieza. Esto nos da una idea aproximada de que por cada giro completo (necesitaremos hacer girar la pieza desde diferentes alturas) haremos una media de 24 fotografías.
4) También es recomendable trabajar en un set con la **iluminación** controlada, aunque como alternativa también podremos trabajar en exteriores.
5) Será de mucha utilidad utilizar un **fondo neutro** antireflectante.
6) Por último, necesitaremos un ordenador con **software** específico para hacer el procesado de las imágenes y obtener el volumen.

El proceso de trabajo debería ser el siguiente: 
1) **Colocar la pieza** de manera estable en la mesa giratoria. Debemos poder fotografiarla totalmente, por lo que o bien podemos construir una peana específica, o bien podemos girar la pieza para conseguir realizar las fotos desde todos los ángulos. Es importante que la pieza no se mueva durante la toma de las fotos.
2) Iluminarla correctamente. Una **iluminación** rasante ayudará a obtener una textura más detallada, mientras que una iluminación difusa ayudará a hacer una mejor captura del color.
3) Realizar las **fotografías**, teniendo en cuenta que la calidad de las mismas es uno de los factores clave en el resultado final. Para ello, debemos tener enfocado todo el objeto, intentando tener la mayor profundidad de campo posible. Podemos utilizar una [calculadora de profundidad de campo](https://www.photopills.com/calculators/dof), teniendo en cuenta que cerrar el diafragma y utilizar una lente angular (el software que utilizaremos posteriormente corrige las deformaciones) siempre nos va a favorecer. También es importante utilizar el ISO más bajo posible para evitar el ruido. Supongamos que hacemos tres ciclos de fotografías (uno para la parte superior de la pieza, uno medio y uno inferior), cada ciclo basta con que sea de 20 a 40 fotografías, dependiendo de la complejidad de la pieza, intentando que entre ellas haya un solapamiento de un 60-70%. El solapamiento puede ser menor si en la base tenemos un dibujo de rejilla, que pude en el alineamiento posterior de las imágenes (podíamos bajar hasta un 30-40%). Mantendremos mismo punto de enfoque, diafragma y velocidad de obturación en todas las tomas, teniendo en cuenta que la calidad de las imágenes será más importante que la cantidad. Si la cámara lo permite, es mejor dispara en RAW o TIF antes que en JPG, ya que la compresión de este último formato hace que la calidad de las imágenes sea peor.
4) Pasamos a la parte del procesado en el ordenador. El programa recomendado es [Reality Capture](https://www.capturingreality.com/) por su velocidad de procesamiento (hay que tener en cuenta que necesitaremos un ordenador con una buena tajeta gráfica). Importamos las fotografías y procedemos a alinearlas, para que se genere una nube de puntos. Una vez creada la nube, podemos restringir la zona que queremos que procese, dejando fuera artefactos, la peana, u otros elementos que no sean necesarios para el proyecto. Una vez generada la primera malla, que puede tener unos 50 millones de polígonos, y pesar 2 GB, es recomendable guardar el archivo original y exportarlo como .OBJ para conservar tanto el volumen como la textura y el color. Posteriormente, volvemos a exportar otra malla, pero esta vez limitando el número de polígonos a 3 millones, con lo que conseguimos un peso de 300 MB, y procedemos a colorearlo y crear la textura, para guardarlo también en .OBJ. Existe una alternativa de software open source, [Meshroom](https://alicevision.org/#meshroom), pero el tiempo de alineado de las fotos puede ser sensiblemente superior que con Reality Capture. [Agisoft](https://www.agisoft.com/) es un software de fotogrametería más enfocado a los espacios  que a los objetos.
Los puntos 3 y 4 de este flujo pueden ser hechos directamente con un teléfono móvil, existen app específicas como [Polycam](https://poly.cam/), o [Heges](https://hege.sh/), pero esta última sólo funciona con iOS.
5) Por último en [Blender](https://www.blender.org/) o un programa de modelado similar podríamos eliminar los artefactos que se hayan generado  al generar la malla, y que no nos interese conservar.

### Pros y contras
Como pros de este técnica podríamos destacar la versatilidad a la hora de adaptarse tanto objetos de pequeño formato como de gran formato. La facilidad de acceder a una cámara de fotos también podría ser tenida como una ventaja, ya que no requiere de un hardware costoso y específico como podría ser un escaner 3D. Como contras, se puede destacar que el procesamiento de grandes conjuntos de datos de imágenes puede ser intensivo en recursos computacionales y llevar tiempo. También que puede ser problemático el hacer fotogrameterias de objetos brillantes, aunque existen recursos como el cubrir la pieza con polvo de talco o similar 

## Modelado 3D

La última técnica que abordaremos para crear un archivo digital destinado a la fabricación digital es el modelado 3D. Esta técnica nos permite generar desde cero un volumen o una superficie que luego será fabricada. Es importante destacar que las técnicas previamente mencionadas no son independientes de esta; de hecho, es común que, tras realizar una fotogrametría o un escaneado, se importen los resultados a un programa de modelado para su refinamiento antes de proceder con la fabricación.

### 3D Builder
3D Builder es un software muy sencillo e intuitivo para la edición de modelos 3D, especializado en la reparación de mallas. Aunque es bastante básico para la creación de formas primitivas, permite modificarlas estableciendo cotas. Este programa es óptimo para salir de apuros o realizar pequeños retoques.

**Contras**: Su funcionalidad es limitada para proyectos más complejos y no ofrece tantas herramientas avanzadas como otros programas de modelado 3D.

### ZBrush
ZBrush es ideal para el esculpido, permitiendo trabajar con modelos que contienen un gran número de polígonos, lo que lo hace perfecto para piezas orgánicas con mucho detalle. Ofrece una biblioteca de figuras básicas que facilita no comenzar el modelado desde cero. Es muy útil para crear huecos y permite trabajar por capas, así como contar con un historial de cambios. Además, permite la visualización en 360 grados.

**Contras**: No es intuitivo y tiene una curva de aprendizaje compleja.

### Maya
Maya es excelente para la creación de videojuegos y animación, destacándose en la gestión de UVs. Además, es muy eficaz para renderizar los trabajos esculpidos en ZBrush.

**Contras**: Su interfaz puede ser complicada para los principiantes, y su costo es elevado, lo que puede ser una barrera para algunos usuarios.

### Blender
Blender es un software de modelado 3D de código abierto que ofrece una amplia gama de herramientas y capacidades para la creación y edición de modelos 3D.

**Contras**: Aunque es muy potente y versátil, su interfaz puede resultar poco intuitiva para nuevos usuarios, y puede requerir una considerable inversión de tiempo para dominar todas sus funcionalidades.

### FreeCAD
FreeCAD es una herramienta de modelado 3D de código abierto que se centra en la ingeniería y el diseño de productos. Es especialmente útil para proyectos de CAD paramétrico.

**Contras**: La interfaz puede ser menos intuitiva y amigable en comparación con otros programas de modelado 3D, y algunas de sus funcionalidades avanzadas pueden ser difíciles de dominar sin una capacitación adecuada.

### OpenSCAD
OpenSCAD es un software de modelado 3D basado en scripts que permite a los usuarios definir modelos 3D mediante un lenguaje de programación específico.

**Contras**: Requiere conocimientos de programación para su uso, lo que puede ser una barrera significativa para los usuarios sin experiencia en programación. Además, su enfoque en el modelado basado en scripts puede ser menos intuitivo para quienes prefieren una interfaz gráfica.

