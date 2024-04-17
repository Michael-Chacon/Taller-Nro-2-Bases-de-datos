# Taller Nro 2 Bases de datos

## Consultas sobre una tabla

1. Lista el primer apellido de todos los empleados.

   ```sql
   SELECT apellido1 FROM empleado;
   ```

   

2. Lista el primer apellido de los empleados eliminando los apellidos que estén
  repetidos.

  ```SQL
  SELECT DISTINCT(apellido1) FROM empleado;
  ```

  

3. Lista todas las columnas de la tabla empleado.

   ```sql
   
   SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
   FROM empleado;
   ```

   

4. Lista el nombre y los apellidos de todos los empleados.

   ```sql
   SELECT nombre, apellido1, apellido2 FROM empleado;
   ```

5. Lista el identificador de los departamentos de los empleados que aparecen
  en la tabla empleado.

  ```sql
  SELECT codigo_departamento FROM empleado;
  ```

6. Lista el identificador de los departamentos de los empleados que aparecen
  en la tabla empleado, eliminando los identificadores que aparecen repetidos.

  ```SQL
  SELECT DISTINCT codigo_departamento FROM empleado;
  ```

7. Lista el nombre y apellidos de los empleados en una única columna.

   ```sql
   SELECT CONCAT(nombre, ' ', apellido1, ' ', apellido2) FROM empleado;
   ```

8. Lista el nombre y apellidos de los empleados en una única columna,
  convirtiendo todos los caracteres en mayúscula.

  ```SQL
  SELECT UPPER(CONCAT(nombre, ' ', apellido1, ' ', apellido2)) FROM empleado;
  
  ```

9. Lista el nombre y apellidos de los empleados en una única columna,
  convirtiendo todos los caracteres en minúscula.

  ```SQL
  SELECT LOWER(CONCAT(nombre, ' ', apellido1, ' ', apellido2)) FROM empleado;
  ```

10. Lista el identificador de los empleados junto al nif, pero el nif deberá
    aparecer en dos columnas, una mostrará únicamente los dígitos del nif y la
    otra la letra.

    ```sql
    NO SE COMO HACER ESTE PUNTO
    ```

11. Lista el nombre de cada departamento y el valor del presupuesto actual del
    que dispone. Para calcular este dato tendrá que restar al valor del
    presupuesto inicial (columna presupuesto) los gastos que se han generado
    (columna gastos). Tenga en cuenta que en algunos casos pueden existir
    valores negativos. Utilice un alias apropiado para la nueva columna columna
    que está calculando.

    ```sql
    SELECT nombre, presupuesto - gasto AS 'Presupuesto disponible'
    FROM departamento;
    ```

    

12. Lista el nombre de los departamentos y el valor del presupuesto actual
    ordenado de forma ascendente.

    ```SQL
    SELECT nombre, presupuesto - gasto AS 'Presupuesto_actual'
    FROM departamento
    ORDER BY Presupuesto_actual ASC;
    ```

13. Lista el nombre de todos los departamentos ordenados de forma
    ascendente.

    ```sql
    SELECT nombre
    FROM departamento
    ORDER BY nombre ASC;
    ```

    

14. Lista el nombre de todos los departamentos ordenados de forma
    descendente.

    ```SQL
    SELECT nombre
    FROM departamento
    ORDER BY nombre DESC;
    ```

    

15. Lista los apellidos y el nombre de todos los empleados, ordenados de forma
    alfabética tendiendo en cuenta en primer lugar sus apellidos y luego su
    nombre.

    ```sql
    SELECT nombre, CONCAT(apellido1, ' ', apellido2) AS 'apellidos'
    FROM empleado
    ORDER BY apellidos ASC, nombre ASC;
    ```

16. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen mayor presupuesto.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    ORDER BY presupuesto DESC
    LIMIT 3;
    ```

17. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen menor presupuesto.

    ```SQL
    SELECT nombre, presupuesto
    FROM departamento
    ORDER BY presupuesto ASC
    LIMIT 3;
    ```

18. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen mayor gasto.

    ```sql
    fSELECT nombre, gasto
    FROM departamento
    ORDER BY presupuesto DESC
    LIMIT 2;
    ```

19. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen menor gasto.

    ```sql
    SELECT nombre, gasto
    FROM departamento
    ORDER BY presupuesto ASC
    LIMIT 2;
    ```

20. Devuelve una lista con 5 filas a partir de la tercera fila de la tabla empleado. La
    tercera fila se debe incluir en la respuesta. La respuesta debe incluir todas las
    columnas de la tabla empleado.

    ```SQL
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    LIMIT 5 OFFSET 2; 
    ```

21. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto mayor o igual a 150000 euros.

    ```SQL
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto >= 150000;
    ```

22. Devuelve una lista con el nombre de los departamentos y el gasto, de
    aquellos que tienen menos de 5000 euros de gastos.

    ```sql
    SELECT nombre, gasto
    FROM departamento
    WHERE presupuesto < 5000;
    ```

23. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto entre 100000 y 200000 euros. Sin
    utilizar el operador BETWEEN.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto > 100000  AND presupuesto < 200000;
    ```

24. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Sin utilizar el operador BETWEEN.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto < 100000 OR presupuesto > 200000;
    ```

25. Devuelve una lista con el nombre de los departamentos que tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto BETWEEN 100000 AND 200000;
    ```

26. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

    ```SQL
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto NOT BETWEEN 100000  AND 200000;
    ```

27. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean mayores
    que el presupuesto del que disponen.

    ```sql
    SELECT nombre, presupuesto, gasto
    FROM departamento
    WHERE gasto > presupuesto;
    ```

28. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean menores
    que el presupuesto del que disponen.

    ```sql
    SELECT nombre, gasto, presupuesto
    FROM departamento
    WHERE presupuesto > gasto;
    ```

29. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean iguales al
    presupuesto del que disponen.

    ```SQL
    SELECT nombre, gasto, presupuesto
    FROM departamento
    WHERE presupuesto = gasto;
    ```

30. Lista todos los datos de los empleados cuyo segundo apellido sea NULL.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 IS NULL;
    ```

31. Lista todos los datos de los empleados cuyo segundo apellido no sea NULL.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 IS NOT NULL;
    ```

32. Lista todos los datos de los empleados cuyo segundo apellido sea López.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 = 'López';
    ```

33. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Sin utilizar el operador IN.

    ```
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 = 'López' OR apellido2 = 'Moreno';
    ```

    

34. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Utilizando el operador IN.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 IN ('López', 'Moreno');
    ```

35. Lista los nombres, apellidos y nif de los empleados que trabajan en el
    departamento 3.

    ```sql
    SELECT nombre,apellido1, apellido2, nit
    FROM empleado
    WHERE codigo_departamento = 3;
    ```

36. Lista los nombres, apellidos y nif de los empleados que trabajan en los
    departamentos 2, 4 o 5.

    ```sql
    SELECT nombre,apellido1, apellido2, nit
    FROM empleado
    WHERE codigo_departamento IN (2,4,5);
    ```

    

## Consultas multitabla (Composición interna)

### Resuelva todas las consultas utilizando la sintaxis de SQL1 y SQL2.

1. Devuelve un listado con los empleados y los datos de los departamentos
  donde trabaja cada uno.

  ```sql
  SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo AS 'id_departamento', d.nombre AS 'departamento', d.presupuesto, d.gasto
  FROM empleado AS e, departamento AS d
  WHERE e.codigo_departamento = d.codigo;
  ```

2. Devuelve un listado con los empleados y los datos de los departamentos
  donde trabaja cada uno. Ordena el resultado, en primer lugar por el nombre
  del departamento (en orden alfabético) y en segundo lugar por los apellidos
  y el nombre de los empleados.

  ```sql
  SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo AS 'id_departamento', d.nombre AS 'departamento', d.presupuesto, d.gasto
  FROM empleado AS e, departamento AS d
  WHERE e.codigo_departamento = d.codigo
  ORDER BY d.nombre ASC, e.apellido1 ASC, e.apellido2 ASC, e.nombre ASC;
  ```

3. Devuelve un listado con el identificador y el nombre del departamento,
  solamente de aquellos departamentos que tienen empleados.

  ```sql
  SELECT DISTINCT d.codigo, d.nombre
  FROM departamento AS d, empleado AS e
  WHERE d.codigo = e.codigo_departamento;
  ```

4. Devuelve un listado con el identificador, el nombre del departamento y el
  valor del presupuesto actual del que dispone, solamente de aquellos
  departamentos que tienen empleados. El valor del presupuesto actual lo
  puede calcular restando al valor del presupuesto inicial
  (columna presupuesto) el valor de los gastos que ha generado
  (columna gastos).

  ```sql
  
  ```

5. Devuelve el nombre del departamento donde trabaja el empleado que tiene
  el nif 38382980M.

6. Devuelve el nombre del departamento donde trabaja el empleado Pepe Ruiz
  Santana.

7. Devuelve un listado con los datos de los empleados que trabajan en el
  departamento de I+D. Ordena el resultado alfabéticamente.

8. Devuelve un listado con los datos de los empleados que trabajan en el
  departamento de Sistemas, Contabilidad o I+D. Ordena el resultado
  alfabéticamente.

9. Devuelve una lista con el nombre de los empleados que tienen los
  departamentos que no tienen un presupuesto entre 100000 y 200000 euros.

10. Devuelve un listado con el nombre de los departamentos donde existe
    algún empleado cuyo segundo apellido sea NULL. Tenga en cuenta que no
    debe mostrar nombres de departamentos que estén repetidos.