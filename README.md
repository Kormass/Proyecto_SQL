## PEDRO ORTEGA

### GRUPO R4

~~~sql
- creando base de datos

create database Proyecto.db

use Proyecto.db

- creando tablas

CREATE TABLE "Carreras" (

​	"id_carrera"	INT,

​	"Carrera"	VARCHAR (48),

​	PRIMARY KEY("id_carrera" AUTOINCREMENT)

);

CREATE TABLE "Cursos" (

​	"id_curso"	INT,

​	"curso"	INT,

​	PRIMARY KEY("id_curso" AUTOINCREMENT)

);

CREATE TABLE "Instructores" (

​	"id_instructor"	INT,

​	"instructor"	VARCHAR (48),

​	"Especialidad"	VARCHAR (48),

​	PRIMARY KEY("id_instructor" AUTOINCREMENT)

);

CREATE TABLE "Rutas" (

​	"id_ruta"	INT,

​	"ruta"	VARCHAR (48),

​	PRIMARY KEY("id_ruta" AUTOINCREMENT)

);

create table Aprendices (

​	"id_aprendiz" INT PRIMARY KEY AUTOINCREMENT,

​	"id_matriculaxruta" INT

​	"nombre" VARCHAR (48)

);

CREATE TABLE Matriculas (

  Id_matricula INT PRIMARY KEY AUTOINCREMENT,

  Estado VARCHAR (48),

  Nombre VARCHAR (48),

  Carrera VARCHAR (48),

  RutaAprendizaje VARCHAR (48),

  Curso VARCHAR (48),

  Instructor VARCHAR (48)

);

-- insertando datos a las tablas

insert into Carreras (Carrera)

VALUES

("Desarrollo de software"),

("Electronica"),

("Mecanica Automotriz"),

("Seguridad y Salud Ocupacional"),

("Soldadura");

insert into Rutas (ruta)

VALUES

("Sistemas de informacion Empresariales"),

("Videojuegos"),

("Machine Learning"),

("Microcontroladores"),

("Robotica"),

("Dispositivos Bio.medicos"),

("Motores Hibridos"),

("Vehiculos de Uso Agricola"),

("Sistemas de Gestion en Seguridad Ocupacional"),

("Soldadura Autogena Industrial"),

("Soldadura Electrica Industrial"),

("Soldadura Submarina");

insert into Cursos (curso)

VALUES

("Matematicas Basicas"),

("Algebra Computacional"),

("Programacion Basica"),

("Ingles"),

("Electronica Basica"),

("Motor de Cuatro Tiempos"),

("Enfermedades Laborales"),

("Higiene Postural en el trabajo"),

("Ergonomia"),

("Legislacion Laboral en Colombia"),

("Materiales de Soldadura"),

("Metodos de Soldadura"),

("Fusion de Metales"),

("Buceo 1"),

("Buceo 2"),

("Riesgo Electrico"),

("Bases de Datos Relacionales"),

("Bases de Datos No Relacionales"),

("Electronica Digital"),

("Microprocesadores");

insert into Instructores (instructor, Especialidad)

VALUES

("Ricardo Vicente Jaimes", "Sistemas"),

("Marinela Narvaez", "Salud Ocupacional"),

("Agustin Parra Granados", "Soldadura"),

("Nelson Raul Buitrago", "Mecanica"),

("Roy Hernando Llamas", "Ingles"),

("Maria Jimena Monsalve", "Electronica"),

("Juan carlos Cobos", "Electronica"),

("Pedro Nell Santoamaria", "Sistemas"),

("Andrea Gonzales", "Sistemas"),

("Marisela Sevilla", "Salud Ocupacional");

INSERT INTO Aprendices (id_matricula,nombre)

values 

(1,"Pedro Ortega"),

(2,"Jose Velandia"),

(1,"Franyer Garzon"),

(5,"Jose Ariza"),

(2,"Alejandro Palacio"),

(2,"Alejandro Mancilla"),

(4,"Samuel Rodriguez"),

(3,"Diana Paola");

-- creando relacion de tablas

Alter table Rutas

ADD id_carrera INT;

Alter table Instructores

ADD id_cursos INT;

Create table Cursos_por_ruta(

​	"id_cursosxruta" INT PRIMARY KEY AUTOINCREMENT,

​	"id_cuross" INT,

​	"id_rutas" INT

);

