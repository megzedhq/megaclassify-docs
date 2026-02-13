# Setup Admin Panel - Installation Steps

This is the primary production installation flow for **cPanel-based hosting**.

!!! warning
    Keep this guide aligned with the documentation bundled in your CodeCanyon ZIP. If package docs and this page differ by version, follow the package-specific instructions first.

## 1) Upload Project Files

- Open **cPanel → File Manager**
- Create app folder, e.g. `/home/{{CPANEL_USER}}/{{APP_PATH}}`
- Upload and extract project files from CodeCanyon package
- Confirm Laravel files exist (`artisan`, `app/`, `public/`, `vendor/` after Composer install)

## 2) Set Public Web Root

Point your domain/subdomain document root to Laravel `public` folder.

Example:

- App root: `/home/{{CPANEL_USER}}/{{APP_PATH}}`
- Web root: `/home/{{CPANEL_USER}}/{{APP_PATH}}/public`

For cPanel subdomains/addon domains, adjust document root in **Domains** settings.

## 3) Create Database from cPanel

In **MySQL® Databases**:

- Create database: `{{DB_NAME}}`
- Create database user: `{{DB_USER}}`
- Set strong password
- Add user to database with **ALL PRIVILEGES**

## 4) Install PHP Dependencies

Run from project root (SSH/Terminal):

```bash
composer install --no-dev -o
```

## 5) Environment Setup

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

## 6) Generate App Key

```bash
php artisan key:generate
```

## 7) Run Migrations

```bash
php artisan migrate --force
```

## 8) Create Storage Symlink

```bash
php artisan storage:link
```

## 9) Clear/Optimize Cached Artifacts

```bash
php artisan optimize:clear
```

## 10) Apply Final Permissions

```bash
find /home/{{CPANEL_USER}}/{{APP_PATH}} -type f -exec chmod 644 {} \;
find /home/{{CPANEL_USER}}/{{APP_PATH}} -type d -exec chmod 755 {} \;
chmod -R 775 /home/{{CPANEL_USER}}/{{APP_PATH}}/storage
chmod -R 775 /home/{{CPANEL_USER}}/{{APP_PATH}}/bootstrap/cache
```

## 11) SSL Enablement

In cPanel:

- Open **SSL/TLS Status**
- Run AutoSSL (or install custom certificate)
- Force HTTPS from domain settings / redirect rules

## 12) Buyer Verification Checklist (Install Gate)

- [ ] Purchase code confirmed
- [ ] Buyer details match CodeCanyon account
- [ ] Package source is official download
- [ ] No nulled/modified core package used
- [ ] All required setup files from ZIP preserved

## 13) Post-Install Smoke Test

- Open `https://{{YOUR_DOMAIN}}`
- Verify homepage and login load
- Login to admin user
- Create test category/listing
- Upload a test image
- Confirm image visible in frontend/admin
