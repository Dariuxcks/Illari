# Registro de cambios de ILLARI

Fechas en hora de Ecuador. Todo el código se generó con asistencia de IA (ver `USO_DE_IA.md`).

## 1.4.1 · 13 nov 2026

- Autoría: **BY Anthony Cisneros a.k.a rxn1n** (autor y creador) en la cabecera de la app, en el pie del panel, en los metadatos (`<meta name="author">`) y en las exportaciones CSV/JSON.
- Nuevo `AUTHORS.md` con autor y coautores; `LICENSE` y `README.md` actualizados.
- Publicación en GitHub Pages (`rxn1n.github.io/Illari`) y Vercel.

## 1.4.0 · 13 nov 2026

Reducción medible de las limitaciones restantes, con datos reales:

- **Consenso de 8 modelos de lluvia** (ECMWF, GFS, ICON, GEM, JMA, Météo-France, UKMO y CMA) con dos niveles:
  - **AVISO**, cuando el percentil 75 llega a 30 mm o más;
  - **ALERTA**, cuando el promedio llega a 30 mm o más.
- **Validación del consenso** con pronósticos emitidos un día antes, 1 ago–11 nov 2026, en el Centro de Guayaquil:

  | Pronóstico | Aguaceros fuertes avisados | Falsas alarmas |
  |---|---|---|
  | Un modelo | 5 de 7 | 5 |
  | ALERTA (promedio) | 5 de 7 | 3 |
  | AVISO (percentil 75) | 7 de 7 | 14 |

  El 26 oct el AVISO pronosticaba 54 mm y cayeron 58.
- **Área quemada solo en vegetación natural** (MODIS): en el Casitagua bajó de 476 a 402 ha, frente a unas 300 ha reportadas.

## 1.3.0 · 13 nov 2026

Alineado con la página oficial del desafío (objetivos y recursos) y con la Guía de usuario de datos NISAR de ASF.

- **Archivo SAR de la ciudad**, desde la API pública de ASF, la misma de Vertex y sin cuenta:
  - NISAR, Sentinel-1, ALOS PALSAR, UAVSAR y RADARSAT-1, con línea de tiempo 2006–2026, enlaces a Vertex y Earthdata Search, y vistas HH y HV de la última pasada NISAR.
  - Hallazgo: NASA voló el radar UAVSAR sobre Guayaquil en 2013–2015.
- **Agencias socias del desafío** (CONAE SAOCOM; CSA RCM y RADARSAT-1): condiciones de acceso y enlaces.
- **¿Por qué se ve así?:** física del radar (HH, HV, doble rebote, dispersión de volumen) y factores humanos.
  - La cobertura del suelo de MODIS IGBP 2024 muestra dónde cayó el cambio.
  - La población GPW 2020 da el número mínimo de personas en zonas con agua nueva.
- **Serie temporal NISAR** de una misma órbita, con animación ▶ de todas sus pasadas.
- Las fechas BETA (sin calibrar) no se comparan con PROVISIONAL o VALIDATED, como advierte ASF.
- **Recursos oficiales del desafío** enlazados en el método.
- Resultado real: tras la tormenta del 26 oct hubo 36,9 km² de agua abierta nueva (Sentinel-1):
  - 37 % cultivos, 28 % humedales, 3 % zona urbana;
  - al menos 15 800 personas en esas zonas.

## 1.2.0 · 12 nov 2026, noche

Objetivo: resolver técnicamente las limitaciones de la ficha técnica, no solo describirlas. Todo se verificó contra los servidores reales de NASA y Open-Meteo.

- **Confirmación multisensor** con productos clasificados y validados de NASA, sin clave (GIBS):
  - **OPERA DSWx-S1 (agua, radar Sentinel-1):** cada 2–6 días; serie de agua abierta y agua nueva por sector.
  - **OPERA DSWx-HLS (agua, óptico):** cuando no hay nubes.
  - **OPERA DIST-ALERT (pérdida de vegetación, 30 m)** y **focos VIIRS** para Quito.
  - Las clases se leen con la paleta oficial, sin interpretar tonos. Nueva capa «Confirmación OPERA».
- **Validación retrospectiva de los índices:** pronósticos emitidos en el pasado (Open-Meteo Previous Runs e Historical Forecast) frente a lo ocurrido.
  - Guayaquil: aciertos y falsas alarmas de lluvia fuerte.
  - Quito: FWI en días con y sin focos VIIRS, y umbral local calibrado.
- Resultado real, 12 nov: la tormenta del 26 oct aumentó el agua abierta de Guayaquil de 212 a 232 km² (Sentinel-1, 24 → 28 oct). En Quito, el FWI mediano fue 3,7 en días con fuego frente a 0,2 sin fuego.

## 1.1.0 · 12 nov 2026 (antes del inicio del hackathon)

Verificado contra los servidores reales de NASA desde un navegador:
- CMR y GIBS responden con CORS, también desde origen `null` (abrir el archivo con doble clic).
- GIBS publica el mosaico diario `NISAR_L2_Geocoded_Polarimetric_Covariance` desde el 29 oct 2025. **No** publica la capa de 12 días por WMS, así que se eliminó.

Cambios:
- **Comparador válido:** solo se comparan pares con el mismo track, la misma dirección y el mismo modo de polarización. Si no, la comparación se bloquea y se explica el motivo. La huella de cada pasada en CMR excluye órbitas que cubren menos de media ciudad.
- **Ficha del par:** muestra fecha y hora UTC, track, dirección, frame, polarización, colección y cobertura de las dos fechas.
- **Estado de las fuentes:** cada consulta externa queda registrada con su resultado, código HTTP y hora. El registro se exporta en la escena `.json`.
- **Simulación siempre identificada:** banner, sello del mapa, marca de agua "SIMULACIÓN" (también en el PNG exportado), CSV, JSON y aviso con botón para reconectar.
- **Agua recalibrada** con la paleta real de NASA: el agua tranquila se ve oscura y azulada, no azul brillante.
- **Áreas comunicadas como aproximaciones (≈):** se indica que no están calibradas y que falta validación independiente. Los índices del modo Estimado se presentan como exploratorios, no como probabilidades.
- Avisos cuando la pasada posterior llega varios días después del evento o cuando las fechas están muy separadas.

## 1.0.0 · 12 nov 2026

- Unión de GroundWatch NISAR y Vigía Ecuador: Observado (radar NISAR) y Estimado (pronóstico), para Guayaquil y Quito.
