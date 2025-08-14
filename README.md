# Laboratorio 3 – Análisis GeoEspacial y Sensores Remotos

Este repositorio contiene el código, datos y reporte correspondientes al **Laboratorio 3** de la asignatura *Data Science*, cuyo objetivo es analizar cambios en la cobertura vegetal del departamento de Petén, Guatemala, entre enero de 2020 y enero de 2024, utilizando imágenes Sentinel-2 L2A.

## 📂 Contenido del repositorio

- `Lab_3_Area_deforestada.ipynb` – Notebook de Jupyter con el código completo del análisis.
- `2020-B04.tiff` / `2020-B08.tiff` – Bandas Rojo (B04) y NIR (B08) para enero 2020.
- `2024-B04.tiff` / `2024-B08.tiff` – Bandas Rojo (B04) y NIR (B08) para enero 2024.
- `Reporte.pdf` – Informe final con metodología, resultados, métricas y conclusiones.
- Figuras generadas:
  - `fig_diff_ndvi.png`
  - `fig_mask_def.png`

## 🎯 Objetivos

- Descargar y preprocesar imágenes Sentinel-2 L2A con baja nubosidad para el AOI definido.
- Calcular el **NDVI** para 2020 y 2024.
- Detectar cambios en la cobertura vegetal mediante la diferencia de NDVI y umbrales.
- Calcular métricas de área deforestada y generar visualizaciones claras.

## 🗺️ Área de estudio

- **Región:** Departamento del Petén, Guatemala.
- **Coordenadas aprox.:** Latitud 17.25°, Longitud −89.9°.
- **Fechas:** Enero 2020 y Enero 2024.
- **Cobertura de nubes:** ≤ 10%

## ⚙️ Metodología resumida

1. **Obtención de datos:** Descarga de imágenes Sentinel-2 L2A (B04 y B08) desde [Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/).
2. **Preprocesamiento:** Recorte al AOI, conversión a `float32`, filtrado por baja nubosidad.
3. **Cálculo NDVI:**
   ```python
   NDVI = (NIR - Red) / (NIR + Red)
   ```
4. **Diferencia NDVI:** `NDVI_2024 - NDVI_2020`
5. **Máscara de deforestación:** Umbral `< -0.2` aplicado a la diferencia.
6. **Cálculo de métricas:** Reproyección a EPSG:32616 y conversión de píxeles a hectáreas.

## 📊 Resultados clave

- **Área deforestada:** 154,892.25 ha
- **Porcentaje sobre el AOI:** 2.82 %
- **Zona con mayor pérdida:** Sector Suroeste (SW) (~42.0% de los píxeles con pérdida).

## 🖼️ Visualizaciones

- **NDVI 2020 y 2024** – Mapas comparativos de salud de vegetación.
- **Diferencia de NDVI** – Áreas con valores negativos indican pérdida de vegetación.
- **Máscara de deforestación** – Zonas con pérdida significativa según el umbral.

## 📦 Requisitos

Este proyecto utiliza Python 3.10 y las siguientes librerías:

```bash
pip install rasterio numpy matplotlib
```

## ✍️ Autores

- Gabriel Paz – 221087
- Christian Echeverría – 221441

**Fecha:** 14 de agosto del 2028  
**Universidad del Valle de Guatemala – Facultad de Física – Data Science**
