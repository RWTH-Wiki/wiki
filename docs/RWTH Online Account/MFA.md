RWTH Online 强制要求 2FA，正确地配置对日后登陆账号、访问相关资源等至关重要。

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

其中，TAN list 认证方式被认为是最繁琐、最不安全的一种认证方式，但是作为账号多因素认证的入口又不得不使用。推荐在账号激活后尽快配置其他的 MFA 方式，以提升安全性和便捷性。下面介绍其中几种 MFA 的配置方式。

### 手机 Authenticator App 验证

常用的手机令牌 App 有：Google Authenticator, Microsoft Authenticator, Yubico Authenticator 等，可以根据自己的习惯选择。

> Microsoft Authenticator 目前不支持云备份，Yubico Authenticator 需要拥有 yubico 密码学硬件才能使用