# 气象论文助手

面向作者自己稿件的 Codex skill：气象科学审查、专业英文润色、投稿检查、按需文献调研与基于真实材料的起草。默认期刊为 JAMES；用户指定其他期刊时查询该刊官方规范。

## 从 GitHub 安装

仓库发布后，在另一台 Codex 中输入以下提示：

```text
使用 $skill-installer 从 https://github.com/ericatomspheric/atmospheric-paper-assistant 安装
skills/atmospheric-paper-assistant。
```

安装器会下载整个 skill 及其参考文件，无需手动传文件夹。私有仓库需要目标环境有相应访问权限。安装后在下一轮使用；若没有出现，重启 Codex。

按当前官方文档，个人发现目录是 `~/.agents/skills/`；部分 Codex 安装器和本机环境使用 `~/.codex/skills/`。使用目标 Codex 的内置安装器；手动安装则按其当前支持的目录放置，避免在两个目录安装同名副本。

官方说明：[Build skills](https://learn.chatgpt.com/docs/build-skills)。GitHub 托管不会让每台 Codex 自动获得或自动更新这份 skill。

## 使用

```text
使用 $atmospheric-paper-assistant 全面检查我的 JAMES 稿件。
核对物理解释、试验证据、图表与跨章节一致性，润色英文，
交付修订稿、科学审查报告和需要我确认的问题。
```

也可指定“仅语法润色”、另一个目标期刊，或要求文献调研。默认说明用中文、稿件用学术英文。文档处理与实时检索依赖目标环境中实际可用的工具；skill 本身不提供外部服务或专用计算程序。

## 结构与扩展

```text
skills/atmospheric-paper-assistant/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── scientific-review.md
    ├── atmospheric-writing.md
    ├── journal-selection.md
    ├── journals/james.md
    └── research-and-drafting.md
```

- `SKILL.md`：共同任务、修改边界、交付要求及按需加载入口。
- `scientific-review.md`：物理、方法、统计和证据检查。
- `atmospheric-writing.md`：术语、尺度、量的定义和专业英文表达。
- `journal-selection.md` 与 `journals/`：目标期刊选择、官方要求和核验日期。
- `research-and-drafting.md`：文献调查与从材料起草。

增加期刊时，在 `journals/` 新增经官方资料核验的档案，并在 `journal-selection.md` 登记链接。专业写作规则从真实稿件问题和可核验资料迭代；若以后某个方向的指南很长，再拆成按需读取的文件。项目特有的术语、试验名称和作者决定留在稿件项目中。

## 维护、更新与版本

以仓库中的 `skills/atmospheric-paper-assistant/` 为维护源，保留 skill 名称，方便现有调用继续使用。修改后检查元数据、相对链接和 [行为验收案例](docs/evaluation.md)，再提交并用 Git 标签发布可追溯版本；首次正式版本建议使用 `v0.1.0`，当前尚未创建版本标签。

采用安装器下载的副本不会随仓库更新。更新时先备份本地改动，再用同一来源更新；内置安装器若因目标目录已存在而拒绝安装，不要直接覆盖，先将旧目录移出发现位置后安装新版本。需要固定版本时，指定 Git 标签或提交。

维护者可克隆仓库，并把个人发现目录中的 skill 链接到仓库内的 skill 文件夹，让本地修订与仓库使用同一份源文件；已有目录应先备份。更新克隆通过 `git pull --ff-only`，有本地修改时先处理，避免丢失内容。

今后需要插件目录中的安装体验或捆绑连接器时，可沿用 `skills/` 布局封装插件，无需重写科学与期刊指南。当前直接从 GitHub 安装即可。

## 发布范围

发布包仅包含 skill 指令、通用参考指南和维护文档。论文原稿、研究数据及作者个人记录保存在各自项目中。维护者可按希望的复用范围选择许可证。
