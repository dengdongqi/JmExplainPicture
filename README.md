# 金茂智能魔镜APP简易说明书

## 功能介绍
* 主页
![首页图](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/1.png)
功能: 时间、天气、新闻、社区公告、音乐、留言、健康评测、安心食材、智慧菜谱、可视对讲(丰林、西西、罗格朗)、园区监控(大华、海康)、语音显示、设置  
* 左屏
![左屏图](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/2.png)
功能: 智能家居控制系统 (ABB、485直连BUSPRO、IP BUSPRO、485转USB ZIGBEE、485直连ZIGBEE、西门子)  
* 右屏
![右屏图](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/3.png)  
功能: 健康系统、户型系统、格瑞系统、科技系统

## 部分功能说明

### 设置
* 配置工具
![配置工具](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/4.png)
账号处输入特定密码触发影藏操作:  
①.0000000000 --> 返回系统桌面  
②.2222222222 --> 开启上传网址,可上传setting.txt等配置文件  
③.ADBWIFI --> 开启ADB WIFI 用于开发人员远程调试  
④.升级失败 --> pad133内存不足时,会导致升级失败.通过输入'升级失败'处理此问题.(前提是点击升级提醒下载好APK并升级无效之后输入才有效)
* 模块调试
![模块调试](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/5.png)  
设置-模块调试-输入工程密码'8888'  
可配置项目启用指定功能:智能家居、可视对讲、园区监控、右屏展示、物业名称、园区监控摄像头、主页图、可视对讲轮播图. 选择完成后滑动至底部点击应用完成修改配置
* 唤醒开关
设置-唤醒开关  
默认开启,AI语音使用的前提为<font color=red>魔镜可正常使用网络</font>,完成AI语音SDK验证才可使用  
测试: 对魔镜说<font color=red>'小茂你好'</font>唤醒AI对讲 魔镜回答'您好，很高兴为您服务'为正常  
提高识别率: 普通话发音标准,语速稍慢
* 蓝牙
<font color=red>健康系统</font>使用的前提必须打开蓝牙

### 可视对讲

#### 罗格朗
本地局域网LAN口通讯
* 服务器配置
本地服务器安装在电脑中，浏览器访问http://IP:8080/cfgserver进入地址本配置文件.
* 第三方服务器
三方服务器用来记录地址本（当本地配置服务器同步云小区，罗格朗服务器将地址本同步到三方服务器中）
* 魔镜配置方式
输入222222222222进入配置界面 选择依次选择户号(eg:’0区1栋2单元6层1户’) 完成绑定。
* 主机端配置:
(1).长按’#’号键进入管理页面
(2).输入密码(公司的主机设备密码:’111111’)
(3).按键’0’进入地址设置
(4).输入本地服务器中地址本对应主机的安装码完成配置
(5).路由器:路由器Ip改为主机对应的网关((3)地址设置处查看)

#### 西西
本地局域网LAN口通讯
* 服务器配置
将服务器安装在电脑中(并双击X:\apache-tomcat-X\bin\startup.bat启动服务),访问地址http://电脑IP:8080/intercom/#/login 账号密码super aaa。
* 添加设备
服务器-设备管理-项目信息-建筑信息-新建建筑-添加房间0107(房间号);服务器-设备管理-设备列表-新增设备(0107房间,魔镜mac,自动分配ip,此刻时间) 注!!!: 新增加设备后室外机端需要重启更新获取新增设备的IP地址.
* 魔镜配置  
(1).魔镜端-设置-配置工具-账号处输入222222222222- 进入配置界面  
(2).和魔镜同一局域网下, 用电脑访问魔镜端显示的魔镜访问地址  
(3).修改setting.txt文件中xixi标签下配置  
(4).xixi配置格式:#xixi@IP端口 eg:#xixi@192.168.0.201@8080  
(5).上传文件，自动提示重启后,完成配置
* 呼叫
室外机输入 0107(房间号) 呼叫魔镜
* 授权  
授权文件: rqe134dfaf.txt 需部署在服务器电脑的 X:\apache-tomcat-X\webapps\sdk_reg目录下.  
文件中关键内容 sdkNum:授权数量  expireDate:过期时间  
sdkNum超出/不足: 会导致初始化失败!!!!!!!!!!!! 解决办法:联系西西开发人员更新授权文件

