**MD5签名SDK下载（JAVA/PHP/.NET）：**[**http://www.bianxianmao.com/doc/MD5SignSDK.zip**](http://www.bianxianmao.com/doc/MD5SignSDK.zip)

**Java MD5签名实现**

参考示例：[http://blog.csdn.net/u011627980/article/details/52778326](http://blog.csdn.net/u011627980/article/details/52778326)

**签名规则：**

变现猫与开发者之间所有的请求进行md5签名，确保传输的安全可靠。

**签名原理：**

md5签名的原理如下：**将所有的参数值与appSecret按参数名升序进行排列**。

```
Md5(value1+value2+...appSecret...+valueN)

```

appSecret在签名中的顺序取决于他在所有参数名中的顺序。

**注意：**签名验证时，必须遍历request请求中的所有参数，进行签名验证。变现猫向开发者发起的请求，未来有可能会添加业务参数，开发者在验证请求时，务必对所有参数进行遍历，全部加入签名验证数据中。

如果开发者写死签名验证参数，未来变现猫升级参数将导致开发者服务不可用，请谨慎。

**签名规则测试用例：**

为了方便开发者对签名方法进行测试验证，下面提供几个测试用例，开发者可以参考下面的用例，使用相同的输入参数，看产生的签名与我们提供的签名是否一致。

```
原参数列表：
appKey=9f676b9b496f44ff9bb81ae6ed3e9360,
appUid=1,
sex=0,
appType=app,
mobile=13366668888,
nickName=变现猫,
appEntrance=1,
appHomeUrl=http://www.bianxianmao.com,
face=http://www.bianxianmao.com/web/images/logo-08.png,
redirect=http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/home,
redirectLoginUrl=http://www.bianxianmao.com/login.html,
timestamp=1480925973841

按参数名升序排列后的参数列表（带appSecret）：
appEntrance=1,
appHomeUrl=http://www.bianxianmao.com,
appKey=9f676b9b496f44ff9bb81ae6ed3e9360,
appSecret=fc2ce7ee45ae45729932b25d6d2607b9,
appType=app,
appUid=1,
face=http://www.bianxianmao.com/web/images/logo-08.png,
mobile=13366668888,
nickName=变现猫,
redirect=http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/home,
redirectLoginUrl=http://www.bianxianmao.com/login.html,
sex=0,
timestamp=1480925973841
```

```
MD5签名appSecret秘钥：fc2ce7ee45ae45729932b25d6d2607b9

待签名原串（带appSecret）： 1http://www.bianxianmao.com9f676b9b496f44ff9bb81ae6ed3e9360fc2ce7ee45ae45729932b25d6d2607b9app1http://www.bianxianmao.com/web/images/logo-08.png13366668888变现猫http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/homehttp://www.bianxianmao.com/login.html01480925973841
```

```
MD5签名后的sign字符串为： a8695e677323a90199c82b0201caeacc

```

签名后的URL：

```
http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/home?face=http%3A%2F%2Fwww.bianxianmao.com%2Fweb%2Fimages%2Flogo-08.png&sex=0&appEntrance=1&appHomeUrl=http%3A%2F%2Fwww.bianxianmao.com&sign=a8695e677323a90199c82b0201caeacc&timestamp=1480925973841&nickName=%E5%8F%98%E7%8E%B0%E7%8C%AB&redirect=http%3A%2F%2F1.migree.com.cn%2Fqmdb%2Fshop%2Fweixin%2Findex.html%23%2Ftab%2Fhome&appUid=1&redirectLoginUrl=http%3A%2F%2Fwww.bianxianmao.com%2Flogin.html&appType=app&appKey=9f676b9b496f44ff9bb81ae6ed3e9360&mobile=13366668888
```



