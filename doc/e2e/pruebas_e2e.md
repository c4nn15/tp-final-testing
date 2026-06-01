# Pruebas End-to-End (E2E)

---

## E2E-01: Flujo completo de alquiler y devolución

**Precondición:** Sistema iniciado, sin datos previos.

| Paso | Acción | Resultado esperado |
|------|--------|--------------------|
| 1 | Ir a "Vehículos" → Registrar: ABC123, Toyota Corolla, 5000 | Mensaje de éxito, aparece en tabla |
| 2 | Ir a "Clientes" → Registrar: 11111111, Juan Perez | Mensaje de éxito, aparece en tabla |
| 3 | Ir a "Alquilar" → Seleccionar ABC123 en tabla, ingresar DNI 11111111, días 3 | Mensaje "Alquiler OK — $15.000,00 estimado" |
| 4 | Verificar que ABC123 ya no aparece en tabla de disponibles | No está listado |
| 5 | Ir a "Devolver" → Seleccionar ABC123 en tabla | Campo PATENTE se autocompleta |
| 6 | Clic "Procesar devolución" | Mensaje "Devolución OK — TOTAL: $15.000,00" |
| 7 | Ir a "Vehículos" → Verificar estado ABC123 | Estado: "disponible" |

**Resultado:** ✅ PASS

---

## E2E-02: Intento de alquiler de vehículo no disponible

| Paso | Acción | Resultado esperado |
|------|--------|--------------------|
| 1 | Registrar vehículo XYZ001 | OK |
| 2 | Registrar cliente A (DNI: 22222222) | OK |
| 3 | Registrar cliente B (DNI: 33333333) | OK |
| 4 | Cliente A alquila XYZ001 por 2 días | OK |
| 5 | Intentar que Cliente B alquile XYZ001 | Error: "no esta disponible" |

**Resultado:** ✅ PASS

---

## E2E-03: Validación de datos inválidos a lo largo del flujo

| Paso | Acción | Resultado esperado |
|------|--------|--------------------|
| 1 | Intentar registrar vehículo sin patente | Error visible |
| 2 | Intentar registrar vehículo con tarifa 0 | Error visible |
| 3 | Intentar alquilar con días = "abc" | Error "Días inválidos" |
| 4 | Intentar alquilar con patente inexistente | Error "no encontrado" |

**Resultado:** ✅ PASS

---

## E2E-04: Navegación completa por todas las secciones

| Paso | Acción | Resultado esperado |
|------|--------|--------------------|
| 1 | Clic en cada sección del menú lateral | Se carga la página correspondiente |
| 2 | Volver a sección anterior | Los datos siguen visibles (no se pierden) |
| 3 | Registrar datos en una sección y verificar en otra | Los datos persisten en memoria durante la sesión |

**Resultado:** ✅ PASS
