# Agents Directory

本目录用于存放可被 Codex 风格运行器复用的 skills。

## 目录职责

- `.agents/skills/`：按任务聚焦的 skill 入口
- `SKILL.md`：每个 skill 的唯一必需入口文件
- 可选子目录：`references/`、`assets/`

## 何时新增 skill

适合新增 skill 的情况：

- 某类任务会反复出现
- 该任务可以被收敛成稳定输入、稳定输出和稳定验收方式
- 现有 `agent/` 总规则已经不适合承载过多细节

不适合新增 skill 的情况：

- 只是某个平台的一次性笔记
- 只是把现有规则复制一份换个标题
- 没有明确触发条件和退出条件

## skill 最低契约

每个 `SKILL.md` 至少应包含以下部分：

- skill 名称
- skill 描述
- 触发场景
- 不应触发的场景
- 所需输入
- 输出要求
- 边界与风险
- 验收方式

详细约束见 [`docs/skill_pack_contract.md`](../docs/skill_pack_contract.md)。

## 与其他目录的分工

- `AGENTS.md`：运行时全局入口，不承载具体模块流程细节
- `agent/`：展开版全局规则
- `.agents/skills/`：具体任务工作流
- `templates/`：可填写模板
- `examples/`：外部用户可对照的输入 / 输出样例
