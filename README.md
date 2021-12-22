# 东莞理工疫情自动打卡助手

### 使用方法
设置好Secrets即可。设置方法[点击这里](https://gitee.com/bertramoon/dgut-autoreport-configure)。有多个账号的话，以","分隔开，如设置USERNAME为"2018001,2018002"，PASSWORD为"123456,7891011",SERVER_KEY为"-K SCT105680T2xabydNVRuTkcMm7PKQgWaJE,SCT105696T3sabwdNBRuTkcMm7XQSgNsCD"。


### 更新日志

#### 2021-12-22
- 修改部分代码，当今日已经打过卡时，Server酱不再进行推送打卡成功信息
- 考虑到大部分人的Server酱没有会员，因此修改为只推送标题（没会员只能推送标题），内容包括学号和打卡情况

#### 2021-12-21
- 增加Server酱订阅微信通知服务

#### 2021-12-21
- 疫情打卡系统更新，调用的dgut-requests也进行了更新，主要是删除了location参数