- Rellenando nuevas tablas

INSERT INTO Matriculas (id_ruta, id_aprendiz)

values 

(2, 1),

(3, 2),

(3, 3),

(1, 3),

(2, 4),

(1, 5),

(2, 6),

(3, 7),

ALTER TABLE Matriculas

ADD Estado_Matricula;

UPDATE Matriculas set Estado_Matricula = "En Ejecucion" where id_matricula = 2;

UPDATE Matriculas set Estado_Matricula = "Aprobado" where id_matricula = 3;

UPDATE Matriculas set Estado_Matricula = "Aprobado" where id_matricula = 4;

UPDATE Matriculas set Estado_Matricula = "Aprobado" where id_matricula = 6;

UPDATE Matriculas set Estado_Matricula = "En Ejecucion" where id_matricula = 7;

UPDATE Matriculas set Estado_Matricula = "Aprobado" where id_matricula = 8;

UPDATE Matriculas

SET Estado_matriculas = "cancelado"

WHERE estado_matriculas IS NULL;



SELECT Aprendices.nombre, Rutas.ruta

FROM Aprendices

JOIN Matriculas ON Aprendices.id_matricula = Matriculas.id_matricula

JOIN Rutas ON Matriculas.id_ruta = Rutas.id_ruta

WHERE Matriculas.Estado_Matricula = "cancelado";

–NO HABIA VISTO LA PESTAÑA DE DATOS–

-- Crear la base de datos

CREATE DATABASE IF NOT EXISTS PROYECTO;

USE PROYECTO;

-- Crear la tabla Carrera

CREATE TABLE Carrera (

  id_carrera INT PRIMARY KEY AUTO_INCREMENT,

  nombre_carrera VARCHAR(50)

);

-- Crear la tabla RutaAprendizaje

CREATE TABLE RutaAprendizaje (

  id_ruta INT PRIMARY KEY AUTO_INCREMENT,

  nombre_ruta VARCHAR(50),

  id_carrera INT,

  FOREIGN KEY (id_carrera) REFERENCES Carrera(id_carrera)

);

-- Crear la tabla Aprendiz

CREATE TABLE Aprendiz (

  id_aprendiz INT PRIMARY KEY AUTO_INCREMENT,

  nombre VARCHAR(50),

  estado VARCHAR(20),

  id_ruta INT,

  FOREIGN KEY (id_ruta) REFERENCES RutaAprendizaje(id_ruta)

);

-- Crear la tabla Instructores

CREATE TABLE Instructores (

  id_instructor INT PRIMARY KEY AUTO_INCREMENT,

  nombre_instructor VARCHAR(255) NOT NULL,

  especialidad VARCHAR(255) NOT NULL

);

-- Crear la tabla Curso

CREATE TABLE Curso (

  id_curso INT PRIMARY KEY AUTO_INCREMENT,

  nombre_curso VARCHAR(50),

  id_ruta INT,

  id_instructor INT,

  FOREIGN KEY (id_ruta) REFERENCES RutaAprendizaje(id_ruta),

  FOREIGN KEY (id_instructor) REFERENCES Instructores(id_instructor)

);

-- Insertar datos en la tabla Carrera

INSERT INTO Carrera (nombre_carrera) VALUES

("Desarrollo de Software"),

("Electrónica"),

("Mecánica Automotriz"),

("Seguridad y Salud Ocupacional"),

("Soldadura");

- Insertar datos en la tabla RutaAprendizaje

INSERT INTO RutaAprendizaje (nombre_ruta) VALUES

("Sistemas de Información Empresariales"),

("Videojuegos"),

("Machine Learning"),

("Microcontroladores"),

("Robótica"),

("Dispositivos Bio-médicos"),

("Motores Híbridos"),

("Vehículos de Uso Agrícola"),

("Sistemas de Gestión en Seguridad Ocupacional"),

("Soldadura Autógena Industrial"),

("Soldadura Eléctrica Industrial"),

("Soldadura Submarina");

-- Insertar datos en la tabla Curso

INSERT INTO Curso (nombre_curso) VALUES

("Matemáticas Básicas"),

("Álgebra Computacional"),

("Programación Básica"),

("Inglés"),

