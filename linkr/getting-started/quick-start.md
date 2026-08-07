---
sidebar_position: 1
---

# 快速上手

本节教程目的是为了让大家快速上手使用瑞莎灵控（Radxa Linkr） 产品。

## 产品外观

| 序号 |       视图        | 序号 |       视图        | 序号 |       视图        |
| :--: | :---------------: | :--: | :---------------: | :--: | :---------------: |
|  ①   | 灵控正视图 |  ②   | 灵控侧视图 |  ③   | 灵控背视图 |

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-view.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

## 产品接口

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-interface.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

| 序号 | 说明                   | 序号 | 说明                                                             |
| :--: | :--------------------- | :--: | :--------------------------------------------------------------- |
|  1   | 用户按键           |  2   | USB-C 设备接口                                                 |
|  3   | HDMI 输入接口        |  4   | 视频状态指示灯                                                         |
|  5   | 系统状态指示灯             |  6   | USB-C 网络接口                                                      |

## 使用前提

您需要提前准备好以下设备：

- 瑞莎灵控
- 主机（控制设备）
- 被控设备（如 PC、主板、工控机等）
- USB-C 数据线
- USB-C 数据线或 USB-C 转 RJ45 数据线（用于网络连接）

:::tip 主机（控制设备）
主机（控制设备）需要安装 Chrome、Edge 或火狐浏览器（建议最新版），后期需要在浏览器中访问瑞莎灵控的管理界面。
:::

## 硬件连接

瑞莎灵控支持 USB-C 直连 PC、USB-C 转 RJ45 连接路由器/交换机、Wi-Fi 热点以及 Wi-Fi 客户端连接，快速上手主要介绍 USB-C 直连 PC 和 USB-C 转 RJ45 的连接方式。

:::tip 其他连接方式

更多的连接方式请参见 [硬件连接](./connect-methods.md) 页面。

:::


<Tabs>
<TabItem value="usb-c-direct" label="USB-C 直连" default>

使用瑞莎灵控的 HDMI 输入接口和 USB-C 设备接口连接被控设备，同时使用 USB-C 数据线连接灵控的 USB-C 网络接口和主机（控制设备）。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/usb-c-direct.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

1. 瑞莎灵控
2. 被控设备
3. 主机（控制设备）

</TabItem>
<TabItem value="usb-c-rj45" label="USB-C 转 RJ45">

使用瑞莎灵控的 HDMI 输入接口和 USB-C 设备接口连接被控设备，同时使用 USB-C 转 RJ45 数据线连接灵控的 USB-C 网络接口和路由器/交换机。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/usb-c-rj45.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

1. 瑞莎灵控
2. 被控设备
3. 主机（控制设备）
4. 路由器 / 交换机

</TabItem>
</Tabs>

完成上面的硬件连接后，系统状态指示灯会由蓝色闪烁状态（系统启动中）转为蓝色常亮状态（系统正常运行），视频状态指示灯亮起说明检测到被控设备的 HDMI 视频信号。

## 首次配置

### 访问 [linkr.now](https://linkr.now/)

完成硬件连接后，使用 Chrome、Edge 或火狐浏览器打开 [linkr.now](https://linkr.now/) 页面，访问瑞莎灵控的管理界面。

说明：后续 linkr.now 版本更新后，UI 界面可能有所不同，按照实际页面提示进行操作即可。

### 允许访问权限

在首次访问 [linkr.now](https://linkr.now/) 页面时，浏览器可能会提示您允许访问权限。请根据提示进行操作，以确保能够正常搜索到瑞莎灵控。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-acess-allow.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### 搜索灵控设备

点击 `Start Scanning` 选项搜索局域网内的瑞莎灵控设备。

:::tip 多个灵控设备
若是有多个灵控设备，可以短按灵控侧边的用户按键，对应的灵控设备会在设备页面高亮显示，方便用户区分。
:::

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-scan.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### 选择灵控设备

首次配置的设备名称会显示序列号的部分信息，点击对应的设备选项进行配置。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-select-device.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### 设置用户信息

设置灵控设备的访问用户名、密码和设备名称，设置完成后点击 `Next` 进行下一步。

:::tip 设备名称
对于有多个灵控设备的用户，可以设置不同的设备名称，方便区分不同的灵控设备。
:::

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-device-info.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### 登陆灵控设备

设置完成后，您可以使用刚刚设置的用户名和密码登录灵控设备。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-login.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### 灵控管理界面

登陆成功后会显示被控设备的系统界面，侧边是灵控设备的功能选项区。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-succ.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>
