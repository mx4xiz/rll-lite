# R.L.L Lite — Build Instructions (Android APK & AAB)

## Prerequisites

Install these on your computer before starting:

1. **Node.js** (v18+) — https://nodejs.org
2. **Android Studio** — https://developer.android.com/studio
   - During install, make sure to include: Android SDK, Android SDK Platform, Android Virtual Device
3. **Java JDK 17** — usually bundled with Android Studio

After installing Android Studio, open it once and let it finish downloading SDK components.

---

## Step-by-Step Build

### 1. Install dependencies

Open a terminal in this folder (`rll-capacitor/`) and run:

```bash
npm install
```

### 2. Build the web app

```bash
npm run build
```

This creates a `dist/` folder with the compiled app.

### 3. Add the Android platform (first time only)

```bash
npx cap add android
```

### 4. Sync the web build into Android

```bash
npx cap sync android
```

### 5. Open in Android Studio

```bash
npx cap open android
```

Android Studio will open the project.

---

## Building the APK in Android Studio

Once Android Studio is open:

1. Wait for Gradle to finish syncing (progress bar at the bottom)
2. Go to **Build → Build Bundle(s) / APK(s) → Build APK(s)**
3. Wait for the build to complete
4. Click **"locate"** in the notification that appears, or find the APK at:
   ```
   android/app/build/outputs/apk/debug/app-debug.apk
   ```

Transfer this `.apk` file to your phone and install it.

---

## Installing on Your Phone

1. On your Android phone, go to **Settings → Security** (or **Apps → Special app access**)
2. Enable **"Install unknown apps"** for your file manager or browser
3. Transfer the APK to your phone (USB, email, Google Drive, etc.)
4. Open the APK file on your phone and tap **Install**

---

## Troubleshooting

**"SDK location not found"**
- Open Android Studio, go to **Tools → SDK Manager**, note the SDK path, then set it:
  ```bash
  export ANDROID_HOME=/path/to/your/android-sdk
  ```

**Gradle build fails**
- Make sure you're using JDK 17 (not 21+)
- In Android Studio: **File → Project Structure → SDK Location → JDK Location**

**App installs but crashes**
- The app requires an internet connection on first load to fetch Google Fonts
- Make sure your phone's Android version is 7.0 (API 24) or higher
