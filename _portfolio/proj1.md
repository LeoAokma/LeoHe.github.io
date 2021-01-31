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

The serial contact seems worked, and the rfid cards could be read as expected.

![avatar](assets/img/portfolio/proj1/IMG_1847.JPG){:width="100%"}

The S70 type of card has uuid with 4 bytes, just the same as the campus id card.


随后我用一台老古董示波器观察了芯片之间的串口通讯。基础电路就装好啦！由于年代久远，加上当时忘记拍照，所以没有初步成型的电路照片。我们还使用了金属舵机。确认原型电路工作良好之后，我们把这个带面包板的原型部署在了门上。然后又根据门锁设计了一个502淬火的瓦楞纸壳。将舵机装进去，并且设计了一个单向传动轴，既可以电动开门也可以手动开门。找不到传动轴的照片了，不过还是可以从其他照片看到它的样子（三层瓦楞纸加上一支废旧的笔，502伺候）。

We first decided to use the chargable power banks as the power supplier. The first generation of the door gate system is literally working! (ugly as it is though)
![avatar](assets/img/portfolio/proj1/IMG_1870.JPG){:width="100%"}

The first generation costs me about a week to finish, which stills results in large electricity consumption for the power bank. What's more, the appearance is ugly and fragile and the mechanical parts are not designed carefully, leading to bad performances and bugs. 

After days of research and discussion, I worked up an 3D sketch in solidworks and printed it with my 3D printer.

![avatar](assets/img/portfolio/proj1/6.png){:width="50%"}
![avatar](assets/img/portfolio/proj1/5.png){:width="50%"}

看到成品的那一瞬间特别开心，因为组件精度和结构强度都超乎我的想象（PLA聚乳酸）。
加上之前的充电宝供电问题，我们改用了市电供电电源，这样就不用换充电宝啦！
After optimization in codes, the door gate now consumes 50% energy less than the prototype. The power is so low that the power bank would halt when the door gate is idle.

![avatar](assets/img/portfolio/proj1/IMG_1870.JPG){:width="100%"}

Then we find the servo motor is always encountering serious lack of energy when operated by the chip, which would lead to failure of door opening. 我的初步估计是面包板的电阻对VCC的5V电压不可忽略，舵机的连接入口离电源太远，导致电位降大，供电不足。将舵机电源直接接到Micro USB输入口针脚上有效的解决了这个问题。

![avatar](assets/img/portfolio/proj1/IMG_1870.JPG){:width="100%"}

The picture shows the Arduino Uno developing board, and we can see that nearly all digital ports are used.

After several practices, we found that smart devices with NFC(e.g. Apple Watch)could also be read by the door gate. So I modified the code, making it compatible for phones and watches. The door gate is much more safer than using merely keys, according to my observation. For cracking the rfid encryption is much more diffcult than simply breaking the lock.

The exposed wires gave me a sense of danger. So I decided to pack the wires up. By using rfid chips with larger power, I can completely clear the wires and the chips outside the door. 

Secondly, Arduino Uno is a demo chip for development, which would lead to higher energy consumption and less stabilities. 还有一点是我们需要缩小芯片的体积，于是我们选择了Arduino Nano Pro芯片代替，体积仅为Uno的1/6，功耗也更低，是成品芯片的不二选择。

于是买来了Nano芯片。本来想通过焊接代替暂时的杜邦线连接以增强电路稳定性，然并卵，反而体现了我的渣焊锡技术（ORZ）。

接下来要做的第一件事情是把新的主机外壳设计出来。已经经过一个月Solidworks软件探索得我，掌握了熟（lā）练（jī）的画图技巧（说出来可能要被学建筑的笑死）
