# 东莞理工疫情自动打卡助手

### 前言
做这个脚本的初心是帮助经常忘记打卡的同学避免断卡。但还是要提醒一下大家，请按需使用，切勿滥用。同时，因为提交的是上一次的表单，所以大家每次离校和返校记得当天十二点去更正自己的表单，保证最新最准确的数据。


### 使用方法
设置好Secrets即可。设置方法[点击这里](https://gitee.com/bertramoon/dgut-autoreport-configure)。有多个账号的话，以","分隔开，如设置USERNAME为"2018001,2018002"，PASSWORD为"123456,7891011",SERVER_KEY为"-K SCT105680T2xabydNVRuTkcMm7PKQgWaJE,SCT105696T3sabwdNBRuTkcMm7XQSgNsCD"。

> 如果需要实现fork该仓库后可以自动拉取更新最新版的话，[点击这里](https://gitee.com/miranda0111/JDscret/blob/main/backup/reposync.md#%E7%94%B3%E8%AF%B7pat)申请并配置好PAT


### 更新日志

#### 2022-1-19
- 解决https连接失败问题：openssl版本问题导致与学校服务器连接不上，修改预装版本为`ubuntu-18.04`从而降低openssl版本并成功连接

#### 2021-12-24
- 更新README.md内容
- 将每日打卡时间定为每天1:00和8:00
- 将自动拉取更新频率调整为3天
- 结果显示学号最后两位改为最后四位

#### 2021-12-22
- 修改部分代码，当今日已经打过卡时，Server酱不再进行推送打卡成功信息
- 考虑到大部分人的Server酱没有会员，因此修改为只推送标题（没会员只能推送标题），内容包括学号和打卡情况

#### 2021-12-21
- 增加Server酱订阅微信通知服务

#### 2021-12-21
- 疫情打卡系统更新，调用的dgut-requests也进行了更新，主要是删除了location参数
