# Geolocation定位

定位模块封装了OS自带的`系统定位`，及市场上主流的三方定位SDK，如`高德定位`、`百度定位`等。并提供统一的JS API调用定位能力。

::: warning 注意
三方定位（高德、百度、腾讯、谷歌）是商业收费服务，需获取授权，注意避免侵权。[详见](#lic)
:::

|项目类型|API|
|:-|:-|
|uni-app|[uni.getLocation(OBJECT)](api/location/location?id=getlocation)|
|5+ App/Wap2App|[plus.geolocation.*](https://www.html5plus.org/doc/zh_cn/geolocation.html)

使用定位功能需在项目manifest.json的“App模块配置”中勾选“Geolocation(定位)”，并根据项目实际需求勾选使用的三方定位SDK：
![](https://native-res.dcloud.net.cn/images/uniapp/geolocation/modules.png)



### 系统定位  

> HBuilderX3.2.16开始独立出“系统定位”模块

使用`系统定位`需在“App模块配置”项的“Geolocation(定位)”下，勾选“系统定位”：
![](https://native-res.dcloud.net.cn/images/uniapp/geolocation/system.png)

`系统定位`调用设备的操作系统提供的定位服务，只支持wgs84坐标系，不同设备对定位功能支持的情况有所差异。

#### iOS平台
由苹果iOS系统提供定位服务，可以获取经纬度信息，支持解析地址信息，即可以直接返回城市街道信息。

#### Android平台
只可以获取经纬度信息，不支持解析地址信息，即无法返回城市街道信息。

标准Android系统的定位服务是Google提供的，但需要手机内置GMS服务，连接Google服务器。  
国内主流手机厂商均自行提供了定位服务，但小众品牌可能不支持，主流品牌中较老的机型也不支持。如下Android手机厂商都支持`系统定位`：
- 华为
- 小米
- Oppo
- Vivo
- 努比亚
- 一加
- 魅族
- 联想
- 金立

在国外通常都是使用Google的GMS提供定位服务。

**注意**
- 由于设备厂商适配的原因，在部分Android设备上定位服务可能不稳定，如需提升定位功能的稳定性建议使用`高德定位`或`百度定位`
- 本地离线打包参考[Android平台系统定位模块配置](https://nativesupport.dcloud.net.cn/AppDocs/usemodule/androidModuleConfig/geolocation?id=%e7%b3%bb%e7%bb%9f%e5%ae%9a%e4%bd%8d)、[iOS平台百度定位模块配置](https://nativesupport.dcloud.net.cn/AppDocs/usemodule/iOSModuleConfig/geolocation?id=%e7%b3%bb%e7%bb%9f%e5%ae%9a%e4%bd%8d)



### 高德定位

> 需要向高德申请商业授权，参考:[商业授权相关说明](app-geolocation?id=business)，使用前需登录 [高德开放平台](https://lbs.amap.com/) 创建应用申请Key

使用`高德定位`需在“App模块配置”项的“Geolocation(定位)”下，勾选“高德定位”：
![](https://native-res.dcloud.net.cn/images/uniapp/geolocation/amap.png)

#### 参数说明  
- appkey_android  
[高德开放平台](https://lbs.amap.com/)为Android平台申请的Key
- appkey_ios  
[高德开放平台](https://lbs.amap.com/)为iOS平台申请的Key

**注意**  
- 调用高德定位SDK提供的定位服务，仅支持gcj02坐标系，支持解析地址信息。
- 配置后需提交云端打包后才能生效，真机运行时请使用[自定义调试基座](https://ask.dcloud.net.cn/article/35115)
- 本地离线打包参考[Android平台高德定位模块配置](https://nativesupport.dcloud.net.cn/AppDocs/usemodule/androidModuleConfig/geolocation?id=%e9%ab%98%e5%be%b7%e5%ae%9a%e4%bd%8d)、[iOS平台高德定位模块配置](https://nativesupport.dcloud.net.cn/AppDocs/usemodule/iOSModuleConfig/geolocation?id=%e9%ab%98%e5%be%b7%e5%ae%9a%e4%bd%8d)


### 百度定位

> 需要向百度申请商业授权，参考:[商业授权相关说明](app-geolocation?id=business)，使用前需登录 [百度地图开放平台](https://lbsyun.baidu.com/) 创建应用申请访问应用密钥（AK）

使用`高德定位`需在“App模块配置”项的“Geolocation(定位)”下，勾选“高德定位”：
![](https://native-res.dcloud.net.cn/images/uniapp/geolocation/baidu.png)

#### 参数说明  
- appkey_android  
[百度地图开放平台](https://lbsyun.baidu.com/)为Android平台申请的访问应用密钥
- appkey_ios  
[百度地图开放平台](https://lbsyun.baidu.com/)为iOS平台申请的访问应用密钥

**注意**  
-调用百度定位SDK提供的定位服务，仅支持gcj02/bd09/bd09ll坐标系，支持解析地址信息。
- 配置后需提交云端打包后才能生效，真机运行时请使用[自定义调试基座](https://ask.dcloud.net.cn/article/35115)
- 本地离线打包参考[Android平台百度定位模块配置](https://nativesupport.dcloud.net.cn/AppDocs/usemodule/androidModuleConfig/geolocation?id=%e7%99%be%e5%ba%a6%e5%ae%9a%e4%bd%8d)、[iOS平台百度定位模块配置](https://nativesupport.dcloud.net.cn/AppDocs/usemodule/iOSModuleConfig/geolocation?id=%e7%99%be%e5%ba%a6%e5%ae%9a%e4%bd%8d)


<a id="business"/>

### 商业授权相关说明@lic

#### 国内用户
2021年起，高德、百度、腾讯等地图服务商开始商业授权。

授权费用：5万元/年。

例外：如果是公益类应用，可以申请豁免商业授权。只要不是公益应用，不管你有多少用户，都需要获取商业授权。

**未授权面临的问题和风险：**
1. 法律问题：违反产品使用许可，也就是侵权了
2. 功能问题：定位、地图、服务器相关接口随时可能被停用
3. 上架某些应用市场会提示侵权而导致无法上架

**商业授权的范围：**
1. 凡是要请求地图厂商服务器的，均属于授权范围。不管是使用这3家的定位SDK、地图SDK，不管是app、web、小程序、服务器接口。
2. 如果你的应用没有配置在3家厂商注册账户后申请的应用秘钥（AppKey等），则无需付费。比如在小程序里使用自带的定位api和map组件，已经由小程序平台给地图厂商付费了，所以开发者无需再向地图厂商申请appkey和付费。但如果开发者自己调用了高德等服务器接口，比如逆地址解析，仍然要付费。

**如何节省费用：**
1. 使用定位时，可以优先调用系统定位。
  - iOS可以直接用。
  - Android如果在国外可直接用。如果国内，因为google服务被墙，情况较复杂。
    + 小米、华为的系统定位可以直接用，因为他们已经向地图厂商购买了授权并封装成了系统定位。但其他品牌的手机则需要开发者自行测试，也有的品牌在较新的手机上支持了系统定位。手机webview的定位api背后也是系统定位，如果系统定位支持，就可以直接用，如果不支持，那webview里也用不了。所以无需考虑用webview的定位来绕过。
    + 微信浏览器、QQ浏览器的定位之所以可以使用，也是因为这些浏览器厂商向地图厂商购买了授权。如果你的web应用跑在这些浏览器里，调用定位api是没问题的。
  - 系统定位只能拿到坐标，无法获取地址信息，比如城市、街道。如需要根据坐标获取街道信息，需使用地图厂商的逆地址解析，这属于商业授权范围。
2. 在你的app里通过schema调用，打开地图厂商的app，比如直接交给高德地图来导航，这种情况无需在地图厂商注册账户和获取应用key，也就不需要付费。
3. 联系DCloud申请折扣优惠。

DCloud为开发者争取了福利，可优惠获取高德、腾讯的商业授权。如有需求请发邮件到`bd@dcloud.io`（注明你的公司名称、应用介绍、HBuilder账户）；你也可以直接通过`uni-im`发起在线咨询，在线咨询地址：[DCloud地图服务专员](https://im.dcloud.net.cn/#/?user_id=b9839630-a479-11ea-b772-0f6ad6cf835c)。

#### 海外用户
海外用户使用google地图，也需要付费，支持按量付费，具体请参阅google地图官网。

