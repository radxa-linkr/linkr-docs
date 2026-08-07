---
sidebar_position: 20
---

# 双重验证（2FA）

瑞莎灵控（Radxa Linkr）支持基于 TOTP 的双重验证。开启后，登录时除了用户名和密码，还需要输入身份验证器生成的 6 位验证码，进一步提高账号安全性。

## 使用前提

请先在手机或其他可信设备上安装支持 TOTP 的身份验证器，例如：

- [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=zh-Hans)
- [Microsoft Authenticator](https://support.microsoft.com/zh-cn/authenticator/about-microsoft-authenticator)
- [Bitwarden Authenticator](https://bitwarden.com/help/bitwarden-authenticator/)
- [1Password](https://support.1password.com/one-time-passwords/)

也可以使用其他支持扫描二维码或手动输入密钥的 TOTP 身份验证器。

:::warning 重要
当前版本不会生成恢复码。开启 2FA 后，请妥善保管身份验证器和 2FA 密钥。不要向他人分享二维码、密钥或验证码。
:::

## 开启双重验证

进入 [linkr.now](https://linkr.now/) 管理页面的系统设置 -> 安全 -> 开启 Two-factor Authentication（2FA）选项。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-2fa-bind.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

① 点击系统设置选项

② 开启 2FA 功能

③ 使用身份验证器扫描页面中的二维码，然后输入身份验证器生成的 6 位验证码。

④ 点击确认完成操作

如果无法扫描二维码，可以复制页面显示的密钥，在身份验证器中手动添加。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-2fa-succ.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

## 使用双重验证登录

开启 2FA 后，登录还需要提供身份验证器生成的 6 位验证码。

<div style={{textAlign: 'center'}}>
   <img src="/img/linkr/linkr-2fa-login.webp" style={{width: '100%', maxWidth: '1200px'}} />
</div>

## 关闭双重验证

进入 [linkr.now](https://linkr.now/) 管理页面的系统设置 -> 安全 -> 点击关闭双重验证的选项。
