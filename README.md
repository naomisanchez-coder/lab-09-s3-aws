Laboratorio 09: Cloud Storage (S3)

Estudiante: Naomi Sanchez

Curso: Desarrollo de Soluciones en la Nube

Tecnologías: Amazon S3, AWS CLI, Node.js (Express 5), AWS SDK v3, HTML5 / JavaScript ES6

📌 Descripción del Proyecto

Este laboratorio cubre la configuración, administración y desarrollo de aplicaciones conectadas a Amazon S3 (Simple Storage Service), implementando buenas prácticas de seguridad, control de acceso mediante IAM, políticas de ciclo de vida, versionamiento y transferencias seguras mediante Presigned URLs.

📁 Estructura del Proyecto

lab-09-s3-aws/
├── backend/                  # Servidor API REST con Express 5 y AWS SDK v3
│   ├── .env                  # Variables de entorno (región, bucket y credenciales IAM)
│   ├── .gitignore            # Archivos ignorados por Git
│   ├── package.json          # Dependencias (express, cors, @aws-sdk/client-s3, etc.)
│   └── server.js             # Endpoints para generación de Presigned URLs y operaciones S3
├── frontend/                 # Interfaz de usuario estática
│   ├── index.html            # UI principal de la Galería Fotográfica
│   └── app.js                # Lógica del cliente, validaciones y subida directa a S3 (PUT)
├── capturas/                 # Evidencias fotográficas de la ejecución de los ejercicios 1, 2 y 3
├── informe/                  # Documentación Markdown con preguntas de análisis y seguridad
│   ├── ejercicio1.md
│   ├── ejercicio2.md
│   ├── ejercicio3.md
│   └── ejercicio4.md
└── README.md                 # Documentación general del repositorio


🛠️ Resumen de Ejercicios Realizados

Ejercicio 1: Configuración de Bucket S3 y AWS CLI

Creación de bucket S3 privado (lab-09-sanchez-20261014) en la región us-east-1.

Operaciones CRUD mediante AWS CLI: creación de carpetas (originales/), subida de archivos, descarga y sincronización de carpetas locales con S3.

Ejercicio 2: Políticas IAM y Seguridad (Mínimo Privilegio)

Creación de la política personalizada PoliticaAccesoBucketImagenes restringida exclusivamente a la ruta originales/* del bucket.

Configuración de usuario IAM con credenciales programáticas para restringir accesos directos al bucket.

Ejercicio 3: Versionamiento y Ciclo de Vida

Habilitación de versionamiento en S3 para prevenir pérdidas accidentales de datos.

Definición de Lifecycle Rules para la transición automática de objetos a clases de almacenamiento de menor costo (S3 Standard-IA / Glacier) y expiración de versiones antiguas.

Ejercicio 4: Aplicación Web con Presigned URLs (Express 5 + S3)

Backend: Implementación de API con Express 5 para firmar peticiones PUT y GET temporales utilizando @aws-sdk/s3-request-presigner.

Frontend: Galería web interactiva en JavaScript que realiza subidas directas desde el navegador a S3 vía HTTP PUT, evitando saturar el servidor backend.

Seguridad y CORS: Configuración de reglas CORS en el bucket S3 para permitir únicamente los métodos PUT y GET desde orígenes autorizados sin exponer credenciales en el cliente.

🚀 Instrucciones de Ejecución

1. Requisitos Previos

Node.js v18+ instalado.

Cuenta de AWS con bucket S3 configurado y permisos IAM adecuados.

2. Configurar e Iniciar el Backend

cd backend
npm install
node server.js


El servidor backend se ejecutará en: http://localhost:3000

3. Iniciar el Frontend

Abre el archivo frontend/index.html en el navegador utilizando la extensión Live Server en VS Code o sirviendo los archivos desde http://127.0.0.1:5500.

🔒 Principios de Seguridad Aplicados

Acceso Privado por Defecto: Bloqueo de todo acceso público al bucket S3.

Presigned URLs: Carga y descarga temporal de objetos mediante tokens firmados con tiempo de expiración (5 a 15 min).

Mínimo Privilegio: Restricción de permisos IAM únicamente a la estructura de carpetas utilizada.

Resguardo de Credenciales: Ninguna credencial de AWS está expuesta en el código frontend; residen exclusivamente en las variables de entorno del servidor.