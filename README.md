# 东莞理工疫情自动打卡助手

### 贡献者名单
按首次参与项目的时间顺序排序
- [Bertramoon](https://github.com/Bertramoon )
- [miranda0111](https://github.com/miranda0111 )
- [drpasserby](https://github.com/drpasserby )
- [IceWindy233](https://github.com/IceWindy233 )

### 前言
做这个脚本的初心是帮助经常忘记打卡的同学避免断卡。但还是要提醒一下大家，请按需使用，切勿滥用。同时，因为提交的是上一次的表单，所以大家每次离校和返校记得当天十二点之后进行一次手动打卡更新自己的表单，保证最新最准确的数据。


### 使用方法
#### 设置环境变量Secrets，配置好账号密码等信息

详细设置方法[点击这里](https://gitee.com/bertramoon/dgut-autoreport-configure)。下面给出简易的设置方法：

首先我们进入`Settings->Secrets->Actions`

![点击secrets](https://gitee.com/bertramoon/img/raw/master/Auto_Report/%E8%AE%BE%E7%BD%AEsecrets.png)


然后设置好相应的secrets即可。例如账号是2018001，密码是123456，只需要设置好USERNAME为2018001，PASSWORD为123456即可。

![设置secrets](https://img-blog.csdnimg.cn/706476d5d770472c8aa472383602cce6.png)

设置完成后启动GitHub Action工作流：

![进入Action](https://img-blog.csdnimg.cn/829ab2c53b0d49bf95daa68fe5f5d0b2.png)

![开启Action](https://img-blog.csdnimg.cn/9a243b9d9d4c420d9a1039872f87c64e.png)

这样就配置好了。如果需要微信通知的话，[请点击这里](https://gitee.com/bertramoon/dgut-autoreport-configure)查看更详细的教程

> 如果需要实现fork该仓库后可以自动拉取更新最新版的话，[点击这里](https://gitee.com/miranda0111/JDscret/blob/main/backup/reposync.md#%E7%94%B3%E8%AF%B7pat)申请并配置好PAT


#### 设置身体状况、体温、是否在校内

##### 方法一：修改配置文件

打开`custom_data.json`文件，可以看到有3个字段：
```json
{
    "body_temperature": 36.6,
    "health_situation": 1,
    "is_in_school": 1
}
```

- body_temperature: 体温，自行填写，一般是36.5-37.0。也可以默认
- health_situation: 身体状况，默认1，表示良好。2-11表示不同身体问题
- is_in_school: 1表示在松山湖校区，2表示在莞城校区，3表示不在学校，也是自行填写

##### 方法二：设置环境变量Secrets

**如果设置了三天自动同步，强烈建议用这个方法**

总共可以设置三个环境变量，且只有三个环境变量均设置了，才会使用环境变量的数据作为自定义数据：
- BODY_TEMPERATURE：体温，一般是36.5-37.0
- HEALTH_SITUATION：身体状况，1表示良好
- IS_IN_SCHOOL：1表示在松山湖校区，2表示在莞城校区，3表示不在学校


### 更新日志

#### 2022-10-23
- 减少重试次数和增加重试间隔，避免账号被误封
- 增加通过环境变量设置自定义数据的方法

#### 2022-10-5
- 增加贡献者名单

#### 2022-10-5
- 配置项custom_data.json增加是否在校。同时dgut-requests库更新，可以正常使用了

#### 2022-9-18
- 由于学校系统的健康状况和每日体温云端数据每日一刷新，因此将其提取为配置项。需要更新到最新版才能正常打卡，请周知。特别鸣谢[drpasserby](https://github.com/drpasserby )和[IceWindy233](https://github.com/IceWindy233 )两位小伙伴的帮助

#### 2022-8-18
- 更新README.md，增加简易使用方法，详细的方法则参考https://gitee.com/bertramoon/dgut-autoreport-configure

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
