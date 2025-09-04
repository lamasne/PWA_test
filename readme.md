# Hello World static web page to Android App

This project demonstrates how to go from a simple Hello World HTML page to a TWA (Trusted Web Activity) running on an Android phone.

---

## 1. Create a simple PWA

1. **Create `index.html`** with your content.
2. **Add a `manifest.json`** with app name, icons, and display mode.
3. **Add a service worker (`service_worker.js`)** to enable offline caching.
4. **Test locally**:

```bash
npx serve
```

5. **Host your PWA** (e.g., using GitHub Pages) to make it accessible via HTTPS.

---

## 2. Wrap the PWA in a TWA using Bubblewrap

1. Install Bubblewrap:

```bash
npm install -g @bubblewrap/cli
```

2. Initialize TWA project:

```bash
bubblewrap init --manifest=https://<your-hosted-pwa>/manifest.json
```

3. Build the project:

```bash
bubblewrap build --output twa-project
```

* This generates an **Android Studio project** that references your PWA URL.

---

## 3. Open project in Android Studio

1. Open the generated TWA project folder.
2. Wait for **Gradle sync** to complete.
3. Build the APK:

```
Build → Build Bundle(s) / APK(s) → Build APK(s)
```

4. APK location:

```
app/build/outputs/apk/debug/app-debug.apk
```

---

## 4. Install APK on your phone

1. Enable **Developer Options** and **USB Debugging** on your phone.
2. Connect your phone via USB.
3. Install the APK via ADB:

```bash
adb -s <device-id> install -r app/build/outputs/apk/debug/app-debug.apk
```

* The TWA app launches as a standalone Android app with icon and splash screen.

---

## 5. Notes

* The TWA **loads the hosted PWA**, so website updates appear automatically.
* Service worker caching allows **offline usage**.
* For Play Store release, create a **signed APK** using `assembleRelease`.
* Phone does **not need to stay connected** after installation.

---

## References

* [Bubblewrap CLI Documentation](https://github.com/GoogleChromeLabs/bubblewrap)
* [Android Studio](https://developer.android.com/studio)
* [PWA Documentation](https://web.dev/progressive-web-apps/)
