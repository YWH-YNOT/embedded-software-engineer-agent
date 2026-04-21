# Skill Pack Contract

本文件定义仓库未来扩展 skill pack 时应遵守的最小接口。目标不是限制内容数量，而是避免 `.agents/skills/` 逐渐变成无边界文档堆。

## 1. 目录契约

每个 skill 使用一个独立目录，结构建议如下：

```text
.agents/skills/<skill-name>/
├─ SKILL.md
├─ references/   # 可选
└─ assets/       # 可选
```

规则：

- `SKILL.md` 是唯一必需入口
- `references/` 仅放支撑该 skill 的参考材料，不堆整套资料库
- `assets/` 仅放该 skill 必需的静态资源

## 2. 命名契约

- 使用小写英文加连字符，例如 `uart-bringup`
- 名称应体现任务，不体现营销包装
- 尽量按“一个 skill 对应一类具体任务”命名

## 3. 内容契约

每个 `SKILL.md` 必须包含以下一级或二级标题：

- `skill 名称`
- `skill 描述`
- `触发场景`
- `不应触发的场景`
- `所需输入`
- `输出要求`
- `边界与风险`
- `验收方式`

建议再补：

- 推荐工作步骤
- 相关模板或示例链接

## 4. 行为契约

一个 skill 应满足以下条件：

- 有明确进入条件
- 有明确退出条件
- 能映射到仓库既有阶段
- 不与 `AGENTS.md`、`agent/` 核心规则冲突
- 不偷跑到多个未验证模块

## 5. 不该出现的 skill

以下内容不适合直接做成 skill：

- 只有平台背景介绍，没有执行路径
- 只描述原理，没有输出契约
- 与现有 skill 高度重叠，但没有新增边界
- 一上来就要求生成完整工程

## 6. 变更管理

新增或修改 skill 时，建议同步检查：

- 是否需要更新 [`README.md`](../README.md)
- 是否需要更新 [`examples/README.md`](../examples/README.md)
- 是否需要补一个对应示例
- 是否构成 breaking change，参见 [`release_policy.md`](release_policy.md)

## 7. 建议验收清单

- [ ] skill 名称清楚
- [ ] 触发条件清楚
- [ ] 输入最小集清楚
- [ ] 输出结构清楚
- [ ] 边界和风险清楚
- [ ] 有可执行的验收方式
- [ ] 与现有规则无冲突
