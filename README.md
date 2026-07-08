# Bera Motorcycles Panama — Sitio web

Sitio estático (HTML/CSS/JS) para beramotorcyclespanam.com, reemplazo del sitio Squarespace.

## Cómo funciona el flujo "agente"

1. Abre una terminal en esta carpeta y ejecuta `claude` (Claude Code).
2. Describe el cambio en lenguaje normal: *"sube el precio de la SBR a $1,400 y publícalo"*.
3. Claude Code edita los archivos, hace commit y push — el hosting publica el cambio en ~1 minuto.

Las instrucciones del agente están en `CLAUDE.md`.

## Puesta en marcha (una sola vez)

### 1. Crear el repo

```bash
cd bera-website
git init && git add -A && git commit -m "sitio inicial"
gh repo create bera-website --private --source=. --push
```

(O crea el repo en github.com y sigue las instrucciones de "push an existing repository".)

### 2. Hosting gratis con Netlify (recomendado)

1. Entra a netlify.com → "Add new site" → "Import an existing project" → conecta el repo de GitHub.
2. Sin configuración de build (es HTML puro). Deploy.
3. Cada push a `main` publica automáticamente.

Alternativa: GitHub Pages (Settings → Pages → deploy from `main`).

### 3. Apuntar el dominio

1. En Netlify: Domain settings → Add custom domain → `beramotorcyclespanam.com`.
2. Donde compraste el dominio (posiblemente Squarespace Domains), cambia los DNS:
   - Registro `A` → IP que indique Netlify, o registro `ALIAS/CNAME` → tu sitio Netlify.
3. Espera la propagación (minutos a 24h). Netlify emite el certificado SSL solo.
4. Cuando el dominio apunte al sitio nuevo, puedes cancelar el plan de Squarespace (el dominio se puede mantener o transferir).

## Estructura

```
bera-website/
├── index.html   # sitio completo: home + páginas SBR, Kavak y Runner 6G (CSS/JS inline)
├── images/      # 56 imágenes: catálogo, héroes, variantes de color, galerías, cascos, logos
├── docs/        # fichas técnicas (PDF) y formularios de compra
├── videos/      # videos del hero
└── CLAUDE.md    # instrucciones del agente
```

Nota: el archivo original de Squarespace (29MB, con todo embebido en base64) fue convertido a esta estructura — mismo sitio, idéntico al original, pero apto para Git.
