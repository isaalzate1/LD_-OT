# Introducción

Este proyecto tiene como objetivo analizar ofertas de trabajo relacionadas con ciencia de datos para identificar tendencias, requerimientos y características clave de los empleos en el sector. Utilizamos dos conjuntos de datos: uno sin limpiar (uncleaned_data) y otro limpio (cleaned_data), con un total de 672 y 660 registros respectivamente, conteniendo información como títulos de trabajos, estimaciones salariales, ubicaciones, y más.

El proceso implicó lidiar con problemáticas comunes en la limpieza y estructuración de datos. Este documento detalla los desafíos encontrados, las soluciones implementadas y cómo se estructuraron los datos finales.

## Archivos principales:

- uncleaned_data: Contiene datos sin procesar.
- cleaned_data: Contiene datos preprocesados, enriquecidos con nuevas columnas calculadas.

## Problemáticas Identificadas y Soluciones

### 1. Separación de Location en City y State
- Problema: Algunas filas no seguían el formato esperado ("Ciudad, Estado"), lo que provocaba errores al dividir la columna.
- Solución: Se añadió una validación previa con str.contains(',') para asegurarse de que solo las filas en el formato correcto se procesaran:

### 2. Cálculo de antigüedad de la empresa (Company Age)
- Problema: Algunas empresas no tienen datos válidos en la columna Founded. Esto provocaba cálculos incorrectos o valores no deseados.
- Solución: Se calculó la antigüedad restando el año actual de la fecha de fundación, pero se asignaron valores nulos (NaN) para empresas sin datos:

### 3. Datos faltantes y problemas de formato en columnas clave
- Problema: Algunas columnas, como Competitors y Revenue, tenían valores nulos o textos inconsistentes.
- Solución: Se reemplazaron los valores nulos por NaN utilizando pd.NA y se procesaron las columnas según el análisis deseado.

### 4. Errores de asignación múltiple en Pandas
- Problema: Errores del tipo ValueError: Columns must be same length as key al intentar asignar valores calculados a nuevas columnas.
- Solución: Se validó previamente la longitud y el contenido de las series involucradas, asegurando consistencia en el proceso de asignació

### 5. Inconsistencias entre uncleaned_data y cleaned_data
- Problema: Las columnas de ambos datasets no coincidían en nombres ni estructura, lo que complicaba comparaciones.
- Solución: Se identificaron diferencias y se normalizaron las columnas necesarias, estandarizando nombres y transformaciones adicionales.

## Resultados Finales
El análisis permitió:

- Identificar las ciudades y estados con mayor oferta de trabajo en ciencia de datos.
- Evaluar tendencias salariales y habilidades más demandadas.
- Determinar antigüedad de las empresas y su relación con las ofertas laborales.