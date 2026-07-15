# BERA Motorcycles Panamá — Sitio web

Sitio estático (HTML + imágenes/docs/videos) para **beramotorcyclespanama.com**.

- **Repo:** https://github.com/BeraPanama/Bera-Motorcyles-Panama (este mismo — ya existe, no crear otro)
- **Hosting:** Vercel, conectado al repo. Cada push a `main` publica automáticamente en ~1 minuto.
- **URL:** https://bera-motorcyles-panama.vercel.app

## Cómo publicar un cambio

```bash
cd bera-website
git add -A
git commit -m "describe el cambio"
git push
```

Nada más. Vercel detecta el push y publica solo. Si `git push` pide autenticación, corre `gh auth login` una vez (o usa GitHub Desktop → Push origin).

## Cómo trabajar con el agente (Claude Code)

1. Abre una terminal en esta carpeta y ejecuta `claude`.
2. Describe el cambio en lenguaje normal: *"sube el precio de la SBR a $1,400 y publícalo"*.
3. Claude Code edita, hace commit y push — y queda en línea.

Las instrucciones del agente están en `CLAUDE.md`.

## Estructura

```
├── index.html   # sitio completo: home + páginas SBR, Kavak y Runner 6G (CSS/JS inline)
├── images/      # imágenes: catálogo, héroes, variantes de color, galerías, cascos, logos
├── docs/        # fichas técnicas (PDF) y formularios
├── videos/      # videos del hero
└── CLAUDE.md    # instrucciones del agente
```

## Pendientes conocidos

- La sección "Compra online" está **oculta** (display:none en las 3 `section-buy`), no eliminada — se reactiva cuando estén listos la pasarela de pago, los datos de transferencia y el Yappy.
- Dominio: apuntar `beramotorcyclespanama.com` al proyecto de Vercel (Domain settings) cuando se decida el corte desde Squarespace.
