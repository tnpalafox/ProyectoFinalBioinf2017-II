# RESUMEN STACKS

Contiene los scripts de la línea de comando que se utilizaron para  demultiplexar los datos crudos.

## Partes del repositorio:
+ [1. Línea de comando de Limpieza y Demultiplexeo](./1Limpieza_Demultiplexeo) aquí se encuentra el script que se utilizó para demultiplexear las lecturas crudas.

En mi trabajo la línea de comando de limpieza y demultiplexeo es el script 1

###1 Línea de comando Limpieza/Demultiplexeo
---------------------------
Aquí vive el script usado para demultiplexear las lecturas crudas. Utilicé la línea de comando de Stacks [ *process_radtags*, Catchen, 2017.](http://catchenlab.life.illinois.edu/stacks/comp/process_radtags.php) Con esta línea de comando 
es posible examinar las lecturas crudas de una secuencia de secuenciación de Illumina (que es el tipo de datos con los que cuento) y:

**1.**

* Comprueba que los códigos de barras y el corte con las enzimas (utilizadas en los métodos RAD) estén intactos
* Demultiplexa los datos. 
* Si existen errores ya sea en el código de barras o en el o los sitios de corte (dentro de un cierto límite),  *process_radtags* puede corregirlos. 

**2.**

* Desliza una ventana debajo de la longitud de lectura y checa el puntaje de la calidad promedio dentro de la ventana. Si la puntuación cae por debajo del 90% de probabilidad de ser correcta (una puntuación de phred cruda de 10), la lectura se descarta. Esto permite algunos errores de secuenciación mientras que elimina lecturas donde la secuencia se está degradando conforme  se está secuenciando. 
 
* De forma predeterminada, la ventana es 15% de la longitud de la lectura, pero se puede especificar en la línea de comando otro porcentaje (el umbral y el tamaño de la ventana se pueden ajustar).



| **Este programa puede:** | 
| :----------- | :------: | ------------: | :----------- | :------: | ------------: |
| Manejar datos que están codificados en un código de barras, o sin codificar.|
|Usar códigos de barras combinados.|
|Comprueba y corrige el sitio de corte de las enzimas de restricción para datos digeridos una o dos veces.|       
|Procesar archivos individuales o todo un directorio de archivos.| 
|Leer/escribir directamente datos comprimidos|
|Nombrar archivos de salida de acuerdo con sus nombres de ejemplo en lugar de nombres de código de barras.|
​
​
