---
name: update-s
description: 根据最近的 HTML 代码幻灯片制作、修复和优化修改，维护并更新 html-code-slide-layout-guard skill。Use when the user invokes /update-s or asks to update slide layout guard rules from recent work.
disable-model-invocation: true
---

# Update Slide Layout Guard Skill

本 skill 是 `html-code-slide-layout-guard` 的专用维护入口。用户输入 `/update-s` 时，默认目标是：

- `.cursor/skills/html-code-slide-layout-guard/SKILL.md`
- `.agents/skills/html-code-slide-layout-guard/SKILL.md`（如果存在）

目标不是总结本次任务流水账，而是把真实制作、修复、验证过程中暴露出的可复用经验，沉淀为以后 Agent 能遵守的明确规则。

## 使用方式

用户可以直接说：

```text
/update-s
```

也可以补充范围：

```text
/update-s 根据这次 Dan Koe 英文 slides 的布局修复更新护栏
/update-s 把刚才 preview 溢出的处理经验沉淀进去
/update-s 只更新案例沉淀，不改工作流
```

## 工作流

1. 读取目标 `html-code-slide-layout-guard/SKILL.md`。
2. 查看当前修改上下文：优先看 `git diff`、最近编辑的 HTML slide / prompt / generator 文件，以及用户特别点名的文件。
3. 提炼最多 3-5 条真正可复用的经验；如果只是一次性文案、具体页码或临时审美偏好，不写入 skill。
4. 判断应该更新的位置：
   - 新的硬性约束 → `布局护栏原则` 或 `交付前 checklist`。
   - 新的修复流程 → `工作流` 或 `多页 Preview 修复`。
   - 新的图示模式 → `按图示模式修`。
   - 真实踩坑 → `案例沉淀`。
   - 反面模式 → `反模式（禁止）`。
5. 合并相近规则，优先改写已有条目，不重复追加同义内容。
6. 如 `.cursor` 和 `.agents` 两份目标文件都存在，保持两份内容一致。
7. 修改后检查目标 skill 是否仍然简洁、结构清晰、适合未来 Agent 快速执行。

## 沉淀标准

只写入满足至少一项的内容：

- 未来制作 1280x720 HTML slides 时很可能再次遇到。
- 能防止文字重叠、内容溢出、preview 叠页、图示变形、prompt 与 deck 脱节。
- 能形成可执行检查项，例如“先算高度预算”“必须使用局部定位容器”“不要把装饰性箭头作为 flex 子项”。
- 来自真实修改或验证结果，而不是泛泛设计建议。

不要写入：

- 某一页的临时文案、具体坐标或一次性审美选择。
- 与 HTML slide layout guard 无关的项目管理、资料研究、内容大纲经验。
- 已经在目标 skill 中清楚表达过的同义规则。
- 过长案例叙述；案例必须压缩成“问题 → 处理 → 可复用规则”。

## 更新风格

- 保持中文为主，术语沿用目标 skill 的现有写法。
- 保持规则短、硬、可执行。
- 案例优先写成一行表格或短段，不写长复盘。
- 若发现目标 skill 里有散乱追加段落，优先整理进现有章节，而不是继续堆在末尾。
- 不为了“更新而更新”；如果没有值得沉淀的新规则，直接告诉用户没有必要修改。

## 验收

完成后向用户简短说明：

- 更新了哪个目标 skill。
- 新增或调整了哪些长期规则。
- 是否同步了 `.cursor` 与 `.agents` 两份副本。
- 如果没有更新，说明原因。
