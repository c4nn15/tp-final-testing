# AutoRent — Sistema de Alquiler de Vehículos

## Objetivo del Software
AutoRent es un sistema de escritorio desarrollado en Python que permite gestionar 
el alquiler de vehículos de una agencia. Permite registrar vehículos, clientes, 
procesar alquileres y devoluciones, calculando el costo total automáticamente.

## Requerimientos Funcionales
- RF01: Registrar vehículos con patente, modelo y tarifa diaria.
- RF02: Registrar clientes con DNI y nombre.
- RF03: Alquilar un vehículo disponible a un cliente por N días.
- RF04: Procesar la devolución de un vehículo y calcular el costo total.
- RF05: Listar vehículos (todos, disponibles, alquilados).
- RF06: Listar clientes registrados.
- RF07: Listar alquileres activos.

## Requerimientos No Funcionales
- RNF01: Interfaz gráfica de escritorio (CustomTkinter).
- RNF02: Validación de datos en todos los formularios.
- RNF03: Feedback visual inmediato ante errores o éxitos.
- RNF04: El sistema debe ejecutarse en Python 3.10+.
- RNF05: Navegación por secciones sin recargar la aplicación.

## Tecnologías utilizadas
- Python 3.x
- CustomTkinter (interfaz gráfica)

## Estructura del proyecto
- `modelo.py` — Clases de dominio: Vehiculo, Cliente, Alquiler, Agencia.
- `componentes.py` — Componentes visuales reutilizables (Table, botones, campos).
- `ui.py` — Páginas de la interfaz (Vehículos, Clientes, Alquilar, Devolver).
- `main.py` — Punto de entrada, construcción de la ventana principal.
- `docs/` — Documentación, UML y plan de pruebas.

## Cómo ejecutar
```bash
pip install customtkinter
python main.py
```
