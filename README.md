# AI Viral Clipper Pro

Android app project built with Kotlin, Jetpack Compose, Gemini video analysis, and AndroidX Media3.

## Build an APK with GitHub Actions

The repository includes `.github/workflows/build-apk.yml`. It installs JDK 21, Gradle 9.3.1, Android SDK Platform 36 and Build Tools 36.0.0, creates a temporary debug signing key, and runs the Android debug build.

### Upload this project from an Android phone

1. Download this complete ZIP and extract it on your phone.
2. Create a new **public or private** GitHub repository named `AI-Viral-Clipper-Pro`.
3. Upload the **contents inside** the extracted `clipper_final_work` folder to the repository root. Do not upload the outer folder as an extra nested folder.
4. Confirm that `app`, `gradle`, `.github`, `build.gradle.kts`, and `settings.gradle.kts` are visible at the repository's main page.
5. Open the repository's **Actions** tab. Allow GitHub Actions if GitHub asks.
6. Open **Build AI Viral Clipper Pro APK** and tap **Run workflow**. A push to `main` or `master` also starts a build automatically.
7. Wait for the run to finish. Open the successful run, scroll to **Artifacts**, and download `AI-Viral-Clipper-Pro-APK`.
8. Extract the downloaded artifact ZIP. It contains `AI-Viral-Clipper-Pro.apk`.

The workflow produces a **debug-signed APK** for testing and direct installation. It is not a Play Store release signing setup. Keep the same signing key if you later want to update an installed release build; this workflow generates a temporary key for each run, so successive builds may not install as updates over one another.

## Gemini API key

1. Install the APK.
2. Open the app's Settings screen.
3. Paste the Gemini API key you created in Google AI Studio and save it.
4. Select a video from your phone's Gallery and start analysis.

Do not add a real API key to GitHub, source files, or this ZIP. The app stores the key encrypted at rest with Android Keystore, but a key used directly by a client-side APK is not fully secret. Restrict the key and monitor usage in Google AI Studio.

## Current implementation status

Implemented in this source revision:

- Gallery video selection and reading the actual video duration.
- Gemini Files API upload and video-moment analysis.
- Candidate clip titles, timestamps, estimated scores, and explanations.
- On-device MP4 trimming with AndroidX Media3 Transformer.
- Exported MP4 files saved to `Movies/AI Viral Clipper`.
- Local encrypted storage for the Gemini API key.

Not yet implemented or fully verified:

- Automatic speech-to-text captions with word-level timing and burned-in subtitle rendering.
- Actual 9:16 reframing/cropping in exported videos. Aspect-ratio selection is currently only a saved editor preference.
- Downloading arbitrary public YouTube videos from a URL. Use a video file you own or are authorized to edit. The app does not bypass YouTube restrictions.
- A successful clean Android build and physical-device test have not yet been confirmed from this development environment. The GitHub workflow is provided to perform the build; if it fails, open the run's log and the uploaded build reports to identify the first error.

AI scores are estimates, not a guarantee that a clip will go viral. Video files are uploaded to Google's Gemini API for analysis, so internet data is required and Google's applicable terms and quotas apply.

## Project files

- `app/`: Android app source, resources, and manifest.
- `gradle/libs.versions.toml`: dependency and plugin versions.
- `gradle.properties`: Gradle build settings.
- `build.gradle.kts`, `settings.gradle.kts`: root Gradle configuration.
- `.github/workflows/build-apk.yml`: automatic GitHub Actions APK build.
- `PROJECT_STATUS_AND_TESTS.md`: implementation and verification notes.
