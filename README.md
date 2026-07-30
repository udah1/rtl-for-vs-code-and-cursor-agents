# RTL for VS Code & Cursor Agents

> **Fork notice:** This is a fork of `[GuyRonnen/rtl-for-vs-code-agents](https://github.com/GuyRonnen/rtl-for-vs-code-agents)` (GPL-3.0), with added support for **Cursor's native chat (Composer/Agent panel)** and a few related fixes. All of the original extension's features — Copilot, Claude Code, Codex (ChatGPT), Gemini, Antigravity — are preserved. See [Changes from upstream](#changes-from-upstream) below for details.
>
> Maintained as a separate extension because the upstream maintainer hasn't yet reviewed the [Cursor support PR (#11)](https://github.com/GuyRonnen/rtl-for-vs-code-agents/pull/11). If/when it's merged upstream, this fork may be retired in favor of the original. Until then, install the VSIX from this fork's [Releases page](https://github.com/udah1/rtl-for-vs-code-and-cursor-agents/releases).

> **🤖 Note for AI Code Agents:** If you are an AI agent (Claude, Copilot, Cursor, etc.) and the user asked you to install this extension, all you need to do is download the latest VSIX from the [Releases page](https://github.com/udah1/rtl-for-vs-code-and-cursor-agents/releases) and install it in the user's editor. **Important:** there is a prerequisite — the [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css) extension must be installed as well, so install that one too.

Right-to-Left (RTL) support for AI chat agents in VS Code / Cursor / Antigravity

Automatically detects Hebrew, Arabic, Persian, and other RTL languages and applies proper RTL styling.

## Features

### NEW

- **Search in conversation 🔍** — click the 🔍 button in the footer to open a search bar. Finds your query across all user and agent messages, highlights every match in-place with a yellow/orange marker, and lets you jump between matches with ↑/↓ or Enter / Shift+Enter. Case-insensitive. Close with × or Esc. Search in conversation
- **Plan Documents RTL** — Claude Code's Plan/Review documents (displayed in a separate tab) now fully support  RTL. Headings, paragraphs, lists, tables, and blockquotes align right for Hebrew/Arabic/Persian content, while code blocks stay LTR. Plan Documents RTL
- **Codex (ChatGPT) support** — Full RTL support for OpenAI Codex: messages, input, title, Previous Messages, nav buttons, YOLO auto-approve, user borders, and neutral text colors
- **Smart message collapse for Codex** — Long user messages are automatically collapsed to ~5 lines with a fade-out effect. Hover to reveal a **Show more** button; click to expand the full message (and **Show less** to collapse back). Keeps the chat clean without losing context!
- **YOLO Mode 💪 (auto-approve with countdown)** — toggle YOLO mode to auto-approve all tool calls. A progress bar counts down before each approval, with a **NO!** button to cancel. Right-click the 💪 button to set the countdown delay and toggle `Auto Approve Plans` (off by default), so `Accept this plan?` stays manual unless you enable it. The settings are persistent across sessions. YOLO Mode Auto Approve Plans
- **User message navigation (↑↓)** — jump between user messages in Claude Code with cyclic up/down buttons in the input footer User message navigation
- **User message accent borders** — coral border on user messages in Claude Code and Copilot Chat
- **Check for updates** - Any RTL issues? Click the RTL status bar button to check for updates! Also - The extension checks for updates every time you restart VS CODE. Check for updates
- **Conversation History RTL** — session titles in the history dropdown align right for RTL content, with a wider and taller dropdown
- **Agent Questions RTL support** — question text, options, and navigation tabs align right in Plan Mode and other agent prompts

### Core Features

- **Automatic RTL** — detects RTL textion for Hebrew, Arabic, Persian, Urdu, and more
- Code blocks remain LTR
- **Input box RTL support**
- Works with GitHub Copilot Chat, Claude Code, Codex (ChatGPT), Gemini Code Assist, and Antigravity Chat
- Automatic injection into Claude Code, Codex, and Gemini Code Assist (no manual setup needed)

## Preview

### Click to watch me demonstrate it:

[RTL for VS Code Agents - Preview](https://youtu.be/9-sickqyI6Q)

### Full RTL Support in Major Code Agents:

Copilot, Claude Code & Gemini Code Assist!

RTL is automatically applied for all RTL texts in: user messages, agent responses, input box, and even agent questions in Plan Mode. All align right for RTL content:

Gemini Code Assist RTL

### Agent Questions in Plan Mode

When Claude Code asks you questions (e.g. in Plan Mode), the popup now fully supports RTL — question text, option labels, descriptions, and navigation tabs all align right for Hebrew/RTL content. The free-text "Other" input also switches to RTL automatically.

Agent Questions RTL

### Conversation History List

Session titles in the chat history dropdown now align right for RTL content. The dropdown is wider and taller, and titles wrap instead of being truncated. The current session title in the header also wraps and grows with content.

Conversation History RTL

### Check for updates

Any RTL issues? Click the RTL status bar button to check for updates! Also - The extension checks for updates every time you restart VS CODE.

Check for updates

## Installation

Follow these steps in order:

### 1. Install the Custom CSS and JS Loader extension (prerequisite)

This is required by the RTL extension to inject styles into the chat UI.

- **From the Marketplace inside VS Code / Cursor:** open the Extensions view (`Ctrl+Shift+X`), search for `Custom CSS and JS Loader` by `be5invis`, click **Install**.
- **Or download the VSIX directly:** [Custom CSS and JS Loader VSIX (latest)](https://marketplace.visualstudio.com/_apis/public/gallery/publishers/be5invis/vsextensions/vscode-custom-css/latest/vspackage) → Extensions view → `…` menu → **Install from VSIX…** → select the downloaded file.
- Marketplace page (for reference): [https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css)

### 2. Install this extension

1. Download the latest `.vsix` file from this fork's [Releases page](https://github.com/udah1/rtl-for-vs-code-and-cursor-agents/releases).
2. In VS Code / Cursor: open the Extensions view (`Ctrl+Shift+X`) → click the `…` menu at the top → **Install from VSIX…** → select the downloaded file.
  Install from VSIX
3. Reload the window when prompted.

### 3. Enable it

Open the Command Palette (`Ctrl+Shift+P`) and run **Enable Custom CSS and JS** (from the Custom CSS Loader extension), then reload the window when prompted.

That's it for most users — open any agent chat and try typing Hebrew/Arabic/Persian text. Right-to-left should kick in automatically.

#### If RTL doesn't activate after step 3

The extension wires itself up on install, but on some setups (and after VS Code/Cursor updates) the imports list or the agent webviews need a manual nudge. Click the **RTL** indicator in the status bar (bottom-right of the editor) and run these actions in order — or use the Command Palette and search for `RTL for VS Code Agents:`:

1. **Configure Custom CSS Loader** — adds the RTL script to `vscode_custom_css.imports` in your settings.
2. **Check and Inject** — patches Claude Code / Codex / Gemini Code Assist webviews so RTL works inside their chat panels (Copilot and Cursor don't need this).
3. **Enable Custom CSS and JS** (from the Custom CSS Loader extension) → reload the window.

## And what about RTL for web chats!?

### (i.e. Claude.ai / NotebookLM / Perplexity / ChatGPT) and SaaSs (i.e. Slack / Monday / Heptabse)

### I've got you there also!!

[Multi-RTL Chrome Extension](https://multi-rtl.asia-digital.online)

is all you need!

### Check it out: [https://multi-rtl.asia-digital.online](https://multi-rtl.asia-digital.online)

## Now back to RTL for VS Code Agents:

Commands

- **RTL for VS Code Agents: Check and Inject** - Manually check and inject RTL into Claude Code, Codex, and Gemini Code Assist
- **RTL for VS Code Agents: Configure Custom CSS Loader** - Configure Custom CSS extension for Copilot Chat
- **RTL for VS Code Agents: Check for Updates** - Check GitHub for a newer version and install it
- **RTL for VS Code Agents: Remove All RTL Injections** - Restore all original files (run before uninstalling the extension)

Settings


| Setting                                       | Default | Description                                                                                              |
| --------------------------------------------- | ------- | -------------------------------------------------------------------------------------------------------- |
| `rtlForVsCodeAgents.autoInject`               | `true`  | Automatically inject RTL into new Claude Code / Codex / Gemini versions                                  |
| `rtlForVsCodeAgents.checkIntervalHours`       | `0`     | How often to check (0 = startup only)                                                                    |
| `rtlForVsCodeAgents.autoConfigureCustomCss`   | `false` | Automatically configure Custom CSS Loader                                                                |
| `rtlForVsCodeAgents.autoCheckUpdates`         | `true`  | Automatically check for extension updates from GitHub on startup                                         |
| `rtlForVsCodeAgents.updateCheckIntervalHours` | `24`    | How often to check for updates (0 = startup only)                                                        |
| `rtlForVsCodeAgents.userMessageBorder`        | `true`  | Show coral border on user messages. Easier to toggle via right-click on ↑↓ buttons                       |
| `rtlForVsCodeAgents.yoloCountdownSeconds`     | `5`     | YOLO mode countdown before auto-approve (0 = instant). Easier to change via right-click on the 💪 button |
| `rtlForVsCodeAgents.markdownPreviewRtl`       | `true`  | RTL in the Markdown document **Preview** tab — per-block direction, plus full RTL for RTL-dominant docs   |




Troubleshooting


| Problem                                         | Solution                                                                                        |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| "[Unsupported]" in title bar                    | Normal - this is expected when using Custom CSS                                                 |
| RTL not working in Claude Code / Codex / Gemini | Run "Check and Inject" command                                                                  |
| RTL not working in Copilot                      | Run "Configure Custom CSS Loader", then "Enable Custom CSS and JS"                              |
| RTL stopped after VS Code update                | The extension will notify you automatically — click "Enable Custom CSS" and run "Reload Window" |




Manual Installation (Advanced)

For manual installation or troubleshooting, scripts are available:

### Windows

```powershell
powershell -ExecutionPolicy Bypass -File .\install.ps1
```

### Mac/Linux

```bash
./install.sh
```

### Diagnostics

```powershell
# Windows
powershell -ExecutionPolicy Bypass -File .\diagnose-rtl.ps1

# Mac/Linux
./diagnose-rtl.sh
```

Changelog

### v1.0.12

- **RTL in the Markdown Preview tab, without the freeze:** new `rtlForVsCodeAgents.markdownPreviewRtl` setting (on by default). Every paragraph, heading, list item, blockquote and table cell picks its own direction from its content, so Hebrew/Arabic blocks read right-to-left while English blocks stay left-to-right. When a document is RTL overall, the content root gets a real `direction: rtl`, which also moves list markers and blockquote rules to the right side and flips table column order.
- **Why this is safe:** Cursor's Preview tab is ProseMirror-backed, and writing into its DOM is what caused the v1.0.8 freeze. The direction here comes from CSS plus a single `data-rtl-md` attribute written on the wrapper **above** the ProseMirror root (verified seven levels above `div.tiptap.ProseMirror`), which is outside the subtree ProseMirror observes. Nothing is ever written inside that root. The attribute is only rewritten when the value actually changes, and direction detection samples just the leading blocks with a short-lived cache, so the periodic pass stays cheap on large documents.
- Note that raw `<div dir="rtl">` in a Markdown file has no effect in this tab: ProseMirror parses HTML through its own schema and discards elements and attributes it doesn't model, so the `dir` never reaches the DOM. This setting is the supported way to get the same result.

### v1.0.11

- **Upgrades now actually take effect:** Extension folders are versioned, but nothing rewrote `vscode_custom_css.imports` on upgrade — `configureCustomCss()` was the only writer and it only runs automatically when `autoConfigureCustomCss` is on, which is off by default. So after installing a new VSIX the new version was installed and active while Custom CSS kept loading the **previous** version's script, with no indication anything was wrong. The extension now repairs its own import paths on every startup, and when it finds stale ones it offers to reload Custom CSS and JS (and then the window) for you instead of leaving you to run the disable/enable cycle by hand. Only entries the extension owns are rewritten; other imports are left untouched.

### v1.0.10

- **Fix Markdown preview freezing (regression from v1.0.8):** Cursor's Markdown document editor / preview is ProseMirror-backed, and ProseMirror re-parses the DOM whenever it detects an external mutation. The v1.0.8 table pass wrote inline styles and RLM marks into those tables every 200ms, so each write triggered a re-parse, each re-parse triggered another write — the renderer was measured blocked for up to 80 seconds on complex documents. RTL for Markdown tables is now done **purely in CSS** (`unicode-bidi: plaintext` on cells), with no DOM writes at all in those surfaces.
- **Fix RTL work leaking into Markdown documents:** `characterData` mutations report the text node, not an element, so the editor-area guard never matched them — every text change inside a Markdown document scheduled a full document-wide RTL pass. The guard now resolves text nodes through their parent.
- **Faster RTL detection:** RTL range matching is now a single compiled regex instead of a per-character `Array.some()` closure, `\p{L}` is no longer re-tested per character, and direction detection caps its scan, so the periodic pass stays cheap on long documents and wide tables.
- **Chat table styling is now idempotent:** `applyTableRTL()` only writes when the RTL state actually changed or a re-render stripped its styles, instead of rewriting every cell on every tick.

### v1.0.9

- **Cursor questionnaire answer RTL:** Hebrew/Arabic answers in Cursor's questionnaire UI (`.user-questionnaire-answer-text`) now get `direction: rtl` and `text-align: right` when the content is RTL, same as other user message bubbles.

### v1.0.8

- **RTL for Markdown tables:** Tables in Markdown document editor / preview (`.markdown-editor-react`, `.markdown-body`) now get proper RTL — `direction: rtl` plus `text-align: right` on `th`/`td` so mixed Hebrew/English is readable and flush right. English-only tables stay LTR. Lightweight pass only (no preview freeze). Also applies to tables inside chat markdown.

### v1.0.7

- **Fix the "installation appears to be corrupt" warning:** New auto-fix that reconciles the editor's `product.json` checksums with the modified `workbench.html` (the file the Custom CSS and JS Loader patches). Runs on startup (`rtlForVsCodeAgents.autoFixChecksums`, on by default) and also available as commands **"Fix Editor Checksums"** / **"Restore Editor Checksums"**. Keeps a backup at `product.json.orig.<version>` and self-heals after editor updates / Custom CSS enable-disable cycles. On Windows the install folder may require admin rights.

### v1.0.6

- **Fix Markdown Preview freeze in Cursor/VS Code:** Skip RTL processing on Markdown document surfaces only (`.markdown-editor-react`, `.ui-rich-text-editor[data-variant="document"]`, classic `.markdown-body` / `.markdown-preview`) so opening an `.md` file in Preview no longer freezes the IDE from MutationObserver / polling on hundreds of nodes.
- **Cursor chat RTL preserved:** Does not block `.editor-container` / `.editor-group-container` — Composer and agent messages keep RTL as before.

### v10.1.0

- **YOLO plan approval control:** Added `Auto Approve Plans` to the YOLO right-click popup, off by default, so `Accept this plan?` stays manual unless explicitly enabled

### v10.0.1

- **Restart Extension Host instead of Reload Window:** Post-injection notices now offer "Restart Extension Host" as the primary action — a lighter, faster operation than a full window reload. Applies to injection, removal, and settings-change flows. "Reload Window" remains available as a secondary option, and the Copilot path still requires it.

### v10.0.0

- **Search in conversation 🔍:** new search bar with in-place `<mark>` highlighting for every match across user + agent messages. Navigate with ↑/↓ or Enter / Shift+Enter. Case-insensitive, closes on × or Esc. Counter shows position (e.g. 3/12).
- **Outline for floating popups:** lighter gray 2px outline on the search bar and YOLO settings popup for better visibility.

### v9.1.0

- **Plan Documents RTL:** Claude Code's Plan/Review documents (separate tab) now fully support RTL — headings, paragraphs, lists, tables, and blockquotes align right for RTL content, while code blocks stay LTR. Injected via a lightweight inline script with proper CSP nonce support.

### v9.0.0

- **Codex (ChatGPT) support:** Full RTL support for OpenAI Codex chat — messages, input box, conversation title, Previous Messages section, navigation buttons, YOLO auto-approve, and user message borders
- **Smart message collapse for Codex:** Long user messages auto-collapse to ~5 lines with fade-out. Hover for "Show more" button, click to expand/collapse
- **Neutral text color in Codex:** Override Codex's blue-tinted text with clean neutral colors (light for dark theme, dark for light theme)

### v8.2.5

- **Fix RTL detection with attachments:** Skip attachment containers (filenames, dimensions) when detecting text direction, so Hebrew messages with attachments align correctly
- **Expand collapsed user messages:** Increase collapsed message preview from ~3 lines to ~5 lines

### v8.2.4

- **Fix session history list:** Items now have proper spacing and separator lines (override fixed height)
- **Fix header accent border:** Update selector for new Claude Code DOM structure
- **Move nav/YOLO buttons:** Repositioned next to "Ask before edits" button

### v8.2.2

- **Fix mention mirror RTL sync:** Fixed cursor misalignment in Claude Code 2.1.76+ input box — the new mentionMirror overlay now syncs RTL direction with the input, keeping the caret aligned with visible text

### v8.2.1

- **Bright scrollbar:** Chat panel scrollbar is now much more visible (brighter thumb, wider track) for easier navigation in long conversations

### v8.2.0

- **User message border toggle:** New `userMessageBorder` setting and instant right-click toggle on ↑↓ navigation buttons — toggle the coral border on user messages on/off without reload (persisted via localStorage)

### v8.1.0

- **YOLO Mode 💪 (auto-approve with countdown):** Toggle YOLO mode with the 💪 button to auto-approve all tool calls. A countdown progress bar with a **NO!** cancel button appears before each approval. Right-click the button to adjust the delay (0 = instant) and control whether plan approvals are auto-accepted. Settings are persistent via localStorage.
- **YOLO countdown settings:** Configurable via VS Code Settings (`yoloCountdownSeconds`) or right-click on the 💪 button for instant changes, including the new `Auto Approve Plans` toggle

### v8.0.1

- **Fix BiDi ordering in mixed Hebrew/English lines:** Lines starting with bold text followed by English in parentheses (e.g. `**term** (English explanation)`) now correctly align RTL. Fixed by injecting RLM anchors and switching from `unicode-bidi: plaintext` to `isolate`.

### v8.0.0

- **User message navigation (↑↓):** Jump between user messages in Claude Code chat with cyclic up/down buttons in the input footer
- **Copilot user message borders:** User messages in GitHub Copilot Chat now have a coral accent border matching Claude Code
- **Improve reload notifications:** Add 'Reload Window' button to all injections and removals — soft reload instead of manual Ctrl+Shift+P
- **Install/Uninstall scripts:** No longer force-restart VS Code — reload happens via extension notification button

### v7.5.6

- **Broad bidi-override fix:** Cancel Claude Code's `unicode-bidi: bidi-override` across all chat content (tables, lists, headings, etc.) — not just RTL-marked elements

### v7.5.5

- **Permission reject input RTL:** The free-text input in permission dialogs (e.g. "Make this edit?") now switches to RTL when typing Hebrew

### v7.5.4

- **Fix bidi-override on history title:** Session title and history list items now get `data-rtl-applied` marker so the bidi-override CSS fix covers them too

### v7.5.3

- **Fix Claude Code bidi-override:** Counter the global `* { unicode-bidi: bidi-override }` rule added in Claude Code v2.1.63 that broke all RTL text rendering

### v7.5.2

- **Fix Custom CSS stale imports:** Auto-update no longer accumulates old entries in `vscode_custom_css.imports` — old RTL paths are cleaned up automatically on each configure

### v7.5.1

- **Status Bar Quick Menu:** Click the `RTL v7.5.1` button in the status bar to open a quick menu with all extension actions — also triggers an update check in the background

### v7.5.0

- **Auto-Update:** Check for new versions from GitHub and install with one click — no more manual VSIX downloads
- **Status Bar Button:** Shows current version in the bottom bar; highlights when an update is available
- **Update Settings:** `autoCheckUpdates` and `updateCheckIntervalHours` control automatic checking
- **Post-Update Re-injection:** After updating, old RTL injections are automatically restored and re-injected with the new script
- **Remove Injections Command:** New "Remove All RTL Injections" command to cleanly restore all files before uninstalling

### v7.3.1

- **Session Title Line Clamp:** Session title limited to 3 lines, preventing long prompts from overflowing
- **UI Accent Borders:** Light purple border on history header, coral border on user messages

### v7.3.0

- **Conversation History RTL:** Session titles in the history dropdown align right for Hebrew/RTL content
- **History Dropdown UI:** Wider and taller dropdown, session names wrap instead of being truncated
- **Session Header Button:** Current session title wraps and grows with content instead of being clipped

### v7.2.0

- **Agent Questions RTL:** Question text, option labels, descriptions, and nav tabs in Claude Code's agent prompts (Plan Mode) now align right for Hebrew/RTL content
- **Agent Questions Input:** The "Other" free-text input in agent popups switches to RTL when typing Hebrew

### v7.1.0

- **Copilot RTL Detection:** Auto-detects if Copilot injection was lost after a VS Code update and notifies
- **English-only Notifications:** Fixes BiDi rendering issues in VS Code's notification UI

### v7.0.0

- **Gemini Code Assist:** RTL support for Google Gemini Code Assist chat
- **Auto Injection:** Detects and injects into Gemini Code Assist automatically
- **Smart RTL Detection:** Direction based on first strong character (skips emojis, numbers, bullets)
- **Majority Fallback:** Mixed Hebrew/English text (≥30% RTL letters) correctly detected as RTL
- **List Bullets Fix:** RTL list items no longer lose their bullets

### v6.0.0

- **Cursor Support:** Claude Code in Cursor now supported
- **Auto Injection:** Detects Claude Code in VS Code, Cursor, and Antigravity

### v5.0.0

- **VS Code Extension:** Now available as a proper VS Code extension (.vsix)
- **Selectors:** Update Claude Code selectors for new version

### v4.3.3

- **Diagnostics:** Fix selector extraction

### v4.2.1

- **Antigravity Chat:** Fix streaming RTL
- **Selectors:** Update Claude Code and Antigravity selectors



Older versions

### v4.2.0

- Smarter installer - detects all Claude Code versions

### v4.0.0

- Add Claude Code injection for Antigravity
- Fix streaming messages RTL detection

### v3.0.0

- Fix input box RTL flickering

### v2.0.0

- Add automated installation scripts
- Add RTL support for input boxes

### v1.0.0

- Initial release with GitHub Copilot Chat support



## Changes from upstream

This fork adds the following on top of `[GuyRonnen/rtl-for-vs-code-agents](https://github.com/GuyRonnen/rtl-for-vs-code-agents)` v10.1.0:

- **Cursor support** — RTL for Cursor's native chat (Composer / Agent panel):
  - Agent reply messages (`.markdown-root > div`) are right-aligned, with code blocks preserved as LTR.
  - User message bubbles align right (single-line and multi-line) via a `direction: rtl` rule on `.composer-human-message .justify-between`.
  - The Composer input box (`.composer-input div[contenteditable="true"]`) switches direction based on typed content.
- `rtlForVsCodeAgents.monacoRtlEnabled` **setting** (default: `false`) — controls whether RTL is applied inside Monaco editor instances. Off by default because right-aligning Hebrew/Arabic inside a regular code editor window breaks caret movement and text selection. Enable it if you specifically want Copilot's Monaco-based chat input to flip direction; chat messages get RTL either way.
- **Settings sync under Custom CSS Loader** — the extension now writes a small `rtl-config.js` file next to the main script and adds it to `vscode_custom_css.imports` *before* the main script. Required because the Custom CSS Loader inlines imported scripts into `workbench.html` and doesn't re-run the extension's config block on settings changes — without this, the main script couldn't see updated settings on a Disable/Enable cycle.

See [PR #11](https://github.com/GuyRonnen/rtl-for-vs-code-agents/pull/11) on the upstream repo for the full diff.

## Credits

This extension is a fork of `[GuyRonnen/rtl-for-vs-code-agents](https://github.com/GuyRonnen/rtl-for-vs-code-agents)` by Guy Ronnen — all original features and the vast majority of the code are his work.

The **YOLO Mode** feature (auto-approve with countdown) is based on the original idea and JavaScript snippet by [Chris Le](https://github.com/chrisle) — see the [original gist](https://gist.github.com/chrisle/c6f187278e27f0168d982cd84de08b92).

## License

GPL-3.0, inherited from the original project. See [LICENSE.txt](./LICENSE.txt). Original work © Guy Ronnen and contributors; fork modifications © 2026 udah1, also released under GPL-3.0.