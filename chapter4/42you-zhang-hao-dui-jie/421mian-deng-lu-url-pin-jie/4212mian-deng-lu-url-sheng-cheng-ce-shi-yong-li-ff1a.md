**为了方便开发者对免登陆URL进行测试验证，下面提供一个测试用例，开发者可以参考下面的用例，使用相同的输入参数，看产生的签名与我们提供的签名是否一致。**

原参数列表：

```
appKey=77f869f734cc43d4b9357a66fd280626,
appUid=1,
sex=0,
mobile=13366668888,
nickName=变现猫,
appEntrance=1,
appHomeUrl=
http://www.bianxianmao.com,
appType=app,
face=
http://www.bianxianmao.com/web/images/logo-08.png,
redirect=
http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/home,
redirectLoginUrl=
http://www.bianxianmao.com/login.html,
timestamp=1480924587450
按参数名升序排列后的参数列表（带appSecret）：
appEntrance=1,
appHomeUrl=
http://www.bianxianmao.com,
appKey=77f869f734cc43d4b9357a66fd280626,
appSecret=6c3c4ddb98ee49b593b735545aaac4a4,
appType=app,
appUid=1,
face=
http://www.bianxianmao.com/web/images/logo-08.png,
mobile=13366668888,
nickName=变现猫,
redirect=
http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/home,
redirectLoginUrl=
http://www.bianxianmao.com/login.html,
sex=0,
timestamp=1480924587450
MD5签名秘钥appSecret为：6c3c4ddb98ee49b593b735545aaac4a4
待签名原串（带appSecret）：1
http://www.bianxianmao.com77f869f734cc43d4b9357a66fd2806266c3c4ddb98ee49b593b735545aaac4a4app1http://www.bianxianmao.com/web/images/logo-08.png13366668888变现猫http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/homehttp://www.bianxianmao.com/login.html01480924587450

MD5签名后的sign字符串为：ae1876a5fdd84575325aacc87bfbb5df
签名后的URL：

http://1.migree.com.cn/qmdb/shop/weixin/index.html#/tab/home?face=http%3A%2F%2Fwww.bianxianmao.com%2Fweb%2Fimages%2Flogo-08.png&sex=0&appEntrance=1&appHomeUrl=http%3A%2F%2Fwww.bianxianmao.com&sign=ae1876a5fdd84575325aacc87bfbb5df&timestamp=1480924587450&nickName=变现猫&redirect=http%3A%2F%2F1.migree.com.cn%2Fqmdb%2Fshop%2Fweixin%2Findex.html%23%2Ftab%2Fhome&appUid=1&redirectLoginUrl=http%3A%2F%2Fwww.bianxianmao.com%2Flogin.html&appType=app&appKey=77f869f734cc43d4b9357a66fd280626&mobile=13366668888
```



