## uni-storage键名命名规范

实际开发中，开发者通常会用到 [storage（本地缓存）](https://uniapp.dcloud.net.cn/api/storage/storage.html)，官方的开源库如uni-admin等也使用了storage。

为了规范storage的键名命名，避免与其他开发者的键名冲突，DCloud新增了storage键名命名规范，同时我们推荐所有的插件作者也使用这套规范，如下：

1. storage的键名必须以插件id作为前缀，如 uni-admin 的前缀为 uni-admin-
2. 键名命名要达意，易于通过键名了解这个storage里存的是什么数据，如 uni-admin-theme（admin的主题）

## 官方插件storage键名列表

|插件id							| 键名															| 说明																																																|
| :------:					| :------------------:							| :------------------:																																								|
| uni-id						| uni_id_token											| uniId的Token（由于历史原因，此键名使用了下划线而不是中划线）																				|
| uni-id						| uni_id_token_expired							| uniIdToken的过期时间，时间戳形式（由于历史原因，此键名使用了下划线而不是中划线）										|
| uni-id-pages			| uni-id-pages-userInfo							| 最近一次登录的用户信息																																							|
| uni-admin					| uni-admin-theme										| admin当前使用的主题																																									|
| uni-admin					| uni-admin-statTabsData						| 缓存uni-stat-tabs组件内部数据																																				|
| uni-data-select		| uni-data-select-lastSelectedValue	| 记录最后一次选择的值																																								|
| uni-app客户端sdk	| UNI_LOCALE												| uni.setLocale 记录最后一次设置的语言（由于历史原因，此键名使用了下划线而不是中划线）								|
| uni统计客户端sdk	| __DC_STAT_UUID										| 用户设备id																																													|
| uniCloud客户端sdk	| __LAST_DCLOUD_APPID								| 上次运行到此host+port的应用appId，仅开发调试期间生效。用于清理上个应用内存储的可能影响本次运行的内容|


