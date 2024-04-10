+++
title = "Impresión 3D"
draft = false
weight = 5
+++
## Impresión 3D  
La impresión 3D, también conocida como fabricación aditiva, ha emergido como una tecnología de fácil acceso en el ámbito de la fabricación de objetos tridimensionales. En contraste con los métodos tradicionales de manufactura, caracterizados por procesos sustractivos o de conformado, la impresión 3D se fundamenta en la construcción de objetos mediante la deposición de material capa por capa. Aunque existen diferentes tipos de impresión 3D, esta característica de construir objetos por capas es común de todos ellos. Los más habituales son los siguientes:
1. **FFF** (Fused Filament Fabrication): También conocida como FDM (Fused Deposition Modeling), esta técnica de impresión 3D utiliza un filamento termoplástico que se funde y extruye a través de una boquilla. La boquilla se mueve en un patrón predefinido sobre una plataforma, depositando el material capa por capa para construir el objeto deseado. FFF es uno de los métodos más populares debido a su accesibilidad, bajo costo y versatilidad en la impresión de una amplia variedad de materiales, incluyendo PLA, ABS, PETG, entre otros.
2. **Estereolitografía** (SLA): La estereolitografía es un método de impresión 3D que utiliza un proceso de fotopolimerización para solidificar resinas líquidas mediante la exposición a luz ultravioleta. En un tanque de resina, un láser o una fuente de luz digital proyecta patrones sobre la superficie, solidificando selectivamente la resina capa por capa para formar el objeto deseado. La estereolitografía es conocida por su alta precisión y la capacidad de producir detalles finos, lo que la hace ideal para aplicaciones que requieren una calidad superficial excepcional, como prototipado de alta fidelidad, modelos dentales y joyería.
3. **Sinterizado Selectivo por Láser** (SLS): En el sinterizado selectivo por láser, un láser de alta potencia se utiliza para fusionar selectivamente polvos de material, como poliamida (nylon) o polvo metálico, capa por capa, según un modelo digital tridimensional. Este proceso crea objetos sólidos a partir de polvo suelto, eliminando la necesidad de soportes de impresión y permitiendo la fabricación de piezas con geometrías complejas y una amplia gama de materiales. El SLS es ampliamente utilizado en la fabricación de prototipos funcionales, piezas de producción y componentes industriales debido a su capacidad para producir objetos resistentes y de alta calidad.
   
Como hemos visto en el flujo de trabajo de fabricación digital, una vez tenemos un archivo digital el paso siguiente es ajustarlo para poder fabricarlo, y para ello necesitamos darle una serie de parámetros y convertirlo en un formato que pueda entender la impresora. Básicamente lo que debemos hacer es pasar un .STL a .GCODE. En este [enlace](https://ucomplutense-my.sharepoint.com/:v:/g/personal/ricaresp_ucm_es/EQAFfG5AjQxJoD0yv1Glg5oB5L56j01oE0ZRnJroh3QiGQ) puedes ver un vídeo del proceso básico.   
La checklist básica para imprimir desde Cura sería la siguiente:  
En el menú superior  
1. **Impresora seleccionada** Será el primer paso, ya que de ello depende el volumen de impresión, la tempratura, velocidad de trabajo...  
2. **Material y tamaño de boquilla** El estándar será PLA y boquilla de 0,4 mm.  
En el menú lateral de la izquierda  
3. **Tamaño de la pieza**  
4. **Posición en el plato** El centro del plato de impresión es el lugar óptimo. Hay que girar la pieza para evitar que haya partes en voladizo.  
A la derecha del menú superior  
5. **Altura de la capa** Mayor altura de capa = menor calidad y menor tiempo de impresión.  
6. **Relleno** Suele ser suficiente con un 10-20%.  
7. **Soportes**  
8. **Adherencia al plato**  
Y en "vista previa" del menú superior  
9. **Revisar la capa 1**
