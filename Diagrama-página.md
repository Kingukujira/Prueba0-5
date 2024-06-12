# Diagrama de Secuencia para Crear una Nueva Nota

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    user->>browser: Accede a https://studies.cs.helsinki.fi/exampleapp/spa
    browser->>server: HTTP GET /exampleapp/spa
    server-->>browser: HTML de la aplicación de una sola página (SPA)
    browser-->>server: Solicita recursos adicionales (CSS, JavaScript)
    server-->>browser: Archivos CSS y JavaScript
    browser->>server: Realiza solicitudes AJAX para cargar datos adicionales (JSON)
    server-->>browser: Respuestas JSON con datos adicionales
    browser-->>server: Realiza más solicitudes AJAX según sea necesario
    server-->>browser: Respuestas JSON adicionales
    browser-->>user: Renderiza la aplicación de una sola página (SPA) en el navegador

