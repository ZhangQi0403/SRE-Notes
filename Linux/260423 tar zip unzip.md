# Linux 常用压缩格式

- tar（.tar）：仅仅简单封装，没有太多文件体积的减少
- gzip（.gz）：极大减少文件体积

# tar 命令

Tar [-c -v -x -f -z -C] 参数1 参数2 ... 参数N

- -c：创建压缩文件，用于压缩模式
- -v：显示压缩、解压过程，用于查看进度
- -x：解压
- -f：要创建的文件，或要解压的文件，-f选项必须在所有选项中位置处于最后一个
- -z：gzip模式，不使用-z就是普通的tarball格式
- -C：选择解压的目的地，用于解压模式，不限于该位置

注意：压缩（-c）与解压（-x）冲突，不能同时使用

示例：

tar -cvf test.tar 1.txt 2.txt 3.txt
将后面三个文件压缩到test.tar压缩包里

tar -xvf test.tar /home/heartfelt2amor
将文件解压到该目录

# zip 命令（压缩文件）

Zip [-r] 参数1 参数2 ... 参数N

- -r：需要使用文件夹时

# unzip 命令（解压文件）

Unzip [-d] 参数

- -d：等于tar的-C，指定解压路径
