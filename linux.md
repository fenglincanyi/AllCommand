* 查找 文件名 xxx 
`find / -name 'java' -type d    查找'java'`

* 打开findler
open path

* 比较2个文件
diff path1 path2
vimdiff path1 path2

* 远程传输文件
scp local_path remote:path

* 删除当前目录 所有 .DS_Store
find . -name '*.DS_Store' -type f -delete

* 压缩当前目录的所有文件
zip -r xxx.zip ./*


* 查看Java安装路径
`which java`
`ls -l /usr/bin/java`
``` bash
00:13:30 lrwxrwxrwx 1 root root 22 Jul 17 00:12 /usr/bin/java -> /etc/alternatives/java
```
`ls -lrt /etc/alternatives/java`

``` bash
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.1.alios7.x86_64/jre/bin/java
```
