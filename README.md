## 微软聊天机器人&认知服务介绍
### Bot Framework 是微软公司所提供的简化编写对话机器人的框架，直接支持Skype、Facebook Messenger、Slack、Kik、Office 365邮件等对话渠道，可以通过Direct Line与微信公众号相连。Bot Framework SDK支持C＃与Node.js，整合了Microsoft Cognitive Services中的语义理解服务—LUIS, 帮助开发者建立更加智能的机器人。
### 微软认知服务是微软发布的一组人工智能看、听、 讲、理解、搜索的 API和SDK。微软认知服务基于微软机器学习 API, 开发人员能够很容易地在自己的服务个应用中添加这些智能模块 — — 如情感和视频检测;面部、 语音和视觉识别;语音和语言理解。我们的愿景是建立更加人性化的用户体验和更加高效的生产力应用。

## 微软对话机器人&认知服务服挑战
### 挑战一：使用BOT SDK和LUIS完成对话机器人
基于BOT SDK搭建一套可执行的对话机器人框架，链接微软认知服务自然言语理解服务LUIS,并在本地Emulator和网页Test页面展示对话。
### 挑战二：链接Q&A Maker的对话服务
使用微软认知服务来QnA Maker 结合Bot Framework，完成FAQ问题的集成。
### 挑战三：语音服务集成（Speech Service）
体验链接微软认知服务中的Speech Service中的Custom Speech以及Speaker Recognition 服务，可以集成在服务的前端或者后端 （本模块也可以单独尝试不依赖于Bot项目）
### 挑战四：集成自定义视觉服务(Custom Vision)
加入认知服务Custom Vision，完成物体识别，并使用SDK或者API集成到相应的应用程序中。
### 挑战五：使用Application Insight监测和管理Bot服务
在Bot应用中加入Application Insight对Bot服务进行监测，包括用户的数量，对话渠道，对话时间等信息。

## 参考
* 微软认知服务：https://docs.microsoft.com/zh-cn/azure/cognitive-services/welcome 
* 微软Bot Service: https://docs.microsoft.com/en-us/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-3.0 
