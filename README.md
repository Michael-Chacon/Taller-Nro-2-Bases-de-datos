# Taller Nro 2 Bases de datos

## Consultas sobre una tabla

1. Lista el primer apellido de todos los empleados.

   ```sql
   SELECT apellido1 FROM empleado;
   +-----------+
   | apellido1 |
   +-----------+
   | Rivero    |
   | Salas     |
   | Rubio     |
   | Suárez    |
   | Loyola    |
   | Santana   |
   | Ruiz      |
   | Ruiz      |
   | Gómez     |
   | Flores    |
   | Herrera   |
   | Salas     |
   | Sáez      |
   +-----------+
   ```

2. Lista el primer apellido de los empleados eliminando los apellidos que estén
    repetidos.

  ```SQL
  SELECT DISTINCT(apellido1) FROM empleado;
  +-----------+
  | apellido1 |
  +-----------+
  | Rivero    |
  | Salas     |
  | Rubio     |
  | Suárez    |
  | Loyola    |
  | Santana   |
  | Ruiz      |
  | Gómez     |
  | Flores    |
  | Herrera   |
  | Sáez      |
  +-----------+
  ```

3. Lista todas las columnas de la tabla empleado.

   ```sql
   
   SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
   FROM empleado;
   +--------+-----------+--------------+-----------+-----------+---------------------+
   | codigo | nit       | nombre       | apellido1 | apellido2 | codigo_departamento |
   +--------+-----------+--------------+-----------+-----------+---------------------+
   |      1 | 32481596F | Aarón        | Rivero    | Gómez     |                   1 |
   |      2 | Y5575632D | Adela        | Salas     | Díaz      |                   2 |
   |      3 | R6970642B | Adolfo       | Rubio     | Flores    |                   3 |
   |      4 | 77705545E | Adrián       | Suárez    | NULL      |                   4 |
   |      5 | 17087203C | Marcos       | Loyola    | Méndez    |                   5 |
   |      6 | 38382980M | María        | Santana   | Moreno    |                   1 |
   |      7 | 80576669X | Pilar        | Ruiz      | NULL      |                   2 |
   |      8 | 71651431Z | Pepe         | Ruiz      | Santana   |                   3 |
   |      9 | 56399183D | Juan         | Gómez     | López     |                   2 |
   |     10 | 46384486H | Diego        | Flores    | Salas     |                   5 |
   |     11 | 67389283A | Marta        | Herrera   | Gil       |                   1 |
   |     12 | 41234836R | Irene        | Salas     | Flores    |                NULL |
   |     13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |                NULL |
   +--------+-----------+--------------+-----------+-----------+---------------------+
   ```

   

4. Lista el nombre y los apellidos de todos los empleados.

   ```sql
   SELECT nombre, apellido1, apellido2 FROM empleado;
   +--------------+-----------+-----------+
   | nombre       | apellido1 | apellido2 |
   +--------------+-----------+-----------+
   | Aarón        | Rivero    | Gómez     |
   | Adela        | Salas     | Díaz      |
   | Adolfo       | Rubio     | Flores    |
   | Adrián       | Suárez    | NULL      |
   | Marcos       | Loyola    | Méndez    |
   | María        | Santana   | Moreno    |
   | Pilar        | Ruiz      | NULL      |
   | Pepe         | Ruiz      | Santana   |
   | Juan         | Gómez     | López     |
   | Diego        | Flores    | Salas     |
   | Marta        | Herrera   | Gil       |
   | Irene        | Salas     | Flores    |
   | Juan Antonio | Sáez      | Guerrero  |
   +
   ```

5. Lista el identificador de los departamentos de los empleados que aparecen
    en la tabla empleado.

  ```sql
  SELECT codigo_departamento FROM empleado;
  +---------------------+
  | codigo_departamento |
  +---------------------+
  |                NULL |
  |                NULL |
  |                   1 |
  |                   1 |
  |                   1 |
  |                   2 |
  |                   2 |
  |                   2 |
  |                   3 |
  |                   3 |
  |                   4 |
  |                   5 |
  |                   5 |
  +---------------------+
  ```

