# Diagrama de Secuencia para Crear una Nueva Nota

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    Note over user, browser: Usuario escribe una nota y hace clic en "Save"

    user->>browser: Click en "Save"         // Usuario hace clic en el botón "Save"
    browser->>server: HTTP POST /exampleapp/new_note con contenido de la nota   // Navegador envía una solicitud POST con la nueva nota al servidor
    server-->>browser: Respuesta HTTP (Redirección)   // El servidor responde con una redirección

    Note over browser: El navegador redirige a /exampleapp/notes   // Navegador se redirige a la página de notas

    browser->>server: HTTP GET /exampleapp/notes   // Navegador solicita la página de notas
    server-->>browser: HTML de la página de notas   // El servidor responde con el HTML de la página de notas

    Note over browser: El navegador carga el HTML y solicita los recursos adicionales (CSS, JavaScript)

    browser->>server: HTTP GET /exampleapp/main.css   // Navegador solicita el archivo CSS
    server-->>browser: main.css   // El servidor responde con el archivo CSS

    browser->>server: HTTP GET /exampleapp/main.js   // Navegador solicita el archivo JavaScript
    server-->>browser: main.js   // El servidor responde con el archivo JavaScript

    Note over browser: El navegador ejecuta main.js

    browser->>server: HTTP GET /exampleapp/data.json   // Navegador solicita los datos JSON
    server-->>browser: data.json   // El servidor responde con los datos JSON

    Note over browser: El navegador procesa data.json y actualiza el DOM para mostrar las notas, incluida la nueva nota
