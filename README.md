# Ruta Express

Información centralizada de colectivos y comisionistas para pueblos sin transporte público unificado.

## Stack

- [Astro](https://astro.build) — static site generator
- JSON plano como fuente de datos
- CSS vanilla con diseño mobile-first
- [Formspree](https://formspree.io) — formulario de contacto
- Google AdSense — publicidad

## Desarrollo

```bash
npm install
npm run dev
```

## Build

```bash
npm run build
```

El output estático se genera en `dist/`, listo para deployar en Vercel, Cloudflare Pages o cualquier host estático.

## Estructura

```
src/
├── components/   # Header, Footer, Filtros, etc.
├── data/         # transportes.json
├── layouts/      # Layout.astro (HTML shell)
├── pages/        # index, contacto, privacidad, 404
└── styles/       # global.css
```

## Datos

Editar `src/data/transportes.json` para agregar o modificar servicios. El tipo `origen` y `destino` se usan para los filtros. Los horarios múltiples se separan con `&` y se renderizan apilados.
