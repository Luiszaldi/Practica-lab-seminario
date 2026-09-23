# Equipo XX — Caso Gimnasio

**Integrantes:**
-Luis Fernando Zaldivar Plata
-Sergio Ituriel Hernandez Escalona
-Irene Karina Martinez Solis

## Esquema relacional

<!-- Usen la notación de guias/notacion.md. Una tabla por renglón. -->

```
PLAN(**id_plan**, nombre, costo_mensual)
SOCIO(**num_socio**, nombre, fecha_nacimiento, correo?, id_plan → PLAN)
TELEFONOS_SOCIO(**num_socio** → SOCIO, **telefono**)
LOCKER(**num_locker**, ubicacion, num_socio? → SOCIO UNIQUE)
INSTRUCTOR(**num_empleado**, nombre, especialidad, supervisor? → INSTRUCTOR)
CLASE(**id_clase**, nombre, cupo_max, num_empleado → INSTRUCTOR)
SESION(**id_clase** → CLASE, **numero_sesion**, fecha, hora_inicio, salon)
INSCRIPCION(**num_socio** → SOCIO, **id_clase** → CLASE, **fecha_inscripcion**, estatus)

```

## Diagrama (opcional)

<!-- Si quieren, dibujen aquí el esquema en Mermaid. -->
## Diagrama E/R - Caso Gimnasio

```mermaid
erDiagram
    PLAN ||--o{ SOCIO : "posee"
    SOCIO ||--|{ TELEFONOS_SOCIO : "tiene"
    SOCIO |o--o| LOCKER : "renta"
    INSTRUCTOR |o--o{ INSTRUCTOR : "supervisa"
    INSTRUCTOR ||--o{ CLASE : "imparte"
    CLASE ||--|{ SESION : "se divide en"
    SOCIO ||--o{ INSCRIPCION : "realiza"
    CLASE ||--o{ INSCRIPCION : "recibe"

    PLAN {
        int id_plan PK
        string nombre
        decimal costo_mensual
    }

    SOCIO {
        int num_socio PK
        string nombre
        date fecha_nacimiento
        string correo
        int id_plan FK
    }

    TELEFONOS_SOCIO {
        int num_socio PK, FK
        string telefono PK
    }

    LOCKER {
        int num_locker PK
        string ubicacion
        int num_socio FK
    }

    INSTRUCTOR {
        int num_empleado PK
        string nombre
        string especialidad
        int supervisor FK
    }

    CLASE {
        int id_clase PK
        string nombre
        int cupo_max
        int num_empleado FK
    }

    SESION {
        int id_clase PK, FK
        int numero_sesion PK
        date fecha
        time hora_inicio
        string salon
    }

    INSCRIPCION {
        int num_socio PK, FK
        int id_clase PK, FK
        date fecha_inscripcion PK
        string estatus
    }
```

