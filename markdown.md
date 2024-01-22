
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
<title>对接文档 · 大猿人对接文档 · 看云</title>
    <meta name="description"
          content="看云是一个现代化文档写作、托管及数字出版平台，基于MarkDown语法和Git版本库管理，让你专注于知识创作，可以用于企业知识库、产品手册、项目文档和个人数字出版。"/>
    <meta name="keywords"
          content="文档托管,文档管理,在线创作,文档在线管理,企业知识管理,知识库管理,在线知识管理,文档托管平台,电子出版,在线写书,文档在线转换,在线编辑,在线阅读,个人出版,知识付费,gitbook,开发手册,api手册,在线学习,文档编辑"/>
            <meta name="viewport"
                  content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no"
                  data-react-helmet="true" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
                                <style data-react-helmet="true">
        .dimmer {
            box-sizing: content-box;
            display: flex;
            position: absolute;
            top: 0 !important;
            left: 0 !important;
            width: 100%;
            height: 100%;
            text-align: center;
            vertical-align: middle;
            padding: 0;
            background-color: #FFFFFF;
            opacity: 1;
            line-height: 1;
            animation-fill-mode: both;
            animation-duration: .5s;
            transition: background-color .5s linear;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            user-select: none;
            will-change: opacity;
            z-index: 1000;
        }

        .loader {
            box-sizing: content-box;
            display: block;
            position: absolute;
            top: 50%;
            left: 50%;
            margin: 0;
            text-align: center;
            z-index: 1000;
            -webkit-transform: translateX(-50%) translateY(-50%);
            transform: translateX(-50%) translateY(-50%);
        }

        .loader:before {
            position: absolute;
            content: '';
            top: 0;
            left: 50%;
            width: 50px;
            height: 50px;
            margin: 0 0 0 -25px;
            border-radius: 50px;
            border: 4px solid rgba(0, 0, 0, .1);
        }

        .loader:after {
            position: absolute;
            content: '';
            top: 0;
            left: 50%;
            width: 50px;
            height: 50px;
            margin: 0 0 0 -25px;
            animation: loader .6s linear;
            animation-iteration-count: infinite;
            border-radius: 50px;
            border: 4px solid transparent;
            border-top-color: #767676;
            box-shadow: 0 0 0 1px transparent;
        }

        @keyframes loader {
            from {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
            to {
                -webkit-transform: rotate(360deg);
                transform: rotate(360deg);
            }
        }

        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            overflow: hidden;
        }

        #main {
            display: block !important;
            height: 100vh;
            overflow: hidden;
        }
    </style>
