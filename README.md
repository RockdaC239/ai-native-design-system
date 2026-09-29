<p align="center">
  <img src="./assets/readme/hero.svg" width="100%" alt="AI Native Design System：把视觉意图写进 DESIGN.md，用 tokens 固定数值，用 showcase 展示效果，再应用到产品界面">
</p>

# AI Native Design System

一个 Codex skill，帮助你从视觉参考或现有产品界面出发，建立能被人和 AI 持续使用的设计系统；已有设计系统时，也能按它修改页面，减少风格漂移。

## 它如何工作

**视觉意图 → 设计规则 → 可见样张 → 产品界面**

- `DESIGN.md` 记录产品气质、版式原则、组件规范与 AI 生成规则。
- `tokens` 固定颜色、字体、间距、圆角和动效等具体值。
- `showcase` 展示组件与状态，让规则有可检查的视觉结果。

这三个部分是创建或整理设计系统时的默认交付物；组件库只有在你明确需要可复用的工程组件时才创建。一个页面的小调整也可以只改目标页面，不必重建整套系统。

## 开始使用

将仓库安装到 Codex 的全局 skills 目录：

```bash
git clone https://github.com/RockdaC239/ai-native-design-system.git ~/.codex/skills/ai-native-design-system
```

安装后告诉 Codex 当前阶段、项目路径和目标。也可以先给参考图，暂时不提供项目：

> 使用 `$ai-native-design-system`。我只有几张界面参考图，还没有代码项目。请先分析适合的视觉方向。

> 使用 `$ai-native-design-system`。请查看这个前端项目的现有 UI，为它创建 `design/DESIGN.md`、tokens 和 showcase。

> 使用 `$ai-native-design-system`。项目里已有 `design/DESIGN.md` 和 tokens，请按现有设计系统优化设置页。

如果目标技能目录已存在，在目录内运行 `git pull --ff-only` 更新即可。

## 选择工作方式

| 当前情况 | 技能会做什么 |
| --- | --- |
| 只有想法或参考图 | 分析产品、受众和视觉方向；按要求产出草稿，不强行检查代码 |
| 已有项目，需要设计系统 | 读取必要的页面和样式，确认视觉方向，再建立规则、数值和样张 |
| 已有设计系统，需要改页面 | 先读现有 `DESIGN.md` 与 tokens，沿用既定方向修改目标界面 |

默认的设计系统目录如下；具体项目可沿用自己的约定：

```text
design/
├── DESIGN.md
├── tokens/
│   ├── tokens.ts
│   ├── tokens.json
│   └── tokens.css
└── showcase/
    └── index.html
```

浏览器视觉检查是可选步骤。如果你需要桌面和移动端截图验收，请在请求中说明“做视觉 QA”。

## 仓库内容

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | 完整的工作模式、流程与验证要求 |
| [DESIGN.md 示例](references/DESIGN-md-example.md) | 设计意图文档的结构参考 |

这是设计系统工作流程，不自带一套适用于所有产品的视觉主题。项目自己的 `DESIGN.md`、tokens 和 showcase 才是该项目的设计依据。

## License

[MIT](LICENSE)
