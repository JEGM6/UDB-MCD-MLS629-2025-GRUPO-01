# Informe Final: Análisis Avanzado de ML No Supervisado para Control de Calidad

## Resumen de Metodología

Este análisis empleó técnicas de aprendizaje automático no supervisado para identificar patrones, defectos y optimizar procesos de control de calidad para lotes de productos en 2025. La metodología consistió en cuatro etapas principales:

1. **Análisis Exploratorio de Datos (EDA) y Preprocesamiento**: Exploración inicial de datos, limpieza y estandarización.
2. **Reducción de Dimensionalidad**: Análisis comparativo de PCA, t-SNE y UMAP para reducir características de control de calidad de alta dimensionalidad a representaciones 2D.
3. **Análisis de Agrupamiento**: Aplicación de K-means, DBSCAN y Agrupamiento Espectral para identificar patrones de calidad y anomalías.
4. **Interpretación y Conclusiones**: Integración de los mejores métodos para proporcionar insights accionables para el control de calidad en fabricación.

El conjunto de datos contenía resultados de pruebas de control de calidad en múltiples características, incluyendo mediciones de espesor, aspereza, contenido de carbono, densidad y varias métricas de resistencia. Todos los análisis se realizaron en características numéricas estandarizadas después de la eliminación de valores atípicos.

## Resultados de Cada Etapa

### EDA y Preprocesamiento
- **Resumen del Conjunto de Datos**: 22 características numéricas más identificadores (ItemID, LotNumber, manufacturedDate).
- **Calidad de Datos**: No se detectaron valores faltantes; valores atípicos eliminados usando el método IQR (Q1-1.5*IQR a Q3+1.5*IQR).
- **Preprocesamiento**: Características estandarizadas usando StandardScaler para normalización.
- **Insights Clave**: Se observaron correlaciones fuertes entre mediciones relacionadas (ej. métricas de espesor, propiedades de resistencia); las distribuciones mostraron sesgo variable en las características.

### Reducción de Dimensionalidad
- **PCA**: Explicó ~70% de varianza en los primeros 5 componentes; computación rápida pero limitada a estructuras lineales.
- **t-SNE**: Excelente preservación de estructura local (confiabilidad/continuidad ~0.8-0.9); más lento e inestable en ejecuciones.
- **UMAP**: Rendimiento equilibrado con preservación de vecindad ~0.85-0.95; estable y computacionalmente eficiente.
- **Selección**: UMAP elegido por la mejor preservación de variaciones no lineales de lotes mientras mantiene eficiencia computacional.

### Análisis de Agrupamiento
- **K-means**: k óptimo=3 basado en método del codo y análisis de silueta; bueno para clusters esféricos pero asume convexidad.
- **DBSCAN**: Ajustado con eps=0.5, min_samples=10; identificó 3-5 clusters más puntos de ruido como anomalías.
- **Agrupamiento Espectral**: Funcionó bien en estructuras no convexas pero intensivo computacionalmente.
- **Selección**: DBSCAN seleccionado por sus superiores capacidades de detección de anomalías cruciales para control de calidad.

### Interpretación y Conclusiones
- **Interpretación de Clusters**: Clusters centrales representan lotes de calidad consistente; puntos de ruido (-1) indican potenciales defectos de fabricación.
- **Análisis de Lotes**: Identificó lotes específicos con altas tasas de anomalías que requieren inspección.
- **Patrones de Características**: Los clusters mostraron perfiles distintos en mediciones de resistencia y espesor.

## Hallazgos Clave e Interpretaciones

- **Mejores Métodos**: UMAP para reducción de dimensionalidad combinado con DBSCAN para agrupamiento proporcionó resultados óptimos para análisis de control de calidad.
- **Patrones de Calidad**: Los clusters corresponden a diferentes niveles de calidad de lotes de productos, con lotes de alta calidad mostrando resultados consistentes en todas las características.
- **Detección de Anomalías**: Los puntos de ruido en DBSCAN representan potenciales defectos o valores atípicos en procesos de fabricación, permitiendo control de calidad proactivo.
- **Insights de Fabricación**: Los lotes anómalos a menudo exhiben desviaciones en parámetros críticos como resistencia a ruptura y resistencia al desgarro.

## Recomendaciones para Control de Calidad

1. **Monitoreo**: Inspeccionar de cerca lotes identificados con altas tasas de anomalías por potenciales problemas de fabricación.
2. **Sistemas de Alerta**: Implementar alertas automatizadas para clusters que muestren alta variabilidad o nuevos patrones anómalos.
3. **Análisis de Causa Raíz**: Investigar procesos de producción para lotes consistentemente marcados como defectuosos.
4. **Despliegue de Modelo**: Usar el pipeline UMAP+DBSCAN para monitoreo continuo de control de calidad.
5. **Mejora Continua**: Reentrenar modelos periódicamente con nuevos datos para mantener precisión.

## Limitaciones

- Los parámetros de DBSCAN (eps, min_samples) son sensibles y pueden requerir reajuste para nuevos conjuntos de datos.
- Asume que los puntos de ruido representan defectos, aunque algunos pueden ser variaciones legítimas del proceso.
- El rendimiento del modelo depende de la calidad de datos, consistencia de preprocesamiento y relevancia de características.
- Interpretabilidad limitada por transformaciones no lineales en UMAP.

## Notas de Reproducibilidad

- Usar random_state=42 para resultados consistentes en UMAP y algoritmos de agrupamiento.
- Documentar elecciones de parámetros (UMAP: n_neighbors=15, min_dist=0.1; DBSCAN: eps=0.5, min_samples=10).
- Validar pasos de preprocesamiento (eliminación de valores atípicos IQR, StandardScaler) en nuevos datos.
- Mantener control de versiones para conjuntos de datos y código para asegurar resultados reproducibles.

## Referencias a Notebooks

- [01-EDA_Preprocessing.ipynb](EDA_Preprocessing.ipynb): Exploración de datos, limpieza y preprocesamiento.
- [02-Dimensionality_Reduction.ipynb](Dimensionality_Reduction.ipynb): Análisis comparativo de PCA, t-SNE y UMAP.
- [03-Clustering_Analysis.ipynb](Clustering_Analysis.ipynb): Implementación y evaluación de algoritmos de agrupamiento.
- [04-Interpretation_and_Conclusions.ipynb](Interpretation_and_Conclusions.ipynb): Interpretaciones finales y recomendaciones accionables.

