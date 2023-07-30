# Linux命令快速上手（0）--关于Linux
### 什么是Linux？为什么会出现Linux？

>叠甲：Linux史这一部分内容争议较多，并且没有十分清晰的记载。三十年的老烂账了，Linus Torvalds都还不一定记得。

在上世纪70年代，**Unix**系统以及各种**类Unix系统**开始崛起。尽管这些系统有着强大的功能以及较强的易用性，但是他们是非开放的，由于知识产权原因，其使用会受到大量的限制。于是，**Linus Torvalds**在1991年编写了Linux内核以替代MINIX这一类Unix系统的内核，并在此之上运行用于MINIX的软件。然而，这样的作法依然会受到限制--这会使得Linux无法应用于商业用途。而从1984年就已经立项的**GNU**项目，本**自由软件**的精神，开发了一系列兼容Unix内核的软件--在今天，GNU包括了其特有的Shell、Gnome桌面环境、gcc编译器等应用，这些应用对于程序的运行都是十分重要的--却缺乏一个合适的内核。因此，Linus Torvalds和GNU之父Richard Matthew Stallman一拍即合，修改了Linux的使用协议，让Linux内核改用GNU软件。尽管一开始的Linux内核并不完善，但是在庞大的社区支持下，Linux不断更新迭代，同时，不同的公司/组织/个人也在发行各类装有不同特色应用的Linux**发行版（Distrobution）**，使得Linux得到了广泛的应用。

>实际上，GNU项目中的《GNU通用公共许可协议》被大量的开源软件所使用，对今日的开源软件社区有着深厚的影响。  

>对于Linux是否应当被成为GNU/Linux这一点，开源社区有着巨大的争议。包括GNU之父支持者Richard认为，Linux的众多发行版使用了GNU应用，并且他们都是至关重要的--在后面的学习中你也会体会到这一点。  

>如果你对计算机硬件很感兴趣，那你一定听过*Nvidia f**k you*这句“至理名言”。实际上，这是Linus在一次对大学的访问中，当学生提到Nvidia显卡对Linux系统的兼容性差这一问题时，Linus为表达对Nvidia公司的不满所言。

总而言之，Linux系统是一个**类Unix系统**。一个类Unix系统主要包含两部分：**Kernal和Shell**。前者为底层硬件的具体操作提供了途径，而后者方便用户控制系统，只需要在Shell中输入相应的命令，就可以对系统进行操作。

>你需要学的就是通过Shell操控那个内核。内核在干什么？管他呢。

### 为什么要使用Linux？为什么不用Windows？

~~答：比Windows强大~~

因为Linux有着庞大的开源社区作为支持，并且是开源的，使用者可以自由的配置各种各样的应用。比如，**ROS（Robot operating system）**，也就是在AIM战队的各位，用于使各种程序合作运行的框架，就是（只能）运行在Linux上的。同时，配置开发环境时，Linux往往比Windows更加简便。以**Debian**系的Linux发行版（包括你将要学习的Ubuntu）为例，安装某一程序往往只需要输入：  

```bash
sudo apt install [program]
```

就完成了。

是的。apt甚至会帮你同时安装完成依赖项。缺少依赖了？还是使用 ```apt install``` 一句解决~~而Windows用户甚至会因为在打游戏的时候缺少DirectX花上半天的功夫装驱动~~。

不仅如此，Linux运行程序的速度比Windows更快。比如在Blander上进行渲染，Windows用户会多花30%的时间，而在开发环境ESP32中，根据乐鑫（ESP32的厂商）的说法，编译相同程序时，Linux用户只需要使用Windows用户一半的时间。

>Steam Deck使用的就是Arch Linux。

除此之外，Linux内核是可以根据用户的需求进行定制的。比如，在一些对实时性需求较高（工业生产，机器人......）的情境下，Linux用户可以在内核添加功能，自行编译一个符合自己需求的内核。

最后，Linux占用的资源更少。当Windows11一开机就会使用8G的内存空间时......对于Ubuntu发行版，即使使用被认为更占用资源的KDE桌面环境时仅会使用不到2G的内存空间--而不使用桌面环境则会使得你的内存占用远低于1G。通过删去内核中不必要的功能，Linux可以在各种低性能的嵌入式系统中运行。

>“‘当Windows11一开机就会使用8G的内存空间时’没这么多，windows占多少内存也是看你本来有多少内存的，4G内存它就只占2G了” --mxdh 

>有一个玩笑就是在面包机里用Linux系统。

>Ubuntu默认使用Gnome桌面环境，对，就是GNU的一部分。使用KDE桌面环境、基于Ubuntu的发行版被成为Kubuntu，类似的还有Lubuntu和Mint，当然他们除了桌面环境可能会有变化外也会有一些其他的自带工具。

>Linus非常讨厌Debian，因为早期Debian十分难以安装。不过对于现在的Ubuntu而言，你会有直观的图形安装环境--相信我，它会比安装Windwos更简单。想要体会一下1999年的Debian安装有多难受可以观看视频：https://www.bilibili.com/video/BV1hf4y1N7BS/?spm_id_from=333.337.search-card.all.click&vd_source=271e405cd9556c7b3c77c6d0da84fb3b

>对了，Ubuntu这个发行版是基于Debian的一个发行版，这些基于Debian的发行版 ~~以及基于Debian发行版的发行版或者基于Debian发行版的发行版的发行版%#￥！#@%*&~~ 被成为Debian系。类似的还有REHL系，Arch系等。前文提到的apt则是Debian系Linux的一个特有的**包管理系统**，之后的篇章会提到。

>顺带一提，ROS2可以运行在Windows上，但是为了~~白嫖他人的劳动成果~~使用更多ROS社区上已完成的功能包、加快开发进度，我们依然使用ROS noetic。

**总而言之，希望大家可以享受学习Linux的过程。** 

~~真的会有人享受这玩意？~~