# zhidiantianxia自动打卡，部署到腾讯云函数.
<!--more-->
## 一、注册腾讯云账号，并实名认证。

[点击注册](https://cloud.tencent.com/)

## 二、下载函数包

[点击下载](https://wwb.lanzouf.com/ilJzQ022ovkf)并解压缩。

解压后的文件目录：

```text
zhidiantianxia
├── README.md
├── README_EN.md
├── serverless.yml
└── src
    └── index.py
```

用记事本或其他文本编辑器打开serverless.yml

填写相应数据

```YAML
phone: 手机号
password: 密码
address: 地址
deviceToken: deviceToken
district: 地区
jishiKey: 即时达key
lat: 纬度
lng: 经度
# 下面三个看自己是否需要填写，不填就不用动
health_measures: none
origin_address: none
origin_address_detail: none
```

定时触发器

```YAML
events:
  - timer:
      parameters:
        # argument: ""
        # 每天00:00执行
        cronExpression: 0 0 0 */1 * * *
        enable: true
        qualifier: $DEFAULT
```

定时触发器，默认每天00:00执行，可自行修改为合适的时间。

## 三、部署

### 安装Serverless Framework CLI 

*先安装chocolatey，再用chocolatey安装serverless*

**安装chocolately**

官方教程

[点击查看](https://chocolatey.org/install#:~:text=Install%20Chocolatey%20for%20Individual%20Use%253A)

**安装serverless**

官方教程

[点击查看](https://cloud.tencent.com/document/product/583/44753#windows-.E7.B3.BB.E7.BB.9F)

安装完后，打开刚刚解压的文件夹，在地址栏输入cmd，回车。
在弹出的cmd窗口里面输入

`serverless deploy` 

回车，然后根据提示进行扫码等操作。

完成后，登陆控制台进行查看
[点击登录](https://console.cloud.tencent.com/scf/list)

----
**end**

