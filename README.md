![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Laboratorio | Desafío Empresarial SQL: Ejercicio de Análisis de Datos

## Objetivo

Este desafío empresarial está diseñado para aplicar los conceptos de las cláusulas `GROUP BY` y `HAVING` en SQL. Trabajarás con un conjunto de datos del mundo real para realizar análisis de datos y extraer información significativa.

## Conjunto de Datos

Para este desafío, utilizarás el conjunto de datos **"NYC 311 Service Requests"**. Este conjunto de datos es un rico repositorio de solicitudes de servicio registradas por el servicio 311 de la ciudad de Nueva York desde 2010 hasta la actualidad.

Enlace del Conjunto de Datos: [Conjunto de Datos de Solicitudes de Servicio 311 de NYC](https://nycopendata.socrata.com/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)

## Tareas del Desafío

1. **Identificar los Principales Tipos de Quejas**
   - Consulta el conjunto de datos para encontrar los 5 tipos principales de quejas basados en el número de quejas registradas.
   - Utiliza `GROUP BY` para agrupar los datos por tipo de queja y `ORDER BY` para ordenar los resultados.

2. **Analizar Quejas por Distrito**
   - Calcula el número total de quejas para cada distrito.
   - Utiliza la cláusula `GROUP BY` para agrupar los datos por distrito.
  
   Code:
   USE DATABASE ironhack_database;
CREATE OR REPLACE SCHEMA ironhack_class;

CREATE OR REPLACE STAGE my_stage;

USE SCHEMA ironhack_database.ironhack_class;

DESCRIBE TABLE complains


-- Identificar los Principales Tipos de Quejas
SELECT COMPLAINT_TYPE, COUNT(*) AS total_complaints
FROM complains
GROUP BY COMPLAINT_TYPE
ORDER BY total_complaints DESC;


-- Analizar Quejas por Distrito
SELECT BOROUGH, COUNT(*) AS How_Many FROM complains
GROUP BY BOROUGH
ORDER BY How_Many DESC;

-- Filtrar Tipos de Quejas de Alto Volumen
SELECT *
FROM complains
HAVING COMPLAINT_TYPE LIKE 'Noise%';

-- Comparación de Distritos para un Tipo Específico de Queja
SELECT BOROUGH, COUNT(*) AS Complains_about_Fireworks
FROM complains
WHERE COMPLAINT_TYPE LIKE 'Illegal Fireworks'
GROUP BY BOROUGH
ORDER BY Complains_about_Fireworks DESC

4. **Filtrar Tipos de Quejas de Alto Volumen**
   - Utiliza la cláusula `HAVING` para filtrar tipos de quejas que tienen más de 1000 quejas registradas.
   - Muestra el tipo de queja y el recuento de quejas.

5. **Comparación de Distritos para un Tipo Específico de Queja**
   - Elige un tipo particular de queja.
   - Compara el número de dichas quejas en cada distrito.

## Entregables

- Consultas SQL para cada tarea.
- Breve análisis de los resultados obtenidos de cada consulta.

## Consejos

- Presta atención a los tipos de datos y la estructura del conjunto de datos.
- Utiliza funciones agregadas como `COUNT()` eficazmente con `GROUP BY` y `HAVING`.
- Asegúrate de que tus consultas sean eficientes y estén bien estructuradas.

¡Buena suerte y diviértete con el desafío!
