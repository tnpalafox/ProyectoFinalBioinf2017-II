# Avance 2


Después de mucho pensar, decidí que mi objetivo es aprender a usar diferentes líneas de comando para el análisis de datos RAD (ya que aún no cuento con los míos), trabajaré con los datos de _Berberis alpina_, ya que en mi proyecto trabajré con datos ddRAD. En este tiempo hice lo siguiente:

1. Desmenucé el artículo de [Mastretta-Yanes, _et al_. (2015)](https://www.ncbi.nlm.nih.gov/pubmed/24916682) para poder entender que es lo que hizo, y cómo lo hizo.
En este trabajo Alicia:
	* Realizó el filtrado de calidad y demultiplexeado de sus datos con un script que realizó de Perl. A diferencia de ella **yo** utilizaré *process _ radtags* el cuál es un programa que permite el procesamiento de datos single y double ended.
	
	* Ensambló los datos *de novo* e hizo el genotipado usando Stacks v1.02 utilizando los ajustes que vienen por default y después modificando varios parámetros. Yo utilizaré Stacks v1.46, que es la versión más actual.
	
2. Leí el artículo de [Torkamaneh, _et al_. (2016)] (http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0161333) en el cuál comparan siete líneas de comando, 5 de ellas para datos que cuentan con genoma de referencia y dos para modelos sin genoma de referencia. Como no hay genoma de referencia de _Berberis alpina_ las dos últimas líneas de comando del artículo me son útiles; por lo tanto usaré Stacks y UNEAK.

3. Bajé los datos con los que trabajaré, del siguiente link: [Mastretta-Yanes, _et al_. (2015) _en_ DRYAD](https://datadryad.org/resource/doi:10.5061/dryad.g52m3).

4. Leí artículos a continuación enlistados para poder entender las líneas de comando que utilizaré:

 *[Lu, _et al_. (2012)] (https://bytebucket.org/tasseladmin/tassel-5-source/wiki/docs/TasselPipelineUNEAK.pdf?rev=9ec92a485337109fc3f4228b7218a797a5e718e7)
 
 *[Lu, _et al_. (2013)] (http://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1003215)
 
 *[Glaubitz, _et al_. (2014)] (http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0090346)


5.UNEAK es una línea de comando de llamado de SNPs para organismos sin genoma de referencia, es una extensión de el programa Java TASSEL. Consulté las siguientes páginas esperando poder entender UNEAK :

* [Byers (2014)] (https://prezi.com/1d_7sa8btbde/uneak-pipeline/)

* [Lu] (http://cbsu.tc.cornell.edu/lab/doc/GBS_workshop_Fei_Lu.pdf)


6.Emepecé a hacer mis archivos en Macdown, específicamente el archivo de Resumen el cual pueden encontrar aquí:
[Mi Github] (ProyectoFinalBioinf2017-II/limpieza:demultiplexeo.md )


###Problemas a los que me estoy enfrentando:
+ Tengo una bronca bien básica. Estoy tratando de bajar las secuencias crudas de DRYAD desde mi terminal, para ello estoy usando el comando curl, aquí mi comando (con los ID de cada secuencia):

```
curl -s "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=sequences&id=SRX435319,SRX435317,SRX435316,SRX435315,SRX435314,SRX435313,SRX435312,SRX435311,SRX435310,SRX435309,SRX435308,SRX435307,SRX435306,SRX435305,SRX435304,SRX435303,SRX435302,SRX435301,SRX435300,SRX435299,SRX435298,SRX435297,SRX435296,SRX435295,SRX435294,SRX435293,SRX435292,SRX435291,SRX435290,SRX435289,SRX435288,SRX435287,SRX435286,SRX435285,SRX435284,SRX435283,SRX435282,SRX435281,SRX435280,SRX435279,SRX435278,SRX435277,SRX435276,SRX435275,SRX435274,SRX435273,SRX435272,SRX435271,SRX435270,SRX435269,SRX435268,SRX435267,SRX435266,SRX435265,SRX435264,SRX435263,SRX435262,SRX435261,SRX435260,SRX435259,SRX435258,SRX435257,SRX435256,SRX435255,SRX435254,SRX435253,SRX435252,SRX435251,SRX435250,SRX435249,SRX435248,SRX435247,SRX435246,SRX435245,SRX435244,SRX435243,SRX435242,SRX435241,SRX435240,SRX435239,SRX435238,SRX435237,SRX435236,SRX435235,SRX435234,SRX435233,SRX435232,SRX435231,SRX435230,SRX435229,SRX435228,SRX435227,SRX435226,SRX435225" ; 
```

Pero me marca el siguiente error:
>ID list is empty! In it there are neither IDs nor accessions.
 Error: CEFetchPApplication::proxy_stream(): HTTP/1.1 400 Bad Request
 
 Ya busqué en los foros de ayuda, y mencionan que cuando sale ese error es por que no se está metiendo el código de la manera adecuada, sin embargo ya le dí mil vueltas y no logro encontrar el error.
 
 
+ Tengo una duda: En su paper, Alicia hizo un script de Perl personalizado, las muestras con las que cuenta son single single end y justo como esa línea de comando que ella utilizó trabajo con datos pair end, tuvo que hacer una copia y renombrar los archivos fastq para hacer un "fake P2 pair".

Ya que yo usaré *process_radtags* (que acepta tanto datos single como double end) no haré este paso peeeero... ella también quitó la base  70 en todas las lecturas demultiplexeadas ya que un error en secuencias BERL3 que causaba un efecto lane... yo no quiero quitarlo ya que de acuerdo a *process_radtags* corrige ese tipo de errores , ¿hago y entiendo bien? no quisiera regar el tepache gacho.