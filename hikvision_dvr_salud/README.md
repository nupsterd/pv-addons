# Salud del DVR Hikvision (Portería Virtual)

Lee por ISAPI, solo lectura y a lo sumo una consulta por minuto, la señal, la grabación, el disco y la hora de un DVR Hikvision, y los reporta al backend. Con `verificacion_video` prendida, además baja por RTSP tramos de grabación para la verificación de puertas forzadas y los sube al backend: primero los 2 s de la apertura de una forzada en vivo, con prioridad (fotos rápidas), y después los clips de 30 s. Imagen privada en GHCR (solo `aarch64`).

Desde 0.5.1, los tramos de 2 s también bajan en los canales cuya sesión RTSP el DVR deja abierta (análisis corto de la entrada), y con `eventos_nocturnos` prendida baja un segundo tramo de cada sabotaje para confirmarlo, en sombra, solo para nuestro panel: nada va a la central. Sin opciones nuevas.

Desde 0.5.0, con `eventos_nocturnos` prendida (apagada por defecto; necesita `verificacion_video`), lee el registro `Alarm` del DVR en una ranura extra por ciclo (a lo sumo 6 por hora) y baja por RTSP los tramos de 2 s de los eventos nocturnos y del sabotaje que pide el backend, solo para nuestro panel: nada va a la central. Apagada, se comporta como la 0.4.1.

Desde 0.4.0, con `ronda_virtual` prendida (apagada por defecto), saca la foto de un canal por vez por la única excepción a su lista blanca (`GET /ISAPI/Streaming/channels/<canal>01/picture`, sin query string, dentro del mismo cupo de una consulta por minuto), la analiza en la Pi y manda solo números al backend. **La foto nunca sale de la Pi**: vive en `/tmp`, en RAM. `ronda_banda_superior_px` (56) y `ronda_banda_inferior_px` (72) son las bandas del texto del DVR que no se miden. Apagada, se comporta como la 0.3.0.

Desde 0.3.0 los canales sin cámara van en `excluir_canales`, como texto (`15` o `15,16`); la lista `canales_excluidos` salió de las opciones. Al actualizar desde 0.2.x, cargar `excluir_canales` antes del primer arranque. El detalle está en el `DOCS.md` del add-on.
