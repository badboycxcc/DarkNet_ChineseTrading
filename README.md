# 2021 最新情况
感谢作者大佬的支持。我才能顺利把项目跑起来！
![](深度截图_选择区域_20210512144633.png)

获取信息（不定期更新）https://t.me/reboot_onion(https://t.me/reboot_onion)










### 分割线 ------------------------------------------------------------------------------------

![mosaic.jpg](media/mosaic.jpg)
## DarkNet_ChineseTrading - 暗网中文网监控实时爬虫
![](https://img.shields.io/badge/language-python3-orange.svg)
![](https://img.shields.io/badge/platform-mac|lunix|window-orange.svg)

> [En_Doc](https://github.com/aoii103/DarkNet_ChineseTrading/blob/master/README_en.md)
> [教程:如何实现暗网交易监控](https://mp.weixin.qq.com/s/OaPjAaNcEefQxaXQykheqg)

## 监控大屏(grafana快速实现)
![](media/grafana.png)



## 功能

- Tor节点切换
- 自动注册(中文式账户)
- 自动登录
- 防封禁
- ORM交互
- 事件详情/样本信息录入
- 事件提醒（`telegram`）[图文]
- 分类爬取
- 裸体图片过滤(保存但不发送)
- 残留EXIF-GPS信息提取

加入我们：[https://t.me/fordarknetspiderbot](https://t.me/fordarknetspiderbot)

## 安装

- ###

- #### python环境配置

	下载并安装 *`python 3.8`*
	
	```
	pip install -r ./requirements.txt
	pip install -U 'requests[socks]'
	```
	
- #### tor安装

	> 当前需更新tor至[0.4.0.0版本]，旧版将有几率无法取得数据
	> 如果无法通过如下命令安装最新版，推荐至官网编译安装最新源码包
	
	```
	brew install tor
		
	cd /usr/local/etc/tor
	cp torrc.sample ./torrc
	vi torrc
	```

	将如下配置添加到 `torrc` 后，运行 `restart_tor.sh` 开启tor
	
	```
	SOCKSPort 9150 					# socks5代理地址
	Socks5Proxy 127.0.0.1:1086 		# 科学上网代理地址(如已翻墙可不填)
	RunAsDaemon 1 					# 开启后台运行
	ControlPort 9151 				# 开启控制端口
	```

- #### OCR(mac)

	> 识别率略低，可在parser.py的get_captcha处替换	

	![](media/captcha.png)

	```
	brew install tesseract
	```
	
	[snum.traineddata](media/snum.traineddata)


- #### 存储环境

	安装`Docker`后下载`Redis Mysql`即可

- ### Centos下环境安装

```bash
yum install epel-release -y
yum install redis mariadb mariadb-server git tesseract tesseract-langpack-deu tor -y 
wget -P /usr/share/tesseract/tessdata/ https://pyocean.com/data/tesseract/snum.traineddata 


systemctl start mariadb   #启动mariadb
systemctl enable mariadb  #设置开机自启动
mysql_secure_installation 
```

- ### 运行
	
	配置`config_dev.py`中的连接设定与`TelegramRobotToken`

	```
	mv config_dev.py conf.py 
	bash restart_tor.sh
	bash restart_task.sh
	python run.py
	
	```
	
- ### 运行逻辑
	
	![](media/DarkNet.png)
	
- ### 运行结果截图

	- #### telegram
		
		![](media/newtg.png)
		
	- #### `run.py`
	
		![](media/run.png)
	

- ### 额外命令

	```
	python3 run.py --help

	Usage: run.py [OPTIONS]

	Options:
	  --debug        Print debug log
	  --domain TEXT  Target domain.
	  --save_error   Whether to save the error log
	  --update       Whether it has only been updated to crawl
	  --help         Show this message and exit.

	```	
	


