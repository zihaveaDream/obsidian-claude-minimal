# Claude for Minimal / Obsidian

## 1. 这是什么？

`Claude for Minimal / Obsidian` 是一个为 Obsidian `Minimal` 主题设计的 Claude 风格外观方案。它的目标不是替换你的 Obsidian 工作流，而是在保留 `Minimal` 和 `Minimal Theme Settings` 使用体验的前提下，为 Obsidian 叠加一套更温润、克制、适合长时间写作和阅读的 Claude 风格界面。

这个项目推荐以 **CSS snippet** 的方式使用：继续把 Obsidian 当前主题设为 `Minimal`，再启用 `Claude for Minimal.css`。这样 Minimal 的布局、行宽、折叠、文件列表、插件兼容性和 Minimal Theme Settings 配置仍然保留，只叠加 Claude 风格的颜色、字体、控件和 Markdown 样式。

它主要实现这些效果：

- 使用 Claude 主题的浅色/深色配色、强调色、面板色、边框、圆角和阴影。
- 为 Obsidian 的侧边栏、标签页、按钮、菜单、弹窗、搜索建议、属性区做 Claude 风格适配。
- 为标题、正文、行内代码、代码块、引用、表格、callout、链接、高亮、下划线等 Markdown 元素做风格统一。
- 使用 Claude 风格字体链：`Anthropic Serif Web Text`、`Anthropic Sans Web Text`、`Anthropic Mono Variable`、`Noto Serif SC`。
- 保留 Obsidian / Minimal 的原有编辑体验，不隐藏粗体、斜体、行内代码、高亮、下划线等 Markdown 标记。
- 保留 Obsidian 的按钮、侧边栏控制、源码/阅读切换能力和横向滚动条。

本项目不会引入会影响 Obsidian 使用体验的隐藏规则，不隐藏 Markdown 符号、按钮、侧边栏控件和水平滚动条，尽量让视觉变化停留在外观层，而不改变你原来的编辑习惯。

项目内包含两个使用方式：

- `Claude for Minimal.css`：推荐使用的 CSS snippet。
- `Claude Minimal/`：可选主题包装版，会先导入本地已安装的 `Minimal/theme.css`，再叠加 Claude 外观。

> 字体授权提醒：公开发布到 GitHub 前，请确认 `fonts/` 目录内字体的再分发授权。如果授权不明确，更稳妥的做法是删除 `fonts/`，只在 README 中说明用户需要自行安装对应字体。

## 2. 如何从 0 到 1 配置？

下面以一个全新的 Obsidian vault 为例。

### 2.1 安装 Minimal

1. 打开 Obsidian。
2. 进入 `Settings -> Appearance -> Themes`。
3. 点击 `Manage`。
4. 搜索并安装 `Minimal`。
5. 将当前主题切换为 `Minimal`。

### 2.2 安装 Minimal Theme Settings

1. 进入 `Settings -> Community plugins`。
2. 关闭安全模式或允许社区插件。
3. 点击 `Browse`。
4. 搜索并安装 `Minimal Theme Settings`。
5. 启用插件。

推荐设置：

- `Line height`: `1.5`
- `Line width`: `40`
- `Wide line width`: `50`
- `Max width`: `88`
- `Normal text`: `17`
- `Readable line length`: 按你的习惯开启或关闭

这些不是强制项，只是更接近当前适配时的视觉基准。

### 2.3 安装字体

项目字体位于：

```text
fonts/
├── anthropic/
│   ├── AnthropicSerifWebText-Regular.ttf
│   ├── AnthropicSansWebText-Regular.ttf
│   └── AnthropicMonoVariable-Regular.ttf
└── noto-serif-sc/
    ├── NotoSerifSC-Regular.ttf
    ├── NotoSerifSC-Medium.ttf
    ├── NotoSerifSC-SemiBold.ttf
    ├── NotoSerifSC-Bold.ttf
    └── ...
```

字体对应关系：

- `AnthropicSerifWebText-Regular.ttf` -> `Anthropic Serif Web Text`
- `AnthropicSansWebText-Regular.ttf` -> `Anthropic Sans Web Text`
- `AnthropicMonoVariable-Regular.ttf` -> `Anthropic Mono Variable`
- `NotoSerifSC-*.ttf` -> `Noto Serif SC`

macOS：

1. 打开 `fonts/anthropic/`，全选字体文件并安装。
2. 打开 `fonts/noto-serif-sc/`，全选字体文件并安装。
3. 完全退出并重新打开 Obsidian。

Windows：

