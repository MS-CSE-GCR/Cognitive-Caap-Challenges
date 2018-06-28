# 挑战 2：链接Q&A Maker的对话服务
## 背景介绍

在完成挑战一的bot框架和LUIS之后，客户希将一些FAQ的问答输入Bot，让Bot能够直接回答用户一些常见问题。在微软的认知服务中，QnA Maker API提供了基于FAQ语料库问答调用，请帮助该客户使用QnA Maker集成到现有Bot中，满足业务的需求。
## 挑战

### 集成认知服务QnA Maker需要的开发环境:

*	Global Azure 订阅
* (可选) 使用API创建和维护知识库，准备开发语言（C#/Go/Java/Node.js/Python）所需IDE


### 使用 QnA Maker Portal 创建一个FAQ的问答知识库

* 登陆 qnamaker.ai 操作界面
    * 在Azure上创建一个QnA Maker的服务
    * 使用URL或者本地文件的形式导入知识库（Knowleadge Base）
    * 使用Test 页面进行测试
    * 发布
    * 将QnA Maker 服务集成到bot中（挑战一使用的bot）
  参考 [这里](#qnamaker.ai)


### （可选）使用API编程的方式创建一个FAQ的问答知识库


* 使用API通过代码创建
    * 在Azure上创建一个QnA Maker的服务
    * 使用API导入知识库（Knowleadge Base）
    * 使用API更新知识库
    * 发布
  参考 [这里](#qnamaker_api)


## 成功标准

* 展示所使用的知识库并可以在bot中提问FAQ相应问题。


## Reference

### Azure 订阅

* Azure 登陆页面 <a href="https://portal.azure.com" target="_blank">链接</a>

### qnamaker.ai
* QnA Maker 官网 <a href="https://www.qnamaker.ai/" target="_blank">链接</a>
* Azure QnA Maker Service <a href="https://docs.microsoft.com/en-us/azure/cognitive-services/qnamaker/how-to/set-up-qnamaker-service-azure" target="_blank">如何在Azure创建QnA Maker </a>

### qnamaker api
* 通过 API 创建 <a href="https://docs.microsoft.com/en-us/azure/cognitive-services/qnamaker/quickstarts/create-new-kb-csharp" target="_blank">使用C# </a>
* 通过 API 创建 <a href="https://docs.microsoft.com/en-us/azure/cognitive-services/qnamaker/quickstarts/create-new-kb-nodejs" target="_blank">使用Node.JS </a>
* <a href="https://docs.microsoft.com/en-us/azure/cognitive-services/qnamaker/overview/languages-supported" target="_blank">支持语言</a>

