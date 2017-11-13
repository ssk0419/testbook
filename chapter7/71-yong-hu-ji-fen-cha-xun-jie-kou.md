## **接口说明** {#接口说明}

**该接口由开发者开放给变现猫，变现猫进行调用。**

这个请求参数为appUid、AppKey、时间戳等信息，并对请求参数进行MD5签名。开发者收到该请求后，需要对签名进行验证，验证通过后请返回积分信息给变现猫。

**接口地址：在开发者后台接口配置模块配置**\(URL以http:\/\/开头\)

```
示例：http://www.xxx.com/api/getAppPointApi.json

```

**输入参数：**

| **参数** | **是否必须** | **参数类型** | **限制长度** | **参数说明** |
| :--- | :--- | :--- | :--- | :--- |
| appUid | yes | string | 255 | app用户id |
| appKey | yes | string | 255 | 接口appKey，应用的唯一标识 |
| timestamp | yes | string | 20 | 服务器当前时间，1970-01-01开始的时间戳，毫秒为单位。 |
| sign | yes | string | 255 | MD5签名,将URL中每个参数值和appSecret（appSecret在开发者后台接口配置处可查看密钥）按照参数名称升序，拼接然后md5转码 详见MD5签名规则[http://www.bianxianmao.com/doc/md5.html](http://www.bianxianmao.com/doc/md5.html)） |

**响应参数：**

| **参数** | **是否必须** | **参数类型** | **限制长度** | **参数说明** |
| :--- | :--- | :--- | :--- | :--- |
| status | yes | string | 255 | 查询状态，回复ok或者fail |
| errorMessage | no | string | 255 | 出错原因\(请用utf-8进行URL编码，防止中文乱码,javaURL编解码详见[http://blog.csdn.net/u011627980/article/details/50911249](http://blog.csdn.net/u011627980/article/details/50911249)\) |
| point | yes | number数字 | 20 | app用户积分余额 |

请按JSON格式返回结果。

**响应示例：**

成功：

```
{
'status': 'ok',
'errorMessage': '',
'point': '1000'
}

```

失败：

```
{
'status': 'fail',
'errorMessage': '失败原因（通知变现猫）'
}

```

**请求超时处理方式：**

变现猫向开发者发起查询积分请求时，变现猫设置超时时间为30秒，由于开发者服务器响应过慢，或者网络异常等原因，可能会出现超时情况。如果请求超时，变现猫将在该笔交易中取消积分兑换方式。