("Electrónica Básica"),

("Motor de Cuatro Tiempos"),

("Enfermedades Laborales"),

("Higiene Postural en el Trabajo"),

("Ergonomía"),

("Legislación Laboral en Colombia"),

("Materiales de Soldadura"),

("Métodos de Soldadura"),

("Fusión de Metales"),

("Buceo 1"),

("Buceo 2"),

("Riesgo Eléctrico"),

("Bases de Datos Relacionales"),

("Bases de Datos NO Relacionales"),

("Electrónica Digital"),

( "Microprocesadores");

-- Insertar datos en la tabla Instructores

INSERT INTO Instructores (nombre_instructor, especialidad) VALUES

("Ricardo Vicente Jaimes", "Sistemas"),

("Marinela Narvaez", "Salud Ocupacional"),

("Agustín Parra Granados", "Soldadura"),

("Nelson Raúl Buitrago", "Mecánica"),

("Roy Hernando Llamas", "Inglés"),

("Maria Jimena Monsalve", "Electrónica"),

("Juan Carlos Cobos", "Electrónica"),

("Pedro Nell Santamaría", "Sistemas"),

("Andrea González", "Sistemas"),

( "Marisela Sevilla", "Salud Ocupacional");

-- Crear la tabla Matriculas

CREATE TABLE Matriculas (

  id_matricula INT PRIMARY KEY,

  id_estudiante VARCHAR(255) NOT NULL,

  id_carrera INT,

  id_cursoxruta INT,

  id_instructor INT,

  FOREIGN KEY (id_carrera) REFERENCES Carrera(id_carrera),

  FOREIGN KEY (id_cursoxruta) REFERENCES RutaAprendizaje(id_rutaxcurso),

  FOREIGN KEY (id_instructor) REFERENCES Instructores(id_instructor)

);

-- Insertar datos en la tabla Aprendiz

INSERT INTO aprendiz (nombre, estado, id_ruta)

VALUES

  ("Carlos Saúl Gómez","activo ",1),

  ("Leyla María Delgado Vargas","Activo", 1),

  ("Juan José Cardona","Cancelado", 1),

  ("Sergio Augusto Contreras Navas","Activo", 1),

  ("Ana María Velázquez Parra","Activo", 1),

  ("Gustavo Noriega Alzate","Terminado",2),

  ("Pedro Nell Gómez Díaz","Terminado",2),

  ("Jairo Augusto Castro Camargo","Terminado",2),

  ("Henry Soler Vega","Cancelado",2),

  ("Antonio Cañate Cortés","Terminado",5),

  ("Daniel Simancas Junior","Terminado",5);

-- Insertar datos en la tabla "matricula"

INSERT INTO matriculas (id_aprendiz, ruta_aprendizaje, instructor)

VALUES

  (1, 1, "Activo", "marinela Narvaez"),

  (1, 1, "Activo" "Ricardo Vicente Jaimes"),

  (1, 1,"Activo","Agustín Parra Granados"),

  (1, 1,"Activo" ,"Nelson Raúl Buitrago")

  (2, 1,"Activo","Ricardo Vicente Jaimes"),

  (2, 1, "Activo","Agustín Parra Granados"),

  (2, 1,"Terminado","Roy Hernando Llamas"),

  (2, 1,"Terminado","Nelson Raúl Buitrago"),

  (3, 2, "Cancelado","Ricardo Vicente Jaimes"),

  (3, 2, "Cancelado","Agustín Parra Granados"),

  (3, 2, "Cancelado","Roy Hernando Llamas"),

  (4, 2, "Activo","Nelson Raúl Buitrago"),

  (4, 2, "Activo","Ricardo Vicente Jaimes"),

  (4, 2, "Activo","Agustín Parra Granados"),

  (5, 3, "Activo","Roy Hernando Llamas"),

  (5, 3, "Activo","Marinela Narvaez"),

  (5, 3, "Activo","Juan Carlos Cobos"),

  (6, 4, "Terminado","Maria Jimena Monsalve"),

  (6, 4, "Terminado","Juan Carlos Cobos"),

  (6, 4, "Terminado","Juan Carlos Cobos"),

  (7, 4, "Terminado","Maria Jimena Monsalve"),

  (7, 4, "Terminado","Juan Carlos Cobos"),

  (7, 4,"Terminado","Juan Carlos Cobos"),

  (8, 5,"Terminado","Maria Jimena Monsalve"),

  (8, 5,"Terminado" ,"Juan Carlos Cobos"),

  (9, 5,"Cancelado","Maria Jimena Monsalve"),

  (9, 5, "Cancelado","Juan Carlos Cobos"),

  (9, 5, "Cancelado","Agustín Parra Granados"),

  (10, 11,"Terminado","Agustín Parra Granados"),

  (10, 11,"terminado","Agustín Parra Granados"),

  (11, 10,"Terminado","");

  (11, 10, "terminado",""),
