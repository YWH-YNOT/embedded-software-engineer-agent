# GitHub 网页设置清单

本文件只记录那些**不能仅靠修改本地文件完成**的 GitHub 仓库设置。下面的事情不代表已经完成；需要维护者到 GitHub 网页手动操作。

## 1. 设置为 Template Repository

目标：

- 让外部开发者可以直接从仓库生成自己的模板副本

步骤：

1. 打开仓库主页。
2. 进入 `Settings`。
3. 在 `General` 页面找到 `Template repository`。
4. 勾选 `Template repository`。
5. 保存后，确认仓库主页出现 `Use this template` 按钮。

## 2. 开启 Discussions

目标：

- 把使用问题、路线讨论、平台请求从 Issue 中分流出来

步骤：

1. 进入 `Settings`。
2. 打开 `General`。
3. 找到 `Features`。
4. 勾选 `Discussions`。
5. 回到仓库主页，确认顶部导航出现 `Discussions`。
6. 根据 [`discussions_seed_topics.md`](discussions_seed_topics.md) 创建首批话题。

## 3. 配置 Protected Branch

目标：

- 防止 `main` 被直接误改

步骤：

1. 进入 `Settings -> Branches`。
2. 添加或编辑 `Branch protection rule`，匹配 `main`。
3. 建议至少开启：
   - `Require a pull request before merging`
   - `Require status checks to pass before merging`
   - `Require conversation resolution before merging`
   - `Do not allow bypassing the above settings`（按团队实际权限决定）
4. 选择 `docs-check` 作为必需状态检查。

## 4. 开启 Require Review From Code Owners

目标：

- 让关键目录修改自动请求对应 owner 审阅

步骤：

1. 先确认 `.github/CODEOWNERS` 已存在并语法正确。
2. 在 `Settings -> Branches -> Branch protection rule` 中开启 `Require review from Code Owners`。
3. 保存设置。
4. 用一个测试 PR 确认 `AGENTS.md`、`.agents/skills/**`、`.github/**` 等目录会自动请求 owner 审阅。

## 5. 创建第一个 Release

目标：

- 给外部使用者一个明确版本锚点

步骤：

1. 确认需要发布的 tag 已存在。
2. 进入 `Releases` 页面。
3. 点击 `Draft a new release`。
4. 选择或创建 tag。
5. 按 [`release_policy.md`](release_policy.md) 判断这是 alpha、beta 还是稳定版。
6. 发布说明中至少写清：
   - 版本范围
   - 新增内容
   - 已知边界
   - breaking changes（如果有）

## 6. 后续启用 GitHub Pages

目标：

- 仅在需要公开浏览文档入口时启用，不是当前 P0-P1 必做项

步骤：

1. 进入 `Settings -> Pages`。
2. 选择部署源。
3. 仅当文档入口、导航结构和维护责任明确后再启用。
4. 启用前先确认不会把当前仓库拖入站点维护成本。

## 7. 建议顺序

建议按以下顺序操作：

1. Discussions
2. Template repository
3. CODEOWNERS + protected branch
4. 首个正式 release
5. GitHub Pages（如确有必要）
