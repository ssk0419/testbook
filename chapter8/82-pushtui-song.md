## **推送接口说明** {#推送接口说明}

**Push推送主要用于变现产品和开发者自有产品的信息同步，例如视频直播上线通知等信息，开发者通过接口获取消息后，在客户端进行消息推送。**

**该接口由变现猫开放给开发者，开发者进行调用。**

这个请求参数为appKey、timestamp等信息，并对请求参数进行MD5签名。开发者收到该请求后，需要对签名进行验证，验证通过后变现猫返回push信息给开发者。

**接口地址：在开发者后台接口配置模块配置**\(URL以http:\/\/开头\)

```
http://push.bianxianmao.com/notice/push

```

**输入参数：**

| **参数** | **是否必须** | **参数类型** | **限制长度** | **参数说明** |
| :--- | :--- | :--- | :--- | :--- |
| appKey | yes | string | 255 | 接口appKey，应用的唯一标识 |
| timestamp | yes | string | 20 | 服务器当前时间，1970-01-01开始的时间戳，毫秒为单位。 |
| sign | yes | string | 255 | MD5签名,将URL中每个参数值和appSecret（appSecret在开发者后台接口配置处可查看密钥）按照参数名称升序，拼接然后md5转码 详见MD5签名规则[http://www.bianxianmao.com/doc/md5.html](http://www.bianxianmao.com/doc/md5.html)） |
| page | no | number | 无限制 | 分页页码，不传参数默认第1页 |
| rows | no | number | 1000 | 分页条数，最大限制1000条每页,不传参数默认100条每页 |

**响应HTTP状态码：**

| **状态码** | **含义** | **说明** |
| :--- | :--- | :--- |
| 200 | 正常 | 请求成功并正常返回 |
| 400 | 参数错误 | 发送的请求参数不正确，如: 必须的参数没有传递等 |
| 401 | 签名检验错误 | 签名没有传递或者不正确 |
| 403 | 处理错误 | 发送的请求在接口层面处理出现错误，如: 用户名必须唯一 而创建时传递了已经存在的用户名 |
| 404 | 目标错误 | 请求调用的目标不存在，如: appKey错误导致没有找到对应的接入app |
| 500 | 接口内部错误 | 接口内部反生错误，暂时不能响应请求。 |

**响应参数：**

| **参数** | **是否必须** | **参数类型** | **限制长度** | **参数说明** |
| :--- | :--- | :--- | :--- | :--- |
| msg | yes | string | 255 | 返回信息，OK表示成功，不成功回传出错具体信息\(请用utf-8进行URL解码，防止中文乱码,javaURL编解码详见[http://blog.csdn.net/u011627980/article/details/50911249](http://blog.csdn.net/u011627980/article/details/50911249)\) |
| code | yes | number | 无限制 | 出错编号 0表示正常 大于0都表示对应的错误编号 |
| data | yes | string | 无限制 | 返回数据对象, json格式字符串\(请用utf-8进行URL解码，防止中文乱码,javaURL编解码详见[http://blog.csdn.net/u011627980/article/details/50911249](http://blog.csdn.net/u011627980/article/details/50911249)\) |
| total\_numbers | yes | number | 无限制 | 推送信息总条数 |
| total\_pages | yes | number | 无限制 | 总页数 |
| current\_page | yes | number | 无限制 | 当前页 |
| page\_rows | yes | number | 无限制 | 分页条数 |

请按JSON格式返回结果。

**响应示例：**

成功：

```
http status code: 200

{
    'code': 0,
    'msg': 'OK',
    'data':
        [{
            "id": 16, 
            "account": "用户一号", 
            "channel": "luck_prize_rolling", 
            "content": "您购买的第1018期商品iphone7手机，马上就要开奖啦，请登录APP随时关注中奖结果。", 
            "status": "等待发送", 
            "created": 1494314420, 
            "created_show": "2017-05-09 15:20:20", 
            "updated": 1494314420, 
            "updated_show": "2017-05-09 15:20:20"
        },{
            "id": 18, 
            "account": "用户二号", 
            "channel": "luck_prize_rolling", 
            "content": "您购买的第1018期商品iphone7手机，马上就要开奖啦，请登录APP随时关注中奖结果。", 
            "status": "等待发送", 
            "created": 1494314417, 
            "created_show": "2017-05-09 15:20:17", 
            "updated": 1494314417, 
            "updated_show": "2017-05-09 15:20:17"
        }],
    'total_numbers': 2,
    'total_pages': 1,
    'current_page': 1,
    'page_rows': 100
}

```

失败：

```
http status code: 401

{
    'code': '1006',
    'msg': 'sign签名校验错误,请检查后重新传递'
}
```



