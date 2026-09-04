# Homelab - Raspberry Pi 5 Server

Bienvenido al repositorio de mi servidor doméstico. Este proyecto documenta el montaje, configuración y despliegue de un entorno de servicios 100% basado en contenedores Docker sobre una Raspberry Pi 5.

El servidor está diseñado para ser eficiente (sin entorno de escritorio), accesible en remoto mediante túneles virtuales y fácil de restaurar en caso de fallos de hardware.

## Índice de Documentación

La documentación está dividida en los siguientes módulos:

1. [**Hardware de la Raspberry Pi**](Raspberry%20Pi%20Hardware.md)
   * Especificaciones de la placa, almacenamiento SSD y gestión de energía.
2. [**Software Base y Herramientas**](Raspberry%20Pi%20Software.md)
   * Flasheo de Raspberry Pi OS Lite (64-bit), habilitación de SSH, configuración de Zsh como intérprete de comandos y monitorización con Bottom.
3. [**Configuración de Red y Acceso Remoto**](Network%20Configuration.md)
   * Asignación de IP estática local e implementación de Tailscale para acceso seguro desde fuera de casa.
4. [**Despliegue de Aplicaciones (Docker)**](App%20Deployment.md)
   * Arquitectura del `docker-compose.yml` maestro y desglose de todos los servicios alojados (Multimedia, Descargas, Nube y Monitorización).
5. [**Guía de Solución de Problemas (Troubleshooting)**](Troubleshooting.md)
   * Protocolos de rescate ante bloqueos de arranque (`USB-MSD Timeout`), bucles en contenedores por cortes de luz y errores de conexión SFTP.

## 🛠️ Stack Tecnológico Principal

* **Sistema Operativo:** Raspberry Pi OS Lite (Debian)
* **Contenedores:** Docker & Docker Compose
* **Terminal:** Zsh + SSH
* **Red Virtual:** Tailscale
* **Proxy Inverso:** Nginx Proxy Manager

---
*Mantenido por Antonio Cañete López.*
