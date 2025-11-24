Desarrollar un análisis avanzado de aprendizaje no supervisado (Machine Learning) utilizando el dataset contenido el archivo @/dataset.csv 
El dataset seleccionado contiene los resultados de diferentes pruebas realizadas sobre diferentes lotes de un mismo producto para el año 2025
Cada resultado de cada prueba es una misma columna.

1.	Reducción de dimensionalidad: Aplicar las tecnicas PCA, t-SNE y UMAP. Realizando un análisis comparativo riguroso que justifique cuál proporciona la mejor representación de los datos, incluyendo visualizaciones interpretables y métricas de evaluación.

2.	Clustering: Implementación de los algoritmos de clustering K-means, DBSCAN y Spectral Clustering, realizando una evaluación exhaustiva mediante múltiples métricas internas (como silueta, Davies-Bouldin, Calinski-Harabasz, etc.) además de proporcionar una interpretación detallada de los clusters obtenidos en el contexto del dominio de aplicación.

Entregables
* README.md completo con instrucciones de reproducibilidad
* Documentación del proyecto

Entrables de Codigo
* Notebook de exploración y preprocesamiento de datos
* Notebook de reducción de dimensionalidad (Debe contener las tecnicas PCA, t-SNE y UMAP y un resumen de cual de ellos es el mejor para el dataset proporcionado y su justificacion)
* Notebook de clustering (Debe contener los algoritmos  K-means, DBSCAN y Spectral Clustering y un resumen de cual de ellos es el mejor para el dataset proporcionado y su justificacion)
* Notebook de interpretación y conclusiones (Generar las interpretaciones y conclusiones basadas en la mejor tecnica y algoritmo seleccionado. Y preparar conclusiones utiles para un humano)

El análisis realizado utilizando estas tecnicas y la documentacion debe estar orientado al Control de Calidad
Si es necesario puedes crear nuevos dataset para cada caso de uso a partir del dataset original