1. 打开 `fonts/anthropic/`，全选字体文件，右键安装。
2. 打开 `fonts/noto-serif-sc/`，全选字体文件，右键安装。
3. 如果有权限，建议选择“为所有用户安装”。
4. 完全退出并重新打开 Obsidian。

Linux：

1. 将字体复制到 `~/.local/share/fonts/claude-for-minimal/`。
2. 执行：

```bash
fc-cache -f -v
```

3. 完全退出并重新打开 Obsidian。

### 2.4 配置 Obsidian 字体

进入 `Settings -> Appearance -> Fonts`，按下面顺序配置。

Interface font：

```text
Anthropic Serif Web Text, Noto Serif SC, Georgia
```

Text font：

```text
Anthropic Serif Web Text, Noto Serif SC, Georgia
```

Monospace font：

```text
Anthropic Mono Variable, Noto Serif SC, JetBrains Mono, Source Code Pro, monospace
```

顺序很重要。不要把 `system-ui` 放在 `Noto Serif SC` 前面，否则中文会优先落到系统黑体，视觉会和正文的衬线风格不一致。

本项目的 CSS snippet 也会对编辑区和阅读区追加字体约束，避免 Minimal 或 Obsidian 的变量链让中文字体回退到系统默认字体。

### 2.5 安装推荐方案：CSS snippet

这是最推荐的安装方式。

1. 找到你的 vault 目录。
2. 进入：

```text
.obsidian/snippets/
```

如果没有 `snippets` 文件夹，可以手动新建。

3. 将项目根目录下的文件复制进去：

```text
Claude for Minimal.css
```

目标路径应类似：

```text
YourVault/.obsidian/snippets/Claude for Minimal.css
```

4. 回到 Obsidian。
5. 进入 `Settings -> Appearance -> CSS snippets`。
6. 点击刷新按钮。
7. 启用 `Claude for Minimal`。
8. 确认当前主题仍然是 `Minimal`。

如果 Obsidian 已经打开很久，建议执行一次 `Reload app`，或完全退出后重新打开。

### 2.6 可选安装：主题包装版

如果你希望在 Obsidian 的主题列表中看到 `Claude Minimal`，可以使用主题包装版。

1. 确认你已经安装了 `Minimal`，并且主题目录名是：

```text
Minimal
```

2. 将整个文件夹复制到 vault 的主题目录：

```text
Claude Minimal/
```

目标路径应类似：

```text
YourVault/.obsidian/themes/Claude Minimal/
```

3. 确认目录结构是：

```text
YourVault/.obsidian/themes/
├── Minimal/
│   └── theme.css
└── Claude Minimal/
    ├── manifest.json
    └── theme.css
```

4. 在 Obsidian 中进入 `Settings -> Appearance -> Themes`。
5. 选择 `Claude Minimal`。

注意：`Claude Minimal/theme.css` 会通过下面这行导入相邻的 Minimal：

```css
@import url("../Minimal/theme.css");
```

所以如果你的 Minimal 主题目录被改名，主题包装版会失效。多数情况下，CSS snippet 方案更稳。

### 2.7 检查是否生效

生效后你应该看到：

- 英文标题和正文接近 Claude Serif 的观感。
- 中文正文使用 `Noto Serif SC`，而不是系统黑体。
- UI 控件有 Claude 风格的暖白背景、柔和边框和橙色强调色。
- 行内代码和代码块使用 Anthropic Mono 风格。
- Markdown 源码标记、侧边栏控件和横向滚动条仍然可用。

如果中文字体没有变化，优先检查：

1. `Noto Serif SC` 是否真的安装成功。
2. Obsidian 是否已经完全重启。
3. 字体顺序里 `Noto Serif SC` 是否排在 `system-ui` 前面。
4. `Claude for Minimal` snippet 是否启用。

如果你希望界面更接近 Claude 官网的无衬线 UI，可以只把 Interface font 改成：

```text
Anthropic Sans Web Text, system-ui, Noto Serif SC
```

但这样界面中的中文会回退到系统黑体，更像原生 macOS / Windows UI，不再和笔记正文完全一致。

### 2.8 文件结构

```text
.
├── Claude for Minimal.css
├── Claude Minimal/
│   ├── manifest.json
│   └── theme.css
├── fonts/
│   ├── anthropic/
│   └── noto-serif-sc/
└── README.md
```

### 2.9 更新主题

如果你只使用 snippet，更新时替换：

```text
YourVault/.obsidian/snippets/Claude for Minimal.css
```

如果你使用主题包装版，更新时替换：

```text
YourVault/.obsidian/themes/Claude Minimal/
```

建议更新后重启 Obsidian。
