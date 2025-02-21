### uniCloud和微信小程序云开发、支付宝小程序云开发有何区别？

微信、支付宝、百度的小程序，均提供了云开发。但它们都仅支持自家小程序，无法在其他端使用。

`uniCloud`和微信小程序云开发、支付宝小程序云开发使用相同的基础建设平台，微信小程序云开发背后是腾讯云的TCB团队，支付宝小程序云开发背后是阿里小程序云团队。`uniCloud`是DCloud和阿里小程序云团队、腾讯云的TCB团队直接展开深层次合作，在他们底层资源的基础上进行二次封装，提供的跨端云开发方案。

简单来说，uniCloud和微信小程序云开发、支付宝小程序云开发一样稳定健壮，但有更多优势：
- 跨平台。不管你在uniCloud里选择了阿里还是腾讯的serverless，均可以跨uni-app的全端使用。从pc到h5，从Android到iOS，以及各家小程序快应用，十几个平台全端支持
- uniCloud提供了`clientDB`神器，减少90%的服务器开发工作量，且保障数据安全。[详见](/uniCloud/database)
- uniCloud提供了[uni-id](uni-id-summary.md)、[uniPay](/uniCloud/unipay)等重要框架，大幅减少开发者的相应功能开发量。
- uniCloud提供了[uni-starter](https://ext.dcloud.net.cn/plugin?id=5057)，客户端开发工作量大幅减少。
- uniCloud提供了[uniCloud admin](/uniCloud/admin)，管理端开发工作量大幅减少。
- uniCloud提供了[schema2code](schema2code.md)，只需编制数据库schema文件，用户端和管理端的数据列表、分页、搜索、详情查看、修改、删除，全套代码均能自动生成。
- 更易学。uniCloud提供了`JQL`查询语言，比SQL和MongoDB的查询语法更简单易掌握，尤其是联表查询非常简单。[详见](https://uniapp.dcloud.io/uniCloud/database?id=jsquery)
- 更完善的工具链。前端uni-app、云端uniCloud、还有ide端的HBuilderX，互相紧密搭配，打造闭环的优秀开发体验
- 更丰富的生态。插件市场有大量现成的轮子和资源 [详见](https://ext.dcloud.net.cn/?cat1=7&orderBy=TotalDownload)

如果你已经使用过微信小程序云开发，想进一步了解对比差异或如何从微信小程序云迁移到uniCloud，[详见](uniCloud/wx2unicloud.md)

### uniCloud稳定吗？DCloud服务器异常会影响我的线上业务吗？

`uniCloud`是 DCloud 和阿里云、腾讯云等成熟云厂商合作推出的云服务产品，阿里云、腾讯云等提供云端基础资源，DCloud提供API设计、前端框架、IDE工具支持、管理控制台、插件生态等服务，开发者的云函数直接托管在阿里云等服务商的serverless平台。

用户终端上的应用在运行时，直连云服务商serverless平台，不会经过DCloud服务器，开发者无需担心因DCloud服务器负载而影响自己业务的问题。

阿里云和腾讯云都有商业级SLA。如果真出问题，他们会负责赔偿。

### 云函数 和 传统 Node.js 开发有何区别？

云函数相当于 Node.js + Serverless + DCloud改进。
- 传统Node.js开发需要购买服务器，安装Node.js环境，部署 pm2 等守护进程；云函数无需考虑服务器环境，只需专心实现业务代码，然后将云函数一键上传，云服务商负责云函数运行环境的准备。
- 传统Node.js开发模式，开发者需监控服务器参数，比如硬盘使用率，避免服务器负载过高导致业务中断；云函数模式下，开发者无需关心云函数运行的宿主环境，云厂商会实现服务调配及硬件监控。
- 用户量较大时，传统Node.js开发需考虑购买更多服务器并实现负载均衡；云函数模式下，云服务商自动弹性扩容，开发者无需担心服务器扛不住压力。
- 传统Node.js开发模式，需考虑安全防护，比如DDos攻击；云函数模式，云厂商的API网关会做拦截防护，开发者无需关心，并可节省高防IP等费用

总结一下，前端同学即便可熟练编写Node.js代码，但对于DB优化、弹性扩容、攻击防护、灾备处理等方面还是有经验欠缺的，但`uniCloud`将这些都封装好了，真正做到仅专注业务实现，其它都委托云厂商服务。

另外，在 Node.js 代码实现上，云函数每次执行的宿主环境（可简单理解为虚拟机或服务器硬件）可能相同，也可能不同，因此传统`Node.js`开发中将部分信息存储本地硬盘或内存的方案就不再适合，建议通过云数据库或云存储的方案替代。

当然还有最重要的一点，在uniCloud中，推荐大量业务使用clientDB，一个应用中写不了太多云函数。

### uniCloud只支持uni-app，怎么开发web界面？

uni-app可以开发web界面，详见：[uni-app宽屏适配指南](https://uniapp.dcloud.io/adapt)

如果是需要pc版admin的话，uniCloud提供了[uniCloud admin](https://uniapp.dcloud.io/uniCloud/admin)

### 可否通过http url方式访问云函数或云数据库？

- 场景1：比如App端微信支付，需要配服务器回调地址，此时需要一个HTTP URL。
- 场景2：非uni-app开发的系统，想要连接uniCloud，读取数据，也需要通过HTTP URL方式访问。

uniCloud提供了`云函数URL化`，来满足上述需求。[详见](https://uniapp.dcloud.io/uniCloud/http)

### 微信云开发支持客户端直接操作数据库，uniCloud支持吗？

uniCloud提供了比微信云开发更优秀的前端操作数据库方案，见：[clientDB](clientdb.md)

### 云开发是nodejs+改良版MongoDB组合，对比php+mysql的传统组合怎么样？

nodejs的性能优于php，MongoDB的性能也优于mysql。

对于前端而言，MongoDB这种类json的文档数据库更加易用，且有更高的灵活性。
操作MongoDB仍然使用js的方法。

MongoDB非常灵活，可以对大数据量的表随便增加字段。而mysql的表数据量一旦变大，每增加一个字段，数据库的体积和性能都会造成负面影响。

MongoDB的字段可以嵌套，表达tree型的数据非常方便，扩展起来随心所欲。

对于希望增加数据冗余以提高性能的开发者而言，nosql数据库则是利器。

当然，对于喜欢传统数据库的开发者而言，仍然可以按传统方式设计数据库表结构。

MongoDB的功能要比mysql强大很多。sql太简单的了，一段sql语句其实就是一个字符串，写不了复杂的逻辑。

而MongoDB有非常多的js api，各种聚合运算符，它是可编程的，而不是仅靠一段字符串sql语句来表达。

举个例子，商品数据表中有4个字段：浏览量、收藏量、购买量、评价。需要生成一个近期热门商品列表，4个字段各占25%的权重，加权后排序。这种需求sql是无法直接实现的。而MongoDB里可以一个查询直接返回排序好的结果。

SQL的模糊查询也很弱，like只有前后%，导致很多开发者不得不再使用ElastciSearch这些三方数据库。虽然后期版本的mysql也支持有限正则。但MongoDB的正则查询还是超过开发者预期的强大。

MongoDB虽然强大，但易用性不佳，尤其是聚合运算写起来非常复杂。

uniCloud在MongoDB的基础上改良，进一步提供了`DB Schema`和`JQL`。

`DB Schema`是一个json文件，可以对数据进行描述、约定字段值域、控制操作权限、描述字段之间的关系，让数据库管理更高效，并且大幅降低了服务端的代码开发工作量。[详见](https://uniapp.dcloud.io/uniCloud/schema)

`JQL`是一套操作uniCloud数据库的方法，它更符合js开发者的习惯，并且极大的降低了学习成本和代码量。
比如联表查询、tree查询，都变的非常简单。像tree查询是以往只有oracle才有的功能。`JQL`文档[详见](https://uniapp.dcloud.net.cn/uniCloud/database?id=jsquery)

曾经DCloud官方也推进过阿里云和腾讯云提供serverless的mysql。但经过对MongoDB的深入研究和改良，DCloud已经放弃了难用的mysql。推荐开发者了解uniCloud的云数据库，用起来更强大和方便。

### 支持websocket吗？

:::warning 注意
在云函数请求三方服务器时支持任意方式请求，包括http、websocket（需要使用nodejs原始的写法或三方包，后续uniCloud会支持websocket相关接口）等。下面说明的是针对云函数和客户端之间的通讯的说明
:::

1. uni-push2.0，全端支持（APP、H5、各端小程序）当应用在线时就是一个免费的websocket服务，详情文档：[https://uniapp.dcloud.io/unipush-v2.html](https://uniapp.dcloud.io/unipush-v2.html)
2. 如果是im方面的需求，有DCloud基于uni-push2.0开发的云端一体的、全平台的、免费的、开源即时通讯系统，详情查看：[https://uniapp.dcloud.net.cn/uniCloud/uni-im.html](https://uniapp.dcloud.net.cn/uniCloud/uni-im.html)

### 如何导入老数据库的数据？
- 方式1：可以在HBuilderX里用db_init.json来批量创建云数据库和插入表内容，[详见](https://uniapp.dcloud.io/uniCloud/cf-database?id=%e4%bd%bf%e7%94%a8db_initjson%e5%88%9d%e5%a7%8b%e5%8c%96%e9%a1%b9%e7%9b%ae%e6%95%b0%e6%8d%ae%e5%ba%93)
- 方式2：阿里云支持在uniCloud web控制台界面直接导入导出数据
- 方式3：在云函数里，使用nodejs标准写法，连接老数据库，如使用mysql的[插件](https://ext.dcloud.net.cn/plugin?id=1925)，把数据读出来，再批量写入云数据库
- 方式4：将一个云函数URL化，用其他语言读取老数据库，通过http方式提交到云函数，云函数将接收到的数据存入云数据库

### 云函数访问时快时慢怎么回事？

云函数对应的资源，如果长时间不使用，会被阿里云或腾讯云平台从内存中释放。一旦被释放，启动云函数时会有一个冷启动的过程。

表现为：隔了很久不用，第一次用就会比较慢，然后立即访问第二次，则很快，毫秒级响应。

冷启动的速度一般不会超过1.5秒，如超过1.5秒应该是云函数写的有问题或网络有问题。

资源回收策略方面，阿里云是15分钟内没有第二次访问的云函数，就会被回收。腾讯云是半小时。

两家云厂商仍然在优化这个问题。目前如果开发者在意这个问题，给开发者的建议是：
1. 使用clientDB可以减少遇到冷启动问题的概率
2. 非高频访问的云函数，合并到高频云函数中。有的开发者使用纯单页方式编写云函数，即在一个云函数中通过路由处理实现了整个应用的所有后台逻辑。参考[插件](https://ext.dcloud.net.cn/search?q=%E8%B7%AF%E7%94%B1&cat1=7&orderBy=UpdatedDate)
3. 非高频访问的云函数，可以通过定时任务持续运行它（注意腾讯云可以使用这个方式完全避开冷启动，而阿里云的定时任务最短周期大于资源回收周期）
4. 配置云函数的单实例多并发，请参考：[单实例多并发](cf-functions.md#concurrency)

### uniCloud访问速度感觉不如传统服务器？@slow
有开发者在一台单机上安装php或java，连接同电脑的mysql。然后与uniCloud比较速度，认为uniCloud偏慢。这里需要澄清如下差异：

- 原因1. 冷启动。具体分析见上一问题

- 原因2. 代码和数据库不在一台服务器
在一台单机上安装php或java，同时安装数据库，访问速度确实快。但在使用云数据库时，即数据库是单独的服务器，和运行代码不在一台服务器上时，就会略微造成些延迟。但商业应用的数据库肯定都是独立服务器。

- 原因3. 拦截器
后端开发的请求一般都有路由管理框架或拦截器，每个请求都要拦截，校验权限。使用这类框架肯定会增加耗时。

clientDB就是这种情况，因为clientDB内部有权限校验系统，某些权限的验证还需要数据库查询。

所以虽然clientDB的速度慢一些，但实际上开发者在自己写了路由拦截和权限管理的框架后，速度也一样会下降。

从uni-id 3.0起，用户的角色权限缓存在token里，不再查库。clientDB的速度比之前提升了100毫秒左右。如果还未升级，请尽快[升级](https://ext.dcloud.net.cn/plugin?id=2116)。同时注意如果用了uniCloud admin，也要配套升级。如果自己在云函数里编写过相关业务逻辑，请务必阅读升级注意事项。

- 原因4. 数据库索引

查询表的索引要正确配置，需要在where里查询的字段都建议配上索引，否则查询会很慢。

但注意索引不能太多，否则增删改数据时又会变慢，精准很重要。推荐详细阅读[索引文档](https://uniapp.dcloud.io/uniCloud/db-index)

### 发布H5时还得自己找个服务器部署前端网页，可以不用自己再找服务器吗？

uniCloud支持[前端网页托管](https://uniapp.dcloud.io/uniCloud/hosting)，选择阿里云作为云厂商时完全免费！

- 如果你已经有备案过的域名，直接解析过来即可；
- 如果你要新注册域名，备案流程和传统云主机略有不同，涉及一个uniCloud没有固定ip的问题。此时可以去买花生壳的备案服务；也可以临时买一个短期固定ip，走固定ip备案。这里有开发者分享的[经验贴](https://ask.dcloud.net.cn/article/38116)

如果是因为微信js sdk等服务要求配置固定ip白名单，那么腾讯云收费空间已经支持固定ip，[详见](https://uniapp.dcloud.io/uniCloud/cf-functions?id=eip)

### uniCloud云数据库如何实现全文检索

uniCloud的云数据库本身就是文档型数据库，可以全文检索。

查询数据时可以传入正则表达式。相比sql的like只有前后的%，正则表达式要强大的多。详情请参考[正则表达式查询](https://uniapp.dcloud.io/uniCloud/cf-database?id=regexp)

当然如果你需要额外配置ElastciSearch等三方数据库，也可以自己找服务器安装这些服务，同步数据，把需要搜索的数据同步过去。

### uniCloud内如何使用formdata

nodejs本身不支持formdata，但是可以通过手动拼装formdata的方式来进行支持，[参考](https://www.npmjs.com/package/form-data)

结合`uniCloud.httpclient.request`使用的示例

```js
const FormData = require('form-data');
let form = new FormData();
form.append('my_field', 'my value');
form.append('my_buffer', new Buffer(10));

form.append('img', new Buffer(10), {
  filename: `${Date.now()}.png`,
  contentType: 'image/png'
})

uniCloud.httpclient.request('https://example.com',{
  content: form.getBuffer(),
  headers: form.getHeaders()
})
```

### 腾讯、阿里的serverless有什么大案例？

- 微信小程序云开发，已经有50万开发者，包括腾讯自有的很多大日活应用都构建在腾讯云serverless上，如微信生活缴费、乘车码、微信读书、腾讯新闻、腾讯相册等。
- 2019年双11，阿里部分业务已经迁移在serverless上。支付宝小程序也提供了云开发功能。


### 如何控制云函数数量？云函数是否可以按多级目录整理@merge-functions

不需要控制数量，实际开发中不会突破限制。

因为实际开发中会使用框架而不是真的一个一个开发云函数。

1. 使用[clientDB](https://uniapp.dcloud.net.cn/uniCloud/clientdb)。这种方式是在前端直接操作数据库，此时一个云函数都不需要写。开发效率远超传统开发模式。包括它配套的action云函数是不占用云函数数量的。
2. 使用[uni-cloud-router单路由云函数框架](https://uniapp.dcloud.net.cn/uniCloud/uni-cloud-router)，这种方式只有一个云函数，所有接口都是这个云函数的不同参数，它有统一的路由管理。

以免费空间的48个云函数举例，一般情况下：
- [uni-id](uni-id-summary.md)会有一个云对象（uni-id-co）或老版的云函数（uni-id-cf），这是必备的一个云函数
- 如果使用uni统计、app升级中心、uni发布平台、uniPush2、[uni-search热搜词统计跑批](https://ext.dcloud.net.cn/plugin?id=3851)，这些会自带云函数

上述几个是官方推荐的几个常用框架所带的云函数，然后开发者自己的代码里，大多数业务使用clientDB开发，不写云函数，或者写了配套的action云函数也不占用云函数数量；如果还需要自己写一些云函数，再加上uni-cloud-router，用这个单路由云函数搞定剩余需求；另外如果有跑批数据的需求可以再来一个云函数。所以无论如何48个云函数都占不满。

uniCloud的每个云函数是一个独立进程，不存在云函数级别的多级目录概念。

每个云函数下可以有子目录，但它们都属于这个云函数的一部分，而不是另一个云函数。

单路由云函数框架不止是官方提供的uni-cloud-router，插件市场有很多类似框架：[详见](https://ext.dcloud.net.cn/search?q=%E8%B7%AF%E7%94%B1&cat1=7&orderBy=TotalDownload)


### 港澳台及境外用户访问比较慢怎么办@global-accelerate

港澳台及海外/国外用户需要使用全球加速（海外加速）。uniCloud服务商为阿里云时支持配置全球加速，步骤如下：

1. 参考[阿里云全球加速](https://help.aliyun.com/document_detail/153198.html)文档，开通服务并对`自有域名`进行加速
2. 将上述域名CNAME到`api.next.bspapp.com`
3. [自行初始化uniCloud](uniCloud/init.md)传入endpoint参数，其值为开通全球加速的自有域名

### 腾讯云提示当前实名主体已经有三个账号怎么办@tencent-exceed-account-limit

开通腾讯云服务空间时实名认证提示实名主体已有三个账号，这往往是开发者在微信小程序开发工具里不小心开通了多个免费的小程序云，此时可以参考以下流程注销不用的账号：

1. 打开[腾讯云找回账号](https://cloud.tencent.com/services/forgotAccount)页面
2. 选择找回账号方式为实名信息
3. 操作完成之后可以看到自己实名信息对应的全部腾讯云账号
4. 选择不使用的账号登录之后注销即可，参考文档：[注销腾讯云账号](https://cloud.tencent.com/document/product/378/30253)

同时，如果付费购买腾讯云服务空间，每个账号可以最多拥有50个腾讯云服务空间（注意其中仅有一个享受免费额度）。

### 高并发下简单的防止超卖

> uniCloud阿里云现已支持redis，开通并使用redis请参考:[redis开通和使用](uniCloud/redis.md)，如何使用redis防止超卖请参考：[redis高并发抢购](uniCloud/redis.md?id=snap-over-sell)（推荐使用）。如下方式针对无redis场景比较不灵活（不推荐使用）

高并发时很多用户同时对一条数据读写，很容易造成数据混乱，表现在秒杀抢购等场景就是超卖。以秒杀为例，开发者可以从扣除库存这步入手对超卖进行很大程度的限制，下面是一个简单的示例（**注意以下代码未使用事务**）

```js
// 云函数
const db = uniCloud.database()
const dbCmd = db.command
exports.main = async function(event){
  const transaction = await db.startTransaction()
  // 其他业务逻辑...
  // 库存减一
  const reduceRes = await db.collection('goods').where({
    _id: 'goods_id', // 商品ID
    stock: dbCmd.gt(1) // 限制库存大于1的才允许扣除库存
  }).update({
    stock: dbCmd.inc(-1)
  })
  if(reduceRes.updated === 0) { // 如果没成功更新库存就认为下单失败
    await transaction.rollback()
    return {
      code: 1001,
      message: '下单失败'
    }
  }
}
```


### 云存储、数据库还没有使用就多了几次

关于云存储：这里的读写次数，并不一定是针对文件的：包括：上传文件、修改Policy、修改ACL、修改CORS 等操作，都会被认为是COS写。环境初始化时也会执行很多次初始化操作，写入 policy/acl/cors 等配置信息。用户每次操作 修改安全域名、修改静态域名等，也会触发 CORS 的写入。

关于数据库：开发者通过uniCloud web控制台访问数据库也会增加少量读写次数

### 部署网站到前端网页托管报“The requested file was not found on this server.”

- 部署history模式的uni-app项目时，如果未修改前端网页托管的配置，直接访问子页面时就会遇到上面的错误。如何配置请参考[部署uni-app项目](uniCloud/hosting.md?id=host-uni-app)

### 使用腾讯云报未登录Cloudbase

腾讯云会在本地storage存储一些信息，请不要在应用使用过程中使用clearStorage等接口直接删除storage。

### 阿里云前端网页托管域名报错指引@ali-hosting-domain

1. 错误信息：`该域名已经被添加过，不能重复添加`

  前端网页托管会和阿里云上其他的CDN业务（包括但不限于CDN）冲突，如需绑定到前端网页托管请先将此域名与其他业务解除关联。
  
2. 错误信息：`The root domain of your domain is reserved by another account`

  当前域名有在阿里云开通全站加速相关业务（可能配置了泛域名加速），与前端网页托管冲突。可以考虑使用三级域名或去除泛域名加速改为单独配置需要加速的域名。

### 授权其他用户访问服务空间@collaborator

详见文档：[服务空间的多人协作](/uniCloud/concepts/space?id=collaboration)

### 如何使用promise/async/await@promise

uniCloud客户端callFunction及数据库相关接口会返回Promise类型结果，请参考以下写法使用：

```html
// index.vue
<template>
  <view class="content">
    <button type="default" @click="testThen">promise+then</button>
    <button type="default" @click="testAwait">async+await</button>
  </view>
</template>

<script>
  export default {
    data() {
      return {}
    },
    methods: {
      testThen() {
        uniCloud.callFunction({
          name: 'test'
        }).then(res => {
          console.log(res)
        }).catch(err => {
          console.error(err)
        })
      },
      async testAwait() {
        const res = await uniCloud.callFunction({
          name: 'test'
        })
        console.log(res)

        // 如需捕获错误需使用如下写法
        // try {
        //   const res = await uniCloud.callFunction({
        //     name: 'test'
        //   })
        //   console.log(res)
        // } catch (err) {
        //   console.error(err)
        // }

      }
    }
  }
</script>

<style>
</style>
```

### 发生故障时如何判断故障点@fault

当你的系统出问题时，如何判断是DCloud还是阿里云或腾讯云的问题？

首先再次声明，DCloud的服务仅限于开发阶段。发行部署后，应用的访问不经过DCloud的服务器。

1. 通过域名判断故障点
- unicloud.dcloud.net.cn，属于DCloud，这个网站是开发期间使用的，你的应用上线运行时，不经过DCloud服务器。
	如果该域名可以访问，但是在该域名下操作连接阿里云或腾讯云的数据出现问题，那么也是阿里云或腾讯云出了问题。
- bspapp.com，属于阿里云。如果该域名访问报错，说明阿里云serverless出故障了。
- tencentcloudapi.com，属于腾讯云。如果该域名访问报错，说明腾讯云serverless出故障了。

当然还有一种情况报错，其实是客户端的问题，包括浏览器的跨域问题，或者小程序的域名白名单问题，导致客户端无法连接uniCloud。这需要通过配置来解决，参考文档：[小程序和浏览器的域名访问配置](https://uniapp.dcloud.io/uniCloud/quickstart?id=useinmp)

2. 通过测试系统判断故障点
- [hello uniCloud 阿里云版](https://hellounicloud.dcloud.net.cn/#/)
- [hello uniCloud 腾讯云版](https://hellounicloud.dcloud.net.cn/tcb/#/)

如果测试系统不正常，那就说明这家云厂商的服务出故障了。

这2个系统是完全独立的，如果两个系统都故障了，那就是2家云厂商都故障了，而不是DCloud服务故障了。再次声明，发布后的服务，不连接DCloud的服务器。

当遇到uniCloud故障时，在uniCloud的QQ群或论坛里反馈即可。因为阿里云、腾讯云其实都有拨测系统，他们也会及时知道故障并解决的。

### 常见错误@freq-error

**`operation exceeded time limit`、`云数据库执行时间超限`错误**

此错误一般由数据库操作超时引发，具体如何优化请参考：[性能优化](https://uniapp.dcloud.io/uniCloud/db-performance)

**使用事务时出现`WriteConflict`错误**

事务的执行会锁行，同时执行的不同事务在操作同一行数据是会存在冲突导致写入失败。尽量优化流程，避免事务互相冲突

**长时间未使用的服务空间再次访问时报错**

可能出现的错误信息有：`请求云函数超时`、`Response timeout for 10000ms, POST https://api.next.bspapp.com/server -1`

此问题一般是数据库长时间未访问，mongoDB WiredTiger存储引擎在内存中淘汰了表和索引，导致数据库请求超时引发云函数报错。

**腾讯云报`SIGN_PARAM_INVALID signature is expired`**错误

此问题一般出现在腾讯云云函数本地调试时，一般由当前开发用机器系统时间错误引起

**腾讯云报`access token disabled for ANONYMOUS login`错误**

服务空间从来没有上传过云函数，上传一个云函数即可

### 云函数通过https访问其他服务器时出现“certificate has expired”@lets-encrypt-cert

> 本章节仅对let's encrypt证书调整进行说明，其他情况请检查对应网站证书是否过期

let's encrypt于2021年9月30日根证书过期并切换到新版根证书。详情参考：[DST Root CA X3 Expiration (September 2021)](https://letsencrypt.org/docs/dst-root-ca-x3-expiration-september-2021/)。此次过期行为引起nodejs8请求使用了let's encrypt证书的网站时出现`certificate has expired`错误。

解决方案有以下两种：

1. 将云函数升级到nodejs12，删除旧云函数，配置node版本之后重新上传。详情参考：[云函数package.json](https://uniapp.dcloud.net.cn/uniCloud/cf-functions?id=packagejson)

2. （不推荐）使用`uniCloud.httpclient.request`时使用`rejectUnauthorized: false`。示例代码如下：

  ```js
  const https = require('https')
  const httpsAgent = new https.Agent({
    rejectUnauthorized: false
  })
  await uniCloud.httpclient.request('https://xxx.com/get', {
  	httpsAgent
  })
  ```

### 调用云函数时出现“Unauthenticated access is denied”@access-denied

如使用腾讯云作为服务商，出现此问题时请检查前端是否有执行clearStorage操作。clearStorage会清理掉腾讯云设置的token，导致请求云函数报错。

### 阿里云存储在部分地区、运营商无法访问的问题

阿里云云存储目前没有服务空间级别的域名隔离，因此在有服务空间的云存储因为违法、违规被封禁域名时会影响其他服务空间。阿里云提供了一个备用CDN域名`vkceyugu-backup.cdn.bspapp.com`，替换原CDN域名`vkceyugu.cdn.bspapp.com`。有一定业务量的用户可以在uniCloud web控制台云存储界面申请独立cdn域名。

### 等级保护认证

如需云厂商提供等级保护证书，请发送邮件到service@dcloud.io申请，邮件模板参考：[申请解除限制邮件模板](price.md#apply-email-template)

### 使用uniCloud.init初始化阿里云正式版服务空间报“InvalidSpaceId.NotFound”

商用版如果使用uniCloud.init需要自行传递endpoint参数，参考：[uniCloud.init](concepts/space.md#multi-space)

### 使用阿里云访问云函数时出现“unknow system error”

检查云函数运行时间是否超出配置的超时时间，优化代码逻辑或配置更长的超时时间

### 关于DDoS

对于针对ip地址进行的流量攻击是无法到达云函数的，云厂商的网关会拦截此类攻击流量。如果攻击者模拟真实请求，此时可以通过云函数[IP防刷](ip-filter.md)功能，进行一定程度的防护。云厂商也正在提供网关层面的防刷机制。

如何处理针对云存储的流量攻击，参考：[阿里云云存储安全策略](cdn-security-policy.md)