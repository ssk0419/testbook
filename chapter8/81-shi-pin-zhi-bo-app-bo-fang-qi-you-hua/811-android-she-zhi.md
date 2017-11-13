**添加硬件加速的配置可以提高播放流畅度，提高用户体验，以下是相关代码**

```
Application
android:hardwareAccelerated="true"
getWindow().addFlags(WindowManager.LayoutParams.FLAG_HARDWARE_ACCELERATED)
用于webview设置

getSettings().setJavaScriptEnabled(true);
 //addJavascriptInterface(this.a, "etouch_client");
 WebSettings settings = getSettings();
 // settings.setJavaScriptCanOpenWindowsAutomatically(true);
 settings.setLayoutAlgorithm(LayoutAlgorithm.NARROW_COLUMNS);
 settings.setSupportMultipleWindows(false);
 settings.setDefaultTextEncodingName("UTF-8");
 settings.setRenderPriority(RenderPriority.HIGH);
 inti = VERSION.SDK_INT;
 try {
 settings.setAllowFileAccess(true);
 if (i>= 5) {
 settings.setDatabaseEnabled(true);
 settings.setGeolocationEnabled(true);
 }

 if (i>= 7) {
 settings.setAppCacheEnabled(true);
 settings.setDomStorageEnabled(true);
 settings.setUseWideViewPort(true);
 settings.setLoadWithOverviewMode(true);
 }
 if (i>= 8) {
 settings.setPluginState(PluginState.ON);
 }
 settings.setBuiltInZoomControls(false);
 settings.setSupportZoom(false);
 settings.setAppCachePath(context.getCacheDir().getAbsolutePath());
 } catch (Exception e) {
 }

 setScrollBarStyle(0);
```



