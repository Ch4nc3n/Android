# Android可执行程序

## 4.2 Android程序的安装流程

安装方式：

	1.系统程序安装：开机时安装，这类安装没有安装界面
	2.通过android市场进行安装：没有安装界面
	3.ADB工具安装：没有安装界面
	4.手机自带安装：通过sd卡里的apk文件安装，有安装界面

## 4.3 dex文件格式

### 数据类型

u1,u2,u4,u8,sleb128,uleb128,uleb128p1

### dex文件结构

	dex header
	string_ids
	type_ids
	proto_ids
	field_ids
	method_ids
	class_def
	data
	link_data

## 4.4 odex文件格式

### odex文件结构

odex文件头
dex文件
依赖库
辅助数据



## 4.5 dex文件验证与优化工具dexopt的工作过程


