# herdr-app skill

Community agent skill for the [Herdr](https://herdr.dev/) desktop app. It is **not** an official Herdr project, and it is **not** the older [Herdr TUI](https://herdr.dev/tui/) skill.

This repository is a thin entry point. It tells an agent when to help with Herdr App settings, layouts, keybindings, and mods, and when to coordinate terminals and agents. The version-matched manuals stay on your machine: the app writes `AGENTS.md`, and `herdr-app --skill` / `hc --skill` print the live guides. This repo does not copy those official manuals.

这是给 [Herdr](https://herdr.dev/) 桌面版用的社区 agent skill，**不是**官方项目，也**不是**旧的 [Herdr TUI](https://herdr.dev/tui/) skill。

它只做薄入口：在你要改 Herdr App 的设置、布局、快捷键、mod，或编排终端和 agent 时提醒 agent 怎么做。和当前版本对齐的手册仍在本机：App 会写入 `AGENTS.md`，`herdr-app --skill` / `hc --skill` 会打印实时指南。本仓库不收录这些官方手册。

## Install / 安装

Install with the skills CLI:

用 skills CLI 安装：

```sh
npx skills add BIGPPWONG/herdr-app-skills --skill herdr-app
```

Add `-g` to install it for every project. Omit `-g` to install it into the current project only.

加上 `-g` 会装到所有项目；不加则只装到当前项目。

You need the Herdr app and herdr-core (`hc`) installed separately. This skill does not install Herdr, and an agent using it should not install the skill itself unless you ask.

Herdr App 和 herdr-core（`hc`）需要另行安装。本 skill 不会安装 Herdr；使用它的 agent 也不应在未经你同意时自行安装 skill。

## What it does / 它做什么

When loaded, the skill asks the agent to:

加载后，它会要求 agent：

1. Resolve the app home as `$HERDR_APP_HOME`, else `$XDG_CONFIG_HOME/herdr-app`, else `~/.config/herdr-app` (this default is used on every OS).
2. Read the installed `AGENTS.md` for settings, layouts, keys, and mods, and never overwrite that file or the generated `.d.ts` files.
3. Run `herdr-app --skill` to drive the window, and `hc --skill` to run or coordinate agents and programs.
4. Keep a clear boundary with the older TUI: use `herdr-app` and `hc`, never the `herdr` CLI or `HERDR_ENV`.
5. Ask before changing config, creating tabs or spaces, sending messages, or orchestrating work when not already inside a herdr-core terminal (`HC_TERMINAL_ID` unset).

解析 App 配置目录的顺序是 `$HERDR_APP_HOME`，否则 `$XDG_CONFIG_HOME/herdr-app`，否则 `~/.config/herdr-app`（各系统默认都是这一路径）。改设置、布局、快捷键或 mod 时先读已安装的 `AGENTS.md`，且不得覆盖该文件和生成的 `.d.ts`。改窗口跟 `herdr-app --skill`，编排终端和 agent 跟 `hc --skill`。不要用旧 TUI 的 `herdr` 命令或 `HERDR_ENV`。不在 herdr-core 终端内（未设置 `HC_TERMINAL_ID`）时，改配置、新建 tab/space、发消息或编排前要先征得你同意。

It can be installed beside the official [`herdr-core`](https://github.com/herdrdev/herdr-core/tree/master/skills/herdr-core) skill. They complement each other; they are not a replacement for the live `--skill` manuals or for `AGENTS.md`.

它可以和官方 [`herdr-core`](https://github.com/herdrdev/herdr-core/tree/master/skills/herdr-core) skill 一起使用，彼此互补，都不能替代实时 `--skill` 手册或 `AGENTS.md`。

## Layout / 目录

```text
skills/herdr-app/SKILL.md
README.md
LICENSE
```

## License

MIT, Copyright (c) 2026 BIGPPWONG. See [LICENSE](LICENSE).
