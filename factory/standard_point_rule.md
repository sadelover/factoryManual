# 什么标准点名 #
  标准点名是一套用于统一暖通空调系统点名命名的规则，使用这套规则后，常见设备的控制策略将能自动匹配项目点规则，比如开关设备、设备诊断、效率分析等高级用途中，将省去再配置点名的工作。

  另一个好处是项目的横向比对，使用同一套规则语言，将变得标准化、通用化。比如项目A的RealtimeEfficiency点和项目B的RealtimeEfficiency点代表的都是各自的机房整体效率，可直接互相比对。


# 常用点名规则 #


## 冷水机组 ##
  常用语义：
   `Ch`: Chiller 冷机
 `ChW`: Chilled Water 冷冻水
 `CW`: Cooling Water 冷却水
 `Enter`: 进口
`Leave`: 出口
`AMP`: Amper 电流 
`Eva`: Evaporator 蒸发器
`Con`: Condensor 冷凝器

```
以下01后缀表示1#冷机，如果2#冷机则后缀改为02

冷机以Ch开头
风冷热泵以 ASHP开头
水源热泵以 WSHP开头
地源热泵以 GSHP开头
```
### 冷机通讯卡读取点名 ###


|编号|	点名	|点名解释	|数据类型|	值解释及注意点|	单位要求|
|--|--|--|--|--|--|
|1	|ChOnOff01	|1#冷机开关机状态	|bool	|false：处于关闭状态，true：处于开启状态	||
|2	|ChOnOffSetting01	|1#冷机关机开机命令设置	|bool	|false：发送关指令，true：发送开指令	||
|3	|ChAmpLmtSetPointFeedback01	|1#冷机电流百分比限定值反馈	|double	|机组的最大限定，一般不变，值是95-100|	%|
|4	|ChAMPS01	|1#冷机电流百分比	|double	|实际冷水机组运行电流百分比，值范围是0-100	|%|
|5	|ChAutoMode01	|1#冷机控制远程就地状态	|bool	|false：就地，true：远程	||
|6	|ChChWTempSupplyActiveSetPoint01	|1#冷机冷水温度实际设定反馈	|double	|一般6-11	|摄氏度|
|7	|ChChWTempSupplySetPoint01	|1#冷机冷水温度设定	|double	|一般6-11	|摄氏度|
|8	|ChCondPressure01	|1#冷机冷凝器冷媒压力	|double	|	|kPa|
|9	|ChCondTemp01	|1#冷机冷凝器冷媒温度	|double		||摄氏度|
|10	|ChEnterCondTemp01	|1#冷机冷凝器进水温度	|double	|	|摄氏度|
|11	|ChEnterEvapTemp01	|1#冷机蒸发器进水温度	|double		||摄氏度|
|12	|ChErr01	|1#冷机故障报警	|bool	|false：正常，true：报警	||
|13	|ChEvapPressure01	|1#冷机蒸发器冷媒压力	|double	|	|kPa|
|14	|ChEvapTemp01	|1#冷机蒸发器冷媒温度	|double	|	|摄氏度|
|15|	ChGasExhaustTemp01	|1#冷机排气温度	|double	|	|摄氏度|
|16|	ChLeaveCondTemp01	|1#冷机冷凝器出水温度	|double	|	|摄氏度|
|17|	ChLeaveEvapTemp01	|1#冷机蒸发器出水温度	|double	|	|摄氏度|
|18|	ChMotorRunHour01	|1#冷机压缩机运行时间	|int	|	|小时|
|19|	ChOilDP01	|1#冷机油压差	|double		||Pa|
|20|	ChOilT01	|1#冷机油温	|double		||摄氏度|
|21|	ChWarningFaultCode01	|1#冷机故障代码	|int	|整数，直接从冷机通讯中读取，不需要翻译|无	|

### 冷机附属阀门点名 ###

|编号|	点名	|点名解释	|数据类型|	值解释及注意点|	单位要求|
|--|--|--|--|--|--|
|1	|ChEvaValveAutoMode01	|1#主机冷冻电动阀远程就地状态	|bool	|false：就地，true：远程	|无|
|2	|ChEvaValveEnabled01	|1#主机冷冻电动阀使能	|bool	|false：禁用，true：启用	|无|
|3	|ChEvaValveErr01	|1#主机冷冻电动阀使能	|bool	|false：正常，true：报警	|无|
|4	|ChEvaValveOnOffSetting01	|1#主机冷冻电动阀开关设置	|bool	|false：正常，true：报警	|无|
|5	|ChEvaValveStatus01	|1#主机冷冻电动阀开关状态	|int	|0：关闭状态, 1：开启状态, 2：关闭中，3：开启中	|无|
|6	|ChConValveAutoMode01	|1#主机冷却电动阀远程就地状态	|bool	|false：就地，true：远程	|无|
|7	|ChConValveEnabled01	|1#主机冷却电动阀使能	|bool	|false：禁用，true：启用	|无|
|8	|ChConValveErr01	|1#主机冷却电动阀报警	|bool	|false：正常，true：报警	|无|
|9	|ChConValveOnOffSetting01	|1#主机冷却电动阀开关控制|	bool	|false：发送关指令，true：发送开指令	|无|
|10	|ChConValveStatus01	|1#主机冷却电动阀开关状态|	int	|0：关闭状态, 1：开启状态, 2：关闭中，3：开启中	|无|

