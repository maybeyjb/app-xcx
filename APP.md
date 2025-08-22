# APP

# 资产收集

## mumu



1、反模拟器调试	2、反证书检验	3、工具证书没配置好	4、反代理VPN	5、app不走http/s 

因为bp抓的是web流量，有的app不走web，就抓不到

配置代理

这里注意：需要用当前的网段

![image-20250330174702626](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613087.png)

封包工具抓。有的app有调试检测，但是他只是启动的时候检测你是否有抓包，所以你启动app的时候不开，等进去后在开启bp/

科莱抓。

反模拟器、app判断的主要还是模拟器和真机之间的差异，比如模拟器没有手机卡，手机号，磁盘这些。

![image-20250330141912076](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613088.png)

apk的靶场。这个andior和java语言类似

![image-20250330180325526](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613090.png)

### 证书校验：

第6天前10分钟有安装配置证书的教程

单向校验--xp模块：屏蔽他的校验		演示安装xp。

开启xp模块，（重启模拟器），成功绕过靶场的单向验证 	xp框架绕过单向验证

![image-20250330194551395](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613091.png)

然后开启后就成功绕过：

![image-20250330223549789](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613092.png)

重打包。  重打包就是他会对自己的文件名有一个特有的md5值，然后只要你重打包后md5值就是发生变化，这时候打开app，发现md5值不同，就会出错。



### 代理检测 :

wifi自身代理：

![image-20250330223859577](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613093.png)

绕过代理：app代理工具postern来替换网络设置代理或者用本地代理工具proxifier（将模拟器的进程转发到指定的端口）

![image-20250405160701775](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613094.png)

![image-20250330201854774](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613095.png)

 本机设置代理

![image-20250330202319454](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613096.png)

这两种方式都可以绕过代理验证：

![image-20250330224025699](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613097.png)

## 翻车：

逍遥代理有问题，下次之间在多开器里面删了重新下载一个

模拟器的进程可以通过科莱来进行抓取确认，找到进程

app演示，绕过单向代理

![image-20250330224331512](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613098.png)

![image-20250330231008194](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613099.png)

双重代理：代理+证书校验   xp+代理工具

就是打开xp框架模板+代理工具就可以。

探探的双重验证。下节课

双重代理，就是这个app你需要挂代理，但是你还想抓流量包。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       

# 单向双向

mobexler：

运行即可，自动调试的：

![image-20250403104144702](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613100.png)

直接上传apk文件去，自动反编译分析，提取一些信息。反编译如果有壳，就反编译的不全。

![image-20250405144005058](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613101.png)

可能存在双向验证、就需要你脱壳后反编译找到里面的证书key导入，才能进行后续抓包操作：

![image-20250405144243295](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613102.png)

双向绕过：

需要将app的证书导入到bp中，app反编译找到证书，密钥来导入证书（能反编译，如果有壳就比较难，有证书文件）

![image-20250405144615335](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613103.png)

### 绕过方法：

探探的代理证书检测。

夜神的xp框架安装。

开始绕双向验证：先关闭通杀。配置对应frida   firda-tools版本

![image-20250403110942954](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613104.png)

与模拟器建立连接，需要启动模拟器frida，配置

真机是另一种配置方式

![image-20250403135536820](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613105.png)

 配置firda环境

![image-20250405170152741](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613106.png)

adb.exe：主机和模拟器之间连接用的。将下载的frida文件解压后放到对应的模拟器的adb.exe目录下。这里夜神是nox_adb.exe。

![image-20250405171718586](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613107.png)

做好转发：

![image-20250405173541687](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613108.png)

#### 方案1：

Firda+r0capture+WireShark   

这个方案比较简单，配置好就能抓到，但是WireShark 不方便，所以还是方案2比较合适测试。

![image-20250403135616424](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613109.png)

安装r0capture即可，配置好，真机下载另一个配置。

python r0capture.py -U -f com.well.likes -p tantan.pcap

![image-20250405202647861](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613110.png)



无论哪个方案都要看这3个好着没；

1、运行模拟器里的frida 	2、3、看与模拟器连接是否正常。 	、

最后是看你的frida的版本是否和上传到模拟器上面的frida版本一致，这里翻车了很久

![image-20250405202939617](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613111.png)

![image-20250405203224351](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613112.png)

#### 方案2：

Firda+HOOK-JS+BurpSuite

需要准备好js，hook技术

将js文件放到模拟器的目录下，利用Firda技术配合代理和js文件（hook）成功抓取数据包到bp中。

![image-20250403135728385](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613113.png)

FridaScripts-main 主要是这个技术里面的js包。

s![image-20250405203525685](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613114.png)

frida  -U  -f  com.p1.mobile.putong  -l  SSLUnpinning.js    	com.well.likes	com.p1.mobile.putong

![image-20250405213212122](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613115.png)

利用Firda技术绕王者营地，记住要开启模拟器那边的Firda进程。翻车（xp框架容易搞崩app或者模拟器）：



测试抖音，比较困难，通杀方案也抓不全

这个方法都是先试一试上面单向的能不能行，不行再用这个方法。



## IOS

IOS端-双向认证-SSL Kill switch 2

因为证书是在apk包里面，所以我们直接解压，找到证书导入bp，但是需要密码，需要反编译，因为有壳，所以这里我们是没法绕过的。

直接解压apk文件    一般看的是里面的assets和res文件     再里面找到apk对应的证书。

![image-20250403140532904](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613116.png)

使用工具对目标apk进行反编译尝试，使用frida的另一个模块尝试脱壳。

使用对应的Dump模块进行脱壳的时候，需要进去输入对应的命令，这里xd不会，，，，，，


# 小程序

小程序还是推荐使用wx电脑真机进行抓包。然后如果非要拿手机，andrid需要root，ios较麻烦。

![image-20250406155017455](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613121.png)

 科莱确定进程，wechat.exe是wx的聊天进程，而wechatappex.exe才是小程序的进程。

前面都是配置代理，如果配置好后打开小程序显示网络异常，一般要么是代理没有配置好，要么就是浏览器的bp证书没装好。

### 反编译工具

![image-20250406132608425](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613122.png)

老牌unpackminiapp

配置环境

applet目录下，打开小程序所产生的文件夹，进行反编译。

unveilr

主包&分包   一般就是将有的功能点分开打包的。在一些大厂，功能多的会用分包.。

![image-20250406155054733](https://cdn.jsdelivr.net/gh/maybeyjb/blue-team/img/202506161613123.png)

所以一般对这种分包的用unveilr工具，支持对整个文件夹进行反编译。

演示

案例分析


