# Visión (Portería Virtual)

Detector de personas con conteo de línea de una cámara RTSP, en vivo 24/7 o sobre archivos. Manda al backend de Portería Virtual solo los cruces y un latido (sin imágenes); `backend_url`, `backend_secret` y `device_serial` vienen vacíos. Grabador opcional sin recodificar (`grabador`: `apagado`, `ventanas` o `por_cruce`; apagado por defecto), con retención máxima de 30 días. El video no sale de la Pi. Imagen privada en GHCR (solo `aarch64`).