</head>
<body>
    <style>
  .wwads-horizontal,
  .wwads-vertical {
    background-color: #f4f8fa;
    padding: 5px;
    min-height: 120px;
    margin-top: 20px;
    box-sizing: border-box;
    border-radius: 3px;
    font-family: sans-serif;
    display: flex;
    min-width: 150px;
    position: relative;
    overflow: hidden;
  }
  .wwads-horizontal {
    flex-wrap: wrap;
    justify-content: center;
  }
  .wwads-vertical {
    flex-direction: column;
    align-items: center;
    padding-bottom: 32px;
  }
  .wwads-horizontal a,
  .wwads-vertical a {
    text-decoration: none;
  }
  .wwads-horizontal .wwads-content,
  .wwads-horizontal .wwads-img,
  .wwads-vertical .wwads-content,
  .wwads-vertical .wwads-img {
    margin: 5px;
  }
  .wwads-horizontal .wwads-content {
    flex: 130px;
    text-align: left;
  }
  .wwads-vertical .wwads-content {
    margin-top: 10px;
    text-align: left;
  }
  .wwads-content .wwads-text,
  .wwads-horizontal .wwads-text {
    font-size: 14px;
    line-height: 1.4;
    color: #0e1011;
    -webkit-font-smoothing: antialiased;
    word-break: break-word;
    font-family: "BlinkMacSystemFont","Segoe UI", "Microsoft Jhenghei", "Microsoft Yahei", arial, sans-serif;
  }
  .wwads-content strong,.wwads-content b {
    padding: 1px 1px;
    border-bottom: 2px solid #ec515b;
    color:#202124;
    font-family: "BlinkMacSystemFont","Segoe UI", "Microsoft Jhenghei", "Microsoft Yahei", arial, sans-serif;
  }
  .wwads-horizontal .wwads-poweredby,
  .wwads-vertical .wwads-poweredby {
    display: flex;
    align-items: center;
    margin-top: 1em;
  }
  .wwads-vertical .wwads-poweredby {
    position: absolute;
    left: 10px;
    bottom: 10px;
    display: flex;
    align-items: center;
  }
  .wwads-horizontal .wwads-poweredby .wwads-logo,
  .wwads-vertical .wwads-poweredby .wwads-logo {
    background: url("data:image/svg+xml;charset=utf-8,%3Csvg viewBox='0 0 130 130' xmlns='http://www.w3.org/2000/svg' xml:space='preserve' version='1.1'%3E%3Cpath d='m130,60.8c-1.2,-18.7 -10.3,-35.3 -24.1,-46.4c-11.1,-9 -25.3,-14.4 -40.8,-14.4c-0.6,0 -1.1,0 -1.6,0c-3.3,0.1 -6.6,0.4 -9.8,1c-30.5,5.4 -53.7,32 -53.7,64c0,1.9 0.1,3.7 0.2,5.6c2.5,29.5 24.7,53.4 53.4,58.5c2.4,0.4 4.8,0.7 7.3,0.9c0.8,0 1.7,0.1 2.5,0.1c0.5,0 1.1,0 1.6,0c34,0 62,-26.2 64.8,-59.5c0.2,-1.8 0.2,-3.7 0.2,-5.6c0.1,-1.4 0.1,-2.8 0,-4.2zm-97.6,9.8c3.7,7.7 11.5,13 20.6,13c0.3,0 0.5,0 0.8,0l0,9.8c-0.3,0 -0.5,0 -0.8,0c-14.6,0 -26.9,-9.6 -31,-22.8c-1,-3.1 -1.5,-6.4 -1.5,-9.8c0,-18 14.6,-32.5 32.5,-32.5c0.3,0 0.5,0 0.8,0c3.4,0.1 6.7,0.7 9.8,1.7c6.5,2.2 12.1,6.5 16,11.9c2,2.8 3.5,5.9 4.6,9.2c0.9,3 1.4,6.2 1.4,9.6l-9.8,0c0,-2.2 -0.3,-4.3 -0.9,-6.3c-0.9,-3.2 -2.5,-6.2 -4.7,-8.6c-1.9,-2.1 -4.1,-3.9 -6.6,-5.2c-2.9,-1.5 -6.2,-2.5 -9.8,-2.6c-0.3,0 -0.5,0 -0.8,0c-12.6,0 -22.8,10.2 -22.8,22.8c0,3.5 0.8,6.8 2.2,9.8zm78.1,0c-0.2,1.7 -0.5,3.3 -1,4.8c-3.4,10.5 -13.2,18.1 -24.8,18.1c-3.1,0 -6.1,-0.5 -8.9,-1.6c-2.2,-0.8 -4.2,-1.9 -6.1,-3.2c-2.4,-1.7 -4.5,-3.8 -6.2,-6.1c-0.3,-0.4 -0.5,-0.8 -0.8,-1.2c-2,-3.2 -3.4,-6.9 -3.9,-10.8l9.9,0c0.3,1.7 0.9,3.3 1.7,4.8c1.6,2.9 4.1,5.3 7.1,6.7c0.6,0.3 1.2,0.5 1.8,0.7c1.7,0.6 3.5,0.9 5.4,0.9c7.9,0 14.5,-5.7 16,-13.2c0.2,-1 0.3,-2 0.3,-3.1c0,-2.4 -0.5,-4.6 -1.4,-6.7c-1.7,-3.7 -4.7,-6.7 -8.4,-8.3l3.5,-9.1c7.4,3.1 13.1,9.5 15.2,17.4c0.4,1.6 0.7,3.3 0.8,5.1c0,0.5 0.1,1 0.1,1.6c-0.1,1.1 -0.2,2.2 -0.3,3.2z' fill='%23a6b7bf' /%3E%3C/svg%3E%0A") no-repeat;
    padding: 0 1px 11px 11px;
  }
  .wwads-horizontal .wwads-poweredby .wwads-logo-text,
  .wwads-vertical .wwads-poweredby .wwads-logo-text {
    font-size: 11px;
    margin-left: 3px;
    color: #a6b7bf;
  }
  .wwads-horizontal .wwads-hide,
  .wwads-vertical .wwads-hide {
    position: absolute;
    right: -23px;
    bottom: -23px;
    width: 46px;
    height: 46px;
    border-radius: 23px;
    transition: all 0.3s ease-in-out;
    cursor: pointer;
  }
  .wwads-horizontal .wwads-hide .hide-svg,
  .wwads-vertical .wwads-hide .hide-svg {
    position: absolute;
    left: 10px;
    top: 10px;
    background: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' width='6' height='7' fill='%23a6b7bf'%3E%3Cpath d='M.879.672L3 2.793 5.121.672a.5.5 0 11.707.707L3.708 3.5l2.12 2.121a.5.5 0 11-.707.707l-2.12-2.12-2.122 2.12a.5.5 0 11-.707-.707l2.121-2.12L.172 1.378A.5.5 0 01.879.672z'/%3E%3C/svg%3E") no-repeat;
  }
  .wwads-horizontal .wwads-hide:hover,
  .wwads-vertical .wwads-hide:hover {
    background: rgb(0 0 0/0.05);
  }
</style>
<style>
  #wwads {
    position: fixed;
    bottom: 10px;
    right: 10px;
    max-width: 180px;
    z-index: 1001;
    border:2px solid #ececec;
  }
  @media only screen and (min-width: 600px) and (max-width: 1600px) {
    #wwads + #main .article-body,
    #wwads + #main .article-navigation,
    #wwads + #main .article-foot {
      max-width: calc(100% - 190px);
      margin-left: 0 !important;
    }
  }
  @media only screen and (max-width: 600px) {
    #wwads {
      bottom: 0;
      right: 0;
      left: 0;
      font-size:large;
      max-width: 100%;
      margin-top: 0;
      height: 120px;
      padding-bottom: 0;
      flex-direction: row;
      align-items: center;
    }
    #wwads .wwads-content {
      flex: 1;
    }
    #wwads .wwads-poweredby {
      position: relative;
      left: 0;
      bottom: 0;
      display: flex;
      align-items: center;
    }
    #wwads + #main .sidebar {
      bottom: 120px;
    }
  
    #wwads + #main .article {
      padding-bottom: 120px;
    }
  }
</style>
<div id="wwads" class="wwads-cn wwads-vertical">
  
                                            
                                                        <a href="https://e.topthink.com/api/go/eca037080f91e9719" class="wwads-img" target="_blank" rel="sponsored noopener" referrerpolicy="no-referrer-when-downgrade"><img src="https://static.kancloud.cn/asset/app/images/chat.png?version=1a7cbd87d3964e64c59f" width="145" /></a>
        <div class="wwads-content">
          <a href="https://e.topthink.com/api/go/eca037080f91e9719" class="wwads-text" target="_blank" rel="sponsored noopener" referrerpolicy="no-referrer-when-downgrade">ThinkChat🤖让你学习和工作更高效，注册即送10W Token，即刻<b>开启你的AI之旅</b></a>
          <a href="https://www.topthink.com/" title="由顶想云提供广告服务" class="wwads-poweredby" target="_blank"><img class="wwads-logo" /><span class="wwads-logo-text">广告</span></a>
        </div>        
                                            
  <a class="wwads-hide" onclick="parentNode.remove()" title="隐藏广告"><svg class="hide-svg"></svg></a>
