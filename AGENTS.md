# Melodify Android Fork — Project Guidelines & Rules (AGENTS.md)

Read this file before starting any task or writing any code in this repository.

---

## 1. Project Details

- **Local Path:** `D:\Personal\SHHH\Projects\Melodify-Android-forked`
- **Fork Remote (origin):** `https://github.com/yugdabgar21/Melodify-Android`
- **Upstream Remote (upstream):** `https://github.com/UranophileLab/Melodify-Android`
- **Assigned Issue:** [Issue #11: ui/ ux enhancement](https://github.com/UranophileLab/Melodify-Android/issues/11)

---

## 2. Core Operational Rules (Strictly Enforced)

1. **No Android Studio:**
   - Do not require or open Android Studio. All builds are triggered and handled via CI/CD pipelines.

2. **No Local Gradle / SDK CLI Tests:**
   - **Never run `./gradlew assemble...` or `./gradlew test...` on the local machine.**
   - Local CLI building and testing is slow, resource-heavy, and battery consuming. We fully rely on GitHub Actions for compiling and packaging.

3. **Development & Testing Cycle:**
   - **Step 1:** Investigate and propose UI/UX changes.
   - **Step 2:** Get approval from the user before applying significant changes.
   - **Step 3:** Commit and push changes to the fork on GitHub.
   - **Step 4:** GitHub Actions builds the `Melodify-Debug-APK` and publishes it as an artifact.
   - **Step 5:** User downloads the Debug APK and tests it directly on their physical Android phone.
   - **Step 6:** Only when phone testing passes does the team move to the next screen/feature.

4. **GitHub Actions Workflow Structure (`.github/workflows/apk.yml`):**
   - Modeled after the Ivy Wallet workflow:
     - **Active Job:** `debug_apk` — builds and uploads the Debug APK artifact (`Melodify-Debug-APK`) on every push/PR so the user can download and test immediately.
     - **Commented Job:** `optimized_apk` — reserved for the final release/optimized APK build. **Keep this job commented out** while iterations and subtasks are ongoing. Uncomment only when all tasks are complete and fully tested.

---

## 3. Issue #11 Objectives (UI/UX Enhancement)

The goal is to modernize the music player experience, drawing inspiration from **Echo** and **Auris** music players:
- **Visual Style:** Clean, minimalist layout, smooth transitions, rounded corners, modern padding/margins.
- **Theme & Palette:** Modern dark and light theme support with subtle glassmorphism / transparency effects where appropriate.
- **Typography & Spacing:** Clear visual hierarchy, balanced padding, readable font weights and sizes.

### Target Screens & Subtasks:
1. **Home Screen (`MainActivity` & fragments/layouts):**
   - Modernized album/playlist grid and cards.
   - Clean recent tracks list with sleek item views.
   - Polished bottom navigation and top app bar.
2. **Now Playing Screen (`MusicOverviewActivity`):**
   - Large, rounded album artwork with smooth drop shadow / elevation.
   - Sleek seekbar / progress bar with easy scrub interaction.
   - Intuitive, modern playback control buttons (play/pause, skip, shuffle, repeat, favorite).
3. **Mini Player:**
   - Floating or docked smooth bottom player bar with clear track title, artist, progress indicator, and quick play/pause controls.
4. **Library & Playlists (`ListActivity`, `SavedLibrariesActivity`, `FavoritesActivity`):**
   - Organized list layout with rounded item shapes and easy-to-tap action buttons.

---

## 4. Communication & Reporting Rules

- **Explain in Layman's Terms:**
  - Always explain what you investigated, what you plan to change, and what the user will see on their screen in simple, non-jargon language.
  - State any potential risks or edge cases clearly.
- **Approval Gates:**
  - Break work down into manageable steps (one screen/subtask at a time).
  - Never jump ahead to the next screen until the user has tested the APK on their phone and approved the current step.