6. Lista el identificador de los departamentos de los empleados que aparecen
    en la tabla empleado, eliminando los identificadores que aparecen repetidos.

  ```SQL
  SELECT DISTINCT codigo_departamento FROM empleado;
  +---------------------+
  | codigo_departamento |
  +---------------------+
  |                NULL |
  |                   1 |
  |                   2 |
  |                   3 |
  |                   4 |
  |                   5 |
  +---------------------+
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
  SELECT UPPER(CONCAT_WS(' ', nombre, apellido1, apellido2)) FROM empleado;
  +-----------------------------------------------------+
  | UPPER(CONCAT_WS(' ', nombre, apellido1, apellido2)) |
  +-----------------------------------------------------+
  | AARÓN RIVERO GÓMEZ                                  |
  | ADELA SALAS DÍAZ                                    |
  | ADOLFO RUBIO FLORES                                 |
  | ADRIÁN SUÁREZ                                       |
  | MARCOS LOYOLA MÉNDEZ                                |
  | MARÍA SANTANA MORENO                                |
  | PILAR RUIZ                                          |
  | PEPE RUIZ SANTANA                                   |
  | JUAN GÓMEZ LÓPEZ                                    |
  | DIEGO FLORES SALAS                                  |
  | MARTA HERRERA GIL                                   |
  | IRENE SALAS FLORES                                  |
  | JUAN ANTONIO SÁEZ GUERRERO                          |
  +-----------------------------------------------------+
  ```

9. Lista el nombre y apellidos de los empleados en una única columna,
    convirtiendo todos los caracteres en minúscula.

  ```SQL
  SELECT LOWER(CONCAT_WS(' ', nombre, apellido1, apellido2)) FROM empleado;
  +-----------------------------------------------------+
  | LOWER(CONCAT_WS(' ', nombre, apellido1, apellido2)) |
  +-----------------------------------------------------+
  | aarón rivero gómez                                  |
  | adela salas díaz                                    |
  | adolfo rubio flores                                 |
  | adrián suárez                                       |
  | marcos loyola méndez                                |
  | maría santana moreno                                |
  | pilar ruiz                                          |
  | pepe ruiz santana                                   |
  | juan gómez lópez                                    |
  | diego flores salas                                  |
  | marta herrera gil                                   |
  | irene salas flores                                  |
  | juan antonio sáez guerrero                          |
  +-----------------------------------------------------+
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
    +------------------+------------------------+
    | nombre           | Presupuesto disponible |
    +------------------+------------------------+
    | Desarrollo       |                 114000 |
    | Sistemas         |                 129000 |
    | Recursos Humanos |                 255000 |
    | Contabilidad     |                 107000 |
    | I+D              |                  -5000 |
    | Proyectos        |                      0 |
    | Publicidad       |                  -1000 |
    +------------------+------------------------+
    ```
    
    
    
12. Lista el nombre de los departamentos y el valor del presupuesto actual
    ordenado de forma ascendente.

    ```SQL
    SELECT nombre, presupuesto - gasto AS 'Presupuesto_actual'
    FROM departamento
    ORDER BY Presupuesto_actual ASC;
    +------------------+--------------------+
    | nombre           | Presupuesto_actual |
    +------------------+--------------------+
    | I+D              |              -5000 |
    | Publicidad       |              -1000 |
    | Proyectos        |                  0 |
    | Contabilidad     |             107000 |
    | Desarrollo       |             114000 |
    | Sistemas         |             129000 |
    | Recursos Humanos |             255000 |
    +------------------+--------------------+
    ```
    
