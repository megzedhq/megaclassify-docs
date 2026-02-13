# Setup Mobile Application - Installation Steps

This page provides a clear, step-by-step installation flow for the MegaClassify mobile app.

## 1) Unzip and Open the Project

1. Unzip the downloaded mobile app source package.
2. Open the project folder in your editor/IDE.

## 2) Run Initial Flutter Commands

From the project root, run:

```bash
flutter clean
flutter pub get
```

## 3) Create Firebase Project and Download JSON

1. Open [Firebase Console](https://console.firebase.google.com/).
2. Create a **new project**.
3. Add an **Android app** inside Firebase.
4. Enter your Android **package name** and app name.
5. Generate and download `google-services.json`.

## 4) Place Firebase File in App

Copy the downloaded file to:

- `android/app/google-services.json`

## 5) Update Android App Identity and Keys

Open `android/app/src/main/AndroidManifest.xml` and verify/update:

- Package name
- App label (app name)
- Google Maps API key (`meta-data` entry, if used)

## 6) Update App Icon / Logo

Replace app launcher icons in the Android resources icon folders.

Common locations include:

- `android/app/src/main/res/mipmap-*`
- Any project-specific icon/logo assets folder used by your app

## 7) Generate Android Keystore (Release)

Create a release keystore file and keep it inside:

- `android/keystore/`

Example command:

```bash
keytool -genkey -v -keystore android/keystore/release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias release
```

## 8) Configure `key.properties`

Create or update `android/key.properties`:

```properties
storePassword=YOUR_STORE_PASSWORD
keyPassword=YOUR_KEY_PASSWORD
keyAlias=release
storeFile=keystore/release-key.jks
```

## 9) Update App Config Values

Open:

- `lib/core/config/app_config.dart`

Update the following values:

- Host URL (API base URL)
- Frontend URL
- Google Places API key

## 10) Build the App

After configuration is complete, build APK/AAB:

```bash
flutter build apk
# or
flutter build appbundle
```

---

## Quick Checklist

- [ ] `flutter clean` and `flutter pub get` completed
- [ ] Firebase project created
- [ ] `google-services.json` placed in `android/app/`
- [ ] Manifest package name, app label, and Maps API key updated
- [ ] App icons/logo replaced
- [ ] Keystore generated in `android/keystore/`
- [ ] `android/key.properties` updated
- [ ] `lib/core/config/app_config.dart` updated
- [ ] Release build generated successfully
