# Roadmap

本文件按 P0 / P1 / P2 记录仓库演进方向，避免把路线图写成泛泛而谈的愿景。

## P0

目标：把仓库从个人 Prompt 仓库升级成外部开发者可上手的 Codex / GitHub 原生模板仓库。

- [x] 增加运行时入口 `AGENTS.md`
- [x] 增加 `.agents/skills/` 首批技能目录
- [x] README 升级为对外首页
- [x] 示例扩展为多组聚焦场景
- [x] 增加最小文档检查 CI
- [x] 增加 GitHub 网页设置清单

## P1

目标：补齐外部协作所需的社区和版本基建。

- [x] 增加 `CODE_OF_CONDUCT.md`
- [x] 增加 `SECURITY.md`
- [x] 增加 `CHANGELOG.md`
- [x] 强化 `CONTRIBUTING.md`
- [x] 升级结构化 Issue / PR 模板
- [x] 增加 `CODEOWNERS`
- [x] 增加版本策略与路线文档
- [x] 增加 Discussions 草稿与提问指南

## P2

目标：在不破坏核心契约的前提下扩展能力。

- [ ] 增加更多平台示例，例如 GD32、ESP32、NXP、RP 系列
- [ ] 增加 RTOS 场景下的 skill 和示例
- [ ] 增加 DMA、ADC、EXTI、Watchdog 的聚焦示例
- [ ] 视维护成本决定是否启用 GitHub Pages
- [ ] 视实际需求决定是否引入更严格的文档或链接检查

## 不在当前路线中的事项

- 大型自动发布系统
- 复杂网站或文档站
- 一次性覆盖所有 MCU 生态
- 为“看起来完整”而扩写大量重复文档
