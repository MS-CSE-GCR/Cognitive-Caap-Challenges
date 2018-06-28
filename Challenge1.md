# 挑战 1: 使用BOT SDK和LUIS完成对话机器人
## 背景介绍

在开始研究BOT和认知服务之前，请确保您的Azure帐号和所使用的开发环境支持相应的开发。本例以查询航班为例，使用LUIS完成对航空公司的航班查询语句的解析，同时航班飞行受到天气情况紧密相关，我们同时需要做一个天气查询的问答。

## 挑战

对话机器人和认知服务挑战需要的开发环境:

*	Global Azure 订阅
* LUIS(Language understading intelligence service)帐号 (与Azure订阅帐号保持一致即可)
* Skype 账号和客户端（免费申请）
*	C# 或者 Node.js 的开发工具(对于基于Bot Build的开发二选一即可，后面的认知服务没有此限制)

### 使用LUIS创建一个查询航班的语义理解模型

* 登陆 luis.ai 操作界面
    * 创建一个航班&天气查询的APP
    * 使用Intent, Entity, Phrase List 等功能实现基本功能
    * 尝试Pattern，不同Entity类型（Composite，hierarchical 等）
    * 使用Test 页面进行测试
    * 发布URL测试，集成Azure订阅Key
  参考 [这里](#luis)


### 创建一个Bot对话机器人程序，同时集成LUIS实现天气查询的功能


* 使用Bot Service在线创建
    * 创建包含LUIS的Bot服务集成上一部做好的LUIS App，
    * 从互联网上的天气API，使用LUIS的识别结果作为参数，来获取天气数据
    * 使用Test 页面进行测试
    * 发布Skype应用，在SKype中完成对话
  参考 [这里](#bot)

* 使用Bot SDK在本地创建
    * 创建包含LUIS的Bot服务集成上一部做好的LUIS App，
    * 从互联网上的天气API，使用LUIS的识别结果作为参数，来获取天气数据
    * 使用Emulator进行测试
    * 创建Azure App Service， 并将本地的应用程序发布到Azure App Service
    * 在Azure上创建 Bot Channel Service，将发布的App Serivce的bot程序关联到Bot Channel Service上
    * 发布Skype应用，在Skype中完成对话
  参考 [这里](#bot)

## 成功标准

* LUIS模块，使用URL测试，包含下面的两个命令，并输出要求识别结果
* Bot模块，使用Skype(或Test in Web)完成演示全国任意主要城市天气查询

**LUIS 命令**

* 今天(城市名)天气怎么样？

要求识别出：意图，Entity城市名

* 帮我订一张从（城市名）到（城市名）明天下午的机票

要求识别出：意图，Entity城市名，Entity时间

(城市名要求涵盖全国主要省会级城市)



## Reference

### Azure 订阅

* Azure 登陆页面 <a href="https://portal.azure.com" target="_blank">链接</a>

### Luis
* LUIS官网 <a href="https://www.luis.ai/home" target="_blank">链接</a>
* LUIS App创建及相关文档 <a href="https://docs.microsoft.com/en-us/azure/cognitive-services/LUIS/create-new-app" target="_blank">链接</a>


### Bot

* Bot Service <a href="https://docs.microsoft.com/en-us/azure/bot-service/bot-service-quickstart?view=azure-bot-service-3.0" target="_blank">在线创建Bot Servie</a>
* Bot SDK 本地创建 <a href="https://docs.microsoft.com/en-us/azure/bot-service/dotnet/bot-builder-dotnet-quickstart?view=azure-bot-service-3.0" target="_blank">使用C# SDK</a>
* Bot SDK 本地创建 <a href="https://docs.microsoft.com/en-us/azure/bot-service/nodejs/bot-builder-nodejs-quickstart?view=azure-bot-service-3.0" target="_blank">使用Node.JS SDK</a>
* Bot Builder Sample Code for LUIS integration <a href="https://github.com/Microsoft/BotBuilder-Samples" target="_blank">示例代码</a>

