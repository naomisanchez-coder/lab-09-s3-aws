# Ejercicio 3: Versionado, Ciclo de Vida y Resiliencia

- **Versionado de Bucket:** Habilitado exitosamente en `lab-09-sanchez-20261014`.
- **Prueba de Sobreescritura:** Subidas 3 versiones progresivas de `prueba.txt` verificadas con sus Version IDs.
- **Prueba de Resiliencia:** Simulación de borrado accidental, verificación de *Delete Marker* y restauración del archivo original.
- **Regla de Ciclo de Vida (`regla-imagenes-antiguas`):**
  - Prefijo: `originales/`
  - Transición Versión Actual: Standard-IA (30 días) -> Glacier Instant Retrieval (90 días).
  - Transición Versión No Actual: Glacier Deep Archive (60 días).
  - Expiración Versión No Actual: Eliminación permanente tras 365 días.
