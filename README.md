# embedded-software-engineer-agent

[![Release](https://img.shields.io/github/v/release/YWH-YNOT/embedded-software-engineer-agent)](https://github.com/YWH-YNOT/embedded-software-engineer-agent/releases)
[![License](https://img.shields.io/github/license/YWH-YNOT/embedded-software-engineer-agent)](LICENSE)
![Docs](https://img.shields.io/badge/docs-zh--CN-0A7EA4)

一个面向 Codex / ChatGPT / Claude 的嵌入式软件工程 Agent 开源模板仓库。重点不是“自动写完整工程”，而是把嵌入式项目约束成可审查、可追问、可验证、可复用的工作流。

## 先看这里

30 秒开始：

1. 打开 [`AGENTS.md`](AGENTS.md)。
2. 把它作为 Codex 运行时入口，必要时再补充 `agent/` 展开规则。
3. 先填写 [`templates/project_intake.md`](templates/project_intake.md) 和 [`templates/hardware_intake.md`](templates/hardware_intake.md)。
4. 从 [`examples/`](examples/) 里选一个最接近你场景的示例照着走。

运行时与文档分工：

- [`AGENTS.md`](AGENTS.md)：运行时入口，短、硬、直接约束 Agent 行为
- [`agent/`](agent/)：展开版规则、工作流、追问机制、输出契约
- [`.agents/skills/`](.agents/skills/)：可复用的技能工作流，面向具体任务

## 项目是什么

这是一个“嵌入式软件工程师 Agent”的模板仓库，服务对象是想把 AI 用在真实嵌入式项目里的开发者，而不是想看一个营销化 Prompt 收藏夹的人。

仓库核心产物是：

- 运行时入口：`AGENTS.md`
- 展开规则：`agent/`
- 结构化模板：`templates/`
- 可触发技能：`.agents/skills/`
- 场景示例：`examples/`

## 解决什么问题

- 防止 AI 在资料不足时直接乱写寄存器、时钟、引脚和初始化代码
- 强制 AI 先做资料审查，再决定是否能进入模块开发
- 强制 AI 主动追问真正影响驱动写法和验证路径的关键问题
- 强制 AI 一次只推进一个未验证模块
- 强制 AI 在模块完成前先给出验证方法、成功判据和失败排查路径
- 为 Codex / GitHub 协作提供更稳定的入口、模板和示例结构

## 不解决什么问题

- 没有原理图、没有芯片手册、没有官方资料，却要求直接生成完整工程
- Linux BSP / 驱动框架、复杂 GUI、多核异构系统、射频协议栈
- 大型应用层业务框架
- “万能自动开发器”式的一步到位承诺

## 适合谁

- 工程学生、初级工程师、独立开发者
- 用 Codex / ChatGPT / Claude 协助做单 MCU / 单 SoC 项目的开发者
- 希望把 Prompt、Workflow、模板和示例沉淀成 GitHub 可协作仓库的人
- 想把后续能力扩成 skill pack 体系，但当前先做 P0-P1 的维护者

## 推荐使用流程

1. 用 [`AGENTS.md`](AGENTS.md) 启动 Agent。
2. 根据任务类型加载对应 skill，例如：
   - 项目接入：[`project-intake`](.agents/skills/project-intake/SKILL.md)
   - UART bring-up：[`uart-bringup`](.agents/skills/uart-bringup/SKILL.md)
   - I2C bring-up：[`i2c-bringup`](.agents/skills/i2c-bringup/SKILL.md)
   - SPI bring-up：[`spi-bringup`](.agents/skills/spi-bringup/SKILL.md)
   - 单模块调试：[`module-debug-checklist`](.agents/skills/module-debug-checklist/SKILL.md)
3. 用 `templates/` 收集项目信息和模块计划。
4. 用 `examples/` 对照输出结构，确认当前回复是否符合仓库规则。
5. 对规则或示例有问题时，优先用 Issue / Discussion 反馈，而不是在 PR 中直接扩散新规则。

## 仓库结构

```text
embedded-software-engineer-agent/
├─ AGENTS.md
├─ README.md
├─ LICENSE
├─ CODE_OF_CONDUCT.md
├─ SECURITY.md
├─ CHANGELOG.md
├─ CONTRIBUTING.md
├─ agent/
│  ├─ system.md
│  ├─ workflow.md
│  ├─ rules.md
│  ├─ questioning.md
│  └─ output_contract.md
├─ .agents/
│  └─ skills/
│     ├─ project-intake/
│     ├─ uart-bringup/
│     ├─ i2c-bringup/
│     ├─ spi-bringup/
│     └─ module-debug-checklist/
├─ templates/
├─ examples/
├─ docs/
└─ .github/
   ├─ ISSUE_TEMPLATE/
   ├─ workflows/
   ├─ CODEOWNERS
   └─ release.yml
```

## 最小示例

最小输入可以短到这个程度：

```text
平台：STM32F103C8T6
目标：先做 UART1 日志口
资料：原理图、引脚表、数据手册、STM32Cube HAL
约束：不要直接写整包工程，先审资料，缺信息就追问
```

预期 Agent 输出不是代码洪流，而是：

1. 当前处于哪个阶段
2. 已确认了什么
3. 还缺什么关键资料
4. 当前只处理哪个模块
5. 如何验证这个模块是否真的可用

可直接对照的示例：

- [`examples/stm32_uart_minimal/`](examples/stm32_uart_minimal/)
- [`examples/stm32_i2c_sensor/`](examples/stm32_i2c_sensor/)
- [`examples/stm32_spi_memory/`](examples/stm32_spi_memory/)
- [`examples/multi_module_integration/`](examples/multi_module_integration/)
- [`examples/insufficient_info_case/`](examples/insufficient_info_case/)

## 支持范围

当前仓库第一版聚焦：

- 单 MCU / 单 SoC
- GPIO / UART / SPI / I2C / Timer / PWM / ADC / DMA / EXTI / Watchdog / PSRAM
- 裸机或轻量 RTOS
- 有原理图、芯片手册、官方 SDK/HAL、官方例程可参考的项目
- 以“模块化开发 + 单模块验证 + 最后集成”为主线

## 非目标范围

当前不重点支持：

- Linux BSP / 驱动框架
- 复杂 GUI
- 多核异构系统
- 射频协议栈
- 没有原理图和官方资料却要求直接生成完整工程
- 大型应用层业务框架

## 如何提 Issue / 如何参与贡献

- 规则、模板、示例、skill 有问题：请使用 Issue 模板
- 使用问题、选型讨论、工作流争议：建议优先走 Discussions
- 安全问题：不要公开提 Issue，参见 [`SECURITY.md`](SECURITY.md)
- 贡献规则：参见 [`CONTRIBUTING.md`](CONTRIBUTING.md)
- 不能通过本地文件完成的 GitHub 设置：参见 [`docs/github_settings_checklist.md`](docs/github_settings_checklist.md)

如果你第一次打开这个仓库，建议按这个顺序阅读：

1. [`AGENTS.md`](AGENTS.md)
2. [`README.md`](README.md)
3. [`agent/system.md`](agent/system.md)
4. [`templates/project_intake.md`](templates/project_intake.md)
5. [`examples/insufficient_info_case/expected_output.md`](examples/insufficient_info_case/expected_output.md)
