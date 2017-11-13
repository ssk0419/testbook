**由于变现猫接入的支付宝支付类型为支付宝手机网站支付，如果app（安卓）没有接入过支付宝支付，可能存在在app中无法唤起支付宝客户端问题，如果出现这种情况则:**

在客户端加入以下代码，重写webview加载方法，以下代码为安卓处理方式：

```
//android WebView相关设置
mWebView.setWebViewClient(new PayWebViewClient());
//实现代码
class PayWebViewClient extends WebViewClient {

public boolean shouldOverrideUrlLoading(final WebView view, String url) {

System.out.println("url=" + url);

Uri uri = Uri.parse(url);

if (url.startsWith("http:") || url.startsWith("https:")) {

return false;

} else if ("alipays".equals(uri.getScheme())||"weixin".equals(uri.getScheme())) {//支付宝支付或微信支付

try {

Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));

startActivity(intent);

} catch (ActivityNotFoundException notFoundEx) {//尝试h5网页支付

return true;

}

}

return true;

}

}
```



