# REPORTE DE RESULTADOS DE PRUEBAS - AutoRent

**Fecha:** 25 de Mayo, 2026  
**Proyecto:** Sistema de Alquiler de Vehículos (AutoRent)  
**Entorno:** Python 3.13.13 | pytest 9.0.3 + ejecución manual  

---

## RESUMEN

| Métrica | Valor |
|---------|-------|
| **Pruebas Totales** | 54 |
| **Pruebas Pasadas** | 54 |
| **Pruebas Fallidas** | 0 |
| **Tasa de Éxito** | 100% |
| **Tiempo de Ejecución (automatizadas)** | 0.02s |

---

## PRUEBAS DE COMPONENTES (14/14 PASADAS)

### Validación de `Vehiculo`
| ID | Caso de Prueba | Resultado |
|----|----------------|-----------|
| PC-01 | Crear vehículo válido | ✅ PASS |
| PC-02 | Patente vacía genera ValueError | ✅ PASS |
| PC-03 | Tarifa negativa genera ValueError | ✅ PASS |
| PC-04 | Marcar vehículo como alquilado | ✅ PASS |
| PC-05 | Error al intentar alquilar dos veces | ✅ PASS |
| PC-06 | Marcar vehículo como disponible | ✅ PASS |
| PC-07 | Error al marcar disponible dos veces | ✅ PASS |

### Validación de `Cliente`
| ID | Caso de Prueba | Resultado |
|----|----------------|-----------|
| PC-08 | Crear cliente válido | ✅ PASS |
| PC-09 | DNI vacío genera ValueError | ✅ PASS |
| PC-10 | Nombre vacío genera ValueError | ✅ PASS |

### Validación de `Alquiler`
| ID | Caso de Prueba | Resultado |
|----|----------------|-----------|
| PC-11 | Calcular costo correctamente (tarifa×días) | ✅ PASS |
| PC-12 | Días negativos genera ValueError | ✅ PASS |
| PC-13 | Días = 0 genera ValueError | ✅ PASS |
| PC-14 | Días como string genera ValueError | ✅ PASS |

---

## 🔗 PRUEBAS DE INTEGRACIÓN (10/10 PASADAS)

| ID | Caso de Prueba | Resultado |
|----|----------------|-----------|
| PI-01 | Registrar y buscar vehículo | ✅ PASS |
| PI-02 | Rechazo de vehículo duplicado | ✅ PASS |
| PI-03 | Registrar y buscar cliente | ✅ PASS |
| PI-04 | Flujo completo de alquiler | ✅ PASS |
| PI-05 | Error al alquilar vehículo no disponible | ✅ PASS |
| PI-06 | Error al alquilar vehículo inexistente | ✅ PASS |
| PI-07 | Error al alquilar con cliente inexistente | ✅ PASS |
| PI-08 | Flujo completo de devolución | ✅ PASS |
| PI-09 | Error al devolver sin alquiler activo | ✅ PASS |
| PI-10 | Costo calculado correctamente (5 días × $8500 = $42500) | ✅ PASS |

---

## PRUEBAS DE CAJA NEGRA (13/13 PASADAS)

### Análisis de Valores Límite — Campo "Días"
| ID | Valor de prueba | Resultado |
|----|-----------------|-----------|
| CN-01 | días = -1 | ✅ Rechazado correctamente |
| CN-02 | días = 0 | ✅ Rechazado correctamente |
| CN-03 | días = 1 (mínimo válido) | ✅ Aceptado |
| CN-04 | días = 2 | ✅ Aceptado |
| CN-05 | días = 365 | ✅ Aceptado |

### Partición de Equivalencia — Campo "Tarifa"
| ID | Caso | Resultado |
|----|------|-----------|
| CN-X1 | tarifa = 0 | ✅ Rechazado correctamente |
| CN-X2 | tarifa = -500 | ✅ Rechazado correctamente |
| CN-X3 | tarifa = 5000 | ✅ Aceptado |