</div>
<div id="main">
    <div class="seo">
        <div class="content">
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
                    </div>
        <div class="catalog">
            <ul>
                                    <li><a href="3090391">大猿人</a></li>
                                    <li><a href="3090392">对接文档</a></li>
                            </ul>
        </div>
    </div>
    <div class="dimmer">
        <div class="loader"></div>
    </div>
</div>
<script type="application/payload+json">
    {
        "config":{"id":614203,"title":"\u5927\u733f\u4eba\u5bf9\u63a5\u6587\u6863","description":"","cover":"https:\/\/cover.kancloud.cn\/m644454938\/aaaaaaa!middle","author":{"name":"\u65e0\u987b\u7ec8\u6709","email":"644454938@qq.com","url":"https:\/\/www.kancloud.cn\/@m644454938"}},
        "options":{"book":{"id":614203,"title":"\u5927\u733f\u4eba\u5bf9\u63a5\u6587\u6863","namespace":"m644454938","name":"aaaaaaa","price":0,"cover":"https:\/\/cover.kancloud.cn\/m644454938\/aaaaaaa","middle_cover":"https:\/\/cover.kancloud.cn\/m644454938\/aaaaaaa!middle","small_cover":"https:\/\/cover.kancloud.cn\/m644454938\/aaaaaaa!small"},"plugins":{"host":"plugins.kancloud.cn","scheme":"https"},"web":{"host":"www.kancloud.cn","scheme":"https"},"environment":"reader","base":"\/m644454938\/aaaaaaa\/content","entry":"\/m644454938\/aaaaaaa"},
        "style": "",
        "article":{"path":"3090392","ref":"\u5bf9\u63a5\u6587\u6863.md","title":"\u5bf9\u63a5\u6587\u6863","content":"# \u8bdd\u8d39\u5145\u503c\u5e73\u53f0V2.0\n\n## 1 \u73af\u5883\u53d8\u91cf\n\n### \u63a5\u53e3\n\n| \u53c2\u6570\u540d | \u5b57\u6bb5\u503c |\n| --- | --- |\n| baseurl | [http:\/\/\u57df\u540d\/yrapi.php\/](http:\/\/xn--eqrt2g\/yrapi.php\/) |\n\n## 2 \u8bdd\u8d39\u6d41\u91cf\u4f9b\u5e94\u7cfb\u7edf\n\n## 2.1 \u63a5\u53e3\u8bf4\u660e\n\napi\u63d0\u4ea4\u65b9\u5f0f\uff1aHTTP POST(\u8868\u5355) Content-Type\uff1aapplication\/x-www-form-urlencoded  \n\u5145\u503c\u56de\u8c03\u65b9\u5f0f\uff1aHTTP POST(\u8868\u5355) \u53c2\u6570\u683c\u5f0f\u5b9e\u4f8b\uff1aorder\\_number=1&out\\_trade\\_num=1&mobile=1&otime=1&state=1\n\n## 2.2 \u7b7e\u540d\u8bf4\u660e\n\n\u7b7e\u540d\u6b65\u9aa4\uff1a  \n1\u3001\u51c6\u5907\u597d\u6240\u6709\u5f85\u7b7e\u540d\u53c2\u6570\uff08\u6240\u6709\u201d\u8bf7\u6c42\u53c2\u6570\u201c\u6216\u6240\u6709\u201d\u56de\u8c03\u53c2\u6570\u201c\u90fd\u8981\u53c2\u6570\u7b7e\u540d\uff0c\u9664\u5f00sign\u5b57\u6bb5\uff0c\u6ca1\u4e2aapi\u4f20\u9012\u7684\u53c2\u6570\u90fd\u4e0d\u540c\uff0c\u8fd9\u53e5\u63d0\u793a\u5f88\u91cd\u8981\uff09\n\n2\u3001\u751f\u6210\u7b7e\u540d\u5b57\u7b26\u4e32\uff08\u53c2\u6570\u540d\u5b57\u5178\u5347\u5e8f\u6392\u5e8f\uff0capikey\u4e0d\u53c2\u4e0e\u6392\u5e8f\uff0c\u76f4\u63a5\u653e\u6700\u540e\uff0c\u5982\u540e\u9762\u793a\u4f8b\u8fdb\u884c\u7ec4\u88c5\uff09\u201ca=1&b=2&c=3&apikey=\u4f60\u7684\u5546\u6237key\u201d\u3002(\u5b9e\u9645\u5b57\u6bb5\u540d\u5e76\u975e\u662fa\u3001b\u3001c\u8fd9\u91cc\u53ea\u662f\u6f14\u793a)\n\n3\u3001\u5bf9\u7b7e\u540d\u5b57\u7b26\u4e32\u8fdb\u884c\u5927\u5199md5\uff0c\u7b7e\u540d=md5(\u7b7e\u540d\u5b57\u7b26\u4e32)\n\n\u7279\u522b\u8bf4\u660e\uff1a\u7b7e\u540d\u5b57\u7b26\u4e32\u4e0d\u8fdb\u884cURL\u7f16\u7801\uff0c\u5982\u679c\u4f7f\u7528php \u7684http\\_build\\_query\u62fc\u88c5\u5b57\u7b26\u4e32\u65f6\uff0c\u4f1a\u81ea\u52a8\u8fdb\u884cURL\u7f16\u7801\uff0c\u5efa\u8bae\u5bf9\u7b7e\u540d\u5b57\u7b26\u4e32\u8fdb\u884c\u4e00\u6b21URL\u89e3\u7801 \uff1b\u63d0\u4ea4\u62a5\u6587\u4e2d\u4e0d\u8981\u5305\u542b\u79d8\u94a5\uff0c\u5bb9\u6613\u9020\u6210\u79d8\u94a5\u66b4\u9732\u4e14\u4e0d\u80fd\u9a8c\u7b7e\u901a\u8fc7\uff1b\n\nphp\u7b7e\u540d\u5b9e\u4f8b\uff08\u5176\u5b83\u8bed\u8a00\u81ea\u884c\u7f16\u5199\uff09\uff1a\n\n~~~\n\/\/\u7b7e\u540d\u53c2\u6570\u53ea\u662f\u793a\u4f8b\uff0c\u5e76\u975e\u771f\u5b9e\u63d0\u4ea4\u6570\u636e\n$param = [\"\u53c2\u6570\u540d\u79f0\"=>\"\u53c2\u6570\u503c\",...];\n\/\/\u5b57\u5178\u6392\u5e8f\nksort($param);\n\/\/\u62fc\u63a5\u7b7e\u540d\u4e32\n$sign_str = http_build_query($param) . '&apikey=aaaaaaaaaaaaaaaaaaa';\n\/\/\u7b7e\u540d\n$sign = strtoupper(md5(urldecode($sign_str)));\n$param['sign'] = $sign;\n$httpdata = $param;\n\n~~~\n\n## 2.3 \u5145\u503c\u63d0\u4ea4\u63a5\u53e3\n\n> POST[http:\/\/\u57df\u540d\/yrapi.php\/index\/recharge](http:\/\/xn--eqrt2g\/yrapi.php\/index\/recharge)\n\n### \u63a5\u53e3\u8bf4\u660e\n\n> \u63d0\u4ea4\u5145\u503c\u8ba2\u5355\n\n### \u8bf7\u6c42\u4f53(Request Body)\n\n| \u53c2\u6570\u540d\u79f0 | \u6570\u636e\u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| out\\_trade\\_num | string | GG5822222266 | true | \u5546\u6237\u8ba2\u5355\u53f7\uff0c\u7531\u5546\u6237\u81ea\u5df1\u751f\u6210\u552f\u4e00\u5355\u53f7\u3002  \n\uff08\u540c\u4e00\u5546\u6237\uff0c\u4e0d\u80fd\u5b58\u5728\u76f8\u540c\u5355\u53f7\u8ba2\u5355\uff0c\u76f8\u540c\u8ba2\u5355\u53f7\u4e0d\u80fd\u63d0\u5355\uff09 |\n| product\\_id | number | 68 | true | \u4ea7\u54c1ID\uff08\u4ee3\u7406\u540e\u53f0\u67e5\u770b\uff09 |\n| mobile | string | 18866667777 | true | \u5145\u503c\u53f7\u7801\uff08\u624b\u673a\u53f7\u3001\u7535\u8d39\u6237\u3001qq\u53f7\u7b49\uff09 |\n| notify\\_url | string | [http:\/\/www.abc.com](http:\/\/www.abc.com\/) | true | \u56de\u8c03\u5730\u5740\uff0c\u7528\u4e8e\u63a5\u6536\u5145\u503c\u72b6\u6001\u56de\u8c03 |\n| userid | string | 10001 | true | \u5546\u6237ID\uff0c\u901a\u8fc7\u5ba2\u670d\u6216\u4ee3\u7406\u540e\u53f0\u83b7\u53d6 |\n| amount | number | 100 | false | \u9762\u503c\uff0c\uff08\u4e0d\u4f20\u4e0d\u6821\u9a8c\uff09\u5982\u679c\u4ea7\u54c1\u7684\u9762\u503c\u4e0e\u6b64\u53c2\u6570\u4e0d\u540c\uff0c\u63d0\u5355\u9a73\u56de |\n| price | number | 94.8 | false | \u6700\u9ad8\u6210\u672c\uff0c\uff08\u4e0d\u4f20\u4e0d\u6821\u9a8c\uff09\u5982\u679c\u4ea7\u54c1\u6210\u672c\u8d85\u8fc7\u8fd9\u4e2a\u503c\uff0c\u63d0\u5355\u9a73\u56de |\n| area | string | \u5e7f\u4e1c | false | \u7535\u8d39\u7701\u4efd\/\u76f4\u8f96\u5e02\uff0c\u5982\uff1a\u56db\u5ddd\u3001\u5317\u4eac\u3001\u4e0a\u6d77\uff0c\u4ec5\u7535\u8d39\u5e26\u6b64\u53c2\u6570 |\n| ytype | string | 1 | false | \u7535\u8d39\u9a8c\u8bc1\u4e09\u8981\u7d20\uff0c1-\u8eab\u4efd\u8bc1\u540e6\u4f4d\uff0c2-\u94f6\u884c\u5361\u540e\u516d\u4f4d,3-\u8425\u4e1a\u6267\u7167\u540e\u516d\u4f4d\uff0c\u4ec5\u5357\u7f51\u7535\u8d39\u5e26\u6b64\u53c2\u6570 |\n| id\\_card\\_no | string | 123456 | false | \u8eab\u4efd\u8bc1\u540e6\u4f4d\/\u94f6\u884c\u5361\u540e6\u4f4d\/\u8425\u4e1a\u6267\u7167\u540e6\u4f4d\uff0c\u4ec5\u5357\u7f51\u7535\u8d39\u5e26\u6b64\u53c2\u6570 |\n| city | string | \u5e7f\u5dde | false | \u5730\u7ea7\u5e02\u540d\uff0c\u4ec5\u90e8\u5206\u5357\u7f51\u7535\u8d39\u5e26\u6b64\u53c2\u6570\uff0c\u662f\u5426\u5e26\u6b64\u53c2\u6570\u9700\u54a8\u8be2\u6e20\u9053\u65b9 |\n| param1 | string | \\* | false | \u6269\u5c55\u53c2\u6570\uff0c\u540e\u53f0\u67e5\u770b\u63d0\u4ea4\u7684\u4ea7\u54c1\u7c7b\u76ee\u662f\u5426\u9700\u8981\u63d0\u4ea4\u6b64\u53c2\u6570 |\n| param2 | string | \\* | false | \u6269\u5c55\u53c2\u6570\uff0c\u540e\u53f0\u67e5\u770b\u63d0\u4ea4\u7684\u4ea7\u54c1\u7c7b\u76ee\u662f\u5426\u9700\u8981\u63d0\u4ea4\u6b64\u53c2\u6570 |\n| param3 | string | \\* | false | \u6269\u5c55\u53c2\u6570\uff0c\u540e\u53f0\u67e5\u770b\u63d0\u4ea4\u7684\u4ea7\u54c1\u7c7b\u76ee\u662f\u5426\u9700\u8981\u63d0\u4ea4\u6b64\u53c2\u6570 |\n| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | \u7b7e\u540d\uff1b\u7b7e\u540d\u89c4\u5219\u89c12.2\u201c\u7b7e\u540d\u8bf4\u660e\u201d |\n\n~~~\n\u8bf7\u6c42\u793a\u4f8b\uff1a\nout_trade_num=ABC1111&product_id=11&mobile=18899998888&notify_url=http:\/\/www.abc.com\/yuanren&userid=10001&sign=GZWDK8X7TGJFA8N8O9HILQ6WSI46C8FJ\n\n~~~\n\n### \u54cd\u5e94\u4f53\n\n\u25cf \u54cd\u5e94\u6570\u636e\u683c\u5f0f\uff1aJSON\uff0c\u5f53\u201chttp\u72b6\u6001\u975e200\u201d\u6216\u8005\u201c\u54cd\u5e94\u4f53\u65e0\u6570\u636e\u65f6\u201d\u53ef\u80fd\u662f\u670d\u52a1\u5668\u6216\u5176\u4ed6\u94fe\u8def\u51fa\u73b0\u6545\u969c\uff0c\u65e0\u6cd5\u51c6\u786e\u5224\u5b9a\u662f\u5426\u6210\u529f\u4e0b\u5355\uff0c\u8bf7\u901a\u8fc7\u8ba2\u5355\u67e5\u8be2\u6216\u8005\u4eba\u5de5\u65b9\u5f0f\u518d\u6b21\u786e\u8ba4\u72b6\u6001\u3002\n\n| \u53c2\u6570\u540d\u79f0 | \u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| errno | string | \\* | true | \u9519\u8bef\u7801\uff0c0\u4ee3\u8868\u6210\u529f\uff0c\u975e0\u4ee3\u8868\u63d0\u4ea4\u5931\u8d25 |\n| errmsg | string | \\* | true | \u9519\u8bef\u63cf\u8ff0 |\n| data | object | \\* | true | errno=0\u65f6 \u8fd4\u56de\u6570\u636e |\n| \u21e5 order\\_number | string | \\* | true | \u7cfb\u7edf\u5b9a\u5355\u53f7 |\n| \u21e5 mobile | string | \\* | true | \u5145\u503c\u624b\u673a\u53f7 |\n| \u21e5 product\\_id | string | \\* | true | \u4ea7\u54c1ID |\n| \u21e5 total\\_price | string | \\* | true | \u6d88\u8d39\u91d1\u989d |\n| \u21e5 out\\_trade\\_num | string | \\* | true | \u5546\u6237\u8ba2\u5355\u53f7 |\n| \u21e5 title | string | \\* | true | \u5145\u503c\u4ea7\u54c1\u8bf4\u660e |\n\n~~~\n\u54cd\u5e94\u793a\u4f8b\uff1a\n{\n    \"errno\": 0,\n    \"errmsg\": \"\u4e0b\u5355\u6210\u529f\",\n    \"data\": {\n        \"order_number\": \"XYZ111111\",\n        \"mobile\": \"18866667777\",\n        \"product_id\": 10001,\n        \"total_price\": \"95.00\",\n        \"out_trade_num\": \"ABC1111\",\n        \"title\": \"100\u5143\u8bdd\u8d39\",\n    }\n}\n\n~~~\n\n## 2.4 \u67e5\u8be2\u7528\u6237\u4fe1\u606f\n\n> POST[http:\/\/\u57df\u540d\/yrapi.php\/index\/user](http:\/\/xn--eqrt2g\/yrapi.php\/index\/user)\n\n### \u8bf7\u6c42\u4f53(Request Body)\n\n| \u53c2\u6570\u540d\u79f0 | \u6570\u636e\u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| userid | string | 1001 | true | \u8d26\u53f7ID |\n| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | \u7b7e\u540d\uff1b\u7b7e\u540d\u89c4\u5219\u89c12.2\u201c\u7b7e\u540d\u8bf4\u660e\u201d |\n\n### \u54cd\u5e94\u4f53\n\n\u25cf \u54cd\u5e94\u6570\u636e\u683c\u5f0f\uff1aJSON\n\n| \u53c2\u6570\u540d\u79f0 | \u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| errno | string | \\* | true | \u9519\u8bef\u7801\uff0c0\u4ee3\u8868\u6210\u529f\uff0c\u975e0\u4ee3\u8868\u5931\u8d25 |\n| errmsg | string | \\* | true | \u9519\u8bef\u63cf\u8ff0 |\n| data | object | \\* | true | errno=0\u65f6 \u8fd4\u56de\u6570\u636e |\n| \u21e5 id | string | \\* | true | userid |\n| \u21e5 username | string | \\* | true | \u540d\u79f0 |\n| \u21e5 balance | string | \\* | true | \u4f59\u989d |\n\n## 2.5 \u83b7\u53d6\u4ea7\u54c1\u7c7b\u578b\u548c\u4ea7\u54c1\u5206\u7c7b\n\n> POST[http:\/\/\u57df\u540d\/yrapi.php\/index\/typecate](http:\/\/xn--eqrt2g\/yrapi.php\/index\/typecate)\n\n### \u8bf7\u6c42\u4f53(Request Body)\n\n| \u53c2\u6570\u540d\u79f0 | \u6570\u636e\u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| userid | string | 1001 | true | \u5546\u6237ID |\n| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | \u7b7e\u540d |\n\n### \u54cd\u5e94\u4f53\n\n\u25cf \u54cd\u5e94\u6570\u636e\u683c\u5f0f\uff1aJSON\n\n| \u53c2\u6570\u540d\u79f0 | \u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| errno | string | \\* | true | \u8fd4\u56de0 |\n| errmsg | string | \\* | true | \u9519\u8bef\u63cf\u8ff0 |\n| data | object | \\* | true | errno=0\u65f6 \u8fd4\u56de\u6570\u636e |\n| \u21e5 id | string | \\* | true | \u4ea7\u54c1\u7c7b\u578bid |\n| \u21e5 type\\_name | string | \\* | true | \u4ea7\u54c1\u7c7b\u578b\u540d\u79f0 |\n| \u21e5 cate | array | \\* | true | \u5206\u7c7b\u5217\u8868 |\n| \u21e5\u21e5 id | int | \\* | true | \u5206\u7c7bID |\n| \u21e5\u21e5 cate | string | \\* | true | \u5206\u7c7b\u540d\u79f0 |\n| \u21e5\u21e5 type | string | \\* | true | \u4ea7\u54c1\u7c7b\u578bID |\n\n## 2.5 \u83b7\u53d6\u4ea7\u54c1\n\n> POST[http:\/\/\u57df\u540d\/yrapi.php\/index\/product](http:\/\/xn--eqrt2g\/yrapi.php\/index\/product)\n\n### \u8bf7\u6c42\u4f53(Request Body)\n\n| \u53c2\u6570\u540d\u79f0 | \u6570\u636e\u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| userid | string | 10001 | true | \u5546\u6237ID |\n| type | int | 1 | false | \u4ea7\u54c1\u7c7b\u578bID,\u975e\u5fc5\u987b |\n| cate\\_id | int | 10 | false | \u5206\u7c7bID,\u975e\u5fc5\u987b |\n| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | \u7b7e\u540d |\n\n### \u54cd\u5e94\u4f53\n\n\u25cf \u54cd\u5e94\u6570\u636e\u683c\u5f0f\uff1aJSON\n\n| \u53c2\u6570\u540d\u79f0 | \u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| errno | string | \\* | true | \u9519\u8bef\u7801\uff0c0\u4ee3\u8868\u6210\u529f\uff0c\u975e0\u4ee3\u8868\u5931\u8d25 |\n| errmsg | string | \\* | true | \u9519\u8bef\u63cf\u8ff0 |\n| data | object | \\* | true | errno=0\u65f6 \u8fd4\u56de\u6570\u636e |\n| \u21e5 id | int | \\* | true | \u5206\u7c7bID |\n| \u21e5 cate | string | \\* | true | \u5206\u7c7b\u540d\u79f0 |\n| \u21e5 sort | string | \\* | true | \u6392\u5e8f |\n| \u21e5 type | string | \\* | true | \u4ea7\u54c1\u7c7b\u578bID |\n| \u21e5 products | array | \\* | true | \u4ea7\u54c1\u5217\u8868 |\n| \u21e5\u21e5 id | string | \\* | true | \u4ea7\u54c1ID,\u4e0b\u5355\u62a5\u6587\u4e2d\u7528\u6b64\u53c2\u6570 |\n| \u21e5\u21e5 name | string | \\* | true | \u4ea7\u54c1\u540d\u79f0 |\n| \u21e5\u21e5 desc | string | \\* | true | \u4ea7\u54c1\u8bf4\u660e |\n| \u21e5\u21e5 api\\_open | string | \\* | true | \u81ea\u52a8\u5145\u503c |\n| \u21e5\u21e5 isp | string | \\* | true | \u8fd0\u8425\u5546\u96c6\u5408\uff08\u8bdd\u8d39\u3001\u6d41\u91cf\u6709\u6548\uff09\uff0c1\u79fb\u52a8,2\u7535\u4fe1,3\u8054\u901a,4\u865a\u62df |\n| \u21e5\u21e5 ys\\_tag | string | \\* | true | \u6807\u7b7e |\n| \u21e5\u21e5 price | string | \\* | true | \u4ef7\u683c\uff0c\u4e0b\u5355\u6263\u8d39\u91d1\u989d |\n| \u21e5\u21e5 y\\_price | string | \\* | true | \u539f\u4ef7 |\n| \u21e5\u21e5 max\\_price | string | \\* | true | \u5c01\u9876\u4ef7\u683c |\n| \u21e5\u21e5 type | string | \\* | true | \u4ea7\u54c1\u7c7b\u578bID |\n| \u21e5\u21e5 cate\\_name | string | \\* | true | \u4ea7\u54c1\u5206\u7c7b\u540d\u79f0 |\n| \u21e5\u21e5 type\\_name | string | \\* | true | \u4ea7\u54c1\u7c7b\u578b\u540d\u79f0 |\n\n## 2.6 \u81ea\u53d1\u67e5\u8be2\u8ba2\u5355\u72b6\u6001\n\n> POST[http:\/\/\u57df\u540d\/yrapi.php\/index\/check](http:\/\/xn--eqrt2g\/yrapi.php\/index\/check)\n\n### \u8bf7\u6c42\u4f53(Request Body)\n\n| \u53c2\u6570\u540d\u79f0 | \u6570\u636e\u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| userid | string | 10001 | true | \u8d26\u6237ID |\n| out\\_trade\\_nums | string | CZH668877,CZH9988666 | true | \u5546\u6237\u8ba2\u5355\u53f7\uff1b\u591a\u4e2a\u7528\u82f1\u6587,\u5206\u5272 |\n| sign | string | JCXHF8S66BO6MPG5JNW2DGEJ9SB3F7ST | true | \u7b7e\u540d |\n\n### \u54cd\u5e94\u4f53\n\n\u25cf \u54cd\u5e94\u6570\u636e\u683c\u5f0f\uff1aJSON\n\n| \u53c2\u6570\u540d\u79f0 | \u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| errno | string | 0 | true | \u9519\u8bef\u7801\uff0c0\u4ee3\u8868\u6210\u529f\uff0c\u975e0\u4ee3\u8868\u5931\u8d25 |\n| errmsg | string | \u67e5\u8be2\u6210\u529f | true | \u9519\u8bef\u63cf\u8ff0 |\n| data | object | \\* | true | errno=0\u65f6 \u8fd4\u56de\u6570\u636e |\n| \u21e5 order\\_number | string | CZH1111111 | true | \u7cfb\u7edf\u8ba2\u5355\u53f7 |\n| \u21e5 out\\_trade\\_num | string | AB882863666 | true | \u5546\u6237\u8ba2\u5355\u53f7 |\n| \u21e5 create\\_time | string | 1652403339 | true | \u4e0b\u5355\u65f6\u95f4 |\n| \u21e5 mobile | string | 18866667777 | true | \u624b\u673a\u53f7 |\n| \u21e5 product\\_id | string | 88 | true | \u4ea7\u54c1ID |\n| \u21e5 charge\\_amount | float | 100 | true | \u5145\u503c\u6210\u529f\u9762\u989d |\n| \u21e5 charge\\_kami | string | yspm1mkdksald | true | \u5361\u5bc6\u6d41\u6c34 |\n| \u21e5 state | string | 1 | true | \u5145\u503c\u72b6\u6001\uff1a-1\u53d6\u6d88\uff0c0\u5145\u503c\u4e2d \uff0c1\u5145\u503c\u6210\u529f\uff0c2\u5145\u503c\u5931\u8d25\uff0c3\u90e8\u5206\u6210\u529f |\n\n## 2.7 \u5145\u503c\u7ed3\u679c\u901a\u77e5-\u5f02\u6b65\u901a\u77e5\n\n> POST-\u8868\u5355\u683c\u5f0f  \n> \u56de\u8c03\u5730\u5740\uff1a\u8ba2\u5355\u63d0\u4ea4\u65f6\u53c2\u6570\u4e2d\u4f20\u7684\u56de\u8c03\u7684\u5730\u5740\n\n### \u8bf7\u6c42\u4f53(Request Body)\n\n| \u53c2\u6570\u540d\u79f0 | \u6570\u636e\u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| userid | int | 10001 | true | \u5546\u6237ID |\n| order\\_number | CZH000000000 | string |  | true |\n| out\\_trade\\_num | string | ABC2222 | true | \u5546\u6237\u8ba2\u5355\u53f7 |\n| otime | number | 1652403339 | true | \u6210\u529f\/\u5931\u8d25\u65f6\u95f4\uff0c10\u4f4d\u65f6\u95f4\u6233 |\n| state | number | 1 | true | \u5145\u503c\u72b6\u6001\uff1b-1\u53d6\u6d88\uff0c 0\u5145\u503c\u4e2d\uff0c 1\u5145\u503c\u6210\u529f \uff0c2\u5145\u503c\u5931\u8d25\uff0c3\u90e8\u5206\u6210\u529f\uff08-1,2\u505a\u5931\u8d25\u5904\u7406\uff1b1\u505a\u6210\u529f\u5904\u7406\uff1b3\u505a\u90e8\u5206\u6210\u529f\u5904\u7406\uff09 |\n| mobile | string | 18866667777 | true | \u5145\u503c\u624b\u673a\u53f7 |\n| remark | string | \u5145\u503c\u6210\u529f | true | \u5907\u6ce8\u4fe1\u606f |\n| charge\\_amount | float | 100 | true | \u5145\u503c\u6210\u529f\u9762\u989d |\n| voucher | string | [http:\/\/www.abc.com\/xxx](http:\/\/www.abc.com\/xxx) | true | \u51ed\u8bc1 |\n| charge\\_kami | string | 3etydgd45gf11 | true | \u5361\u5bc6\/\u6d41\u6c34\u53f7 |\n| sign | string | DS9V0606ITN8GLJM5M4L4DYWQX0VDMVM | true | \u7b7e\u540d\u5b57\u7b26\u4e32\uff0c\u7528\u4e8e\u9a8c\u7b7e,\u4ee5\u4fdd\u8bc1\u56de\u8c03\u53ef\u9760\u6027\u3002  \n\u7b7e\u540d\u89c4\u5219\u89c1\uff1a2.2\u7b7e\u540d\u8bf4\u660e  \n\u6ce8\uff1a\u6240\u6709\u53c2\u6570\u90fd\u8981\u53c2\u4e0e\u7b7e\u540d\uff0c\u8bf7\u83b7\u53d6\u6240\u6709\u53c2\u6570\u7b7e\u540d\uff0c\u800c\u4e0d\u662f\u83b7\u53d6\u73b0\u6709\u53c2\u6570\u8868\u4e2d\u7684\u5b57\u6bb5\u7b7e\u540d\uff0c\u4ee5\u514d\u56de\u8c03\u53c2\u6570\u589e\u52a0\u65f6\u5bfc\u81f4\u7b7e\u540d\u4e0d\u901a\u8fc7 |\n| ... | \\* | \\* | \\* | \u66f4\u591a\u53c2\u6570 |\n\n### \u54cd\u5e94\u4f53\n\n\u25cf \u6536\u5230\u56de\u8c03\u54cd\u5e94\u6587\u672c\u201csuccess\u201d\uff0c\u5982\u679c\u4e0d\u54cd\u5e94\u7cfb\u7edf\u6bcf\u96941\u5206\u949f\u4f1a\u518d\u6b21\u53d1\u8d77\u56de\u8c03\uff0c\u6700\u591a\u56de\u8c035\u6b21\u3002\n\n~~~\nsuccess\n\n~~~\n\n~~~\n php\u7248\u56de\u8c03\u9a8c\u7b7e\u793a\u4f8b\uff1a\n\n $apikey=\"\u4f60\u7684\u79d8\u94a5\";\n $data = $_POST;\/\/\u63a5\u6536\u6240\u6709post\u7684\u6570\u636e\n unset($data['sign']);\/\/\u5220\u9664\u6389sign\u5b57\u6bb5\n ksort($data);\/\/\u6392\u5e8f\n $sign_str = urldecode(http_build_query($data)) . '&apikey=' . $apikey;\/\/\u83b7\u5f97\u7b7e\u540d\u539f\u4e32\n $mysign=strtoupper(md5($sign_str));\/\/\u7b7e\u540d\n if($mysign==$_POST['sign']){\n \/\/\u7b7e\u540d\u6b63\u786e\n }\n\n\n~~~\n\n## 2.8 \u7535\u8d39\u652f\u6301\u5730\u533a\u67e5\u8be2\n\n> POST[http:\/\/\u57df\u540d\/yrapi.php\/index\/elecity](http:\/\/xn--eqrt2g\/yrapi.php\/index\/elecity)\n\n### \u8bf7\u6c42\u4f53(Request Body)\n\n| \u53c2\u6570\u540d\u79f0 | \u6570\u636e\u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| userid | string | 10001 | true | \u8d26\u53f7ID |\n| sign | string | DS9V0606ITN8GLJM5M4L4DYWQX0VDMVM | true | \u7b7e\u540d\uff1b\u7b7e\u540d\u89c4\u5219\u89c12.2\u201c\u7b7e\u540d\u8bf4\u660e\u201d |\n\n### \u54cd\u5e94\u4f53\n\n\u25cf \u54cd\u5e94\u6570\u636e\u683c\u5f0f\uff1aJSON\n\n| \u53c2\u6570\u540d\u79f0 | \u7c7b\u578b | \u793a\u4f8b | \u4e0d\u4e3a\u7a7a | \u63cf\u8ff0 |\n| --- | --- | --- | --- | --- |\n| errno | string | 0 | true | \u9519\u8bef\u7801\uff0c0\u4ee3\u8868\u67e5\u8be2\u6210\u529f\uff0c\u975e0\u4ee3\u8868\u5931\u8d25 |\n| errmsg | string | \u67e5\u8be2\u6210\u529f | true | \u9519\u8bef\u63cf\u8ff0 |\n| data | array | \\* | true | errno=0\u65f6 \u8fd4\u56de\u6570\u636e |\n| \u21e5 city\\_name | string | \u5e7f\u4e1c | true | \u5730\u533a\u540d\u79f0 |\n| \u21e5 sort | int | 100 | true | \u6392\u5e8f |\n| \u21e5 initial | string | G | true | \u9996\u5b57\u6bcd |\n| \u21e5 need\\_ytype | Int | 1 | true | \u662f\u5426\u4e09\u8981\u7d20\u8ba4\u8bc1 |\n| \u21e5 need\\_city | Int | 1 | true | \u662f\u5426\u9700\u8981\u9009\u62e9\u57ce\u5e02\uff08\u5f53\u6b64\u5f00\u5173\u6253\u5f00\u4ee5\u540e\u624d\u6709\u4e0b\u9762\u7684\u57ce\u5e02\u5217\u8868\uff09 |\n| \u21e5 city | Array | \\* | true | \u652f\u6301\u7684\u5730\u7ea7\u5e02 |\n| \u21e5\u21e5 city\\_name | string | \u5e7f\u5dde | true | \u57ce\u5e02\u540d\u79f0 |\n| \u21e5\u21e5 initial | string | G | true | \u9996\u5b57\u6bcd |"},
        "summary":[{"id":3090391,"pid":0,"name":"default.md","title":"\u5927\u733f\u4eba","is_probation":0,"ref":"default.md","path":"3090391","index":0},{"id":3090392,"pid":0,"name":"\u5bf9\u63a5\u6587\u6863.md","title":"\u5bf9\u63a5\u6587\u6863","is_probation":0,"ref":"\u5bf9\u63a5\u6587\u6863.md","path":"3090392","index":1}]
    }
</script>
<script type="text/javascript" src="https://static.kancloud.cn/asset/reader.js?version=ed38795423544aa3e336"></script>
<script type="text/javascript">
        if (self === top) {
        kancloud.bootstrap();
    }
    </script>
<script src="https://www.topthink.com/assistant/js" async></script>
<script type="text/javascript">
    document.addEventListener('tas:ready',function() {
        window.tas.init('zPdyXwbQ', {
            appearance: {
                button: {
                    hidden: true
                }
            },
            chat: {
                enable: false,
            },
            robot: {
                enable: false,
            },
            broadcast: {
                enable: false,
            },
            doc: {
                enable: false
            },
            feedback: null,
            scripts: null
        })
    });
</script>
</body>
</html>
