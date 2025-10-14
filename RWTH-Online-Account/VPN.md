---
title: "连接校园 VPN"
description: "部分校园服务需要连接 eduroam 网络或在校外使用 VPN 访问。"
---
## 什么是 VPN？

虚拟专用网络 (VPN) 是一种互联网安全服务，使用户可以好像连接专用网络一样访问互联网。它不仅会加密互联网通信，而且还能够提供高度匿名访问。人们使用 VPN 的一些最常见原因包括：防范公共 WiFi 上的监听、规避互联网审查，或连接到公司内部网络以进行远程办公。

> 参见：https://www.cloudflare.com/zh-cn/learning/access-management/what-is-a-vpn/

## RWTH VPN 地址

vpn.rwth-aachen.de

## 身份验证

通过 VPN 的身份验证需要先配置 MFA，参见 [[MFA]]。

RWTH Aachen 的 VPN 使用 OTP（一次性密码） 进行 MFA，即：`TAN list`, `Authenticator app e.g. for smartphone (TOTP)` 和 `Hardware Token for VPN and RWTH Single Sign-On (HOTP)` 三种方式，此三种方式均可按照 IdM 中的提示自行配置。

在客户端界面输入 VPN 地址，输入正确的用户名和密码后，会要求输入一个一次性密码，此即为 MFA 中配置的 HOTP/TOTP/TAN。输入正

## 客户端

使用 [Cisco Secure Client (AnyConnect)](https://webspace.noc.rwth-aachen.de/shib/Cisco_Anyconnect/) 进行连接。

下面介绍不同系统的安装方式。

### Windows

直接下载 [cisco-secure-client-win-5.1.8.122-core-vpn-webdeploy-k9.msi](https://webspace.noc.rwth-aachen.de/shib/Cisco_Anyconnect/cisco-secure-client-win-5.1.8.122-core-vpn-webdeploy-k9.msi) 并安装运行即可