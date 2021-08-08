# 另外一种让小助手运行的方法

首先感谢[MustangYM](https://github.com/MustangYM/)大佬的微信小助手！！！

---

## 小助手Alfred扩展

在小助手原有的Alfred扩展的基础上修改了下，新增了：
1. 加载小助手并启动的功能
2. 使用官方微信双开功能

如果日常使用Alfred，这种方式还是很方便的，不用Alfred的同学继续使用独立App运行吧。

**核心代码也是下面那两行，仍是DYLD_INSERT_LIBRARIES加载，所以依然需要自行[关闭SIP](SIP.md)。**

![XEvGWzqsxod2fli](https://i.loli.net/2021/08/08/XEvGWzqsxod2fli.png)
![7fiqGkBleuW3EbD](https://i.loli.net/2021/08/08/7fiqGkBleuW3EbD.png)

下载地址：[WeChat.Plugin.alfredworkflow](https://github.com/levie-vans/WeChatAssistant-ForMac/releases/)

---

## WeChatAssistant-ForMac

**DYLD_INSERT_LIBRARIES需要关闭系统的SIP，如果使用此方法，请自行[关闭SIP](SIP.md)。**

前段时间，[微信小助手](https://github.com/MustangYM/WeChatExtension-ForMac)用户被大规模封号。

我个人认为，究其原因，可能是下面几点：
1. 微信可能会检测自身完整性是否被破坏。WeChatExtension是使用insert_dylib写入微信的MachO的Load Commands来进行加载的，这个过程中，必定不可逆的破坏的微信的签名，甚至需要使用codesign进行重签才可以使用。
2. 微信可以通过检测WeChatExtension这个dylib是否加载到自身进程来进行检测。
3. 其他可能存在的针对函数功能的检测手段。

经过我一段时间的实践，只要针对前两者进行处理，小助手就已经可以稳定运行了：
1. 使用原版微信，不破坏微信的任何原始文件，通过设置环境变量DYLD_INSERT_LIBRARIES的值来加载小助手的dylib。
2. 将WeChatExtension改名为其他系统dylib的名称加载。

所以核心代码就两句：
```shell
export DYLD_INSERT_LIBRARIES="改名后的小助手dylib的路径"
nohup /Applications/WeChat.app/Contents/MacOS/WeChat > /tmp/wechat.txt 2>&1 &
```
为了更方便，将shell封装成App，每次使用只需运行一次这个App，它就会先设置好环境变量并启动官方微信，完美。

下载地址：[WeChatAssistant.dmg](https://github.com/levie-vans/WeChatAssistant-ForMac/releases/download/1.0.0/WeChatAssistant.dmg)

>**假设启动不了，试着重签一下WeChat Assistant.app，重签它不影响微信的自身签名。**

```shell
codesign --force --deep --sign - /Applications/WeChat\ Assistant.app/
```

如果后期微信增加了其他类型检测，再见招拆招吧。总之，广阔天地，大有作为。



## DualWechat-ForMac

如果不需要小助手的其他功能，日常也只是需要双开功能，那么直接使用官方微信无疑是更加安全的。这次就更简单了，一句话的代码：

```shell
nohup /Applications/WeChat.app/Contents/MacOS/WeChat > /tmp/wechat.txt 2>&1 &
```

下面是封装好的App，只要运行一下就可以双开官方微信了。
下载地址：[DualWeChat.dmg](https://github.com/levie-vans/WeChatAssistant-ForMac/releases/download/1.0.0/DualWeChat.dmg)
