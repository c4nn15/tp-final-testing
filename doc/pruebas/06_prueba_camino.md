# Prueba de Camino (Caja Blanca)

Se analizan los caminos posibles dentro del código del método `alquilar_vehiculo` de `Agencia`.

---

## Método analizado: `Agencia.alquilar_vehiculo(patente, dni, dias)`

### Caminos identificados

```
Camino 1: buscar_vehiculo → None → raise ValueError (vehículo no encontrado)
Camino 2: buscar_vehiculo → OK → buscar_cliente → None → raise ValueError (cliente no encontrado)
Camino 3: buscar_vehiculo → OK → buscar_cliente → OK → not disponible → raise ValueError
Camino 4: buscar_vehiculo → OK → buscar_cliente → OK → disponible → dias inválidos → raise ValueError
Camino 5: buscar_vehiculo → OK → buscar_cliente → OK → disponible → dias OK → Alquiler creado ✓
```

### Casos de prueba por camino

| ID | Camino | Condición | Resultado esperado |
|----|--------|----------|--------------------|
| CC-01 | 1 | Patente no existe en el sistema | ValueError: "Vehiculo 'ZZZ999' no encontrado." |
| CC-02 | 2 | Patente OK, DNI no existe en el sistema | ValueError: "Cliente con DNI '99999' no encontrado." |
| CC-03 | 3 | Ambos existen, pero el vehículo ya está alquilado | ValueError: "El vehiculo 'ABC123' no esta disponible." |
| CC-04 | 4 | Vehículo y cliente OK, pero dias=0 | ValueError: "Los dias deben ser un entero positivo." |
| CC-05 | 5 | Vehículo disponible, cliente existe, dias=3 | Alquiler creado correctamente, vehículo pasa a "alquilado" |

---

## Complejidad ciclomática

- **Número de caminos independientes:** 5
- **Fórmula:** CC = E − N + 2 (aristas − nodos + 2)
- Cada camino corresponde a una condición de guarda distinta dentro del método.
