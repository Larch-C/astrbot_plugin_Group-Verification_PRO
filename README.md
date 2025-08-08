# 🤖 QQ群成员动态数学题验证插件

<div align="center">
  
![Version](https://img.shields.io/badge/version-1.0.4-blue.svg)  
![License](https://img.shields.io/badge/license-MIT-green.svg)  
![Platform](https://img.shields.io/badge/platform-AstrBot-purple.svg)  

一个智能、高度可定制的QQ群验证工具，通过动态数学题有效拦截机器人，保护您的群聊安宁  

[功能简介](#features) •  
[安装方法](#installation) •  
[配置说明](#configuration) •  
[使用教程](#usage) •  
[常见问题](#faq) •  
[更新日志](#changelog) •  
[作者及许可](#author)

</div>

---

<a id="features"></a>
## ✨ 功能简介

本插件为 AstrBot 提供了强大的新成员智能验证功能，能有效过滤广告机器人和可疑用户，全面提升群聊质量。

- 🧠 **动态数学题验证**  
  新成员需回答随机生成的 100 以内加减法问题，代替呆板的静态关键词，极大提升验证强度。  
- 🔄 **错误重试机制**  
  回答错误后自动生成新题并重置计时，给予真实用户改正机会。  
- ⏱️ **多段式时间控制**  
  自定义验证总时长、超时前警告时机、失败后踢出延迟等。  
- 🎨 **完全可定制化消息**  
  欢迎语、错误提示、超时警告、踢出公告等均可自定义，支持丰富变量。  
- 🔍 **实时监测**  
  自动检测新成员入群并立即发起验证流程。  
- 💬 **动态变量支持**  
  支持 `{at_user}`、`{member_name}`、`{question}`、`{timeout}`、`{countdown}` 等多种占位变量。  

---

<a id="installation"></a>
## 📥 安装方法

<details>
<summary>展开查看详细安装步骤</summary>

1. 打开 AstrBot 插件管理界面。  
2. 在插件市场搜索 `astrbot_plugin_Group-Verification_PRO` 并安装。  
3. 安装完成后，进入插件配置页面进行参数设置。  
4. 保存配置并重启机器人，或在插件管理中手动重载本插件。  
5. （可选）下载 release 包，解压后放入 `astrbot/plugins` 目录，再重启机器人。  

</details>

---

<a id="configuration"></a>
## ⚙️ 配置说明

### v1.0.1 配置项

| 配置项                        | 类型    | 说明                                               |
| ----------------------------- | ------- | -------------------------------------------------- |
| `verification_timeout`        | int     | 验证总超时时间（秒），默认 `300`。                  |
| `kick_countdown_warning_time` | int     | 超时前发送警告秒数，设为 `0` 可禁用，默认 `60`。     |
| `kick_delay`                  | int     | 发送“验证超时”消息后延迟踢出秒数，默认 `5`。        |
| `new_member_prompt`           | string  | 新成员入群时发送的欢迎及验证提示语。               |
| `welcome_message`             | string  | 验证成功后的祝贺提示语。                           |
| `wrong_answer_prompt`         | string  | 回答错误后的提示语（自动附带新题）。               |
| `countdown_warning_prompt`    | string  | 即将超时前的警告消息。                             |
| `failure_message`             | string  | 验证失败前的“最后通牒”消息。                       |
| `kick_message`                | string  | 成员被踢出后在群内的公开通知。                     |

### 支持的模板变量

- `{at_user}` — @目标用户 的 CQ 码，例如 `[CQ:at,qq=12345]`  
- `{member_name}` — 用户的群名片或 QQ 昵称  
- `{question}` — 随机生成的数学题，例如 `76 + 24 = ?`  
- `{timeout}` — 验证超时时长（分钟）  
- `{countdown}` — 踢出前的延迟秒数（即 `kick_delay` 值）  

---

<a id="usage"></a>
## 📝 使用教程

<table>
  <tr>
    <td width="50%">
      <h3>1️⃣ 启用与配置</h3>
      <p>在 AstrBot 插件页启用本插件，填写提示语、时间参数等配置。</p>
    </td>
    <td width="50%">
      <h3>2️⃣ 新人入群验证</h3>
      <p>新成员入群后，机器人自动 @ 该用户并发送入群提示及一道数学题。</p>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>3️⃣ 回答与重试</h3>
      <p>用户需在规定时间内 @ 机器人回复正确答案；答错后重置计时并生成新题。</p>
    </td>
    <td width="50%">
      <h3>4️⃣ 超时与踢出</h3>
      <p>未完成验证会收到超时警告，最终超时将发送失败消息并在延迟后踢出。</p>
    </td>
  </tr>
</table>

---

<a id="faq"></a>
## ❓ 常见问题

<details>
<summary><b>为什么用户回答数字后机器人没有响应？</b></summary>
<p>请确认用户在回复中正确 <b>@ 了机器人</b>，否则机器人无法识别消息。</p>
</details>

<details>
<summary><b>机器人没有对新成员发起验证？</b></summary>
<p>检查机器人是否为管理员，且 AstrBot 的事件通知权限正常，未被QQ风控或屏蔽。</p>
</details>

<details>
<summary><b>可以调整数学题难度吗？</b></summary>
<p>当前版本固定为 100 以内加减法，足以区分真实用户与脚本；未来版本或支持难度配置。</p>
</details>

---

<a id="changelog"></a>
## 📋 更新日志

### v1.0.4 - 2025-08-08
 * [关键修复] 解决了因 from astrbot.api.bot import Bot 语句在部分 AstrBot 框架版本中不兼容而导致的 ModuleNotFoundError 问题。
 * [兼容性] 通过移除该导入和相关的类型提示，确保了插件在不同 AstrBot 版本中的加载成功率，提升了插件的普适性。
### v1.0.3 - 2025-08-07
 * [关键修复] 修复了 _timeout_kick 函数中存在一个不完整代码行而导致的 SyntaxError，该错误会使插件加载失败。
### v1.0.2 - 2025-08-07
 * [健壮性] 重构消息格式化逻辑：引入了安全的字符串格式化方法。现在，即使用户自定义的消息模板缺少某些占位符（如 {member_name}），插件也不会因 KeyError 而崩溃。
 * [健壮性] 优化答案提取算法：不再简单地提取消息中出现的第一个数字。新逻辑会智能地提取用户回复中的最后一个数字作为答案，显著提高了在复杂回复（如 “答案是15”）中的识别准确率。
 * [可维护性] 移除平台硬编码：重构了踢出流程，不再硬编码 aiocqhttp 平台。通过在任务创建时动态传递 bot 实例，为未来支持其他 OneBot 兼容的平台适配器打下基础。

### v1.0.1 (2025-08-07)

- 🚀 **验证方式升级**：从静态关键词验证升级为 100 以内动态数学题验证  
- 🔔 **高级控制能力**：新增验证超时前警告、错误重试、自定义踢出延迟等功能  
- 🏗️ **代码重构**：优化验证逻辑与状态管理，提升稳定性与可维护性  

---

<a id="author"></a>
## 👤 作者及许可

- **作者**：huotuo146  
- 🌐 GitHub：[huntuo146](https://github.com/huntuo146)  
- 📧 Email：[2996603469@qq.com](mailto:2996603469@qq.com)  
- 🔗 项目地址：[astrbot_plugin_Group-Verification_PRO](https://github.com/huntuo146/astrbot_plugin_Group-Verification_PRO)  

本项目采用 [MIT 许可证](LICENSE) 开源。  

---

<div align="center">
<p>如果您觉得这个插件有用，请考虑给项目一个 ⭐Star！</p>
<p>有问题或建议？欢迎 <a href="https://github.com/huntuo146/astrbot_plugin_Group-Verification_PRO/issues/new">提交 Issue</a></p>
<sub>Made with ❤️ by huotuo146</sub>
</div>