13. Lista el nombre de todos los departamentos ordenados de forma
    ascendente.

    ```sql
    SELECT nombre
    FROM departamento
    ORDER BY nombre ASC;
    +------------------+
    | nombre           |
    +------------------+
    | Contabilidad     |
    | Desarrollo       |
    | I+D              |
    | Proyectos        |
    | Publicidad       |
    | Recursos Humanos |
    | Sistemas         |
    +------------------+
    ```
    
    
    
14. Lista el nombre de todos los departamentos ordenados de forma
    descendente.

    ```SQL
    SELECT nombre
    FROM departamento
    ORDER BY nombre DESC;
    +------------------+
    | nombre           |
    +------------------+
    | Sistemas         |
    | Recursos Humanos |
    | Publicidad       |
    | Proyectos        |
    | I+D              |
    | Desarrollo       |
    | Contabilidad     |
    +------------------+
    ```
    
    
    
15. Lista los apellidos y el nombre de todos los empleados, ordenados de forma
    alfabética tendiendo en cuenta en primer lugar sus apellidos y luego su
    nombre.

    ```sql
    SELECT nombre, CONCAT_WS(' ', apellido1, apellido2) AS 'apellidos'
    FROM empleado
    ORDER BY apellidos ASC, nombre ASC;
    +--------------+----------------+
    | nombre       | apellidos      |
    +--------------+----------------+
    | Diego        | Flores Salas   |
    | Juan         | Gómez López    |
    | Marta        | Herrera Gil    |
    | Marcos       | Loyola Méndez  |
    | Aarón        | Rivero Gómez   |
    | Adolfo       | Rubio Flores   |
    | Pilar        | Ruiz           |
    | Pepe         | Ruiz Santana   |
    | Juan Antonio | Sáez Guerrero  |
    | Adela        | Salas Díaz     |
    | Irene        | Salas Flores   |
    | María        | Santana Moreno |
    | Adrián       | Suárez         |
    +--------------+----------------+
    ```
    
16. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen mayor presupuesto.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    ORDER BY presupuesto DESC
    LIMIT 3;
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | I+D              |      375000 |
    | Recursos Humanos |      280000 |
    | Sistemas         |      150000 |
    +------------------+-------------+
    ```
    
17. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen menor presupuesto.

    ```SQL
    SELECT nombre, presupuesto
    FROM departamento
    ORDER BY presupuesto ASC
    LIMIT 3;
    +--------------+-------------+
    | nombre       | presupuesto |
    +--------------+-------------+
    | Proyectos    |           0 |
    | Publicidad   |           0 |
    | Contabilidad |      110000 |
    +--------------+-------------+
    ```
    
18. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen mayor gasto.

    ```sql
    SELECT nombre, gasto
    FROM departamento
    ORDER BY presupuesto DESC
    LIMIT 2;
    +------------------+--------+
    | nombre           | gasto  |
    +------------------+--------+
    | I+D              | 380000 |
    | Recursos Humanos |  25000 |
    +------------------+--------+
    ```
    
19. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen menor gasto.

    ```sql
    SELECT nombre, gasto
    FROM departamento
    ORDER BY presupuesto ASC
    LIMIT 2;
    +------------+-------+
    | nombre     | gasto |
    +------------+-------+
    | Publicidad |  1000 |
    | Proyectos  |     0 |
    +------------+-------+
    ```
    
20. Devuelve una lista con 5 filas a partir de la tercera fila de la tabla empleado. La
    tercera fila se debe incluir en la respuesta. La respuesta debe incluir todas las
    columnas de la tabla empleado.

    ```SQL
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    LIMIT 5 OFFSET 2; 
    +--------+-----------+--------+-----------+-----------+---------------------+
    | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento |
    +--------+-----------+--------+-----------+-----------+---------------------+
    |      3 | R6970642B | Adolfo | Rubio     | Flores    |                   3 |
    |      4 | 77705545E | Adrián | Suárez    | NULL      |                   4 |
    |      5 | 17087203C | Marcos | Loyola    | Méndez    |                   5 |
    |      6 | 38382980M | María  | Santana   | Moreno    |                   1 |
    |      7 | 80576669X | Pilar  | Ruiz      | NULL      |                   2 |
    +--------+-----------+--------+-----------+-----------+---------------------+
    ```
    
21. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto mayor o igual a 150000 euros.

    ```SQL
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto >= 150000;
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | Sistemas         |      150000 |
    | Recursos Humanos |      280000 |
    | I+D              |      375000 |
    +------------------+-------------+
    ```
    
22. Devuelve una lista con el nombre de los departamentos y el gasto, de
    aquellos que tienen menos de 5000 euros de gastos.

    ```sql
    SELECT nombre, gasto
    FROM departamento
    WHERE presupuesto < 5000;
    +------------+-------+
    | nombre     | gasto |
    +------------+-------+
    | Proyectos  |     0 |
    | Publicidad |  1000 |
    +------------+-------+
    ```
    
23. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto entre 100000 y 200000 euros. Sin
    utilizar el operador BETWEEN.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto > 100000  AND presupuesto < 200000;
    +--------------+-------------+
    | nombre       | presupuesto |
    +--------------+-------------+
    | Desarrollo   |      120000 |
    | Sistemas     |      150000 |
    | Contabilidad |      110000 |
    +--------------+-------------+
    ```
    
24. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Sin utilizar el operador BETWEEN.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto < 100000 OR presupuesto > 200000;
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | Recursos Humanos |      280000 |
    | I+D              |      375000 |
    | Proyectos        |           0 |
    | Publicidad       |           0 |
    +------------------+-------------+
    ```
    
25. Devuelve una lista con el nombre de los departamentos que tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

    ```sql
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto BETWEEN 100000 AND 200000;
    +--------------+-------------+
    | nombre       | presupuesto |
    +--------------+-------------+
    | Desarrollo   |      120000 |
    | Sistemas     |      150000 |
    | Contabilidad |      110000 |
    +--------------+-------------+
    ```
    
26. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

    ```SQL
    SELECT nombre, presupuesto
    FROM departamento
    WHERE presupuesto NOT BETWEEN 100000  AND 200000;
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | Recursos Humanos |      280000 |
    | I+D              |      375000 |
    | Proyectos        |           0 |
    | Publicidad       |           0 |
    +------------------+-------------+
    ```
    
27. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean mayores
    que el presupuesto del que disponen.

    ```sql
    SELECT nombre, presupuesto, gasto
    FROM departamento
    WHERE gasto > presupuesto;
    +------------+-------------+--------+
    | nombre     | presupuesto | gasto  |
    +------------+-------------+--------+
    | I+D        |      375000 | 380000 |
    | Publicidad |           0 |   1000 |
    +------------+-------------+--------+
    ```
    
28. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean menores
    que el presupuesto del que disponen.

    ```sql
    SELECT nombre, gasto, presupuesto
    FROM departamento
    WHERE presupuesto > gasto;
    +------------------+-------+-------------+
    | nombre           | gasto | presupuesto |
    +------------------+-------+-------------+
    | Desarrollo       |  6000 |      120000 |
    | Sistemas         | 21000 |      150000 |
    | Recursos Humanos | 25000 |      280000 |
    | Contabilidad     |  3000 |      110000 |
    +------------------+-------+-------------+
    ```
    
29. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean iguales al
    presupuesto del que disponen.

    ```SQL
    SELECT nombre, gasto, presupuesto
    FROM departamento
    WHERE presupuesto = gasto;
    +-----------+-------+-------------+
    | nombre    | gasto | presupuesto |
    +-----------+-------+-------------+
    | Proyectos |     0 |           0 |
    +-----------+-------+-------------+
    ```
    
30. Lista todos los datos de los empleados cuyo segundo apellido sea NULL.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 IS NULL;
    +--------+-----------+--------+-----------+-----------+---------------------+
    | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento |
    +--------+-----------+--------+-----------+-----------+---------------------+
    |      4 | 77705545E | Adrián | Suárez    | NULL      |                   4 |
    |      7 | 80576669X | Pilar  | Ruiz      | NULL      |                   2 |
    +--------+-----------+--------+-----------+-----------+---------------------+
    ```

