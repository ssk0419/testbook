**当用户在未登录状态下直接进入变现产品，当用户有登录需要时，唤起所在App客户端的登录。**

**实现方式：**

1、参数设置

在免登陆参数中设置（此参数不参与签名）:redirectLoginUrl=bianxianmaoAppLogin

2、客户端处理

```
-(BOOL) webView:(UIWebView *)WebView shouldStartLoadWithRequest:(NSURLRequest *)request navigationType:(UIWebViewNavigationType)navigationType{

NSString *requestStr=[[request.URL absoluteString] stringByRemovingPercentEncoding];

if([requestStr hasPrefix:@"objc://"]){

//解析参数
    NSArray *requestArray = [requestStr componentsSeparatedByString:@"login:/"];

NSString *redirect = requestArray[1];

//唤起自身app登录页面，登录完成后拼接redirect生成有帐号体系的免登陆URL
}

return YES;

}
```



