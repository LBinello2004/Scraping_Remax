# 🏠 Análisis de Inmuebles RE/MAX (CABA y Buenos Aires)

Este proyecto implementa un pipeline completo de datos para **extraer, limpiar y enriquecer información de propiedades inmobiliarias** publicadas en RE/MAX Argentina, con foco en **CABA y Provincia de Buenos Aires**.

El objetivo es construir un dataset listo para análisis exploratorio (EDA) y modelado predictivo.

---

## 🚀 ¿Qué hace el proyecto?

- Scrapea propiedades desde la API de RE/MAX
- Filtra por:
  - 📍 Ubicación: CABA y Buenos Aires
  - 💼 Operación: venta y alquiler
  - 🏘️ Tipo: departamentos, casas, PH, etc.
- Limpia y estructura los datos
- Enriquece el dataset con nuevas variables
- Genera datasets listos para análisis

---

## 📁 Estructura del proyecto
remax_project/
│
├── scraper/
│ └── remax_scraper_ventas_alquileres_ba_caba.py
│
├── data/
│ ├── raw/
│ │ └── remax_base_completa.csv
│ │
│ ├── cleaned/
│ │ ├── remax_caba_limpio.csv
│ │ └── remax_resto_bsas_limpio.csv
│ │
│ └── enriched/
│ └── remax_caba_limpio_enriched.csv
│
├── notebooks/
│ ├── limpieza_remax.ipynb
│ └── enrichment_remax.ipynb
│
└── README.md


---

## ⚙️ Pipeline de datos
### 1. Scraping

Script principal:

- Consume la API de RE/MAX
- Filtra resultados antes de pedir el detalle (optimización clave)
- Evita duplicados
- Guarda por batches
- Tiene checkpoint → permite reanudar ejecuciones largas

Output:remax_base_completa.csv

---

### 2. Limpieza

Notebook:
- Normalización de variables
- Eliminación de duplicados
- Manejo de valores nulos
- Estandarización de columnas

Output: remax_caba_limpio.csv, remax_resto_bsas_limpio.csv

---

### 3. Enrichment

Notebook:
- Agregado de variables derivadas
- Preparación del dataset para análisis

Output: remax_caba_limpio_enriched.csv

---

## 🔄 Flujo del pipeline
API RE/MAX
↓
SCRAPER (filtrado + detalle + batches + checkpoint)
↓
remax_base_completa.csv
↓
LIMPIEZA (notebook)
↓
remax_caba_limpio.csv + remax_resto_bsas_limpio.csv
↓
ENRICHMENT (notebook)
↓
remax_caba_limpio_enriched.csv
↓
EDA / MODELADO

---

## 📊 Dataset final

Incluye variables como:

- 💰 Precio
- 🏘️ Tipo de propiedad
- 📍 Barrio
- 📐 Superficie (total, cubierta, etc.)
- 🛏️ Ambientes
- 📌 Ubicación (lat/lon)
- 🏢 Características adicionales

---

## 💡 Características destacadas

- 🔁 Ejecución reanudable (checkpoint)
- ⚡ Scraping optimizado (filtrado previo)
- 💾 Guardado incremental
- 🧹 Pipeline modular (scraping → limpieza → enrichment)

---

## 🎯 Usos posibles

- Análisis de precios inmobiliarios
- Modelos de predicción de precios
- Segmentación de propiedades
- Visualizaciones geográficas
- Insights del mercado inmobiliario

---

## 📌 Notas

- Los datos fueron obtenidos de fuentes públicas
- El dataset está orientado a fines académicos y analíticos
