

Miki量化框架  
====
	  1.目前量化领域，保密性几乎成为行业的标准，这同时也导致大量的重复性开发，Miki量化框架的宗旨就是希望能减少这种重复性
	    造轮子的情况。  
	  2.后期框架将会逐渐支持美股、日股等市场，最终目标是支持全球主要股票市场交易---如果技术能够实现的话。
	  3.完全采用python语言实现的量化框架，原则尽量以简洁的语言实现金融的交易等功能，系统架构清晰，方便二次开发，理论上支持
	    股票、期货、期权等，目前只支持股票。  
	  4.如果遇到问题，欢迎提交issue、代码，QQ群：1042883511。  

系统要求：
----	
	1.内存最好16G以上
	2.硬盘最好采用固态硬盘，1T~2T
	
框架架构：  
----
	1.api为下单接口实现  
	2.data为数据存储、接收、提取等功能的实现，实盘模式需要运行main.py文件  
	3.strategy为策略实现模块，  
	  * 1.新建py文件实现策略功能，   
	  * 2.from system.trade.strategyVar import * 引入全局变量  
	      initialize实现策略的初始化，
	      before_trading_start每天开盘前运行，  
	      handle_data每分钟运行，
	      after_trading_end每天收盘后运行，
	      after_backtest_end回测结束后运行。  
	3.trade主要包含context上下文会话、logger日志、order下单等模块，
	  others.yaml为一些配置，ChangeDict为公司股票更名信息，Multiplier为期货合约单位，
	  dataGenerator.py为数据推送引擎。   
	4.运行前，建议配备一块1T-2T的固态硬盘，通过dataOthers.py的save_old_data存储行情数据到本地，缓存大小大概150G左右
	  再通过generate_dataUnit函数生成cache推送数据，系统通过读取cache文件进行数据推送，  
	  dataSQL.py的update_finance_data从api读取财务数据存储到本地。  
	5.阅读源码也可以对系统架构更熟悉  


项目捐赠：  
---
	支付宝账号：15012463435



























