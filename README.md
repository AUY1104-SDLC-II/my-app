🚀 My App - Hola Mundo Web

Esta es nuestra aplicación de ejemplo. Es una página web sencilla que corre dentro de un contenedor Nginx.

🎯 ¿Qué hace este repo?

Demuestra cómo una aplicación puede delegar su proceso de "empaquetado" a una librería externa. Aquí solo nos preocupamos por el código de la web y el Dockerfile.

📦 Componentes

index.html: Nuestra página "¡Hola Mundo!".

Dockerfile: La receta para crear el contenedor.

.github/workflows/deploy.yml: El archivo que "llama" a la librería DevOps.

🔐 Configuración de Seguridad

Para que el despliegue funcione, configuramos en la Organización:

Variable (vars): DOCKER_USERNAME (tu usuario de Docker).

Secret (secrets): DOCKER_PASSWORD (tu Access Token de Docker Hub).

📊 Diagrama de Secuencia

Así es como interactúan los dos repositorios cuando haces un cambio:

sequenceDiagram
participant Dev as 👨‍💻 Desarrollador
participant App as 📁 Repo: My-App
participant Lib as 📚 Repo: DevOps-Library
participant Hub as 🐳 Docker Hub

    Dev->>App: git push
    App->>App: Detecta cambio en 'feat/...'
    App->>Lib: ¡Hey! Usa tu plantilla 'build-push'
    Note over Lib: Se ejecuta en servidores de GitHub
    Lib->>Hub: Sube la imagen construida
    Hub-->>Dev: ✅ Imagen disponible en el registro


⌨️ Comandos para pruebas

Si quieres ver el proceso en vivo o forzar un despliegue:

git commit --allow-empty -m "trigger pipeline": Dispara el flujo sin necesidad de cambiar código.

gh run list: (Si tienes GitHub CLI) Lista los despliegues actuales.

gh run view --log: Permite ver los errores o éxitos en tiempo real desde la consola.

Logro: Integración exitosa con Reusable Workflows