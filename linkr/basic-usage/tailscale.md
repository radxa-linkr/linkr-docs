---
sidebar_position: 15
---

# Tailscale 远程访问

瑞莎灵控（Radxa Linkr）内置 Tailscale 客户端。将设备加入 Tailnet 后，无需公网 IP 或端口转发，即可通过加密网络远程访问灵控管理界面。

Tailscale 基于 WireGuard 协议，设备之间的通信会经过加密。

:::tip

使用 Tailscale 远程不会影响灵控的本地网络访问方式。设备仍可通过 USB-C 直连 PC、USB-C 转 RJ45 连接路由器/交换机、Wi-Fi 热点以及 Wi-Fi 客户端连接方式访问。

:::

## 使用前提

- 注册 [tailscale.com](https://tailscale.com/) 账号

- 灵控可以访问互联网

- 主机（控制设备）可以访问互联网并安装 Tailscale

## 配置 Tailscale

进入 [linkr.now](https://linkr.now/) 管理页面的高级设置 -> 启用 Tailscale 功能 -> 绑定 Tailscale 账号。

- 启用 / 绑定 Tailscale

点击绑定选项会自动跳转到 Tailscale 登录 / 授权页面，根据提示将设备连接到 Tailnet。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-tailscale.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-tailscale-connect.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-bind-succ.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

绑定成功后，[linkr.now](https://linkr.now/) 管理页面会显示绑定的账号和版本信息。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-tailscale-succ.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

## 查看 Tailscale IP

绑定成功后，可在 [Tailscale 管理后台](https://login.tailscale.com/admin/machines) 查看设备分配的 Tailscale IP（通常为 `100.x.x.x` 网段）。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-tailscale-ip.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

## 远程控制灵控

主机（控制端）安装并登录 Tailscale，确保其与灵控设备加入同一个账号或 Tailscale 私有网络（Tailnet），然后通过以下地址访问灵控：

```text
https://<设备 Tailscale IP>
```

如果 Tailnet 已启用 MagicDNS，也可以使用 MagicDNS / Full domain 访问：

```text
https://<设备主机名>.<Tailnet 的 DNS 名称>.ts.net
```

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-tailscale-remote-succ.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

:::tip 提示
Tailscale 仅提供安全的网络连接。访问灵控管理界面时，仍需使用灵控本身的用户名和密码登录。
:::

## 参考资料

- [Tailscale 官方文档](https://tailscale.com/kb/)
- [Tailscale 管理后台](https://login.tailscale.com/admin/machines)
- [WireGuard 协议](https://www.wireguard.com/)
