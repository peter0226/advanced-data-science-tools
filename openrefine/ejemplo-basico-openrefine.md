# Ejemplo: Limpieza de datasets con OpenRefine

Este ejemplo muestra el proceso de limpieza de un dataset con errores comunes utilizando OpenRefine.


## 1. Importar el dataset

1. Abrir OpenRefine.
2. Seleccionar **Create Project**.
3. Elegir el archivo `empleados_dirty.csv`.
4. Presionar **Next**.
5. Verificar la vista previa.
6. Presionar **Create Project**.

![Importar](imagenes/01.png)
![Importar](imagenes/02.png)
![Importar](imagenes/03.png)
![Clustering](imagenes/04.png)

## 2. Exploración inicial

Se revisan las columnas del dataset:

- Employee.ID
- Employee.Name
- Department
- Salary
- Hire.Date
- City

Se identifican problemas como:
- duplicados
- formatos inconsistentes
- valores nulos


## 3. Identificar duplicados

1. En **Employee.Name**:
   - Click en ▼
   - Seleccionar **Facet → Text facet**

2. Se observan nombres repetidos.

![Identificar](imagenes/05.png)
![Identificar](imagenes/06.png)


## 4. Agrupar valores similares (Clustering)

1. En la columna:
   - **Edit cells → Cluster and edit**

2. Presionar **Cluster**.

3. Revisar agrupaciones.

4. Unificar valores:
   - **Merge selected & re-cluster**
   - o **Merge selected & close**

![Agrupar](imagenes/07.png)
![Agrupar](imagenes/08.png)
![Agrupar](imagenes/09.png)
![Agrupar](imagenes/10.png)


## 5. Eliminar espacios innecesarios

1. En columnas de texto:
   - **Edit cells → Common transforms → Trim leading and trailing whitespace**

![Eliminar](imagenes/11.png)


## 6. Limpiar valores numéricos (Salary)

1. En **Salary**:
   - **Edit cells → Transform**

2. Usar:

```grel
value.replace("$","")
```

3. Luego:
   - **Edit cells → Common transforms → To number**

![Limpiar](imagenes/12.png)
![Limpiar](imagenes/13.png)


## 7. Estandarizar fechas

1. En **Hire.Date**:
   - **Edit cells → Transform**

2. Corregir separadores si es necesario:

```grel
value.replace(".","-")
```

```grel
value.replace("/","-")
```

3. Convertir a fecha:

**Edit cells → Common transforms → To date**

![Fechas](imagenes/14.png)
![Fechas](imagenes/15.png)
![Fechas](imagenes/16.png)
![Fechas](imagenes/17.png)
![Fechas](imagenes/18.png)


## 8. Identificar valores nulos

1. En cualquier columna:
   - **Facet → Customized facets → Facet by blank**

2. Analizar registros vacíos.

![Nulos](imagenes/19.png)
![Nulos](imagenes/20.png)


## 9. Marcar registros (Flag rows)

1. Seleccionar filas relevantes.
2. Aplicar:
   - **Edit rows → Flag rows**

3. Filtrar por:
   - **Facet → Facet by flag**
  
![Marcar](imagenes/21.png)
![Marcar](imagenes/22.png)


## 10. Filtrar registros marcados

1. En el panel izquierdo:
   - Seleccionar **true**

2. Se muestran solo los registros marcados.

![Filtrar](imagenes/23.png)


## 11. Eliminar registros con menor calidad

1. Identificar registros incompletos.
2. Aplicar:

**Edit rows → Remove matching rows**

![Eliminar](imagenes/24.png)
![Eliminar](imagenes/25.png)


## 12. Eliminar duplicados automáticamente

1. Ir a:
   - **Edit rows → Remove duplicate rows**

2. Seleccionar columnas clave:
   - Employee.Name
   - Department
   - City

3. Presionar **OK**

![Remove duplicates](imagenes/26.png)
![Remove duplicates](imagenes/27.png)


## 13. Validar resultados

Verificar:

- nombres únicos
- valores consistentes
- ausencia de duplicados

![Validación](imagenes/28.png)


## 14. Estandarizar valores de texto

Ejemplo en columna City:

1. **Edit cells → Transform**

```grel
value.replace("Mexico City","CDMX")
```

![City](imagenes/29.png)


## 15. Resultado final

El dataset queda:

- sin duplicados
- sin valores inconsistentes
- con formato uniforme
- listo para análisis

![Resultado](imagenes/30.png)


## Conclusión

El proceso de limpieza de datos permitió corregir errores comunes como duplicados, valores nulos, inconsistencias en texto y formatos incorrectos. 

Se aplicaron técnicas de exploración, transformación y validación para obtener un dataset estructurado, consistente y adecuado para análisis posteriores.
