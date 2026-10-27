# Local patches over camera_android_camerax 0.6.30

- `CameraXLibraryPigeonProxyApiBaseCodec.writeValue`: when the plugin has detached
  from the engine (`ignoreCallsToDart`), reply `null` instead of throwing
  `IllegalArgumentException: Unsupported value` on the main thread. Happens when
  `ProcessCameraProvider.getInstance()` (or another async CameraX call) completes
  after the Activity/engine went away (Crashlytics, Android 17 on Pixel, 1.8.1).
  Still present upstream in 0.7.6; remove this override once fixed there.
