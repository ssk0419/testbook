在选择无账号对接的情况下，开发者可在“开发者后台-对接”中直接获取相应已拼接完成的变现产品的url。将url打开后的h5页面嵌套在自有H5产品的webview中即可实现对应变现产品的接入。

**注意：**

①url由变现产品的产品链接和开发者产品的相关参数拼接而来，其中有的链接包含了开发者产品的非必选的参数，有的未包含，开发者可自行根据需求对变成产品URL进行对应参数的拼接和删除。其中开发者产品参数表如下。

**开发者产品参数列表说明**：

| **参数名** | **是否必须** | **参数类型** | **限制长度** | **参数说明** |
| :--- | :--- | :--- | :--- | :--- |
| **appKey** | yes | string | 255 | 接口appKey，开发者产品的唯一标识（在后台接口配置获取[http://www.bianxianmao.com/](http://www.bianxianmao.com/)manage/account/info.html，注意：Key首字母大写） |
| **appType** | yes | string | 20 | 应用类型：必须为h5 |
| **appEntrance** | no | String | 50 | 入口链接ID，在开发者后台配置。 用来区分不同的入口，方便后期统计、分析不同入口带来的uv 、pv 、订单转化 |
| **appHomeUrl** | no | string | 225 | 返回开发者产品的url\(请用utf-8进行URL编码，防止中文乱码,javaURL编解码详见[http://blog.csdn.net/u011627980/](http://blog.csdn.net/u011627980/)article/details/50911249\) |

②appEntrance为非必选参数，开发者需在自有产品的不同入口部署变现产品时，可在开发者后台配置入口及其AppEntrance值。为方便后期统计、分析不同入口带来的uv 、pv 、订单转化，开发者可在变现产品url后拼接上AppEntrance参数

福利社链接后添加AppEntrance示例：[http://fuli.bianxianmao.com?appKey=468f8023e69b42b58ddfa2a54611fd1d&appType=h5&appEntrance=1](http://fuli.bianxianmao.com/?appKey=468f8023e69b42b58ddfa2a54611fd1d&appType=h5**&appEntrance=1**)

③appHomeUrl为非必选参数，此参数一般用于开发者H5产品，开发者需要在变现产品中直接返回自有产品某个页面，可在变现产品url后拼接上appHomeUrl参数

福利社链接后添加appHomeUrl示例（此处appHomeUrl取[www.bianxianmao.com](http://www.bianxianmao.com/)为例）：

[https://fuli.bianxianmao.com?appKey=468f8023e69b42b58ddfa2a54611fd1d&appType=app&appEntrance=1&appHomeUrl=http%3A%2F%2Fwww.bianxianmao.com](https://fuli.bianxianmao.com/?appKey=468f8023e69b42b58ddfa2a54611fd1d&appType=app&appEntrance=1&appHomeUrl=http%3A%2F%2Fwww.bianxianmao.com)