~~~



## PREGUNTAS 

### 1. Agregue un campo Estado_Matrícula a la tabla Matrícula que indique si eestudiante se 

### encuentra “En Ejecución”, “Terminado” o “Cancelado”**

~~~SQL
ALTER TABLE Matriculas

ADD Estado_Matricula VARCHAR(50);
~~~

### 2. Agregue a el campo edad a la tabla de Aprendices.

~~~SQL
ALTER TABLE Aprendiz

ADD Edad INT;
~~~

### 3. Si suponemos que los cursos tienen una duración diferente dependiendo de la ruta que lo contenga ¿qué modificación haría a la estructura de datos ya planteada?

-- Actualizar la duración de los cursos según la ruta

– incluso se puede realizar una tabla aparte donde se registren el tipo de curso para saber cuanto va a durar segun el contenido de cada uno de estos y asi modificarlo en un futuro mas facilmente si se llega a realizar algun cambio en los mismos

~~~sql
ALTER TABLE Cursos_por_ruta

ADD duracion_curso INT NOT NULL;
~~~

### 4. Seleccionar los nombres y edades de aprendices que están cursando la carrera de electrónica.

~~~sql
SELECT A.nombre, A.Edad

FROM AprendiZ A

JOIN Matricula M ON A.id_aprendiz = M.id_aprendiz

JOIN RutaAprendizaje R ON M.id_ruta = R.id_ruta

JOIN Carrera C ON R.id_carrera = C.id_carrera

WHERE C.nombre_carrera = "Electrónica";
~~~

    +------------------------------+------+--------------+
    | nombre	                   | Edad |nombre_carrera|
    +------------------------------+------+--------------+
    | Gustavo Noriega Alzate       |   20 | Electrónica  |
    | Pedro Nell Gómez Díaz        |   20 | Electrónica  |
    | Jairo Augusto Castro Camargo |   20 | Electrónica  |
    | Henry Soler Vega             |   20 | Electrónica  |
    +------------------------------+------+--------------+

### 5. Seleccionar Nombres de Aprendices junto al nombre de la ruta de aprendizaje que cancelaron.

~~~sql
SELECT A.nombre, R.nombre_ruta

FROM Aprendiz A

JOIN Matricula M ON A.id_aprendiz = M.id_aprendiz

JOIN RutaAprendizaje R ON M.id_ruta = R.id_ruta

WHERE M.Estado_Matricula = "Cancelado";
~~~

    +--------------------+-------------+
    | nombre             | nombre_ruta |
    +--------------------+-------------+
    | Juan José Cardona  | Videojuegos |
    | Henry Soler Vega   | Robótica    |
    +--------------------+-------------+



### 6. Seleccionar Nombre de los cursos que no tienen un instructor asignado.

~~~sql
SELECT nombre_curso

FROM Curso

WHERE id_instructor IS NULL;
~~~

    +----------------------------------+
    | nombre_curso                     |
    +----------------------------------+
    | Motor de Cuatro Tiempos          |
    | Enfermedades Laborales           |
    | Higiene Postural en el Trabajo   |
    | Ergonomía                        |
    | Legislación Laboral en Colombia  |
    | Métodos de Soldadura             |
    | Buceo 1                          |
    | Buceo 2                          |
    | Riesgo Eléctrico                 |
    +----------------------------------+

### 7. Seleccionar Nombres de los instructores que dictan cursos en la ruta de aprendizaje “Sistemas de Información Empresariales”.

~~~sql
SELECT DISTINCT I.nombre_instructor

FROM Instructor I

JOIN Curso C ON I.id_instructor = C.id_instructor

