# Proyecto EDA de Calidad del Vino

## Descripcion General

Este proyecto contiene un flujo completo de analisis exploratorio de datos (EDA) y limpieza de datos para el dataset de calidad del vino (vinos portugueses "Vinho Verde").

El analisis combina muestras de vino tinto y blanco, limpia y valida los datos, explora distribuciones de variables, detecta outliers y estudia relaciones entre variables fisicoquimicas y la calidad del vino.

Notebook principal de analisis:

- `parcial.ipynb`

Archivos de datos:

- `Wine/winequality-red.csv`
- `Wine/winequality-white.csv`
- `Wine/winequality.names`

## Objetivos

- Cargar y unir los datasets de vino tinto y blanco.
- Realizar controles de calidad de datos (nulos, duplicados, tipos de datos).
- Detectar outliers con el metodo IQR.
- Generar estadisticas descriptivas y distribuciones de calidad.
- Comparar perfiles entre vinos tintos y blancos.
- Analizar correlaciones con la variable objetivo (`quality`).
- Resumir hallazgos para futuros modelos predictivos.

## Stack Tecnologico

- Python 3.13+
- pandas
- numpy
- matplotlib
- seaborn
- jupyter
- ipykernel
- Poetry (gestion de dependencias y entorno)

Las dependencias del proyecto estan definidas en `pyproject.toml` y fijadas en `poetry.lock`.

## Estructura del Repositorio

```text
parcial/
	parcial.ipynb
	pyproject.toml
	poetry.lock
	readme.md
	Wine/
		winequality-red.csv
		winequality-white.csv
		winequality.names
```

## Flujo del Analisis (Notebook)

El notebook esta organizado en las siguientes secciones:

1. Importacion de librerias y configuracion de graficos.
2. Carga de datos y union con etiqueta `wine_type`.
3. Exploracion inicial (`shape`, columnas, `info`, filas de muestra).
4. Limpieza de datos (nulos, duplicados, ajustes de tipos).
5. Deteccion de outliers con IQR y visualizacion con boxplots.
6. Estadisticas descriptivas (global, por `wine_type`, por `quality`).
7. Analisis de distribucion de calidad y desbalance de clases.
8. Analisis de correlacion (heatmap y correlaciones ordenadas con quality).
9. Distribuciones de variables y boxplots por nivel de calidad.
10. Comparacion entre vino tinto y blanco y exploracion con pairplot.
11. Resumen final del analisis con conclusiones.

## Principales Hallazgos (EDA)

- El dataset combinado original tiene 6,497 filas; despues de eliminar duplicados quedan 5,320 filas.
- No se encontraron valores faltantes en el dataset final usado para el analisis.
- La calidad del vino se concentra en puntuaciones medias (principalmente 5, 6 y 7), mostrando desbalance en la variable objetivo.
- Los vinos blancos presentan una calidad promedio ligeramente superior a la de los vinos tintos.
- Hay diferencias de composicion importantes entre tipos de vino, sobre todo en variables de dioxido de azufre y azucar residual.
- Las variables mas asociadas con la calidad incluyen:
	- Positiva: `alcohol` (la relacion lineal positiva mas fuerte).
	- Negativas: `density`, `volatile acidity`, `chlorides`.
- Los boxplots por nivel de calidad confirman visualmente esas direcciones de correlacion.
- Existen outliers en multiples variables; es preferible un tratamiento robusto antes que eliminacion ciega.

## Requisitos para Replicar en tu Maquina

Necesitas:

- Git
- Python 3.13 o version compatible con Poetry
- Poetry instalado globalmente

### 1) Clonar el repositorio

```bash
git clone <url-de-tu-repo>
cd parcial
```

### 2) Instalar dependencias

```bash
poetry install
```

### 3) Activar el entorno virtual (opcional)

```bash
poetry shell
```

Si `poetry shell` no esta disponible en tu configuracion, ejecuta los comandos con `poetry run ...`.

### 4) Ejecutar Jupyter Notebook

```bash
poetry run jupyter notebook
```

Luego abre `parcial.ipynb` y ejecuta todas las celdas de arriba hacia abajo.

## Notas de Reproducibilidad

- Mantener la carpeta `Wine/` y los CSV en la misma ubicacion relativa respecto al notebook.
- El notebook lee los archivos con rutas relativas:
	- `Wine/winequality-red.csv`
	- `Wine/winequality-white.csv`
- Para resultados consistentes, usar las versiones fijadas en `poetry.lock`.

## Posibles Siguientes Pasos

- Construir un modelo base de clasificacion o regresion para predecir calidad.
- Comparar rendimiento por tipo de vino (modelo unico vs modelos segmentados).
- Tratar el desbalance de clases con tecnicas de remuestreo o pesos.
- Evaluar preprocesamiento robusto para manejar outliers.

## Autor

- brandone12

