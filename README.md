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

Esta variante es la que está publicada en **https://juliocesarsandoval.com**, con Firebase Hosting.

### Dónde vive

| Proyecto de Firebase | Sitio | Dominio | Uso |
|---|---|---|---|
| `juliocesar-dev` (JulioCesarPortafolio) | https://juliocesar-dev.web.app | `juliocesarsandoval.com` y `www.juliocesarsandoval.com` | **Producción.** Es lo que ve la gente. |
| `juliocesarportafolio2026` (JulioCesarPortafolio2026) | https://juliocesarportafolio2026.web.app | Ninguno | Copia sin dominio. Solo se actualiza si publicas ahí a propósito. |

Quien decide qué sitio se sirve en el dominio es Firebase (Hosting → Dominios personalizados), no el DNS. Los dos proyectos usan la misma IP (`199.36.158.100`), así que el DNS por sí solo no dice a cuál apunta. El TXT `hosting-site=…` de Hostinger solo sirve para verificar la propiedad del dominio.

`.firebaserc` tiene `juliocesar-dev` como proyecto por defecto, así que `firebase deploy` publica directo en producción.

### Publicar un cambio

```powershell
cd C:\Users\Julio\Downloads\Portafolio\05-editorial-magazine
firebase deploy --only hosting
git add .
git commit -m "Describe el cambio"
git push
```

Guardar en GitHub (`git push`, repo `SandovalJulio/Portafolio2026`) no publica el sitio: hay que correr `firebase deploy` aparte.

Para confirmar que el cambio está en vivo, revisa https://juliocesarsandoval.com, no solo la URL `.web.app`. El navegador puede guardar la página hasta 1 hora (`max-age=3600`); usa Ctrl+F5 o una ventana de incógnito.

### DNS (Hostinger)

| Registro | Valor |
|---|---|
| A `@` | `199.36.158.100` |
| TXT `@` | `hosting-site=juliocesarportafolio2026` |
| CNAME `www` | `juliocesarportafolio2026.web.app` |

El TXT y el CNAME ya nombran al proyecto `juliocesarportafolio2026`, pero el dominio sigue conectado en Firebase a `juliocesar-dev`, y así funciona bien.

### Pasar el dominio al proyecto nuevo (opcional)

1. En la consola de `juliocesar-dev` → Hosting, quita `juliocesarsandoval.com` y `www.juliocesarsandoval.com`.
2. En `juliocesarportafolio2026` → Hosting → Agregar dominio personalizado, agrega los dos (`www` con redirección al dominio principal). El DNS de Hostinger ya está listo.
3. Cambia `default` en `.firebaserc` a `juliocesarportafolio2026`.

Mientras Firebase emite el certificado, el dominio puede fallar unos minutos.

### Otros dominios en `juliocesar-dev`

`juliocesar.pro` (activo, con error de host) y `manuelito.es.org` (verificación perdida) siguen registrados en ese sitio. No afectan a `juliocesarsandoval.com`.

### Otros hostings

En GitHub Pages, Netlify, Vercel o Cloudflare Pages basta con subir la carpeta tal cual. Si cambia el dominio final, ajusta `rel="canonical"` y las URLs `og:image` en `index.html`.
