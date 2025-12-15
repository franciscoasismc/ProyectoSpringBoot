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
|   `codpostal`   |   NUMBER      | `NOT NULL`, exactamente 5 dígitos |
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
|   `fechaFin`    |   DATE        | No puede ser anterior a la fecha actual |
|   `username`    |   VARCHAR     | `FOREIGN KEY`     |
|   `idDireccion` |   NUMBER      | `FOREIGN KEY`     |

---
---