#### 丰林
外网线上注册,注册之后可去除外网本地局域网LAN口通讯
![丰林可视对讲](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/6.png)  
* 一、门口机设置
![丰林机器设置网站](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/7.png)  
1. 查看门口机ip，先按#号键，输入<font color=red>反向日期</font>，eg：当时日期是2019/12/16 则输入：16122019 密码后按#。则会弹出当时机器ip和服务器地址  
2. 门口机工程配置页面 http://192.168.0.64(门口机IP):6060(门口机端口)/v1/intf/setting  (与室外机同一局域网内访问)
(1).服务器设置:112.74.164.111 ----> 输入目前服务器IP  
(2).服务器端口默认:180 ----> 目前服务器端口:180  
(3).安装位置: 0905  ----> 9单元5栋  
(4).门口机位置: 01 ----> 默认1楼，可设置-1，-2等！  
(5).电梯中继器账号:admin  
(6).电梯中继器密码:admin 只有设置主机后才能生效,与中继器对应  
(7).是否主机:'是' ----> 设置当前门口机为梯控主机 梯控数据与主机通讯  
(8).电梯出口：0 ----> 填写数字：0表示前门 1表示后门  
(9).网络选择：这里选择静态ip下列设置ip才能生效！  
(10).本机ip:门口机IP (读取默认)  
(11).子网掩码 (读取默认)  
(12).本机网关 (读取默认)  
(13).本机DNS  (读取默认)  
(14).设备名称: 门口机名称  
(15).------记录设备(门口机)ID号 下一步需要-------
3. 输入工程密码: '88888888'点击 提交 完成修改
* 二、 服务器管理平台 ( http://112.74.164.111:180/index.php/Home/index)
![丰林服务器管理平台](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/8.png)
账号密码: 登录所在大区的具体丰林服务器账号  
abcdef
123456  
hedong
123456  
tfjmy
123456
1. 选择 '设备上线' -- 添加 -- (序列号,机器码) 填一2(15)步记录的门口机id
2. 重启门口机
3. 选择 '设备上线' -- 添加 -- (序列号,机器码) 填魔镜序列号地址 -->可视对讲配置页面魔镜序列号eg:RC133N120030013
 三、 魔镜端配置
 ![丰林魔镜端配置](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/9.png)
1. 方式一: 设置 - 可视对讲 - 输入工程密码 '8888'进行设置  
(1).设备名称:室内机XXXX  
(2).安装位置: 一2(3) 一致  eg:0905  
(3).房号,楼号: int 两位数 eg:09,02 九楼二号房  
(4).服务器IP: 一2(1) 一致  
(5).服务器端口: 一2(2) 一致
2. 方式二: 上传Setting_XXXXXX.txt 丰林配置  
(1).丰林配置格式: #fenglin@AliasName@UnitNo@FloorNo@RoomNo@ServerIp@ServerPort,eg:#fenglin@室内机0907@0905@09@07@112.74.164.111@180  
(2).上传并重启 应用/魔镜 完成配置
* 呼叫
室外机输入 0902(房号,楼号) 呼叫魔镜

### 园区监控

#### 大华
本地局域网LAN口通讯
 ![大华界面](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/9.png)
* 查看设备属性
登录路由器查看’终端设备’获取设备分配的IP 端口默认37777  
同局域网下访问摄像头ip 可进入设备配置页, 账号密码默认 账号:admin  密码:admin / admin123 / admin000
* 魔镜配置方法  
(1).魔镜端-设置-配置工具-账号处输入222222222222- 进入配置界面  
(2).和魔镜同一局域网下, 用电脑访问魔镜端显示的魔镜访问地址  
(3).修改setting.txt文件中大华摄像头的ip地址与设备端分配的IP一致,端口,摄像头账号密码  
(4).大华配置格式:#摄像头昵称@摄像头IP@默认端口@账号@密码,eg:#电梯口@192.168.1.108@37777@admin@admin  
(5).上传文件，自动提示重启后,完成配置
* 魔镜(LAN)，摄像头局域网通讯,必须同一局域网下才能正常使用
* 甲方正常要求-30秒超时自动挂断

#### 海康萤石云
外网通讯,需正常访问网络
* 切换萤石云账号  
(1).配置文件setting.txt内更新haikang标签下配置  
(2).格式:#haikang@(具体萤石云开发账号appKey)@(具体萤石云开发账号appSecret)   (<font color=red>key,secret云平台 https://open.ys7.com/cn 获取</font>)  
(3).eg.#haikang@a19cef09fbd44642bb4f990faacbac9d@f905ef86efa096ba45664904721fac54  
(4).应用内-设置-配置工具-账号处输入"2222222222"  
(5).通过电脑在魔镜同局域网下访问"魔镜访问地址"  
(6).上传更新配置文件setting.txt,并按提示重启魔镜  
* 问题:<font color=red>调用次数超过限制</font>
 开发者账号的api调用次数超过限制,云平台开通企业账号/付费可增加调用次数

### 智能家居

#### ABB
本地局域网WIFI通讯
![ABB](https://raw.githubusercontent.com/dengdongqi/JmExplainPicture/main/2.png)
* 更换ABB配置
1. 更换IP/端口  
(1).魔镜端-设置-配置工具-账号处输入222222222222- 进入配置界面  
(2).和魔镜同一局域网下, 用电脑访问魔镜端显示的魔镜访问地址  
(3).修改setting.txt文件中abb标签下配置  
(4).abb配置格式:#abb@IP端口 eg:#abb@192.168.1.232@8888  
(5).上传文件，自动提示重启后,完成配置
2. 更换设备配置  
(1).默认模板xlsx设备配置文件:[模板](https://github.com/dengdongqi/JmExplainPicture/blob/main/jinmao_smart_home.xlsx)  
(2).按模板格式更新具体详情设备xlsx表格数据  
(3).魔镜端-设置-配置工具-账号处输入222222222222- 进入配置界面  
(4).和魔镜同一局域网下, 用电脑访问魔镜端显示的魔镜访问地址  
(5).上传XLSX文件,手动重启APP,完成配置
