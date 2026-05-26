# Comparativa de Rutas — Antes vs. Después

Dashboard interactivo para comparar dos propuestas de rutas (la **anterior** vs. la **optimizada**):
analiza eficiencia, ocupación laboral y agrupación geoespacial a partir de un archivo Excel.

## Características

- **Filtros globales** (Ciudad, Regional, Ruta, Supervisor) en cascada que aplican a todo el tablero.
- **Mapas** lado a lado con cada punto de venta coloreado por usuario/ruta (paleta estable para ~81 usuarios).
- **Tablas por ruta** comparables (Tiempo de servicio, desplazamiento, total y % de ocupación).
- **% de ocupación sin tope** (resalta en rojo a quienes superan el 100 %).
- Carga de datos por **archivo Excel** (`.xlsx`) directamente desde el navegador.

## Stack

- [Vite](https://vitejs.dev/) + [React 18](https://react.dev/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Leaflet](https://leafletjs.com/) y [SheetJS](https://sheetjs.com/) (se cargan vía CDN en tiempo de ejecución)

---

## Cómo correrlo en tu PC

Necesitas [Node.js](https://nodejs.org/) 18 o superior.

```bash
npm install      # instala dependencias
npm run dev      # entorno de desarrollo (http://localhost:5173)
npm run build    # genera la versión de producción en /dist
npm run preview  # previsualiza el build de producción
```

---

## Subirlo a GitHub

1. Crea un repositorio **vacío** en GitHub (sin README ni .gitignore).
2. Desde la carpeta del proyecto:

```bash
git init
git add .
git commit -m "Dashboard comparativo de rutas"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
git push -u origin main
```

> Reemplaza `TU_USUARIO/TU_REPO` por los tuyos.

---

## Desplegarlo en Vercel

1. Entra a [vercel.com](https://vercel.com/) e inicia sesión con tu cuenta de GitHub.
2. Click en **Add New… → Project** e importa el repositorio que acabas de subir.
3. Vercel detecta automáticamente **Vite**. Deja la configuración por defecto:
   - **Framework Preset:** Vite
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
4. Click en **Deploy**. En ~1 minuto tendrás una URL pública (ej. `https://tu-repo.vercel.app`) lista para compartir.

Cada vez que hagas `git push` a `main`, Vercel volverá a desplegar automáticamente.

---

## Estructura

```
dashboard-rutas/
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
├── public/
│   └── favicon.svg
└── src/
    ├── main.jsx
    ├── index.css
    └── App.jsx        ← lógica y UI del dashboard
```

## Notas sobre los datos

El archivo Excel debe tener hojas cuyo nombre identifique cada conjunto, por ejemplo:
`BASE NUEVA`, `DEZPLASAMIENTO NUEVA`, `BASE VIEJA`, `DEZPLASAMIENTO VIEJA`.

Si tus columnas de **Regional** o **Supervisor** tienen un encabezado distinto,
ajústalo en el diccionario `const F = { ... }` al inicio de `src/App.jsx`.
