# Proyecto: Detección de Anomalías en Sensores Industriales

Este proyecto demuestra el uso de **aprendizaje no supervisado** para detectar anomalías en los datos de sensores de una planta química simulada. El objetivo es identificar estados operativos inusuales que podrían indicar una falla potencial en el equipo o un problema en el proceso.

---

## 🎯 Objetivo de Negocio

En un entorno industrial, las fallas inesperadas de los equipos pueden costar millones en reparaciones y tiempo de inactividad. Este modelo busca crear un sistema de alerta temprana que identifique desviaciones del comportamiento normal, permitiendo un mantenimiento predictivo y proactivo.

---

## 🛠️ Proceso y Herramientas

1.  **Generación y Preparación de Datos:**
    * Se generó un conjunto de datos simulado para 5 sensores usando **Python** y **Pandas**.
    * Se utilizó **SQL** (con agregación condicional) para pivotar los datos de un formato largo a uno ancho, preparando los datos para el análisis.

2.  **Selección de Clusters (K):**
    * Se aplicaron dos técnicas para determinar el número óptimo de "estados operativos normales": el **Método del Codo** y el **Análisis de Silueta**.
    * El Análisis de Silueta mostró un pico claro en **K=6**, lo que indicó que esta era la agrupación más coherente.

3.  **Modelado y Detección de Anomalías:**
    * Se entrenó un modelo de clustering **K-Means** con K=6 para aprender los patrones de operación normal.
    * Se calculó la distancia de cada punto al centroide de su cluster más cercano para generar una **puntuación de anomalía**.
    * Las lecturas con la mayor puntuación de anomalía fueron identificadas como los puntos que más se desvían del comportamiento estándar.

---

## 📊 Resultados

El modelo agrupó exitosamente los datos en 6 clusters distintos, cada uno representando un "perfil" operativo diferente de la planta. El sistema final puede ordenar cualquier lectura de la planta por su "rareza", permitiendo a los ingenieros enfocarse en las desviaciones más significativas.

---

## 🚀 Puesta en Práctica

Este modelo podría ser la base de un sistema de monitoreo en tiempo real. Un script podría ejecutar este análisis cada minuto, y si una nueva lectura supera un umbral de "puntuación de anomalía", podría enviar automáticamente una alerta a la sala de control.

---

## 📁 Cómo Usar este Repositorio

1.  Ejecuta el notebook `1_Analisis_y_Preparacion.ipynb` para generar la base de datos y ver el proceso de transformación de datos con SQL.
2.  Ejecuta el notebook `2_Clustering_y_Anomalias.ipynb` para ver el análisis de K-Means, la selección de clusters y la detección final de anomalías.
