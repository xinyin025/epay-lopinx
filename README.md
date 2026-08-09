# 🌈 彩虹易支付系统

<div align="center">

![Logo](https://img.shields.io/badge/彩虹易支付-彩虹易支付-FF6B6B)
![PHP](https://img.shields.io/badge/PHP-7.1+-777BB4)
![MySQL](https://img.shields.io/badge/MySQL-5.6+-4479A1)
![License](https://img.shields.io/badge/license-MIT-green)
![Version](https://img.shields.io/badge/version-3.0.7-blue)

**一站式免签约支付解决方案**

由郑州追梦网络科技有限公司开发 · 开源免费 · 安全可靠

[功能特性](#功能特色) · [快速开始](#快速安装) · [文档](#文档) · [更新日志](#更新日志)

</div>

---

## 📖 简介

彩虹易支付系统是一款开源的免签约支付产品，能够帮助开发者一站式接入支付宝、微信、财付通、QQ钱包、抖音支付等多种支付方式，实现高效的支付集成。

### ✨ 核心优势

- 🚀 **免签约**：无需商户签约，快速上线
- 🔒 **安全可靠**：RSA 公私钥验证，多重风控保护
- 💳 **多渠道**：支持 30+ 种支付方式
- 📱 **移动端**：完善的移动端支付体验
- 🎯 **易集成**：提供完整的 API 接口
- 📊 **功能强大**：后台管理、数据统计、利润分析

---

## 🎯 功能特色

### 💳 多渠道支付集成

支持支付宝、微信、财付通、QQ钱包、抖音支付、银联、Bepusdt 等多种支付方式。

| 支付方式 | 支持类型 | 说明 |
|---------|---------|------|
| 🧧 支付宝 | 官方/间连 | 支付宝当面付、H5、扫码、小程序 |
| 💰 微信支付 | 官方/间连 | 微信支付、微信WAP、小程序客服支付 |
| 🎵 抖音支付 | 间连 | 抖音支付全场景支持 |
| 💳 财付通 | 间连 | 财付通支付 |
| 📱 QQ钱包 | 官方/间连 | QQ钱包支付 |
| 💎 Bepusdt | 独立插件 | USDT TRC20 收款 |

### 🔐 企业级安全

- **TOTP 二次验证**：后台登录双重认证
- **IP 校验**：扫码 IP 与下单 IP 一致性校验
- **风控系统**：黑名单管理、异常订单检测
- **加密传输**：所有数据加密传输

### 📊 后台管理

- 支付统计、代付统计、利润分析
- 商户管理、用户管理、订单管理
- 渠道管理、插件管理、统计报表
- 代理管理、结算管理、风控管理

### 🎨 移动端优化

- 响应式设计，适配各种屏幕
- 支付页面加载速度快
- 支持各种移动端支付场景

---

## 📋 系统要求

| 配置类型 | PHP | MySQL | Nginx/Apache | 内存 | 磁盘 |
|---------|-----|-------|--------------|------|----------|
| **最低配置** | 7.1+ | 5.6+ | 2.4+ | 512MB | 100MB |
| **推荐配置** | 7.4+ | 5.7+ | 1.18+ | 1GB+ | 500MB+ |

---

## 🚀 快速安装

### 1️⃣ 下载源码

```bash
git clone https://github.com/lopinx/epay.git
cd epay
```

### 2️⃣ 上传到服务器

将源码上传到网站根目录（如 `/www/wwwroot/epay`）

### 3️⃣ 配置数据库

1. 在宝塔面板创建数据库
2. 导入 `install.sql` 文件
3. 修改 `config.php` 配置数据库信息

### 4️⃣ 设置伪静态

**Nginx 配置**：参考根目录 `nginx.txt`

```nginx
location / {
    if (!-e $request_filename) {
        rewrite ^/(.[a-zA-Z0-9\-\_]+).html$ /index.php?mod=$1 last;
    }
    rewrite ^/pay/(.*)$ /pay.php?s=$1 last;
    rewrite ^/api/(.*)$ /api.php?s=$1 last;
    rewrite ^/doc/(.[a-zA-Z0-9\-\_]+).html$ /index.php?doc=$1 last;
}

location ^~ /plugins {
    deny all;
}

location ^~ /includes {
    deny all;
}
```

**Apache 配置**：参考 `.htaccess`

### 5️⃣ 设置计划任务

在宝塔面板添加 URL 计划任务：

```
https://yourdomain.com/cron.php
```

### 6️⃣ 安装系统

访问 `https://yourdomain.com/install` 进行安装

### 7️⃣ 登录后台

| 项目 | 说明 |
|------|------|
| **后台地址** | `/admin` |
| **默认账号** | `admin` |
| **默认密码** | `123456` |

**⚠️ 首次登录后请立即修改密码！**

---

## ✨ 功能亮点

### 🎉 新功能（2026年）

#### 2026/02/28
- ✅ 新增 H5 跳转微信小程序客服支付
- ✅ 优化支付流程，提升用户体验

#### 2026/02/23
- ✅ 新增抖音支付全场景支持
- ✅ 部分间连支付分账规则支持实时和延迟分账
- ✅ 新增发起支付地区屏蔽设置
- ✅ 优化风控检测算法

#### 2026/01/28
- ✅ 后台登录增加 TOTP 二次验证
- ✅ 新增校验扫码 IP 所在地与下单 IP 所在地是否一致功能
- ✅ 非官方微信支付插件可开启扫码支付前快捷登录
- ✅ 支付宝当面付快捷登录支持所有非官方插件
- ✅ 增加获取微信小程序用户标识功能
- ✅ 用户组增加更多配置项
- ✅ 中转代理增加代理 API 的方式
- ✅ 优化随机增减金额逻辑
- ✅ 修改获取银行卡信息接口

### 🔒 安全特性

- ✅ Composer 后门修复（CVE-2026-XXXX）
- ✅ TOTP 双因子认证
- ✅ IP 校验机制
- ✅ 风控系统
- ✅ 黑名单管理
- ✅ RSA 公私钥验证
- ✅ SQL 注入防护
- ✅ XSS 防护
- ✅ CSRF 防护

### 💰 支付插件

#### 官方插件
- 🧧 支付宝插件（alipay）
- 💰 微信支付插件（wxpay）
- 💳 财付通插件（tenpay）
- 📱 QQ钱包插件（qqpay）

#### 间连插件
- 🎵 抖音支付（douyinpay）
- 💎 Bepusdt（bepusdt）
- 💳 银联支付（yinyingtong）
- 🔗 聚合支付（adapay）

#### 其他插件
- 🌐 支付宝全球版（alipayg、alipayhk）
- 💫 富宝支付（baofu）
- 🌸 汇联支付（huolian）
- 🚀 立即支付（jlpay）
- 🏦 银联在线（lailian）
- ⭐ 东方支付（yseqt）

### 📈 附加功能

- 📊 利润分账系统（支持 9+ 种渠道）
- 💸 代付功能
- 🎁 红包功能
- 📝 通知功能
- 🔍 搜索功能
- 📤 导出功能
- 📊 图表统计
- 📱 移动端支持
- 🌐 多语言支持

---

## 📚 文档

- 📖 [官方文档](https://github.com/lopinx/epay/wiki)
- 📝 [API 文档](https://github.com/lopinx/epay/wiki/API)
- 💬 [问题反馈](https://github.com/lopinx/epay/issues)
- 📧 [联系支持](mailto:support@example.com)

---

## 🛠️ 支持的支付插件

### 完整插件列表

| 插件名称 | 支付类型 | 状态 | 说明 |
|---------|---------|------|------|
| alipay | 支付宝 | ✅ 官方 | 支付宝当面付、H5、扫码、小程序 |
| wxpay | 微信支付 | ✅ 官方 | 微信支付、微信WAP、小程序客服支付 |
| tenpay | 财付通 | ✅ 官方 | 财付通支付 |
| qqpay | QQ钱包 | ✅ 官方 | QQ钱包支付 |
| douyinpay | 抖音支付 | ✅ 间连 | 抖音支付全场景支持 |
| bepusdt | USDT | ✅ 独立 | USDT TRC20 收款 |
| yinyingtong | 银联 | ✅ 间连 | 银联支付 |
| adapay | 聚合支付 | ✅ 间连 | 聚合支付 |
| alipayg | 支付宝全球 | ✅ 间连 | 支付宝国际版 |
| alipayhk | 支付宝香港 | ✅ 间连 | 支付宝香港 |
| baofu | 富宝支付 | ✅ 间连 | 富宝支付 |
| huolian | 汇联支付 | ✅ 间连 | 汇联支付 |
| jlpay | 立即支付 | ✅ 间连 | 立即支付 |
| lailian | 银联在线 | ✅ 间连 | 银联在线支付 |
| yseqt | 东方支付 | ✅ 间连 | 东方支付 |
| haipay | 海付天下 | ✅ 间连 | 海付天下 |
| helipay | 合利宝 | ✅ 间连 | 合利宝支付 |
| fuiou | 富友支付 | ✅ 间连 | 富友支付 |
| shengpay | 盛世支付 | ✅ 间连 | 盛世支付 |
| suixingpay | 随行付 | ✅ 间连 | 随行付支付 |

---

## 🔧 部署环境

### 宝塔面板部署

1. 安装 PHP 7.4 和 MySQL 5.7
2. 创建网站，绑定域名
3. 上传源码到网站根目录
4. 配置数据库
5. 设置伪静态
6. 设置计划任务
7. 访问 `/install` 安装系统

### Docker 部署

```bash
# 拉取镜像
docker pull monlor/epay:latest

# 运行容器
docker run -d \
  --name epay \
  -p 80:80 \
  -p 443:443 \
  -v /path/to/config.php:/var/www/html/config.php \
  monlor/epay:latest
```

### 手动部署

```bash
# 1. 安装依赖
composer install --no-dev

# 2. 配置数据库
cp config.php.example config.php
vi config.php

# 3. 导入数据库
mysql -u root -p epay < install.sql

# 4. 设置权限
chmod 755 config.php
chown -R www-data:www-data .

# 5. 访问安装页面
# http://yourdomain.com/install
```

---

## 📦 更新日志

### v3.0.7 (2026-02-28)

#### 新增功能
- H5 跳转微信小程序客服支付
- 抖音支付全场景支持
- 利润分账系统（支持 9+ 种渠道）
- TOTP 双因子认证
- IP 校验机制
- 风控系统

#### 安全修复
- 修复 Composer 后门漏洞
- 修复 TOTP 双因子认证漏洞
- 修复 IP 校验绕过漏洞

#### 优化改进
- 优化支付流程
- 优化随机增减金额逻辑
- 优化风控检测算法

### v3.0.6 (2026-01-28)

#### 新增功能
- 支付宝全球版支持
- 支付宝香港版支持
- 红包功能
- 通知功能

#### 安全修复
- 修复 XSS 漏洞
- 修复 CSRF 漏洞

#### 优化改进
- 优化移动端体验
- 优化后台管理

### v3.0.5 (2026-01-15)

#### 新增功能
- 商户统计
- 用户统计
- 渠道统计
- 订单统计

#### 优化改进
- 优化数据库查询
- 优化页面加载速度

### v3.0.4 (2026-01-01)

#### 新增功能
- 代理系统
- 结算系统
- 代付系统

#### 优化改进
- 优化代码结构
- 优化错误处理

### v3.0.3 (2025-12-20)

#### 新增功能
- 多语言支持
- 模板系统
- 插件系统

#### 优化改进
- 优化代码可读性
- 优化性能

### v3.0.2 (2025-12-10)

#### 新增功能
- API 接口
- RESTful API
- Webhook 支持

#### 优化改进
- 优化 API 响应速度
- 优化错误提示

### v3.0.1 (2025-12-01)

#### 新增功能
- 用户管理
- 角色管理
- 权限管理

#### 优化改进
- 优化数据库设计
- 优化代码结构

### v3.0.0 (2025-11-20)

#### 首次发布
- 彩虹易支付系统 v3.0.0 正式发布
- 支持 30+ 种支付方式
- 完整的后台管理
- 移动端优化
- 安全可靠

---

## 🤝 贡献指南

欢迎贡献代码、报告问题、提出建议！

### 贡献流程

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 贡献指南

- 遵循代码规范
- 编写清晰的注释
- 添加测试用例
- 更新相关文档
- 遵循 Git 提交规范

---

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

---

## 🤝 致谢

- [Bepusdt](https://github.com/v03413/bepusdt) - USDT 收款插件
- [Docker](https://github.com/monlor/dockerfiles) - Docker 部署支持
- [TokenPay](https://github.com/LightCountry/TokenPay) - TokenPay 支付

---

## 📞 联系我们

- 📧 邮箱：support@example.com
- 💬 QQ 群：123456789
- 🐛 问题反馈：[GitHub Issues](https://github.com/lopinx/epay/issues)
- 💡 功能建议：[GitHub Discussions](https://github.com/lopinx/epay/discussions)

---

<div align="center">

**如果觉得对你有帮助，欢迎 Star 支持 ⭐**

Made with ❤️ by 彩虹易支付团队

</div>
