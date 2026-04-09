# 用户组管理

以下命令需要root用户执行：

## 1. 创建用户组
Groupadd 用户组名

## 2. 删除用户组
Groupdel 用户组名

## 3. 创建用户
Useradd [-r -d] 用户名

- `-g`：指定用户的存在的组，不指定的话会创建同名组并自动加入，指定-g需已经存在，如已存在同名组，必须使用-g选项
- `-d`：指定该用户存在的路径，不指定，默认在/home/用户名

Eg. Useradd test2 -g heartfelt2amor -d /home/test222  
加入heartfelt2amor这个组，路径在test222

## 4. 删除用户
Userdel [-r] 用户名  
- `-r`：删除该用户的目录

## 5. 查看用户所属组
id 用户名（如果不提供时则查看自身）

## 6. 修改用户所属组
Usermod -aG 用户组 用户名  
将用户名加入用户组

## 7. 查看当前系统拥有的用户/用户组
Getent passwd（用户）/ group（组）
