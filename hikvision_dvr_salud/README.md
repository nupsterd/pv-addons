# Salud del DVR Hikvision (Portería Virtual)

Lee por ISAPI, solo lectura y a lo sumo una consulta por minuto, la señal, la grabación, el disco y la hora de un DVR Hikvision, y los reporta al backend. Con `verificacion_video` prendida, además baja por RTSP tramos de grabación solo para la verificación de puertas forzadas y los sube al backend. Imagen privada en GHCR (solo `aarch64`).
