# 实现功能

- [x] 易班签到(基于易班校本化的签到都可以使用此脚本)
  - [x] 登录时数美验证码验证（浏览器方法）
  - [x] 多用户签到
  - [x] 获取签到排名
  - [x] 自动校正签到时间
  - [x] 签到提交
    - [x] 自动获取签到位置
    - [x] 使用绑定的设备签到
    - [x] 自定义位置
    - [X] 图片签到
- [x] 易签到(易班app内签到分支)
  - [x] 多用户签到
  - [x] 获取签到结果
  - [x] 自动校正签到时间
  - [x] 签到提交
    - [x] 自动获取签到位置
    - [x] 自定义位置
    - [X] 图片签到
- [x] 易班销假（提交issues开放）
- [x] 签到程序自动更新
- [x] 多线程签到（多用户、多学校、不同签到入口同时完成）
- [x] 签到结果推送
  - [X] pushplus推送加（目前需要实名认证后才可使用，认证费用1元由推送加收取，与本脚本无关）
```diff
- 图片签到有校内和校外之分，目前仅测试过校外
```
#### 如果您的学校不支持此脚本或在使用中有任何问题，请提交Issues联系我

# 警告
## 使用本项目，您必须接受以下内容，否则应当退出此页：
### 此脚本仅开源基础功能，完整功能由开源者控制，仅供个人免费研究使用，控制的内容包括：
#### 设备允许签到的数量
#### 用户是否允许签到
#### 强制更新脚本

* 此项目运行过程中会收集您的个人信息（用于控制单一设备用户数量）
* 仅额外提供给“记性较差忘记签到”的人
* 使用此脚本有可能违反您所在 单位/学校 的规章制度
* 使用此脚本所造成的一切后果您应当明白，包括但不限于：
* 账号被封停
* 您个人被给予相关处罚
> 使用并复制此脚本，则默认视为您 已经接受 了此免责声明。请仔细阅读
> 
- - - 
# 支持学校列表（排名按已知先后顺序）
```diff
+ 福建林业职业技术学院  晚签
- 佳木斯大学 （暂不确定）
+ 台州学院  晚签
+ 福州大学  晚签  销假
+ 三江学院  晚签  销假
- 四川轻化工大学  （暂不确定）
+ 南京工程学院 早签
+ 东莞职业技术学院  易伴云  晚签
+ 闽南科技学院
+ 哈尔滨商业大学
+ 东莞职业技术学院
- 黑龙江科技大学 （暂不确定）
+ 昆明冶金高等专科学校
- 江门职业技术学院 （暂不确定）
+ 广东食品药品职业学院  晚签
+ 福州大学至诚学院  易伴云 晚签
- 四川工业科技学院  （暂不确定）
- 海南卫生健康职业学院  （暂不确定）
+ 广西建设职业技术学院  晚签
- 福建医科大学  （暂不确定）
- 广东金融学院  （由于碰到的素质极差，永不支持，源代码层面禁用）
+ 厦门海洋职业技术学院  晚签
+ 长春大学旅游学院 （暂不确定）
- 更多学校敬请反馈
```
- - - 
### [下载点此](https://github.com/2117516450/yiban-signin/releases)
- - - 
### [程序使用帮助|讨论](https://github.com/2117516450/yiban-signin/issues/10)
### 程序使用帮助|讨论QQ群 `643200955`
- - - 
此脚本已开源部分代码及制作方式/思路：
https://www.wcyuns.cn/archives/yiban

将视情开源所有代码
- - - 

```mermaid
graph TD;
    易班-->登录;
    登录-->登录成功;
    登录-->登录失败;
    
    登录成功-->签到任务;
    签到任务-->校本化;
    登录成功-->销假任务;
    销假任务-->获取未销假假条;
    获取未销假假条-->销假;
    销假-->获取销假结果;
    获取销假结果-->销假完成;
    销假完成-->程序退出;

    登录失败-->密码错误;
    登录失败-->数美验证码;
    
    密码错误-->程序退出;
    数美验证码-->登录;

    校本化-->签到流程;

    签到流程-->晚点签到;
    签到流程-->易签到;

    易签到-->签到时间判断;
    晚点签到-->签到时间判断;

    签到时间判断-->到签到时间;
    签到时间判断-->未到签到时间;

    到签到时间-->获取签到位置;
    获取签到位置-->位置选择;

    未到签到时间-->等待到达签到时间;
    等待到达签到时间-->到签到时间;

    位置选择-->范围内签到;
    位置选择-->范围外签到;

    范围内签到-->上传图片或绑定设备签到;
    范围外签到-->上传图片或绑定设备签到;

    上传图片或绑定设备签到-->成功签到;

    成功签到-->获取签到结果;
    获取签到结果-->通过配置方式发送给用户;

    通过配置方式发送给用户-->程序退出;
```
### 脚本基于python，由于在windows上进行开发编译，仅保证windows10+以上系统正常工作，linux_x86(CentOS Stream release 10)、linux_arm(香橙派)下编译后不保证脚本正常使用，mac系统暂未编译

