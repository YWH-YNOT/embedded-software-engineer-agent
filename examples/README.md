# Examples Index

本目录不是案例堆积区，而是外部用户快速理解工作方式的入口。

## 如何使用

1. 先按你当前的真实阶段选示例，而不是按平台名字选示例。
2. 先看 `input.md`，确认你的输入是否接近这个场景。
3. 再看 `expected_output.md`，确认 Agent 是否遵守输出契约。
4. 最后看 `notes.md`，理解这个示例刻意强调了什么边界。

## 示例索引

| 示例 | 主要阶段 | 说明 |
| --- | --- | --- |
| [`stm32_uart_minimal`](stm32_uart_minimal/input.md) | Phase 3 -> 4 | 最小 UART bring-up |
| [`stm32_i2c_sensor`](stm32_i2c_sensor/input.md) | Phase 3 -> 4 | I2C 总线 + 单传感器闭环 |
| [`stm32_spi_memory`](stm32_spi_memory/input.md) | Phase 3 -> 4 | SPI 事务层与设备层分离 |
| [`multi_module_integration`](multi_module_integration/input.md) | Phase 5 -> 6 | 单模块通过后再做集成 |
| [`insufficient_info_case`](insufficient_info_case/input.md) | Phase 0 -> 1 | 资料不足必须先追问 |
| [`stm32_uart_i2c_spi_psram`](stm32_uart_i2c_spi_psram/input_example.md) | 全链路 | 完整长示例，适合看整体节奏 |

## 选哪个示例

- 如果你刚开始接入项目：先看 `insufficient_info_case`
- 如果你现在只做单模块 bring-up：看 `stm32_uart_minimal` / `stm32_i2c_sensor` / `stm32_spi_memory`
- 如果你已经有多个模块通过：看 `multi_module_integration`
- 如果你想看完整工作流：看 `stm32_uart_i2c_spi_psram`

## 新增示例时的建议

每组示例至少包含：

- `input.md`
- `expected_output.md`
- `notes.md`

如果是保留的历史长示例，可以沿用旧命名，但建议在本索引中说明用途和边界。
