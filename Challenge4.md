# 挑战四：集成更多认知服务

## 背景

AdventureWorks是一家主要的户外和登山装备零售商，希望通过更多地了解消费者所穿的装备来了解消费者的行为。作为与他们的数据科学团队的联合项目，他们已经以产品目录图像的形式为您的团队提供数据以开始使用。该团队的任务是尝试使用多种机器学习方法对产品目录数据中的装备进行分类，来实现目标的第一步。

AdventureWorks最终会使用这些知识来对图片中的信息进行分类，包括来自著名的西雅图Mt. Rainier雪山在内的地点所拍摄照片中的装备。(Mt. Rainier是来自世界各地登山者的热门登山目的地)，和其他的著名户外圣地。这将为全球现有和未来的客户的需求提供更真实的测试和分析。

第二步，AdventureWorks和当地的一家提供导游服务的机构合作，帮助他们收集登山者带头盔的图片，来鼓励登山者使用头盔，确保人身安全。在实际的场景中，有些登山者会佩戴带头盔，有些人会佩戴帽子，AdventureWorks希望有一个可以定位图片中头盔的解决方案。目标检测在图片分类的基础上增加一些复杂的有效的层次，会预测事物何时出现以及在图片中的位置。模型也可以识别一张给定图片中的多个物体。

机器学习解决方案非常复杂，训练定制模型需要时间，专业知识，数据准备，持续维护和模型部署。作为一个快速开始方法，预先构建的解决方案提供了一种快速创建即用型解决方案的方法，然后再开始构建定制化的模型。

## 先决条件

* 团队有一个共享代码的环境和相应的IDE开发环境。如果使用Pyhton，请在Jupyter环境进行开发
* 请下载户外装备数据集 <a href="https://challenge.blob.core.windows.net/challengefiles/gear_images.zip" target="_blank">点击这里</a>
* 下载登山者使用头盔数据集 (用来训练和测试的图片URL集合) 本地下载 <a href="https://challenge.blob.core.windows.net/challengefiles/summit_post_urls_selected.txt" target="_blank">下载</a>
* 团队至少有1个自定义计算机视觉(Custom Vision)账户。创建<a href="https://customvision.ai" target="_blank">链接</a>。
* 选择一个调用REST API 和进行展示Client，可以是Web 页面，Mobile App，微信测试号，公众号或者Web App

## 挑战

使用团队设置和专业知识来完成以下任务。

自定义计算机视觉 (Custom Vision Service) 是一款用于构建自定义图像分类器的工具。它利用了转移学习(Transfer Learning)的优势，即现有的机器学习模型可以用来预测类似的类别。这比从头开始的培训需要更少的数据。 挑战分为两部分，第一部分是使用custom vision 进行图像分类， 第二部分是使用custom vision 提供物体检测功能进行登山人员是否佩戴头盔的识别

## 挑战第一部分：
您的挑战是创建一个分类模型，以预测图像是否是**hardshell jacket**或**insulated jacket**，并使用户外装备目录图像中冲锋衣和夹克类数据的一部分。

训练模型完成后，使用您熟悉的开发语言，比如Java，C#，JS 等调用预测rest API (Predictive endpoint) 来预测未用于训练的图像的类别。比如，您可以使用Python和Jupyter Notebook。 图像可以是来自没有上传的目录数据的图像或在线找的图像。
Rest API 的说明可以参见：<a href="https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290" target="_blank">点击这里</a>

大家也可以尝试使用Custom Vision 的SDK，但是，SDK 目前支持的部分的开发语言，请参考<a href="https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/python-tutorial" target="_blank">Python 的例子</a>

注意：Custom Vision具有易于使用的用户界面，用于上传图像，使用他们的类标记它们（例如insulated_jacket）并对模型进行培训。

**成功标准**

* 每个团队成员都可以从Web App, Mobile App, 或者Jupyter Notebook 中调用团队的Custom Vision 预测Rest API，以预测训练中未使用的户外外套(Jacket)图像的类别并显示成功的结果

## 挑战第二部分：
您的挑战是创建一个物体识别模型，以预测图像中的人物是否是佩戴头盔（helmets）和头盔的位置。比如，一些图片里面有的人带着是帽子，而非头盔，您可以尝试识别图片人物带着是帽子而非头盔。

训练模型完成后，使用您熟悉的开发语言，比如Java，C#，JS 等调用预测rest API (Predictive endpoint) 来预测未用于训练的图像里面的物体类别。比如，您可以使用Python和Jupyter Notebook。 图像可以是来自没有上传的目录数据的图像或在线找的图像。
Rest API 的说明可以参见：<a href="https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290" target="_blank">点击这里</a>

大家也可以尝试使用Custom Vision 的SDK，但是，SDK 目前支持的部分的开发语言，请参考

注意：Custom Vision具有易于使用的用户界面，用于上传图像，使用他们的类标记它们（例如insulated_jacket）并对模型进行培训。

**成功标准**

* 每个团队成员都可以从Web App, Mobile App, 或者Jupyter Notebook 中调用团队的Custom Vision 预测Rest API，以预测训练中未使用的户外外套(Jacket)图像的类别并显示成功的结果

## 参考

**请先了解下面知识**

* 机器学习入门 <a href="https://youtu.be/k-K3g4FKS_c" target="_blank">视频</a>
* 一些常见机器学习术语的定义 <a href="https://docs.microsoft.com/azure/machine-learning/studio/what-is-machine-learning#key-machine-learning-terms-and-concepts?wt.mc_id=OH-ML-ComputerVision" target="_blank">参考</a>
* 分类描述 <a href="https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-the-5-questions-data-science-answers?wt.mc_id=OH-ML-ComputerVision#question-1-is-this-a-or-b-uses-classification-algorithms" target="_blank">参考</a>
* 机器学习过程概述图 <a href="https://blogs.msdn.microsoft.com/continuous_learning/2014/11/15/end-to-end-predictive-model-in-azureml-using-linear-regression/" target="_blank">文档</a>
* 什么是目标检测？ <a href="https://tryolabs.com/blog/2017/08/30/object-detection-an-overview-in-the-age-of-deep-learning/" target="_blank">参考</a>
* 什么是mAP？ <a href="http://fastml.com/what-you-wanted-to-know-about-mean-average-precision/" target="_blank">参考</a>

**自定义计算机视觉服务 (Custom Vision Service)**

* 自定义计算机视觉服务 (Custom Vision Service) <a href="https://customvision.ai" target="_blank">参考</a>
* 自定义计算机视觉服务(Custom Vision Service) 文档 <a href="https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home?wt.mc_id=OH-ML-ComputerVision" target="_blank">链接</a>
* 自定义计算机视觉(Custom Vision) Python SDK (Linux) <a href="https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/python-tutorial?wt.mc_id=OH-ML-ComputerVision" target="_blank">链接</a>

**调用预测API**

* Requests是进行API调用的最流行的Python库之一，请点击 <a href="http://docs.python-requests.org/en/master/" target="_blank">参考</a> 同时见 <a href="https://github.com/michhar/python-jupyter-notebooks/blob/master/cognitive_services/Computer_Vision_API.ipynb" target="_blank">示例代码</a>
* 或者您也可以参考Custom Vision Service提供的一个用Python `urllib` library 和 Python 不同版本调用服务的例子- <a href="https://southcentralus.dev.cognitive.microsoft.com/docs/services/57982f59b5964e36841e22dfbfe78fc1/operations/5a3044f608fa5e06b890f164" target="_blank">文档</a>