# 运行环境
## Windows
已封装`exe` 已在`Windows11` `Windows10`上测试通过（理论上全Windows系统通用）
## Linux
已测试编译发布ARM及X86版本，如有其他需求或在使用过程中出现问题，请提交issues

# 运行方式
## Windows
双击 易签.exe 后，会自动在目录下生成 user_status.json 文件，填写 user_status.json 文件后重新运行程序即可开始签到
### Windows 下自动运行
使用 任务计划程序  详细配置请参照[任务计划程序启动闪退](https://github.com/2117516450/yiban_signin/issues/13)
## Linux
运行./yiqian.bin即可，同目录下填写`user_status.json`文件
### Linux 下自动运行
都用上linux了应该自己会设置自动签到了
注意：一定要`cd`到脚本所在目录，不然无法获取配置文件

# 配置脚本
详细配置详解请到： [json配置](https://github.com/2117516450/yiban-signin/blob/main/json.md)

脚本使用已经尽量简便化，基础使用只需要在配置中填写易班的账号密码

不可删除配置中的""，有可能导致程序出错

只要正确输入账号密码就可以开始自动签到

详细配置在`user_status.json`文件中（运行exe后自动生成）
如对配置脚本有疑问，请提交Issues联系我

# 用户配置

## 单用户账户配置

```json
"user": [
        {
            "enable": "默认填写1，改为0则停止此用户签到",
            "user": "默认为空，填写易班账号",
            "password": "默认为空，填写易班密码",
            "PhoneModel": "默认为空，填写手机型号（如不清楚用途请留空）",
            "PhoneCode": "默认为空，填写手机识别码（如不清楚用途请留空）",
            "pushplustoken": "默认为空，填写pushplus推送加token",
            "yiqiandao_name": "默认为空，填写易伴云签到模块名称（使用易伴云签到必填，否则可能出现错签）",
            "yiqiandao_uuid": "这里填易伴云的设备id，如签到时提示有设备绑定就需要填，填写方式请看https://github.com/2117516450/yiban_signin?tab=readme-ov-file#%E5%AD%97%E6%AE%B5%E8%A7%A3%E6%9E%90",
            "other": "默认为空，功能未开发，备用",
            "record_cancel": "默认为空，填1则进行销假",
            "LngLat": {
                "stat": "默认为0，填写1则使用自定义的签到位置（如不清楚用途请留空让程序自动获取）",
                "lon": "默认为空，stat为1时生效，填写经度，填写格式必须为：123.123456",
                "lat": "默认为空，stat为1时生效，填写纬度，填写格式必须为：12.123456",
                "Adders": "默认为空，填写地址（有些学校地址获取的是学校名称，此栏目可改成具体地理位置，填写后上报地址以此位置为准）",
                "Reason": "默认为空，stat为1时生效，填写签到理由，可为空",
                "photopath": "默认为空，填写签到图片路径"
            },
            "sleep": "默认为0，仅运行填数字，代表签到延时，单位分钟，如填1则表示延时1分钟"
        }
    ]
```

## 多用户账户配置
### 注意：多用户就是把单用户的配置文件复制粘贴一遍，但是中间用英文`,`分割
```json
"user": [
        {
            "enable": "默认填写1，改为0则停止此用户签到",
            "user": "默认为空，填写易班账号",
            "password": "默认为空，填写易班密码",
            "PhoneModel": "默认为空，填写手机型号（如不清楚用途请留空）",
            "PhoneCode": "默认为空，填写手机识别码（如不清楚用途请留空）",
            "pushplustoken": "默认为空，填写pushplus推送加token",
            "yiqiandao_name": "默认为空，填写易伴云签到模块名称（使用易伴云签到必填，否则可能出现错签）",
            "yiqiandao_uuid": "这里填易伴云的设备id，如签到时提示有设备绑定就需要填，填写方式请看https://github.com/2117516450/yiban_signin?tab=readme-ov-file#%E5%AD%97%E6%AE%B5%E8%A7%A3%E6%9E%90",
            "other": "默认为空，功能未开发，备用",
            "record_cancel": "默认为空，填1则进行销假",
            "LngLat": {
                "stat": "默认为0，填写1则使用自定义的签到位置（如不清楚用途请留空让程序自动获取）",
                "lon": "默认为空，stat为1时生效，填写经度，填写格式必须为：123.123456",
                "lat": "默认为空，stat为1时生效，填写纬度，填写格式必须为：12.123456",
                "Adders": "默认为空，填写地址（有些学校地址获取的是学校名称，此栏目可改成具体地理位置，填写后上报地址以此位置为准）",
                "Reason": "默认为空，stat为1时生效，填写签到理由，可为空",
                "photopath": "默认为空，填写签到图片路径"
            },
            "sleep": "默认为0，仅运行填数字，代表签到延时，单位分钟，如填1则表示延时1分钟"
        },
        {
            "enable": "默认填写1，改为0则停止此用户签到",
            "user": "默认为空，填写易班账号",
            "password": "默认为空，填写易班密码",
            "PhoneModel": "默认为空，填写手机型号（如不清楚用途请留空）",
            "PhoneCode": "默认为空，填写手机识别码（如不清楚用途请留空）",
            "pushplustoken": "默认为空，填写pushplus推送加token",
            "yiqiandao_name": "默认为空，填写易伴云签到模块名称（使用易伴云签到必填，否则可能出现错签）",
            "yiqiandao_uuid": "这里填易伴云的设备id，如签到时提示有设备绑定就需要填，填写方式请看https://github.com/2117516450/yiban_signin?tab=readme-ov-file#%E5%AD%97%E6%AE%B5%E8%A7%A3%E6%9E%90",
            "other": "默认为空，功能未开发，备用",
            "record_cancel": "默认为空，填1则进行销假",
            "LngLat": {
                "stat": "默认为0，填写1则使用自定义的签到位置（如不清楚用途请留空让程序自动获取）",
                "lon": "默认为空，stat为1时生效，填写经度，填写格式必须为：123.123456",
                "lat": "默认为空，stat为1时生效，填写纬度，填写格式必须为：12.123456",
                "Adders": "默认为空，填写地址（有些学校地址获取的是学校名称，此栏目可改成具体地理位置，填写后上报地址以此位置为准）",
                "Reason": "默认为空，stat为1时生效，填写签到理由，可为空",
                "photopath": "默认为空，填写签到图片路径"
            },
            "sleep": "默认为0，仅运行填数字，代表签到延时，单位分钟，如填1则表示延时1分钟"
        }
    ]
```

更多用户以此类推

## 签到位置

```json
"LngLat": {
                "stat": "默认为0，填写1则使用自定义的签到位置（如不清楚用途请留空让程序自动获取）",
                "lon": "默认为空，stat为1时生效，填写经度，填写格式必须为：123.123456",
                "lat": "默认为空，stat为1时生效，填写纬度，填写格式必须为：12.123456",
                "Adders": "默认为空，填写签到地址,如：**省**市**区**镇**学院(**校区)（有些学校地址获取的是学校名称，此栏目可改成具体地理位置，填写后上报地址以此位置为准）",
                "Reason": "默认为空，stat为1时生效，填写签到理由，可为空",
                "photopath": "默认为空，填写签到图片路径,范例如下"
                "#photopath-说明-linux": "/home/user/photo.jpg"
                "#photopath-说明-win1": "C:/home/photo.jpg"
                "#photopath-说明-win2": "C:\\home\\user\\photo.jpg"

            }

```

需要修改`lon` `lat`和`Address`

获取签到座标及地址可以参考: [坐标拾取器 | 高德地图API](https://lbs.amap.com/tools/picker)

## 字段解析

`user` 填写用户名

`password` 填写密码

易班校本化签到仅需填写上面的用户名密码，其他签到请看下面的进阶配置：

`user>enable` 是否启用此账户签到

`pushplustoken` pushplus推送加token，用于签到结果微信推送

`PhoneModel` 易班校本化的签到用手机型号（可自动获取，最好不填）

`PhoneCode` 易班校本化的签到用手机识别码（可自动获取，最好不填）

`LngLat` 里面是签到的地址参数。注意：有些自动获取能获取到经纬度但获取不到Adders（详细地址），可单独填写Adders，不用改LngLat内的其他参数

`sleep` 如果不需要抢第一或者到点就签，可以用此参数，内填阿拉伯数字，单位分钟

`record_cancel` 易班校本化销假参数，如果需要销假，此值改为1，默认销假1次，销假成功后自动变为0

以下是`易签到（易伴云、易点名）`的参数填写

`yiqiandao_name` 签到模块名称，如 2023级学生签到 
![image](https://github.com/user-attachments/assets/74c28624-dc6f-46e1-b4d3-6f9336d433a9)

`yiqiandao_uuid` 设备id，如果签到后提示签到失败，有绑定设备的情况下，就需要填写这个uuid，获取方法如下

打开易班>我的>扫一扫
![b78f285a05b0bddbcbbae43a63f7def8](https://github.com/user-attachments/assets/c1ac99fb-83a7-4244-babe-5b18fa65af14)

扫描此二维码
![435bffed915e9eb82f3d014496cc120e](https://github.com/user-attachments/assets/740f9bef-a5ed-4beb-bcb6-0133d16dfe64)

点击继续访问
![e3c02231971cb2657f11cef77c2c8e20](https://github.com/user-attachments/assets/231ec3b9-1511-43b8-8432-820620272039)

最终会打开一个页面，其中UUID：后面的就是你的设备id

填写为`"yiqiandao_uuid": "2294a0de650c12cb",`
![image](https://github.com/user-attachments/assets/800f71db-2293-4baf-9968-b99bc25bae75)

# 完整配置解析

```json
{
    "#-说明1": "修改本文件必看",
    "#-说明2": "此文件是保存用户登录信息及签到的配置文件",
    "#-说明3": "如不清楚请不要修改 LngLat 下的数据",
    "#-说明5": "除非提示经纬度获取失败,否者不要动LngLat下的数据",
    "#-说明6": "配置文件内所有符号均为英文输入法下符号,如,{}[];输入中文符号会导致配置文件读取失败",
    "#-说明7": "错误修改可能导致程序崩溃",
    "user": [
        {
            "enable": "1",
            "user": "",
            "password": "",
            "PhoneModel": "",
            "PhoneCode": "",
            "pushplustoken": "",
            "yiqiandao_name": "",
            "yiqiandao_uuid": "",
            "other": "",
            "record_cancel": "",
            "LngLat": {
                "stat": 0,
                "lon": "",
                "lat": "",
                "Adders": "",
                "Reason": "",
                "photopath": ""
            },
            "sleep": "0"
        }
    ],
    "reset": 0,
    "#reset-说明": "1为遇到签到错误自动重新运行，2为遇到所有错误都自动重新运行（包括网络错误，与'skip'冲突），0为不自动运行，自动运行有可能导致使用pushplus遭到封号",
    "skip": 0,
    "#skip-说明": "1为遇到运行错误自动跳过，2为遇到所有错误都自动跳过（包括网络错误），0为不自动跳过，使用自动跳过有可能导致漏签",
    "exit": 0,
    "#exit-说明": "1为签到完成后自动退出，0为不自动退出，自动退出方便服务器后台运行签到程序",
    "start": 0,
    "start-说明": "值为0为不开启签到延时，为其他数字则代表全局签到时间将在签到开始后1至start数值内随机延时签到",
    "threaded": 0,
    "threaded-说明": "0为不使用多线程签到，1为使用多线程签到，默认不启用，如'log'项不为OFF，则强制不使用多线程",
    "log": "OFF",
    "#log-日志说明": "OFF(关闭)|INFO(信息)|debug(调试)",
    "proxy": "",
    "#proxy-代理说明": "此处填写github代理地址，格式如：https://ghproxy.cn/",
    "#user-单用户说明": [
        {
            "enable": "1为启用账户签到，0为不启用账户签到",
            "user": "这里填用户的账号(务必填在引号内)",
            "password": "这里填用户的账户密码(务必填在引号内)",
            "PhoneModel": "这里填用户的设备编号(不填则自动获取)",
            "pushplustoken": "这里填pushplus(推送加)的token（如不使用可以不填）(务必填在引号内)",
            "yiqiandao_name": "这里填易签到的签到模块（中文）非易签到用户不填",
            "yiqiandao_uuid": "这里填易伴云的设备id，如签到时提示有设备绑定就需要填，填写方式请看https://github.com/2117516450/yiban_signin?tab=readme-ov-file#%E5%AD%97%E6%AE%B5%E8%A7%A3%E6%9E%90",
            "other": "其他易班内模块(暂未开发)",
            "record_cancel": "模块_销假（暂未开放）",
            "LngLat": {
                "stat": "为0自动获取经纬+随机计算的经纬，为1使用填写的固定经纬度,默认为0",
                "lon": "填写签到经度,如100.254877123456（保留6位小数）",
                "lat": "填写签到纬度,如20.123456（保留6位小数）",
                "Adders": "填写签到地址,如：**省**市**区**镇**学院(**校区)，如果自动获取的地址有误，可自行修改，此行有最高优先级",
                "Reason": "填写使用在范围外签到(或者图片签到)的原因（非必填）",
                "photopath": "如果需要上传图片，填写图片的完整路径，路径不要有引号，尽量使用jpg图片，范例如下：",
                "#photopath-说明": "/home/user/photo.jpg"
            },
            "sleep": "签到延时（单位分钟，只填数字）"
        }
    ],
    "#user-多用户说明": [
        {
            "enable": "1为启用账户签到，0为不启用账户签到",
            "user": "这里填用户1的账号(务必填在引号内)",
            "password": "这里填用户1的账户密码(务必填在引号内)",
            "PhoneModel": "这里填用户1的设备编号(不填则自动获取)",
            "pushplustoken": "这里填pushplus(推送加)的token（如不使用可以不填）(务必填在引号内)",
            "yiqiandao_name": "这里填易签到的签到模块（中文）非易签到用户不填",
            "yiqiandao_uuid": "这里填易伴云的设备id，如签到时提示有设备绑定就需要填，填写方式请看https://github.com/2117516450/yiban_signin?tab=readme-ov-file#%E5%AD%97%E6%AE%B5%E8%A7%A3%E6%9E%90",
            "other": "其他易班内模块(暂未开发)",
            "record_cancel": "模块_销假（暂未开放）",
            "LngLat": {
                "stat": "为0自动获取经纬+随机计算的经纬，为1使用填写的固定经纬度,默认为0",
                "lon": "填写签到经度,如100.254877123456（保留6位小数）",
                "lat": "填写签到纬度,如20.123456（保留6位小数）",
                "Adders": "填写签到地址,如：**省**市**区**镇**学院(**校区)，如果自动获取的地址有误，可自行修改，此行有最高优先级",
                "Reason": "填写使用在范围外签到(或者图片签到)的原因（非必填）",
                "photopath": "如果需要上传图片，填写图片的完整路径，路径不要有引号，尽量使用jpg图片，范例如下：",
                "#photopath-说明": "/home/user/photo.jpg"
            },
            "sleep": "签到延时（单位分钟，只填数字）"
        },
        {
            "enable": "1为启用账户签到，0为不启用账户签到",
            "user": "这里填用户2的账号",
            "password": "这里填用户2的账户密码",
            "PhoneModel": "这里填用户2的设备编号(不填则自动获取)",
            "pushplustoken": "这里填pushplus(推送加)的token（如不使用可以不填）(务必填在引号内)",
            "yiqiandao_name": "这里填易签到的签到模块（中文）非易签到用户不填",
            "other": "其他易班内模块(暂未开发)",
            "record_cancel": "模块_销假（暂未开放）",
            "LngLat": {
                "stat": "为0自动获取经纬+随机计算的经纬，为1使用填写的固定经纬度,默认为0",
                "lon": "填写签到经度,如100.123456（保留6位小数）",
                "lat": "填写签到纬度,如20.123456（保留6位小数）",
                "Adders": "填写签到地址,如：**省**市**区**镇**学院(**校区)，如果自动获取的地址有误，可自行修改，此行有最高优先级",
                "Reason": "填写使用在范围外签到(或者图片签到)的原因（非必填）",
                "photopath": "如果需要上传图片，填写图片的完整路径，路径不要有引号，尽量使用jpg图片，范例如下：",
                "#photopath-说明": "/home/user/photo.jpg"
            },
            "sleep": "签到延时（单位分钟，只填数字）"
        },
        "2用户举例，可添加更多用户,完整复制 {}, 内的内容粘贴在后面即可",
        "设备型号推荐自动获取，填写错误会导致签到失败",
        "pushplus(推送加)是集成了微信、短信、邮件、企业微信、HiFlow连接器、钉钉、飞书等渠道的信息推送平台",
        "为使用方便，强烈建议注册并填写获取到的token，可以很方便的获取签到成功状态"
    ],
    "config_version": "460"
}
```

- - -

# 特别说明
* 第一次使用如提示登录失败需要在同一网络下在手机上将易班重新登录即可
* 同一网络指：共用一个wifi、共用一条宽带
* 如过一段时间出现登录不上，签不了到的情况，请登录手机易班一次即可
* python 脚本完全开源时间待定

# 感谢名单
感谢@xiaonanbunan 提供账号密码帮助测试脚本
