# embedded-software-engineer-agent

[![Release](https://img.shields.io/github/v/release/YWH-YNOT/embedded-software-engineer-agent)](https://github.com/YWH-YNOT/embedded-software-engineer-agent/releases)
[![License](https://img.shields.io/github/license/YWH-YNOT/embedded-software-engineer-agent)](LICENSE)
![Docs](https://img.shields.io/badge/docs-zh--CN-0A7EA4)

一个面向 Codex / ChatGPT / Claude 的嵌入式软件工程师 Agent 规则仓库。

这个项目不是“让 AI 一次性吐出完整工程”的代码生成器，而是一套受控、可审查、可复用的工作规则。它要求 AI 先审资料、先追问关键缺失信息、按模块推进开发、逐模块验证，最后才进入系统集成与回归测试。

## 项目简介

本仓库提供四类核心内容：

- Prompt：约束 AI 的角色、目标、边界与禁止行为
- Workflow：把嵌入式项目拆成可管控的阶段
- Templates：用于收集项目资料、制定模块计划、记录调试与集成结果
- Examples：演示 Agent 如何在真实约束下工作，而不是直接“拍脑袋写代码”

文档以中文为主，必要处保留英文术语。

## 这个 Agent 解决什么问题

- 防止 AI 在资料不全时直接乱写驱动、寄存器配置或初始化代码
- 强制 AI 优先依据官方参考手册、数据手册、官方 SDK/HAL、官方例程
- 强制 AI 明确指出缺失信息，并提出少量但关键的问题
- 把项目拆成可独立验证的模块，而不是一次性生成整包工程
- 在每个模块完成后先给出验证方法、测试清单、成功判据、失败排查路径
- 在所有模块验证通过后再做系统集成、回归测试与风险收敛

## 不解决什么问题

- 没有原理图、没有芯片手册、没有官方资料，却要求直接生成完整可用工程
- Linux BSP、复杂驱动框架、复杂 GUI、射频协议栈等超出 V1 范围的系统级问题
- 多核异构、大型应用层业务框架、强平台耦合中间件的全流程设计
- 用营销化语言包装“万能自动开发器”

## 适用场景

- 单 MCU / 单 SoC 的嵌入式项目
- 裸机或轻量 RTOS 场景
- 需要实现 GPIO / UART / SPI / I2C / Timer / PWM / ADC / DMA / EXTI / Watchdog / PSRAM 等常见模块
- 已有芯片型号、引脚分配、原理图、官方手册、SDK/HAL、现有工程可供审查
- 希望把开发过程沉淀成可追踪、可复用、可交接的记录

## 工作流总览

1. 资料审查：先确认芯片、板级资源、时钟、电源、引脚、外设连接、SDK/HAL、现有代码与交付目标。
2. 关键追问：仅提出会影响架构、驱动写法、时序、中断、DMA、验证方式的关键问题。
3. 模块拆解：按依赖关系排出模块顺序，一次只处理一个未验证模块。
4. 单模块开发：优先依据官方资料与官方例程，先做最小可用，再做必要封装。
5. 单模块验证：先给测试步骤、成功判据、失败排查路径，再宣布模块完成。
6. 系统集成：所有模块单独通过后再做集成，记录接口变化、耦合点与资源冲突。
7. 回归测试：输出回归清单、风险清单、遗留问题与后续优化建议。

## 快速开始

1. 准备资料：至少提供项目目标、芯片型号、原理图、引脚分配、官方手册、SDK/HAL 或现有代码。
2. 将 [`agent/system.md`](agent/system.md) 作为主 Prompt 使用。
3. 将 [`agent/rules.md`](agent/rules.md)、[`agent/workflow.md`](agent/workflow.md)、[`agent/questioning.md`](agent/questioning.md)、[`agent/output_contract.md`](agent/output_contract.md) 作为补充上下文。
4. 先填写 [`templates/project_intake.md`](templates/project_intake.md) 和 [`templates/hardware_intake.md`](templates/hardware_intake.md)，让 Agent 从资料审查开始，而不是从写代码开始。
5. 每开发一个模块前，先填写 [`templates/module_plan.md`](templates/module_plan.md)。
6. 模块验证和系统集成时，分别使用 [`templates/module_debug_checklist.md`](templates/module_debug_checklist.md) 与 [`templates/integration_report.md`](templates/integration_report.md) 记录结果。

## 推荐使用方式

- 最稳妥：把整个仓库作为上下文提供给 AI，再把项目资料与现有代码一并提供。
- 最轻量：至少复制 `agent/system.md`，并附上 `agent/rules.md` 与 `agent/output_contract.md`。
- 最工程化：在项目推进过程中持续填写 `templates/`，把 Agent 输出沉淀成团队文档。

建议把 Agent 放在“技术审查 + 模块开发助手”的位置，而不是放在“自动包办整项目”的位置。

## 仓库结构说明

```text
embedded-software-engineer-agent/
├─ README.md
├─ LICENSE
├─ CONTRIBUTING.md
├─ agent/
│  ├─ system.md
│  ├─ workflow.md
│  ├─ rules.md
│  ├─ questioning.md
│  └─ output_contract.md
├─ templates/
│  ├─ project_intake.md
│  ├─ hardware_intake.md
│  ├─ module_plan.md
│  ├─ module_debug_checklist.md
│  └─ integration_report.md
├─ examples/
│  └─ stm32_uart_i2c_spi_psram/
│     ├─ input_example.md
│     ├─ agent_output_example.md
│     └─ notes.md
└─ .github/
   ├─ ISSUE_TEMPLATE/
   │  ├─ bug_report.yml
   │  ├─ feature_request.yml
   │  └─ new_platform_support.yml
   └─ PULL_REQUEST_TEMPLATE.md
```

## 一个最小示例

用户输入可以像这样开始：

```text
目标平台：STM32F407
已有资料：原理图、RM0090、数据手册、STM32CubeF4 HAL、现有 GPIO 初始化代码
要做模块：UART1 调试口、I2C1 传感器、SPI2 外挂 PSRAM
要求：不要直接写整包工程，先审资料并指出缺失信息
```

预期的 Agent 行为不是直接生成代码，而是：

1. 先列出已确认信息与缺失项
2. 先问少量关键问题
3. 给出模块拆解与顺序
4. 只处理当前模块，并给出验证方法与完成标准

完整示例见 [`examples/stm32_uart_i2c_spi_psram/`](examples/stm32_uart_i2c_spi_psram/)。

## 支持范围

V1 当前支持：

- 单 MCU / 单 SoC 项目
- GPIO / UART / SPI / I2C / Timer / PWM / ADC / DMA / EXTI / Watchdog / PSRAM
- 裸机或轻量 RTOS
- 有明确硬件资料与官方文档可参考的项目
- 以“模块化开发 + 单模块验证 + 最后集成”为主线

## 非目标范围

V1 暂不重点支持：

- Linux BSP / 驱动框架
- 复杂 GUI
- 多核异构系统
- 射频协议栈
- 没有原理图和官方资料却要求直接生成完整工程
- 大型应用层业务框架

## 开源协作说明

- 仓库重点是规则、模板与示例，不追求文档数量。
- 新增规则时，应优先检查是否能并入现有文件，避免重复文档。
- 提交改动时，请说明它解决了什么工程问题、改变了什么工作流、如何保持“官方优先、阶段控制、验证闭环”。
- 详细协作要求见 [`CONTRIBUTING.md`](CONTRIBUTING.md)。

如果你第一次使用这个仓库，建议按顺序阅读：

1. `README.md`
2. `agent/system.md`
3. `agent/rules.md`
4. `agent/output_contract.md`
5. `examples/stm32_uart_i2c_spi_psram/agent_output_example.md`
