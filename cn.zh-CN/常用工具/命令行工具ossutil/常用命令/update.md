# update {#concept_303828 .concept}

update命令用于更新ossutil版本。

## 命令格式 {#section_2fu_n1f_agm .section}

``` {#codeblock_w45_f1b_5gz}
./ossutil update [-f]
```

该命令检查当前ossutil的版本与最新版本，输出两者的版本号，如果有更新版本，询问是否进行升级。如果指定了--force（简写为-f）选项，当有可用更新时不再询问，直接升级。

## 使用示例 {#section_qjs_oz2_mx7 .section}

升级ossutil版本：

``` {#codeblock_rgf_izs_9af}
./ossutil update 
当前版本为：v1.5.1，最新版本为：1.6.0
确定更新版本(y or N)? y
更新成功!
```

## 常用选项 {#section_le1_8r7_kp2 .section}

您可以在使用update命令时附加如下选项：

|选项名称|描述|
|----|--|
|-f，--force|强制操作，不进行询问提示。|
|--retry-times|当错误发生时的重试次数，默认值：10，取值范围：1-500。|
|--loglevel|设置日志级别，默认为空，表示不输出日志文件。可选值为： -   info：输出提示信息日志。
-   debug：输出详细信息日志（包括http请求和响应信息）。

 |
|--proxy-host|网络代理服务器的url地址，支持http、https、socks5。例如https://120.79.128.211:3128、 socks5://120.79.128.211:1080。|
|--proxy-user|网络代理服务器的用户名，默认为空。|
|--proxy-pwd|网络代理服务器的密码，默认为空。|

**说明：** 更多通用选项请参见[查看选项](cn.zh-CN/常用工具/命令行工具ossutil/查看选项.md#)。

