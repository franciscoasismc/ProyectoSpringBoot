# PROYECTO SPRING BOOT ☕🍃

## 💡 IDEA DE LA APLICACIÓN 💡
**Aplicación que servirá para administrar las tareas del hogar.**
Se darán de alta tareas con una fecha y descripción, usuarios a los cuales se les asignarán las tareas y direcciones las cuales pertenecerán a los usuarios.

### 🔧 FUNCIONALIDADES 🔧
- **Crear** de tareas, usuarios y direcciones.
- **Listar** tareas, usuarios y direcciones.
- **Actualizar** tareas, usuarios y direcciones.
- **Borrar** tareas, usuarios y direcciones.
- Asignar tareas a usuarios y direcciones.
- Asignar direcciones a usuarios.

Tablas de la base de datos: **Usuarios**, **Direcciones** y **Tareas**.

---
---


## 💾 TABLAS DE LA BASE DE DATOS 💾
### 👨 USUARIOS 👨
|      CAMPO      |     TIPO      |   RESTRICCIONES   |
|   :---------:   |  :-------:    | :---------------: |
|   `username`    |   VARCHAR     |  `PRIMARY KEY`    |
|   `nombre`      |   VARCHAR     |  `NOT NULL`       |
|   `apellidos`   |   VARCHAR     |  -                |
|   `email`       |   VARCHAR     |  `NOT NULL`, `UNIQUE`, debe contener @ y terminar en .com/.es |
|   `password`    |   VARCHAR     |  Longitud: 5-20   |
|   `roles`       |   VARCHAR     |  Valores: `ADMIN` / `USER` |

### 🏠 DIRECCIONES 🏠
|      CAMPO      |     TIPO      |   RESTRICCIONES   |
|   :---------:   |  :-------:    | :---------------: |
|   `idDireccion` |   NUMBER      | `PRIMARY KEY`, Autoincremento |
|   `calle`       |   VARCHAR     | `NOT NULL`        |
|   `numero`      |   VARCHAR     | `NOT NULL`, debe ser mayor que 0 |
|   `codPostal`   |   NUMBER      | `NOT NULL`, exactamente 5 dígitos |
|   `municipio`   |   VARCHAR     | `NOT NULL`        |
|   `provincia`   |   VARCHAR     | `NOT NULL`, debe ser una provincia de Andalucía |
|   `username`    |   VARCHAR     | `FOREIGN KEY`     |

### 📃 TAREAS 📃
|      CAMPO      |     TIPO      |   RESTRICCIONES   |
|   :---------:   |  :-------:    | :---------------: |
|   `idTarea`     |   NUMBER      | `PRIMARY KEY`, Autoincremento |
|   `nombre`      |   VARCHAR     | `NOT NULL`        |
|   `descripcion` |   TEXT        | -                 |
|   `estado`      |   BOOLEAN     | Por defecto `false` |
|   `fechaFin`    |   DATETIME    | No puede ser anterior a la fecha actual |
|   `username`    |   VARCHAR     | `FOREIGN KEY`     |
|   `idDireccion` |   NUMBER      | `FOREIGN KEY`     |

---
---


## 📑 DIAGRAMA ENTIDAD-RELACIÓN 📑
+ USUARIO (1:N) <- TIENE (M:N) ->  DIRECCION (1:N)
+ USUARIO (0:1) <- REALIZA (1:N) -> TAREA (0:N)
+ DIRECCION (1:1) <- CONTIENE (1:N) -> TAREA (0:N)

```mermaid
erDiagram
  USUARIO }|--|{ DIRECCION : TIENE
  USUARIO o|--o{ TAREA : REALIZA
  DIRECCION ||--o{ TAREA : CONTIENE
  TAREA
  USUARIO {
    String username
    String nombre
    String apellidos
    String email
    String password
    String roles
  }
  DIRECCION {
    int idDireccion
    String calle
    String numero
    int codPostal
    String municipio
    String provincia
    String username
  }
  TAREA {
    int idTarea
    String nombre
    String descripcion
    boolean estado
    LocalDateTime fechaFin
    String username
    int idDireccion
  }
