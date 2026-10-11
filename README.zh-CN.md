# Cauli Photo 0.0.1-alpha.1

[English](README.md)

Alpha 临时测试版 · 构建号 1

## 源码对应

应用源码：源码仓库 `main` 上的 `release/0.0.1-alpha.1`，提交 `b277d6bfcd461250bea7f82a60ec4b5763fda27a`。本仓库的 `v0.0.1-alpha.1` tag 标识发布说明。

## 下载

| 平台 | 安装包 | 校验文件 |
| --- | --- | --- |
| macOS · Apple Silicon | [dmg](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_aarch64.dmg) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_aarch64.dmg.sha256) |
| Windows · x64 | [exe](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_x64-setup.exe) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_x64-setup.exe.sha256) |
| Linux · x64 | [deb](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.deb) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.deb.sha256) |
| Linux · x64 | [AppImage](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.AppImage) | [SHA-256](https://github.com/CloudSir/cauli-photo-release/releases/download/v0.0.1-alpha.1/CauliPhoto_0.0.1-alpha.1_amd64.AppImage.sha256) |

## 更新内容

- 首次公开的 Alpha 临时测试版，提供 macOS、Windows 和 Linux 安装包。
- 支持目录扫描选片、RAW + JPEG 配对、照片预览、评分、入选/淘汰和保护标记。
- Linux AppImage 捆绑 GStreamer，支持视频播放。

## 安装说明

### macOS

打开 DMG，将 **Cauli Photo.app** 拖入 **Applications（应用程序）**，然后启动安装副本。

测试包使用 ad-hoc 签名，未公证。若系统拦截，先核对来源和校验值，尝试启动后到 **系统设置 → 隐私与安全性 → 仍要打开**。若仍提示“已损坏”，重新下载并核对校验值。对于确认可信的测试副本，可先验证签名，再仅移除此应用的隔离属性：

```sh
codesign --verify --deep --strict --verbose=2 '/Applications/Cauli Photo.app'
# 仅在签名验证通过后继续。
xattr -dr com.apple.quarantine '/Applications/Cauli Photo.app'
open '/Applications/Cauli Photo.app'
```

不要自行重签名应用或关闭系统整体安全检查。正常启用 Gatekeeper 的下载放行流程尚未实测。

首次启动或替换应用后可能弹出钥匙串授权。它用于访问本地加密数据库的密钥（`app.cauli.photo.desktop` / `application-state-key-v1`），请输入“登录”钥匙串密码，并仅允许可信的 Cauli Photo 访问。提示可能再次出现，不要为消除提示删除密钥或重置钥匙串。

### Windows

运行安装包，完成后启动 Cauli Photo。若 SmartScreen 拦截已确认可信、校验一致的安装包，可在界面允许时选择 **更多信息 → 仍要运行**。不要关闭系统防护，企业策略可能不允许安装。若安装器提示缺少 Microsoft WebView2 Runtime，按提示安装。浏览器下载后的 SmartScreen 路径尚未实测。

### Linux

安装 deb 时使用 apt 自动安装依赖：

```sh
sudo apt install './CauliPhoto_0.0.1-alpha.1_amd64.deb'
```

Ubuntu 22.04 上运行 AppImage：

```sh
sudo apt install libfuse2 imagemagick libheif1
chmod +x './CauliPhoto_0.0.1-alpha.1_amd64.AppImage'
'./CauliPhoto_0.0.1-alpha.1_amd64.AppImage'
```

## 校验方法

将安装包和对应的 `.sha256` 下载到同一目录。

macOS：

```sh
shasum -a 256 -c 'CauliPhoto_0.0.1-alpha.1_aarch64.dmg.sha256'
```

Linux 使用 `sha256sum -c '<安装包文件名>.sha256'`。Windows 使用 `Get-FileHash -Algorithm SHA256 -LiteralPath '<安装包文件名>'`，与对应 `.sha256` 文件第一项比较。
