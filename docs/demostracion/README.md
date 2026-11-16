# Cómo demostrar el caso NISAR de Guayaquil

[Abrir el visor interactivo](https://dariuxcks.github.io/Illari/docs/demostracion/visor.html) · [Descargar la presentación](ILLARI_guia_demostracion.pptx) · [Ver el mapa](mapa.png) · [Archivo del visor para uso sin conexión](visor.html)

*Dancing with the SARs* propone utilizar radar NISAR en una aplicación interactiva para seguir y visualizar cambios en la superficie terrestre. En Guayaquil, ILLARI permite examinar dónde y cuánto cambió la señal que regresó al radar entre dos pasadas separadas por 12 días. La atribución de esos cambios a un fenómeno concreto sigue abierta. [Enunciado publicado por la sede de Sonoma](https://edeon.sonoma.edu/nasaspaceapps-26/index.html)

## Qué puede comprobar el jurado

| Objetivo | Evidencia que se puede abrir | Alcance del caso |
|---|---|---|
| Utilizar observaciones NISAR reales | La ficha del par identifica dos productos GCOV PROVISIONAL del 7 y 19 de octubre de 2026, con track 112 descendente, frame 090, modo 4005 y polarización DHDH. [Adquisiciones y procedencia](../../CASO_NISAR_GUAYAQUIL.md) | El tablero en vivo usa mosaicos diarios GIBS en falso color. El visor del caso usa los valores calibrados HH y HV extraídos de los GCOV. |
| Comparar la misma zona entre dos fechas | El divisor conserva el encuadre al alternar ambas fechas. Los cuatro recortes comparten una malla de 1335 × 1327 píxeles de 10 m en UTM 17S. [Visor](https://dariuxcks.github.io/Illari/docs/demostracion/visor.html) | Las vistas de pantalla tienen resolución reducida. El cálculo usa la malla original del recorte urbano. |
| Localizar y cuantificar cambios | El mapa de diferencia resta, píxel por píxel, la señal del 7 a la del 19. Las medianas del cambio son **+0,23 dB en HH** y **+0,13 dB en HV**. [Mapa de ambas polarizaciones](mapa.png) | Los valores resumen el cambio de señal dentro del recorte. Determinar la causa física exige otras observaciones. |

## Demostración de 90 segundos

| Tiempo | Qué hacer | Qué señalar en pantalla |
|---|---|---|
| 0–20 s | En el tablero, elegir **Guayaquil → Observado → Situación actual**. Seleccionar **Antes 7 oct. 2026** y **Después 19 oct. 2026**, ambos **T112 D · F090 · DHDH · PROVISIONAL**. | Mostrar las fechas y el frame que hacen identificable el par. [Tablero público](https://dariuxcks.github.io/Illari/) |
| 20–45 s | Abrir el visor del caso, pulsar **HH** y mover **Posición del divisor** sobre un mismo tramo de la ribera. | El panel izquierdo muestra las dos pasadas con idéntica escala. En el derecho, el azul indica menor retorno del radar el día 19 y el naranja indica mayor retorno. |
| 45–65 s | Pulsar **HV**. Leer el valor debajo del mapa y volver a **HH** para compararlo. | La mediana cambia de **+0,13** a **+0,23 dB**. Una mediana cercana a cero puede coexistir con aumentos y disminuciones locales. |
| 65–90 s | Cerrar con la fecha de la tormenta y el resultado del contraste con OPERA. | Ambas pasadas preceden al **26 de octubre**. En el cruce exploratorio coincidieron **7 de 1413 celdas** clasificadas por OPERA como agua abierta nueva aparente. Esa coincidencia limitada deja pendiente validar la detección de inundaciones. [Método y resultados](../../CASO_NISAR_OPERA_GUAYAQUIL.md) |

## Prioridades del equipo

1. **Cerrar la entrega formal.** La persona responsable del equipo debe comprobar la ficha **Team → Project**, enlazar el tablero y el visor, citar los datos NASA, declarar la asistencia de Claude y ChatGPT y conservar el comprobante del envío. El plazo anunciado fue el **15 de noviembre de 2026 a las 23:59**, en la zona horaria asignada al equipo. La documentación registra calibración el 12 de noviembre. Corresponde a la sede resolver cualquier duda sobre la cronología y la elegibilidad. [Indicaciones del equipo organizador](https://github.com/nasa/spaceapps/discussions/1916) · [Declaración del proyecto](../../USO_DE_IA.md)
2. **Ensayar el recorrido desde el enlace público.** Verificar ambas polarizaciones y las dos medianas, y tener a mano el mapa y el HTML descargado para presentar si falla la red. El modo Estimado y sus pronósticos pueden presentarse aparte.
3. **Validar un episodio de inundación.** Elegir un evento documentado con adquisiciones compatibles anteriores y posteriores, comparar con los rásteres de agua WTR originales de OPERA, controlar el desfase de fechas y confrontar el resultado con una referencia independiente. Esa evaluación permitiría estimar aciertos, omisiones y falsas alarmas. [Contraste exploratorio ya realizado](../../CASO_NISAR_OPERA_GUAYAQUIL.md)

Datos de NASA–ISRO NISAR distribuidos por ASF DAAC. Ideación y dirección del proyecto, Darío Proaño. Diseño y código de ILLARI, Anthony Cisneros (rxn1n). Esta guía se preparó con asistencia de ChatGPT.