31. Lista todos los datos de los empleados cuyo segundo apellido no sea NULL.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 IS NOT NULL;
    +--------+-----------+--------------+-----------+-----------+---------------------+
    | codigo | nit       | nombre       | apellido1 | apellido2 | codigo_departamento |
    +--------+-----------+--------------+-----------+-----------+---------------------+
    |      1 | 32481596F | Aarón        | Rivero    | Gómez     |                   1 |
    |      2 | Y5575632D | Adela        | Salas     | Díaz      |                   2 |
    |      3 | R6970642B | Adolfo       | Rubio     | Flores    |                   3 |
    |      5 | 17087203C | Marcos       | Loyola    | Méndez    |                   5 |
    |      6 | 38382980M | María        | Santana   | Moreno    |                   1 |
    |      8 | 71651431Z | Pepe         | Ruiz      | Santana   |                   3 |
    |      9 | 56399183D | Juan         | Gómez     | López     |                   2 |
    |     10 | 46384486H | Diego        | Flores    | Salas     |                   5 |
    |     11 | 67389283A | Marta        | Herrera   | Gil       |                   1 |
    |     12 | 41234836R | Irene        | Salas     | Flores    |                NULL |
    |     13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |                NULL |
    +--------+-----------+--------------+-----------+-----------+---------------------+
    ```

32. Lista todos los datos de los empleados cuyo segundo apellido sea López.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 = 'López';
    +--------+-----------+--------+-----------+-----------+---------------------+
    | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento |
    +--------+-----------+--------+-----------+-----------+---------------------+
    |      9 | 56399183D | Juan   | Gómez     | López     |                   2 |
    +--------+-----------+--------+-----------+-----------+---------------------+
    ```

33. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Sin utilizar el operador IN.

    ```
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 = 'López' OR apellido2 = 'Moreno';
    +--------+-----------+--------+-----------+-----------+---------------------+
    | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento |
    +--------+-----------+--------+-----------+-----------+---------------------+
    |      6 | 38382980M | María  | Santana   | Moreno    |                   1 |
    |      9 | 56399183D | Juan   | Gómez     | López     |                   2 |
    +--------+-----------+--------+-----------+-----------+---------------------+
    ```
    
    
    
34. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Utilizando el operador IN.

    ```sql
    SELECT codigo, nit, nombre, apellido1, apellido2, codigo_departamento
    FROM empleado
    WHERE apellido2 IN ('López', 'Moreno');
    +--------+-----------+--------+-----------+-----------+---------------------+
    | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento |
    +--------+-----------+--------+-----------+-----------+---------------------+
    |      6 | 38382980M | María  | Santana   | Moreno    |                   1 |
    |      9 | 56399183D | Juan   | Gómez     | López     |                   2 |
    +--------+-----------+--------+-----------+-----------+---------------------+
    ```
    
35. Lista los nombres, apellidos y nif de los empleados que trabajan en el
    departamento 3.

    ```sql
    SELECT nombre,apellido1, apellido2, nit
    FROM empleado
    WHERE codigo_departamento = 3;
    +--------+-----------+-----------+-----------+
    | nombre | apellido1 | apellido2 | nit       |
    +--------+-----------+-----------+-----------+
    | Adolfo | Rubio     | Flores    | R6970642B |
    | Pepe   | Ruiz      | Santana   | 71651431Z |
    +--------+-----------+-----------+-----------+
    ```
    
