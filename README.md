### 部署步骤
机器需求：
1. 2012 windows server
2. centos 7.2

windows程序需求：
1. 注册32位PHPCOM.dll ，放置C:\Windows\SysWOW64，需要安装2012 C++依赖库
    
```
//注册com组件
cd C:\Windows\SysWOW64
regsvr32.exe PHPCOM.dll
```

2. C盘根目录放置 mtmanapi.dll mtmanapi64.dll
3. pythonCOM 加入计划任务，python程序放置D:\pythonCOM

```
//程序说明
D:\pythonCOM\config.json //配置文件
D:\pythonCOM\com.py //主程序
D:\pythonCOM\moniter.py //监控脚本文件
```

```
//运行说明:只需要moniter.py脚本
python moniter.py
//假如设置了计划任务，从计划任务启动即可
```

4. mt4数据库备份服务 MetaTrader4ReportServer开启

```
cd D:\MetaTrader4ReportServer
mtreportsrv.exe /install  //安装服务
mtreportsrv.exe /start  //启动服务
//假如已安装服务，重启即可
mtreportsrv.exe /restart  //重启服务
```

5. 报价websocket程序 AppServer

```
cd D:\AppServer
```

6. 信号源ea


### 重启pythonApi服务
#### 命令行启动或运行定时任务
```
python D:\pythonCOM\moniter.py
```
#### 查看启动日志
```
D:\pythonCOM\log\[moniter]-2018-04-28.log
```
#### 浏览器访问本地端口确认开启
```
127.0.0.1:5000/ping
```
成功启用服务的返回值
```
{
  "code": 200
}
```
