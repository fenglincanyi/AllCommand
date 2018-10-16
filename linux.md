* 查找 文件名 xxx 
find / -name 'java' -type d    查找'java'

* 打开findler
open path

* 比较2个文件
diff path1 path2

* 远程传输文件
scp local_path remote:path

* 删除当前目录 所有 .DS_Store
find . -name '*.DS_Store' -type f -delete

* 压缩当前目录的所有文件
zip -r xxx.zip ./*
