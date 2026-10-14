# Ejercicio 2: Seguridad, IAM y Cifrado

- **Usuario IAM creado:** `app-imagenes-user` (acceso programático)
- **Política IAM asignada:** `PoliticaAccesoBucketImagenes` (lectura/escritura/listado en bucket específico)
- **Política de Bucket:** Aplicado `DenyInsecureConnections` para forzar HTTPS (`aws:SecureTransport`).
- **Cifrado en reposo:** Validado SSE-S3 (AES-256) en propiedades de objeto.
- **Pruebas de CLI:** Validado acceso concedido para `ls`/`cp` y `AccessDenied` para `delete-bucket` con perfil `app-user`.
