# Python抢票程序优化，可以选择车次和座次


## 本代码文章首发于公众号「Python知识圈」，如需转载，请通过公众号联系作者pk哥，谢谢

![公众号](https://github.com/Brucepk/pk.github.io/blob/master/gzh.jpg)

[我的个人技术博客](https://www.pyzhishiquan.com/)

### 说明
本文源码在第一版的基础上做的优化，提醒：运行代码请仔细阅读文章相关的配置。二等座的value值是大写的O，而不是阿拉伯数字0，需要抢二等座的切记。[具体文章](https://dwz.cn/3ij9hkI5)

pk 哥在元旦前写了一篇关于自动化抢票的程序 [用Python抢火车票加邮件通知](https://mp.weixin.qq.com/s?__biz=MzU4NjUxMDk5Mg==&mid=2247484924&idx=1&sn=b9d1e91f48208b21aded7a2a5bb5a075&chksm=fdfb6203ca8ceb15e068a1e05cce009a408d369353eed644b35d42f715f1f392be99bd328285&token=1637290204&lang=zh_CN#rd)，本来只是写着玩玩，增加抢票的另一种途径而已。没想到短短几天，群里加了将近 150 名小伙伴，这也预示春节的火车票真是一票难求啊。pk 哥写这个程序的初衷是因为去年我的返程票是通过手动不停的刷新点击抢到的，我想着能不能通过程序自动化去刷新并点击抢票，所以就有了这个 Python 抢票程序。

毕竟这个程序是 Python 模拟手工去操作浏览器的，所以会因为各种网络或者其他因素导致程序终止，群里反馈最多的就是增加车次选择功能和座次选择功能。本文主要讲解这两个优化点，群里也有很多小白也在用这个程序，所以本文会对一些详细的参数配置进行说明。



### 自动抢票流程
首先，梳理下本次优化后的抢票流程。

自动启动浏览器，自动化输入程序里设置好的 12306 的登录账号和密码。

自己手动输入验证码，图形验证码设别功能太复杂，涉及到人工智能的图像识别，自己做的话成功率不高，所以我这里让大家手动输入，输入验证码后手动点击「登录」按钮。

登录成功后页面会自动校验，确认登录成功后会自动跳转到查票页面。根据自己程序代码里输入的出发地和目的地进行查票。

根据自己输入的车次进行查询右边「预定」按钮是否高亮可点，不可点的话会一直点击「查询」按钮不断的刷新页面直到出现有票点击「按钮」按钮。

提交订单页面，选择乘客，选择座位类型，如果没有自己想要的类型，比如，二等座，页面会重新回到火车票查询页面，重新查询，如此循环。

抢到你想要的票后，提交订单，发送邮件，完成！

登录页面
这部分我把浏览器窗口最大化了，之前没设置全屏，大家电脑显示屏大小不一样，可能出现有些元素被遮挡无法点击。

登录之后可能会出现网络可能出现的问题的提示，估计是服务器的问题，这时手动点一下左上角的返回，一般就可以恢复正常，如果点一次还是这个提示，那就点两次吧。

### 原文请 [点击这里查看](https://mp.weixin.qq.com/s?__biz=MzU4NjUxMDk5Mg==&mid=2247484965&idx=1&sn=f7aae7334a6aa42c969fc284522754eb&chksm=fdfb61daca8ce8cc98e1eb6748ea39070338a1b946d99d357e801635881f497c2a5fefecdc52&token=1637290204&lang=zh_CN#rd)
