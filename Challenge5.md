# 挑战 - 监视 Node.js Web 应用程序

## 背景介绍
Azure Application Insights，可轻松监视 Web
应用程序的可用性、性能和使用情况。 还可以快速确定并诊断应用程序中的错误，而无需等待用户报告这些错误。 

### 挑战需要的开发环境:

完成本挑战：

*   需要 Azure 订阅和现有 Node.js Web 应用程序。

如果没有 Node.js Web 应用程序，则可以按照[创建 Node.js Web
应用快速入门](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-nodejs)创建一个。

如果你还没有 Azure
订阅，可以在开始前创建一个[免费](https://azure.microsoft.com/free/)帐户。

登录到 [Azure 门户](https://portal.azure.com/)。

1. 启用 Application Insights

Application Insights 可以从任何连接 Internet
的应用程序收集遥测数据，而不考虑它是在本地运行还是在云中运行。 

>   添加 Application Insights 资源

2.  配置 App Insights SDK

3.  将 Node.js 的 Application Insights SDK
    添加到应用程序。 从应用的根文件夹运行：

**备注**

这需要 3-5
分钟，然后数据才开始显示在门户中。 如果此应用是一个低流量测试应用，请记住，仅当存在活动请求或正在执行的操作时，才会捕获大多数指标。

4. 开始在 Azure 门户中监视 ，查看有关当前正在运行的应用程序的详细信息。

5.  单击“应用映射”以获取应用程序组件之间依赖关系的可视布局。 每个组件均显示
    KPI，如负载、性能、失败和警报。

>   应用程序地图

6.  打开“Application Insights Analytics”，将生成以图表形式呈现请求计数的查询，编写自己的查询来分析其他数据。

7.  “运行状况概述时间线”

>   启用“页面视图加载时间”图表以填充“客户端遥测”数据，请将此脚本添加到要跟踪的每一页：

>   HTML复制

>   \<!--

>   To collect end-user usage analytics about your application,

>   insert the following script into each page you want to track.

>   Place this code immediately before the closing \</head\> tag,

>   and before any other scripts. Your first data will appear

>   automatically in just a few seconds.

>   \--\>

>   \<script type="text/javascript"\>

>   var appInsights=window.appInsights\|\|function(config){

>   function i(config){t[config]=function(){var
>   i=arguments;t.queue.push(function(){t[config].apply(t,i)})}}var
>   t={config:config},u=document,e=window,o="script",s="AuthenticatedUserContext",h="start",c="stop",l="Track",a=l+"Event",v=l+"Page",y=u.createElement(o),r,f;y.src=config.url\|\|"https://az416426.vo.msecnd.net/scripts/a/ai.0.js";u.getElementsByTagName(o)[0].parentNode.appendChild(y);try{t.cookie=u.cookie}catch(p){}for(t.queue=[],t.version="1.0",r=["Event","Exception","Metric","PageView","Trace","Dependency"];r.length;)i("track"+r.pop());return
>   i("set"+s),i("clear"+s),i(h+a),i(c+a),i(h+v),i(c+v),i("flush"),config.disableExceptionTracking\|\|(r="onerror",i("_"+r),f=e[r],e[r]=function(config,i,u,e,o){var
>   s=f\&&f(config,i,u,e,o);return s!==!0&&t["_"+r](config,i,u,e,o),s}),t

>   }({

>   instrumentationKey:"\<insert instrumentation key\>"

>   });

>   window.appInsights=appInsights;

>   appInsights.trackPageView();

>   \</script\>

# 将LUIS结果添加到Application Insight

本挑战将LUIS请求和响应信息添加到*Application
Insight*遥测数据存储。一旦你有了这些数据, 你可以用 Kusto 的语言来查询它,
或者PowerBi实时地分析、汇总和报告意图以及话语的实体。此分析可帮助您确定是否应添加或编辑LUIS应用程序的意图和实体。

## 成功标准:

-   将应Application Insight添加到 web app bot 中

-   捕获并发送LUIS查询结果以Application Insight

-   查询应用程序对最高意图、分数和话语的洞察力

本挑战中的所有代码都可在*LUIS-samples github存储
库*与本教程相关的每一行都被注释为APPINSIGHT:

# 将Application Insight添加到 web app bot 中

目前, Application Insight, 使用在这个 web app bot, 收集通用的状态遥测为
bot。它不收集*LUIS*请求和响应信息, 您需要检查和修复您的意图和实体。

为了捕获LUIS的请求和响应, web app bot 需要**Application Insight**安装和配置的
NPM 包**app.js**文件。然后,
意向对话处理程序需要将LUIS请求和响应信息发送到Application Insight。

1.  在 Azure 门户中, 在 web app bot 服务中, 选择**建立**下的**Bot 管理**部分。

>   搜索应用程序洞察力

2.  使用应用程序服务编辑器打开一个新的浏览器选项卡。在顶部栏中选择应用程序名称,
    然后选择**打开羚控制台**.

>   搜索应用程序洞察力

3.  在控制台中, 安装Application Insight和下划线包:

>   cd 站点 \\wwwroot&&Npm安装applicationinsights&&Npm安装下划线

![](https://docs.microsoft.com/en-us/azure/cognitive-services/luis/media/luis-tutorial-appinsights/npm-install.png)

>   搜索应用程序洞察力

>   等待要安装的软件包:

``` javascript

luisbot\@1.0.0 D:\\home\\site\\wwwroot

\`-- applicationinsights\@1.0.1

\+-- diagnostic-channel\@0.2.0

\+-- diagnostic-channel-publishers\@0.2.1

\`-- zone.js\@0.7.6

npm WARN luisbot\@1.0.0 No repository field.

luisbot\@1.0.0 D:\\home\\site\\wwwroot

\+-- botbuilder-azure\@3.0.4

\| \`-- azure-storage\@1.4.0

\| \`-- underscore\@1.4.4

\`-- underscore\@1.8.3

```

* 捕获并发送LUIS查询结果Application Insight

1.  在 "应用程序服务编辑器浏览器" 选项卡中, 打开**app.js**文件。

2.  将下列 NPM 库添加到现有的需要线：

```javascript

>   // APPINSIGHT: Add underscore for flattening to name/value pairs

>   var \_ = require("underscore");

>   // APPINSIGHT: Add NPM package applicaitoninsights

>   let appInsights = require("applicationinsights");

```

3.  创建Application Insight对象并使用 web app bot
    应用程序设置**BotDevInsightsKey**:

```javascript

>   // APPINSIGHT: Set up ApplicationInsights with Web App Bot settings
>   "BotDevAppInsightsKey"

>   appInsights.setup(process.env.BotDevAppInsightsKey)

>   .setAutoDependencyCorrelation(true)

>   .setAutoCollectRequests(true)

>   .setAutoCollectPerformance(true)

>   .setAutoCollectExceptions(true)

>   .setAutoCollectDependencies(true)

>   .setAutoCollectConsole(true,true)

>   .setUseDiskRetryCaching(true)

>   .start();

>   // APPINSIGHT: Get client

>   let appInsightsClient = appInsights.defaultClient;

```

4.  添加 "**appInsightsLog**功能：

```javascript

>   // APPINSIGHT: Log LUIS results to Application Insights

>   // APPINSIGHT: must flatten as name/value pairs

>   var appInsightsLog = function(session,args) {

>   // APPINSIGHT: put bot session and LUIS results into single object

>   var data = Object.assign({}, session.message,args);

>   // APPINSIGHT: ApplicationInsights Trace

>   console.log(data);

>   // APPINSIGHT: Flatten data into name/value pairs

>   flatten = function(x, result, prefix) {

>   if(_.isObject(x)) {

>   \_.each(x, function(v, k) {

>   flatten(v, result, prefix ? prefix + '_' + k : k)

>   })

>   } else {

>   result["LUIS_" + prefix] = x

>   }

>   return result;

>   }

>   // APPINSIGHT: call fn to flatten data

>   var flattenedData = flatten(data, {})

>   // APPINSIGHT: send data to Application Insights

>   appInsightsClient.trackEvent({name: "LUIS-results", properties:
>   flattenedData});

>   }

```
>   函数的最后一行是将数据添加到Application
>   Insight中的位置。该事件的名称是**LUIS-Results**, 一个唯一的名称,
>   除了任何其他遥测数据收集此 web app bot。

5.  使用该**appInsightsLog**功能。将其添加到每个意向对话框中:

```javascript

>   // APPINSIGHT: Log results to Application Insights

>   appInsightsLog(session,args);

```
# 在Application Insight查看LUIS条目

>   分析查询窗口

1.  要拉出最高意图、分数和话语


