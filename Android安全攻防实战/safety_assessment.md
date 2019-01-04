   ## 安装santoku以及drozer

   运行drozer

   1.手机端运行drozer(enable)
   2.adb forward tcp:31415 tcp:31415
   3.开启 console  $ drozer console connect

   枚举包
   $ run app.package.list #列出所有已安装的包
   $ run app.package.info #列出包的信息 (-a 包名) (-p 权限)  

   枚举activity
   $ run app.activity.info #列出所有导出的activity (-f activity名) (-a 包名)

   枚举content provider
   $ run app.provider.info #列出所有导出的content provider (-p 权限名) (-a 包名)

   枚举service
   $ run app.service.info

   枚举broadcast receiver
   $ run app.broadcast.info # (-a ) (-f ) (-u 未导出的receice) (-i 是否包含intent filter)

   列出包中所有导出的activity
   $ run app.package.attacksurface 包名
 
   运行activity
   $ run app.activity.start ... 参数

   编写drozer模块
   $ module repository create /Users/moonagirl/Desktop/example/repo
   $ module install /Users/moonagirl/Desktop/example/ex.device.info
   $ run ex.device.info

   
 