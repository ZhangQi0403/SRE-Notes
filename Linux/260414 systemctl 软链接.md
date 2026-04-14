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
