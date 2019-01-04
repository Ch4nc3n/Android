# 破解技术

## 试用版软件

### 9.1.2 针对授权key方式的破解

## 序列号保护

## 网络验证

## In-app Billing(应用内付费)

## Google Play License 保护

## 重启验证

### Mono for Android(C#)

／assemblies目录下的dll文件

### Qt for Android(c++)

分析so文件


# 反破解技术

## 10.1 对抗反编译

### 10.1.2 对抗dex2jar

不支持RSUB_INT_LIT8指令

## 10.2 对抗静态分析

### 10.2.1 代码混淆技术

### 10.2.2 NDK保护

### 10.2.3 外壳保护

## 10.3 对抗动态调试

### 10.3.1 检测调试器

AndroidManifest.xml->Application->android:debuggable = 'false'

### 10.3.2 检测模拟器

adb shell getprop

ro.product.model:该值在模拟器中为sdk,在手机中为手机型号
ro.build.tags:该值在模拟器中为test-keys,通常在正常手机中它的值为release-keys
ro.kernel.qemu:该值在模拟器中为1，在手机中没有该属性

## 10.4 防止重编译

### 10.4.1 检查签名
### 10.4.2 校验保护

