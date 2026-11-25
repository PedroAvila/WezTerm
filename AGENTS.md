# AGENTS.md — Project Rules and Guidelines

Welcome. This document defines the directives, environment context, documentation standards, and operational guidelines that **any artificial intelligence agent (or developer)** must adhere to whilst interacting with, modifying, or extending the files within this workspace.

---

## 📌 1. Project Context and Purpose

* **Workspace root path:** `D:\WezTerm`
* **Purpose:** Knowledge base, technical documentation, user manuals, and configurations for a modern, highly efficient development environment on **Windows 11**.
* **Core technology stack:**
  * **Terminal:** [WezTerm](https://wezfurlong.org/wezterm/) (GPU-accelerated terminal emulator).
  * **Editor:** [Neovim](https://neovim.io/) with the [LazyVim](https://www.lazyvim.org/) distribution.
  * **C/C++ Toolchain:** GCC via [WinLibs](https://winlibs.com/) (POSIX UCRT) for native compilation of Tree-sitter parsers (`nvim-treesitter`).
  * **Development ecosystem:** TypeScript, Angular, HTML, SCSS, and Node.js.
  * **Default shell:** PowerShell.

---

## 💻 2. Operating Environment and System Conventions

1. **Operating System:** 64-bit Windows 11.
2. **Command Shell:** PowerShell (`pwsh` or Windows PowerShell).
   * When proposing terminal commands or scripts, they must be compatible with PowerShell for Windows.
   * Use appropriate quotation marks for paths containing spaces and avoid assumptions of pure Unix/Linux environments (for instance, avoid `export VAR=val`; use `$env:VAR = "val"` or `[Environment]::SetEnvironmentVariable`).
3. **Encoding:** All files must be created and saved in **UTF-8 without BOM**.
4. **Standard Windows locations referenced in the project:**
   * Neovim configuration: `$env:LOCALAPPDATA\nvim\` (`C:\Users\<User>\AppData\Local\nvim\`)
   * Neovim data: `$env:LOCALAPPDATA\nvim-data\`
   * WezTerm configuration: `$env:USERPROFILE\.wezterm.lua` or `$env:USERPROFILE\.config\wezterm\wezterm.lua`

---

## 🛡️ 3. Fundamental Rules for AI Agents

### A. Language and Tone
* **Primary language:** **Spanish**. All new documentation, explanations, commit messages, or technical responses must be drafted in clear, professional, and educational Spanish.
* **Tone:** Precise, structured, direct, and focused on practical solutions.

### B. Consistency with Established Configuration
Any manual, shortcut, or setting suggested by an agent must strictly align with the agreed configuration rules:
* **WezTerm:**
  * **Golden rule for shortcuts:** Use of the `Ctrl` + `Alt` + `[key]` modifier combination for custom shortcuts (split management with `Ctrl+Alt+D`/`S`, tabs with `Ctrl+Alt+C`, navigation using arrow keys).
  * Do not reintroduce the traditional WezTerm `Leader` key unless explicitly requested by the user.
  * Base visual theme: `Catppuccin Mocha`, 85% opacity with *Acrylic* effect, and `JetBrainsMono Nerd Font Mono` font.
* **LazyVim / Neovim:**
  * `<leader>` key: Always the **Space bar (`Space`)**.
  * Shortcut sequences must be documented sequentially (for example: `<leader>bd` is press `Space`, release, press `b`, release, press `d`).
  * The file explorer is toggled with `<leader>e`.
* **Tree-sitter and Compilers:**
  * The officially configured compiler is **GCC (WinLibs)**.
  * Do not suggest Visual Studio Build Tools (`cl.exe`) or `zig cc` for Tree-sitter, as they cause known compatibility errors (`unable to parse target query`).

### C. Safe File Modification
* **Mandatory backups:** Prior to proposing destructive replacements or the removal of configuration folders (such as `$env:LOCALAPPDATA\nvim`), include the prior backup command (`Move-Item ... .bak`).
* **Non-destructive editing:** If editing an existing file, respect its formatting, relative links, and pre-existing sections.
* **File naming conventions:** 
  * Documentation: Descriptive lowercase names separated by hyphens or underscores (`.md`).
  * Scripts/Configurations: `.lua`, `.ps1` as appropriate.

### D. Direct File Access & Token Efficiency (Exact File Targeting)
* **Strict rule:** When the user provides an exact file name, path, or mention (e.g. `@[filename]`), the agent **MUST NOT** search, list, or read other unrelated files in the repository.
* Go straight to the target file, perform the required read or edit, and finish the task without wasting time or consuming extra tokens.
* See [`adrs/0001-acceso-directo-a-archivos-especificados.md`](file:///D:/WezTerm/adrs/0001-acceso-directo-a-archivos-especificados.md) for full context and architecture decision records.

---

## 📝 4. Formatting Standards for Markdown Documentation

When creating or editing Markdown files in this repository, follow these guidelines:
1. **Headings:** Clean hierarchical structure (`# H1` for a single title, `## H2` for sections, `### H3` for subsections).
2. **Shortcut tables:** Use legible Markdown tables with fixed columns:
   ```markdown
   | Action | Keyboard Shortcut | Description |
   | :--- | :--- | :--- |
   ```
3. **Code blocks with explicit syntax highlighting:**
   * Always specify a language identifier: `powershell`, `lua`, `vim`, `typescript`, `bash`, `text`.
4. **Callouts and blockquotes:** Use blockquote-style blocks (`> **Key note:**` or `> **Important:**`) for warnings or critical points.

---

## 🗂️ 5. Project File Map

| File | Description |
| :--- | :--- |
| [`AGENTS.md`](file:///D:/WezTerm/AGENTS.md) | Fundamental rules, guidelines, and standards for AI agents and collaborators. |
| [`adrs/0001-acceso-directo-a-archivos-especificados.md`](file:///D:/WezTerm/adrs/0001-acceso-directo-a-archivos-especificados.md) | Architecture Decision Record: Direct file access and token efficiency rule. |
| [`manual-wezterm.md`](file:///D:/WezTerm/manual-wezterm.md) | Quick reference manual and custom configuration for WezTerm using `Ctrl + Alt`. |
| [`manual_completo_de_lazyvim.md`](file:///D:/WezTerm/manual_completo_de_lazyvim.md) | Comprehensive guide to LazyVim (modes, buffers, splits, shortcuts, LSP, Mason, and themes). |
| [`gu_a_de_instalaci_n_neovim_lazyvim_en_windows_11.md`](file:///D:/WezTerm/gu_a_de_instalaci_n_neovim_lazyvim_en_windows_11.md) | Step-by-step tool provisioning guide with `winget`, GCC configuration, and Angular/TypeScript support. |

---

## 🚀 6. Quick Checklist for New Changes

Before marking a task as complete in this project:
- [ ] Does the change respect the Windows 11 and PowerShell environment?
- [ ] Do the described shortcuts adhere to the conventions (`Ctrl + Alt` in WezTerm, `Space` in LazyVim)?
- [ ] Is the documentation drafted in clear and concise Spanish?
- [ ] Are the command blocks reproducible and safe?
- [ ] Have the tables or references been updated if new files were added?
