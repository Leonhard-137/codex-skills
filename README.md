# codex-skills

用于 Codex 的个人技能合集。每个技能独立存放在 `skills/<name>/`，从 `SKILL.md` 读取执行规则，按需加载配套资料。

首批发布用户主导的学习工作流：由学习者决定目标、深度和笔记表述，AI 提供资料定位、概述、局部答疑与核查，并在合适时用图片解释结构和过程。

## 技能目录

| 技能 | 当前版本 | 用途 |
| --- | --- | --- |
| [study](skills/study/SKILL.md) | 2.0.3 | 学习入口：接续论文、教材和主题学习，协调概述、答疑与整理。 |
| [feyn-review](skills/feyn-review/SKILL.md) | 1.0.1 | 围绕当前问题和自拟笔记答疑，检查理解，按授权做机械修正。 |
| [renorm-overview](skills/renorm-overview/SKILL.md) | 1.0.2 | 在约定尺度提供概述，解释主要问题与概念关系，再逐块展开。 |

三个技能会相互引用学习边界与讲解规则，安装时请将三个目录一起安装；安装后，局部答疑和主题概述可以分别调用。它们是供当前 agent 使用的技能，安装或切换技能本身不会创建新 agent。

## 安装

在 Codex 中让内置安装器从本仓库安装三个目录：

```text
$skill-installer 请从 Leonhard-137/codex-skills 安装以下技能：
skills/study
skills/feyn-review
skills/renorm-overview
```

也可以克隆仓库后，将这三个完整目录并列放入 Codex 的用户技能目录 `~/.agents/skills/`，或目标项目的 `.agents/skills/`。目录之间的相对链接需要保留；已有同名技能时，先比较版本和本地修改再更新。

Codex 会检测技能变更；如果安装后没有显示，可重启。安装与发现机制见 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 使用

```text
$study 我想学习 CNN 的基础知识，先帮我判断合适的范围和学习方向。

$study 按这篇论文接续阅读，机械错误等我明确要求时再修改。

$feyn-review 我这样理解权重共享是否正确？请指出问题，保留我的原句。

$renorm-overview 先解释这个主题的主要问题与概念关系，细节由我选择展开。
```

新学习任务先确认范围；续学和局部追问沿用已有决定。学习者可以只阅读、提问，也可以自拟笔记。练习、讲义、展示和文件整理均按实际请求开展。

设计思路、五种学习情境和人机分工见 [Study 使用说明](skills/study/README.md)。

## 可选配套能力

以下工具按任务需要使用，本仓库尚未包含：

| 能力或技能 | 何时需要 |
| --- | --- |
| `obsidian-vault-notes`（OVN） | 检索、链接和修改真实 Obsidian 笔记。 |
| `manage-personal-knowledge`（MPK） | PDF 资料库、资源身份与索引管理。 |
| `textbook` | 把确认后的原稿制作成 TeX 讲义。 |
| `paper-to-talk` / `beamer` | 按明确请求制作报告或展示材料。 |
| `web-access` / `uni-search` | 常规原生检索不足时的补充访问能力。 |

基础阅读、概述和答疑可直接进行。可选能力缺失时，应说明具体限制，不能把讨论或普通文件操作说成已经完成专门的索引、校验或排版流程。

## 仓库结构与维护

```text
skills/
├── study/
│   ├── SKILL.md
│   ├── README.md
│   ├── agents/openai.yaml
│   └── references/workflows.md
├── feyn-review/
│   ├── SKILL.md
│   └── agents/openai.yaml
└── renorm-overview/
    ├── SKILL.md
    └── agents/openai.yaml
```

新增技能放入新的 `skills/<name>/` 目录，并更新上面的目录表。当前发布内容是指令与说明文件，不依赖固定盘符、私人笔记或账号凭据；知识库位置沿用使用者的实际配置。

仓库与已安装的技能是独立副本。发布更新需要提交并推送仓库，使用端通过安装或复制更新，不会自动双向同步。

Study 文档保留了历史设计参考与旧版上游线索。文件格式校验仅证明结构合规，具体教学行为仍需在真实使用中检验。
