---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 管理全局 IP 地址

可以在**子网**屏幕中管理全局 IP 地址。 

1. 在浏览器中，打开[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://control.softlayer.com/){: new_window} 并登录到您的帐户。
2. 在客户门户网站导航中，选择**网络 > IP 管理 > 子网**。
3. 在下拉菜单中，选择**全局 IPv4**（或 IPv6）来过滤子网列表，以仅显示全局 IP。
4. 单击要管理的全局 IP。
 
  **注：全局 IP 是一种静态 IP 地址，可以路由到 IBM Cloud 网络中的任何服务器。当前静态 IP 地址产品只能路由到同一数据中心内的 IP 地址，但全局 IP 地址无此限制。**

5. 在 IP 地址管理页面上，输入您希望将全局 IP 地址路由到的服务器的 IP 地址，并输入任何适用的注释，然后选择**更新**。

![图 2](images/2_1.png)

## 向服务器添加全局 IP 

必须将全局 IP 正确添加到系统后，服务器才会接受该 IP 的流量。每个系统需要的命令略有不同，因此接下来的几节中将显示这些命令。

### 对于 Linux 服务器：

**Red Hat/CentOS**

1. 编辑（vim 或 nano）`/etc/sysconfig/network-scripts/ifcfg-eth1:1`

* 添加以下行：
```
      DEVICE=eth1
      IPADDR=[全局 IP 地址]
      NETMASK=255.255.255.255
      NETWORK=[主 IP 块的网络]
      ONBOOT=yes
```

**Debian/Ubuntu**

1. 编辑 `/etc/network/interfaces`

* 添加以下行：

```
      post-up ip addr add [全局 IP 地址]/32 dev eth1
      post-down ip addr del [全局 IP 地址]/32 dev eth1
```

如果系统无法正常运行，请改为添加以下行，将 # 替换为下一个可用的编号：

```
        auto eth1:#

        iface eth1:# inet static

        address [全局 IP 地址]

        netmask 255.255.255.255

        gateway [服务器主公用网关]
```

### 对于 Windows 服务器

1. 浏览至：**开始 -> 控制面板 -> 网络连接 -> 本地区域连接（公用）（属性）**。
* 选择 **Internet 协议 (TCP/IP)**，然后单击**属性 -> 高级**。
* 在“IP 地址”部分中，选择**添加**，然后输入 IP 地址和子网掩码。
* 完成此任务后，只需单击“确定”返回到桌面。

要验证设置是否已生效，请通过浏览至**开始 -> 运行 ->“cmd”**来打开 DOS 提示符并运行以下命令：

```
        > ipconfig /all
```

**注：**

* 如果服务器上已经有如上面示例所示的 `eth1:1` 文件，请将最后一位数增大到下一个可用的整数。
* 将全局 IP 地址修改为新服务器或 VSI 最长需要 5 分钟才能生效。 
* 在 IBM Cloud 网络中，路由更改的更新时间少于 1 分钟。
* 全局 IP 不适用于本地负载均衡器。
* 全局 IP 从唯一子网进行分发；现有客户 IP 无法转换为或用作全局 IP。
* 全局 IP 本身并不是自动故障转移解决方案，因为全局 IP 不执行运行状况检查；但是，如果您想回避 DNS 传播，那么全局 IP 地址可用作故障转移环境的组件。
