# systemctl命令

## 基本语法
Systemctl + 指令 + 软件名（服务名）

## 常用指令
- `start`：启动
- `stop`：停止
- `status`：查看运行状态
- `enable`：开机自启
- `disable`：停止开机自启

## 常见服务示例
- `sshd`：远程登录
- `NetworkManager`：主网络服务
- `network`：副网络服务
- `firewalld`：防火墙

> 除了内置服务以外，部分第三方软件安装后也可以用systemctl控制

---

# 软链接

## 基本语法
Ln -s 参数1 参数2

## 示例
Ln -s /etc/yum.conf ~/yum.conf  
类似于在home目录里添加yum快捷方式

# date
date [-d] [格式化的字符串，可配合+"%格式"] 在命令行中查看系统时间
%s:1970-1-1到现在的秒数

# 修改linux时区（需要有root权限）
rm -f /etc/localtime 先删除本地时间
ln -s /usr/share/zoneinfo时区信息/地区 /etc/localtime 把要加的时间连接到现在的本地时间文件夹里

# ntp 自动校准
yum -y install ntp
然后可通过指令启动并且设置开机自启

ntpdate -u 服务器名(eg.ntp.aliyun.com)
