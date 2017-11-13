**当用户在未登录状态下直接进入变现产品，当用户有登录需要时，唤起所在App客户端的登录。**

**实现方式：**

* 使用JavaScriptInterface接口，添加如下代码：

1.参数设置：

在免登陆参数中设置（此参数不参与签名）：redirectLoginUrl=bianxianmaoAppLogin

2.App客户端设置

//android WebView相关设置

```
mWebView.addJavascriptInterface(new JsInterface(this), "bianxianmao");
webSettings.setJavaScriptEnabled(true);
```

//实现JsInterface

```
private class JsInterface {
private Context mContext;
public JsInterface(Context context) {
this.mContext = context;
}
@JavascriptInterface
public void onLoginClick(String redirectUrl) {
//打印原生js返回的请求参数 Log.i("onLoginClick","redirectUrl="+redirectUrl);
//唤起app登录，同时将currentUrl设置到免登录的redirect参数中
}
}
```



