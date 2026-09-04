<p align="center">
  <img src="media/icon.png" width="96" height="96" alt="Cursor Manager">
</p>

<h1 align="center">Cursor Manager</h1>

<p align="center">
  Manage accounts and credit limits within the cursor Sand、 Switching, device and client modes.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Cursor-Extension-1473E6?style=flat-square" alt="Cursor Extension">
  <img src="https://img.shields.io/badge/Windows-Supported-1473E6?style=flat-square" alt="Windows Supported">
  <img src="https://img.shields.io/badge/macOS-Experimental-6B7280?style=flat-square" alt="macOS Experimental">
  <img src="https://img.shields.io/badge/License-Proprietary-C2410C?style=flat-square" alt="Proprietary License">
</p>

Cursor Manager 是一款运行在 Cursor 侧栏中的账号管理扩展。它将多账号、额度、登录设备、客户端登录状态和 Sand Stream 集中到一个界面中，适合需要在多个 Cursor 账号之间查看用量、备份账号和切换登录状态的用户。

扩展不会为账号增加原本不存在的订阅权益，也不会解锁账号无权使用的模型。账号套餐、模型权限和服务可用性仍以 Cursor 官方返回结果为准。

## 目录

- [主要功能](#主要功能)
- [安装](#安装)
- [快速开始](#快速开始)
- [界面说明](#界面说明)
- [添加账号](#添加账号)
- [账号管理](#账号管理)
- [额度与用量](#额度与用量)
- [Sand Stream](#sand-stream)
- [设置](#设置)
- [备份与恢复](#备份与恢复)
- [数据与安全](#数据与安全)
- [兼容性](#兼容性)
- [常见问题](#常见问题)
- [命令](#命令)

## 主要功能

- 在 Cursor 侧栏集中管理多个账号。
- 通过浏览器授权添加支持自动续期的账号。
- 支持 Token、本机登录状态和 JSON 备份导入。
- 查看当前账号摘要以及 Auto、Other Models、Grok Bot 用量。
- 刷新单个账号或当前账号的套餐和额度信息。
- 切换 Cursor 当前登录账号，并在切换前检查可续期令牌。
- 为账号添加备注、复制 Token、打开控制台。
- 查询登录设备，并提交设备下线操作。
- 查看和调整账号的超额使用状态。
- 安装、检查和卸载 Sand Stream。
- 支持 Sand、Task、子代理和后台任务相关使用场景。
- 导入、预览和导出账号备份。

## 安装

### 从 VSIX 安装

1. 下载发布页中的 `.vsix` 文件。
2. 打开 Cursor 的扩展页面。
3. 点击扩展页面右上角的更多操作按钮。
4. 选择“从 VSIX 安装”。
5. 选择下载的 VSIX 文件并等待安装完成。
6. 按提示重新加载窗口。

安装完成后，点击活动栏中的 Cursor Manager 图标即可打开侧栏。

### 更新版本

安装新版 VSIX 前，建议先导出账号备份。直接安装新版通常会覆盖旧版本，但不会主动清空已有账号记录。

如果新版涉及 Sand 更新，应先在旧版本中卸载 Sand，完整退出 Cursor，再安装新版扩展并重新安装 Sand。

## 快速开始

推荐按以下顺序首次使用：

1. 打开 Cursor Manager。
2. 进入“工具箱”。
3. 使用“浏览器授权”添加账号。
4. 完成登录后回到 Cursor，等待账号出现在列表中。
5. 点击账号卡片上的刷新按钮读取额度。
6. 需要切号时点击切换按钮并确认。
7. 切换完成后完整退出 Cursor，再重新打开。

浏览器授权是推荐的账号添加方式。它能够获得完整的客户端登录凭据，可用于切号和自动续期。

## 界面说明

Cursor Manager 分为三个页签。

### 账号列表

用于查看当前账号、账号备注、套餐、用量和登录状态。

账号卡片顶部提供常用操作：

- 刷新账号信息。
- 切换为该账号。
- 复制该账号 Token。
- 从列表删除账号。

部分扩展操作会根据账号类型、套餐和当前状态显示，包括令牌续期、转换为可续期账号、控制台、登录设备、备注和超额设置。

### 工具箱

用于添加、备份和恢复账号，以及管理 Sand Stream：

- 浏览器授权。
- Token 导入。
- 导入本机登录状态。
- 导入账号备份。
- 导出账号备份。
- 刷新当前账号用量。
- 安装 Sand Stream。
- 卸载 Sand Stream。

### 设置页

用于调整自动续期、账号信息查询和高级路径选项。普通用户通常只需要保留默认设置。

## 添加账号

### 浏览器授权

这是推荐方式。

1. 进入“工具箱”。
2. 点击“浏览器授权”。
3. 在打开的隔离浏览器中登录 Cursor。
4. 页面出现授权按钮时完成授权。
5. 回到 Cursor，等待导入结果。

成功后，该账号通常支持：

- 正常切号。
- 手动续期。
- 后台自动续期。
- 额度查询。
- 登录设备查询。

请勿在授权过程中关闭浏览器或 Cursor。授权完成后，可自行关闭隔离浏览器。

### Token 导入

支持以下常见格式：

```text
userId::accessToken
```

```text
userId::accessToken::refreshToken
```

也可以粘贴完整的 `WorkosCursorSessionToken=...`。

三段式格式只有在第三段是真实、独立且不同于 Access Token 的 Refresh Token 时，才能作为可续期账号导入。

#### 不可续期令牌

如果导入的令牌没有独立 Refresh Token，扩展会显示“检测到不可续期令牌”。此时可以选择：

- “仅导入额度”：保存账号并查看 Auto、Other 和 Bot 用量，但不建议用它切号。
- “浏览器授权”：使用现有登录状态完成授权，获取适合客户端使用的完整登录凭据。
- “取消”：不保存本次导入。

仅额度账号不能保证正常发送消息，也不能自动续期。令牌失效后，需要重新授权。

### 导入本机

如果当前 Cursor 已经正常登录，可以使用“导入本机”将当前登录账号加入 Cursor Manager 列表。

此操作只添加账号记录，不会自动切换账号。

### 导入备份

选择 Cursor Manager 导出的 JSON 文件后，会先显示导入预览。确认前不会清空现有账号。

预览中会标明：

- 待导入账号数量。
- 新增账号数量。
- 将被更新的已有账号数量。

请只导入来源可信的备份文件。

## 账号管理

### 刷新账号

点击账号卡片上的刷新按钮，可以重新读取该账号的邮箱、套餐、用量、重置时间和超额状态。

刷新失败不代表账号记录已经丢失。常见原因包括网络不可用、令牌失效或“联网查询账号信息”被关闭。

### 切换账号

1. 在账号卡片上点击切换按钮。
2. 核对目标账号后确认。
3. 等待“切换成功”提示。
4. 点击“立即重启”，或者自行完整退出 Cursor 后重新打开。

仅执行“Reload Window”不足以完成切号，因为 Cursor 需要在完整启动时重新读取登录状态。

不建议切换标记为“无法续期”或“仅用于查看额度”的账号。这类账号可能在发送消息时出现登录错误。

### 复制 Token

复制操作会将账号登录凭据写入系统剪贴板。使用完成后建议及时覆盖剪贴板内容，不要将 Token 发送给他人或提交到 Git 仓库。

### 删除账号

删除操作只会移除 Cursor Manager 中的账号记录，不会自动退出 Cursor 当前已经登录的账号。

### 账号备注

可以为账号添加简短备注，例如“主力”“备用”或“工作账号”，方便区分多个相似邮箱。

### 控制台

控制台入口会在隔离浏览器中打开对应账号页面。该浏览器与日常浏览器数据分开，关闭窗口即可结束本次会话。

### 登录设备

登录设备页面用于查看账号当前会话，并可提交指定设备下线操作。下线可能需要一段时间才能完全生效。

请谨慎处理最后一个可用会话。将其下线后，账号可能需要重新完成浏览器授权。

### 令牌续期

只有通过浏览器授权获得完整凭据的账号才支持续期。

自动续期开启时，扩展会在令牌接近失效时尝试更新；也可以在账号操作中手动续期。仅额度账号不会执行自动续期。

## 额度与用量

### 顶部摘要

顶部区域显示当前账号和总体用量摘要。没有选中账号时，会提示先导入或探测本机账号。

### 账号用量

账号卡片可以显示：

- Auto：自动模型选择相关用量。
- Other Models：指定模型相关用量。
- Grok Bot：Bot 周期用量；没有独立额度时显示为不可用。
- 套餐名称和周期重置时间。

具体额度口径可能随 Cursor 套餐调整而变化，应以 Cursor 官方账户页面为准。

### 超额使用

支持查看和调整账号的超额使用状态。开启超额后，套餐内额度耗尽时可能继续产生额外费用。

提交前请确认账号和设置方向。Cursor Manager 不承担因超额设置产生的费用。

## Sand Stream

Sand Stream 是可选的客户端模式功能，不影响基础账号管理、备份和额度查询。

### 使用前提

- 当前版本已在 Cursor 3.18.9 上验证。
- Sand Stream 必须使用 HTTP/2。
- 安装和卸载可能需要管理员权限。
- 操作完成后必须完整退出并重新打开 Cursor。
- Cursor 更新后应重新检查 Sand 状态。

不同 Cursor 版本的内部结构可能变化。未明确验证的版本不应仅凭“已注入”状态判断为完全可用。

### 安装

1. 确认正在使用兼容的 Cursor 版本。
2. 确认客户端连接模式为 HTTP/2。
3. 打开“工具箱”。
4. 点击“安装 Sand Stream”。
5. 阅读确认信息并继续。
6. 完整退出 Cursor，再重新打开。
7. 回到 Cursor Manager 检查状态。

重复点击安装不会增加账号权益，也不用于解锁模型。如果状态异常，应先查看错误提示，不要连续重复安装。

### 卸载

1. 打开“工具箱”。
2. 点击“卸载 Sand Stream”。
3. 确认恢复操作。
4. 完整退出 Cursor，再重新打开。

卸载后建议再次打开 Cursor Manager 检查状态。Cursor 更新、重装或移动安装目录后，也应重新检查。

### Sand 与账号权限

Sand Stream 不会修改账号真实套餐，不会赋予 Team 或 Enterprise 身份，也不会让账号使用未获得权限的模型。

如果服务端返回登录或模型权限错误，应先检查账号登录状态、订阅和所选模型，而不是重复安装 Sand。

## 设置

### 自动续期

对通过浏览器授权获得完整凭据的账号进行定期检查，并在令牌临近失效时尝试更新。

关闭后，仍可在账号操作中手动续期。

### 联网查询账号信息

连接 Cursor 官方服务读取账号邮箱、套餐、额度、重置时间和超额状态。

关闭后，账号列表仍会保留，但额度和套餐信息不会自动更新。

### Cursor 路径

用于指定 Cursor 的应用资源目录。正常情况下保持为空，扩展会使用当前 Cursor 的安装位置。

只有自动识别失败或使用便携版、自定义安装目录时才需要填写。

### 浏览器授权客户端 ID（高级）

浏览器登录和令牌续期使用的客户端标识。普通用户应保持默认值；填写错误会导致浏览器授权或续期失败。

## 备份与恢复

### 导出备份

1. 打开“工具箱”。
2. 点击“导出备份”。
3. 在预览中核对账号。
4. 选择保存位置。

导出的 JSON 可能包含可用于登录的敏感凭据。请将它视为密码文件保管。

### 导入备份

1. 打开“工具箱”。
2. 点击“导入备份”。
3. 选择 JSON 文件。
4. 检查新增和更新预览。
5. 确认导入。

同一账号再次导入时，可能会更新已有记录，而不是新增重复账号。

## 数据与安全

- 账号列表和扩展设置保存在本机 Cursor 环境中。
- 查询额度、设备和账号状态时，需要连接 Cursor 官方服务。
- 浏览器授权使用独立浏览器环境，不复用日常浏览器配置。
- Token、Cookie 和账号备份都属于敏感凭据。
- 不要将 Token 粘贴到聊天、Issue、截图或公开仓库。
- 不要提交导出的账号 JSON。
- 不要使用来源不明的 Token 或备份文件。
- 如果 Token 曾经公开，应尽快让相关会话失效并重新登录。

## 兼容性

### Windows

Windows 是当前主要支持平台。账号管理、浏览器授权、切号、完整重启和 Sand 管理均按 Windows 环境设计。

### macOS

macOS 已包含常用路径、浏览器、重启和权限处理，但目前属于实验性支持。发布前建议在 Intel 与 Apple Silicon 设备上分别验证。

macOS 使用注意事项：

- 浏览器授权需要安装 Google Chrome、Microsoft Edge 或 Chromium。
- Sand 安装可能触发管理员密码提示。
- 修改 Cursor 应用内容可能受到 macOS 代码签名和系统安全策略影响。
- 如果 Cursor 安装在用户 Applications 目录或自定义位置，可能需要手动指定路径。

## 常见问题

### 一直显示 “Taking longer than expected”

先确认请求是否最终返回明确错误。如果始终没有结果，可能是 Cursor 的用户 Hook 在提交前阻塞。可以临时关闭 `beforeSubmitPrompt` 或 `UserPromptSubmit` Hook，完整重启 Cursor 后再次测试。

### 出现 “Sand traffic is not supported on this endpoint”

通常表示 Sand 请求没有通过所需的 HTTP/2 通道。确认客户端使用 HTTP/2，并完整重启 Cursor。切换模型不能解决该问题。

### 出现 “ERROR_NOT_LOGGED_IN”

当前账号登录凭据未被 Cursor 服务端接受。常见原因包括：

- 导入的是仅用于额度查询的网页令牌。
- Token 已失效。
- 缺少真实 Refresh Token。
- 切号后没有完整重启 Cursor。

建议重新使用“浏览器授权”添加账号。

### 为什么有些 Token 导入时会提示不可续期

因为这些 Token 没有提供独立的 Refresh Token。它们可以在有效期内查询部分账号信息，但不能保证稳定切号和自动续期。

### 为什么切号后仍显示原账号

切号后必须完整退出 Cursor，再重新打开。Reload Window 不会清除全部运行时登录缓存。

### 为什么看不到额度

检查以下项目：

1. “联网查询账号信息”是否开启。
2. 当前网络能否访问 Cursor 官方服务。
3. 账号 Token 是否有效。
4. 点击账号卡片上的刷新按钮重新读取。

### 浏览器授权没有打开

确认已安装 Google Chrome、Microsoft Edge 或 Chromium。macOS 仅安装 Safari 时，当前版本无法启动隔离浏览器授权。

### Cursor 更新后 Sand 状态异常

Cursor 更新可能改变兼容条件。不要直接重复安装；先卸载旧 Sand，完整重启，再根据当前扩展版本的兼容说明决定是否重新安装。

## 命令

可以在 Cursor 命令面板中搜索以下命令：

- `Cursor Manager: 打开控制面板`
- `Cursor Manager: 安装 Sand Stream`
- `Cursor Manager: 卸载 Sand Stream`

旧版命令仍保留兼容入口，但新用户应优先使用 Cursor Manager 命令。

## 使用声明

Cursor Manager 是本地账号管理工具，不提供 Cursor 账号、订阅、额度或模型权限。请仅管理属于你本人或已获授权的账号，并遵守 Cursor 的服务条款及所在地适用规则。

使用 Sand Stream 前，请确认当前 Cursor 版本与扩展版本兼容，并自行评估修改客户端文件带来的稳定性、更新和系统安全风险。

## License

Copyright (c) 2026 Ti. All rights reserved.

Cursor Manager is proprietary software distributed under a restricted binary license. Copying, redistribution, decompilation, disassembly, de-obfuscation, reverse engineering, automated analysis, and source reconstruction are prohibited unless the publisher grants prior written permission.

See `LICENSE.txt` for the complete license terms.