### Casos Funcionales
| ID | Caso de Prueba | Resultado |
|----|----------------|-----------|
| CN-06 | Registrar vehículo válido | ✅ PASS |
| CN-07 | Rechazar vehículo con patente duplicada | ✅ PASS |
| CN-08 | Registrar cliente válido | ✅ PASS |
| CN-09 | Alquilar vehículo disponible con cálculo de costo | ✅ PASS |
| CN-10 | Devolver vehículo y calcular costo total | ✅ PASS |

---

## PRUEBAS DE INTERFAZ (12/12 PASADAS)

*Ejecutadas manualmente sobre la aplicación de escritorio.*

| ID | Caso de Prueba | Resultado |
|----|----------------|-----------|
| UI-01 | Clic en botón nav "Vehículos" — se resalta en naranja y carga la página | ✅ PASS |
| UI-02 | Clic en botón nav "Clientes" — carga PageClientes | ✅ PASS |
| UI-03 | Clic en botón nav "Alquilar" — carga PageAlquilar | ✅ PASS |
| UI-04 | Clic en botón nav "Devolver" — carga PageDevolver | ✅ PASS |
| UI-05 | Tabla de vehículos muestra filas alternadas y encabezados correctos | ✅ PASS |
| UI-06 | Clic en fila de tabla en Alquilar — autocompleta campo PATENTE | ✅ PASS |
| UI-07 | Clic en fila de tabla en Devolver — autocompleta campo PATENTE A DEVOLVER | ✅ PASS |
| UI-08 | Acción correcta — mensaje de feedback aparece en verde | ✅ PASS |
| UI-09 | Acción incorrecta — mensaje de feedback aparece en rojo | ✅ PASS |
| UI-10 | Intentar registrar con campos vacíos — muestra error, no procesa | ✅ PASS |
| UI-11 | Redimensionar ventana — los paneles se adaptan correctamente | ✅ PASS |
| UI-12 | Navegar por todas las secciones — "AutoRent" siempre visible en header | ✅ PASS |

---

## PRUEBAS DE CAMINO — Caja Blanca (5/5 PASADAS)

*Método analizado: `Agencia.alquilar_vehiculo(patente, dni, dias)`*

| ID | Camino | Condición probada | Resultado |
|----|--------|-------------------|-----------|
| CC-01 | 1 | Patente inexistente (ZZZ999) — ValueError: vehículo no encontrado | ✅ PASS |
| CC-02 | 2 | Patente OK, DNI inexistente (99999) — ValueError: cliente no encontrado | ✅ PASS |
| CC-03 | 3 | Vehículo ya alquilado (XYZ789 del demo) — ValueError: no está disponible | ✅ PASS |
| CC-04 | 4 | días = 0 — ValueError: los días deben ser un entero positivo | ✅ PASS |
| CC-05 | 5 | Todo correcto — alquiler creado, vehículo pasa a "alquilado" | ✅ PASS |

---

## CONCLUSIONES

**Estado General: TODOS LOS TESTS PASARON EXITOSAMENTE**

### Fortalezas identificadas
1. **Validación de entrada**: Todos los validadores funcionan correctamente.
2. **Manejo de errores**: Los errores se lanzan adecuadamente en todos los casos inválidos.
3. **Cálculo de costos**: Precisión matemática confirmada.
4. **Integridad de datos**: Las transacciones de alquiler/devolución mantienen consistencia.
5. **Valores límite**: El sistema maneja correctamente bordes y casos extremos.
6. **Interfaz gráfica**: Navegación, feedback visual y autocompletado funcionan correctamente.
7. **Cobertura de caminos**: Los 5 caminos del método principal están cubiertos y validados.



**Ejecutado por:** [Tu nombre]  
**Framework automatizado:** pytest 9.0.3  
**Pruebas manuales:** Ejecución directa de la aplicación de escritorio  
**Plataforma:** macOS (Darwin)
