# Setup Admin Panel - Installation Steps

This is the primary production installation flow for aaPanel + Nginx.

!!! warning
    Keep this guide aligned with the documentation bundled in your CodeCanyon ZIP. If package docs and this page differ by version, follow the package-specific instructions first.

## 1) Upload Project Files

- Create site in aaPanel (`Website` -> `Add Site`)
- Set root path, e.g. `/www/wwwroot/{{YOUR_DOMAIN}}`
- Upload extracted project files from CodeCanyon package
- Ensure Laravel app files are present (`artisan`, `app/`, `public/`, `vendor/` once installed)

## 2) Configure Nginx Document Root

Point Nginx to Laravel `public` directory.

Example site path:

- App root: `/www/wwwroot/{{YOUR_DOMAIN}}`
- Web root: `/www/wwwroot/{{YOUR_DOMAIN}}/public`

Update aaPanel site config accordingly.

## 3) Install PHP Dependencies

Run from project root:

```bash
composer install --no-dev -o
```

## 4) Environment Setup

```bash
cp .env.example .env
```

Edit `.env` with real values:

```dotenv
APP_NAME=MegaClassify
APP_ENV=production
APP_KEY=
APP_DEBUG=false
APP_URL=https://{{YOUR_DOMAIN}}

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE={{DB_NAME}}
DB_USERNAME={{DB_USER}}
DB_PASSWORD={{DB_PASSWORD}}

CACHE_DRIVER=file
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
```

## 5) Generate App Key

```bash
php artisan key:generate
```

## 6) Run Migrations

```bash
php artisan migrate --force
```

## 7) Create Storage Symlink

```bash
php artisan storage:link
```

## 8) Clear/Optimize Cached Artifacts

```bash
php artisan optimize:clear
```

## 9) Apply Final Permissions

```bash
chown -R www:www /www/wwwroot/{{YOUR_DOMAIN}}
chmod -R 775 storage bootstrap/cache
```

## 10) SSL Enablement

In aaPanel:

- Open site settings -> SSL
- Apply Let's Encrypt certificate
- Force HTTPS redirection

## 11) Buyer Verification Checklist (Install Gate)

- [ ] Purchase code confirmed
- [ ] Buyer details match CodeCanyon account
- [ ] Package source is official download
- [ ] No nulled/modified core package used
- [ ] All required setup files from ZIP preserved

## 12) Post-Install Smoke Test

- Open `https://{{YOUR_DOMAIN}}`
- Verify homepage and login load
- Login to admin user
- Create test category/listing
- Upload a test image
- Confirm image visible in frontend/admin
