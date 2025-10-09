---
title: "配置 MFA"
description: "RWTH Online 强制要求 MFA，正确地配置对日后登陆账号、访问相关资源等至关重要。"
---

## 什么是 MFA？

多因素身份验证（MFA）是一种验证[用户身份](https://www.cloudflare-cn.com/learning/access-management/what-is-identity/)的方式，比传统的用户名与密码组合更加安全。MFA 通常包含一个密码，但同时也包含一个或两个其他身份验证因素。[双因素身份验证 (2FA)](https://www.cloudflare-cn.com/learning/access-management/what-is-two-factor-authentication/) 是 MFA 的一种。

MFA 是[身份和访问管理 (IAM)](https://www.cloudflare-cn.com/learning/access-management/what-is-identity-and-access-management/) 的重要组成部分，通常在[单点登录 (SSO)](https://www.cloudflare-cn.com/learning/access-management/what-is-sso/) 解决方案中实施。

> 参见：https://www.cloudflare-cn.com/learning/access-management/what-is-multi-factor-authentication/

## 配置 MFA

RWTH Online 支持的 MFA 形式包括：

- Hardware token for VPN and RWTH Single Sign-On (HOTP)：密码学硬件 HOTP
- Hardware token for RWTH Single Sign-On (WebAuthn/FIDO2)：密码学硬件 WebAuthn/FIDO2
- Authenticator app e.g. for smartphone (TOTP)：手机令牌验证 TOTP
- E-Mail：邮箱一次性密码验证
- TAN list (one-time security codes)：一次性密码列表

其中，TAN list 认证方式被认为是最繁琐、最不安全的一种认证方式，但是作为账号多因素认证的入口又不得不使用。推荐在账号激活后尽快配置其他的 MFA 方式，以提升安全性和便捷性。

登录 [idM Selfservice](https://www.rwth-aachen.de/selfservice)，在左侧边栏选择 `Token Manager (MFA)`，即可查看目前已有的 MFA 方式，点击列表下方的`CREATE`即可新建新的验证方式。

下面介绍其中几种 MFA 的配置方式。

### 手机 Authenticator App 验证

常用的手机令牌 App 有：Google Authenticator, Microsoft Authenticator, Yubico Authenticator 等，可以根据自己的习惯选择。

> Microsoft Authenticator 目前不支持云备份，Yubico Authenticator 需要拥有 yubico 密码学硬件才能使用，对初次接触 MFA 验证的同学推荐使用 Google Authenticator。

在键入描述后点击`CREATE`即可生成 TOTP token secret，使用手机验证器扫描二维码即可添加（Google Authenticator 直接点击右下角的`+`，选择`Scan a QR code`），添加后即可显示六位数字的 Security Code，把看到的 code 写入`Verify Token`栏即可验证并完成添加。

此后，在登录账号后要求 MFA 时，即可选择 Authenticator App 验证方式，输入目前手机令牌上显示的六位数字即可完成验证。

### EMail 验证

输入要接受验证码的邮箱并验证即可，和大部分主流网站的验证方式相同，不再赘述。

> hint: 尽量选择自己的私人邮箱进行验证，不要使用 RWTH 邮箱，以避免死锁。

### 密码学硬件 WebAuthn 验证

若想使用此验证方式，需要持有支持 FIDO 的密码学硬件。

> 参见： https://sspai.com/post/78479, https://www.microsoft.com/zh-cn/security/business/security-101/what-is-fido2?msockid=2e86fcb9d398629d24a4eac0d2966303

配置好密码学硬件的 FIDO 模块并设置 FIDO PIN 后，即可将密码学硬件插入电脑，并选择创建`Hardware token for RWTH Single Sign-On (WebAuthn/FIDO2)`，在键入描述后点击`REGISTER`即可启动 WebAuthn 验证，在浏览器弹出的窗口中输入 FIDO PIN 后，触摸密码学硬件的确认区域即可完成添加。

此后，在登录账号后要求 MFA 时，即可选择 WebAuthn 验证方式，将密码学硬件插入设备，输入 FIDO PIN 并触摸确认区域即可完成验证。

> WebAuthn 功能需要浏览器支持，目前市面上主流的浏览器 Chrome, Safari, Firefox, Edge 等均支持 WebAuthn。