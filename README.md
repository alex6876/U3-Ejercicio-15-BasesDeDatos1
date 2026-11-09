# Modelo Relacional de Bases de Datos 15



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para un sistema de gestión de esports y torneos de videojuegos, enfocado en el control de videojuegos, torneos, equipos, inscripciones de equipos, partidos, jugadores, plantillas y estadísticas de jugadores.

---

## Estructura de Tablas y Atributos



### 1. Videojuegos



* **PK (Clave Primaria):** `id_codigo_videojuego`


* **Atributos:**
* `nombre`


* `género`


* `desarrollador`


* `plataforma`





### 2. Torneo



* **PK (Clave Primaria):** `id_Torneo`


* **Atributos:**
* `nombre`


* `fecha_inicio`


* `fecha_fin`




* **FK (Claves Foráneas):**
* `id_codigo_videojuego` (asociado a la tabla Videojuegos)





### 3. Equipo



* **PK (Clave Primaria):** `id_Equipo`


* **Atributos:**
* `tag`


* `razón_social`


* `pais_origen`


* `fecha_fundación`





### 4. inscripción-equipo



* **FK (Claves Foráneas):**
* `id_Torneo` (asociado a la tabla Torneo)


* `id_Equipo` (asociado a la tabla Equipo)





### 5. Partido



* **PK (Clave Primaria):** `id_Partido`


* **Atributos:**
* `mapa_set_equipo2`


* `mapa_set_equipo1`


* `fecha_y_hora`


* `id_quipo1`


* `id_equipo2`




* **FK (Claves Foráneas):**
* `id_Torneo` (asociado a la tabla Torneo)





### 6. Jugador



* **PK (Clave Primaria):** `id_Jugador`


* **Atributos:**
* `nickname`


* `nombre_real`


* `nacionalidad`




* **FK (Claves Foráneas):**
* `id_Equipo` (asociado a la tabla Equipo)





### 7. Plantilla



* **FK (Claves Foráneas):**
* `id_Torneo` (asociado a la tabla Torneo)


* `id_Equipo` (asociado a la tabla Equipo)


* `id_Jugador` (asociado a la tabla Jugador)





### 8. Estadistica-jugador



* **FK (Claves Foráneas):**
* `id_Jugador` (asociado a la tabla Jugador)


* `id_Partido` (asociado a la tabla Partido)




* **Atributos:**
* `muertes`


* `bajas`


* `daño_total`


* `asistencia`





---

## Relaciones Principales



* **Videojuegos y Torneo:** Un videojuego puede ser el eje de múltiples torneos organizados mediante `id_codigo_videojuego`.


* **Torneo y Equipo (inscripción-equipo):** La relación de muchos a muchos entre torneos y equipos se gestiona a través de la tabla intermedia `inscripción-equipo`.


* **Torneo y Partido:** Los partidos oficiales se disputan en el contexto de un torneo específico vinculado por `id_Torneo`.


* **Equipo y Jugador:** Un equipo está integrado por varios jugadores que forman parte de su plantilla o roster actual.


* **Torneo, Equipo y Jugador (Plantilla):** La asociación específica de los jugadores que participan con sus equipos en un torneo determinado se administra en la tabla `Plantilla`.


* **Jugador y Partido (Estadistica-jugador):** El rendimiento individual de los competidores en cada encuentro se registra mediante la tabla `Estadistica-jugador`, relacionando `id_Jugador` e `id_Partido`.
