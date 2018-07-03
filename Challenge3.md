# 挑战二：语音服务集成

## 背景

在微软认知服务的Speech服务里，除了提供了传统的Speech to Text 和 Text To Speech，还提供了一个定制化的STT 和 TTS 服务 （Custom Speech 和 Custom Voice)，同时，说话人识别（Speaker Recognition）还可以让您进行说话人的识别和验证。在这个挑战里，您将会尝试使用Custom Speech 根据您训练数据和场景，实现一个您自己的定制化STT 模型。 然后，尝试使用说话人识别 - Speaker Recognition 进行说话人的验证和尝试

## 先决条件

* 团队有一个共享代码的环境和相应的IDE开发环境。如果使用Pyhton，请在Jupyter环境进行开发
* 请先体验一下Speech Service 的Demo <a href="https://azure.microsoft.com/zh-cn/services/cognitive-services/directory/speech/" target="_blank">点击这里</a>
* 团队至少有1个Speech Service账户。创建<a href="https://azure.microsoft.com/zh-cn/try/cognitive-services/my-apis/?api=speech-services" target="_blank">链接</a>。
* 选择一个调用REST API 和进行展示Client，可以是Web 页面，Mobile App，微信测试号，公众号或者Web App
* 为定制化语音服务（Custom Speech Service） 准备训练数据Dataset，比如Acoustic （Audio File），Language，Pronuciation。关于Custom Speech 训练用Dataset 可以参考<a href="https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/how-to-customize-speech-models" target="_blank">点击这里</a>

## 挑战

使用团队设置和专业知识来完成以下任务：

微软认知服务里的语音服务（Speech Service）提供了丰富的Speech 服务，这里有两个非常有用的服务希望大家在这里进行尝试。 第一个是训练和使用您自己的自定义语音服务 (Custom Speech Service)，第二部分是使用说话人识别（Speaker Recognition）来去对说话人进行识别和验证

## 挑战第一部分：
您的挑战是创建一个定制化的语音服务(<a href="https://cris.ai/Home/CustomSpeechCustom" target="_blank"> Custom Speech Service</a>)，以识别特定的词语，发音方式或者声音环境和习惯。首先，选择要支持的语言，建议尝试英语和中文。参考<a href="https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/how-to-customize-speech-models" target="_blank">如何创建自定义语音模型</a> 

请先定义您的识别场景和特殊词汇，比如，我们会发现通用的语音识别服务识别特殊词汇 - "WeLink" 会识别成"We Link" 或者"Willing", 那么用户说 "Hello WeLink"， 就会识别成 "Hello Waiting" 或者 "Hello Willing" 等。 如果是中文就会是"华为威廉" 而不是"华为微联"。 那么下面我们就可以用Custom Speech 根据您定义的训练数据集进行特殊的Speech 模型的训练。 

训练模型完成和测试后，发布custom endpoint (Rest API URL). 然后，使用您熟悉的开发语言，比如Java，C#，JS 等调用预测rest API (Predictive endpoint)来对不同的语音进行识别。同时，您也可以使用Speech SDK。 使用Custom Speech Endpoint 和标准的Speech Service REST API 和 SDK基本一样，只是需要替换标准Speech Endpoint。在SDK里面，除了YourSubscriptionKey 和YourServiceRegion，还需要将YourDeploymentId 填入到SDK中。请参考<a href="https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/rest-apis#speech-to-text" target="_blank"> REST API</a> 和 <a href="https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-sdk" target="_blank"> Speech SDK</a>  

关于训练数据的准备，可以参考 <a href="https://github.com/Microsoft/Cognitive-Custom-Speech-Service" target="_blank">custom speech 训练数据准备示例</a>

**成功标准**
* 每个团队成员都可以从Web App, Mobile App, 或者Windows App 中调用团队的Custom Speech Endpoint, 看看是否能是否特殊词汇，强调等，然后，也使用标准的Speech Service Endpoint 识别同样一段话，看看结果是否有区别。这个有个Windows App 可以参考，请下载编译 <a href="https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/Windows/csharp_samples" target="_blank">Speech Service Windows app demo</a>

在函数 RecognitionUsingCustomizedModelAsync， 请将Custom Speech 里的Subscription key 和 DeploymentId 输入在函数里。

## 挑战第二部分：
语音具有独特的特征，可以用来识别一个人，就像指纹一样。将语音用作访问控制和身份验证场景的信号已经成为一种新型创新工具 - 基本上提供了安全级​​别，简化了客户的身份验证体验。这个挑战的部分，需要大家使用说话人识别辨识各个说话人，或将语音用作身份验证。

**成功标准**
1. 说话人识别 - 在给定一组说话人的情况下，自动辨识出谁是正在说话的人。

* 完成注册
  说话人识别的注册是独立于文本的，这意味着对于说话者在音频中说什么没有限制。讲话者的声音被录制，并且提取许多特征以形成独特的声音签名。

* 识别讲话人的身份 
  Speaker Recognition API可以自动识别在一个音频文件中说话的人，给定一组潜在的扬声器。输入音频与提供的扬声器组配对，并且在找到匹配的情况下，返回扬声器的身份

  在识别期间提供未知说话者的音频以及未来的说话者组。将输入语音与所有发言者进行比较，以确定其发音是谁，并且如果找到匹配，则返回发言者的身份。

2. 说话人验证 - 根据说话人的声音或语音，自动验证和核实用户身份。

* 完成注册 
  说话人验证的注册是依赖于文本的，这意味着发言人需要选择在注册和验证阶段使用的特定密码短语。

  在注册时，讲话者的声音被记录为表示特定的短语，然后提取许多特征并识别所选择的短语。在一起，提取的特征和选择的短语形成独特的语音签名。

* 演讲者验证

  在验证过程中，将输入的语音和短语与注册的语音签名和短语进行比较 - 以验证它们是否来自同一个人，以及他们是否说出正确的短语。

## 参考

**自定义语音识别服务 (Custom Speech Service)**

* 自定义语音识别服务 (Custom Speech Service) <a href="https://cris.ai/" target="_blank">Portal</a>
* 自定义语音识别服务 (Custom Speech Service)文档 <a href="https://docs.microsoft.com/zh-cn/azure/cognitive-services/speech-service/how-to-customize-speech-models" target="_blank">链接</a>
* 自定义语音识别服务(Custom Speech Service) Windows App 例子 <a href="https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/Windows/csharp_samples" target="_blank">链接</a>