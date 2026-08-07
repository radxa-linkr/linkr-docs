---
sidebar_position: 10
---

# Wi-Fi 热点

主要介绍瑞莎灵控自发热点给主机（控制设备）连接的控制方式。

:::tip 使用前提
Wi-Fi 热点连接需要进入 [linkr.now](https://linkr.now/) 的管理界面进行配置，所以首次配置需要通过 USB-C 直连和 USB-C 转 RJ45 方式连接成功后才可以配置 Wi-Fi 连接。

- [USB-C 直连](./usb-c.md)

- [USB-C 转 RJ45](./rj45.md)

:::

## 硬件连接

使用瑞莎灵控的 HDMI 输入接口和 USB-C 设备接口连接被控设备，在 [linkr.now](https://linkr.now/) 的管理界面中配置 Wi-Fi 热点后，主机（控制设备）连接到瑞莎灵控的 Wi-Fi 热点。

:::tip

示意图是 Wi-Fi 热点连接方式的接线图，若没有开启热点，请先按照有线连接（USB-C 直连或 USB-C 转 RJ45）方式配置好热点，再进行下图的硬件连接。

:::

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/wifi-hot.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

① 瑞莎灵控

② 被控设备

③ 主机（控制设备）

- 指示灯说明

完成上面的硬件连接后，系统状态指示灯会由蓝色闪烁状态（系统启动中）转为蓝色常亮状态（系统正常运行），视频状态指示灯亮起说明检测到被控设备的 HDMI 视频信号。

## 控制被控设备

### 配置 Wi-Fi 连接

基于有线连接（USB-C 直连或 USB-C 转 RJ45）方式在灵控的管理界面进行 Wi-Fi 连接。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-wifi-hot.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### Wi-Fi 控制被控设备

断开有线连接方式，验证 Wi-Fi 热点控制方式，主机（控制设备）连接灵控对应的 Wi-Fi 热点。

使用 Chrome、Edge 或火狐浏览器打开 [linkr.now](https://linkr.now/) 页面，访问瑞莎灵控的管理界面。

说明：后续 linkr.now 版本更新后，UI 界面可能有所不同，按照实际页面提示进行操作即可。

### 允许访问权限

在首次访问 [linkr.now](https://linkr.now/) 页面时，浏览器可能会提示您允许访问权限。请根据提示进行操作，以确保能够正常搜索到瑞莎灵控。

:::tip

已经允许访问权限的不会再次申请，直接进入下一步。

:::

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

点击对应名称的设备卡片进入控制页面。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-device.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### 登陆灵控设备

使用设置的用户名和密码登录灵控设备。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-login.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

### 灵控管理界面

登陆成功后会显示被控设备的系统界面，侧边是灵控设备的功能选项区。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-succ.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>
