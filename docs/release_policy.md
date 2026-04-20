# Release Policy

本文件定义仓库的版本阶段、发版条件和 breaking change 边界。

## 历史说明

仓库已经存在一个早期公开版本 `v0.1.0`。它是仓库公开化的起点。

从本文件开始，后续版本建议采用更清晰的阶段命名和进入条件：

- `v0.1.0-alpha`
- `v0.3.0-beta`
- `v1.0.0`

这三个版本定义的是阶段标准，不要求历史 tag 立即重写。

## 阶段定义

## `v0.1.0-alpha`

表示仓库已经具备对外试用的最小模板能力：

- 有可直接运行的 `AGENTS.md`
- `agent/` 规则体系齐全
- 至少一套模板和多组示例可用
- 有基本 CI
- 有基本 community health 文件

但此阶段仍允许规则和目录发生较大调整。

## `v0.3.0-beta`

表示仓库已经具备更稳定的外部协作能力：

- skill pack 结构已稳定
- 示例覆盖更广的平台或模块组合
- issue / PR / Discussions 流程运转稳定
- 规则变更已有明确评审和回归路径

此阶段仍允许调整，但不应频繁打破核心输出契约。

## `v1.0.0`

表示仓库已达到公开长期维护标准：

- 运行时入口、核心规则、输出契约稳定
- 关键 skill 接口稳定
- 对 breaking change 有明确管理策略
- 外部开发者可以稳定复用并参与协作

## 什么时候可以发 release

满足以下条件时，才建议发 release：

- README、AGENTS、`agent/`、`templates/`、`examples/` 没有明显自相矛盾
- 关键目录结构稳定
- 示例和输出契约一致
- CI 通过
- 已知边界已写清楚

## 什么属于 breaking change

以下改动默认视为 breaking change：

- `AGENTS.md` 中的阶段结构发生变化
- 输出结构的 8 个一级标题变更
- `.agents/skills/` 的触发语义发生不兼容变化
- `templates/` 中关键字段含义发生变化
- `examples/` 目录契约发生变化

以下改动通常不算 breaking change：

- 示例补充
- 新增 skill
- README 改写但不改变规则语义
- Issue / PR 模板增强

## 发版建议

- 小版本：新增示例、skill、模板字段、协作基建增强
- 预发布：用于 alpha / beta 阶段公开试用
- 稳定版：只在核心契约已收敛时发布
