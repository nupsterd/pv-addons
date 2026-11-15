# Salud del DVR Hikvision (Portería Virtual)

Lee por ISAPI, solo lectura y a lo sumo una consulta por minuto, la señal, la grabación, el disco y la hora de un DVR Hikvision, y los reporta al backend. Con `verificacion_video` prendida, además baja por RTSP tramos de grabación solo para la verificación de puertas forzadas y los sube al backend: primero los 2 s de la apertura de una forzada en vivo, con prioridad (fotos rápidas), y después los clips de 30 s. Imagen privada en GHCR (solo `aarch64`).

Desde 0.3.0 los canales sin cámara van en `excluir_canales`, como texto (`15` o `15,16`); la lista `canales_excluidos` salió de las opciones. Al actualizar desde 0.2.x, cargar `excluir_canales` antes del primer arranque. El detalle está en el `DOCS.md` del add-on.
