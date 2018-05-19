# 指针&MachO文件
## 指针
* 指针自增、自减的结果，其实就是指针指向的数据类型**宽度**决定的！
* 指针加上或减去一个整数的结果，其实就是指针指向的数据类型**宽度**决定的！
* 指针求差，得到的结果是整形，其结果和指针指向的数据类型**宽度**有关！
* 这也就是指针的特点！ 它的运算单位 是数据类型的宽度！

关于汇编,重点.只能是带大家入门.

## 逆向原理
**动态调试** 通过界面调试Cycript\Xcode LLDB!
**静态分析** 利用我们之前学习的汇编代码,分析三方APP的源码!
**代码注入** 注入的其实是动态库!HOOK代码 改变原来程序的执行流程!
**重签名**   安装在非越狱手机上面

## class-dump
$ class-dump -H MachO文件Path -o 头文件路径

## MachO文件
官方介绍总共有11种格式! 是 Mach Object的缩写,是Mac\iOS 上用于存储程序,库的标准格式!
常见的格式:

* 1.可执行文件 
* 2.objcet
	* .o 文件(目标文件)
	* .a 静态库文件.其实就是N个.o文件的集合
* 3.DYLIB: 动态库文件
	* dylib
	* framework
* 4.动态连接器
* 5.DSYM 


### 动态库共享缓存
为了提高性能,系统的动态库文件都存在了动态库共享缓存里面!
### 动态加载器(dyld)
* dynamic linker
* dynamic loadel	
	
### 拆分二进制文件
经常用于整合静态库

**瘦身**

```
$ lipo 002--可执行文件 -thin armv7 -output macho_armv7
$ lipo 002--可执行文件 -thin armv64 -output macho_armv64
```


**整合**

```
$ lipo -create macho_armv7 macho_arm64 -output machO_v7_64
```

