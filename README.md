# Análisis Avanzado de ML No Supervisado para Control de Calidad

Este proyecto realiza un análisis avanzado de aprendizaje automático no supervisado en datos de control de calidad para identificar patrones, defectos y optimizar procesos de fabricación utilizando el conjunto de datos `dataset.csv`.

## Instalación

1. Clona el repositorio.
2. Instala las dependencias requeridas:
   ```
   pip install -r requirements.txt
   ```
   El archivo `requirements.txt` incluye: pandas, scikit-learn, numpy, matplotlib, seaborn, plotly, umap-learn.

## Uso

Ejecuta los cuadernos de Jupyter en el siguiente orden para un análisis completo:

1. **EDA_Preprocessing.ipynb**: Realiza análisis exploratorio de datos, limpieza de datos y preprocesamiento.
2. **Dimensionality_Reduction.ipynb**: Aplica técnicas de reducción de dimensionalidad.
3. **Clustering_Analysis.ipynb**: Realiza análisis de agrupamiento en los datos reducidos.
4. **Interpretation_and_Conclusions.ipynb**: Interpreta los resultados, identifica anomalías y proporciona recomendaciones.

Cada cuaderno se basa en el anterior, asegurando un flujo de trabajo estructurado.

## Descripción del Conjunto de Datos

- **Fuente**: Resultados de pruebas de control de calidad para lotes de productos en 2025.
- **Columnas**:
  - `ItemID`: Identificador único para cada Proucto.
  - `LotNumber`: Identificador de lote.
  - `manufacturedDate`: Fecha de fabricación.
  - `THICK-MIN`, `THICK-AVG`, `THICK-LEFT-EDGE`, `THICK-RIGHT-EDGE`: Mediciones de grosor.
  - `ASPERITYBOT`, `ASPERITYTOP`: Mediciones de aspereza (rugosidad).
  - `CARBONMEM`: Contenido de carbon.
  - `DENSITY`: Densidad del material.
  - `MDTBELONG`, `TDTBELONG`: Mediciones de Elongacion a la rotura (Tensile Break Elongation MD and TD) en direcciones máquina y transversal.
  - `MDYIELONG`, `TDYIELONG`: Elongación por limite elastico (Tensile Yield Elongation MD and TD) en direcciones máquina y transversal.
  - `MDTBSTR`, `TDTBSTR`: Resistencia a la ruptura por tracción (Tensile Break Strength MD and TD) en direcciones máquina y transversal.
  - `MDTYISTR`, `TDTYISTR`: Resistencia a la Traccion (Tensile Yield Strength MD and TD) en direcciones máquina y transversal.
  - `TEARMD`, `TEARTD`: Resistencia al desgarro (Tear Strength MD and TD) en direcciones máquina y transversal.
  - `MELTFLOWMEM`: Índice de Fluidez (Melt Flow).
  - `OIT`: Tiempo de inducción de oxidación (Oxidative Induction Time).
  - `PINPUNCTURE`: Resistencia a la perforación (Pin Puncture).
- **Preprocesamiento**:
  - Imputar valores faltantes en columnas numéricas con la media.
  - Eliminar valores atípicos utilizando el método del Rango Intercuartílico (IQR).
  - Estandarizar características numéricas utilizando StandardScaler para normalización.

## Hallazgos Clave

- **Mejores Métodos**: UMAP para reducción de dimensionalidad combinado con DBSCAN para agrupamiento.

- **Interpretaciones**:
  - Los clústeres representan diferentes niveles de calidad de lotes de productos.
  - Los puntos de ruido (anomalías) indican posibles defectos o valores atípicos en el control de calidad.
  - Los lotes de alta calidad muestran resultados de pruebas consistentes en todas las características.
- **Recomendaciones**:
  - Monitorear de cerca los lotes con altas tasas de anomalías.
  - Implementar alertas automatizadas para clústeres con alta variabilidad.
  - Investigar las causas raíz en los procesos de producción para lotes defectuosos.
  - Utilizar el modelo de agrupamiento para control de calidad continuo y reentrenar periódicamente con nuevos datos.

## Autores
## GRUPO 01
- AT172560 – Leonardo Antonio Aguilera Torres
- BM252943 – Brenda Carolina Barillas Marroquín
- GM131896 – Josué Elías Granados Martínez
- RH252948 – Heedy Eufemia Ramírez Hernández

## Licencia

Este proyecto está licenciado bajo la Licencia MIT - consulta el archivo LICENSE para más detalles.
