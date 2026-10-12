<div align="center">

<img src="app/src/main/res/drawable-nodpi/ic_launcher.png" width="110" alt="PlusPatcher icon"/>

# ➕ PlusPatcher

### Patch Baldi's Basics mobile APKs with PC mod assets. Right on your phone.

<img src="ezgif-261bbcbb277fbbe5.gif" width="320" alt="PlusPatcher demo"/>



![Platform](https://img.shields.io/badge/platform-Android%208.0%2B-3DDC84?logo=android&logoColor=white)




![Kotlin](https://img.shields.io/badge/Kotlin-1.9-7F52FF?logo=kotlin&logoColor=white)




![License](https://img.shields.io/badge/license-Apache%202.0-blue)




![Build](https://img.shields.io/badge/build-GitHub%20Actions-2088FF?logo=githubactions&logoColor=white)



</div>

---

## ✨ Features

- 📦 **Patch in 4 taps**: pick APK → pick mod → patch → export
- 🗜️ **Reads `.zip` and `.rar`** PC mod packs
- 🔏 **Re-signs the APK** (v1/v2/v3) so Android will install it
- 🔋 **Background patching** with a foreground service and wake lock
- 📱 **Xiaomi / HyperOS aware**: warns you to disable *MIUI Battery Saver*
- 🎨 **5 UI colours**: Breeze Magenta, Green, Dark Mode, White, Rainbow 🌈
- 🛑 **Godot mods are rejected** with a clear error
- ⚙️ **Auto-built by GitHub Actions**: APK and source zip as artifacts

## 🚀 How to use

1. Open **PlusPatcher** and tap **Select Baldi APK**.
2. Tap **Select PC mod** and choose your `.zip` / `.rar`.
3. Tap **Patch**. It keeps running in the background.
4. When it says *Patched & signed!*, tap **Export** and save the APK.
5. **Uninstall the original Baldi app first** (the signature is different), then install the patched APK.

> 📱 **Xiaomi / Redmi / POCO:** go to settings and disable **MIUI Battery Saver** for PlusPatcher so patching keeps going in the background.

## 🧠 What gets patched

| Mod content | Result |
|---|---|
| `StreamingAssets/...` files | ✅ Copied into the APK's `assets/` |
| Loose files (audio, textures, bundles) | ✅ Copied into `assets/` |
| `Assembly-CSharp.dll` (code mods like *speed up Baldi*) | ⚠️ Swapped in **only on Mono APKs** |
| Code mods on **IL2CPP** APKs | ❌ Not possible (code is native `.so`) |
| PC-only `*_Data` internals, `.exe`, `.pdb` | ⏭️ Skipped |
| Godot mods (`.pck`, `.gd`, `.tscn`, …) | 🛑 Rejected |

**Tip:** open your APK as a zip. If `assets/bin/Data/Managed/Assembly-CSharp.dll` exists, it's Mono. If you see `lib/arm64-v8a/libil2cpp.so`, it's IL2CPP.
A swapped DLL must match the APK's Baldi and Unity version, or the game may crash. Keep a backup of the original APK.

## 🛠️ Build it yourself

**With GitHub Actions (easiest):** fork or upload this repo, open the **Actions** tab, and run **Build PlusPatcher**. Download `PlusPatcher-apk` or `PlusPatcher-source` from the run's artifacts.

**Locally:** needs JDK 17, the Android SDK and Gradle 8.7.
```bash
keytool -genkeypair -keystore app/src/main/assets/pp.p12 -storetype PKCS12 \
  -storepass plusplus -keypass plusplus -alias pp -keyalg RSA -keysize 2048 \
  -validity 10000 -dname "CN=PlusPatcher"
gradle assembleDebug
```

## 📜 Credits & license

Made by **tielbirb** (2026).
Not affiliated with the Baldi's Basics Modding Team, Basically Games, or Unity.
Licensed under the [Apache License 2.0](LICENSE).

<div align="center">⭐ Star the repo if PlusPatcher helped you!</div>
