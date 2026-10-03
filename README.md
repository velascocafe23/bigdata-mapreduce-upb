# Taller MapReduce con Python puro: solución de ejercicios

**Autor:** Sebastián Velasco Ardila
**Programa:** Maestría en Ciencia de Datos, Universidad Pontificia Bolivariana
**Curso:** Big Data · **Docente:** Camilo Soto · **Fecha:** octubre de 2026

Solución de los ejercicios del módulo 1 (MapReduce con Python puro) del curso. Todo el trabajo está en el notebook [solucion_ejercicios.ipynb](solucion_ejercicios.ipynb), que se puede leer directamente en GitHub con sus salidas ya ejecutadas.

## Contenido

| Sección | Ejercicios | Temas |
|---|---|---|
| Nivel 1: fundamentos | 1.1 a 1.5 | Contador de caracteres, palabras largas, promedio de ventas, estadísticas de temperatura, conteo por categoría |
| Nivel 2: procesamiento de archivos | 2.1 a 2.3 | Distribución de longitud de palabras, palabras únicas por archivo, índice invertido |
| Nivel 3: retos avanzados | 3.1 a 3.4 | Top N palabras, bigramas, sesiones web, detector de anomalías |
| Rendimiento | P.1 y P.2 | Secuencial contra paralelo, efecto del tamaño de bloque |

Cada ejercicio incluye el objetivo, la solución con mapper y reducer documentados, la prueba del caso borde y las observaciones sobre el resultado.

## Hallazgos principales

1. **Ejercicio 3.4:** la regla de 2 desviaciones estándar no detecta la anomalía con los datos del enunciado. Con 3 lecturas es matemáticamente imposible que se active; se requieren al menos 6.
2. **Ejercicio P.1:** para un archivo de 0,75 MB, la ejecución paralela (0,454 s) es unas 4 veces más lenta que la secuencial (0,107 s), porque la sobrecarga de coordinación supera al trabajo útil.
3. **Ejercicio P.2:** los bloques muy pequeños penalizan el rendimiento: con 4 KB (183 bloques) el tiempo de pared es casi el doble que con 64 KB (12 bloques), por el costo fijo de cada bloque.
4. Varias salidas esperadas del enunciado (1.1, 2.2 y 2.3) son ilustrativas y no coinciden con el resultado real de los datos; cada caso está verificado y anotado en el notebook.

## Cómo ejecutarlo

El notebook depende del material del curso (`bigdata-101`), que no se incluye en este repositorio:

1. Copiar `solucion_ejercicios.ipynb` en la carpeta `modules/01-mapreduce/` del repositorio del curso. Usa rutas relativas al framework (`01-pure-python/01-basics/mapreduce_framework.py`), a los scripts de simulación distribuida (`01-pure-python/03-distributed-simulation/`) y a los datos (`../../datasets/`).
2. Abrirlo con Jupyter o VS Code y ejecutar las celdas en orden.

Requiere Python 3 sin librerías adicionales. Se ejecutó con Python 3.13 en Windows.
