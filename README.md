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
   SELECT CONCAT_WS(' ', nombre, apellido1, apellido2) FROM empleado;
   +----------------------------------------------+
   | empleados
   +----------------------------------------------+
   | Aarón Rivero Gómez                           |
   | Adela Salas Díaz                             |
   | Adolfo Rubio Flores                          |
   | Adrián Suárez                                |
   | Marcos Loyola Méndez                         |
   | María Santana Moreno                         |
   | Pilar Ruiz                                   |
   | Pepe Ruiz Santana                            |
   | Juan Gómez López                             |
   | Diego Flores Salas                           |
   | Marta Herrera Gil                            |
   | Irene Salas Flores                           |
   | Juan Antonio Sáez Guerrero                   |
   +----------------------------------------------+
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
    SELECT
        codigo,
        REGEXP_REPLACE(nit, '[^0-9]+', '') AS numeros,
        REGEXP_REPLACE(nit, '[^A-Za-z]+', '') AS letras
    FROM
        empleado;
        +--------+----------+--------+
    | codigo | numeros  | letras |
    +--------+----------+--------+
    |      1 | 32481596 | F      |
    |      2 | 5575632  | YD     |
    |      3 | 6970642  | RB     |
    |      4 | 77705545 | E      |
    |      5 | 17087203 | C      |
    |      6 | 38382980 | M      |
    |      7 | 80576669 | X      |
    |      8 | 71651431 | Z      |
    |      9 | 56399183 | D      |
    |     10 | 46384486 | H      |
    |     11 | 67389283 | A      |
    |     12 | 41234836 | R      |
    |     13 | 82635162 | B      |
    +--------+----------+--------+
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
  +-------------+-----------+--------+-----------+-----------+-----------------+------------------+-------------+--------+
  | id_empleado | nit       | nombre | apellido1 | apellido2 | id_departamento | departamento     | presupuesto | gasto  |
  +-------------+-----------+--------+-----------+-----------+-----------------+------------------+-------------+--------+
  |           1 | 32481596F | Aarón  | Rivero    | Gómez     |               1 | Desarrollo       |      120000 |   6000 |
  |           6 | 38382980M | María  | Santana   | Moreno    |               1 | Desarrollo       |      120000 |   6000 |
  |          11 | 67389283A | Marta  | Herrera   | Gil       |               1 | Desarrollo       |      120000 |   6000 |
  |           2 | Y5575632D | Adela  | Salas     | Díaz      |               2 | Sistemas         |      150000 |  21000 |
  |           7 | 80576669X | Pilar  | Ruiz      | NULL      |               2 | Sistemas         |      150000 |  21000 |
  |           9 | 56399183D | Juan   | Gómez     | López     |               2 | Sistemas         |      150000 |  21000 |
  |           3 | R6970642B | Adolfo | Rubio     | Flores    |               3 | Recursos Humanos |      280000 |  25000 |
  |           8 | 71651431Z | Pepe   | Ruiz      | Santana   |               3 | Recursos Humanos |      280000 |  25000 |
  |           4 | 77705545E | Adrián | Suárez    | NULL      |               4 | Contabilidad     |      110000 |   3000 |
  |           5 | 17087203C | Marcos | Loyola    | Méndez    |               5 | I+D              |      375000 | 380000 |
  |          10 | 46384486H | Diego  | Flores    | Salas     |               5 | I+D              |      375000 | 380000 |
  +-------------+-----------+--------+-----------+-----------+-----------------+------------------+-------------+--------+
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
  +-------------+-----------+--------+-----------+-----------+-----------------+------------------+-------------+--------+
  | id_empleado | nit       | nombre | apellido1 | apellido2 | id_departamento | departamento     | presupuesto | gasto  |
  +-------------+-----------+--------+-----------+-----------+-----------------+------------------+-------------+--------+
  |           4 | 77705545E | Adrián | Suárez    | NULL      |               4 | Contabilidad     |      110000 |   3000 |
  |          11 | 67389283A | Marta  | Herrera   | Gil       |               1 | Desarrollo       |      120000 |   6000 |
  |           1 | 32481596F | Aarón  | Rivero    | Gómez     |               1 | Desarrollo       |      120000 |   6000 |
  |           6 | 38382980M | María  | Santana   | Moreno    |               1 | Desarrollo       |      120000 |   6000 |
  |          10 | 46384486H | Diego  | Flores    | Salas     |               5 | I+D              |      375000 | 380000 |
  |           5 | 17087203C | Marcos | Loyola    | Méndez    |               5 | I+D              |      375000 | 380000 |
  |           3 | R6970642B | Adolfo | Rubio     | Flores    |               3 | Recursos Humanos |      280000 |  25000 |
  |           8 | 71651431Z | Pepe   | Ruiz      | Santana   |               3 | Recursos Humanos |      280000 |  25000 |
  |           9 | 56399183D | Juan   | Gómez     | López     |               2 | Sistemas         |      150000 |  21000 |
  |           7 | 80576669X | Pilar  | Ruiz      | NULL      |               2 | Sistemas         |      150000 |  21000 |
  |           2 | Y5575632D | Adela  | Salas     | Díaz      |               2 | Sistemas         |      150000 |  21000 |
  +-------------+-----------+--------+-----------+-----------+-----------------+------------------+-------------+--------+
  ```

3. Devuelve un listado con el identificador y el nombre del departamento,
    solamente de aquellos departamentos que tienen empleados.

  ```sql
  SELECT DISTINCT d.codigo, d.nombre
  FROM departamento AS d, empleado AS e
  WHERE d.codigo = e.codigo_departamento;
  +--------+------------------+
  | codigo | nombre           |
  +--------+------------------+
  |      1 | Desarrollo       |
  |      2 | Sistemas         |
  |      3 | Recursos Humanos |
  |      4 | Contabilidad     |
  |      5 | I+D              |
  +--------+------------------+
  ```

4. Devuelve un listado con el identificador, el nombre del departamento y el
    valor del presupuesto actual del que dispone, solamente de aquellos
    departamentos que tienen empleados. El valor del presupuesto actual lo
    puede calcular restando al valor del presupuesto inicial
    (columna presupuesto) el valor de los gastos que ha generado
    (columna gastos).

```sql
SELECT DISTINCT d.codigo, d.nombre, d.presupuesto - d.gasto AS 'presupuesto_actual'
FROM empleado AS e, departamento AS d
WHERE e.codigo_departamento = d.codigo;
+--------+------------------+--------------------+
| codigo | nombre           | presupuesto_actual |
+--------+------------------+--------------------+
|      1 | Desarrollo       |             114000 |
|      2 | Sistemas         |             129000 |
|      3 | Recursos Humanos |             255000 |
|      4 | Contabilidad     |             107000 |
|      5 | I+D              |              -5000 |
+--------+------------------+--------------------+
```

5. Devuelve el nombre del departamento donde trabaja el empleado que tiene
     el nif 38382980M.

     ```sql
     SELECT d.nombre
     FROM departamento AS d, empleado AS e
     WHERE e.codigo_departamento = d.codigo AND e.nif = '38382980M';
     +------------+
     | nombre     |
     +------------+
     | Desarrollo |
     +------------+
     ```

6. Devuelve el nombre del departamento donde trabaja el empleado Pepe Ruiz
     Santana.

     ```sql
     SELECT d.nombre
     FROM departamento AS d, empleado AS e
     WHERE e.codigo_departamento = d.codigo AND e.nombre = 'Pepe' AND e.apellido1 = 'Ruiz' AND e.apellido2 = 'Santana';
     +------------------+
     | nombre           |
     +------------------+
     | Recursos Humanos |
     +------------------+
     ```

7. Devuelve un listado con los datos de los empleados que trabajan en el
     departamento de I+D. Ordena el resultado alfabéticamente.

     ```sql
     SELECT e.codigo, e.nit, e.nombre, e.apellido1, e.apellido2, e.codigo_departamento 
     FROM empleado AS e, departamento AS d
     WHERE e.codigo_departamento = d.codigo AND d.nombre = 'I+D'
     ORDER BY e.nombre ASC;
     +--------+-----------+--------+-----------+-----------+---------------------+
     | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento |
     +--------+-----------+--------+-----------+-----------+---------------------+
     |     10 | 46384486H | Diego  | Flores    | Salas     |                   5 |
     |      5 | 17087203C | Marcos | Loyola    | Méndez    |                   5 |
     +--------+-----------+--------+-----------+-----------+---------------------+
     ```

8. Devuelve un listado con los datos de los empleados que trabajan en el
     departamento de Sistemas, Contabilidad o I+D. Ordena el resultado
       alfabéticamente.

     ```sql
     SELECT e.codigo, e.nit, e.nombre, e.apellido1, e.apellido2, e.codigo_departamento 
     FROM empleado AS e, departamento AS d
     WHERE e.codigo_departamento = d.codigo AND d.nombre IN ('Sistemas', 'Contabilidad', 'I+D')
     ORDER BY e.nombre ASC;
     +--------+-----------+--------+-----------+-----------+---------------------+
     | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento |
     +--------+-----------+--------+-----------+-----------+---------------------+
     |      2 | Y5575632D | Adela  | Salas     | Díaz      |                   2 |
     |      4 | 77705545E | Adrián | Suárez    | NULL      |                   4 |
     |     10 | 46384486H | Diego  | Flores    | Salas     |                   5 |
     |      9 | 56399183D | Juan   | Gómez     | López     |                   2 |
     |      5 | 17087203C | Marcos | Loyola    | Méndez    |                   5 |
     |      7 | 80576669X | Pilar  | Ruiz      | NULL      |                   2 |
     +--------+-----------+--------+-----------+-----------+---------------------+
     ```

9. Devuelve una lista con el nombre de los empleados que tienen los
     departamentos que no tienen un presupuesto entre 100000 y 200000 euros.

     ```sql
     SELECT e.nombre
     FROM empleado AS e, departamento AS d
     WHERE e.codigo_departamento = d.codigo AND d.presupuesto NOT BETWEEN 100000 AND 200000;
     +--------+
     | nombre |
     +--------+
     | Adolfo |
     | Pepe   |
     | Marcos |
     | Diego  |
     +--------+
     ```

10. Devuelve un listado con el nombre de los departamentos donde existe
     algún empleado cuyo segundo apellido sea NULL. Tenga en cuenta que no
     debe mostrar nombres de departamentos que estén repetidos.

     ```sql
     SELECT d.nombre
     FROM empleado AS e, departamento AS d
     WHERE e.codigo_departamento = d.codigo AND e.apellido2  IS NULL;
     +--------------+
     | nombre       |
     +--------------+
     | Contabilidad |
     | Sistemas     |
     +--------------+
     ```

     

# Consultas multitabla (Composición externa)

### Resuelva todas las consultas utilizando las cláusulas LEFT JOIN y RIGHT JOIN.

1. Devuelve un listado con todos los empleados junto con los datos de los
    departamentos donde trabajan. Este listado también debe incluir los
    empleados que no tienen ningún departamento asociado.

  ```sql
  SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo AS 'id_codigo_departamento', d.nombre AS 'id_departamento', d.presupuesto, d.gasto
  FROM empleado AS e
  LEFT JOIN departamento AS d ON d.codigo = e.codigo_departamento;
  +-------------+-----------+--------------+-----------+-----------+------------------------+------------------+-------------+--------+
  | id_empleado | nit       | nombre       | apellido1 | apellido2 | id_codigo_departamento | id_departamento  | presupuesto | gasto  |
  +-------------+-----------+--------------+-----------+-----------+------------------------+------------------+-------------+--------+
  |           1 | 32481596F | Aarón        | Rivero    | Gómez     |                      1 | Desarrollo       |      120000 |   6000 |
  |           2 | Y5575632D | Adela        | Salas     | Díaz      |                      2 | Sistemas         |      150000 |  21000 |
  |           3 | R6970642B | Adolfo       | Rubio     | Flores    |                      3 | Recursos Humanos |      280000 |  25000 |
  |           4 | 77705545E | Adrián       | Suárez    | NULL      |                      4 | Contabilidad     |      110000 |   3000 |
  |           5 | 17087203C | Marcos       | Loyola    | Méndez    |                      5 | I+D              |      375000 | 380000 |
  |           6 | 38382980M | María        | Santana   | Moreno    |                      1 | Desarrollo       |      120000 |   6000 |
  |           7 | 80576669X | Pilar        | Ruiz      | NULL      |                      2 | Sistemas         |      150000 |  21000 |
  |           8 | 71651431Z | Pepe         | Ruiz      | Santana   |                      3 | Recursos Humanos |      280000 |  25000 |
  |           9 | 56399183D | Juan         | Gómez     | López     |                      2 | Sistemas         |      150000 |  21000 |
  |          10 | 46384486H | Diego        | Flores    | Salas     |                      5 | I+D              |      375000 | 380000 |
  |          11 | 67389283A | Marta        | Herrera   | Gil       |                      1 | Desarrollo       |      120000 |   6000 |
  |          12 | 41234836R | Irene        | Salas     | Flores    |                   NULL | NULL             |        NULL |   NULL |
  |          13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |                   NULL | NULL             |        NULL |   NULL |
  +-------------+-----------+--------------+-----------+-----------+------------------------+------------------+-------------+--------+
  ```

  

2. Devuelve un listado donde sólo aparezcan aquellos empleados que no
    tienen ningún departamento asociado.

  ```sql
  SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo
  FROM empleado AS e
  LEFT JOIN departamento AS d ON d.codigo = e.codigo_departamento
  WHERE e.codigo_departamento IS NULL;
  +-------------+-----------+--------------+-----------+-----------+--------+
  | id_empleado | nit       | nombre       | apellido1 | apellido2 | codigo |
  +-------------+-----------+--------------+-----------+-----------+--------+
  |          12 | 41234836R | Irene        | Salas     | Flores    |   NULL |
  |          13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |   NULL |
  +-------------+-----------+--------------+-----------+-----------+--------+
  ```

  

3. Devuelve un listado donde sólo aparezcan aquellos departamentos que no
    tienen ningún empleado asociado.

  ```sql
  SELECT d.codigo AS 'id_codigo_departamento', d.nombre AS 'id_departamento', d.presupuesto, d.gasto
  FROM departamento AS d
  LEFT JOIN empleado AS e ON d.codigo = e.codigo_departamento
  WHERE e.codigo_departamento IS NULL;
  +------------------------+-----------------+-------------+-------+
  | id_codigo_departamento | id_departamento | presupuesto | gasto |
  +------------------------+-----------------+-------------+-------+
  |                      6 | Proyectos       |           0 |     0 |
  |                      7 | Publicidad      |           0 |  1000 |
  +------------------------+-----------------+-------------+-------+
  ```

4. Devuelve un listado con todos los empleados junto con los datos de los
    departamentos donde trabajan. El listado debe incluir los empleados que no
    tienen ningún departamento asociado y los departamentos que no tienen
    ningún empleado asociado. Ordene el listado alfabéticamente por el
    nombre del departamento.

  ```sql
  
  ```

5. Devuelve un listado con los empleados que no tienen ningún departamento
    asociado y los departamentos que no tienen ningún empleado asociado.
  Ordene el listado alfabéticamente por el nombre del departamento.

```

