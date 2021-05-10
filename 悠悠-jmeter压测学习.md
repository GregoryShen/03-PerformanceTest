







## [21-Plugins Manager插件管理器](ddd)

### 前言

前面讲了 JDBC 连接数据库的时候,需要下载 mysql 对应的 jar 包, 放到 `lib\ext`目录下就可以使用了.

JMeter 有个插件管理器 Plugins Manager,可以方便的管理其他插件的下载和更新.

### 插件管理器 Plugins Manager

下载地址: https://jmeter-plugins.org/install/Install/

下载插件后把 jar 包放到 `lib/ext` 目录,然后重启 JMeter

### 查看插件管理

重启 JMeter 后打开 `选项`->`Plugins Manager`

出现报错: Failed to download plugins repository. One of the possible reasons is that you have proxy requirement for Internet connection.
Please read the instructions on this page: https://jmeter-plugins.org/wiki/PluginsManagerNetworkConfiguration/

解决文档地址: https://jmeter-plugins.org/wiki/PluginsManagerNetworkConfiguration/

### 解决报错

解决办法:

下载 JMeter Plugins Manager 证书,使用 Chrome 打开如下地址: https://jmeter-plugins.org/ 选择安全证书.

证书->详细信息->复制到文件->下一步->使用 Base64 编码格式, 报错文件名称为 `pluginsManager.cer`

以管理员身份打开 cmd, 进入到 jdk 安装目录, 找到 jre 的 bin 目录下,执行一下指令,当前 cer 证书地址为: `C:\Users\dell\Desktop\PluginsManager.cer`

```shell
.\keytool.exe -import -alias JMeter -keystore ..\lib\security\cacerts -file "C:\Users\dell\Desktop\PluginsManager.cer"
```

输入密钥库口令: `changeit`

是否信任此证书? [否]:  y

验证证书已经安装成功

```shell
.\keytool.exe -list -keystore ..\lib\security\cacerts -alias JMeter
```

### 插件管理

再次重新打开 JMeter, 在选项里就能正常打开插件管理了

* Installed Plugins(已安装的插件)

  即插件 jar 包中已经包含的插件,可以通过选中勾选框来使用这些插件

* Available Plugins(可下载的插件)

  即该插件扩展的一些插件,可以通过选中勾选框来下载你所需要的插件

* Upgrades(可更新的插件)

  即可以更新到最新版本的一些插件,可以通过点就右下角的 Apply Changes and Restart JMeter 按钮来下载更新

Available Plugins 勾选需要下载的插件(勾选了`Selenium/WebDriver Support`, `Test Plan Check Tool`, `Throughput Shaping Timer`)

## [22-监听器之每秒事务数Transactions per Second](https://mp.weixin.qq.com/s/5F1J4csoLyJwsZOjH9r38g)

### 前言

Transactions per Second 也就是每秒事务数,在性能测试中非常重要的一个指标,我们在聚合报告里面能看到最后的测试结果 TPS 值.

如果我们想查看更详细的报告,查看压测过程中不同时间段的每秒事务数,可以使用 Transactions per Second 插件来查看.

### Transactions per Second

jmeter 安装后,添加监听器,是默认不带 Transactions per Second.

先安装 Jmeter 插件管理器,在插件管理页面,勾选 jpgc - Standard Set,点安装

安装完成后会自动重启 JMeter

### 监听器 - jp@gc - Transactions per Second

Transactions per Second 插件的作用是在测试脚本执行过程中,监控查看服务器的 TPS 表现 — 比如整体趋势、实时平均值走向、稳定性等.

添加监听器 jp@gc - Transactions per Second

设置线程5,循环100次开始压测,聚合报告看到吞吐量9.6/sec

再查看 jp@gc - Transactions per Second 插件的报告,可以看到更详细的实时 TPS

红色是代表全部成功的,有报错的话会绿色显示.

## [23-监听器之响应时间Response Times Over Time](https://mp.weixin.qq.com/s/WuGI2dpSBzjrihwm8WKK7g)

### 前言

压测的时候,我们会经常关注2个重要的指标 TPS 和 RT

* TPS 每秒处理的事务数(Transactions per Second), JMeter 的 Throughput 为吞吐量(请求数/秒)
* RT 响应时间(Response), 从发起请求到完全接收到应答的时间消耗.

### 每秒处理的事务数(Transactions per Second)

TPS: 每秒处理的事务数, JMeter 的 Throughput 为吞吐率(请求数/秒)

宏观上: TPS=并发数/响应时间, JMeter 的 Throughput = (number of requests)/(total time)

这里涉及到一个概念并发数,这个并发数是指单位时间内发出去的请求数.这里的单位时间并不是1秒,是一个绝对的同一时间,比如0.0001秒甚至更小的时间.

那么这里的绝对并发我们是没法知道的,我们通常说的并发数一个相对的并发,相对并发也就是我们线程组里面设置的(线程数)虚拟用户数.

根据聚合报告看到,平均响应时间是94毫秒,吞吐量27.9/sec

通过上面的公式 tps=线程数3/平均响应时间0.094秒,算出的结果是31.9,跟统计的27.9差不多.

也可以这样理解这个公式,绝对的并发数不存在的,请求发出的时间总有先后,绝对的 TPS 也是无法计算的,统计的角度看

TPS = 服务器处理请求总数/花费的总时间

我们设置线程组的持续压测时间为5秒,设置线程数3,于是压测的结果TPS值数27.5

根据公式 TPS = 总请求数139/总时长5秒,得到的结果是27.8,这样就很接近报告的 TPS 值了.

为了找到服务器的最大 TPS 值,我们一般设置不同的并发数(线程组)来压测.

### 响应时间(Response Time)

RT 也就是平均响应时间(Response Time),在聚合报告里面可以看平均值(单位是毫秒),如果我们想查看更详细的报告,跟着每个时间段的平均响应时间,添加-监听器-jp@gc - Response Times Over Time

压测后,先看聚合报告的平均值92毫秒

再看实时监控的平均响应时间

这种曲线图在写性能报告的时候加上会显示更专业