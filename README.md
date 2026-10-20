# Caracterización oceanográfica y prevalencia de *Caligus rogercresseyi* en Aysén y Magallanes

Repositorio de investigación asociado a la memoria de título **“Caracterización oceanográfica mediante datos satelitales y su relación con la prevalencia de *Caligus rogercresseyi* en las regiones de Aysén y Magallanes”**, de Nicolás Andrés Pino Leal (2026).

El proyecto reúne procedimientos de extracción, preparación y análisis de datos sanitarios y oceanográficos para caracterizar y comparar las condiciones de las regiones de Aysén y Magallanes, y estudiar su relación con la presencia y prevalencia del piojo de mar en centros de cultivo de salmónidos.

El análisis utiliza registros sanitarios y variables ambientales, junto con herramientas estadísticas, métodos de agrupamiento no supervisado y modelos de aprendizaje automático. Entre las técnicas documentadas se encuentran las series temporales, los diagramas de caja, las pruebas estadísticas, K-means, el análisis de componentes principales (PCA), Random Forest, XGBoost y la interpretación de modelos mediante SHAP.

Los resultados deben interpretarse dentro del alcance de los datos y del diseño observacional del estudio. Las asociaciones estadísticas y la importancia predictiva de las variables no demuestran, por sí solas, relaciones causales.

## Metodología

El flujo de trabajo general comprende las siguientes etapas:

1. **Obtención de datos:** recopilación de registros sanitarios desde SERNAPESCA y extracción de información oceanográfica satelital desde Copernicus Marine.
2. **Preparación y limpieza:** revisión, transformación y organización de los datos para facilitar su integración y análisis. Los notebooks de descarga y ajuste documentan parte de este proceso.
3. **Exploración estadística:** descripción de las variables, elaboración de series temporales y diagramas de caja, y aplicación de pruebas estadísticas para explorar diferencias y patrones entre regiones.
4. **Comparación temporal y ambiental:** análisis de las observaciones y de las diferencias entre Aysén y Magallanes, considerando la disponibilidad y compatibilidad de los registros.
5. **Agrupamiento no supervisado:** aplicación de K-means y uso de PCA para explorar estructuras, agrupaciones y perfiles presentes en los datos.
6. **Modelado predictivo:** evaluación de modelos basados en árboles de decisión, particularmente Random Forest y XGBoost. El repositorio también contiene un notebook de redes LSTM y otros análisis complementarios.
7. **Interpretación de variables:** uso de SHAP para examinar la contribución de las variables a las predicciones de los modelos.
8. **Caracterización de perfiles:** integración de los resultados exploratorios, estadísticos y de modelado para describir patrones de infestación y condiciones ambientales en las dos regiones.

## Estructura del repositorio

El repositorio contiene notebooks de Jupyter, archivos de registro y carpetas de resultados. La descripción siguiente se basa en los nombres y la organización visibles en el repositorio; no implica que todos los archivos constituyan una única secuencia automática de ejecución.

### Descarga y preparación de datos

| Archivo | Función general |
| --- | --- |
| `descarga_magallan.ipynb` | Notebook asociado a la descarga o preparación de información para Magallanes. |
| `descargas_aysen.ipynb` | Notebook asociado a la descarga o preparación de información para Aysén. |
| `descargas2.ipynb` | Notebook complementario para procesos de descarga de datos. |
| `ajusteDataset.ipynb` | Preparación y ajuste de conjuntos de datos para análisis posteriores. |
| `ejemplo.ipynb` | Notebook de ejemplo o pruebas de procesamiento. |

### Exploración y análisis estadístico

| Archivo | Función general |
| --- | --- |
| `exploración.ipynb` | Análisis exploratorio de los datos y revisión de patrones. |
| `arima.ipynb` | Análisis de series temporales mediante técnicas asociadas a modelos ARIMA. |
| `Comparacion_Temporal/` | Carpeta con resultados relacionados con la comparación temporal. |
| `Resultados_Exploracion/` | Carpeta destinada a resultados del análisis exploratorio. |

