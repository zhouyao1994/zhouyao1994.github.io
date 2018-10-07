---
layout: post
---

# TensorFlow TPU 实战

## 准备步骤

* 也许你在这篇博客了解[深度学习的应用](https://www.youtube.com/watch?v=mWl45NkFBOc&list=PLOU2XLYxmsIKGc_NBoIhTn2Qhraji53cv),之后你从这个[视频](https://www.youtube.com/watch?v=zEOtG-ChmZE),中了解到了TPU,被它强大的性能所吸引.在[这篇博客](https://blog.riseml.com/benchmarking-googles-new-tpuv2-121c03b71384)里对TPU和英伟达的GPU性价比做了对比得出的结论是:通NVIDIA的GPU相比同样的计算任务TPU只需要你花费一半的费用,详细的[测试过程](https://blog.riseml.com/comparing-google-tpuv2-against-nvidia-v100-on-resnet-50-c2bbb6a51e5e)你可以在这篇文章中找到,经过这番了解,你对TPU产生了兴趣,想要真正的去尝试一下使用它

* 首先,你需要能保证网络通畅,能够在网页访问google cloud网站,并且有一个google账户,同时开通GCP (google compute platform),如果你在注册的时候能够绑定一张信用卡,就能获得100美元的免费代金券,有效期一年,用来试用用google的云计算工具,你能够在[这篇文章]()找到详细的教程
* 在google的[这篇文档]()中你能找到step by step 试用tpu的步骤,这份文档,使用的是MNIST数据集,用来进行手写体识别,当你按流程走完,之后,你会发现一个有趣的现象是:TPU运算的过程是:首先,从storage bulket(存储通,类似s3服务)中读取数据,之后,再通过cpu运算送入TPU运算.TPU并不能从你的主机里面读取你的数据,

## 调优步骤

* 在tensorflow dev summit 的[一份YouTube演讲中](https://youtu.be/SxOsJPaxHME?list=PLQY2H8rRoyvxjVx3zfw4vA4cvlKogyLNN) 有提到 让TPU跑的更快,这是由于TPU性能太强了,以致于发现绝大多数TPU出现性能慢的时候,都是由数据输入的速率跟不上TPU的计算能力造成的.通过一些简单的参数设置,能让你的TPU处理图片的速度从最初的150张image/s 到后来的600image/s再后来的1350image/s,最后速度能够达到2300image/s性能提升了15倍,这意味着,以前你需要使用7个小时才能训练完的数据,现在你半个小时就可以完成了
* 你应该觉得很震撼.于是你在这份演讲附带的链接中,找到了这次profile的[性能文件](http://download.tensorflow.org/dev_summit_2018/cloud_tpu_traces.tgz)在解压缩之后,你就可以用`tensorbord --logdir 1-simple`命令打开这份文件中的案例,可视化以下运行的过程.你可以好奇的左边点点,右边点点,看看这个工具都有哪些选项.如果你不知道怎么使用tensorboard,你可以在[这个文档中](https://www.tensorflow.org/guide/summaries_and_tensorboard)找到教程,在[这个视频](https://www.youtube.com/watch?v=eBbEDRsCmv4)中你能得到直观的了解,[这个视频](https://www.youtube.com/watch?v=XcHWLsVmHvk&list=PLQY2H8rRoyvxjVx3zfw4vA4cvlKogyLNN&index=12)让你得到更高级的了解
* 如果你按照上面的MNIST教程走过一篇,当你使用ctpu命令运行的时候,你会观察到,ctpu命令,起了一个250G的磁盘(待补充),一个配置很高的 VM 主机,你可能想能不能起一个配置低一点的VM这样能够减少你的花销.[这份文档](https://cloud.google.com/tpu/docs/custom-setup)能够给你一个自定义定制 VM 的 step by step 的教程
* 完成这样的实验教程之后,你会觉得在实验过程中,由于国内网速的原因,使用网页端的ssh速度慢,实在是不痛快,你想优化这个过程,然后你又了解到 gcloud 这个工具,能够使用命令行创建一个VM实例,TPU实例,GS实例,从而能够避免你一次次使用网页创建示例,由于网络的原因使用网页创建实例体验实在是不好,gcloud这个工具的出现你觉得真的是很有用.而且这个工具是可以在本地运行的,恰好你在Ubuntu桌面上而[这份文档](https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu)告诉你如何安装gcloud
* 当你按照文档安装完gcloud的时候返现, initialize SDK 的时候,出现了问题.这是由于国内网络环境,无法访问google导致你需要用到 proxy 工具,[这里](https://cloud.google.com/sdk/docs/proxy-settings)有你配置 proxy 的文档,在配置的时候,建议使用 http 代理,原因是google的 gsutil 工具,目前只支持 http 爱丽, 你可以在这个[地址](https://github.com/chuyik/some_good_stuff/issues/7)找到 将 ss 转 http 的方法,处理完成后,记得重新启动 Chrome 浏览器
* 完成上面的配置,你已经可以脱离网页工具了,完全使用bash就可以做完实验了,等等,别忘了,你本次实验是为了体会TPU的性能的,你需要用到TPU的profile工具,来判断,TPU的性能是否被最大化利用,你能够在[这个profile配置文件](https://cloud.google.com/tpu/docs/cloud-tpu-tools#profile_tab)找到profile工具中各个选项详细的意义
* 当你完成这些之后,你希望在你以后使用tensorflow的过程中,能尽可能的充分利用它的效率,这个[调优文档](https://www.tensorflow.org/performance/datasets_performance)能给你带来一些有用的建议
* 一个[小优化](https://medium.com/tensorflow/introducing-the-model-optimization-toolkit-for-tensorflow-254aca1ba0a3?linkId=57036398),使得体积小4倍,运行速度快2倍,原因是把32位的数据,用8位表示,以及其他的一些优化.

## 官方tweeter推荐的资料

* [tensorflow-without-a-phd](https://github.com/GoogleCloudPlatform/tensorflow-without-a-phd)
* 编程习惯
  1. 用`print()` 将常用的信息print出来

## debug工具TensorBoard

* 在[这个视频中](https://youtu.be/XcHWLsVmHvk?list=PLQY2H8rRoyvxjVx3zfw4vA4cvlKogyLNN)有tensorfboard 可视化的Debug工具,这个[文档中](https://github.com/tensorflow/tensorboard/blob/master/tensorboard/plugins/debugger/README.md)有介绍