### ddms logcat

## 8.3 定位关键代码
### 8.3.1 代码注入法

Log

const-string v3, "SN"
invoke-static {v3,v0}, Landroid/util/Log;->V(Ljava/lang/String;Ljava/lang/String;)I

### 8.3.2 栈跟踪法

new Exception("print trace").printStackTrace();

new-instance v0,Ljava/lang/Exception;
const-string v1,"print trace"
invoke-direct {v0,v1},Ljava/lang/Exception;-><init>(Ljava/lang/String;)V
invoke-virtual {v0},Ljava/lang/Exception;->printStackTrace()V

### 8.3.3 Method Profiling

android.os.Debug.startMethodTracing("123")

const-string v0,"123"
invoke-static {v0},Landroid/os/Debug;->startMethodTracing()V

android.os.Debug.stopMethodTracing()

invoke-static {},Landroid/os/Debug;->stopMethodTracing()V

## 8.5 使用ida调试android原生程序

