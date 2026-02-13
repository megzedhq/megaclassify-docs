# Setup Mobile Application - Prerequisite

Prepare the following before building the MegaClassify mobile app.

## Requirements

### Source & Tools
- Latest MegaClassify mobile source from the official CodeCanyon package
- **Flutter SDK (Required)**
  - Recommended: **Flutter 3.22.x**
  - Minimum: **Flutter 3.16+**
  - Dart comes bundled with Flutter
- Android Studio (Android build) + latest Android SDK tools
- Xcode (iOS build, macOS required)

### Backend & API
- Working backend API deployed and reachable publicly
- API Base URL (HTTPS recommended)

**API Base URL Examples**
- `https://api.example.com`
- `https://api.yourdomain.com`
- `https://apimega.megzed.com` (sample)

### Release Build / Publishing
- Android signing keystore (`.jks`) for Play Store release builds
- iOS signing: Apple Developer account + Bundle ID + certificates/profiles
- App package name / bundle ID finalized (changing later will break updates)

## Configuration Inputs

### API
- `API_BASE_URL=https://api.example.com`
  - Example: `API_BASE_URL=https://apimega.megzed.com`

### App Identity
- App name (display name)
- Android package name (example: `com.example.megaclassify`)
- iOS bundle identifier (example: `com.example.megaclassify`)

### Optional (If Enabled)
- Push notifications keys (Firebase)
- Google Maps key (if location/maps features exist)
- Deep links / App Links configuration (if share links or QR routes exist)
- Payment keys (Razorpay/Stripe/PayPal/etc. if mobile payments enabled)

## Recommended System Setup

### Flutter Environment Check
Run:
```bash
flutter doctor
flutter --version
