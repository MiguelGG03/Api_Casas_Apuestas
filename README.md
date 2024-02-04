# Limpieza de datos

## Bookmaker-DS

Sistema de apuestas para partidos de futbol de la UEFA Champions League

## Instalacion

Clonar el repositorio: [https://github.com/rubences/Api_Casas_Apuestas.git](https://github.com/rubences/Api_Casas_Apuestas.git)

Crear un archivo .env utilizando de ejemplo .env-example

Ejecutar ./install.sh para crear el entorno virtual y para instalar todos los modulos a utilizar

## Ejecucion

Ejecutar ./boot.sh para hacer correr el servidor

## Mi análisis

El enlace al repositorio es el siguiente : [https://github.com/MiguelGG03/Api_Casas_Apuestas.git](https://github.com/MiguelGG03/Api_Casas_Apuestas.git)

### Problemas

1. En la tabla `apuestas`, los valores nulos en la columna `equipo_ganador_id` indican `apuestas` que se han realizado pero para las cuales el resultado del partido correspondiente aún no se ha determinado o no se ha registrado correctamente.

2. Los valores de la columna `ganador` en la tabla partidos están vacíos (llenos de None), lo cual sugiere que los resultados de algunos partidos no se han registrado.

3. Dentro de la tabla `apuestas` podemos encontrar que todas las apuestas se hacen desde el mismo id de usuario.

4. Dentro de la tabla `apuestas` encontramos que las apuestas para un mismo partido las ganan ambos equipos en casos diferentes.

### Conclusiones

Después de un análisis exhaustivo de los datos, he llegado a la conclusión de que no tiene sentido hacer un análisis de esta base de datos con fines de hacer predicciones o poder conocer futuros movimientos de los usuarios.

La limpieza de los datos supone practicamente cambiar por completo la tabla `apuestas` y hacer cambios tambien en partes de otras tablas como `partidos`.

El problema está en la incoherencia de los datos proporcionados dentro de la tabla `apuestas`, principalmente porque:

- Todas las apuuestas (excepto una) son realizadas por el usuario con id 88, esto no es una razon de mucho peso pero es extraño.
- Todas las apuestas (excepto una) son realizadas al mismo partido, esto no es una razon de mucho peso pero es extraño.
- Aún sabiendo que mayoritariamente las apuestas fueron realizadas hacia el partido cuyo id es el 1 , los resultados __para el mismo partido__ fueron diferentes. Es decir, que para el mismo partido algunas apuestas dan como equipo ganador al Villarreal, otras al Atalanta, y otras se quedan vacias (que interpreté como un empate), lo cual no tiene ningún sentido.

> El partido en el que se basan las apuestas es el Villarreal vs Atalanta de 2021 y cuyo resultado fue de empate 2 a 2

Debido a todos estos problemas expuestos, llego a la conclusion de que no es rentable hacer un análisis de predicción sobre estos datos, porque obtendremos resutados que no van a estar basados en unos datos coherentes.

### Solución

La única solucion es, o bien cambiar los datos manualmente registro por registro, o bien encontrar una nueva tabla apuestas con datos correctos.
