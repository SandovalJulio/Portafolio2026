# 05 — Editorial / Magazine

Portafolio estático de **Julio César Sandoval** con estética de revista impresa.

## Estilo

- **Papel y tinta:** fondo off-white cálido (`#f5f0e8`), texto negro tinta y un solo acento cian (`#11B4DB`). En tema claro, el texto en acento usa `#076a83` (mismo cian, más profundo) para cumplir contraste 4.5:1; `#11B4DB` se usa tal cual en filetes, botones, barra de progreso y en todo el tema oscuro. Tema oscuro automático vía `prefers-color-scheme: dark`.
- **Tipografía:** *Fraunces* (serif variable) para titulares, capitulares y pull-quotes; *Inter* para el texto corrido. Ambas desde Google Fonts, con fallbacks del sistema. No se usa el peso 300.
- **Recursos de diseño:** cabecera tipo masthead, portada con el nombre partido en tres líneas, índice de contenidos, secciones numeradas (I. Experiencia, II. Proyectos, III. Skills, IV. Educación, V. Certificaciones, VI. Sobre mí, VII. Contacto), kickers en versalitas, filetes finos, capitulares, texto a dos columnas en escritorio, leyendas de imagen en cursiva y proyectos maquetados a doble columna alternando imagen/texto. Dentro de Proyectos hay una lista de *proyectos personales* y otra de repositorios en GitHub.
- **Interacciones:** barra de progreso de lectura, masthead pegajoso que se compacta al desplazar, índice móvil accesible, scroll suave y resaltado de la sección activa.
- **Animaciones discretas** (todas se desactivan con `prefers-reduced-motion`): entrada escalonada de la portada con leve desenfoque, filetes que se trazan, foto de portada que se descubre y se desplaza apenas al hacer scroll (solo navegadores con `animation-timeline`), reveal-on-scroll escalonado, imágenes de proyecto que se descubren al entrar, contadores en las cifras, subrayado que se dibuja bajo la sección activa y sello de certificación que gira al pasar el cursor.

## Archivos

```
05-editorial-magazine/
├── index.html      # marcado semántico, SEO, Open Graph, JSON-LD
├── styles.css      # estilos mobile-first, tema claro/oscuro
├── script.js       # vanilla JS, sin dependencias
├── README.md
├── cv/
│   └── CV-Julio-Cesar-Sandoval.pdf   # enlazado con "Descargar CV"
└── img/
    ├── favicon.svg
    ├── profile.webp
    ├── me.webp
    └── projects/{prompts,castube,htmlgen,valeria}.webp
```

## Cómo usarlo

No hay paso de build. Abre `index.html` con doble clic o sirve la carpeta con cualquier servidor estático:

```bash
npx serve .
# o
python -m http.server 8080
```

## Despliegue

- **Firebase Hosting:** `firebase init hosting` (public: `.`), luego `firebase deploy`.
- **GitHub Pages / Netlify / Vercel / Cloudflare Pages:** sube la carpeta tal cual; no requiere configuración.

Antes de publicar, ajusta `rel="canonical"` y las URLs `og:image` en `index.html` si el dominio final cambia.