JOIN RutaAprendizaje R ON C.id_ruta = R.id_ruta

WHERE R.nombre_ruta = "Sistemas de Información Empresariales";
~~~

    +-------------------------+
    | nombre_instructor       |
    +-------------------------+
    | Marinela Narvaez        |
    | Ricardo Vicente Jaimes  |
    | Agustín Parra Granados  |
    | Nelson Raúl Buitrago    |
    | Roy Hernando Llamas     |
    +-------------------------+

### 8. Genere un listado de todos los aprendices que terminaron una Carrera mostrando el nombre del profesional, el nombre de la carrera y el  énfasis de la carrera (Nombre de la Ruta de aprendizaje)

~~~sql
SELECT A.nombre AS Nombre_Aprendiz, C.nombre_carrera AS Carrera, R.nombre_ruta AS Enfasis

FROM Aprendiz A

JOIN Matricula M ON A.id_aprendiz = M.id_aprendiz

JOIN RutaAprendizaje R ON M.id_ruta = R.id_ruta

JOIN Carrera C ON R.id_carrera = C.id_carrera

WHERE M.Estado_Matricula = "Terminado";
~~~

    +------------------------------+--------------+---------------------------------+
    | Nombre_Aprendiz              |    Carrera   | Enfasis                         |
    +------------------------------+--------------+---------------------------------+
    | Gustavo Noriega Alzate       | Electrónica  | Microcontroladores              |
    | Pedro Nell Gómez Díaz        | Electrónica  | Microcontroladores              |
    | Jairo Augusto Castro Camargo | Electrónica  | Robótica                        |
    | Antonio Cañate Cortés        | Soldadura    | Soldadura Eléctrica Industrial  |
    | Daniel Simancas Junior       | Soldadura    | Soldadura Autógena Industrial   |
    +------------------------------+--------------+---------------------------------+

### 9. Genere un listado de los aprendices matriculados en el curso “Bases de Datos Relacionales”.

~~~SQL
SELECT A.nombre AS Nombre_Aprendiz

FROM Aprendiz A

JOIN Matricula M ON A.id_aprendiz = M.id_aprendiz

JOIN Curso C ON M.id_curso = C.id_curso

WHERE C.nombre_curso = "Bases de Datos Relacionales";
~~~

    +-----------------------------+
    | Nombre_Aprendiz             |
    +-----------------------------+
    | Carlos Saúl Gómez           |
    | Ana María Velázquez Parra   |
    +-----------------------------+

### 10. Nombres de Instructores que no tienen curso asignado.

~~~sql
SELECT nombre_instructor

FROM Instructor

WHERE id_instructor NOT IN (SELECT DISTINCT id_instructor FROM Curso WHERE id_instructor IS NOT NULL);
~~~

    +------------------------+
    | nombre_instructor      |
    +------------------------+
    | Pedro Nell Santamaría  |
    | Andrea González        |
    | Marisela Sevilla       |
    +------------------------+



### PREGUNTAS TIPO OPCION MULTIPLE

### ¿Cuál de las siguientes consultas se utilizaría para obtener el nombre de la carrera de un estudiante matriculado en el curso "Inglés"?

**a.** SELECT c.carrera FROM Carreras c JOIN Matriculas m ON c.id_carrera = m.id_carrera WHERE m.nombre_curso = "Inglés";

**b.** SELECT c.carrera FROM Carreras c JOIN Matriculas m ON c.id_carrera = m.id_carrera AND m.nombre_curso = "Inglés";

**c.** SELECT c.carrera FROM Carreras c, Matriculas m WHERE c.id_carrera = m.id_carrera AND m.nombre_curso = "Inglés";

**d.** SELECT carrera FROM Carreras WHERE id_carrera IN (SELECT id_carrera FROM Matriculas WHERE nombre_curso = "Inglés");

#### Respuesta: B

## Si no supieramos un termino de un campo completo que simbolo usaremos para referirnos de que hay algo mas despues de la consulta?

1. $
2. \#
3. “
4. %

####  Respuesta: D

## ¿Si tuvieramos que realizar una consulta que tenga alguna funcion dentro de la misma, y luego quisieramos trabajar con el resultado que operador deberiamos utilizar para comparar?

1. Where
2. Having
3. =, < >
4. If

#### Respuesta: B