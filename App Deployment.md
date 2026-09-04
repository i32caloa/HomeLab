# Despliegue de Aplicaciones

Toda la infraestructura de servicios del servidor funciona bajo contenedores Docker. Esto evita instalar dependencias directamente en el sistema operativo, manteniendo la Raspberry Pi limpia y asegurando que los servicios no interfieran entre sí.

El despliegue se gestiona de forma centralizada mediante un único archivo `docker-compose.yml`

## Multimedia y Entretenimiento

* **Jellyfin (Puerto 8096):** El núcleo multimedia. Indexa y reproduce por streaming todo el contenido de vídeo. Cuenta con decodificación por hardware habilitada.
* **Komga (Puerto 25600):** Servidor dedicado a la gestión y lectura de bibliotecas de cómics y manga.
* **RomM (Puerto 8070):** Gestor de bibliotecas de videojuegos retro accesible desde navegador. Utiliza un contenedor auxiliar MariaDB (`romm-db`).

## Monitorización y Cuadros de Mando

* **Homepage (Puerto 8088):** Dashboard principal del Homelab. Agrupa enlaces a todos los servicios e integra APIs internas para mostrar métricas en tiempo real (espacio en disco, descargas activas, estado de red).
* **Jellystat (Puerto 3000):** Analítica avanzada para Jellyfin. Registra historiales de reproducción y actividad de usuarios. Requiere un contenedor PostgreSQL (`jellystat-db`).
* **Uptime Kuma (Puerto 3001):** Sistema de vigilancia. Realiza comprobaciones constantes a los puertos locales y alerta si algún contenedor deja de responder.

## Administración y Nube Personal

* **Portainer (Puerto 9443):** Interfaz gráfica (GUI) para administrar el motor de Docker, reiniciar contenedores caídos y revisar logs sin necesidad de terminal.
* **Nginx Proxy Manager (Puertos 81 / 80 / 443):** Panel para la creación de proxies inversos y obtención de certificados SSL.
* **Nextcloud (Puerto 8080):** Nube personal para sincronización de archivos y copias de seguridad de dispositivos móviles. Utiliza un contenedor auxiliar (`nextcloud_db`).
* **jfa-go (Puerto 8056):** Gestor de cuentas externas. Permite generar enlaces de invitación para que familiares o amigos creen sus propios usuarios en Jellyfin con restricciones de tiempo y contenido.

---
**Nota sobre el rendimiento:** Para evitar cuellos de botella en las operaciones de I/O del SSD tras un reinicio físico, se recomienda esperar 5 minutos a que servicios pesados como las bases de datos terminen de inicializarse antes de comprobar los *healthchecks*.
