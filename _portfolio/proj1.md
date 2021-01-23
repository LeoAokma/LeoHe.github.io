---
title: DIY:3D Printed RFID Doorgate
subtitle: subtitle lorem ipsum dolor sit amet consectetur.
image: assets/img/portfolio/proj1/IMG_1853.bmp
alt: Shirts on a hanger

caption:
  title: DIY:3D Printed RFID Doorgate(2018)
  subtitle: A DIY project mixed with elctronics, programming and model designing.
  thumbnail: assets/img/portfolio/proj1/5.png
---
我拿出了尘封多年的芯片，找到了MFRC-522模组，查阅了一下Documentation之后简单接了一下线，码了几十行代码，接上Arduino。

![avatar](assets/img/portfolio/proj1/IMG_1847.JPG){:width="100%"}

串口通讯也正常，并且可以读卡了

![avatar](assets/img/portfolio/proj1/IMG_1847.JPG){:width="100%"}

S70型号的卡是四个Byte的，和我们的校园卡一样


随后我用一台老古董示波器观察了芯片之间的串口通讯。基础电路就装好啦！由于年代久远，加上当时忘记拍照，所以没有初步成型的电路照片。我们还使用了金属舵机。确认原型电路工作良好之后，我们把这个带面包板的原型部署在了门上。然后又根据门锁设计了一个502淬火的瓦楞纸壳。将舵机装进去，并且设计了一个单向传动轴，既可以电动开门也可以手动开门。找不到传动轴的照片了，不过还是可以从其他照片看到它的样子（三层瓦楞纸加上一支废旧的笔，502伺候）。

我们决定采用充电宝供电（因为桌上有10个充电宝跃跃欲试），于是第一代门禁系统就开始工作啦（实在是太丑了，再度吐槽）。

![avatar](assets/img/portfolio/proj1/IMG_1870.JPG){:width="100%"}

第一代门禁工作了大概一个星期，耗电量还挺大的，加上外观丑陋、机械强度低、门锁轴和舵机轴共轴性差，门禁经常发生一些令人窒息的bug，比如开门之后没有响应，这些bug其实挺好笑的我都不舍得删，但是在舍友的威(xiào)胁(shēng)下，我还是把它们改了。

为了迫切解决以上问题，我一边有空就看看代码补充一些功能，并且找到降低功耗的办法，一边设计新的门锁

于是经过一个星期的讨论，我们总算有了成品的初稿，我用SolidWorks画了每个零件的图纸，组装成了装配体，随后3D打印出成品

![avatar](assets/img/portfolio/proj1/6.png){:width="50%"}
![avatar](assets/img/portfolio/proj1/5.png){:width="50%"}


看到成品的那一瞬间特别开心，因为组件精度和结构强度都超乎我的想象（PLA聚乳酸）。
加上之前的充电宝供电问题，我们改用了市电供电电源，这样就不用换充电宝啦！
然后经过代码的改进，整个系统的功耗减小到原来的50%，现在的功率已经低到充电宝都会自动停电。

![avatar](assets/img/portfolio/proj1/IMG_1870.JPG){:width="100%"}

令人窒息的是，改用了独立供电后门禁出现了令人窒息的bug，一刷卡门只开一半，然后蜂鸣器又开始唱歌，舵机也开始跳舞。。。花了两个月折腾的门禁秒变门铃

经过对比实验，我发现当舵机断电时程序不会出错，也就是意味着舵机这个部分的硬件连接有问题。分别尝试了功率更小的电机和相同型号没有负载的电机，均可正常运行。根据以上实验结果，我们可以判断出是供电出了问题。我的初步估计是面包板的电阻对VCC的5V电压不可忽略，舵机的连接入口离电源太远，导致电位降大，供电不足。将舵机电源直接接到Micro USB输入口针脚上有效的解决了这个问题。

![avatar](assets/img/portfolio/proj1/IMG_1870.JPG){:width="100%"}

图示为Arduino Uno开发板，可以看到几乎所有的数字引脚都被占用。
After several practices, we found that smart devices with NFC(e.g. Apple Watch)could also be read by the door gate. 于是我们进一步修改代码，使得可以利用手机和手表开门。
当然这个门禁的安全性是非常高的（至少比钥匙开锁要高几倍，也就是说与其破解这个电子门锁，不如暴力踹开门或者撬锁emmmm）

首先，鉴于把读卡器放在外面显得很突兀，而且会看到线，给人一种不安全感，也降低了稳定性，我决定更换功率更大的射频板，放在屋内读取卡片。令人意外的是，即使新的射频卡片功耗是原来卡片的一倍，我们的总功耗仅仅是略微上升，这得益于之前写的的功耗控制算法。

其次，Arduino Uno仅仅只能作为一个调试代码和调试原型机的一个芯片，很多模块都高度集成，一方面提供了调试的便利性，但另一方面使得功耗比单纯的MCU+ADC+WDT+晶振等核心模块直接组装起来的Mega328P芯片组的功耗要大许多。还有一点是我们需要缩小芯片的体积，于是我们选择了Arduino Nano Pro芯片代替，体积仅为Uno的1/6，功耗也更低，是成品芯片的不二选择。

于是买来了Nano芯片。本来想通过焊接代替暂时的杜邦线连接以增强电路稳定性，然并卵，反而体现了我的渣焊锡技术（ORZ）。既然第一个Nano板子已经焊上了，也只能硬着头皮继续做了。
接下来要做的第一件事情是把新的主机外壳设计出来。已经经过一个月Solidworks软件探索得我，掌握了熟（lā）练（jī）的画图技巧（说出来可能要被学建筑的笑死）

