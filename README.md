# Orientation-Aware Residential Cooling Loads (1D Implicit FVM)

> Modelo 1D en volúmenes finitos (implícito) para cargas de enfriamiento residenciales con radiación solar por orientación.

## ¿Qué hace?

* Resuelve conducción transitoria 1D en paredes y techo (esquema implícito estable).
* Acopla convección exterior/interior, radiación LW linealizada y ganancia solar (directa + difusa) según orientación N/E/S/O.
* A partir de clima horario, entrega temperaturas de superficie, flujos de calor al recinto y energía de enfriamiento.
* Convierte kWh térmicos a kWh eléctricos vía COP y a costo con una tarifa.

## ¿Para qué sirve?

* Comparar orientaciones, materiales, setpoints y COP.
* Generar figuras y tablas mensuales/anuales listas para informes.
* Base reproducible y ligera para docencia e investigación.

## Entradas esperadas

* Archivos CSV por superficie (pared_1, pared_2, pared_3, pared_4, techo) con fecha-hora, temperatura ambiente, cielo efectivo, radiación directa y difusa.
* Parámetros físicos y de operación: geometría (Lx, Ly, h, espesor), propiedades (k, ρ, c), coeficientes de convección, emisividad/absorptancia, COP, tarifa y setpoint interior.

## Salidas

* Series horarias de flujo de calor hacia el recinto por superficie y total.
* Tablas: consumo mensual y anual (kWh térmicos, kWh eléctricos, costo).
* Figuras: temperaturas interior/exterior, radiación por orientación, flujo y carga de enfriamiento.

## Supuestos clave

* Transferencia 1D en cerramientos opacos homogéneos.
* Radiación LW linealizada en exterior e interior.
* “Solo enfriamiento”: se contabilizan horas con calor hacia adentro (positivo).
* Sistema lineal tridiagonal resuelto con algoritmo de Thomas.

## Perillas de configuración

* Geometría: Lx, Ly, altura, espesor, número de nodos.
* Materiales: k, ρ, c.
* Fronteras: h_ext, h_int, emisividad, absorptancia, cielo efectivo.
* Operación: setpoint interior, COP, tarifa, paso temporal interno.

## Convenciones

* Signo positivo = calor hacia el recinto (carga de enfriamiento).
* Orientaciones: 1=Norte, 2=Este, 3=Sur, 4=Oeste (ajustable al dataset).

## Estructura sugerida del repo

* data/: clima horario por superficie
* src/: núcleo FVM, postproceso y utilidades de I/O
* notebooks/: reproducción de figuras y tablas
* figures/: gráficas generadas
* results/: tablas CSV/LaTeX
* README.md, requirements.txt, LICENSE

## Licencia

MIT.

## Cita sugerida

Juan Riascos, Thomas Martinod, Fernando Londoño, “Orientation-Aware Residential Cooling Loads (1D Implicit FVM)”, 2025.
