# Setup Mobile Application - Setup & Build

Follow your package-specific mobile framework guide first, then use these general steps.

## 1) Connect to API

Set API endpoint to your deployed backend:

- Example: `https://apimega.megzed.com`

## 2) Install Dependencies

Use the command set required by shipped framework (Flutter/React Native/etc.).

## 3) Configure Environment/Constants

Update:

- Base URL
- App identifiers
- Feature flags
- Payment/notification keys (if any)

## 4) Build App

Generate debug build first, then release build using your signing config.

## 5) Troubleshooting

### CORS / API Network Failures

- Verify backend CORS allows mobile origin or wildcard policy as needed
- Check SSL validity and TLS compatibility
- Confirm API path/version matches mobile code expectations

### Authentication Fails

- Check API URL and auth endpoints
- Validate server time/timezone
- Verify credentials and token configuration
