# MEGA Tarimas — Landing page

Landing page de una sola página para MEGA Tarimas, construida con [Astro](https://astro.build) en modo
completamente estático (`output: 'static'`). Sin React/Vue/Svelte, sin Tailwind, sin librería de
animación ni de carrusel: componentes `.astro` nativos, CSS con variables y JavaScript ligero
(reveal on scroll + menú móvil + validación nativa del formulario).

## Estructura

```
src/
├── assets/images/     # Fotografías fuente (optimizadas por Astro al compilar)
├── components/        # Un componente por sección (Header, Hero, NuestrasTarimas, ...)
├── layouts/Layout.astro
├── pages/index.astro  # Única página del sitio; navegación por anclas
└── styles/            # fonts.css, tokens.css (paleta/tipografía/espaciado), global.css
public/
├── fonts/             # Montserrat autoalojada (Regular/Bold/ExtraBold, subset latin)
└── favicon.jpg, apple-touch-icon.jpg, og-image.jpg
```

## Comandos

| Comando           | Acción                                         |
| :----------------- | :---------------------------------------------- |
| `npm install`       | Instala dependencias                            |
| `npm run dev`       | Servidor de desarrollo en `localhost:4321`       |
| `npm run build`     | Genera el sitio estático en `./dist/`            |
| `npm run preview`   | Sirve `./dist/` localmente para verificarlo      |

## Despliegue en HostGator

1. **Requisitos locales**: Node.js 18+ y npm.
2. Generar el paquete estático:
   ```sh
   npm install
   npm run build
   ```
3. **Qué entregar**: únicamente el **contenido** de la carpeta `dist/` (no la carpeta en sí). Debe
   incluir `index.html` y las subcarpetas `_astro/` y `fonts/` junto con los archivos sueltos
   (`favicon.jpg`, `apple-touch-icon.jpg`, `og-image.jpg`).
4. El administrador del hosting debe **respaldar el sitio existente** y confirmar la *document root*
   del dominio antes de reemplazar archivos (normalmente `public_html/` para el dominio principal, o
   la carpeta asignada si `megatarimas.mx` está configurado como dominio adicional/addon).
5. Subir el contenido de `dist/` a esa carpeta mediante **cPanel File Manager** o **FTP**, tarea del
   responsable del servidor (este proyecto no solicita ni almacena credenciales de HostGator/cPanel/FTP).
6. **Verificación posterior**: cargar el dominio con HTTPS, revisar que la página principal y sus
   activos (imágenes, fuentes, CSS, JS) respondan sin 404, probar cada ancla del menú, el botón de
   WhatsApp, el formulario (sin backend aún) y las preguntas frecuentes, y confirmar el comportamiento
   responsive en móvil, tablet y escritorio.

No se requiere Node.js en producción, ni rewrites de Vercel, ni funciones serverless: `dist/` es un
sitio 100% estático servible desde cualquier raíz de dominio.

## Pendientes

- **Formulario de cotización**: no está conectado a ningún backend. El punto de integración está
  aislado en [`src/components/FormularioCotizacion.astro`](src/components/FormularioCotizacion.astro)
  con un comentario `TODO`; solo intercepta el envío para evitar una recarga, sin mostrar un estado de
  éxito falso.
- **Aviso de privacidad**: el enlace del footer no tiene una URL asignada todavía (marcado con `TODO`
  en [`src/components/Footer.astro`](src/components/Footer.astro)).
- **Certificaciones**: se muestran como tarjetas tipográficas (NOM-144, ISPM-15, ISO 9001, NWPCA, FSC)
  porque no hay logotipos oficiales autorizados en el repositorio. Si el cliente los proporciona,
  reemplazar esas tarjetas por los sellos reales respetando sus derechos de uso.

## Observaciones de contenido conservadas literalmente

Por indicación expresa, estos tres puntos del copy aprobado **no se corrigieron**:

1. La opción de formulario `A la medida / sobre diseñoTarimas para exportación (tratamiento térmico)`
   aparece concatenada en la fuente de verdad.
2. El CTA del formulario dice literalmente `Solicitar cotización Ahora` (con esa capitalización).
3. El hero incluye tanto `Listas para exportación` como `Listos para Exportación Internacional`.
