# Post-Install Settings (Admin Panel)

After your `/install` wizard is completed and you can login to the admin panel, do these settings to make the system fully working.

---

## 1) Login to Admin Panel

1. Open the admin login URL shown on the installer finish screen.
2. Login with the email + password shown.

✅ **Expected Result:** You can access the admin dashboard.

---

## 2) Firebase / Google Settings

Go to:

**Admin Panel → Settings → Firebase / Google**

### Steps
1. Upload your Firebase service account JSON.
2. Fill required Firebase keys (if shown).
3. Save.

### Checklist
- [ ] JSON uploaded successfully
- [ ] Firebase keys saved
- [ ] Test login/notification works (if your app uses it)

> ⚠️ Common mistakes:
> - Uploading wrong JSON (not service account)
> - JSON has invalid format
> - Missing required Firebase fields

---

## 3) SMTP Email Settings

Go to:

**Admin Panel → Settings → Email / SMTP**

### Steps
1. Fill:
   - SMTP Host
   - Port
   - Username
   - Password
   - Encryption (`tls` / `ssl`)
   - From Name + From Email
2. Click **Save**
3. Send a **Test Email**.

### Checklist
- [ ] SMTP saved
- [ ] Test email sent successfully

> ⚠️ Common mistakes:
> - Wrong port + encryption combo
> - Using Gmail without App Password
> - Server blocks outbound SMTP

---

## 4) AI Settings (OpenAI / Gemini)

Go to:

**Admin Panel → Settings → AI**

### Steps
1. Add OpenAI API key and/or Gemini API key.
2. Save.
3. Run a test generation (if your panel provides test button).

### Checklist
- [ ] API keys saved (no extra spaces)
- [ ] Test success

> ⚠️ Common mistakes:
> - Keys pasted with quotes/spaces
> - Provider disabled but key added

---

## 5) Final Verification

✅ Confirm these work:
- Admin login works
- DB is connected
- Uploads work (`public/storage`)
- Email works (test email)
- AI works (test prompt)
