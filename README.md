# 加壳器

涉及的加壳器: 自动化实现apk解包,打包, AndroidManifest.xml修改, apk签名



### gen1_v2

简单的一代壳原理实现, 基于[dpt-shell](https://github.com/luoyesiqiu/dpt-shell) 基础上做一个修改. 

在dpt-shell的大框架上, 剔出了函数抽取相关部分, 只关注于dex的加载与执行

=>  [原理分析](./analysis/gen1_v2.md), gen1_v2和gen1_v1的原理有一些关键的区别



```
项目布局:
	-dpt: java项目, 用于加壳,可以生成jar包
	-shell: Android Studio项目, 功能是加载dex, 可以调试来辅助理解
```



usage:

```
usage: java -jar dpt.jar [option] -f <apk>
 -c,--disable-acf      Disable app component factory(just use for debug).
 -D,--debug            Make apk debuggable.
 -f,--apk-file <arg>   Need to protect apk file.
 -l,--noisy-log        Open noisy log.
 -x,--no-sign          Do not sign apk.


λ java -jar dpt.jar -f org_v01.apk 
//他会执行 ProxyAppComponentFactory实现相关加载,与此同时ProxyApplication不会得到执行

λ java -jar dpt.jar -c -f org_v01.apk 
//他会执行 ProxyApplication实现相关加载,与此同时ProxyAppComponentFactory不会得到执行

ps: 至于为什么,我也不知道,QAQ
```







