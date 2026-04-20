# Contributing

感谢你为 `embedded-software-engineer-agent` 提交改进。

本仓库不是“Prompt 收藏夹”，而是一个面向 Codex / GitHub 原生协作的模板仓库。贡献内容必须优先维护以下目标：

- 规则可执行
- 边界可审查
- 输出可验证
- 文件职责清晰
- 仓库对陌生开发者可快速上手

## 提交前先判断你的改动属于哪一类

- 运行时入口：`AGENTS.md`
- 展开版规则：`agent/`
- 技能工作流：`.agents/skills/`
- 结构化模板：`templates/`
- 示例：`examples/`
- 协作与发布基建：`.github/`、`docs/`

如果改动会影响运行时行为，请同时检查：

- `AGENTS.md`
- `agent/system.md`
- `agent/workflow.md`
- `agent/rules.md`
- `agent/output_contract.md`

这些文件职责不同，但语义必须一致。

## 适合提交的内容

- 修正规则歧义、冲突或不可执行表达
- 增加能明确收敛任务的 skill
- 增加新的平台或模块示例，但要说明边界
- 改进模板，使其更容易填写和审查
- 改进 CI、Issue 模板、PR 模板、CODEOWNERS 等协作基础设施

## 不建议提交的内容

- 营销化文案
- 与当前目标无关的脚本框架
- 大量重复文档
- 没有示例和验收方式支撑的“新规则”
- 把社区经验写成官方事实
- 在资料缺失前提下鼓励直接生成完整工程

## 对 skill 的要求

新增或修改 `.agents/skills/` 时，请至少回答：

- 什么时候应触发
- 什么时候不应触发
- 需要什么输入
- 输出必须长什么样
- 边界和风险是什么
- 怎样判断这个 skill 已经完成

不要把 skill 写成大而空的理论综述。

## 对示例的要求

新增 `examples/` 时，建议每组至少包含：

- `input.md`
- `expected_output.md`
- `notes.md`

示例应尽量覆盖以下两类价值：

- 资料不足时先追问
- 单模块先验证，之后再集成

## 对规则改动的要求

如果改动 `AGENTS.md` 或 `agent/`：

1. 说明现有规则为什么不够。
2. 说明新规则解决什么问题。
3. 说明是否影响现有示例或模板。
4. 说明是否构成 breaking change。

## PR 最低要求

- README 中的目录说明与实际结构一致
- 新增文件职责清楚，不与现有文档重复冲突
- 新增模板能直接填写
- 新增示例与输出契约一致
- 新增 skill 有明确触发条件和验收方式
- 本地能通过文档检查工作流的等价检查

## 推荐提交流程

1. 先查现有 Issue / Discussions，避免重复方向。
2. 小步提交，避免把规则、示例、CI 和路线图全部混成一个 PR。
3. 修改规则时，优先同步示例。
4. 修改模板时，优先给出一段真实填写样例。
5. 修改协作基建时，说明它解决了哪个外部协作痛点。

## 沟通建议

- 用具体工程场景说话
- 用文件路径定位问题
- 用验证方法支撑结论
- 不把“我感觉”写成“仓库必须这样做”

## 相关文件

- 运行时入口：[`AGENTS.md`](AGENTS.md)
- 发布策略：[`docs/release_policy.md`](docs/release_policy.md)
- 路线图：[`docs/roadmap.md`](docs/roadmap.md)
- 手动 GitHub 设置：[`docs/github_settings_checklist.md`](docs/github_settings_checklist.md)
