# 环境变量

## 查看环境变量
Env 查看环境变量

## PATH变量
环境变量PATH：记录了系统执行任何命令的搜索路径

## $符号
$符号：取到变量的值

Eg. Echo $PATH 输出PATH当前的值即路径

如果想输出路径+别的字符的话，可以括起来  
eg. echo ${PATH}ABC 输出的先是PATH的值紧跟着ABC

## Export：临时设置变量值

- **添加**：Export 变量名=变量值
- **修改**：eg. Export PATH=$PATH:新路径（如果不是新变量，要确保有原有内容，防止被丢弃）

## 永久生效设置

### 当前用户永久生效
1. vi ~/.bashrc 打开vi编辑器插入该变量
2. 使编辑生效：source ~/.bashrc，或重新登录finalshell使生效

### 所有用户永久生效
把 ~/.bashrc 改为 /etc/profile
