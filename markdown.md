# 话费充值平台V2.0

## 1 环境变量

### 接口

| 参数名 | 字段值 |
| --- | --- |
| baseurl | [http://域名/yrapi.php/](http://xn--eqrt2g/yrapi.php/) |

## 2 话费流量供应系统

## 2.1 接口说明

api提交方式：HTTP POST(表单) Content-Type：application/x-www-form-urlencoded  
充值回调方式：HTTP POST(表单) 参数格式实例：order\_number=1&amp;out\_trade\_num=1&amp;mobile=1&amp;otime=1&amp;state=1

## 2.2 签名说明

签名步骤：  
1、准备好所有待签名参数（所有”请求参数“或所有”回调参数“都要参数签名，除开sign字段，没个api传递的参数都不同，这句提示很重要）

2、生成签名字符串（参数名字典升序排序，apikey不参与排序，直接放最后，如后面示例进行组装）“a=1&amp;b=2&amp;c=3&amp;apikey=你的商户key”。(实际字段名并非是a、b、c这里只是演示)

3、对签名字符串进行大写md5，签名=md5(签名字符串)

特别说明：签名字符串不进行URL编码，如果使用php 的http\_build\_query拼装字符串时，会自动进行URL编码，建议对签名字符串进行一次URL解码 ；提交报文中不要包含秘钥，容易造成秘钥暴露且不能验签通过；

php签名实例（其它语言自行编写）：

~~~
//签名参数只是示例，并非真实提交数据
$param = [&quot;参数名称&quot;=&gt;&quot;参数值&quot;,...];
//字典排序
ksort($param);
//拼接签名串
$sign_str = http_build_query($param) . &#039;&amp;apikey=aaaaaaaaaaaaaaaaaaa&#039;;
//签名
$sign = strtoupper(md5(urldecode($sign_str)));
$param[&#039;sign&#039;] = $sign;
$httpdata = $param;

~~~

## 2.3 充值提交接口

&gt; POST[http://域名/yrapi.php/index/recharge](http://xn--eqrt2g/yrapi.php/index/recharge)

### 接口说明

&gt; 提交充值订单

### 请求体(Request Body)

| 参数名称 | 数据类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| out\_trade\_num | string | GG5822222266 | true | 商户订单号，由商户自己生成唯一单号。  
（同一商户，不能存在相同单号订单，相同订单号不能提单） |
| product\_id | number | 68 | true | 产品ID（代理后台查看） |
| mobile | string | 18866667777 | true | 充值号码（手机号、电费户、qq号等） |
| notify\_url | string | [http://www.abc.com](http://www.abc.com/) | true | 回调地址，用于接收充值状态回调 |
| userid | string | 10001 | true | 商户ID，通过客服或代理后台获取 |
| amount | number | 100 | false | 面值，（不传不校验）如果产品的面值与此参数不同，提单驳回 |
| price | number | 94.8 | false | 最高成本，（不传不校验）如果产品成本超过这个值，提单驳回 |
| area | string | 广东 | false | 电费省份/直辖市，如：四川、北京、上海，仅电费带此参数 |
| ytype | string | 1 | false | 电费验证三要素，1-身份证后6位，2-银行卡后六位,3-营业执照后六位，仅南网电费带此参数 |
| id\_card\_no | string | 123456 | false | 身份证后6位/银行卡后6位/营业执照后6位，仅南网电费带此参数 |
| city | string | 广州 | false | 地级市名，仅部分南网电费带此参数，是否带此参数需咨询渠道方 |
| param1 | string | \* | false | 扩展参数，后台查看提交的产品类目是否需要提交此参数 |
| param2 | string | \* | false | 扩展参数，后台查看提交的产品类目是否需要提交此参数 |
| param3 | string | \* | false | 扩展参数，后台查看提交的产品类目是否需要提交此参数 |
| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | 签名；签名规则见2.2“签名说明” |

~~~
请求示例：
out_trade_num=ABC1111&amp;product_id=11&amp;mobile=18899998888&amp;notify_url=http://www.abc.com/yuanren&amp;userid=10001&amp;sign=GZWDK8X7TGJFA8N8O9HILQ6WSI46C8FJ

~~~

### 响应体

● 响应数据格式：JSON，当“http状态非200”或者“响应体无数据时”可能是服务器或其他链路出现故障，无法准确判定是否成功下单，请通过订单查询或者人工方式再次确认状态。

| 参数名称 | 类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| errno | string | \* | true | 错误码，0代表成功，非0代表提交失败 |
| errmsg | string | \* | true | 错误描述 |
| data | object | \* | true | errno=0时 返回数据 |
| ⇥ order\_number | string | \* | true | 系统定单号 |
| ⇥ mobile | string | \* | true | 充值手机号 |
| ⇥ product\_id | string | \* | true | 产品ID |
| ⇥ total\_price | string | \* | true | 消费金额 |
| ⇥ out\_trade\_num | string | \* | true | 商户订单号 |
| ⇥ title | string | \* | true | 充值产品说明 |

~~~
响应示例：
{
    &quot;errno&quot;: 0,
    &quot;errmsg&quot;: &quot;下单成功&quot;,
    &quot;data&quot;: {
        &quot;order_number&quot;: &quot;XYZ111111&quot;,
        &quot;mobile&quot;: &quot;18866667777&quot;,
        &quot;product_id&quot;: 10001,
        &quot;total_price&quot;: &quot;95.00&quot;,
        &quot;out_trade_num&quot;: &quot;ABC1111&quot;,
        &quot;title&quot;: &quot;100元话费&quot;,
    }
}

~~~

## 2.4 查询用户信息

&gt; POST[http://域名/yrapi.php/index/user](http://xn--eqrt2g/yrapi.php/index/user)

### 请求体(Request Body)

| 参数名称 | 数据类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| userid | string | 1001 | true | 账号ID |
| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | 签名；签名规则见2.2“签名说明” |

### 响应体

● 响应数据格式：JSON

| 参数名称 | 类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| errno | string | \* | true | 错误码，0代表成功，非0代表失败 |
| errmsg | string | \* | true | 错误描述 |
| data | object | \* | true | errno=0时 返回数据 |
| ⇥ id | string | \* | true | userid |
| ⇥ username | string | \* | true | 名称 |
| ⇥ balance | string | \* | true | 余额 |

## 2.5 获取产品类型和产品分类

&gt; POST[http://域名/yrapi.php/index/typecate](http://xn--eqrt2g/yrapi.php/index/typecate)

### 请求体(Request Body)

| 参数名称 | 数据类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| userid | string | 1001 | true | 商户ID |
| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | 签名 |

### 响应体

● 响应数据格式：JSON

| 参数名称 | 类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| errno | string | \* | true | 返回0 |
| errmsg | string | \* | true | 错误描述 |
| data | object | \* | true | errno=0时 返回数据 |
| ⇥ id | string | \* | true | 产品类型id |
| ⇥ type\_name | string | \* | true | 产品类型名称 |
| ⇥ cate | array | \* | true | 分类列表 |
| ⇥⇥ id | int | \* | true | 分类ID |
| ⇥⇥ cate | string | \* | true | 分类名称 |
| ⇥⇥ type | string | \* | true | 产品类型ID |

## 2.5 获取产品

&gt; POST[http://域名/yrapi.php/index/product](http://xn--eqrt2g/yrapi.php/index/product)

### 请求体(Request Body)

| 参数名称 | 数据类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| userid | string | 10001 | true | 商户ID |
| type | int | 1 | false | 产品类型ID,非必须 |
| cate\_id | int | 10 | false | 分类ID,非必须 |
| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | 签名 |

### 响应体

● 响应数据格式：JSON

| 参数名称 | 类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| errno | string | \* | true | 错误码，0代表成功，非0代表失败 |
| errmsg | string | \* | true | 错误描述 |
| data | object | \* | true | errno=0时 返回数据 |
| ⇥ id | int | \* | true | 分类ID |
| ⇥ cate | string | \* | true | 分类名称 |
| ⇥ sort | string | \* | true | 排序 |
| ⇥ type | string | \* | true | 产品类型ID |
| ⇥ products | array | \* | true | 产品列表 |
| ⇥⇥ id | string | \* | true | 产品ID,下单报文中用此参数 |
| ⇥⇥ name | string | \* | true | 产品名称 |
| ⇥⇥ desc | string | \* | true | 产品说明 |
| ⇥⇥ api\_open | string | \* | true | 自动充值 |
| ⇥⇥ isp | string | \* | true | 运营商集合（话费、流量有效），1移动,2电信,3联通,4虚拟 |
| ⇥⇥ ys\_tag | string | \* | true | 标签 |
| ⇥⇥ price | string | \* | true | 价格，下单扣费金额 |
| ⇥⇥ y\_price | string | \* | true | 原价 |
| ⇥⇥ max\_price | string | \* | true | 封顶价格 |
| ⇥⇥ type | string | \* | true | 产品类型ID |
| ⇥⇥ cate\_name | string | \* | true | 产品分类名称 |
| ⇥⇥ type\_name | string | \* | true | 产品类型名称 |

## 2.6 自发查询订单状态

&gt; POST[http://域名/yrapi.php/index/check](http://xn--eqrt2g/yrapi.php/index/check)

### 请求体(Request Body)

| 参数名称 | 数据类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| userid | string | 10001 | true | 账户ID |
| out\_trade\_nums | string | CZH668877,CZH9988666 | true | 商户订单号；多个用英文,分割 |
| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | 签名 |

### 响应体

● 响应数据格式：JSON

| 参数名称 | 类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| errno | string | 0 | true | 错误码，0代表成功，非0代表失败 |
| errmsg | string | 查询成功 | true | 错误描述 |
| data | object | \* | true | errno=0时 返回数据 |
| ⇥ order\_number | string | CZH1111111 | true | 系统订单号 |
| ⇥ out\_trade\_num | string | AB882863666 | true | 商户订单号 |
| ⇥ create\_time | string | 1652403339 | true | 下单时间 |
| ⇥ mobile | string | 18866667777 | true | 手机号 |
| ⇥ product\_id | string | 88 | true | 产品ID |
| ⇥ charge\_amount | float | 100 | true | 充值成功面额 |
| ⇥ charge\_kami | string | yspm1mkdksald | true | 卡密流水 |
| ⇥ state | string | 1 | true | 充值状态：-1取消，0充值中 ，1充值成功，2充值失败，3部分成功 |

## 2.7 充值结果通知-异步通知

&gt; POST-表单格式  
&gt; 回调地址：订单提交时参数中传的回调的地址

### 请求体(Request Body)

| 参数名称 | 数据类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| userid | int | 10001 | true | 商户ID |
| order\_number | CZH000000000 | string |  | true |
| out\_trade\_num | string | ABC2222 | true | 商户订单号 |
| otime | number | 1652403339 | true | 成功/失败时间，10位时间戳 |
| state | number | 1 | true | 充值状态；-1取消， 0充值中， 1充值成功 ，2充值失败，3部分成功（-1,2做失败处理；1做成功处理；3做部分成功处理） |
| mobile | string | 18866667777 | true | 充值手机号 |
| remark | string | 充值成功 | true | 备注信息 |
| charge\_amount | float | 100 | true | 充值成功面额 |
| voucher | string | [http://www.abc.com/xxx](http://www.abc.com/xxx) | true | 凭证 |
| charge\_kami | string | 3etydgd45gf11 | true | 卡密/流水号 |
| sign | string | DS9V0606ITN8GLJM5M4L4DYWQX0VDMVM | true | 签名字符串，用于验签,以保证回调可靠性。  
签名规则见：2.2签名说明  
注：所有参数都要参与签名，请获取所有参数签名，而不是获取现有参数表中的字段签名，以免回调参数增加时导致签名不通过 |
| ... | \* | \* | \* | 更多参数 |

### 响应体

● 收到回调响应文本“success”，如果不响应系统每隔1分钟会再次发起回调，最多回调5次。

~~~
success

~~~

~~~
 php版回调验签示例：

 $apikey=&quot;你的秘钥&quot;;
 $data = $_POST;//接收所有post的数据
 unset($data[&#039;sign&#039;]);//删除掉sign字段
 ksort($data);//排序
 $sign_str = urldecode(http_build_query($data)) . &#039;&amp;apikey=&#039; . $apikey;//获得签名原串
 $mysign=strtoupper(md5($sign_str));//签名
 if($mysign==$_POST[&#039;sign&#039;]){
 //签名正确
 }


~~~

## 2.8 电费支持地区查询

&gt; POST[http://域名/yrapi.php/index/elecity](http://xn--eqrt2g/yrapi.php/index/elecity)

### 请求体(Request Body)

| 参数名称 | 数据类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| userid | string | 10001 | true | 账号ID |
| sign | string | DS9V0606ITN8GLJM5M4L4DYWQX0VDMVM | true | 签名；签名规则见2.2“签名说明” |

### 响应体

● 响应数据格式：JSON

| 参数名称 | 类型 | 示例 | 不为空 | 描述 |
| --- | --- | --- | --- | --- |
| errno | string | 0 | true | 错误码，0代表查询成功，非0代表失败 |
| errmsg | string | 查询成功 | true | 错误描述 |
| data | array | \* | true | errno=0时 返回数据 |
| ⇥ city\_name | string | 广东 | true | 地区名称 |
| ⇥ sort | int | 100 | true | 排序 |
| ⇥ initial | string | G | true | 首字母 |
| ⇥ need\_ytype | Int | 1 | true | 是否三要素认证 |
| ⇥ need\_city | Int | 1 | true | 是否需要选择城市（当此开关打开以后才有下面的城市列表） |
| ⇥ city | Array | \* | true | 支持的地级市 |
| ⇥⇥ city\_name | string | 广州 | true | 城市名称 |
| ⇥⇥ initial | string | G | true | 首字母 |
