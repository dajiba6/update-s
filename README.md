# update-s

`update-s` is a Cursor Agent Skill for maintaining the `html-code-slide-layout-guard` skill from real slide-making work.

It is designed as a manual slash-triggered workflow: invoke `/update-s` when a recent HTML slide generation, layout fix, preview repair, or narrator prompt update produced reusable lessons worth preserving.

## What It Updates

By default, this skill maintains:

- `.cursor/skills/html-code-slide-layout-guard/SKILL.md`
- `.agents/skills/html-code-slide-layout-guard/SKILL.md` when that mirror exists

The goal is not to create a task log. The goal is to turn repeated layout failures and proven fixes into future-facing guardrails that another agent can follow.

## Install

Copy this directory into a Cursor project:

```text
.cursor/skills/update-s/
```

The directory should contain:

```text
update-s/
├── README.md
└── SKILL.md
```

Restart Cursor or wait for skills to reload if `/update-s` does not appear immediately.

## Usage

In Cursor chat, run:

```text
/update-s
```

You can also provide scope:

```text
/update-s 根据这次英文 slides 的布局修复更新护栏
/update-s 把 preview 二层溢出的处理经验沉淀进去
/update-s 只更新案例沉淀，不改工作流
```

## What Gets Preserved

The skill only records reusable guidance, such as:

- Layout constraints that prevent overflow, overlap, or clipped content.
- Preview fixes for multi-slide HTML files.
- Rules for 1280x720 fixed-canvas slide fragments.
- Diagram-specific layout fixes for Venn, funnel, radar, loop, compass, and other dense visual patterns.
- Real failure cases compressed into `problem -> fix -> reusable rule`.

It avoids preserving:

- One-off page copy.
- Temporary coordinates.
- Subjective design preferences.
- Duplicate rules already present in the target skill.
- Long retrospectives that slow future agents down.

## Maintenance Philosophy

`update-s` should make `html-code-slide-layout-guard` sharper, not longer by default.

Prefer rewriting and merging existing rules over appending new sections. If no durable lesson exists, the correct output is to say that no update is needed.
