# Bore相关文档
## Android Studio 环境
### Ubuntu
#### 调试依赖文件
```
sudo apt install libncurses5
```
## java目录
mirror 反射调用client app
top.niunaijun.blackbox 核心模块，相对Virtualapp，作者重写了核心代码，工作原理和Virtualapp相同
client 主要是针对内部应用客户端功能的Hook
## blackbox
### 四大组件
#### Service
https://www.jianshu.com/p/9480d462e10e

根据Android Service相关源码，制作了一套简化版的Service作为Blackbox内部管理应用的Service，比如ActivityStack
#### Activity
https://www.jianshu.com/p/329a9eba3a79
### 具体细节

### BlackBoxCore
1.launch
2. ActivityManagerStub内部编写Hook内部应用客户端使用的安卓函数
## jni
## aidl
远程服务调用接口
### 开发技巧
#### 调试
android.os.Debug.waitForDebugger()代码可以在此处暂停进程等待Android Studio附加进程调试，但是需要在其他处设置断点，否则附加后程序就会继续进行
## 缺陷
### /system/lib64/libsandhook-native.so not found in my userspace 
初步怀疑系统层IO未重定向
### com.kiwi.browser浏览器打开崩溃
1. 直接打开崩溃，缺少contentprovider
2. Blackbox陷入调试状态，com.kiwi.browser正常打开但是会卡死, 报错找不到com.miui.contenter和读取GUP_channel超时(Timed out waiting for GPU channel)
初步推测com.kiwi.browser的provider注册没有及时同步
## 参考文档
https://blog.csdn.net/luoshengyang/article/details/6689748