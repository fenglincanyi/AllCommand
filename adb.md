文档：<https://developer.android.com/studio/command-line/logcat?hl=zh-cn>


* gradle任务查看其子依赖任务，不会真正执行会skip
<br>`./gradlew clean :module_name:podInstall -m`

* 启动app的某个activity

adb shell am start -a android.intent.action.VIEW -d "schema://path"

启动app的某个activity，并携带参数

adb shell am start -a android.intent.action.VIEW -d "schema://path?param1=abcd'&'param2=12'&'param3=cdef"
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
* grep 过滤日志 或的关系

` adb logcat -c && adb logcat -v color | grep -E "AAA|BBB" `

* 启动debug

adb shell am set-debug-app -w 包名

adb shell am clear-debug-app


https://droidyue.com/blog/2017/05/14/a-little-but-useful-debug-skill_for_android/

* adb 过滤日志（https://developer.android.com/studio/command-line/logcat?hl=zh-cn#formatmodify）

adb logcat *:W  (warining级别以上的日志)

zsh报错：

```shell
zsh: no matches found: *:W
```

* adb输出显示颜色

```shell
adb logcat -v color
```

* adb 清除缓存，从当前日志开始shuc
```shell
adb logcat -c && adb logcat
```

编辑vim ~/.zshrc,增加配置：setopt no_nomatch，生效：source ~/.zshrc

* 过滤
```shell
adb logcat -c && adb logcat -v color | grep " E "

adb logcat -c && adb logcat -v color | grep "app_name"
```
android studio Terminal 中执行adb logcat *:S 报错
zsh: no matches found: *:S
因为zsh缺省情况下始终自己解释这个*:S，而不会传递给adb logcat来解释
在~/.zshrc中加入:
setopt no_nomatch
然后执行命令

source .zshrc


* systrace 使用

`python systrace.py --time=监控时长  -a 进程名 -o 输出文件 gfx input view webview wm am audio video camera hal  res dalvik rs sched freq idle load`
