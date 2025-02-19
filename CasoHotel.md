# SOLUCION CASO HOTEL

### Karen Nicolle Arango Valencia

```mermaid
classDiagram
direction TB
    class Hotel {
	    - str nombre
	    - Direccion direccion
	    - Persona duenio
	    - list habitaciones
	    - list trabajadores
	    - list reservas
        + listarTrabajadores() list<Trabajador>
	    + agregarHuesped(Huesped) void
	    + agregarReserva(Reserva) void
        + listarHuespedes() list<Huesped>
        + listarReservas() list<Reserva>
        + obtenerHabitacionesDisponibles() list<Habitacion>
        + modificarInfoHotel() void
    }
    class Direccion {
	    - int calle
	    - int carrera
	    - int numero
	    - str barrio
	    - str ciudad
    }
    class Habitacion {
	    - int numeroUnico
	    - bool disponibilidad
    }
    class Individual {
	    - double tarifaNoche
	    - int maximoHuespedes : 1
    }
    class Doble {
	    - double tarifaNoche
	    - int maximoHuespedes : 2
    }
    class Suite {
	    - double tarifaNoche
	    - int maximoHuespedes : 4
    }
    class Persona {
	    - int id
	    - str nombre
	    - int edad
	    - str nacionalidad
	    - int numeroContacto
    }
    class Huesped {
	    - Date fechaRegistro
        - list reservasActuales
    }
    class Trabajador {
        - str cargo
    }
    class Reserva {
	    - Habitacion habitacionReserva
	    - Huesped huespedReserva
	    - Date inicioReserva
	    - Date finReserva
        + actualizarEstado() void
        + calcularCosto() double
    }
    Hotel "1" --> "1" Direccion : tiene
    Hotel "1" o-- "1..*" Habitacion : tiene
    Hotel "1" o-- "0..*" Reserva : tiene
    Hotel "1" o-- "1..*" Persona : tiene
    Hotel "1" o-- "1..*" Trabajador : emplea
    Huesped "1" --> "0..*" Reserva : realiza
    Reserva "1" --> "1" Habitacion : tiene
    Reserva "1" --> "1" Huesped : tiene
    Habitacion "1" o-- "0..*" Reserva : historial
    Habitacion <|-- Individual : tipo
    Habitacion <|-- Doble : tipo
    Habitacion <|-- Suite : tipo
    Persona <|-- Huesped : tipo
    Persona <|-- Trabajador : tipo
```
