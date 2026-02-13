# Setup Web Application - Deploy Steps

## 1) Configure Environment

Set production environment values:

- API base URL (`https://apimega.megzed.com` or your server)
- App title/branding
- Analytics keys (if used)

## 2) Install and Build

Run framework-specific install/build commands from the web source directory.

## 3) Deploy Static/Server Artifacts

- Upload build output to hosting
- Configure web server rewrite rules (if SPA)
- Enable HTTPS

## 4) Post-Deploy Validation

- Open homepage and listing pages
- Verify login/register actions
- Confirm API data loads without CORS errors

## Troubleshooting

### Blank Page After Deploy

- Check browser console for missing asset paths
- Verify base path/public URL settings

### CORS Error on API Calls

- Allow web app domain in backend CORS config
- Ensure preflight OPTIONS requests are handled

### 500/502 from API Proxy

- Validate upstream API URL
- Check Nginx/hosting proxy settings and logs
