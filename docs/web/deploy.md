# Setup Web Application - Deploy Steps

## 1) Configure Environment (React/Vite)

Set production values in your frontend environment file (example: `.env.production`):

```dotenv
VITE_APP_NAME=MegaClassify
VITE_API_BASE_URL=https://apimega.megzed.com
```

Also configure branding keys and analytics IDs if your build uses them.

## 2) Install and Build (React/Vite)

From web source directory:

```bash
npm install
npm run build
```

Build output is typically generated in `dist/`.

## 3) Deploy Build Output to Web Server

- Upload `dist/` contents to your frontend domain document root
- If hosted in cPanel, use **File Manager** or Git deployment
- Configure SPA fallback so unknown routes return `index.html`
- Ensure HTTPS is enabled

### Nginx SPA Fallback Example

```nginx
location / {
  try_files $uri $uri/ /index.html;
}
```

### Apache (.htaccess) SPA Fallback Example

```apache
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>
```

## 4) Post-Deploy Validation

- Open homepage and listing pages
- Verify login/register actions
- Confirm API data loads without CORS errors
- Refresh direct route URLs (for example `/profile` or `/listing/123`) to validate SPA fallback

## Troubleshooting

### Blank Page After Deploy

- Check browser console for missing asset paths
- Verify Vite `base` setting and deployment path
- Confirm `dist/assets/*` files are uploaded

### CORS Error on API Calls

- Allow frontend domain in backend CORS config
- Ensure preflight `OPTIONS` requests are handled

### 404 on Refresh (SPA Routes)

- Web server fallback rule is missing or incorrect
- Re-check Nginx/Apache rewrite config