### Agrupamiento y reducción de dimensionalidad

| Archivo | Función general |
| --- | --- |
| `PCA_Cluster.ipynb` | Notebook dedicado al análisis de componentes principales y agrupamiento. |
| `Resultados_PCA_Cluster/` | Carpeta con resultados asociados a PCA y clustering. |

### Aprendizaje automático e interpretación

| Archivo | Función general |
| --- | --- |
| `ML.ipynb` | Notebook de análisis de aprendizaje automático; el detalle de sus experimentos depende de las celdas ejecutadas y de los datos de entrada. |
| `rf_ml.ipynb` | Notebook relacionado con modelos Random Forest y aprendizaje automático. |
| `xg_ml.ipynb` | Notebook relacionado con modelos XGBoost y aprendizaje automático. |
| `LSTM.ipynb` | Implementación experimental de redes neuronales LSTM para análisis o predicción temporal. |
| `SHAP_RF_region/` | Resultados de interpretación SHAP asociados a Random Forest por región. |
| `SHAP_RandomForest/` | Resultados de interpretación SHAP para modelos Random Forest. |
| `SHAP_XGB_region/` | Resultados de interpretación SHAP asociados a XGBoost por región. |
| `Registro_RandomForest.xlsx` | Libro de registro relacionado con experimentos de Random Forest. |
| `Registro_XGBoost.xlsx` | Libro de registro relacionado con experimentos de XGBoost. |



## Requisitos

El proyecto utiliza Python y notebooks de Jupyter. Las bibliotecas declaradas en el repositorio incluyen:

- `copernicusmarine`
- `pandas`
- `xarray`
- `seaborn`
- `matplotlib`
- `openpyxl`
- `numpy`
- `scipy`
- `statsmodels`
- `scikit-learn`
- `xgboost`

El notebook `LSTM.ipynb` puede requerir dependencias adicionales para redes neuronales, según la implementación concreta. Antes de ejecutar ese notebook, se recomienda revisar sus importaciones y las versiones utilizadas.


## Fuentes de datos

- **SERNAPESCA:** registros sanitarios y productivos utilizados en la investigación.
- **Copernicus Marine:** información oceanográfica satelital utilizada para caracterizar las condiciones ambientales.

La disponibilidad de datos puede depender de las condiciones de acceso de cada servicio y de los archivos descargados durante el desarrollo del estudio.

## Organización y almacenamiento de los datos

Los datos del proyecto se organizan en dos directorios principales: coleccion/ y data/.

Nota sobre los datos: Las carpetas coleccion/ y data/ se encuentran excluidas del control de versiones mediante .gitignore debido al tamaño de los archivos (NetCDF y registros sanitarios). Para ejecutar los notebooks de manera local, es necesario crear ambas carpetas manualmente en la raíz del proyecto y poblar con la información correspondiente de SERNAPESCA y Copernicus Marine.

coleccion/: almacena los datos oceanográficos descargados desde Copernicus Marine. Esta carpeta contiene subcarpetas correspondientes a cada centro de cultivo, en las cuales se guardan los archivos en formato NetCDF (.nc) con las variables oceanográficas obtenidas.

data/: contiene los archivos CSV con los conjuntos de datos utilizados en los análisis, así como el archivo Excel con los registros parasitarios empleados para construir los datasets. Estos archivos constituyen la base para los procesos de limpieza, integración y análisis estadístico posteriores.

## Memoria de título

**Título:** *Caracterización oceanográfica mediante datos satelitales y su relación con la prevalencia de Caligus rogercresseyi en las regiones de Aysén y Magallanes.*

**Autor:** Nicolás Andrés Pino Leal.

**Año:** 2026.

## Agradecimientos

ANID Fondecyt de Iniciación 11261470