```



## Consultas resumen

1. Calcula la suma del presupuesto de todos los departamentos.

   ```sql
   SELECT SUM(presupuesto) FROM departamento;
   +------------------+
   | SUM(presupuesto) |
   +------------------+
   |          1035000 |
   +------------------+
   ```

   

2. Calcula la media del presupuesto de todos los departamentos.

   ```sql
   SELECT AVG(presupuesto) FROM departamento;
   +--------------------+
   | AVG(presupuesto)   |
   +--------------------+
   | 147857.14285714287 |
   +--------------------+
   ```

3. Calcula el valor mínimo del presupuesto de todos los departamentos.

   ```sql
   SELECT MIN(presupuesto) FROM departamento;
   +------------------+
   | MIN(presupuesto) |
   +------------------+
   |                0 |
   +------------------+
   ```

   

4. Calcula el nombre del departamento y el presupuesto que tiene asignado,
  del departamento con menor presupuesto.

  ```sql
  SELECT nombre, presupuesto
  FROM departamento
  WHERE presupuesto = (
      SELECT MIN(presupuesto)
      FROM departamento
  )
  ORDER BY nombre ASC
  LIMIT 1;
  +-----------+-------------+
  | nombre    | presupuesto |
  +-----------+-------------+
  | Proyectos |           0 |
  +-----------+-------------+
  ```

  

5. Calcula el valor máximo del presupuesto de todos los departamentos.

   ```sql
   SELECT MAX(presupuesto) FROM departamento;
   +------------------+
   | MAX(presupuesto) |
   +------------------+
   |           375000 |
   +------------------+
   ```

   

6. Calcula el nombre del departamento y el presupuesto que tiene asignado,
  del departamento con mayor presupuesto.

  ```sql
  SELECT nombre, presupuesto
  FROM departamento
  WHERE presupuesto = (
      SELECT MAX(presupuesto)
      FROM departamento
  );
  +--------+-------------+
  | nombre | presupuesto |
  +--------+-------------+
  | I+D    |      375000 |
  +--------+-------------+
  ```

7. Calcula el número total de empleados que hay en la tabla empleado.

   ```
   SELECT COUNT(codigo) FROM empleado;
   +---------------+
   | COUNT(codigo) |
   +---------------+
   |            13 |
   +---------------+
   ```

8. Calcula el número de empleados que no tienen NULL en su segundo
  apellido.

  ```sql
  SELECT COUNT(apellido2) 
  FROM empleado
  WHERE apellido2 IS NOT NULL;
  +------------------+
  | COUNT(apellido2) |
  +------------------+
  |               11 |
  +------------------+
  ```

  

9. Calcula el número de empleados que hay en cada departamento. Tienes que
  devolver dos columnas, una con el nombre del departamento y otra con el
  número de empleados que tiene asignados.

  ```sql
  SELECT d.nombre, COUNT(e.nombre) AS 'numero_empleados'
  FROM departamento as d
  LEFT JOIN empleado AS e ON  d.codigo = e.codigo_departamento
  GROUP BY d.nombre;
  +------------------+------------------+
  | nombre           | numero_empleados |
  +------------------+------------------+
  | Desarrollo       |                3 |
  | Sistemas         |                3 |
  | Recursos Humanos |                2 |
  | Contabilidad     |                1 |
  | I+D              |                2 |
  | Proyectos        |                0 |
  | Publicidad       |                0 |
  +------------------+------------------+
  ```

  

10. Calcula el nombre de los departamentos que tienen más de 2 empleados. El
    resultado debe tener dos columnas, una con el nombre del departamento y
    otra con el número de empleados que tiene asignados.

    ```sql
    SELECT d.nombre, COUNT(e.nombre) AS 'numero_empleados'
    FROM departamento as d
    LEFT JOIN empleado AS e ON  d.codigo = e.codigo_departamento
    GROUP BY d.nombre
    HAVING COUNT(e.nombre) > 2;
    +------------+------------------+
    | nombre     | numero_empleados |
    +------------+------------------+
    | Desarrollo |                3 |
    | Sistemas   |                3 |
    +------------+------------------+
    ```

    

11. Calcula el número de empleados que trabajan en cada uno de los
    departamentos. El resultado de esta consulta también tiene que incluir
    aquellos departamentos que no tienen ningún empleado asociado.

    ```
    Es igual al punto 9
    ```

    

12. Calcula el número de empleados que trabajan en cada unos de los
    departamentos que tienen un presupuesto mayor a 200000 euros.

    ```sql
    SELECT d.nombre, COUNT(e.nombre) AS 'numero_empleados'
    FROM departamento AS d
    LEFT JOIN empleado AS e ON d.codigo = e.codigo_departamento
    WHERE d.presupuesto > 200000 
    GROUP BY d.nombre;
    +------------------+------------------+
    | nombre           | numero_empleados |
    +------------------+------------------+
    | Recursos Humanos |                2 |
    | I+D              |                2 |
    +------------------+------------------+
    ```

    