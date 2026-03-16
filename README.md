# Lab 3 - Minería de Datos: Análisis Exploratorio y Modelos Predictivos de Airbnb

**Autores:** Jose Sanchez, Roberto Najera, Andre Pivaral 
**Fecha:** Marzo 2026
**Curso:** Minería de Datos

---

## Descripción

Este laboratorio analiza el dataset de publicaciones de Airbnb en ciudades de Estados Unidos con dos objetivos principales:

1. **Explorar y entender la estructura del dataset** mediante análisis exploratorio y clustering
2. **Predecir el precio por noche** usando modelos de regresión lineal y regularización

El dataset (`listings.RData`) contiene **171.748 registros** y **80 variables** de alojamientos en 10 ciudades/regiones de EE.UU.

---

## Estructura del Proyecto

```
lab3MD/
├── lab3.Rmd          # Código fuente R Markdown
├── lab3.html         # Informe interactivo (abrir en navegador)
├── lab3.pdf          # Informe en PDF
└── listings.RData    # Dataset de Airbnb
```

---

## Contenido del Informe

### Análisis Exploratorio (Actividades 1-8)
- Descripción del dataset: 10 ciudades, distribución de listings
- Limpieza de datos: manejo de valores faltantes y outliers de precio
- Distribución de precios por ciudad y tipo de alojamiento
- Puntajes de reseñas y correlaciones entre variables numéricas

### Clustering K-means (Actividad 5-8)
Se identificaron **4 perfiles de alojamiento** mediante K-means:

| Cluster | Perfil | Características |
|---------|--------|-----------------|
| 1 | Económico pequeño | Precio bajo, 1-2 huéspedes |
| 2 | Gama media | Precio moderado, uso estándar |
| 3 | Premium para grupos | Precio alto, alta capacidad |
| 4 | Largo plazo | Precio variable, alta disponibilidad |

### Modelos de Regresión (Actividades 9-13)
Se construyeron y compararon **7 modelos predictivos** del precio:

| Modelo | Descripción |
|--------|-------------|
| Simple | Solo `accommodates` como predictor |
| Múltiple | `accommodates`, `bedrooms`, `beds`, `review_scores_rating` |
| Stepwise | Selección automática de variables |
| Modelo final | Variables seleccionadas + análisis de residuos completo |
| Ridge | Regresión con regularización L2 |
| Lasso | Regresión con regularización L1 (selección de variables) |
| ElasticNet | Combinación de Ridge y Lasso |

**Variables más importantes para predecir el precio:** `accommodates`, `bedrooms`, `review_scores_rating`

---

## Principales Hallazgos

- Los Ángeles (26.5%) y Nueva York (21.1%) concentran casi la mitad de los listings
- La mediana del precio por noche es ~$193 USD con fuerte asimetría hacia precios altos
- El 74% de los listings corresponde a alojamiento completo ("Entire home/apt")
- Ningún modelo presenta sobreajuste significativo (diferencia R² train/test < 0.01)
- Los modelos de regularización no superan significativamente a los modelos lineales clásicos, dado que la multicolinealidad no es severa

---

## Requisitos para Ejecutar

### Software
- R >= 4.0
- RStudio (recomendado)

### Paquetes R
```r
install.packages(c("tidyverse", "ggplot2", "scales", "cluster",
                   "factoextra", "knitr", "corrplot", "glmnet", "car"))
```

### Compilar el informe
Abrir `lab3.Rmd` en RStudio y presionar **Knit** (PDF o HTML).

> El archivo `listings.RData` debe estar en el mismo directorio que `lab3.Rmd`.
