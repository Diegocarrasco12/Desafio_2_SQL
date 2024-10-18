# Desafio_2_SQL
--1. ¿Cuántos registros hay? (1 Punto)
SELECT COUNT(*) total_registros from inscritos;
![(P 1) total registros](https://github.com/user-attachments/assets/1181b9d9-b9a2-4712-952b-c2fdea1353a8)


--2. ¿Cuántos inscritos hay en total? (1 Punto)
SELECT SUM(cantidad) AS total_inscritos from inscritos;
![(P 2) Total Inscritos](https://github.com/user-attachments/assets/ce48661b-4c5c-4d50-a47d-6b17c78b73b8)


--3. ¿Cuál o cuáles son los registros de mayor antigüedad? (1 Punto)
SELECT * 
FROM INSCRITOS
WHERE fecha = (SELECT MIN(fecha) FROM INSCRITOS);
![(P 3)Mayor antiguedad](https://github.com/user-attachments/assets/f80e6683-cfe3-4006-bba9-3e3709185013)


--4. ¿Cuántos inscritos hay por día? (Indistintamente de la fuente de inscripción) (1 Punto)
SELECT fecha, SUM(cantidad) AS total_inscritos
FROM INSCRITOS
GROUP BY fecha
ORDER BY fecha;
![(P 4) Inscritos por día](https://github.com/user-attachments/assets/319bc0cc-762b-41f3-8250-dff9ff63c338)


--5. ¿Cuántos inscritos hay por fuente? (1 Punto)
SELECT fuente, SUM(cantidad) AS total_inscritos
FROM INSCRITOS
GROUP BY fuente
ORDER BY fuente;
![(P 5) Inscritos por fuente](https://github.com/user-attachments/assets/655266d4-c455-4e72-bd63-3f33864afb2b)


--6. ¿Qué día se inscribió la mayor cantidad de personas? Y ¿Cuántas personas se inscribieron en ese día? (1 Punto)
SELECT fecha, SUM(cantidad) AS total_inscritos
FROM INSCRITOS
GROUP BY fecha
ORDER BY total_inscritos DESC
LIMIT 1;
![(P 6) Día con mayor cantidad de inscritos](https://github.com/user-attachments/assets/21129fdd-ff06-45e5-9db3-54c0b722161a)


--7. ¿Qué día se inscribieron la mayor cantidad de personas utilizando el blog? ¿Cuántas personas fueron? (si hay más de un registro con el máximo de personas, considera solo el primero)(1 Punto)
SELECT fecha, SUM(cantidad) AS total_inscritos
FROM INSCRITOS
WHERE fuente = 'Blog'
GROUP BY fecha
ORDER BY total_inscritos DESC
LIMIT 1;
![(7) Dia mayor inscritos BLOG](https://github.com/user-attachments/assets/e4c2c036-f3f8-4270-abbf-7826346e882c)


-- 8. ¿Cuál es el promedio de personas inscritas por día? Toma en consideración que la base de datos tiene un registro de 8 días, es decir, se obtendrán 8 promedios. (1 Punto)
SELECT fecha, AVG(cantidad) AS promedio_inscritos
FROM INSCRITOS
GROUP BY fecha
ORDER BY fecha;
![(8) Promedio personas inscritas por día](https://github.com/user-attachments/assets/b7f7ab85-4c1c-4023-8200-416173357d8e)


--9. ¿Qué días se inscribieron más de 50 personas?(1 Punto)
SELECT fecha, SUM(cantidad) AS total_inscritos
FROM INSCRITOS
GROUP BY fecha
HAVING SUM(cantidad) > 50
ORDER BY fecha;
![(9) Días inscritos mas de 50 personas](https://github.com/user-attachments/assets/62d3b929-37c6-4a3a-9216-df8928bd11e8)


-- 10. ¿Cuál es el promedio por día de personas inscritas? Considerando sólo calcular desde el tercer día.(1 Punto)
SELECT fecha, AVG(cantidad) AS promedio_diario 
FROM inscritos 
GROUP BY fecha 
ORDER BY fecha ASC OFFSET 2;
![(10) Promedio inscritos por día](https://github.com/user-attachments/assets/4050d480-4aad-4a9f-b79d-9710e7a30327)






