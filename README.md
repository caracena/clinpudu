# ClinPudu — sitio web

Página de presentación del proyecto ClinPudu (ES / EN / DE), publicada con GitHub Pages en https://clinpudu.cl.

- `index.html` — página única; los textos de los tres idiomas están en el objeto `I18N` del script.
  El idioma se elige con el selector ES/EN/DE, con `?lang=es|en|de`, o según el idioma del navegador.
- `assets/` — logo y favicon.
- `CNAME` — dominio personalizado para GitHub Pages.

## Publicación (GitHub Pages)

1. Fusionar esta rama en `main`.
2. En GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. En **Custom domain** debe aparecer `clinpudu.cl` (viene del archivo `CNAME`). Cuando el DNS propague, activar **Enforce HTTPS**.

## DNS en Cloudflare (zona clinpudu.cl)

En **DNS → Records** crear:

| Tipo  | Nombre | Contenido           | Proxy    |
|-------|--------|---------------------|----------|
| A     | @      | 185.199.108.153     | DNS only |
| A     | @      | 185.199.109.153     | DNS only |
| A     | @      | 185.199.110.153     | DNS only |
| A     | @      | 185.199.111.153     | DNS only |
| AAAA  | @      | 2606:50c0:8000::153 | DNS only |
| AAAA  | @      | 2606:50c0:8001::153 | DNS only |
| AAAA  | @      | 2606:50c0:8002::153 | DNS only |
| AAAA  | @      | 2606:50c0:8003::153 | DNS only |
| CNAME | www    | caracena.github.io  | DNS only |

Dejar los registros en **DNS only** (nube gris) hasta que GitHub emita el certificado HTTPS.
Si después se quiere activar el proxy de Cloudflare (nube naranja), usar **SSL/TLS → Full** (no "Flexible") para evitar bucles de redirección.

Opcional: en **Settings → Pages → Verified domains** (configuración de la cuenta de GitHub) se puede verificar `clinpudu.cl` con el registro TXT que indique GitHub.
