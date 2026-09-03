# GHT - Flores El Trigal (PWA)

App de aseguramiento de hidratación en campo, instalable como PWA (Progressive Web App).

## Estructura

```
/
├── index.html          ← app principal (antes calidad.html)
├── manifest.json        ← metadatos de instalación
├── sw.js                 ← service worker (caché offline)
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   └── icon-maskable-512.png
└── README.md
```

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (público, para Pages gratuito).
2. Sube estos archivos **conservando la estructura de carpetas** (arrastra
   toda la carpeta o usa "Add file → Upload files" y mantén `icons/` como
   subcarpeta).
3. Ve a **Settings → Pages**.
4. En "Source" selecciona la rama `main` y la carpeta `/ (root)`.
5. Guarda. GitHub te dará una URL tipo:
   `https://TU-USUARIO.github.io/NOMBRE-REPO/`
6. Abre esa URL desde el celular (Chrome/Safari) y usa "Agregar a pantalla
   de inicio" / "Instalar app" para instalarla como PWA.

## Notas técnicas

- **Monitores fijos**: los únicos dos monitores habilitados son
  "Monitora Mayra" y "Monitor Jesus". Se eliminó del panel de
  administración la opción de agregar/quitar aseguradores; solo se pueden
  gestionar cortadores.
- **Offline**: el service worker cachea el app shell y las librerías CDN
  (Chart.js, SheetJS, jsPDF, html2canvas, Font Awesome) la primera vez que
  hay conexión. Después, la app carga sin red. Los registros se guardan en
  `localStorage` del navegador, que ya es local/offline por naturaleza.
- **Importante — alcance del offline**: `localStorage` es local a cada
  dispositivo/navegador. Si varios inspectores usan la app en distintos
  celulares, sus registros NO se sincronizan entre sí automáticamente. Si
  necesitas consolidar datos de varios dispositivos, se requiere un backend
  (ya identificado como pendiente: migración a Supabase).
- Si actualizas `index.html` en el futuro, sube también un cambio en
  `sw.js` (por ejemplo incrementa `CACHE_NAME` a `ght-trigal-v2`) para que
  los dispositivos ya instalados detecten la nueva versión.
