----------------------------------------------------------- EXTRACCIÓN Y PREPROCESAMIENTO --------------------------------------------------------
(Este apartado no es el principal, empezamos haciendolo para poder hacer la clasificacion pero durante la clase, la profesora proporciono las proteinas ya
preprocesadas para aquellos que quisieran hacer clasificacion (nuestro caso) por lo que lo incluimos puesto que ya lo teniamos practicamente terminado.)

En este apartado hemos hecho La extracción y el preprocesado de los datos. Para lograr esto hemos hecho 3 funciones:

- leer_archivos_fasta(directorio): Esta función lee archivos fasta en un directorio, extrae las secuencias de nucleótidos y las almacena en un diccionario, 
donde las claves son los identificadores y los valores son las secuencias.

- search_first_codon(diccionario): Esta función busca el codón de inicio ("ATG") en las secuencias del diccionario proporcionado. Para cada secuencia, cuenta 
cuántas veces aparece el codón de inicio y muestra un mensaje indicando si la secuencia contiene o no un codón de iniciación.

- search_end_codon(diccionario): Similar a la función anterior, esta función busca los codones de terminación ("TAA", "TAG", "TGA") en las secuencias. Cuenta
las ocurrencias de estos codones y muestra un mensaje para cada secuencia indicando si contiene o no un codón de terminación.
Utilizamos los archivos pasados por la profesora los cuales contenian en formato fasta secuencias de ARM mensajero. Tambien hemos utilizado el módulo "os" 
para interactuar con el sistema operativo, facilitando la manipulación de archivos y directorios; y Biopython para facilita la manipulación de secuencias 
biológicas, permitiendo la lectura y el análisis sencillo de archivos FASTA.

El programa es adecuado para analizar secuencias biológicas porque utiliza Biopython para leer archivos FASTA de manera fácil, almacena las secuencias en 
un diccionario para un acceso rápido, y está organizado en funciones claras que facilitan su comprensión y modificación. Además, permite buscar codones de 
inicio y terminación de forma sencilla, lo que es clave para entender la traducción de los genes.

------------------------------------------------------------------- CLASIFICACIÓN ---------------------------------------------------------------
Este programa está basado en el caso 1 propuesto por la profesora, específicamente en el proceso de caso práctico "Modelos de clasificación".

El programa se compone de varias funciones que serán necesarias para la clasificación de las proteínas. La primera función, leer_fasta, se encarga 
de leer archivos en formato FASTA de proteinas ya preprocesados proporcionados por la profesora. Esta función identifica los archivos con la extensión 
.fasta, extrae las secuencias de proteínas de cada archivo gracias a la libreria BIO, capaz de leer archivos fasta sin problema y las almacena en una lista.
En esa lista, cada valor representa una proteina.

La segunda función, convertir_a_vectores, transforma estas secuencias de proteínas en vectores numéricos. Utiliza un alfabeto de 20 aminoácidos estándar 
y cuenta cuántas veces aparece cada aminoácido en cada secuencia. Esta conversión sera lo que permita al algoritmo de clasificacion poder hacer su trabajo, 
ya que permite representar las proteínas en un formato numerico.

A continuación, para la clasificacion utilizamos dos funciones:

- aplicar_kmeans: implementa el algoritmo K-means para agrupar las proteínas basándose en sus vectores. Este método identifica patrones y relaciones en los 
datos, asignando cada proteína a un grupo basado en su similitud. Las tecnologias utilizadas para este caso fueron los archivos proporcionados por la profesora, 
que contenían secuencias de proteínas en formato FASTA. Tambien empleamos from sklearn.cluster import KMeans para agrupar estas secuencias en clusters según su 
similitud. También utilizamos from sklearn.decomposition import PCA para reducir la dimensionalidad de los datos a dos dimensiones, facilitando así la 
visualización de los resultados del clustering.

- aplicar_dbscan: aplica el algoritmo de clustering DBSCAN a las secuencias de proteínas, etiquetando cada una como parte de un "cluster" o "outlier", para
posteriormente imprimir los resultados y el número estimado de clusters y puntos de outlier. Las tecnologias utilizadas para este caso fueron los pasados por 
la profesora, que contenían secuencias de proteínas en formato FASTA. Tambien hemos utilizado "from sklearn.cluster import DBSCAN" para agrupa secuencias de 
proteínas por densidad, identificando grupos similares y outliers; además también utilizamos "from sklearn.decomposition import PCA.

Finalmente, la función graficar_clusters utiliza el Análisis de Componentes Principales (PCA) para reducir la dimensionalidad de los vectores y visualizar 
los clusters resultantes en un gráfico. Esto facilita la interpretación de los resultados y permite observar cómo se agrupan las proteínas en función de 
sus características.

El enfoque implementado es adecuado para la clasificación de proteínas porque combina el procesamiento de datos estructurados con algoritmos de agrupamiento 
efectivos. La lectura de archivos FASTA y la conversión de secuencias en vectores numéricos permiten que los algoritmos K-means y DBSCAN identifiquen grupos 
similares y outliers basados en la composición de aminoácidos. Además, el uso de PCA para la reducción de dimensionalidad facilita la visualización e 
interpretación de los resultados, proporcionando una visión clara de cómo se agrupan las proteínas, en donde se observa que ambos algoritmos de clasificacion 
se comportan, (pese a que el obscan con mayor cantidad de clusters por su gran sensibilidad) de una manera similar. En conjunto, estas técnicas hacen que el 
enfoque sea robusto y eficaz para este caso en concreto de clasificacion de proteinas.
