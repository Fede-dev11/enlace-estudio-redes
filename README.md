# Enlace · Estudio de redes

Web estática en español para preparar el examen de Fundamentos de Redes y Comunicaciones.

- CAPA I: las 110 páginas del primer PDF.
- CAPA II: exclusivamente las páginas 1–72 del segundo PDF. No incluye CAPA III.
- 182 diapositivas originales en imagen, con texto consultable y buscador.
- Sección de medios de transmisión con diez medios desarrollados, tabla comparativa, ventajas, limitaciones, aplicaciones y referencias a las diapositivas.
- 15 temas con resumen y seguimiento de progreso local.
- 46 tarjetas y preguntas explicadas, con referencia a la página de origen.
- Prácticas aleatorias de 15 preguntas con revisión de errores.

## Uso

Abre `index.html` directamente o ejecuta `python3 -m http.server 8000` en esta carpeta. No requiere instalar dependencias ni servidor de aplicación. Los estilos incluyen fuentes de Google Fonts, con fuentes locales de respaldo.

GitHub Actions publica automáticamente en GitHub Pages al actualizar `main`. El repositorio debe tener Pages configurado con origen GitHub Actions.

## Fuentes y alcance

Contenido procedente de `CAPA 1 .pdf` y de las primeras 72 páginas de `CAPA II Y III_opt_compressed.pdf`, entregados por el usuario. Las diapositivas son material de estudio original, incluidas referencias históricas y posibles erratas. Los resúmenes y preguntas son ayudas elaboradas para repasar; no constituyen preguntas oficiales ni una actualización de normas técnicas. En las ayudas se aclara que un switch aprende de la MAC de origen, reenvía según la MAC de destino y STP elige el menor identificador de bridge.

El progreso y el historial se guardan en localStorage de cada navegador; no se sincronizan entre dispositivos. No se recopilan respuestas en un servidor.
