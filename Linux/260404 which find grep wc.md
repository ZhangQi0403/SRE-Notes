
# Which
查看所使用的程序（运行指令即调用程序）文件在哪里

# Find
## 基本语法
Find 起始路径 -name “被查找文件名”

- `-name`: 按照文件名搜索

Eg. Find / -name “test*”  
在根目录里搜索以test开头的文件

## 按大小搜索
Find 起始路径 -size +/-大小量

- `-size`：按照文件大小搜索

Eg. find / -size -100M  
在根目录里查找大于100MB的文件

# Grep
## 基本语法
Grep [-n] 关键字 文件路径

从文件中通过关键字过滤文件行（输出带关键字的行）

- `-n` 可选，表示需要过滤的行号

Eg. grep “sb” test.txt  
在test文件中挑出带sb的行

# wc
## 基本语法
wc [-c -m -l -w] 文件路径

- `-c`: 统计bytes数量
- `-m`: 统计字符数量
- `-l`: 统计行数
- `-w`: 统计单词数量

如果不带以上参数，直接 `wc 文件路径`：输出 行数 单词数 字节(byte)数

# 管道符
将管道符左边命令的结果作为右边命令的输入

Eg. grep “sb” test.txt 等于 cat test.txt | grep “sb”

> 有管道，就先（只能）流向管道，因此test流向grep而不是屏幕，cat不往屏幕输出未过滤内容
