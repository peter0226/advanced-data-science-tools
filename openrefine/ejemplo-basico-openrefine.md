# 📘 Ejemplo: Limpieza de datasets con OpenRefine

Este ejemplo muestra el proceso de limpieza de un dataset con errores comunes utilizando OpenRefine.

---

## 🔹 1. Importar el dataset

1. Abrir OpenRefine.
2. Seleccionar **Create Project**.
3. Elegir el archivo `empleados_dirty.csv`.
4. Presionar **Next**.
5. Verificar la vista previa.
6. Presionar **Create Project**.

![Importar](01.png)

---

## 🔹 2. Exploración inicial

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

![Exploración](02.png)

---

## 🔹 3. Identificar duplicados

1. En **Employee.Name**:
   - Click en ▼
   - Seleccionar **Facet → Text facet**

2. Se observan nombres repetidos.

![Duplicados](03.png)

---

## 🔹 4. Agrupar valores similares (Clustering)

1. En la columna:
   - **Edit cells → Cluster and edit**

2. Presionar **Cluster**.

3. Revisar agrupaciones.

4. Unificar valores:
   - **Merge selected & re-cluster**
   - o **Merge selected & close**

![Clustering](05.png)

---

## 🔹 5. Eliminar espacios innecesarios

1. En columnas de texto:
   - **Edit cells → Common transforms → Trim leading and trailing whitespace**

![Trim](06.png)

---

## 🔹 6. Limpiar valores numéricos (Salary)

1. En **Salary**:
   - **Edit cells → Transform**

2. Usar:

------
value.replace("$","")
------

3. Luego:
   - **Edit cells → Common transforms → To number**

![Salary](07.png)

---

## 🔹 7. Estandarizar fechas

1. En **Hire.Date**:
   - **Edit cells → Transform**

2. Corregir separadores si es necesario:

------
value.replace(".","-")
------

------
value.replace("/","-")
------

3. Convertir a fecha:

👉 **Edit cells → Common transforms → To date**

![Fechas](11.png)

---

## 🔹 8. Identificar valores nulos

1. En cualquier columna:
   - **Facet → Customized facets → Facet by blank**

2. Analizar registros vacíos.

![Nulos](21.png)

---

## 🔹 9. Marcar registros (Flag rows)

1. Seleccionar filas relevantes.
2. Aplicar:
   - **Edit rows → Flag rows**

3. Filtrar por:
   - **Facet → Facet by flag**

![Flag](22.png)

---

## 🔹 10. Filtrar registros marcados

1. En el panel izquierdo:
   - Seleccionar **true**

2. Se muestran solo los registros marcados.

![Filtro Flag](23.png)

---

## 🔹 11. Eliminar registros con menor calidad

1. Identificar registros incompletos.
2. Aplicar:

👉 **Edit rows → Remove matching rows**

![Eliminar](24.png)

---

## 🔹 12. Eliminar duplicados automáticamente

1. Ir a:
   - **Edit rows → Remove duplicate rows**

2. Seleccionar columnas clave:
   - Employee.Name
   - Department
   - City

3. Presionar **OK**

![Remove duplicates](25.png)

---

## 🔹 13. Validar resultados

Verificar:

- nombres únicos
- valores consistentes
- ausencia de duplicados

![Validación](26.png)

---

## 🔹 14. Estandarizar valores de texto

Ejemplo en columna City:

1. **Edit cells → Transform**

------
value.replace("Mexico City","CDMX")
------

![City](27.png)

---

## 🔹 15. Resultado final

El dataset queda:

- sin duplicados
- sin valores inconsistentes
- con formato uniforme
- listo para análisis

![Resultado](30.png)

---

## 🎯 Conclusión

El proceso de limpieza de datos permitió corregir errores comunes como duplicados, valores nulos, inconsistencias en texto y formatos incorrectos. 

Se aplicaron técnicas de exploración, transformación y validación para obtener un dataset estructurado, consistente y adecuado para análisis posteriores.