36. Lista los nombres, apellidos y nif de los empleados que trabajan en los
    departamentos 2, 4 o 5.

    ```sql
    SELECT nombre,apellido1, apellido2, nit
    FROM empleado
    WHERE codigo_departamento IN (2,4,5);
    +--------+-----------+-----------+-----------+
    | nombre | apellido1 | apellido2 | nit       |
    +--------+-----------+-----------+-----------+
    | Adela  | Salas     | Díaz      | Y5575632D |
    | Pilar  | Ruiz      | NULL      | 80576669X |
    | Juan   | Gómez     | López     | 56399183D |
    | Adrián | Suárez    | NULL      | 77705545E |
    | Marcos | Loyola    | Méndez    | 17087203C |
    | Diego  | Flores    | Salas     | 46384486H |
    +--------+-----------+-----------+-----------+
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
  SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo AS 'cod_departamento', d.nombre AS 'nombre_departamento', d.presupuesto, d.gasto
  FROM departamento AS d
  LEFT JOIN empleado AS e ON d.codigo = e.codigo_departamento
  UNION
  SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo AS 'cod_departamento', d.nombre AS 'nombre_departamento', d.presupuesto, d.gasto
  FROM empleado AS e
  LEFT JOIN departamento AS d ON d.codigo = e.codigo_departamento
  ORDER BY nombre_departamento ASC;
  +-------------+-----------+--------------+-----------+-----------+------------------+---------------------+-------------+--------+
  | id_empleado | nit       | nombre       | apellido1 | apellido2 | cod_departamento | nombre_departamento | presupuesto | gasto  |
  +-------------+-----------+--------------+-----------+-----------+------------------+---------------------+-------------+--------+
  |          12 | 41234836R | Irene        | Salas     | Flores    |             NULL | NULL                |        NULL |   NULL |
  |          13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |             NULL | NULL                |        NULL |   NULL |
  |           4 | 77705545E | Adrián       | Suárez    | NULL      |                4 | Contabilidad        |      110000 |   3000 |
  |           1 | 32481596F | Aarón        | Rivero    | Gómez     |                1 | Desarrollo          |      120000 |   6000 |
  |           6 | 38382980M | María        | Santana   | Moreno    |                1 | Desarrollo          |      120000 |   6000 |
  |          11 | 67389283A | Marta        | Herrera   | Gil       |                1 | Desarrollo          |      120000 |   6000 |
  |           5 | 17087203C | Marcos       | Loyola    | Méndez    |                5 | I+D                 |      375000 | 380000 |
  |          10 | 46384486H | Diego        | Flores    | Salas     |                5 | I+D                 |      375000 | 380000 |
  |        NULL | NULL      | NULL         | NULL      | NULL      |                6 | Proyectos           |           0 |      0 |
  |        NULL | NULL      | NULL         | NULL      | NULL      |                7 | Publicidad          |           0 |   1000 |
  |           3 | R6970642B | Adolfo       | Rubio     | Flores    |                3 | Recursos Humanos    |      280000 |  25000 |
  |           8 | 71651431Z | Pepe         | Ruiz      | Santana   |                3 | Recursos Humanos    |      280000 |  25000 |
  |           2 | Y5575632D | Adela        | Salas     | Díaz      |                2 | Sistemas            |      150000 |  21000 |
  |           7 | 80576669X | Pilar        | Ruiz      | NULL      |                2 | Sistemas            |      150000 |  21000 |
  |           9 | 56399183D | Juan         | Gómez     | López     |                2 | Sistemas            |      150000 |  21000 |
  +-------------+-----------+--------------+-----------+-----------+------------------+---------------------+-------------+--------+
  ```

5. Devuelve un listado con los empleados que no tienen ningún departamento
    asociado y los departamentos que no tienen ningún empleado asociado.
    Ordene el listado alfabéticamente por el nombre del departamento.

