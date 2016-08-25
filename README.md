﻿# VirtualAppDoc

## Server Process 启动流程

**getService**
![VirtualCoreGetSerivce](https://rawgit.com/prife/VirtualAppDoc/master/pngs/VirtualCoreGetSerivce.svg)

**Binder Provider调用过程**
![VABinderProvider](https://rawgit.com/prife/VirtualAppDoc/master/pngs/VABinderProvider.svg)

**VirtualActivityManagerService启动流程**
![VAMS](https://rawgit.com/prife/VirtualAppDoc/master/pngs/VAMS.svg)

## startActivity 流程

![VAStartActivity](https://rawgit.com/prife/VirtualAppDoc/master/pngs/VAStartActivity.svg)

![VStubContentProvider](https://rawgit.com/prife/VirtualAppDoc/master/pngs/VStubContentProvider.svg)

## install流程

![VAInstall](https://rawgit.com/prife/VirtualAppDoc/master/pngs/VAInstall.svg)

## Broadcast流程

注意：VA对client的xml中定义的receiver（静态广播接收器）做了处理，详细参考VAInstall流程图。

### 标准Broadcast发送/接收

![标准Broadcast发送/接收](https://rawgit.com/prife/VirtualAppDoc/master/pngs/Broadcast.svg)

### VA中Broadcast发送/接收

![VA中Broadcast发送/接收](https://rawgit.com/prife/VirtualAppDoc/master/pngs/VABroadcast.svg)

### VA中动态Broadcast注册

动态注册Broadcast，最终都会调用ActivityManagerNatvie#registerReceiver方法，因此VA中hook了这个方法
然后改造IntentFilter的ACTION字段，具体改造方法与静态广播接收器的方式相同。

代码：RegisterReceiver.java


**PS**
[添加SVG图片的方法](http://stackoverflow.com/questions/13808020/include-an-svg-hosted-on-github-in-markdown)
