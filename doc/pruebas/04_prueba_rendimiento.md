# Prueba de Rendimiento

Evalúan el comportamiento del sistema bajo carga o condiciones extremas.

| ID | Escenario | Método | Métrica objetivo | Resultado esperado |
|----|-----------|--------|-----------------|-------------------|
| PR-01 | Registrar 1000 vehículos | Loop en Agencia.registrar_vehiculo | < 1 segundo total | Sin errores, todos registrados |
| PR-02 | Registrar 1000 clientes | Loop en Agencia.registrar_cliente | < 1 segundo total | Sin errores |
| PR-03 | Listar 1000 vehículos | Agencia.listar_vehiculos() | < 100ms | Retorna lista completa |
| PR-04 | Buscar vehículo en lista de 1000 | buscar_vehiculo() en el peor caso | < 50ms | Encuentra el vehículo correcto |
| PR-05 | 500 alquileres simultáneos (secuencial) | Loop de alquilar_vehiculo | < 2 segundos | Todos registrados correctamente |
| PR-06 | Carga de tabla UI con 100 filas | Table.load() con 100 elementos | Respuesta visual < 1s | Sin freeze de UI |

## Herramienta
Se utiliza el módulo `time` de Python para medir tiempos de ejecución.

```python
import time
inicio = time.time()
# código a medir
fin = time.time()
print(f"Tiempo: {fin - inicio:.4f}s")
```
