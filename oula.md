
## [怪盗]Oula Aleo高性能锄头Ubuntu+HiveOS部署教程v1.8

###📺怪盗oula锄头视频教程
（旧版，现已升级为oula品牌，但方法大同小异）： 

[https://www.youtube.com/watch?v=K4PSg9bZ6i0](https://www.youtube.com/watch?v=K4PSg9bZ6i0)


## 一、 注册oula账户

点击以下怪盗邀请链接注册 (收不到验证码的话, 可能在垃圾邮箱中)：
[https://oula.network/zh/register?invitation=SDDV6L](https://oula.network/zh/register?invitation=SDDV6L)

登录后台-子账户管理-添加一个子账户名,这个就是挖矿账户
![image](https://github.com/user-attachments/assets/5f1779c8-a7e3-4c8a-bae3-5f41ba87578d)

提现:（仅测试锄头的话可跳过）
登录后台-付款设置-绑定自己aleo钱包地址，要先开通谷歌验证。
快速生成自己的 aleo 钱包地址：[https://www.provable.tools/account](https://www.provable.tools/account)
也可以用LEO wallet(网页版和手机都有)： [https://www.leo.app](https://www.leo.app)



## 二、Ubuntu系统:
### 检查环境
需要ubuntu22以上， cuda12.3以上的环境
输⼊```hostnamectl```查看ubuntu版本号,
![image](https://github.com/user-attachments/assets/5ad08c15-3844-4fd7-b46c-35db1c332929)
输入```nvidia-smi```查看cuda和显卡驱动版本,
如果不满⾜操作先卸载驱动:
输⼊```nvidia-uninstall -s -q``` 或 ```apt --purge remove nvidia*``` 或```apt autoremove```，不同系统版本或显卡输⼊
的命令会有不同。
### 下载CUDA&驱动并安装:
```
wget https://developer.download.nvidia.com/compute/cuda/12.6.0/local_installers/cuda_12.6.0_560.28.03_linux.run
```
```
chmod +x cuda_12.6.0_560.28.03_linux.run
./cuda_12.6.0_560.28.03_linux.run --silent --toolkit --driver
```

### 下载锄头
最新版本：[https://github.com/oula-network/aleo/releases](https://github.com/oula-network/aleo/releases)
以下为v1.8为例,实际请更换为最新版本链接:
```
wget https://github.com/oula-network/aleo/releases/download/v1.8/oula-pool-prover
```
启动锄头：
```
chmod +x oula-pool-prover
./oula-pool-prover --pool wss://aleo.oula.network:6666 --account kidcdf --worker-name worker01
```
（以上kidcdf为测试账号， 可换成你oula注册的子账户名）
![image](https://github.com/user-attachments/assets/9d1aeb8b-0421-429e-be4f-cf4f70e73f66)

启动后,等待⼏分钟后，可在Oula后台查看到算⼒情况.

更多方法：
[https://oula-faq.gitbook.io/zh/kai-shi-wa-kuang/publish-your-docs](https://oula-faq.gitbook.io/zh/kai-shi-wa-kuang/publish-your-docs)

**********************************************************************************************************************************

**********************************************************************************************************************************

## 三、HIVEOS部署流程:
第一次用 HIVEOS的，看这里安装和启动:

[https://github.com/gdkiddd/oula/blob/main/hiveos_first.md](https://github.com/gdkiddd/oula/blob/main/hiveos_first.md)

环境要求：hiveos-0.6-227-stable（Ubuntu 20.04）

### 1️⃣ 检查hiveos版本是否是基于Ubuntu 20.04:
```hostnamectl```

如果ubuntu版本正确,则升级显卡驱动(必须!)
```
nvidia-driver-update
```

### 2️⃣ 添加钱包
[https://the.hiveos.farm/wallets](https://the.hiveos.farm/wallets) ，输入aleo查找：

<img width="598" alt="image" src="https://github.com/user-attachments/assets/de7f1a51-fb24-40fa-9447-8b030636a4be">

### 3️⃣ 添加飞行表：
复制下面代码
```
{"name":"oula_miner",
"isFavorite":true,
"items":[{"coin":"ALEO","pool_ssl":false,"wal_id":10333513,"dpool_ssl":false,
"miner":"custom",
"miner_alt":"oula_miner",
"miner_config":{"url":"wss://aleo.oula.network:6666",
"algo":"aleo",
"miner":"oula_miner",
"template":"%WAL%",
"install_url":"http://23.106.143.181/oula/oula_miner-v0.3.0.tar.gz"},
"pool_geo":[]}]}
```
点击hiveos-飞行表-添加自【剪切板】，可一键配置：

![image](https://github.com/user-attachments/assets/7cc98dfb-3236-4172-9dfc-2718713dda63)
输入飞行表名称， 创建飞行表后，就算成功了。

### 4️⃣ 启动 hiveos飞行表

运行前先升级hiveos显卡驱动
```
nvidia-driver-update
```
开机后从优盘启动系统，启动后会自动运行飞行表，自动下载oula程序并启动，
如果启动后提示 github 程序下载失败， 可能是你没有翻墙。

启动后过10分钟左右， 等算力稳定，以下为启动运行成功后，显示算力的画面：

![telegram-cloud-photo-size-5-6194924926851466377-y](https://github.com/user-attachments/assets/758270a2-11d5-47b1-90d9-edddc5a0dc04)

## 疑难解答:
咨询怪盗:  [https://t.me/gdkiddd](https://t.me/gdkiddd)

aleoAsic: [https://aleoasic.com](https://aleoasic.com)
