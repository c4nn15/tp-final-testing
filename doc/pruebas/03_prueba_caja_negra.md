# Prueba de Caja Negra

Se prueba el sistema desde la perspectiva del usuario, sin conocer la implementación interna.
Se usan técnicas de Partición de Equivalencia y Análisis de Valores Límite.

## Partición de Equivalencia — Campo "Días"

| Partición | Rango | Ejemplo | Resultado esperado |
|-----------|-------|---------|-------------------|
| Inválida negativa | días < 0 | -1 | Rechazo con error |
| Inválida cero | días = 0 | 0 | Rechazo con error |
| Válida | días >= 1 | 5 | Aceptado |
| Inválida (no entero) | string | "abc" | Rechazo con error |

## Análisis de Valores Límite — Campo "Días"

| ID | Valor | Resultado esperado |
|----|-------|--------------------|
| CN-01 | días = -1 | Error |
| CN-02 | días = 0 | Error |
| CN-03 | días = 1 | Aceptado (mínimo válido) |
| CN-04 | días = 2 | Aceptado |
| CN-05 | días = 365 | Aceptado |

## Partición de Equivalencia — Campo "Tarifa"

| Partición | Ejemplo | Resultado esperado |
|-----------|---------|-------------------|
| Inválida (cero) | 0 | Error |
| Inválida (negativa) | -500 | Error |
| Válida | 5000 | Aceptado |
| Inválida (texto) | "caro" | Error de conversión |

## Casos funcionales de caja negra

| ID | Acción del usuario | Datos | Resultado visible esperado |
|----|-------------------|-------|---------------------------|
| CN-06 | Registrar vehículo válido | ABC123, Toyota, 5000 | Mensaje de éxito, aparece en tabla |
| CN-07 | Registrar vehículo con patente duplicada | ABC123 (ya existe) | Mensaje de error |
| CN-08 | Registrar cliente válido | 99999, Pedro | Mensaje de éxito |
| CN-09 | Alquilar vehículo disponible | Datos correctos | Mensaje "Alquiler OK" con costo |
| CN-10 | Devolver vehículo | Patente correcta | Mensaje "Devolución OK" con total |