### 冷机附属电表点名 ###
|编号|	点名	|点名解释	|数据类型|	值解释及注意点|	单位要求|
|--|--|--|--|--|--|
|1	|ChPower01	|1#冷机电表实时有功功率	|double		|无|kW|
|2	|ChPowerTotal01	|1#冷机电表有功电度值	|long int		|无|kWh|

### 冷机附属虚拟软件点点名 ###
|编号|	点名	|点名解释	|数据类型|	值解释及注意点|	单位要求|
|--|--|--|--|--|--|
|1	|ChEnabled01	|1#冷机启用（使能）	|bool		|0:禁用, 1:启用, 只有启用时冷机才能被开关操作，一般当冷机维修时本点位由软件设置为0|无|


## 水泵 ##
```
设备代码如下，表格举例以CWP为例：
CWP: 冷却泵
PriChWP	一次冷冻泵
SecChWP	二次冷冻泵
HWP	热水泵
CT	冷却塔
```

### 设备下位机点点名 ###

|编号|	点名	|点名解释	|数据类型|	值解释及注意点|	单位要求|
|--|--|--|--|--|--|
|1	|CWPPressureSupply01	|1#冷却循环泵的供水压力	|double	|如果没有安装，则省略|	bar|
|2	|CWPVSDFreq01	|1#冷却循环泵频率反馈	|double|	无	|Hz|
|3	|CWPVSDFreqSetting01	|1#冷却循环泵频率设定|	double	|无	|Hz|
|4	|CWPErr01	|1#冷却循环泵故障报警	|bool	|false：正常，true：报警|	无|
|5	|CWPAutoMode01|	1#冷却循环泵手自动状态	|bool	|false：就地或手动，true：远程或自动	|无|
|6	|CWPOnOff01	|1#冷却循环泵运行状态	|bool	|false：关闭状态，true：开启状态	|无|
|7	|CWPOnOffSetting01|	1#冷却循环泵启停控制	|bool|	false：关命令，true：开命令|	无|
|8	|CWPPower01	|1#冷却泵总有功功率	|double|	无	|kWh|
|9	|CWPPowerTotal01	|1#冷却泵有功电能	|int	|无	|kWh|
|10	|CWPEnabled01	|1#冷却泵是否可用	|bool	|false：禁用，true：启用	|无|

### 附属虚拟软件点点名 ###
|编号|	点名	|点名解释	|数据类型|	值解释及注意点|	单位要求|
|--|--|--|--|--|--|
|1	|CWPEnabled01	|1#冷却泵启用（使能）	|bool		|0:禁用, 1:启用, 只有启用时设备才能被开关操作，一般当设备维修时本点位由软件设置为0|无|


## 末端风机盘管 ##

### 设备通用点名 ###
|编号|	点名	|点名解释	|数据类型|	值解释及注意点|	单位要求|
|--|--|--|--|--|--|
|1	|F01FCUOnOff01|	1层1#风盘开关状态	|bool	|false：处于关闭状态，true：处于开启状态	|无|
|2|	F01FCUOnOffSetting01|	1层1#风盘开关设定|	bool	|false：发送关指令，true：发送开指令	|无|
|3|	F01FCUFanSpeedSetting	|1层1#风盘风速档位设定|	int	|0：高, 1：中 , 2：低 ,3：自动	|无|
|4	|F01FCUTempSetting|	1层1#风盘温度设定	|double		||摄氏度|
|5|	F01FCUModeSetting	|1层1#风盘模式设定	|int	|0：冷，1：暖，2：睡眠	|无|
|6	|F01FCUFanSpeed|	1层1#风盘风速档位反馈|	int	|0：高, 1：中 , 2：低 ,3：自动	|无|
|7|	F01FCUTemp|1层1#风盘测量温度反馈	|double		||摄氏度|
|8|	F01FCUMode|	1层1#风盘模式反馈	|int	|0：冷，1：暖，2：睡眠	|无|
|9|	F01FCUPanId	|1层1#风盘设备本身地址	|int	|1~99	|无|
|10	|F01FCUAddress|	1层1#风盘PANID	|int	|1~99	|无|
