# update-s

`update-s` 是一个 Cursor Agent Skill，用来根据真实的 HTML 代码幻灯片制作、修复和优化经验，维护 `html-code-slide-layout-guard` 这个排版护栏 skill。

它适合作为手动触发的 `/` 快捷流程使用：当一次 HTML slides 生成、布局修复、preview 修复或 narrator prompt 更新产生了值得复用的经验时，输入 `/update-s`，让 Agent 把这些经验沉淀进目标 skill。

## 更新目标

默认维护以下文件：

- `.cursor/skills/html-code-slide-layout-guard/SKILL.md`
- `.agents/skills/html-code-slide-layout-guard/SKILL.md`，如果这个镜像文件存在

它的目标不是记录任务流水账，而是把反复出现的布局问题、真实验证过的修复方式，转化成未来 Agent 可以直接遵守的护栏规则。

## 安装

把本目录复制到 Cursor 项目中：

```text
.cursor/skills/update-s/
```

目录结构应为：

```text
update-s/
├── README.md
└── SKILL.md
```

如果 `/update-s` 没有立即出现在 slash 列表中，等待 Cursor 重新加载 skills，必要时重启 Cursor。

## 使用方式

在 Cursor 聊天中输入：

```text
/update-s
```

也可以补充更新范围：

```text
/update-s 根据这次英文 slides 的布局修复更新护栏
/update-s 把 preview 二层溢出的处理经验沉淀进去
/update-s 只更新案例沉淀，不改工作流
```

## 会沉淀什么

这个 skill 只记录可复用的长期经验，例如：

- 防止文字溢出、元素重叠、内容被裁切的布局约束。
- 多页 HTML preview 文件的修复方式。
- 1280x720 固定画布 slide 片段的格式规则。
- Venn、funnel、radar、loop、compass 等高密度图示的专项修复规则。
- 被压缩成 `问题 -> 处理 -> 可复用规则` 的真实踩坑案例。

它不会沉淀：

- 某一页的一次性文案。
- 临时坐标和局部微调值。
- 主观审美偏好。
- 目标 skill 中已经存在的重复规则。
- 会拖慢未来 Agent 阅读速度的长篇复盘。

## 维护原则

`update-s` 应该让 `html-code-slide-layout-guard` 更锐利，而不是默认变得更长。

优先改写和合并已有规则，而不是不断追加新段落。如果本次修改没有形成可长期复用的经验，正确做法是告诉用户“不需要更新”。
