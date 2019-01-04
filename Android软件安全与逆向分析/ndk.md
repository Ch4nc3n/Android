### main函数何时被执行

	静态链接：crtbegin_static.S -> __libc_init() ->main()
	动态链接：begin.S -> __linker_init() -> crtbegin_dynamic.S -> __libc_init() 

## 原生文件格式

Android elf

	ELF Header
	Program Header Table
	Section 1
	Section 2
	......
	Section Header Table
	......

## 原生C程序逆向分析

### 7.4.1原生程序的分析方法

1.objdump

2.Ida pro

### 7.4.2 for
### 7.4.3 if...else
### 7.4.4 while
### 7.4.5 switch

ADDLS

### 7.4.6 原生程序的编译时优化

## 7.5 原生C++程序逆向分析

	c++类的逆向
	android ndk对c++特性的支持
	静态链接与动态链接stl的代码区别


