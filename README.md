# Laboratorio 09: Cloud Storage (S3)

**Estudiante:** Naomi Sanchez  
**Curso:** Desarrollo de Soluciones en la Nube  
**Tecnologías:** Amazon S3, AWS CLI, Node.js (Express 5), AWS SDK v3, HTML5 / JavaScript ES6  

---

## 📌 Descripción del Proyecto

Este laboratorio cubre la configuración, administración y desarrollo de aplicaciones conectadas a **Amazon S3** (Simple Storage Service), aplicando buenas prácticas de seguridad, control de acceso mediante IAM, políticas de ciclo de vida, versionamiento y transferencias seguras mediante **Presigned URLs**.

---

## 📁 Estructura del Proyecto

```text
lab-09-s3-aws/
├── backend/
│   ├── .env                 # Variables de entorno (credenciales AWS, puerto, bucket)
│   ├── .gitignore           # Archivos ignorados por Git
│   ├── package.json         # Dependencias de Node.js (Express 5, AWS SDK v3)
│   └── server.js            # API REST con endpoints para Presigned URLs y operaciones S3
├── frontend/
│   ├── index.html           # Interfaz gráfica para carga y galería de imágenes
│   └── app.js               # Lógica del cliente, validaciones y subida directa (PUT) a S3
├── informe/
│   ├── ejercicio1.md        # Documentación de configuración básica y AWS CLI
│   ├── ejercicio2.md        # Seguridad, IAM y políticas de bucket (HTTPS)
│   ├── ejercicio3.md        # Versionamiento, Delete Markers y Reglas de Ciclo de Vida
│   └── ejercicio4.md        # Monitoreo, métricas y aplicación web con Presigned URLs
├── capturas/                # Evidencias fotográficas de cada ejercicio
└── README.md                # Documentación principal del repositorio

🚀 Resumen de Ejercicios Realizados
Ejercicio 1: Configuración Inicial del Bucket y CLI
Creación del bucket privado lab-09-sanchez-20261014 en la región us-east-1.

Configuración de perfiles y credenciales en AWS CLI v1.

Ejecución de operaciones CRUD básicas sobre S3 mediante consola de comandos (aws s3 cp, aws s3 ls, aws s3 rm).

Ejercicio 2: Control de Acceso y Encriptación
Creación del usuario IAM restringido app-imagenes-user con política de mínimo privilegio (PoliticaAccesoBucketImagenes).

Aplicación de política de bucket (Bucket Policy) para denegar solicitudes HTTP no seguras obligando el uso exclusivo de HTTPS (aws:SecureTransport).

Verificación y validación de encriptación en el lado del servidor SSE-S3 (AES256).

Ejercicio 3: Versionamiento, Ciclo de Vida y Resiliencia
Habilitación del Versionado de Objetos en el bucket.

Pruebas de sobreescritura progresiva y demostración de resiliencia ante borrados accidentales mediante Marcadores de Eliminación (Delete Markers).

Creación de la regla de ciclo de vida regla-imagenes-antiguas sobre el prefijo originales/:

Versión Actual: Transición a Standard-IA (30 días) -> Glacier Instant Retrieval (90 días).

Versiones No Actuales: Transición a Glacier Deep Archive (60 días).

Expiración Permanente: Eliminación definitiva tras 365 días.

Ejercicio 4: Aplicación Web con Presigned URLs & Monitoreo
Configuración de reglas CORS en Amazon S3 para permitir peticiones PUT y GET directas desde el navegador web.

Desarrollo de un backend en Node.js (Express 5) que emite Presigned URLs temporales (5 min para subida, 15 min para descarga/visualización) manteniendo las credenciales de AWS protegidas en el servidor.

Creación de interfaz web interactiva con validación de archivos en cliente y servidor (solo JPG, PNG, WEBP < 5 MB).

Configuración de S3 Event Notifications y análisis operacional mediante métricas de Amazon CloudWatch y Storage Lens.

🛠️ Instrucciones de Ejecución (Aplicación Web)
1. Iniciar el Backend
Bash
cd backend
npm install
node server.js
El servidor se ejecutará en http://localhost:3000.

2. Iniciar el Frontend
Abre el archivo frontend/index.html en tu navegador o ejecútalo con la extensión Live Server de VS Code (http://127.0.0.1:5500).
