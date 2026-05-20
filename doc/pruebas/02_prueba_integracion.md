# Prueba de Integración

Verifican la interacción entre las clases (Agencia + Vehiculo + Cliente + Alquiler).

| ID | Flujo | Pasos | Resultado esperado |
|----|-------|-------|--------------------|
| PI-01 | Registro y búsqueda de vehículo | 1. registrar_vehiculo("AA001","Corolla",5000) 2. buscar_vehiculo("AA001") | Retorna el objeto Vehiculo correcto |
| PI-02 | Registro duplicado de vehículo | Registrar dos veces la misma patente | ValueError en el segundo intento |
| PI-03 | Registro y búsqueda de cliente | 1. registrar_cliente("11111","Juan") 2. buscar_cliente("11111") | Retorna el objeto Cliente correcto |
| PI-04 | Flujo completo de alquiler | 1. Registrar vehículo 2. Registrar cliente 3. alquilar_vehiculo | Vehículo pasa a estado "alquilado", Alquiler en lista |
| PI-05 | Alquilar vehículo no disponible | Intentar alquilar un vehículo ya alquilado | ValueError "no esta disponible" |
| PI-06 | Alquilar con vehículo inexistente | alquilar_vehiculo("ZZZ999",...) | ValueError "no encontrado" |
| PI-07 | Alquilar con cliente inexistente | alquilar_vehiculo("AA001","99999",3) | ValueError "no encontrado" |
| PI-08 | Flujo completo de devolución | Alquilar y luego devolver_vehiculo | Vehículo vuelve a "disponible", alquiler removido de lista |
| PI-09 | Devolver vehículo sin alquiler activo | devolver_vehiculo sobre vehículo disponible | ValueError "no tiene alquiler activo" |
| PI-10 | Costo calculado en integración | Alquilar 5 días a $8500 y devolver | costo = $42500 |
