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

Cursor Manager 是一款运行在 Cursor 侧栏中的账号管理扩展。它将多账号、额度、登录设备、客户端登录状态、Sand Stream 和本地 BYOK 路由集中到一个界面中。

扩展不会为账号增加原本不存在的订阅权益，也不会解锁 Cursor 官方付费模型。BYOK 的“Ultra”仅是本地兼容响应，用于让 Cursor 客户端展示并调用用户自己配置的 Provider；成本、额度和模型权限始终由该 Provider 决定。

## 目录

- [主要功能](#主要功能)
- [安装](#安装)
- [快速开始](#快速开始)
- [界面说明](#界面说明)
- [添加账号](#添加账号)
- [账号管理](#账号管理)
- [额度与用量](#额度与用量)
- [Sand Stream](#sand-stream)
- [BYOK](#byok)
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
- 在独立页签管理 BYOK Provider、模型、推理参数、Search 和 Fetch。
- 支持 Anthropic、OpenAI Chat、OpenAI Responses 与 Google Gemini 兼容接口。
- 使用 VS Code SecretStorage 保存 Provider、Search 与 Fetch 密钥。
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

Cursor Manager 分为四个页签：账号列表、工具箱、BYOK 和设置。

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

用于调整自动续期、账号信息查询、切号方式和高级路径选项。普通用户通常只需要保留默认设置。

### BYOK 页

位于“工具箱”和“设置”之间，用于安装本地路由补丁、启动回环服务、独立切换 BYOK、维护 Provider 与模型。网页搜索与读取在当前版本隐藏。Sand 在“工具箱”中拥有自己的独立开关；两个开关都开启时，选择自定义模型走 BYOK，选择其他模型走 Sand。

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
3. 等待切换完成的提示。

默认开启“无感换号”，切换会立刻生效，不需要重启。Cursor 设置界面里显示的账号邮箱是缓存值，要等下一次完整重启才会刷新，功能本身不受影响。

关闭“无感换号”，或开启“切号时重置机器码”时，会出现重启提示，此时点击“立即重启”或自行完整退出 Cursor 后重新打开。仅执行“Reload Window”不足以完成切号，因为 Cursor 需要在完整启动时重新读取登录状态。

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

Grok Bot 进度条下方会直接显示本地重置日期和剩余时间。倒计时每分钟在本地更新，不额外请求接口；服务端时间已过但尚未刷新时显示“等待刷新重置时间”，不会直接认定额度已重置。Bot 使用自己的周期时间，与套餐账单周期分开。

具体额度口径可能随 Cursor 套餐调整而变化，应以 Cursor 官方账户页面为准。

### 超额使用

支持查看和调整账号的超额使用状态。开启超额后，套餐内额度耗尽时可能继续产生额外费用。

提交前请确认账号和设置方向。Cursor Manager 不承担因超额设置产生的费用。

## BYOK

BYOK 将 Cursor 的指定 Agent、模型列表、Rules、摘要和必要兼容请求路由到本机 `127.0.0.1:39831`，再由用户配置的 Provider 完成推理。服务不监听局域网地址。

### 支持的 Provider

- Anthropic Messages API。
- OpenAI Chat Completions 兼容 API。
- OpenAI Responses 兼容 API。
- Google Gemini API。
- 自定义 Base URL、Bearer Token / API Key、HTTP 代理与附加请求头。

模型配置支持 Agent、图片、Cmd+K、Max Mode、Sandbox、Fast、Thinking、输出上限、1M Context，以及 Grok 4.6 的 500K Context。Edit 面板可以配置 Reasoning / Effort、Thinking、Budget、Context 与 Fast 变体。

1M Context 只声明模型容量并控制本地上下文计数与自动压缩，不会自动发送历史 `context-1m-2025-08-07` Beta Header。Fable 5.1 等原生 1M Claude 模型直接使用普通 Messages API；若某个旧版第三方接口明确要求特殊 Header，可在服务商“自定义请求头”中显式配置。

### 首次使用

1. 打开 Byok 页，安装“Byok 路由补丁”，不需要安装 Sand。
2. 补丁完成后等待自动保存和重启 Cursor，无需再次点击重启。
3. 新增模型服务商，填写接口地址与凭据。无需先保存，即可点击“获取模型”；已保存凭据会在展开服务商时读入密码框，小眼睛用于查看或隐藏。
4. 新增模型，或从服务商实际返回的模型列表中选择。模型旁的搜索按钮也只查询该服务商，搜索词在返回列表中筛选，不使用内置总目录；获取模型不会保存草稿。
5. 保存配置并启动本地服务。
6. 开启 BYOK 接管。

“Byok 本地服务”负责在 `127.0.0.1:39831` 接收 Cursor 的自定义模型请求并转发给当前 Provider；它不是第二个路由开关。点击“停止”会在同一次操作中关闭 BYOK 接管、结束本窗口或其他 Cursor 窗口持有的本地服务，Sand 状态不变。

路由补丁只需在首次安装或 Cursor 更新后重新安装。日常开关 BYOK 或 Sand 只会原子更新本地路由配置，不会重复修改 Cursor 文件。

Sand 与 BYOK 的安装、升级和卸载统一使用隐藏助手自动重启，仅在实际文件变更成功后触发。Windows 通过 WMI 创建独立助手，避免控制台黑框和助手随扩展宿主退出；重新启动时直接打开 Cursor GUI 并传入当前工作区。助手就绪后才请求 Cursor 正常退出；保存被取消、系统阻止助手或窗口未退出时会保留窗口并说明原因。日常开关和无文件变更的操作不重启。

### Ultra 兼容边界

BYOK 开启时，本地服务会返回 Ultra 形态的套餐兼容数据，让 Cursor 客户端开放本地 Provider 所需的界面路径。这不等于获得 Cursor 官方 Ultra，不会生成官方额度、绕过服务端鉴权或授权使用未购买的 Cursor 模型。

### 与 Sand 共存

BYOK 与 Sand 可以单独安装、开启和卸载，没有固定安装顺序。Sand 自带独立开关读取器；BYOK 自带自定义模型入口。卸载 Sand 仅撤销 Sand 标记，卸载 BYOK 按本功能的局部修改记录撤销，不再临时卸载、重装另一个功能。旧 BYOK 备份在内存中重现已知变换后局部恢复，无法唯一定位时保留备份并停止。

日常界面刷新和开关读取内存状态，不扫描客户端大文件。后台首次检查、安装/卸载后的检查、检测到文件元数据变化，或主动点击“检查补丁状态”时才进行深度检查。物理安装和卸载仍需读取并校验涉及的客户端文件，不能与日常开关耗时等同。

- BYOK 开启且 Sand 开启：自定义模型走 BYOK，其他模型走 Sand。
- 仅 BYOK 开启：模型列表只提供已配置的自定义模型，请求走 BYOK。
- 仅 Sand 开启：保持 Sand Stream 路由，BYOK 不接管请求。
- 两者都关闭：恢复 Cursor 官方路由。

BYOK 的会话 blob ID 与内容存储采用 Cursor 原生格式：ID 使用原始 SHA-256 字节，JSON/Protobuf 使用原始内容字节，因此同一会话可以在 BYOK 与 Sand 模型之间切换。旧版 BYOK 生成的 44 字节 Base64 文本 ID 会在该会话下一次进入 BYOK 时完整校验并迁移为原生格式；迁移数据不完整时会停止写回，避免进一步损坏会话。已经被旧版 UTF-8 有损转换为替换字符的 ID 无法反推出原哈希，只能保留现有可见记录并另行抢救。

这两个开关互不代替。关闭 Sand 只保留兼容补丁并即时停止 Sand 路由；关闭 BYOK 只停止自定义模型接管，不会关闭 Sand。工具箱中的“彻底移除 Sand 兼容补丁”和 BYOK 页中的“卸载客户端路由补丁”才会修改 Cursor 文件。

卸载 BYOK 路由补丁不会删除 Provider 元数据、模型配置或 SecretStorage 中的密钥。旧 CCursor 同类补丁只在存在可验证备份时恢复；发现无备份的未知或残缺补丁会停止操作。

BYOK 的模型服务不依赖 Sand，也不继承 Sand 的固定版本适配要求。接入 Cursor 原生聊天/Agent 的路由补丁仍依赖 Cursor 内部入口与协议；内部结构发生变化时可能需要适配，不能承诺不受任何 Cursor 版本影响。升级到本次独立补丁实现后，各自升级需要使用的补丁并完整重启一次，顺序不限。

## Sand Stream

Sand Stream 是可选的客户端模式功能，不影响基础账号管理、备份和额度查询。

### 使用前提

- 当前 Sand 补丁适用于 Cursor 3.18.9 和 3.18.25；其他版本会继续执行唯一锚点预检，未完整命中时拒绝写入。
- Sand Stream 必须使用 HTTP/2。
- 安装和卸载可能需要管理员权限。
- 安装和卸载完成后会自动保存并重启 Cursor；保存被取消时可稍后自行重启。
- Cursor 更新后应重新检查 Sand 状态。
- 安装会同时保留 Task、子代理与 Cursor Rules，并修复 Agent Shell 的工作区初始目录；未选择 Skill 时不会加入或显示全局 Skills，用户明确选择后仅加载所选 Skill，并在 Context Usage 中单独统计。
- 选择带 1M 上下文的模型变体时，Sand 会沿用该选择更新上下文用量分母与自动摘要阈值；普通变体仍使用模型原有上限。
- Grok 4.6 在 Cursor 3.18.9/3.18.25 未提供 context 参数时会补入已验证的 500K 上限；若请求已显式选择 context，则始终以显式值为准。
- `push_req_context` 等待上限会从10秒缩短到200毫秒；安装器会在写入前后检查补丁是否完整。

不同 Cursor 版本的内部结构可能变化。未明确验证的版本不应仅凭“已注入”状态判断为完全可用。

### 安装

1. 确认正在使用兼容的 Cursor 版本。
2. 确认客户端连接模式为 HTTP/2。
3. 打开“工具箱”。
4. 点击“安装 Sand 兼容补丁”。
5. 阅读确认信息并继续。
6. 等待自动保存并重新打开 Cursor。
7. 回到 Cursor Manager，确认状态为“Stream+Task+Rules 已齐”。

重复点击安装不会增加账号权益，也不用于解锁模型。如果状态异常，应先查看错误提示，不要连续重复安装。

### 关闭或彻底移除

1. 打开“工具箱”。
2. 日常停用直接关闭 Sand Stream 开关，立即生效且无需重新修改文件。
3. 确定以后不再使用时，点击“彻底移除 Sand 兼容补丁”。
4. 确认恢复操作后，等待自动保存并重新打开 Cursor。

彻底移除后建议再次打开 Cursor Manager 检查状态。Cursor 更新、重装或移动安装目录后，也应重新检查。

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

### 无感换号

默认开启。切号后通过 Cursor 登录深链让新账号立刻生效，不重启也不重载窗口。

关闭后，切号回到写入登录态加完整重启的流程。深链投递失败时也会自动回退到重启提示，不会切到一半卡住。

### 切号时重置机器码

默认关闭。开启后，每次切号会在 Cursor 完全退出之后重置本机机器码，用于避免多个账号被 Cursor 关联。

机器码只有在冷启动时才会重新读取，因此开启该项后切号一律走完整重启，无感换号不生效。

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
- BYOK Provider、Search 和 Fetch 凭据写入 VS Code SecretStorage；JSON 配置只保留非敏感元数据。
- BYOK 路由注入不会采集或转发提示词、模型响应与请求头到遥测 Collector。
- 不要将 Token 粘贴到聊天、Issue、截图或公开仓库。
- 不要提交导出的账号 JSON。
- 不要使用来源不明的 Token 或备份文件。
- 如果 Token 曾经公开，应尽快让相关会话失效并重新登录。

## 兼容性

### Windows

Windows 是当前主要支持平台。账号管理、浏览器授权、切号、完整重启、Sand 与 BYOK 路由管理均按 Windows 环境设计；VSIX 内含 x64 与 arm64 的 BYOK 原生 Markdown 模块。

### macOS

macOS 已包含常用路径、浏览器、重启、权限处理以及 Intel / Apple Silicon 的 BYOK 原生 Markdown 模块，但目前属于实验性支持。

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
- 关闭了无感换号，且切号后没有完整重启 Cursor。

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

### BYOK 开启后仍走官方或 Sand

确认 BYOK 页中的“客户端路由补丁”为已安装、本地服务为运行中，并在安装补丁后完整重启过 Cursor。自定义模型只走 BYOK；未配置为 BYOK 的模型在 Sand 开启时走 Sand、Sand 关闭时走官方。Cursor 更新会替换内部文件，此时需要重新检查并升级两个兼容补丁。

### BYOK 会不会消耗 Cursor 官方额度

选择已配置的 BYOK 模型时，推理请求发送到用户配置的 Provider，消耗该 Provider 的配额；选择其他模型时则按 Sand 独立开关走 Sand 或 Cursor 官方路由。账号、市场和其他未纳入 BYOK 的官方请求仍可能访问 Cursor 服务。

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

## 致谢

Cursor Manager 的 BYOK 服务与路由实现参考并改造自 [CCursor / Cursor++](https://github.com/CometixSpace/CCursor)。本项目的发行许可仅适用于 Cursor Manager 自有代码；所使用的第三方依赖仍分别遵循其各自许可。
