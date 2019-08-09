* 启动app的某个activity

adb shell am start -a android.intent.action.VIEW -d "schema://path"
* 查看app的线程情况

adb shell ps -T|grep 包名

adb shell ps -T|grep USER(上个命令中显示的)  (-c 统计多少个)
```java
➜  [/Users/geng] adb shell ps -T | grep com.xxx
u0_a1118     16885 16885  1049 2063020 196156 0                   0 S com.xxx

➜  [/Users/geng] adb shell ps -T | grep u0_a1118
u0_a1118     16885 16885  1049 2064112 196232 0                   0 S com.xxx
u0_a1118     16885 16891  1049 2064112 196232 0                   0 S Jit thread pool
u0_a1118     16885 16892  1049 2064112 196232 0                   0 S Signal Catcher
u0_a1118     16885 16893  1049 2064112 196232 0                   0 S JDWP
u0_a1118     16885 16894  1049 2064112 196232 0                   0 S ReferenceQueueD
u0_a1118     16885 16895  1049 2064112 196232 0                   0 S FinalizerDaemon
u0_a1118     16885 16896  1049 2064112 196232 0                   0 S FinalizerWatchd
u0_a1118     16885 16897  1049 2064112 196232 0                   0 S HeapTaskDaemon
u0_a1118     16885 16898  1049 2064112 196232 0                   0 S Binder:16885_1
u0_a1118     16885 16899  1049 2064112 196232 0                   0 S Binder:16885_2
u0_a1118     16885 16900  1049 2064112 196232 0                   0 S Binder:16885_3
... ...


➜  [/Users/geng] adb shell ps -T | grep u0_a1118 -c
225
```

* systrace 使用
python systrace.py --time=监控时长  -a 进程名 -o 输出文件 gfx input view webview wm am audio video camera hal  res dalvik rs sched freq idle load