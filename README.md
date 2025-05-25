# 📘 Diccionario de Datos - Sistema de Gestión Académica

## 🧾 Tabla: Estudiante
| Campo             | Tipo            | Descripción                          |
|------------------|-----------------|--------------------------------------|
| id_estudiante     | NUMBER (PK)     | Identificador único del estudiante   |
| nombre            | VARCHAR2(50)    | Nombre del estudiante                |
| apellido          | VARCHAR2(50)    | Apellido del estudiante              |
| correo            | VARCHAR2(100)   | Correo electrónico                   |
| fecha_nacimiento  | DATE            | Fecha de nacimiento                  |
| id_carrera        | NUMBER (FK)     | Referencia a la tabla Carrera        |

## 🧾 Tabla: Carrera
| Campo         | Tipo           | Descripción                        |
|---------------|----------------|------------------------------------|
| id_carrera    | NUMBER (PK)    | Identificador único de la carrera |
| nombre        | VARCHAR2(100)  | Nombre de la carrera              |
| duracion      | NUMBER         | Duración en semestres             |

## 🧾 Tabla: Departamento
| Campo           | Tipo           | Descripción                             |
|------------------|----------------|-----------------------------------------|
| id_departamento  | NUMBER (PK)    | Identificador del departamento          |
| nombre           | VARCHAR2(100)  | Nombre del departamento                 |
| facultad         | VARCHAR2(100)  | Facultad a la que pertenece             |

## 🧾 Tabla: Profesor
| Campo          | Tipo           | Descripción                              |
|----------------|----------------|------------------------------------------|
| id_profesor    | NUMBER (PK)    | Identificador del profesor               |
| nombre         | VARCHAR2(50)   | Nombre del profesor                      |
| apellido       | VARCHAR2(50)   | Apellido del profesor                    |
| correo         | VARCHAR2(100)  | Correo electrónico                       |
| id_departamento| NUMBER (FK)    | Departamento al que pertenece            |

## 🧾 Tabla: Curso
| Campo              | Tipo           | Descripción                             |
|--------------------|----------------|-----------------------------------------|
| id_curso           | NUMBER (PK)    | Identificador del curso                 |
| nombre             | VARCHAR2(100)  | Nombre del curso                        |
| creditos           | NUMBER         | Créditos del curso                      |
| id_departamento    | NUMBER (FK)    | Departamento que lo ofrece              |

## 🧾 Tabla: Clase
| Campo         | Tipo           | Descripción                          |
|---------------|----------------|--------------------------------------|
| id_clase      | NUMBER (PK)    | Identificador único de la clase     |
| id_curso      | NUMBER (FK)    | Curso al que pertenece               |
| id_profesor   | NUMBER (FK)    | Profesor que dicta la clase          |
| id_horario    | NUMBER (FK)    | Horario asignado                     |
| id_aula       | NUMBER (FK)    | Aula donde se dicta la clase         |

## 🧾 Tabla: Horario
| Campo        | Tipo           | Descripción                          |
|--------------|----------------|--------------------------------------|
| id_horario   | NUMBER (PK)    | Identificador del horario            |
| dia          | VARCHAR2(15)   | Día de la clase                      |
| hora_inicio  | VARCHAR2(5)    | Hora de inicio                       |
| hora_fin     | VARCHAR2(5)    | Hora de fin                          |

## 🧾 Tabla: Aula
| Campo       | Tipo           | Descripción                           |
|-------------|----------------|---------------------------------------|
| id_aula     | NUMBER (PK)    | Identificador del aula                |
| edificio    | VARCHAR2(50)   | Nombre del edificio                   |
| capacidad   | NUMBER         | Capacidad del aula                    |

## 🧾 Tabla: Inscripcion (Relación N:M entre Estudiante y Clase)
| Campo         | Tipo         | Descripción                          |
|---------------|--------------|--------------------------------------|
| id_estudiante | NUMBER (FK)  | Estudiante inscrito                  |
| id_clase      | NUMBER (FK)  | Clase a la que se inscribe           |
| PRIMARY KEY   | (id_estudiante, id_clase) | Clave compuesta         |

---

# 🔗 Relaciones entre tablas

| Relación                                | Tipo de relación | Descripción                                    |
|-----------------------------------------|------------------|------------------------------------------------|
| Carrera **tiene** Estudiantes           | 1 : N            | Una carrera puede tener muchos estudiantes     |
| Departamento **administra** Cursos      | 1 : N            | Un departamento ofrece muchos cursos           |
| Departamento **emplea** Profesores      | 1 : N            | Un departamento tiene varios profesores        |
| Curso **genera** Clases                 | 1 : N            | Un curso puede tener varias clases             |
| Profesor **dicta** Clases               | 1 : N            | Un profesor puede dictar varias clases         |
| Horario **asigna** Clases               | 1 : N            | Un horario puede aplicarse a varias clases     |
| Aula **alberga** Clases                 | 1 : N            | Un aula puede albergar varias clases           |
| Estudiante **asiste a** Clases          | N : M            | Se implementa mediante la tabla Inscripcion    |

Documento del proyecto:
[Base de datos tarea.pdf](https://github.com/user-attachments/files/20432368/Base.de.datos.tarea.pdf)
[Base de datos tarea.docx](https://github.com/user-attachments/files/20432370/Base.de.datos.tarea.docx)


