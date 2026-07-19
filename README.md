# ActivityLauncher v8 builder

This repository builds a patched APK from the upstream
[ActivityLauncher](https://github.com/ActivityLauncher/ActivityLauncher) source.

The workflow:

1. checks out the selected upstream ref;
2. applies `patches/activitylauncher.patch`;
3. runs Spotless and the OSS/no-ads unit tests;
4. builds `assembleOssNoadsDebug`;
5. uploads the APK as the `ActivityLauncher-v8` artifact.

Run it from **Actions → Build ActivityLauncher v8 → Run workflow**. The default
application version is `8.0.0` with version code `8`; both can be overridden
from the workflow dispatch form.

The patch adds the Shizuku+ launcher, JVM/native process executors and the
static APK/developer audit. It does not bundle the supplied system binaries or
attempt password brute-force/extraction.

The build is intentionally unsigned debug output. Sign it separately with a
trusted release key before distribution.
