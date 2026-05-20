# Prueba de Componentes

Verifican que cada clase del modelo funcione correctamente de forma aislada.

| ID | Componente | Entrada | Resultado esperado | Tipo |
|----|-----------|---------|-------------------|------|
| PC-01 | `Vehiculo.__init__` | patente="ABC123", modelo="Toyota", tarifa=5000 | Objeto creado, estado="disponible" | Normal |
| PC-02 | `Vehiculo.__init__` | patente="" | ValueError "La patente no puede estar vacia" | Error |
| PC-03 | `Vehiculo.__init__` | tarifa=-100 | ValueError "La tarifa diaria debe ser un valor positivo" | Error |
| PC-04 | `Vehiculo.marcar_alquilado` | Vehículo disponible | estado="alquilado" | Normal |
| PC-05 | `Vehiculo.marcar_alquilado` | Vehículo ya alquilado | ValueError "ya esta alquilado" | Error |
| PC-06 | `Vehiculo.marcar_disponible` | Vehículo alquilado | estado="disponible" | Normal |
| PC-07 | `Vehiculo.marcar_disponible` | Vehículo ya disponible | ValueError "ya esta disponible" | Error |
| PC-08 | `Cliente.__init__` | dni="12345", nombre="Juan" | Objeto creado correctamente | Normal |
| PC-09 | `Cliente.__init__` | dni="" | ValueError "El DNI no puede estar vacio" | Error |
| PC-10 | `Cliente.__init__` | nombre="" | ValueError "El nombre no puede estar vacio" | Error |
| PC-11 | `Alquiler.calcular_costo` | tarifa=5000, dias=3 | 15000.0 | Normal |
| PC-12 | `Alquiler.__init__` | dias=-1 | ValueError "Los dias deben ser un entero positivo" | Error |
| PC-13 | `Alquiler.__init__` | dias=0 | ValueError "Los dias deben ser un entero positivo" | Error |
| PC-14 | `Alquiler.__init__` | dias="cinco" (string) | ValueError | Error |
