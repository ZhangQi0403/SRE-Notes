
# CentOS 7 网络配置与排错实践笔记 🚀

本项目记录了在 VMware 环境下，解决 CentOS 7 虚拟机网络连接失效、FinalShell 连不上的完整排错过程。

## 🔍 问题描述 (Issue)
1. **DHCP 失效**：虚拟机无法通过 DHCP 获取 IP 地址（`ifconfig` 只有 `lo` 或无有效 IP）。
2. **权限受限**：使用 `vi` 编辑配置文件时提示 `E45: 'readonly' option is set`。

---

## 🛠️ 排错与解决方案 (Troubleshooting)

### 步骤 1：获取最高权限 (Root Privilege)
由于 `/etc/sysconfig/` 下的文件属于系统级配置，普通用户无法修改。
```bash
# 切换至 root 用户
su root
# 输入密码（屏幕不显示字符）
```
# 检查实际网卡名称
ifconfig -a 

### 步骤 2：定位并修改网卡配置文件
CentOS 7 的网卡配置文件通常位于 /etc/sysconfig/network-scripts/。
# 编辑对应文件（以 ens33 为例）
vi /etc/sysconfig/network-scripts/ifcfg-ens33

### 步骤 3：配置静态 IP 模板 (Static IP Config)
进入 vi 后，按 i 进入编辑模式，将内容修改为以下 静态 IP 方案（解决 DHCP 服务不稳定的根本方法）：
```bash
TYPE=Ethernet
BOOTPROTO=static      # 关键：从 dhcp 改为 static
NAME=ens33
DEVICE=ens33          # 必须与 ifconfig 查出的网卡名一致
ONBOOT=yes            # 关键：设置开机自动启动网卡
IPADDR=192.168.10.130 # 手动分配的静态 IP
NETMASK=255.255.255.0
GATEWAY=192.168.10.2  # 对应 VMware NAT 设置中的网关
DNS1=114.114.114.114  # 公共 DNS
```
保存退出方法：按 Esc，输入 :wq 并回车。

### 步骤 4：重启网络服务
```bush
systemctl restart network
```



### ⚠️ 经典陷阱：为什么 FinalShell 显示 IP 为 0.0.0.128？

**问题现象**：
在 FinalShell 的连接窗口中，主机地址自动变成了 `0.0.0.128`，导致无法远程连接。

**根本原因**：
1. **DHCP 获取失败**：CentOS 虚拟机没能从 VMware 的虚拟网络（VMnet8）那里拿到有效的 IP。
2. **服务未启动**：VMware 的 DHCP 服务在 Windows 主机上可能已经停止工作。
3. **残留地址**：`0.0.0.128` 并不是一个合法的子网 IP，而是系统在网络未通时的异常显示。

**解决方案**：
不要依赖 FinalShell 自动识别的地址！
1. 回到虚拟机，执行 `ip addr` 或 `ifconfig` 确认。
2. 按照上文配置 **静态 IP**（如 `192.168.10.130`）。
   确保 `/etc/sysconfig/network-scripts/ifcfg-ens33` 中的 `IPADDR` 是你亲自设定的静态地址。
   # 示例：强制锁定为 130
   IPADDR=192.168.10.130
4. **关键操作**：在 FinalShell 的连接配置里，手动把“主机”那一栏从 `0.0.0.128` 修改为你自己设定的静态 IP。
