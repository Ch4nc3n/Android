## 2.2 检查app的证书和签名

com.taobao.taobao为例子

### /META-INF/CERT.RSA 公钥证书的自签名(公钥证书)

	$ keytool -printcert -file META-INF/CERT.RSA 
	所有者: CN=taobao, OU=taobao, O=taobao, L=hangzhou, ST=zhejiang, C=CN
	发布者: CN=taobao, OU=taobao, O=taobao, L=hangzhou, ST=zhejiang, C=CN
	序列号: 4c59152e
	有效期开始日期: Wed Aug 04 15:22:22 CST 2010, 截止日期: Sun Dec 20 15:22:22 CST 2037
	证书指纹:
		 MD5: 50:6D:2C:60:49:63:D3:A9:B2:79:4B:A6:48:01:02:4E
		 SHA1: 4D:84:31:44:ED:57:7E:0A:2F:D7:B7:CC:13:DF:CC:C3:82:DF:49:7A
		 SHA256: C5:E9:BC:4C:5C:C7:A3:44:82:C6:27:CB:9A:76:B8:8E:30:B5:09:D0:DA:3B:A5:4A:66:27:42:00:E1:9C:27:43
		 签名算法名称: SHA1withRSA
		 版本: 3

### /META-INF/CERT.SF app中各个文件的签名(所有资源文件以及它们的hash)

	......
	Name: res/xml/filepaths.xml
	SHA1-Digest: Uy4ufL7AU3FoR6RzozK5FiOSJAs=

	Name: res/xml/launcher_menu.xml
	SHA1-Digest: AfpL2cc6blVtSUZu2iS+9XoNBSU=

	Name: res/xml/pref_update.xml
	SHA1-Digest: LhCd6Vgdu/EPZyuOvqJddgbyMa0=

	Name: res/xml/taobao_account_preferences.xml
	SHA1-Digest: j6KzwQb8doM9jf+4T49IYtPeU7k=

	Name: res/xml/taobao_authenticator.xml
	SHA1-Digest: v0F2CTJ25GhHDzUnthk7KWykvuE=

	Name: resources.arsc
	SHA1-Digest: orcAK0hT2Ua/iPuSmTcB2mh1acQ=
	......

### /META-INF/MANIFEST.MF 申明了资源以及它们的hash

	......
	Name: res/xml/launcher_menu.xml
	SHA1-Digest: X6ZqJqVH+fTxE788rwQWjdlbs5w=

	Name: res/xml/pref_update.xml
	SHA1-Digest: r8EapGmM8c7sVT6V7UIpt95Q9eo=

	Name: res/xml/taobao_account_preferences.xml
	SHA1-Digest: zhApihdYf51fHh8/Q2kn9CdDqI4=

	Name: res/xml/taobao_authenticator.xml
	SHA1-Digest: yjlX5fgxgkZCOgp5EpOMccr+E9A=
	......

## 2.3 对Android App签名

删除原有的META-INF文件夹

### 1.建立一个秘钥存储器(keystore)

	$ keytool -genkey -v -keystore taobao.keystore -alias taobao -keyalg RSA -keysize 2048 -validity 20

### 2.签名

	$ jarsigner -verbose -sigalg MD5withRSA -digestalg SHA1 -keystore taobao.keystore com.taobao.taobao.apk taobao

## 2.4 验证app的签名

	$ jarsigner -verify -verbose com.taobao.taobao.apk

## 2.5 探索AndroidManifest.xml文件

	$ apktool d -f -s com.taobao.taobao.apk

查看 AndroidManifest.xml

### permission元素

<permission android:name="com.taobao.taobao.permission.MIPUSH_RECEIVE" android:protectionLevel="signatureOrSystem"/>
android:nam

	android:name:
	android:icon:
	android:label:
	android:description:
	android:protectionLevel:
		dangerous/normal/signatrue/signatureOrSystem

### application元素

<application android:allowBackup="false" android:configChanges="keyboardHidden" android:exported="false" android:icon="@drawable/icon" android:label="@string/taobao_app_name" android:largeHeap="true" android:launchMode="singleTask" android:name="android.taobao.atlas.startup.AtlasBridgeApplication" android:persistent="false" android:screenOrientation="portrait" android:supportsRtl="false">

	android:debuggable:能否被调试
	android:enable:系统能否启动该组件
	android:description:描述
	android:allowClearUserData:能否清理app相关数据
	android:exported:其他app能否与这一组间进行交互
	android:name:
	android:permission:与该组件交互需要的权限
	android:

	service特有的：
	android:isolatedProcess:表示该service能够在没有权限的情况下运行在一个独立的进程中

	content provider特有的:
	android:withPermission:规定其他app中的组件要对content provider进行修改或添加所需要的权限的名字
	android:readPermission:规定其他app中组件要对content provider进行读取或查询需要的权限名字
	android:authorities:规定了URI作者名字ID列表

## 2.6 adb与activity管理器交互

	$ pm list packages
	$ am start 

	$ am start ...... 启动activity 参数查表
	$ am startservice ...... 启动服务

## 2.7 通过adb提取app里的资源

	$ cd /data/data
	$ ls -alR */ 
	$ ls -alR */files/
	$ ls -al */*/*.mp3

	$ sqlite3 ...








