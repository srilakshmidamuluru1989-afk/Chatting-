# The Inner Circle — Android APK Project

Because an Android `.apk` binary must be compiled with the Android SDK and Gradle, this package gives you everything needed to generate and download your `.apk` file in ~2 minutes—even without installing Android Studio on your computer.

## Option 1: Build Downloadable APK Automatically in the Cloud (No PC Setup Needed)
1. Create a free repository on GitHub and upload the contents of this ZIP.
2. Open the **Actions** tab in your GitHub repository and run **Build Android APK** (or push any file).
3. Once the workflow finishes (~2 minutes), download **`The-Inner-Circle-App-APK`** from the **Artifacts** section—inside is your ready-to-install `app-debug.apk` to share with group members.

## Option 2: Build Locally via Terminal / Android Studio
```bash
npm install
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
```
Your compiled `.apk` will be generated at:
`android/app/build/outputs/apk/debug/app-debug.apk`

## Connecting All APK Users to the Same Live Group Room
1. Create a free project at [Firebase Console](https://console.firebase.google.com/) -> **Realtime Database** -> **Create Database** (start in test mode or add a rule checking `newData.child('appSignature').val() == 'INNER_CIRCLE_APP_V1'`).
2. Copy your database URL (e.g. `https://your-project-default-rtdb.firebaseio.com`).
3. Hardcode `dbUrl` in `www/index.html` before building the APK so everyone who installs the `.apk` automatically joins the exact same private group without manual setup.
