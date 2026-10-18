# DEVINDA EXTRA SPACE — Android APK build project

This is a **project package, not a compiled APK**. It contains your original `index.html` and a Capacitor Android wrapper scaffold.

## Configure private cloud storage
1. Create a project at https://console.firebase.google.com/ and add a Web app.
2. Copy its Web app config into `www/firebase-config.js`, replacing all placeholder values.
3. In Firebase Authentication, enable Email/Password sign-in.
4. Create a Firestore database and a Cloud Storage bucket.
5. Publish the included `firestore.rules` and `storage.rules`; these are intended to restrict each user's documents/files to their own UID. Verify rules in Firebase before uploading private data.
6. Review Firebase quotas and billing. **This package does not provide 1 TB cloud storage**; actual storage capacity and cost depend on the selected cloud plan.

## Build APK
Install Node.js LTS and Android Studio with Android SDK. In this folder run:
```bash
npm install
npx cap add android
npx cap sync android
npx cap open android
```
In Android Studio wait for Gradle sync, then choose **Build → Build Bundle(s) / APK(s) → Build APK(s)**. The debug APK is normally created at `android/app/build/outputs/apk/debug/app-debug.apk`.

## Important current limitations
- The supplied website uses IndexedDB/localStorage for its existing media and icon state. The current source has not yet been fully migrated to Firebase Storage/Firestore; this package includes the Android wrapper and Firebase security/config scaffolding, but cloud persistence needs an integration pass and testing before it can truthfully be called complete.
- Firebase config is intentionally blank and no Firebase account/project is provisioned here.
- A custom app icon must be exported as Android launcher icon assets and added to the Android project after `npx cap add android`. `APP_ICON_PLACEHOLDER.svg` is a starter concept, not a complete Android icon set.
- The website's “1TB” label does not itself provision 1 TB of cloud storage.
