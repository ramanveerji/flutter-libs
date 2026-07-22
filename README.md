# flutter-libs

This repository allows building native Flutter shared libraries (`libflutter.so`) for Android (`arm64-v8a` and `armeabi-v7a`) for specific Flutter SDK versions or Dart SDK versions directly via GitHub Actions.

# How to use this repo?

## 1. Enabling Workflows (in Forked Repositories)
1. Fork this repository.
2. Go to **Settings** in your forked repo.
3. Select **Actions** -> **General** on the left side pane.
4. Under **Workflow permissions**, select **Read and write permissions** and save.

## 2. Generating Flutter Libs
1. Go to the **Actions** tab in your repository.
2. Select the **Flutter Build** workflow on the left sidebar.
3. Click the **Run workflow** dropdown button.
4. In the **version** box, type **EITHER**:
   - A **Dart SDK Version** (e.g. `3.5.4` or `2.19.6`), OR
   - A **Flutter Version** (e.g. `3.27.1` or `3.38.9`).
5. (Optional) Check **Build for armeabi-v7a (32-bit ARM)** if you also need 32-bit ARM binaries (disabled by default).
6. Click **Run workflow**.
7. The workflow will automatically look up the official Flutter release matching the Dart SDK version, build `libflutter.so`, and publish the binaries to **Releases**.

# Finding the correct Flutter version from Dart version manually
1. To find the correct Flutter version manually, visit the [Flutter Release Archive](https://docs.flutter.dev/release/archive). 
2. Find the **Dart version** for which you want to build Flutter libs.
3. Locate the corresponding **Flutter version** in the same row.
4. Enter that Flutter version into the workflow prompt.

# Notes
1. There are 2 workflows present in this repository:
   - **Flutter Build**: Builds native libraries and publishes them to GitHub Releases.
   - **GitHub Cleanup**: Cleans up older action run logs periodically to keep the repository history clean while preserving all generated releases.
