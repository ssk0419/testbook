1、开发者自有H5网站用户在H5网站客户端上点击变现产品的入口（例如：“视频直播”），向网站服务端发起跳转请求。

2、App服务端（开发者）接受到跳转请求之后，拼接url ，同时将下表中的参数值进行md5签名，在App服务端（开发者）生成一个带签名的URL，返回给App客户端（开发者）。App客户端（开发者）通过这个带签名的URL访问变现猫的服务器。

**变现产品URL（变现猫提供）：**

* 直播url：[http://live.bianxianmao.com/redirect.htm](http://live.bianxianmao.com/redirect.htm)

* 爆款特卖url：[http://buy.bianxianmao.com](http://buy.bianxianmao.com/)

* 书城：[http://bookopen.bianxianmao.com/redirect.htm](http://bookopen.bianxianmao.com/redirect.htm)

* 校园书城：[http://bookopen.bianxianmao.com/redirect.htm?edu=1&](http://bookopen.bianxianmao.com/redirect.htm?edu=1&)

* 广告：[http://buy.bianxianmao.com/common/awardModel/ggk.html](http://buy.bianxianmao.com/common/awardModel/ggk.html)

* 广告js：&lt;script id="enter" appkey="appkey替换掉" src="[http://buy.bianxianmao.com/common/awardModel/js/img.js](http://buy.bianxianmao.com/common/awardModel/js/img.js)" bottom="65px" top="" right="20px" left="" appEntrance="1" width="65px" height="auto" business="money"&gt;&lt;/script&gt;

* 福利社：[https://fuli.bianxianmao.com](https://fuli.bianxianmao.com/)

* 积分商城：[https://jifen.bianxianmao.com](https://jifen.bianxianmao.com/)

* **URL参数列表说明（开发者提供）：**

| 参数名 | 是否必须 | 参数类型 | 限制长度 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| **appKey** | yes | string | 255 | 接口appKey，应用的唯一标识（在开发者后台接口配置处可查看） |
| **appUid** | yes | string | 255 | app用户id，需保证唯一性，可以为手机标识等唯一id。变现猫视其为用户唯一标识。 （无账户体系、用户未登录时传递not\_login标识，默认为not\_login） |
| **appType** | yes | string | 20 | 应用类型：h5 |
| **timestamp** | yes | long | 20 | 服务器当前时间，1970-01-01开始的时间戳，毫秒为单位。 例如：2016-12-05 14:56:25 940 timestamp＝1480920985940 |
| **sign** | yes | string | 32 | MD5签名,将URL中每个参数值和appSecret\(appSecret在开发者后台接口配置处可查看密钥）按照参数名称升序，拼接然后md5转码。 详见[http://www.bianxianmao.com/](http://www.bianxianmao.com/)doc/md5\_qian\_ming\_gui\_ze\_ji\_demo.html\) |
| **nickName** | no | string | 50 | 昵称，不传系统会默认生成 |
| **face** | no | string | 225 | 用户头像url |
| **mobile** | no | string | 11 | 手机号 |
| **sex** | no | string | 1 | 性别（男：1，女：0） |
| **appEntrance** | no | string | 50 | 入口链接ID，在开发者后台配置。用来区分不同的入口，方便后期统计、分析不同入口带来的uv、pv、订单转化 |
| **appHomeUrl** | no | string | 225 | 返回对接方应用的 url |
| **redirect** | no | string | 225 | 未登录情况下，app用户登录成功后的变现猫系统重定向地址，当跳到对接方app登录页面时redirectLoginUrl地址中的redirect参数就是用户最后操作的变现猫产品页面URL，默认为空时跳转到相应产品首页 |
| **redirectLoginUrl** | no | string | 225 | 唤起登录url固定值：bianxianmaoAppLogin，当app以游客模式访问，需要唤起登录时传递此参数\(此参数不参与签名\) |

3、变现猫的服务端在收到请求之后，验证签名，并获取appKey、appUid及其他用户信息，并为App客户端返回请求的模块页面

**备注：**

①URL经过签名后，该URL地址5分钟失效，不可事先生成免登录URL地址，否则5分钟后用户访问该地址过期

②每次向服务端的请求链接都是唯一（不相同）的，否则可能会被客户端缓存，在请求后面务必要带上时间戳

**③所有参数都要进行utf-8进行URL编码，所有url都要以**[**http://或https://开头**](http://xn--https-wm6j/%E5%BC%80%E5%A4%B4)

4、免登陆url生成之后验证无误就表示系统对接完成了

**注意事项：**

①变现猫会验证url的签名，时间戳5分钟内有效。因此客户端跳 转到变现猫的链接不可以写死，必须实时签名，否则会出现“登录超时”的问题

②必须保障秘钥的安全性。在服务端保存密钥，在服务端进行url 签名。不允许在客户端保存秘钥，不允许在客户端签名，否则容易被破解，泄漏秘钥，带来安全隐患

③签名时注意参数名大小写不能错

④参数中有带url的请用utf-8进行URL编码，否则获取不到，javaURL编解码详见[http://blog.csdn.net/u011627980/article/details/50911249](http://blog.csdn.net/u011627980/article/details/50911249)

⑤免登陆url的参数sign要根据参数名升序排列后将参数值拼接成字符串再进行MD5转码

⑥免登陆url中不包括签名秘钥appSecret，免登陆url参数不需要排序，切记

