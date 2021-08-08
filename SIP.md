## 关闭SIP方法

### ARM M1

#### ARM M1 处理器关闭 SIP 步骤

1.  关机
2.  按住开机键不松手直到出现下图的画面，然后点击"选项"

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-01.jpg)

3.  点击"继续"

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-02.jpg)

4.  点击菜单栏的"实用工具"，再点击"终端"

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-03.jpg)

5.  输入"csrutil disable"，然后按下回车也就是 "return" 键

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-04.jpg)

6.  输入"y"，然后按下回车也就是 "return" 键

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-05.jpg)

7.  输入您的电脑密码，然后按下回车也就是 "return" 键

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-06.jpg)

8.  等待执行结果……

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-07.jpg)

9.  出现 "System Integrity Protection is off." 证明 SIP 已成功关闭。

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-08.jpg)

10.  输入 "reboot" 然后按下回车也就是 "return" 键重启电脑即可。

![](https://cdn.macwk.com/public/uploads/_/originals/big-sur-disable-sip-screen-09.jpg)

如果后期想再开启 SIP，只需要将上面第 5 步的 "csrutil disable" 换成 "csrutil enable" 即可。

### Intel 处理器

#### macOS 11.x Big Sur（Intel 处理器） 及以下系统关闭 SIP 步骤：

1.  关机，然后重新启动你的Mac电脑，在开机时一直按住Command+R迸入Recovery模式。
2.  进入Recovery模式后打开终端，如图：

![image](https://cdn.macwk.com/public/uploads/_/originals/recovery-utilities-terminal.jpg)

3.  在终端上输入命令 csrutil disable然后回车。

![image](https://cdn.macwk.com/public/uploads/_/originals/csrutil-disable.jpg)

4.  点击左上角苹果图标，再点击重新启动
