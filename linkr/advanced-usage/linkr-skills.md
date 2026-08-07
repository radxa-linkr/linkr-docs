---
id: link-skills
title: 灵控 Skills 使用指南
sidebar_position: 8
---

# 灵控 Skills 使用指南

`linkr-skills` 是一个面向 AI Agent（OpenClaw）的标准化技能包，通过调用瑞莎灵控（Radxa Linkr）提供的标准 HTTP 接口（屏幕截图、键盘、鼠标、文本输入），实现对被控机的远程自动化操作。

适用于远程服务器管理、自动化测试、无人值守运维等场景。

项目源码：[linkr-skills](https://github.com/radxa-linkr/linkr-skills)

:::tip

- 本技能基于灵控标准的 HTTP 接口，接口协议与事件参数的详细说明请参阅 [开发者文档](./develop-guide)
- 涉及的相关文档：[访问令牌](./access-token)、[灵控 Web 使用指南](./usage)

:::

## 功能特性

| 功能 | 说明 |
| :--- | :--- |
| 屏幕截图 | 获取被控机实时屏幕图像，供 AI 模型分析决策 |
| 鼠标控制 | 支持绝对坐标 `[0.00, 1.00]` 和相对坐标（像素）两种模式 |
| 键盘模拟 | 完整的按键按下 / 释放控制，支持组合键 |
| 文本输入 | 支持自动分段，每 30 字符后暂停 1000ms 确保完整输入 |
| 延时控制 | 确保操作序列按预期顺序执行 |

## 系统架构

```text
┌─────────────┐      HTTP API      ┌─────────────┐      KVM Signal      ┌─────────────┐
│   OpenClaw  │ ◄────────────────► │    Linkr    │ ◄──────────────────► │   Target    │
│    (PC)     │                    │             │                      │   Machine   │
└─────────────┘                    └─────────────┘                      └─────────────┘

    HTTP interface (provided by Linkr):
    ├── Screenshot endpoint: /api/public/snapshot
    └── Control endpoint:   /api/public/control
```

## 前置条件

### 1. 获取 API Token

调用灵控公开 API 需要访问令牌（API Key）。请参考 [访问令牌](./access-token) 在灵控 Web 的「系统设置 → 访问令牌」中创建。

### 2. 配置环境变量

使用本技能前，必须设置以下环境变量：

- `Linkr_IP`：灵控设备 IP（如 `192.168.2.224`）
- `Linkr_TOKEN`：API Token

#### Bash

```bash
export Linkr_IP="192.168.x.x"
export Linkr_TOKEN="your_api_token"
```

#### PowerShell

```powershell
[System.Environment]::SetEnvironmentVariable("Linkr_IP", "192.168.x.x", "User")
[System.Environment]::SetEnvironmentVariable("Linkr_TOKEN", "your_api_token", "User")
```

:::warning

- 文档中的 `Linkr_IP`、`Linkr_TOKEN` 只是变量名说明，不会自动替换成真实值
- 真实值必须来自 OpenClaw 运行时能读取到的环境变量
- 修改环境变量后，需要重启 OpenClaw 或重新打开终端再执行

:::

## 安装到 OpenClaw

```bash
# 复制到 OpenClaw skills 目录
cp -r linkr-skills ~/.openclaw/skills/

# 验证安装
openclaw skills list
```

### 依赖

- `curl`：用于 HTTP 请求
- `python3` + `requests`：用于 Python 客户端（可选）

## API 接口

`linkr-skills` 调用以下两个接口，接口的请求方式、参数与响应说明请参阅 [开发者文档 - AI Agent 接口](./develop-guide)。

| 接口 | 方法 | 用途 |
| :--- | :--- | :--- |
| `/api/public/snapshot` | GET | 获取被控机实时屏幕截图（JPEG） |
| `/api/public/control` | POST | 下发键鼠、文本、延时等事件序列 |

```bash
# 截图
curl -X GET "http://${Linkr_IP}:80/api/public/snapshot" -H "Authorization: token ${Linkr_TOKEN}" -o screen.jpeg

# 控制
curl -X POST "http://${Linkr_IP}:80/api/public/control" \
  -H "Content-Type: application/json" \
  -H "Authorization: token ${Linkr_TOKEN}" \
  -d '{"events": [["text", "hello"], ["delay", 300]]}'
```

## 事件类型速查

每个事件是一个数组，第一个元素表示事件类型。各事件的参数详解与示例请参阅 [开发者文档 - 控制接口参数详解](./develop-guide)。

| 事件 | 格式 | 说明 |
| :--- | :--- | :--- |
| 键盘 | `["keyboard", "KeyA", true]` | 按下 / 释放按键 |
| 鼠标绝对坐标 | `["mouse_abs", 0, 0.5, 0.5, 0, 0]` | 移动到屏幕绝对坐标（0.00-1.00） |
| 鼠标相对坐标 | `["mouse_rel", 0, 100, 100, 0, 0]` | 相对当前位置移动指定像素 |
| 文本 | `["text", "hello"]` | 在当前光标位置输入文本 |
| 延时 | `["delay", 1000]` | 暂停指定毫秒数 |

:::warning

- 文本输入事件后**必须**添加暂停事件，确保长文本输入完整
- 文本长度约 30 字符时，建议暂停 **1000ms**
- 长文本必须分段输入，每 30 字符后暂停一次

:::

## 完整示例：在 OpenClaw 中使用

在 OpenClaw 对话中直接输入自然语言指令，AI Agent 会自动加载 `linkr-skills` 技能，将指令翻译为事件序列并下发到被控机。

**用户输入**：

```text
打开 Chrome 浏览器并访问网站 https://radxa.com
```

**Agent 执行流程**：

1. 加载 `linkr-skills` 技能，读取环境变量 `Linkr_IP` 和 `Linkr_TOKEN`
2. 调用截图接口确认当前被控机屏幕状态
3. 生成事件序列，通过控制接口下发

**下发的事件序列**：

```json
{
  "events": [
    ["keyboard", "MetaLeft", true],
    ["keyboard", "KeyR", true],
    ["delay", 50],
    ["keyboard", "KeyR", false],
    ["keyboard", "MetaLeft", false],
    ["delay", 500],
    ["text", "chrome"],
    ["delay", 300],
    ["keyboard", "Enter", true],
    ["keyboard", "Enter", false],
    ["delay", 3000],
    ["mouse_abs", 0, 0.5, 0.08, 0, 0],
    ["delay", 200],
    ["text", "https://radxa.com"],
    ["delay", 1000],
    ["keyboard", "Enter", true],
    ["keyboard", "Enter", false]
  ]
}
```

**步骤分解**：

1. 按下 `Win+R` 打开运行对话框
2. 输入 `chrome` 并按回车启动浏览器
3. 等待 3 秒，等待浏览器启动完成
4. 移动鼠标到地址栏（顶部居中位置）
5. 输入 `https://radxa.com`
6. 暂停 1000ms，确保文本输入完整
7. 按回车跳转页面

## 辅助脚本

`linkr-skills` 提供了 Bash 和 Python 两套辅助脚本，便于快速调用。

### Bash 快速调用

```bash
# 发送控制指令
./scripts/send_control.sh '{"events":[["text","hello"],["delay",300]]}'

# 获取截图
curl -X GET "http://${Linkr_IP}:80/api/public/snapshot" -H "Authorization: token ${Linkr_TOKEN}" -o screen.jpeg
```

### Python 客户端（可选）

```python
from scripts.linkr_client import LinkrClient

client = LinkrClient()

# 获取截图
client.screenshot("desktop.jpeg")

# 输入文本（自动分段：每30字符后暂停1000ms）
client.text("This is a long text that will be automatically split into chunks...")

# 组合键 Win+R
client.key_combo("MetaLeft", "KeyR")

# 点击屏幕中心
client.click(0.5, 0.5)
```

`linkr_client.py` 也支持命令行直接调用：

```bash
# 输入文本
python linkr_client.py text "Hello World"

# 通过 Win+R 运行命令
python linkr_client.py run notepad

# 点击指定位置（绝对坐标 0-1）
python linkr_client.py click 0.5 0.5

# 发送组合键
python linkr_client.py combo MetaLeft KeyR
```

## 最佳实践

### 1. 坐标定位

- 优先使用 `mouse_abs`（绝对坐标），取值范围 `[0.00, 1.00]` 可自适应不同分辨率
- 关键操作前先截图确认当前屏幕状态
- 使用 AI 视觉分析进行 UI 元素定位

### 2. 时序控制（重要）

| 场景 | 建议延时 | 说明 |
| :--- | :--- | :--- |
| 短文本输入后（少于 10 字符） | 300ms | 简单文本 |
| 中等文本输入后（10-30 字符） | 500-800ms | 例如 URL |
| **长文本输入后（约 30 字符）** | **1000ms** | 必须，确保输入完整 |
| 启动应用后 | 2000-5000ms | 取决于应用启动时间 |
| 页面加载后 | 1000-3000ms | 取决于网络状况 |
| 连续按键之间 | 50-100ms | 防止丢键 |

### 3. 长文本输入策略

超过 30 字符的文本必须分段输入：

```json
{
  "events": [
    ["text", "This is a long text that needs"],
    ["delay", 1000],
    ["text", " to be split into multiple parts"],
    ["delay", 1000],
    ["text", " to ensure complete input."],
    ["delay", 1000]
  ]
}
```

使用 Python 客户端时，`client.text()` 会自动分段，无需手动处理。

### 4. 按键操作规则

- 按下与释放必须成对出现：`[key, true]` 和 `[key, false]`
- 修饰键（Ctrl/Alt/Shift/Win）先按下，再按主键
- 释放顺序相反：先释放主键，再释放修饰键

## 常见问题排查

| 现象 | 可能原因 | 解决方法 |
| :--- | :--- | :--- |
| 截图失败 | 网络问题 / 灵控未运行 | 检查 `Linkr_IP` 连通性 |
| 控制无响应 | 事件格式错误 | 检查 JSON 数组长度与类型 |
| 坐标不准确 | 分辨率变化 | 使用 `mouse_abs` 绝对坐标 `[0.00, 1.00]` |
| 文本乱码 | 输入法状态不对 | 先切换为英文输入法 |
| 文本输入不完整 | 延时不足 | 每 30 字符后添加 1000ms 暂停 |
| 操作顺序错乱 | 延时不足 | 增加 `delay` 时长 |
| 长文本被截断 | 缓冲区溢出 | 每 30 字符分段输入 |
