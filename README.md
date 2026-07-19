# ActivityLauncher v8 builder

This repository builds a patched APK from the upstream
[ActivityLauncher](https://github.com/ActivityLauncher/ActivityLauncher) source.

The workflow:

1. checks out the selected upstream ref;
2. applies `patches/activitylauncher.patch`;
3. runs Spotless and the OSS/no-ads unit tests;
4. builds `assembleOssNoadsDebug`;
5. creates a GitHub Release and publishes the APK as a release asset.

Run it from **Actions → Build ActivityLauncher v8 → Run workflow**. The default
application version is `8.0.0` with version code `8`; both can be overridden
from the workflow dispatch form. Each successful run gets a unique build tag
such as `v8.0.0-build.12.1`.

The patch adds the Shizuku+ launcher, JVM/native process executors, per-user
enable/disable controls for applications and activities, and the static
APK/developer audit. It does not bundle the supplied system binaries or
attempt password brute-force/extraction.

The build is intentionally unsigned debug output. Sign it separately with a
trusted release key before distribution.
