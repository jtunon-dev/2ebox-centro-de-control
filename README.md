# Centro de Control 2ebox — producción

Sitio: https://jtunon-dev.github.io/2ebox-centro-de-control/

Este repo es público, pero `index.html` lleva el reporte **cifrado** (AES-256-GCM,
clave derivada con PBKDF2-SHA256 de 600.000 iteraciones). Al abrir el link pide la
clave y descifra en el navegador. Sin la clave el contenido es ilegible.

## Cómo se actualiza

1. Los cambios se prueban primero en el artifact de Claude (QA).
2. Cuando se aprueban, desde `BBDD y Reportería 2ebox/reporte_unificado/`:

   ```
   python pipeline.py          # si hay que refrescar datos
   python publicar_prod.py     # cifra centro-de-control.html → index.html, commit y push
   ```

La clave vive fuera de este repo (`reporte_unificado/.clave_produccion.txt` o la
variable de entorno `CC_CLAVE`). Para cambiarla basta con editar ese archivo y volver
a publicar; los equipos que tenían "Recordar" marcado tendrán que ingresarla de nuevo.
