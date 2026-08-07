---
sidebar_position: 7
---

# 硬件连接

瑞莎灵控支持 USB-C 直连 PC、USB-C 转 RJ45 连接路由器/交换机、Wi-Fi 热点以及 Wi-Fi 客户端连接，用户可根据实际使用场景选择合适的连接方式。

以上方式目的是让瑞莎灵控与主机（控制设备）在同一局域网内，在同一局域网内对被控设备进行控制。

:::tip 远程访问

若需要在不同局域网内访问被控设备，请使用 Tailscale 进行远程访问，具体请参见 [Tailscale 远程访问](../advanced-usage/tailscale.md) 页面。

:::

## 4 种连接方式

Wi-Fi 客户端和 Wi-Fi 热点方式需要在瑞莎灵控的管理界面中进行配置，所以首次配置需要通过 USB-C 直连和 USB-C 转 RJ45 方式连接，然后在 [linkr.now](https://linkr.now/) 管理界面中配置 Wi-Fi 客户端或 Wi-Fi 热点。

<Tabs>
<TabItem value="usb-c-direct" label="USB-C 直连" default>

使用瑞莎灵控的 HDMI 输入接口和 USB-C 设备接口连接被控设备，同时使用 USB-C 数据线连接灵控的 USB-C 网络接口和主机（控制设备）。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/usb-c-direct.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

① 瑞莎灵控

② 被控设备

③ 主机（控制设备）

</TabItem>
<TabItem value="usb-c-rj45" label="USB-C 转 RJ45">

使用瑞莎灵控的 HDMI 输入接口和 USB-C 设备接口连接被控设备，同时使用 USB-C 转 RJ45 数据线连接灵控的 USB-C 网络接口和路由器/交换机。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/usb-c-rj45.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

① 瑞莎灵控

② 被控设备

③ 主机（控制设备）

④ 路由器 / 交换机

</TabItem>
<TabItem value="wifi-hot" label="Wi-Fi 热点">

使用瑞莎灵控的 HDMI 输入接口和 USB-C 设备接口连接被控设备，在 [linkr.now](https://linkr.now/) 的管理界面中配置 Wi-Fi 热点后，主机（控制设备）连接到瑞莎灵控的 Wi-Fi 热点。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/wifi-hot.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

① 瑞莎灵控

② 被控设备

③ 主机（控制设备）

</TabItem>
<TabItem value="wifi" label="Wi-Fi">

使用瑞莎灵控的 HDMI 输入接口和 USB-C 设备接口连接被控设备，在 [linkr.now](https://linkr.now/) 的管理界面中连接 Wi-Fi ，主机（控制设备）和瑞莎灵控连接在同一 Wi-Fi 网络。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/wifi.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

① 瑞莎灵控

② 被控设备

③ 主机（控制设备）

④ 路由器 / 交换机

</TabItem>
</Tabs>

## 指示灯说明

完成上面的硬件连接后，系统状态指示灯会由蓝色闪烁状态（系统启动中）转为蓝色常亮状态（系统正常运行），视频状态指示灯亮起说明检测到被控设备的 HDMI 视频信号。

:::tip 详细步骤

各种硬件连接方式的详细操作可以参考以下教程：

- [USB-C 直连](../basic-usage/usb-c.md)

- [USB-C 转 RJ45](../basic-usage/rj45.md)

- [Wi-Fi 连接](../basic-usage/wifi.md)

- [Wi-Fi 热点](../basic-usage/wifi-hot.md)

:::