```sql
SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo AS 'cod_departamento', d.nombre AS 'nombre_departamento', d.presupuesto, d.gasto
FROM departamento AS d
LEFT JOIN empleado AS e ON d.codigo = e.codigo_departamento
WHERE e.codigo_departamento  IS NULL
UNION
SELECT e.codigo AS 'id_empleado', e.nit, e.nombre, e.apellido1, e.apellido2, d.codigo AS 'cod_departamento', d.nombre AS 'nombre_departamento', d.presupuesto, d.gasto
FROM empleado AS e
LEFT JOIN departamento AS d ON d.codigo = e.codigo_departamento
WHERE e.codigo_departamento IS NULL
ORDER BY nombre_departamento ASC;
+-------------+-----------+--------------+-----------+-----------+------------------+---------------------+-------------+-------+
| id_empleado | nit       | nombre       | apellido1 | apellido2 | cod_departamento | nombre_departamento | presupuesto | gasto |
+-------------+-----------+--------------+-----------+-----------+------------------+---------------------+-------------+-------+
|          12 | 41234836R | Irene        | Salas     | Flores    |             NULL | NULL                |        NULL |  NULL |
|          13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |             NULL | NULL                |        NULL |  NULL |
|        NULL | NULL      | NULL         | NULL      | NULL      |                6 | Proyectos           |           0 |     0 |
|        NULL | NULL      | NULL         | NULL      | NULL      |                7 | Publicidad          |           0 |  1000 |
+-------------+-----------+--------------+-----------+-----------+------------------+---------------------+-------------+-------+
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

    

# Subconsultas

Con operadores básicos de comparación

1. Devuelve un listado con todos los empleados que tiene el departamento
  de Sistemas. (Sin utilizar INNER JOIN).

  ```sql
  SELECT * 
  FROM empleado AS e, departamento AS d
  WHERE d.nombre = (
      SELECT nombre
      FROM departamento
      WHERE nombre = 'Sistemas'
  )
  AND e.codigo_departamento = d.codigo;
  +--------+-----------+--------+-----------+-----------+---------------------+--------+----------+-------------+-------+
  | codigo | nit       | nombre | apellido1 | apellido2 | codigo_departamento | codigo | nombre   | presupuesto | gasto |
  +--------+-----------+--------+-----------+-----------+---------------------+--------+----------+-------------+-------+
  |      2 | Y5575632D | Adela  | Salas     | Díaz      |                   2 |      2 | Sistemas |      150000 | 21000 |
  |      7 | 80576669X | Pilar  | Ruiz      | NULL      |                   2 |      2 | Sistemas |      150000 | 21000 |
  |      9 | 56399183D | Juan   | Gómez     | López     |                   2 |      2 | Sistemas |      150000 | 21000 |
  +--------+-----------+--------+-----------+-----------+---------------------+--------+----------+-------------+-------+
  ```

  

2. Devuelve el nombre del departamento con mayor presupuesto y la cantidad
  que tiene asignada.

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

  

3. Devuelve el nombre del departamento con menor presupuesto y la cantidad
  que tiene asignada.

  ```
  SELECT nombre, presupuesto
  FROM departamento
  WHERE presupuesto = (
      SELECT MIN(presupuesto)
      FROM departamento
  )
  ORDER BY nombre
  LIMIT 1;
  
  ```

  

  ### Subconsultas con ALL y ANY

4. Devuelve el nombre del departamento con mayor presupuesto y la cantidad
  que tiene asignada. Sin hacer uso de MAX, ORDER BY ni LIMIT.

  ```sql
  SELECT nombre, presupuesto
  FROM departamento as d1
  WHERE presupuesto >= ALL (
      SELECT presupuesto 
      FROM departamento AS d2
      WHERE d1.codigo <> d2.codigo
  );
  +--------+-------------+
  | nombre | presupuesto |
  +--------+-------------+
  | I+D    |      375000 |
  +--------+-------------+
  ```

  

5. Devuelve el nombre del departamento con menor presupuesto y la cantidad
  que tiene asignada. Sin hacer uso de MIN, ORDER BY ni LIMIT.

  ```sql
  SELECT nombre, presupuesto
  FROM departamento as d1
  WHERE presupuesto <= ALL (
      SELECT presupuesto 
      FROM departamento AS d2
      WHERE d1.codigo <> d2.codigo
  );
  +------------+-------------+
  | nombre     | presupuesto |
  +------------+-------------+
  | Proyectos  |           0 |
  | Publicidad |           0 |
  +------------+-------------+
  ```

  

6. Devuelve los nombres de los departamentos que tienen empleados
  asociados. (Utilizando ALL o ANY).

  ```sql
  SELECT nombre
  FROM departamento
  WHERE codigo = ANY(
      SELECT codigo_departamento
      FROM empleado
      WHERE codigo_departamento IS NOT NULL
  );
  +------------------+
  | nombre           |
  +------------------+
  | Desarrollo       |
  | Sistemas         |
  | Recursos Humanos |
  | Contabilidad     |
  | I+D              |
  +------------------+
  ```

7. Devuelve los nombres de los departamentos que no tienen empleados
  asociados. (Utilizando ALL o ANY).

  ```sql
  SELECT nombre
  FROM departamento 
  WHERE codigo = ANY(
      SELECT d.codigo
      FROM departamento AS d
      LEFT JOIN empleado AS e ON e.codigo_departamento = d.codigo
      WHERE e.codigo_departamento IS NULL
  );
  +------------+
  | nombre     |
  +------------+
  | Proyectos  |
  | Publicidad |
  +------------+
  ```

  ### Subconsultas con IN y NOT IN

8. Devuelve los nombres de los departamentos que tienen empleados
  asociados. (Utilizando IN o NOT IN).

  ```sql
  SELECT nombre
  FROM departamento 
  WHERE codigo IN (
      SELECT d.codigo
      FROM departamento AS d
      LEFT JOIN empleado AS e ON e.codigo_departamento = d.codigo
      WHERE e.codigo_departamento IS NOT NULL
  );
  +------------------+
  | nombre           |
  +------------------+
  | Desarrollo       |
  | Sistemas         |
  | Recursos Humanos |
  | Contabilidad     |
  | I+D              |
  +------------------+
  ```

9. Devuelve los nombres de los departamentos que no tienen empleados
  asociados. (Utilizando IN o NOT IN).

  ```sql
  SELECT nombre
  FROM departamento 
  WHERE codigo NOT IN (
      SELECT d.codigo
      FROM departamento AS d
      LEFT JOIN empleado AS e ON e.codigo_departamento = d.codigo
      WHERE e.codigo_departamento IS NOT NULL
  );
  +------------+
  | nombre     |
  +------------+
  | Proyectos  |
  | Publicidad |
  +------------+
  ```

  

  ### Subconsultas con EXISTS y NOT EXISTS

10. Devuelve los nombres de los departamentos que tienen empleados
    asociados. (Utilizando EXISTS o NOT EXISTS).

    ```SQL
    SELECT nombre
    FROM departamento d
    WHERE EXISTS (
        SELECT 1
        FROM empleado e
        WHERE e.codigo_departamento = d.codigo
    );
    +------------------+
    | nombre           |
    +------------------+
    | Desarrollo       |
    | Sistemas         |
    | Recursos Humanos |
    | Contabilidad     |
    | I+D              |
    +------------------+
    ```

    

11. Devuelve los nombres de los departamentos que tienen empleados
    asociados. (Utilizando EXISTS o NOT EXISTS).

```SQL
SELECT nombre
FROM departamento d
WHERE NOT EXISTS (
    SELECT 1
    FROM empleado e
    WHERE e.codigo_departamento = d.codigo
);
+------------+
| nombre     |
+------------+
| Proyectos  |
| Publicidad |
+------------+
```

