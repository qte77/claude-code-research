# CC Changelog & Native Sources: New Uncovered Features Detected

## Changelog Monitor Report

Last scanned version: **2.1.215**
New versions detected: **25**

### New Versions Summary

| Version | Features | Covered | Uncovered |
|---------|----------|---------|-----------|
| 2.1.241 | 1 | 0 | 1 |
| 2.1.240 | 1 | 0 | 1 |
| 2.1.239 | 59 | 0 | 59 |
| 2.1.238 | 39 | 1 | 38 |
| 2.1.237 | 2 | 0 | 2 |
| 2.1.236 | 33 | 0 | 33 |
| 2.1.235 | 19 | 0 | 19 |
| 2.1.234 | 51 | 0 | 51 |
| 2.1.233 | 20 | 0 | 20 |
| 2.1.232 | 49 | 1 | 48 |
| 2.1.231 | 1 | 0 | 1 |
| 2.1.229 | 32 | 1 | 31 |
| 2.1.228 | 18 | 0 | 18 |
| 2.1.227 | 5 | 0 | 5 |
| 2.1.226 | 1 | 0 | 1 |
| 2.1.225 | 14 | 0 | 14 |
| 2.1.224 | 31 | 0 | 31 |
| 2.1.223 | 19 | 0 | 19 |
| 2.1.222 | 21 | 1 | 20 |
| 2.1.221 | 39 | 1 | 38 |
| 2.1.220 | 1 | 0 | 1 |
| 2.1.219 | 24 | 1 | 23 |
| 2.1.218 | 36 | 0 | 36 |
| 2.1.217 | 20 | 0 | 20 |
| 2.1.216 | 40 | 0 | 40 |

### Feature Coverage Details

#### v2.1.241

- **[UNCOVERED]** - Bug fixes and reliability improvements

#### v2.1.240

- **[UNCOVERED]** - Bug fixes and reliability improvements

#### v2.1.239

- **[UNCOVERED]** - Cost estimates (`/cost`, status line, `--max-budget-usd`) now include the 1.1× US-only-inference premium for data-residency workspaces
- **[UNCOVERED]** - Added the one-time fullscreen renderer offer on Bedrock, Vertex, Foundry and other previously excluded setups; new installs there now start in fullscreen
- **[UNCOVERED]** - Added `/claude-api upgrade` to migrate Python projects from `anthropic` 0.x to 1.x, and updated the skill's Python reference for 1.x (timeouts use `anthropic.Timeout`, not `httpx.Timeout`)
- **[UNCOVERED]** - Cloud sessions: plugins synced from claude.ai now show as `name@synced`, work with `claude plugin enable/disable <name>@synced`, and never override a same-named plugin you installed
- **[UNCOVERED]** - Alpine/musl builds: native image paste, clipboard, and audio-capture add-ons now load (musl-built binaries instead of glibc ones refused by the runtime)
- **[UNCOVERED]** - The usage-limit message shown when your monthly spend limit is already used up now also says when your session or weekly limit resets
- **[UNCOVERED]** - Fixed Bedrock streaming behind proxies that strip the response Content-Type header, which silently doubled billed API calls by re-running every turn non-streaming
- **[UNCOVERED]** - Fixed Claude Code hanging at startup behind an HTTPS proxy when using Bedrock with an SSO profile and `awsAuthRefresh` — the credential pre-check now honors `HTTPS_PROXY`
- **[UNCOVERED]** - Fixed a raw crash dump when starting Claude Code from a directory that no longer exists; it now prints a clear message
- **[UNCOVERED]** - Fixed Edit and Write calls pausing for about 5 seconds in JetBrains IDE terminals when the Claude Code plugin is connected
- **[UNCOVERED]** - Fixed a race where pressing Esc with a prompt queued could let the next turn finish early, leaving the session idle while Claude was still working and letting a later resubmit repeat actions
- **[UNCOVERED]** - Fixed WebFetch retaining expired page content in memory for the whole session instead of the intended 15 minutes
- **[UNCOVERED]** - Fixed cloud sessions (Claude Code on the web, desktop and mobile apps) resuming out of plan mode after an idle worker restart
- **[UNCOVERED]** - Fixed MCP elicitation forms taller than the terminal being clipped in fullscreen mode: the form now fits the window, with hidden fields reachable by scrolling and Accept/Decline always visible
- **[UNCOVERED]** - Fixed remote MCP servers staying failed after a transient 5xx on a mid-session reconnect in cloud sessions or via SDK `setMcpServers()`
- **[UNCOVERED]** - Fixed custom session titles disappearing from `/resume` after more than ~64 KB of conversation was written following the rename
- **[UNCOVERED]** - Fixed `claude -c`/resume picking up sessions from a different directory whose path differed only by characters like `_`, `-`, or `.`
- **[UNCOVERED]** - Fixed `/resume` and the agents view showing a session as recently changed (and reordering it) when only its file was touched or it was merely reopened
- **[UNCOVERED]** - Fixed `/resume` in all-projects mode telling you to `cd` into a deleted directory (e.g. a removed worktree); such sessions now resume in the current directory
- **[UNCOVERED]** - Fixed the `dark-ansi` theme rendering expanded tool results in fullscreen mode with text the same color as the background
- **[UNCOVERED]** - Fixed the fullscreen renderer prompt reappearing on every launch when it could never be answered; it now stops after being shown on three launches
- **[UNCOVERED]** - Fixed `.worktreeinclude` patterns starting with `**/` silently matching nothing when the target lived in a gitignored directory
- **[UNCOVERED]** - Fixed agents, skills, and commands whose `.md` file starts with a UTF-8 BOM being silently ignored
- **[UNCOVERED]** - Fixed `/insights` echoing literal `<message>` tags in its response on some models
- **[UNCOVERED]** - Fixed marketplace `metadata.pluginRoot` having no effect: bare plugin source names now resolve under it as the docs describe
- **[UNCOVERED]** - Fixed mouse movement in browser-based terminals inserting text like `"35;150;7M"` into the prompt when a mouse report arrived split across writes
- **[UNCOVERED]** - Fixed custom theme overrides for the effort/ultracode status badge colors being ignored
- **[UNCOVERED]** - Fixed OpenTelemetry trace fragmentation: tool executions deferred by a `PreToolUse` hook now resume in the original turn's trace instead of starting a new trace
- **[UNCOVERED]** - Fixed vim mode in the agent view: Escape now switches to NORMAL mode and keeps your text instead of clearing the prompt
- **[UNCOVERED]** - Fixed the `selection:copy` keybinding silently dropping a text selection that had been extended with Shift+Arrow keys
- **[UNCOVERED]** - Fixed the `/voice` startup tip still appearing after voice dictation was enabled via the `voice.enabled` setting
- **[UNCOVERED]** - Fixed shell-mode (`!`) Tab completion dropping the `./` from a `./script` path, which left a command the shell couldn't run
- **[UNCOVERED]** - Fixed fullscreen mode answering a permission prompt or pressing a button when you clicked the terminal window only to bring it back into focus
- **[UNCOVERED]** - Fixed slash-command panels (e.g. `/config`, `/model`) in fullscreen mode covering the latest messages; the conversation now stays pinned above the panel
- **[UNCOVERED]** - Fixed the `/workflows` detail dialog overflowing the terminal and losing its header off-screen when opened while Claude is still responding
- **[UNCOVERED]** - Fixed the Linux sandbox making a nonexistent `.git/config.worktree` unreadable, which broke every sandboxed git command in repos with `extensions.worktreeConfig` set
- **[UNCOVERED]** - Fixed hooks failing with "posix_spawn ENOENT" after the session's working directory was deleted; they now run from the project root or home directory instead
- **[UNCOVERED]** - Fixed `claudeMdExcludes` not excluding a symlinked `.claude/rules` file when the pattern names the rules directory or the symlink rather than its target
- **[UNCOVERED]** - Fixed runaway session-title syncing to Remote Control when two Claude Code processes shared one background job's state (2.1.232 regression); title updates are now deduplicated and rate-limited
- **[UNCOVERED]** - Fixed sessions whose title starts with `/` being unaddressable by `SendMessage` and shown as "(untitled)" in `ListAgents`
- **[UNCOVERED]** - Fixed Ctrl+W, Ctrl+U, Ctrl+K, Option+Backspace, Option+D and vim `df`/`dt` leaving a broken `[Pasted text #N]` placeholder when the cursor was inside it
- **[UNCOVERED]** - Fixed masked (password-style) inputs such as the login code field letting their text be pasted back with Ctrl+Y elsewhere or saved to prompt history when cleared with double Esc
- **[UNCOVERED]** - Fixed Ctrl+Backspace deleting one character instead of a word in search boxes
- **[UNCOVERED]** - Fixed a request rejected by an organization policy check being re-sent before the rejection was shown
- **[UNCOVERED]** - Improved the reminder shown after compaction so a skill's original arguments are not re-run as a new request
- **[UNCOVERED]** - Long file paths on tool-use rows now truncate in the middle to stay on one line
- **[UNCOVERED]** - Remote sessions keep sending keep-alives while a long `SessionStart` or `Setup` hook runs, so the container is not idle-reaped mid-hook
- **[UNCOVERED]** - `/goal`: repeat check-ins on long-running background work now back off (30 min, then 1 h, then every 2 h) instead of repeating every 30 minutes
- **[UNCOVERED]** - `/goal`: resuming a session from the `claude --resume` picker now restores its active goal
- **[UNCOVERED]** - `ListAgents` now tells a session its own name (the one peers use to message it), and `SendMessage` to your own name says so instead of "no agent named …"
- **[UNCOVERED]** - `ListAgents` and `/list-agents` now list your live teammates (previously only subagents and other sessions appeared, so a reachable teammate looked absent)
- **[UNCOVERED]** - `keybindingFlavor: "readline"` now also matches Bash for word keys: Alt+F and Ctrl/Option+→ stop at the end of the word, Alt+D deletes to it (Ctrl+Y pastes it back), and punctuation separates words
- **[UNCOVERED]** - Persistent retry mode (`CLAUDE_CODE_RETRY_WATCHDOG`) now fails immediately on organization spend-limit and out-of-credits errors instead of waiting indefinitely for a reset
- **[UNCOVERED]** - Claude in Chrome: `/clear` now closes the session's Chrome tab group, and empty groups are closed on `/resume` and when Claude Code exits
- **[UNCOVERED]** - Remote sessions: images uploaded from mobile now include their saved file path, so Claude can copy them into files it creates
- **[UNCOVERED]** - Claude Code on the web: requests from Bash and other tools to non-API anthropic.com hosts (e.g. www, docs) now go through the session's network proxy, so your environment's allowed domains apply
- **[UNCOVERED]** - Remote Control: clearer message and `claude doctor` wording when Remote Control isn't enabled for your account
- **[UNCOVERED]** - Windows: cross-session messaging is now available, so Claude Code sessions across your machines can message each other with `SendMessage` and find each other with `ListAgents`, as on macOS and Linux
- **[UNCOVERED]** - [VSCode] "View usage" in the usage-limit banner now sits inline with the warning text instead of floating mid-banner

#### v2.1.238

- **[covered]** - Fixed Remote Control model picks made on a phone or web not updating the model shown in the terminal
  - Covered by: `cc-native/configuration/CC-env-vars-reference.md`
- **[UNCOVERED]** - Added a `keybindingFlavor` setting: set it to `"readline"` to make Ctrl+W in the prompt delete back to the previous whitespace, as in Bash; the default (`"classic"`) is unchanged
- **[UNCOVERED]** - Plugin marketplaces: `headersHelper` on a url marketplace or a catalog entry runs a command that mints HTTP headers (e.g. a short-lived token) for catalog and same-origin archive fetches
- **[UNCOVERED]** - A catalog entry's `headersHelper` runs only when you install or update that plugin, after its command is shown; `claude plugin install/update` ask `[y/N]` (or pass `-y`)
- **[UNCOVERED]** - Added `claude self-hosted-runner --defer-shutdown-max-min <minutes>`: on SIGTERM, keep serving attached sessions, park what is left after that many minutes, then exit
- **[UNCOVERED]** - Added `claude self-hosted-runner --proxy-authorization-command` / `--proxy-authorization-file` for egress proxies that require a freshly issued `Proxy-Authorization` header on every connection
- **[UNCOVERED]** - Fixed unbounded memory growth in long interactive sessions: subagent tool results are now released once they leave the recent display window
- **[UNCOVERED]** - Fixed custom, project, and plugin output styles drifting back to the default voice mid-session
- **[UNCOVERED]** - Fixed `CLAUDE_CODE_ENABLE_PROMPT_SUGGESTION=true` not keeping prompt suggestions on when your account is near, but not over, its usage limit
- **[UNCOVERED]** - Fixed worktree-isolation Bash refusals telling you to remove a redirect when the command had none
- **[UNCOVERED]** - Fixed self-hosted runners occasionally being removed by the server after a single slow or lost poll request, handing their healthy session to another runner
- **[UNCOVERED]** - Fixed MCP elicitation dialogs showing nothing for URLs longer than 4,096 characters, and permission prompts dropping the "don't ask again" option when the project path didn't fit the terminal width
- **[UNCOVERED]** - Fixed leftover `/tmp/claude-*-cwd` files when a Bash command is killed, times out, or is interrupted
- **[UNCOVERED]** - Fixed held Backspace being ignored on terminals that send Ctrl+H for Backspace when keystrokes arrive in large bursts (slow SSH/mosh links)
- **[UNCOVERED]** - Fixed text-wrapping in permission prompt diffs: lines containing wide multi-code-point characters (such as emoji) or tabs are no longer clipped
- **[UNCOVERED]** - Fixed killing a suspended (Ctrl+Z) session sometimes leaving the terminal in bracketed-paste mode with the cursor hidden
- **[UNCOVERED]** - Fixed stdio MCP servers receiving a `server/discover` request before `initialize`, forcing lazy servers to start their backend on every session open
- **[UNCOVERED]** - Fixed a proxy's refusal of a connection being reported as a generic network error instead of naming the proxy
- **[UNCOVERED]** - Fixed the `/model` and `/effort` cache-miss warning appearing when the prompt cache had already expired
- **[UNCOVERED]** - Fixed per-task Stop from the Remote Control tasks panel doing nothing on CLI-hosted sessions
- **[UNCOVERED]** - Fixed remote sessions exiting when a client delivered a user message without a valid role
- **[UNCOVERED]** - Fixed Remote Control sessions started by `claude remote-control` inheriting session-scoped environment variables from the launching shell
- **[UNCOVERED]** - Fixed a Remote Control session whose process crashed staying unavailable until `claude remote-control` was restarted; it can now be reused when you next message it
- **[UNCOVERED]** - Fixed Remote Control messages sent from the web or Desktop while Claude is mid-turn disappearing from the transcript after the turn finishes
- **[UNCOVERED]** - Fixed Remote Control disconnecting with "login expired" when a brief network hiccup delays renewing your sign-in; it now retries and stays connected
- **[UNCOVERED]** - Fixed Remote Control reporting a failed reconnect on sign-out; signing out now ends the session with a clear message
- **[UNCOVERED]** - Fixed `ListAgents`/`SendMessage` reporting "Remote Control is not connected" in sessions run by `claude remote-control` (server mode) or Desktop/IDE hosts; they now list and reach Remote Control peers
- **[UNCOVERED]** - Fixed `ListAgents` and `SendMessage` exposing the idle worker that the agent view pre-warms for your next background session; it now appears only once a task claims it
- **[UNCOVERED]** - Cross-session messaging: sending to a session on this machine that refuses inbound messages (e.g. `crossSessionInbound: "refuse"`) now reports "refused" to the sender instead of a silent success
- **[UNCOVERED]** - Cross-session messaging: a session whose inbox drops your messages (rate limit or full queue) now tells your session, instead of the messages vanishing silently
- **[UNCOVERED]** - Improved startup: bare `claude` starts sooner on macOS
- **[UNCOVERED]** - Improved Bash tool permission checking for zsh-specific syntax in shell conditionals
- **[UNCOVERED]** - Improved Remote Control connection resilience: brief HTTP 403 refusals from a network edge, VPN, or proxy are now tolerated for up to 3 minutes, with the refusing party named when a block persists
- **[UNCOVERED]** - Improved startup responsiveness: the automatic update check now runs about 10 seconds after launch instead of competing with startup for CPU
- **[UNCOVERED]** - Updated the bundled `claude-api` skill for the Managed Agents Aug 19 release: web search/fetch domain settings and memory stores on self-hosted sandboxes
- **[UNCOVERED]** - Changed Ctrl+L and Cmd+K in fullscreen to always just repaint — the double-press `/clear` shortcut was removed, and 1-row nvim terminals no longer trigger automatic `/clear` loops
- **[UNCOVERED]** - Changed `claude mcp list` and `claude mcp get` to show disabled servers as `⊘ Disabled` instead of connecting to them for a health check
- **[UNCOVERED]** - MCP `headersHelper` in a project `.mcp.json`, and inline MCP servers in project or `--add-dir` agent files, now require that folder's trust dialog to have been accepted (also under `claude -p`)
- **[UNCOVERED]** - MCP `headersHelper` from a project `.mcp.json`, plugin, or agent file runs without inherited credential env vars; user, managed and claude.ai-scope helpers now run from the Claude config dir

#### v2.1.237

- **[UNCOVERED]** - Fixed prompt caching for sessions using an LLM gateway or custom base URL
- **[UNCOVERED]** - Added a built-in "Concise" output style: Claude leads with results and skips preamble and narration, while doing the work just as thoroughly. Select it under Output style in /config.

#### v2.1.236

- **[UNCOVERED]** - Added `ANTHROPIC_DEFAULT_MODEL` environment variable: sets the model new sessions start on, while a `/model` pick still overrides it and persists across restarts (unlike `ANTHROPIC_MODEL`)
- **[UNCOVERED]** - Added `notify_when_idle` to cross-session `SendMessage`: ask another Claude Code session on this machine to send one notice when it next goes idle — opt-in, one-shot, no polling (macOS and Linux)
- **[UNCOVERED]** - Sandbox: on macOS, wildcard read-deny rules (e.g. `**/.env`) now take precedence inside allowed read regions, cover matched directories' contents, and can't be bypassed by renaming the denied file
- **[UNCOVERED]** - Fixed clipboard copy, background housekeeping, background sessions, and local MCP logs breaking after the directory a session had switched into was removed (since 2.1.229)
- **[UNCOVERED]** - Fixed the fullscreen renderer failing permanently after a single failed start: it now falls back to the classic renderer instead of exiting on every subsequent launch
- **[UNCOVERED]** - Fixed the `/model` picker rendering taller than the terminal: it now shows only as many models as fit the window, with the rest reachable by scrolling
- **[UNCOVERED]** - Fixed `SendMessage` calls being rejected when a malformed closing tag left the message text inside the summary field
- **[UNCOVERED]** - Fixed unhandled promise rejections when a subprocess fails to start, for example `powershell.exe` on WSL with Windows interop disabled (regression in 2.1.234)
- **[UNCOVERED]** - Fixed fullscreen mode sometimes not showing a newly sent message until the next update after the terminal was resized
- **[UNCOVERED]** - Fixed a blank band that could remain above the prompt after clearing a multi-line prompt, and panes not repainting after resizing the terminal away and back, in fullscreen mode
- **[UNCOVERED]** - Fixed the managed-settings approval prompt sometimes not appearing at startup while still capturing the first keypress as approval
- **[UNCOVERED]** - Fixed terminal tab titles jumping in tmux (iTerm tmux integration): the title is now written only when its text changes instead of animating every 960ms
- **[UNCOVERED]** - Fixed an unclear error when the cloud environments list came back empty or malformed
- **[UNCOVERED]** - Fixed the Fable 5 first-time usage-credits prompt auto-selecting the fallback model after 60 seconds with no answer when using Remote Control
- **[UNCOVERED]** - Fixed spinner tips never appearing, with a repeated background error, when the cached guest-pass reward in `~/.claude.json` was malformed
- **[UNCOVERED]** - Fixed skills hot-reload in SDK/VS Code sessions raising an error on every skills change after the session's working directory was deleted (2.1.229+)
- **[UNCOVERED]** - Fixed self-hosted runner sessions released on idle, retire, or startup timeout occasionally resuming on another runner before the post-session hook had finished
- **[UNCOVERED]** - Fixed the Clawd mascot's eyes and feet rendering unevenly in iTerm2 at some font sizes
- **[UNCOVERED]** - Fixed occasional runaway session recaps: recap text (automatic and `/recap`) is now capped at 400 characters, cut at a word boundary
- **[UNCOVERED]** - Improved startup performance: the session counter is now written in the background
- **[UNCOVERED]** - Improved auto mode: `Monitor` allow rules are now set aside while auto mode is active, so Monitor commands are reviewed the same way Bash commands are
- **[UNCOVERED]** - Improved auto mode on Bedrock, Vertex AI, and Foundry, and when telemetry is disabled: the classifier now uses the same defaults as on the Claude API, including severity-scored classification
- **[UNCOVERED]** - Improved auto mode: the git status check can no longer be fooled by a repo's `status.showUntrackedFiles=no` setting into reporting a clean tree
- **[UNCOVERED]** - Changed the `/model` picker to highlight only the newest model's name, so the highlight marks the new release rather than an arbitrary subset of the list
- **[UNCOVERED]** - `/goal`: an idle session whose goal is parked behind long-running background work now checks in automatically after 30 minutes (then 1h, 2h) instead of waiting for you to return
- **[UNCOVERED]** - `/usage` now shows the usage-credits spend row for Team and Enterprise members, and shows a capped row at 0% before anything is spent
- **[UNCOVERED]** - SIGTERM in print/SDK mode no longer records an interrupted turn or synthetic tool denials before exiting; running commands are still terminated and the process still exits with code 143
- **[UNCOVERED]** - Pressing Enter on a slash-command typo or a command unavailable in this session now reports it instead of running the closest fuzzy match; prefixes and aliases still run
- **[UNCOVERED]** - Remote Control now marks a session offline within seconds when the CLI exits or its terminal closes
- **[UNCOVERED]** - `SendMessage` now refuses further messages to a session up front once a rapid burst would exceed what that session's inbox accepts, instead of reporting them sent while they were dropped
- **[UNCOVERED]** - Aligned the session title chip on the prompt border with the footer's right edge
- **[UNCOVERED]** - Right-aligned footer items (goal indicator, session state, background agent status) and truncated notices now share a consistent right margin with the rest of the prompt area
- **[UNCOVERED]** - [VSCode] Added screen reader support for the transcript: live announcements for replies, permission requests, errors, and status changes, plus per-turn heading navigation

#### v2.1.235

- **[UNCOVERED]** - Added an optional `spellcheck` setting that underlines misspelled words in the prompt input as you type, using your installed `aspell`, `hunspell`, or `ispell`
- **[UNCOVERED]** - Fixed whole-prompt-cache invalidation when a language server disconnected or reconnected mid-session
- **[UNCOVERED]** - Fixed nested markdown list items misaligning at depth 3+ and added a hanging indent to wrapped list items in the terminal UI
- **[UNCOVERED]** - Fixed prompt input highlights (slash commands, keywords, mentions) appearing shifted by one or more characters in some multi-line prompts
- **[UNCOVERED]** - Fixed Shift+Tab inside the permission prompt's comment field approving the edit and granting session-wide edit permission instead of closing the field
- **[UNCOVERED]** - Fixed the Agent tool advertising a general-purpose default in sessions where that agent is unavailable: an omitted `subagent_type` there now gets a clear error listing the available agents
- **[UNCOVERED]** - Fixed notebook cell delete/replace approval dialogs silently omitting the existing cell content when the notebook or cell could not be read; the dialog now says why
- **[UNCOVERED]** - Fixed slash commands run while Claude is responding showing HTML entities instead of the actual characters
- **[UNCOVERED]** - Fixed the prompt footer not showing the "Update installed" restart notice after a background auto-update
- **[UNCOVERED]** - Fixed the expanded task list (`ctrl+t`) always starting collapsed when resuming or relaunching into a session that still has open tasks
- **[UNCOVERED]** - Improved memory and CPU usage while cloud sessions such as `/ultrareview` or `/autofix-pr` run in the background — their event streams are no longer re-scanned and re-rendered on every update
- **[UNCOVERED]** - Improved permission dialogs: display text and "don't ask again" options now always match what a grant would cover, and "don't ask again" is withheld when contents cannot be fully displayed
- **[UNCOVERED]** - Improved the embedded `grep` in native macOS/Linux builds: pathological patterns now fail fast instead of exhausting memory, and `-m N` with `-A/-C` prints correct context
- **[UNCOVERED]** - Improved the context-limit error to say when auto-compact is off and point to `/config` to re-enable it
- **[UNCOVERED]** - Vim mode: NORMAL mode and cursor position are now preserved when toggling the detailed transcript (ctrl+o) or closing a panel
- **[UNCOVERED]** - Dialogs: arrow keys and Enter pressed in quick succession now select the option you navigated to instead of the previously highlighted one
- **[UNCOVERED]** - `SendMessage` now refuses messages too large for cross-session delivery up front instead of silently dropping them
- **[UNCOVERED]** - Remote Control: `claude rc` now applies the same enterprise-gateway availability check as interactive startup
- **[UNCOVERED]** - [VSCode] Fixed focus jumping between open Claude tabs on its own when a window with several Claude panels is restored or reloaded

#### v2.1.234

- **[UNCOVERED]** - Added the optional `CLAUDE_CODE_PROJECT_DIR_NAME` environment variable: hosts that give each session its own config directory can choose a short name for the per-project transcript directory
- **[UNCOVERED]** - Added the `selection:clear` keybinding action, so a key can be bound to clear an in-app text selection; also works in the agents view
- **[UNCOVERED]** - Added a GitLab merge request badge to the footer and statusline: repos with a GitLab remote and an authenticated glab CLI show MR !N with draft/pending/green states
- **[UNCOVERED]** - Claude Code now continues your session automatically when a claude.ai usage limit resets; turn it off in `/config` ("Continue automatically at usage limit")
- **[UNCOVERED]** - Claude is now told to use your account email only to identify you, and not to send it to unrelated services unless you ask
- **[UNCOVERED]** - Security: remote file reads, session restore, CLAUDE.md includes, workflow scripts and file uploads now reject Windows NT-namespace (`\??\`) paths, hardening the remaining pre-approval file accesses against the NTLM credential-leak vector
- **[UNCOVERED]** - Fixed auto mode in very long sessions repeatedly re-checking and denying sandboxed commands' network access after the conversation had been compacted
- **[UNCOVERED]** - Fixed session-scoped permission answers (including denies) being dropped when answering background subagent tool permission prompts
- **[UNCOVERED]** - Fixed a crash when an API response on the non-streaming fallback path (typically via third-party gateways) contained a thinking block missing its thinking field or a text block missing its text field
- **[UNCOVERED]** - Fixed markdown rendering becoming extremely slow for some messages containing unusual Unicode sequences
- **[UNCOVERED]** - Fixed `SendMessage` rejecting a recipient copied from `ListAgents` when the session name is at the 200-character cap or emoji-heavy
- **[UNCOVERED]** - Fixed repository detection mis-reading the host of git remotes with unusual userinfo, producing links and repo-specific behavior for the wrong host
- **[UNCOVERED]** - Fixed MCP diagnostics printing resolved secrets: scope-conflict warnings now show the configured `${VAR}` form, and connection-failure details show only the server origin
- **[UNCOVERED]** - Fixed `strictKnownMarketplaces` allowlists accepting SCP-style git marketplace sources whose host differs from the one git would actually connect to
- **[UNCOVERED]** - Fixed modal text such as the `/login` OAuth URL losing characters when copied in fullscreen
- **[UNCOVERED]** - Fixed a `---` horizontal rule in rendered markdown running into the line after it
- **[UNCOVERED]** - Fixed consecutive shell commands splitting into multiple "Ran 1 shell command" rows when todo/task updates were interleaved between them
- **[UNCOVERED]** - Fixed dialogs like `/permissions` opened while a `!` shell command was running being dismissed when the command finished
- **[UNCOVERED]** - Fixed a queued `!` shell command being sent to the model as plain text after pressing up-arrow to edit the queued input
- **[UNCOVERED]** - Fixed queued messages reappearing in the prompt history while still queued, Esc while selecting a queued message no longer interrupts the turn, and `!` mode no longer sticks after a mid-turn submit
- **[UNCOVERED]** - Fixed accepting the "Try the new fullscreen renderer?" prompt restarting the session without its permission mode (e.g. `--dangerously-skip-permissions`), tool allow/deny rules, model or effort flags
- **[UNCOVERED]** - Fixed `/tui` dropping launch `--allowed-tools`/`--disallowed-tools` rules when it restarts; it now declines to switch, with the reason, when the session has restrictions a restart can't carry over
- **[UNCOVERED]** - Fixed trust prompts omitting the repository-wide scope warning when the directory was first seen before the repository existed there
- **[UNCOVERED]** - Fixed a case where an IDE diff tab closing during a permission re-prompt could answer the new prompt with the previous input
- **[UNCOVERED]** - Fixed: files sent to the user during Remote Control sessions hosted by Claude Code Desktop or VS Code now upload, so they open on phone and web instead of showing an empty card
- **[UNCOVERED]** - Fixed: after `/login` while `CLAUDE_CODE_OAUTH_TOKEN` is set, the stale-token reminder no longer leaks into Claude's automatically resumed turn — it now appears only to you
- **[UNCOVERED]** - Fixed: permission previews now relay only to channel servers admitted by the inbound trust gate, and a server's explicit permission-capability opt-out is honored
- **[UNCOVERED]** - Fixed: credential masking on relayed permission previews can no longer hide commands, paths, or destinations from the approver; oversized private-key blocks now redact under full-strength redaction
- **[UNCOVERED]** - Fixed: provider API tokens that mask on permission previews now mask even when directly followed by shell delimiters
- **[UNCOVERED]** - Fixed Claude Desktop inter-session messages being silently dropped by the recipient session when cross-session messaging read as disabled, which left the sender's query "thinking" for many minutes
- **[UNCOVERED]** - Remote Control: signing this computer in to a different claude.ai account or organization now stops the running session within seconds and says why, instead of a misleading HTTP 404 hours later
- **[UNCOVERED]** - Remote Control sessions started from Claude Code Desktop or VS Code now keep phones and claude.ai/code updated on the session's permission mode (and claude.ai/code on the model) as they change
- **[UNCOVERED]** - Remote Control: effort picks made on a phone or on claude.ai/code now apply to terminal- and Desktop/VS Code-hosted sessions, and the session publishes its effort level to connected clients
- **[UNCOVERED]** - `SendMessage` and `ListAgents` now say when your account's session list was too long to check completely, instead of treating unseen sessions as absent
- **[UNCOVERED]** - Expired Anthropic profile credential now points you at `/login` when a claude.ai login would take precedence
- **[UNCOVERED]** - Improved the transcript: your own prompts now render markdown (highlighted code blocks, inline code, lists) the same way replies do
- **[UNCOVERED]** - Improved the "API returned an empty or malformed response" error to say what came back (content type, body kind, size, request ID) and why the original streaming request failed
- **[UNCOVERED]** - Improved auto-generated session titles to read as short, specific names (e.g. "Login button bug") rather than sentences restating your request (e.g. "Fix the login button on mobile")
- **[UNCOVERED]** - Reduced the context cost of loading the built-in `claude-api` skill from ~200k+ tokens to ~25k by loading reference docs on demand
- **[UNCOVERED]** - `/permissions` can now be opened while Claude is working — rule changes apply to the rest of the current turn
- **[UNCOVERED]** - `/add-dir <path>` can now be used while Claude is working; `/add-dir`, `/autocompact`, `/theme`, `/help`, `/config` and `/advisor` dialogs open mid-turn in the fullscreen TUI
- **[UNCOVERED]** - `/goal` now clears itself with a notice when a turn dies on an unrecoverable error (e.g. revoked auth, an exhausted credit balance, or a context overflow) instead of staying armed
- **[UNCOVERED]** - `/goal`: when background tasks keep a goal waiting for 30+ minutes, Claude now checks in on them instead of waiting indefinitely (set `CLAUDE_CODE_GOAL_CHECKIN_MINUTES=0` to opt out)
- **[UNCOVERED]** - `claude setup-token` now rejects unexpected extra arguments instead of silently ignoring them
- **[UNCOVERED]** - Changed Esc in fullscreen mode to no longer clear a mouse text selection: it interrupts or dismisses as usual and the selection stays highlighted
- **[UNCOVERED]** - Removed the redundant "Allowed by auto mode classifier" line that auto mode showed under every Agent tool call
- **[UNCOVERED]** - Removed the "Default teammate model" setting from `/config`; agent-team teammates now use the leader's model unless the spawn names one
- **[UNCOVERED]** - Dimmed the elapsed-time counter on the running tool header so it no longer competes with the bold counts
- **[UNCOVERED]** - Background task notifications delivered between turns are now sent to the model inside `<system-reminder>` tags, matching mid-turn delivery
- **[UNCOVERED]** - Mantle: skip the admin-pin availability probe at startup when a main-loop model is already picked
- **[UNCOVERED]** - Windows: startup no longer stalls on repeated rename retries when `~/.claude.json` is read-only

#### v2.1.233

- **[UNCOVERED]** - Added GitLab merge request URL support to the `--worktree` flag and the `claude agents` view (where MRs display as `!N`)
- **[UNCOVERED]** - Added an opt-in `forward_user_identity` apps gateway setting on Anthropic upstreams that sends the signed-in user's identity as headers, so a proxy behind the gateway can attribute spend per user
- **[UNCOVERED]** - Added opt-in memory cgroup support for Bash tool commands on Linux (`CLAUDE_CODE_TOOL_MEMORY_LIMIT`) so a runaway build can't stall the session
- **[UNCOVERED]** - Added `CLAUDE_CODE_WEBFETCH_CACHE_TTL_MS` environment variable to configure the WebFetch session URL cache TTL (default unchanged: 15 minutes)
- **[UNCOVERED]** - Fixed cloud sessions occasionally being marked as lost when the environment shut down while Claude was waiting on a permission prompt
- **[UNCOVERED]** - Fixed MCP v2 connections endlessly reopening the subscriptions/listen stream against servers that terminate long-held streams on a fixed timeout (e.g. serverless hosts)
- **[UNCOVERED]** - Fixed Notification hooks not firing for permission prompts when running under Claude Desktop or VS Code
- **[UNCOVERED]** - Fixed idle sessions on Linux sometimes keeping one CPU core at 100% when sandboxing is enabled
- **[UNCOVERED]** - Fixed bundled skill aliases like `/checkup` and `/review` reporting "Unknown command" in `-p` mode or with plugins/MCP loaded when a user or project skill shadows the bundled skill
- **[UNCOVERED]** - Fixed skill/command argument substitution to prevent argument values from being re-expanded as template markers
- **[UNCOVERED]** - Fixed Windows paths spelled with the NT `\??\` device prefix bypassing UNC path validation, closing an NTLM credential-leak vector
- **[UNCOVERED]** - Improved `claude self-hosted-runner` session start time: the session branch is now created without rewriting the working tree, and two server round trips no longer block the agent's launch
- **[UNCOVERED]** - Improved apps gateway error forwarding: 400/413 errors from Vertex, Foundry, and Claude Platform on AWS upstreams now carry the upstream's own message; fixes a bug with auto-compact on apps gateway
- **[UNCOVERED]** - Improved `claude plugin validate` to check a bare `.claude/skills` directory, reporting SKILL.md files whose frontmatter fails to parse
- **[UNCOVERED]** - Improved screen reader mode: the `/effort` selector renders as a numbered list with a typed-number prompt, and hint and dialog text is no longer clipped
- **[UNCOVERED]** - Improved print mode diagnostics: a `[claude-code:unrecognized_model]` line is written to stderr when a request goes out for a model ID Claude Code doesn't recognize; map it with `modelOverrides` to silence
- **[UNCOVERED]** - Changed the GitHub app setup tip to no longer appear in repositories whose origin remote is on gitlab.com or bitbucket.org; the enterprise marketplace tip now covers non-GitHub internal git hosts
- **[UNCOVERED]** - Todo/task-tracking tools (TaskCreate/Get/Update/List, TodoWrite) are no longer available on Opus 4.8, Sonnet 5, Fable 5, Mythos 5, and newer models; set `CLAUDE_CODE_ENABLE_TODO_TOOLS=1` to bring them back
- **[UNCOVERED]** - Windows: fixed auto mode repeatedly stopping for manual approval on ordinary `cd <dir> && <command> > file` Bash commands (a 2.1.232 regression)
- **[UNCOVERED]** - Reverted the 2.1.232 Bash permission changes for Cygwin-style symlinks on Windows and for input redirections (`< file`); a narrower version will return in a later release

#### v2.1.232

- **[covered]** - Hardened the Linux filesystem sandbox against a protected-path bypass
  - Covered by: `cc-native/sandboxing/CC-sandboxing-analysis.md`
- **[UNCOVERED]** - Subagent forking is now on by default: a `subagent_type: "fork"` subagent inherits the full conversation and prompt cache, and non-teammate agent spawns in interactive sessions now run in the background by default
- **[UNCOVERED]** - Type `@` in the prompt to mention another Claude session by name; Claude then uses `SendMessage` to reach that session directly
- **[UNCOVERED]** - `SendMessage` now delivers to a bare name that exactly matches one live session, instead of asking to confirm with a ref first
- **[UNCOVERED]** - Interactive sessions on one machine now keep unique names: starting or renaming a session to a name another live session already uses gives it a `name-word-word` variant and tells you
- **[UNCOVERED]** - Added `/config` rows for "Dialog expiry" and "Messages from your other sessions" (cross-session inbound accept/hold/refuse)
- **[UNCOVERED]** - Added secret redaction for GitLab token families (`glrt-`, `gloas-`, `glptt-`, `glagent-`, `glimt-`, `glsoat-`, `glcbt-`, `glft-`, `glffct-`) and full redaction of routable `glpat-`/`gldt-` tokens; the `glab` CLI config store gets the same sandbox and credential-path protection as `gh`
- **[UNCOVERED]** - Added GitLab support to plugin marketplaces: bare `gitlab.com` repo URLs (including nested subgroups) now clone like `github.com` URLs, and clone auth-failure hints name your actual git host
- **[UNCOVERED]** - Settings: `additionalMarketplaces` and `allowedMarketplaces` are now accepted as friendlier aliases for `extraKnownMarketplaces` and `strictKnownMarketplaces`
- **[UNCOVERED]** - Enterprise policy: a url-typed `blockedMarketplaces` entry for a bare repo URL keeps blocking that URL when the CLI classifies it as a git clone
- **[UNCOVERED]** - Gateway: the `desktop:` overlay now accepts every released Desktop setting (was 11 hand-listed keys), validated at boot against Desktop's own schema; unknown or invalid keys fail boot
- **[UNCOVERED]** - Gateway: empty `managed.policies[].match.groups`/`admin.admin_groups` entries and malformed `email_domain` values (empty, or containing `@`, whitespace, or commas) now fail at boot instead of silently matching no one or granting admin access
- **[UNCOVERED]** - Fable 5 is offered as an advisor in `/advisor` again for organizations with Fable access, with usage-credits consent set up through `/model fable`
- **[UNCOVERED]** - Fixed a PowerShell permission bypass where variable-writing parameters could silently overwrite `$PSDefaultParameterValues` and redirect later commands' file access
- **[UNCOVERED]** - Fixed a Windows permission bypass where Git Bash followed Cygwin-style symlinks that path validation saw as regular files; writes through them now require permission approval
- **[UNCOVERED]** - Fixed nested git repositories inheriting trust from a parent directory; each repository now requires its own trust confirmation
- **[UNCOVERED]** - Fixed MCP connections hanging for the full 30-second connect timeout when a server fails to answer or sends a malformed reply to the protocol-version probe
- **[UNCOVERED]** - Fixed Remote Control sessions hosted by a bridge inside a cloud session inheriting that session's transcript or credentials
- **[UNCOVERED]** - Fixed Remote Control sessions started from Claude Desktop or an IDE appearing as a new claude.ai session each time the local session was resumed; they now reattach to the existing one
- **[UNCOVERED]** - Fixed Remote Control sessions appearing unreachable to newly attached clients while idle
- **[UNCOVERED]** - Fixed Remote Control bridge sessions not restoring conversation history when the session worker restarts
- **[UNCOVERED]** - Remote Control: resuming a conversation whose session was deleted from claude.ai or the app now starts a replacement instead of failing with a message about your login (regressed in v2.1.227)
- **[UNCOVERED]** - Fixed Cloud gateway `/login` exiting silently or leaving an unresponsive terminal after "Press Enter to continue" when managed settings failed to load; the reason is now shown
- **[UNCOVERED]** - Fixed voice mode on native builds getting stuck on "listening…" when the voice service rejected the connection; the rejection is now shown immediately
- **[UNCOVERED]** - Fixed mTLS client certificate rotation requiring a restart; Claude Code now reloads the rotated cert and key automatically on connection errors
- **[UNCOVERED]** - Fixed malformed AWS or Vertex region values being used to build request URLs; they now fall back to the default region
- **[UNCOVERED]** - Fixed stream idle timeout errors failing the request instead of recovering on Bedrock, Vertex, and gateway deployments
- **[UNCOVERED]** - Fixed content-sized overlays containing truncated text rendering one column too wide, and start-truncated text collapsing to an ellipsis
- **[UNCOVERED]** - Fixed a stray garbled character where a long shell-command or agent-description preview was cut off mid-emoji
- **[UNCOVERED]** - Fixed a startup race that could silently unregister a plugin marketplace due to concurrent writes to `known_marketplaces.json`
- **[UNCOVERED]** - Fixed `/update` and `/tui` refusing to restart while work that survives the relaunch was running
- **[UNCOVERED]** - Fixed usage-limit guidance suggesting unavailable slash commands in SDK and remote sessions
- **[UNCOVERED]** - Fixed the consent message for interactive `--advisor fable` launches, which told you to run `/model fable` in an interactive session that had just exited
- **[UNCOVERED]** - Improved fullscreen streaming: long sessions stay responsive because the whole conversation is no longer re-normalized on every update
- **[UNCOVERED]** - Improved the managed settings approval dialog: shows endpoint URLs, uses clearer wording for telemetry-only changes, skips routine OpenTelemetry options, and requires approval for server-managed sandbox binary overrides (`sandbox.bwrapPath`, `sandbox.socatPath`, `sandbox.ripgrep`)
- **[UNCOVERED]** - `/feedback` and `/bug` now open immediately when invoked while Claude is responding, instead of waiting for the turn to finish
- **[UNCOVERED]** - `/plugin install plugin@marketplace` now refreshes the marketplace first, so newly published plugins install without a manual marketplace update
- **[UNCOVERED]** - `/code-review` at high, xhigh, and max effort now runs in a background agent like the other levels
- **[UNCOVERED]** - Pasted and clipboard images are read without blocking the event loop
- **[UNCOVERED]** - Remote Control now keeps reconnecting for about 30 minutes after a network blip and no longer drops after a few blips spread across an hour
- **[UNCOVERED]** - Remote Control: resuming a conversation no longer silently takes Remote Control away from another Claude Code on the same machine that still has it; run `/remote-control` there to move it
- **[UNCOVERED]** - Updated agent panel: completed subagents hide immediately with a `/tasks` footer hint, and the "↓ N more" overflow indicator moved left for visibility
- **[UNCOVERED]** - Remote Control: the terminal now says whether a session was taken over by another device, ended from another app, or deleted, and stops suggesting a reconnect that would undo it
- **[UNCOVERED]** - Bash input redirections (`< file`) are now permission-checked like their argument spellings on all platforms
- **[UNCOVERED]** - Shortened the message shown when resuming a completed background agent
- **[UNCOVERED]** - Cowork sessions no longer inline external @-imports from user-scope memory files
- **[UNCOVERED]** - Hardened the auto-generated cross-session messaging socket directory on shared `/tmp`: a pre-planted symlink or another user's directory is now refused instead of used
- **[UNCOVERED]** - Changed `sandbox.ripgrep` to be honored only from user, managed, and `--settings` settings; project settings can no longer override the sandbox's ripgrep binary
- **[UNCOVERED]** - Removed the startup tip suggesting you create custom subagents, and the matching nudge in the `/powerup` tour

#### v2.1.231

- **[UNCOVERED]** - Fixed MCP OAuth sign-in failing with a redirect URI mismatch for servers that use a pre-registered OAuth client, such as Slack

#### v2.1.229

- **[covered]** - Documented `claude remote-control --continue` for resuming the most recent Remote Control session
  - Covered by: `cc-native/configuration/CC-env-vars-reference.md`
- **[UNCOVERED]** - Added server-supplied Claude Code hook support for self-hosted runner sessions, matching managed-environment behavior
- **[UNCOVERED]** - Added SSE keepalive pings to gateway streaming responses during long thinking pauses, preventing idle-timeout disconnects on Vertex and Bedrock upstreams
- **[UNCOVERED]** - Added plugin marketplace `command` sources: a local command (e.g. an IDE) prints the plugin directory, which is re-resolved each session and applied without a restart; `mode: "link"` uses it in place
- **[UNCOVERED]** - `ListAgents` now marks disconnected Remote Control sessions as `offline` and labels your cloud sessions as `cloud`
- **[UNCOVERED]** - Fixed long responses partly disappearing while streaming and being printed twice in the terminal
- **[UNCOVERED]** - Fixed a crash to the error screen (including on `--resume` of the affected session) when a tool call had a non-string `glob`, `file_path`, or `command` value
- **[UNCOVERED]** - Fixed a RangeError crash when a progress bar or markdown table rendered in a very narrow terminal window (could also crash `claude --continue`/`--resume` at startup)
- **[UNCOVERED]** - Fixed a crash on Windows when a tool call or message referenced a file by an extended-length (`\\?\`) or UNC path
- **[UNCOVERED]** - Fixed auto mode failing on every tool call for users who disable the attribution header via `CLAUDE_CODE_ATTRIBUTION_HEADER` (direct Anthropic API connections)
- **[UNCOVERED]** - Fixed `/model` rejecting Sonnet/Opus 1M for claude.ai subscribers using a custom `ANTHROPIC_BASE_URL` gateway
- **[UNCOVERED]** - Fixed MCP OAuth with strict authorization servers by using `127.0.0.1` instead of `localhost` in the redirect URI
- **[UNCOVERED]** - Fixed Remote Control clients showing a stuck working spinner after a slash command typed in the laptop terminal
- **[UNCOVERED]** - Fixed the Claude Code Review workflow generated by `/install-github-app` completing without posting its review on the pull request
- **[UNCOVERED]** - Fixed multi-second UI stalls after editing a file with thousands of IDE diagnostics while the IDE extension is connected
- **[UNCOVERED]** - Fixed one-shot `claude plugin` commands leaving a stray liveness file that could prevent cleanup of outdated plugin versions
- **[UNCOVERED]** - Fixed dynamic workflows inside CPU-limited containers using the host machine's core count instead of the container's CPU limit
- **[UNCOVERED]** - Fixed a file-watcher handle leak after atomic file replacements, and an uncaught error on Windows when the scheduled-tasks watcher failed on a network or virtual filesystem
- **[UNCOVERED]** - Fixed SDK and `--input-format stream-json` sessions getting a 400 API error when a whitespace-only message was submitted
- **[UNCOVERED]** - Fixed conversations whose messages alone exceed the API's 32 MB request limit retrying compaction when no images or documents can be stripped; they now fail once with a clear message
- **[UNCOVERED]** - Fixed OpenTelemetry export from Claude Desktop sessions being rejected by the Desktop-managed gateway when that gateway is also the telemetry endpoint
- **[UNCOVERED]** - Fixed self-hosted runner and other remote sessions exiting at startup when `managed-mcp.json` is deployed and the server delivers MCP servers; those servers are now skipped with a warning
- **[UNCOVERED]** - Fixed self-hosted runner repository preparation hanging on a Git Credential Manager prompt; git now fails fast when credentials are missing
- **[UNCOVERED]** - Improved workflow fan-outs to stagger same-prefix sibling agents so subsequent agents read the cached prompt prefix instead of re-paying it (`CLAUDE_CODE_WORKFLOW_PREFIX_STAGGER_MS=0` disables)
- **[UNCOVERED]** - Improved "prompt is too long" errors to explain why automatic compaction could not recover instead of only suggesting `/compact`
- **[UNCOVERED]** - Improved sandbox: IPv6 literals in network domain lists are now bracketed (`[::1]:443`), and ambiguous spellings are enforced fail-closed and flagged by `/doctor`
- **[UNCOVERED]** - Updated `/login` to repeat the `CLAUDE_CODE_OAUTH_TOKEN` override warning after a successful login
- **[UNCOVERED]** - Changed `/commit-push-pr` so git/gh commands with dangerous flags (`--force`, `--amend`, `--no-verify`, etc.) are no longer auto-approved
- **[UNCOVERED]** - Changed self-hosted runner Windows startup to require an explicit `--base-dir`; there is no default checkout directory on Windows
- **[UNCOVERED]** - [VSCode] "Report a problem" and `/bug` now open the built-in feedback dialog instead of a retired survey link
- **[UNCOVERED]** - [VSCode] Made the `/btw` side-question panel resizable by dragging its boundary, in both side-docked and stacked layouts
- **[UNCOVERED]** - [VSCode] Added session groups in the sidebar — right-click to create, rename, or delete; Cmd/Ctrl- or Shift-click to move several sessions at once

#### v2.1.228

- **[UNCOVERED]** - Fixed interactive sessions that could stop redrawing entirely, while the process kept running, after a rare internal layout error
- **[UNCOVERED]** - Fixed `git` / Git Bash not being found on Windows when Claude Code is launched from a parent folder of the git installation
- **[UNCOVERED]** - Fixed `/tui` reverting the session to an earlier model when `/model` had been changed since the last response
- **[UNCOVERED]** - Fixed cross-session messaging sometimes starting without an inbox in the first session after install or upgrade
- **[UNCOVERED]** - Fixed Remote Control `/resume` while connected leaking the resumed conversation's title or history into the connected session
- **[UNCOVERED]** - Fixed `claude self-hosted-runner` sessions failing on every fresh runner when the `checkout` hook fails for a repository the session doesn't push to; that repository is now skipped with a warning
- **[UNCOVERED]** - Fixed self-hosted runners ending sessions in the gap between a background task finishing and the follow-up turn starting
- **[UNCOVERED]** - Fixed session cleanup deleting contents inside a project's memory folder
- **[UNCOVERED]** - Fixed background plugin-cache cleanup deleting a plugin's cache when its only version is a symlinked development checkout
- **[UNCOVERED]** - Fixed a settings-merge issue where a marketplace entry redefined in a higher-precedence settings tier could inherit another tier's custom headers; marketplace entries now merge as whole entries
- **[UNCOVERED]** - Fixed the deferred-tools reminder occasionally being sent to the model twice after a skill invocation
- **[UNCOVERED]** - Hardened skills synced from claude.ai: they no longer shadow local commands or MCP prompts, their descriptions are sanitized and labeled, and on your machine their bodies don't run `!` commands or expand `@` files
- **[UNCOVERED]** - Improved cross-session messages: the sender and body now display inline instead of a collapsed line, and messages to Remote Control sessions on other machines show your Remote Control session name as the sender
- **[UNCOVERED]** - Improved Vertex AI credential handling: expired or missing Google Cloud credentials now fail within seconds instead of retrying for minutes
- **[UNCOVERED]** - Improved compaction progress: the retry countdown and stall hint now appear during compaction instead of only a progress bar
- **[UNCOVERED]** - Updated terminal title busy-spinner glyphs to reduce tab-bar jitter on some terminals
- **[UNCOVERED]** - Changed the Write tool so newer models can overwrite an existing file they haven't read this session, matching the Edit tool's rules; older models still require the read first
- **[UNCOVERED]** - Removed the outdated note about auto mode sessions costing slightly more from the first-use notice for Pro, Max, and Team plans

#### v2.1.227

- **[UNCOVERED]** - Fixed feature flags being evaluated without the user's subscription tier when a session started with an expired login token, which could wrongly prompt Max plan users to enable usage credits for Fable
- **[UNCOVERED]** - Fixed every Bash command failing under `claude-code-action` with `allowed_non_write_users` on GitHub-hosted runners
- **[UNCOVERED]** - Fixed `/tui` bringing back a conversation that had been rewound to before its first message
- **[UNCOVERED]** - Improved slash-command menu: blue now marks only the selected row, matched characters are bolded instead of recolored, and emoji or accented names keep their glyphs
- **[UNCOVERED]** - Improved performance: fewer event-loop stalls on file-not-found suggestions and at-mention size checks

#### v2.1.226

- **[UNCOVERED]** - Bug fixes and reliability improvements

#### v2.1.225

- **[UNCOVERED]** - Added gateway spend-limit support to Claude Code's usage warning; the limit-reached message now names the cap, its reset time, and the operator's message (requires the gateway on 2.1.225)
- **[UNCOVERED]** - Added a workspace trust prompt to `claude agents` for untrusted directories, matching the behavior of `claude`
- **[UNCOVERED]** - Fixed a transient 401 replacing a long-lived `CLAUDE_CODE_OAUTH_TOKEN` with a stored login's short-lived token, breaking headless sessions until restart
- **[UNCOVERED]** - Fixed MCP OAuth servers on macOS intermittently failing with a burst of 401 errors, as if never authenticated, after a keychain read timed out
- **[UNCOVERED]** - Fixed auto mode counting a safety-filter refusal of its own permission check toward the consecutive-block limit; the action is still denied, but the model is now told to move on rather than retry
- **[UNCOVERED]** - Fixed cross-session messages staying parked without a notice or expiry in headless sessions and during startup
- **[UNCOVERED]** - Fixed conversation history breaking on Remote Control session resume after very large conversations were compacted
- **[UNCOVERED]** - Fixed hovering over a session in another project in the agents list changing the directory the next agent starts in
- **[UNCOVERED]** - Fixed `claude self-hosted-runner` registering and then failing every session when `--base-dir` cannot be created or written; it now exits at startup with a clear error
- **[UNCOVERED]** - Fixed Claude Code on the web sessions being misreported as stuck, re-sending a growing event backlog on every reconnect
- **[UNCOVERED]** - Improved Remote Control: photos attached from the Claude app are now shown to Claude directly instead of being read from disk with a separate tool call
- **[UNCOVERED]** - [VSCode] Fixed Focus view folding away the latest to-do list, a pending question's context, and settled answers; thinking-only folds show "Thought for Ns" and re-collapse when their turn completes
- **[UNCOVERED]** - SendMessage can now start a conversation with your Remote Control sessions on other machines by name (`ListAgents` shows them as `name [ref]`), instead of only replying after they message you first
- **[UNCOVERED]** - SendMessage: a Remote Control recipient you already confirmed is never swapped for a same-named session on this machine when its own list couldn't be checked

#### v2.1.224

- **[UNCOVERED]** - Added self-hosted environments: `claude self-hosted-runner` turns your own machines or containers into a place Claude Code web, mobile, and desktop sessions can run, on Team and Enterprise plans
- **[UNCOVERED]** - Added `archive` plugin source: install plugins from a zip over HTTPS without git or npm, with optional SHA-256 pinning
- **[UNCOVERED]** - Added a cancel-and-confirm step when removing an unavailable paste changes a command's text
- **[UNCOVERED]** - Added `ANTHROPIC_BEDROCK_REGION_PREFIX` env var for Bedrock to prefer a specific cross-region inference profile over the `AWS_REGION`-derived one
- **[UNCOVERED]** - Added `crossSessionInbound` and `dialogExpiry` settings: cross-session messages sent to a session running with bypassed permissions are held for your approval, and messages to other sessions auto-deliver
- **[UNCOVERED]** - Added sandbox credential-masking options: `extract` and `onExtractNoMatch` for structured env values, `decode: "jwt"` with `maskClaims` for JWT-aware masking, and `awsPairs`/`sigv4` for AWS SigV4 re-signing; these need `network.tlsTerminate` and are honored only from user, managed, or `--settings` settings
- **[UNCOVERED]** - Added cross-session `SendMessage`: Claude Code sessions can now message each other, on any of your machines, with `ListAgents` to discover them (macOS and Linux)
- **[UNCOVERED]** - Fixed long (>200 char) project paths resolving to another project's session directory under a shared sanitized prefix; session list, rename, fork, delete and `/resume` no longer cross projects
- **[UNCOVERED]** - Fixed `SendMessage` reporting "Message sent" when the write to a teammate's inbox had actually failed; failed deliveries are now reported as errors
- **[UNCOVERED]** - Fixed sandbox filesystem deny entries written with a trailing slash (e.g. `denyRead: "~/.aws/"`) being silently bypassable on Linux and macOS
- **[UNCOVERED]** - Fixed sandbox violation details never appearing in Bash tool results; Claude now sees which file or network access was denied and why
- **[UNCOVERED]** - Fixed MCP tools that connect mid-turn being deferred for tool search without their names announced to the model
- **[UNCOVERED]** - Fixed plugin install records being silently corrupted when the same plugin is installed in multiple projects
- **[UNCOVERED]** - Fixed recalled or restored paste content occasionally attaching wrong data or silently losing text when the paste had aged out or placeholder numbers collided
- **[UNCOVERED]** - Fixed copy-on-select on Wayland sometimes not reaching the clipboard; the two selection writes no longer race
- **[UNCOVERED]** - Fixed the feedback survey's transcript share silently failing on long sessions; a failed share now shows an error instead of a success message
- **[UNCOVERED]** - Fixed Remote Control auto-start intermittently failing with "Remote credentials fetch failed" on a cold start with a stale login token
- **[UNCOVERED]** - Fixed Remote Control and SDK clients showing a blank "(no content)" message after `/clear` and other output-less commands
- **[UNCOVERED]** - Fixed a Remote Control session recreated after its server session expired uploading prior local conversation history into the new session
- **[UNCOVERED]** - Improved fullscreen mode to keep the full pre-compaction history in scrollback across repeated compactions, instead of only the most recent interval
- **[UNCOVERED]** - Improved Remote Control: attached web and mobile clients now see compaction progress and the post-compaction boundary instead of a silent pause; `/clear` resets now propagate to attached clients
- **[UNCOVERED]** - Improved Remote Control: connection failures now show a persistent failure indicator with details and a reconnect shortcut, instead of only an 8-second toast
- **[UNCOVERED]** - Removed the 200-subagent-per-session spawn cap; long-running sessions no longer refuse new agents (concurrency and depth limits still apply)
- **[UNCOVERED]** - Changed managed settings: the approval prompt no longer re-appears after re-login or org switching when the organization's settings are unchanged
- **[UNCOVERED]** - Changed the feedback-survey transcript share: with your consent it now also uploads the last request's model settings — the system prompt (which includes your `CLAUDE.md` instructions), tool definitions, and model parameters. Secrets are redacted as before, and these fields are dropped first if the share is too large
- **[UNCOVERED]** - Changed the Bash tool description to always note that command output is displayed to the model, not reliably to the user
- **[UNCOVERED]** - Changed recalled paste placeholder numbers to renumber when accepted into the input
- **[UNCOVERED]** - Changed Remote Control to archive the stale server session instead of leaving a dead one listed when a fresh session is minted after compaction or `/resume`
- **[UNCOVERED]** - [VSCode] Fixed the extension showing Remote Control as connected after the connection failed
- **[UNCOVERED]** - Fixed a session resume silently reconnecting Remote Control after the user turned it off (`--resume`, SDK hosts, and the VS Code extension)
- **[UNCOVERED]** - [VSCode] Fixed sessions not honoring `remoteControlAtStartup` when explicitly enabled

#### v2.1.223

- **[UNCOVERED]** - Added owner wildcard entries (`"owner/*"`) to the `strictKnownMarketplaces` and `blockedMarketplaces` managed settings for allowing or blocking all marketplace repos under a GitHub org
- **[UNCOVERED]** - Added a warning when workflow agents, forked skills, slash commands, or resumed background agents' requested subagent model is restricted and the parent model runs instead
- **[UNCOVERED]** - Added a `/teleport` hint in cloud sessions showing how to continue locally with `claude --teleport <session id>`
- **[UNCOVERED]** - Fixed a Bash permission bypass where a crafted command could hide parts of itself from permission checks
- **[UNCOVERED]** - Fixed permission prompts so commands padded with tabs or invisible Unicode can no longer hide part of the command from the approval dialog
- **[UNCOVERED]** - Fixed workflow scripts being able to use dynamic `import()` to run code outside the workflow sandbox
- **[UNCOVERED]** - Fixed a permission gap where an agent definition's `bypassPermissions` mode ignored the org bypass-permissions disable policy
- **[UNCOVERED]** - Fixed resuming a session after a mid-session `/cd` coming back empty
- **[UNCOVERED]** - Fixed gateway model discovery hiding Claude models registered under provider-prefixed IDs such as `vertex_ai/claude-*` or `bedrock/anthropic.claude-*`
- **[UNCOVERED]** - Fixed `modelOverrides` keys that aren't Anthropic model IDs being treated as the session's canonical model ID; unknown keys are now ignored as documented
- **[UNCOVERED]** - Fixed managed settings: server-delivered settings no longer disable the env block of a machine-local `managed-settings.json` or MDM profile; admin env now merges per key
- **[UNCOVERED]** - Fixed sandboxed commands failing to start on Linux when `sandbox.filesystem.denyWrite` covers the working directory
- **[UNCOVERED]** - Fixed forked background agents getting stuck "already resuming" for the rest of the session when rebuilding the fork's parent prompt failed during resume
- **[UNCOVERED]** - Fixed a resumed session failing every turn, or leaving the interactive app on an unresponsive error screen, when its history held a malformed diagnostics attachment
- **[UNCOVERED]** - Fixed a rare hang when parsing unusual `git push` output
- **[UNCOVERED]** - Changed `CLAUDE_CODE_DISABLE_1M_CONTEXT` to hold every Claude model with a native 1M window to 200K via auto-compaction, not just a fixed list; a startup warning now appears when auto-compaction isn't holding the session to 200K
- **[UNCOVERED]** - Changed auto-compact to keep sessions on unrecognized model IDs within the assumed context window instead of letting them grow past it; set `CLAUDE_CODE_DISABLE_UNKNOWN_MODEL_WINDOW_ENFORCEMENT=1` to restore the previous behavior
- **[UNCOVERED]** - Changed `/review` to be an alias of `/code-review`, which reviews the current diff or a PR (`/code-review <level> <pr#>`); use `/code-review ultra` for a deep cloud review
- **[UNCOVERED]** - Changed `/code-review` with no effort level to reuse the level you typed last; type a level like `/code-review high` to change it

#### v2.1.222

- **[covered]** - Removed ultraplan feature
  - Covered by: `cc-native/agents-skills/CC-plans-as-skill-rule-templates.md`
- **[UNCOVERED]** - Fixed worktree-isolated sessions and their subagents being able to run destructive git commands against the main checkout; isolation now applies to file edits and Bash in every session type
- **[UNCOVERED]** - Fixed PreToolUse auto-allow hooks bypassing tool restrictions in background agent tasks (summaries, compaction, renames)
- **[UNCOVERED]** - Fixed `/usage-credits` on Team and Enterprise showing "you've already sent a usage credit request" for members whose earlier request was dismissed, blocking them from sending a new one
- **[UNCOVERED]** - Fixed the startup connectivity check hanging and then failing behind an HTTPS proxy; it now uses the same proxy-aware transport as API requests and times out with a clear message
- **[UNCOVERED]** - Fixed "Connection closed mid-response" errors being reported on responses that had actually completed
- **[UNCOVERED]** - Fixed `/usage` overattributing usage to MCP servers: a server's share now reflects only the requests that actually consumed its tool results, instead of every turn after any call to it
- **[UNCOVERED]** - Fixed sessions not linking to pull requests created after the branch was pushed, including through the GitHub REST API
- **[UNCOVERED]** - Fixed org-restricted `model: opus`-style subagent and teammate family aliases dropping to the parent model instead of stepping down to the newest org-allowed model in the family
- **[UNCOVERED]** - Fixed stream idle timeout firing on custom `ANTHROPIC_BASE_URL` gateways despite server keep-alive pings arriving on the wire
- **[UNCOVERED]** - Fixed claude.ai connectors being falsely marked as needing authorization when the session token is invalid — they now show a `/login` hint instead
- **[UNCOVERED]** - Fixed tool errors not being displayed for tools no longer available locally, for example after an MCP server is removed
- **[UNCOVERED]** - Fixed `SendMessage` rejecting a long summary — it now truncates instead, so sends no longer fail on a character limit
- **[UNCOVERED]** - Fixed the spinner's effort label in a subagent's transcript view showing the session's effort level instead of the subagent's own `effort:` setting
- **[UNCOVERED]** - Fixed rare crashes when a file watcher hit a filesystem error or during file-watcher teardown
- **[UNCOVERED]** - Fixed screen readers re-reading the whole input line on every backspace in `--ax-screen-reader` mode — end-of-line deletions now echo just the deleted characters
- **[UNCOVERED]** - Fixed host model-selection keys not taking precedence over a stale on-disk `managed-settings.json` when `CLAUDE_CODE_PROVIDER_MANAGED_BY_HOST` is set
- **[UNCOVERED]** - Improved auto mode safety: messages sent to other agent sessions via `SendMessage` are now evaluated by the permission classifier before dispatch
- **[UNCOVERED]** - Improved the refusal when Claude tries to invoke a skill with `disable-model-invocation`: Claude is now told to ask you to run the skill instead of replicating its workflow
- **[UNCOVERED]** - Improved the `/diff` view, the Remote Control workspace diff, and file-edit diffs in Claude Code on the web sessions to use raw git blob content, ignoring workspace-configured diff drivers and textconv
- **[UNCOVERED]** - Changed Remote Control auto-start so repo-local settings (`.claude/settings.json` or `.claude/settings.local.json`) can no longer turn it on (they can still turn it off); enable it at user scope via `/config`

#### v2.1.221

- **[covered]** - Improved tool search on Google Vertex AI: re-enabled for Claude 4.5-generation and newer models
  - Covered by: `cc-native/configuration/CC-model-provider-configuration.md`
- **[UNCOVERED]** - [VSCode] Added Focus view: a chat-menu toggle that hides tool activity behind an expandable per-turn summary with a live running-tool indicator, toggled with `Ctrl+Alt+F` or the "Claude Code: Toggle Focus view" command
- **[UNCOVERED]** - Added `mode: "mask"` for sandbox credential files on Linux and WSL — sandboxed commands read a sentinel copy (the whole file, or just the spans captured by an `extract` regex) while the sandbox proxy substitutes the real value on egress; on macOS file masking falls back to `deny`
- **[UNCOVERED]** - Added warnings to `claude plugin validate` when a marketplace or plugin name would be rejected by Claude Desktop's managed marketplace sync
- **[UNCOVERED]** - Added a `prompt-audit` subcommand to the `claude-api` skill for auditing prompts and tool descriptions for patterns written for older models
- **[UNCOVERED]** - Fixed a Bash tool permission-check bypass where zsh could execute hidden commands in `[[ ]]` regex conditionals; affected commands now prompt for permission
- **[UNCOVERED]** - Fixed PowerShell permission checks mishandling paths containing quote characters on Windows; such paths now prompt for approval
- **[UNCOVERED]** - Fixed the thinking toggle having no effect for the rest of a session that started with thinking off; disabling an MCP server mid-connect no longer silently reverts
- **[UNCOVERED]** - Fixed MCP servers from `--mcp-config` not being connected before the first turn in print mode (`-p`), which made the model emit tool calls as literal text
- **[UNCOVERED]** - Fixed @-mentioned files being silently dropped when pressing Esc to retract a prompt and resubmitting it
- **[UNCOVERED]** - Fixed a crash when preparing API requests for SDK MCP tools named after built-in object properties such as `constructor`
- **[UNCOVERED]** - Fixed WebSearch failing with a 400 error at effort `xhigh`/`max` when thinking is disabled
- **[UNCOVERED]** - Fixed sandboxed large uploads failing with TLS errors through the sandbox proxy
- **[UNCOVERED]** - Fixed Team and Enterprise spend-limit message incorrectly blaming the org's monthly limit instead of your individual spend limit
- **[UNCOVERED]** - Fixed Bedrock authentication with AWS SSO named profiles failing in desktop-managed sessions on Windows machines that set a stray `HOME` environment variable
- **[UNCOVERED]** - Fixed `CLAUDE_CODE_RESUME_INTERRUPTED_TURN=0` not disabling interrupted-turn auto-resume; falsy values are now honored
- **[UNCOVERED]** - Fixed a rare wake-from-sleep race where two Claude Code processes could both refresh the same MCP connector or WIF OAuth token at once, forcing re-authentication
- **[UNCOVERED]** - Fixed renaming a session from Claude Code Desktop or claude.ai not updating the CLI's session name; session names from every rename surface are now sanitized
- **[UNCOVERED]** - Fixed plugin- and org-delivered skills named after terminal-only built-ins (e.g. `/help`, `/feedback`) being un-invocable in non-interactive sessions
- **[UNCOVERED]** - Fixed the "Plugins changed" notification lingering after plugins were reloaded instead of clearing
- **[UNCOVERED]** - Fixed Vim mode: the yank register now survives dialogs, history search, and the transcript view instead of being silently emptied
- **[UNCOVERED]** - Fixed Vim mode: undoing back to an empty prompt now arms the "press ← again" confirm before returning to the agent view
- **[UNCOVERED]** - Improved auto mode: permission checks for parallel tool calls are now cache-efficient, and switching modes while a check is pending reliably prompts instead of applying the stale result
- **[UNCOVERED]** - Reduced prompt-cache costs for auto-mode permission checks by reusing the cached conversation prefix across decisions
- **[UNCOVERED]** - Improved Stats panel to count cache tokens in its token totals, with a breakdown by input, output, cache read, and cache write
- **[UNCOVERED]** - Improved `/ultrareview` error messages when a repo shares no history with its base: a checkout with no branches is now refused up front with advice to create one, and refusal hints no longer suggest `git fetch --unshallow` on clones that are already complete
- **[UNCOVERED]** - Improved Windows startup: process creation times are now read via a native kernel32 call instead of spawning PowerShell, so endpoint security tools that gate `powershell.exe` no longer prompt
- **[UNCOVERED]** - Changed background sessions to commit and push to preserve work, open a draft PR only when the task calls for one, follow your CLAUDE.md git instructions, and always end by reporting where the work lives
- **[UNCOVERED]** - Changed `/plugin install` to refresh a stale marketplace catalog and retry before reporting a plugin not found
- **[UNCOVERED]** - Changed plugins installed from `/plugin` to activate immediately when safe, instead of always requiring `/reload-plugins`
- **[UNCOVERED]** - Changed plugins to accept `"."` as a `skills` path, and the root-level `SKILL.md` validation error now suggests using the plugin root
- **[UNCOVERED]** - Changed `/status` to show the session kind: `interactive`, or a background job that is `attached` or `unattended`
- **[UNCOVERED]** - Changed emoji autocomplete to accept common alternate shortcodes like `:thumbsup:`, `:thumbsdown:`, and `:love:`
- **[UNCOVERED]** - Changed sessions forked with `/fork` to create a new worktree of their own instead of working in the original session's checkout
- **[UNCOVERED]** - Changed Claude in Chrome to close the browser tabs it opens once it no longer needs them
- **[UNCOVERED]** - Changed fast mode to report on the stream when usage credits run out mid-session, instead of failing silently
- **[UNCOVERED]** - Changed Monitor: a watch that exits without producing any output now says so instead of reporting "stream ended"
- **[UNCOVERED]** - Changed the Gateway `model` field validation: non-string values are rejected with a 400 instead of being forwarded
- **[UNCOVERED]** - Removed the repeated "Permission mode changed while the auto-mode classifier call was queued" notice from approval prompts

#### v2.1.220

- **[UNCOVERED]** - Bug fixes and reliability improvements

#### v2.1.219

- **[covered]** - Added Claude Opus 5 (`claude-opus-5`), now the default Opus model — 1M context, fast mode at $10/$50 per Mtok
  - Covered by: `cc-native/context-memory/CC-extended-context-analysis.md`
- **[UNCOVERED]** - Added `sandbox.network.strictAllowlist` setting to deny non-allowlisted hosts for sandboxed commands without prompting
- **[UNCOVERED]** - Added `DirectoryAdded` hook that fires after `/add-dir` or the SDK `register_repo_root` control request registers a new working directory mid-session
- **[UNCOVERED]** - Added `mcp_server_errors` to the headless stream-json init event, listing `--mcp-config` entries skipped by config validation; terminal runs print a startup warning
- **[UNCOVERED]** - Added the `workflowSizeGuideline` settings key so the advisory Dynamic workflow size guideline can be set from any settings file; the `/config` row is hidden while one does
- **[UNCOVERED]** - Added nested subagent forwarding in stream-json: subagents spawned at depth-2+ now appear when `--forward-subagent-text` is set, keyed by their spawning Agent `tool_use` id
- **[UNCOVERED]** - Fixed `claude -p` text output dropping the answer already produced when a turn dies on a mid-stream API error
- **[UNCOVERED]** - Added HTTP status and error text to `claude mcp list` and `/mcp` when a server fails to connect, and a warning for MCP config values with hidden leading or trailing whitespace
- **[UNCOVERED]** - Fixed the Fable model row showing "Requires usage credits" for plans that include it, when a stale cache had baked the label in
- **[UNCOVERED]** - Fixed the `/model` picker showing the merged Opus row as plain "Opus" instead of "Opus (1M context)"
- **[UNCOVERED]** - Fixed copy-on-select inside GNU screen printing base64 into the terminal instead of copying the selection
- **[UNCOVERED]** - Fixed Remote Control clients keeping a stale fast-mode status after a model switch, reconnect, or failed org check
- **[UNCOVERED]** - Fixed `CLAUDE_CODE_GIT_BASH_PATH` on Windows exiting or being used as bash when the path isn't a bash/sh binary; it's now ignored with a warning
- **[UNCOVERED]** - Fixed Vim mode: pressing ← on an empty prompt now returns to the agent view from NORMAL mode, not just INSERT
- **[UNCOVERED]** - Fixed screen-reader mode rewriting the entire input line on every keystroke instead of echoing only the typed character
- **[UNCOVERED]** - Improved the "Remote Control is only available via api.anthropic.com" error to name the specific setting that caused it
- **[UNCOVERED]** - Improved `claude --teleport` to show which repo your current checkout points at when it doesn't match the session's repo
- **[UNCOVERED]** - Changed dynamic workflows to default to a medium size guideline (aim for fewer than 15 agents); pick another size or unrestricted with Dynamic workflow size in `/config`
- **[UNCOVERED]** - Changed managed MCP allowlist/denylist `${VAR}` entries to resolve from the startup environment and managed-settings env instead of settings-file env
- **[UNCOVERED]** - Changed the `/model` picker to highlight only the newest model's name, so the highlight marks the new release rather than an arbitrary subset of the list
- **[UNCOVERED]** - Added the current default workflow size to the running-workflow status line, with a pointer to `/config` for changing it
- **[UNCOVERED]** - Removed Opus 4.7 from fast mode; `/fast` now applies to Opus 5 and Opus 4.8
- **[UNCOVERED]** - Updated the claude-api skill to default to Claude Opus 5, with a migration path from Opus 4.8
- **[UNCOVERED]** - Subagents can now spawn nested subagents up to depth 3 by default (was 1); set CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH=1 to disable nesting

#### v2.1.218

- **[UNCOVERED]** - Changed `/code-review` to run as a background subagent, so review work no longer fills your conversation and keeps stacked slash commands as its review target
- **[UNCOVERED]** - Added screen-reader announcements of deleted text for word and line deletions (`Option+Delete`, `Ctrl+W`, `Cmd+Backspace`, `Ctrl+U`, `Ctrl+K`) in `--ax-screen-reader` mode
- **[UNCOVERED]** - Fixed Windows paths with `\u`-prefixed segments (like `C:\Users\unicorn`) being corrupted into CJK characters in tool inputs, which made those files inaccessible
- **[UNCOVERED]** - Fixed the left arrow key discarding the conversation with no undo: presses right after editing now ask to confirm, and Esc in the agent view returns to the conversation it backgrounded
- **[UNCOVERED]** - Fixed multi-line paste collapsing into one line with `j` in place of newlines in terminals that encode pasted newlines as Ctrl+J
- **[UNCOVERED]** - Fixed `/context` reporting stale pre-compact token usage after compacting from the message picker
- **[UNCOVERED]** - Fixed `/ultrareview` failing on descriptive arguments like "review my auth changes" — they now run a review of your current branch with the text applied as a note to the findings
- **[UNCOVERED]** - Fixed `/code-review ultra` silently running a local review in non-interactive sessions — it now launches the cloud review
- **[UNCOVERED]** - Fixed gateway spend metering to price Bedrock application-inference-profile ARNs and other config-mapped upstream model IDs at the configured model's rates
- **[UNCOVERED]** - Fixed mojibake when a long IDE selection was truncated mid-emoji, and a case where a tool executor error could be silently dropped
- **[UNCOVERED]** - Fixed an engine teardown race that could start and abandon a phantom turn, and made input pushed after close consistently rejected
- **[UNCOVERED]** - Fixed spurious "[Request interrupted by user]" messages after interrupted tool calls, and an unpaired `tool_use` block left in the transcript when a tool aborted mid-response
- **[UNCOVERED]** - Fixed VoiceOver reading "new line" instead of echoing the typed space at the end of the input in `--ax-screen-reader` mode
- **[UNCOVERED]** - Fixed plugin and settings panels not moving the terminal cursor to the focused row, so screen readers and magnifiers can follow arrow-key navigation
- **[UNCOVERED]** - Fixed crashes (maximum call stack exceeded) when a deeply nested watched directory tree was deleted or moved, and when rendering deeply nested UI trees
- **[UNCOVERED]** - Fixed pull request events occasionally being lost when a session exited immediately after creating or linking a PR
- **[UNCOVERED]** - Fixed the Bedrock setup wizard failing profile verification for assume-role profiles in partitioned AWS regions and on proxy-only networks
- **[UNCOVERED]** - Fixed rare negative or incorrect turn duration measurements after a system clock adjustment by timing turns with a monotonic clock
- **[UNCOVERED]** - Fixed the "N MCP servers need authentication" startup notice over-counting claude.ai connectors that aren't connected in claude.ai
- **[UNCOVERED]** - Fixed prompt history entries being dropped or duplicated when history writes raced or failed
- **[UNCOVERED]** - Fixed a retry loop that re-sent identical doomed requests after a context-overflow error with a large thinking budget; `Ctrl+B` backgrounding now applies the same background-shell caps as other paths
- **[UNCOVERED]** - Fixed agent frontmatter hooks running from untrusted folders: hooks now require the agent file's own folder to have accepted workspace trust
- **[UNCOVERED]** - Fixed fork-session lineage being lost after compaction in headless and SDK sessions
- **[UNCOVERED]** - Fixed a resumed session failing every turn, or crashing on resume, when its history held a malformed delta attachment
- **[UNCOVERED]** - Improved `/ultrareview` error feedback so Claude can correct an invalid argument instead of retrying it unchanged
- **[UNCOVERED]** - Improved auto mode: the dangerous-rm, background-`&`, and suspicious-Windows-path checks no longer open permission dialogs; the auto-mode classifier adjudicates them instead
- **[UNCOVERED]** - Improved sandbox command restrictions for IDE interactions
- **[UNCOVERED]** - Improved trust dialogs to name the repository root the grant covers
- **[UNCOVERED]** - Changed `/deep-research` to start only when invoked manually; Claude no longer launches it on its own
- **[UNCOVERED]** - Changed plan mode with auto to no longer prompt for Bash commands the static analyzer can't prove read-only; the auto-mode classifier judges them instead
- **[UNCOVERED]** - Added an announcement when fast mode changes as a result of switching models via `/config model=<x>` or Remote Control
- **[UNCOVERED]** - Changed server-managed settings so benign feature and cost toggles no longer trigger the settings-approval prompt
- **[UNCOVERED]** - Changed agent markdown files to reject agent names containing `:`, which is reserved for plugin namespacing
- **[UNCOVERED]** - Changed skills with `context: fork` to run in the background by default; opt out per skill with `background: false`
- **[UNCOVERED]** - Added `yes`/`no`/`on`/`off`/`1`/`0` (case-insensitive) as accepted values for skill and plugin frontmatter booleans, alongside `true`/`false`
- **[UNCOVERED]** - Fixed remote sessions continuing to send heartbeats after their worker was replaced, which left long-lived desktop and IDE processes retrying a rejected request every few seconds forever

#### v2.1.217

- **[UNCOVERED]** - Added emoji shortcode autocomplete in the prompt input: type `:heart:` to insert ❤️, or `:hea` for suggestions — disable with the `emojiCompletionEnabled` setting
- **[UNCOVERED]** - Added warnings when transcript writes are failing (e.g. disk full) or when session saving is off due to an inherited environment variable, instead of losing transcripts silently
- **[UNCOVERED]** - Fixed a memory leak where truncated MCP tool outputs kept the full untruncated result in memory for the rest of the session
- **[UNCOVERED]** - Fixed Windows auto-update failures that could leave `claude.exe` missing; failed updates now restore the preserved executable automatically
- **[UNCOVERED]** - Fixed background session isolation not canonicalizing symlinked working directories, which could let sessions escape their workspace folder
- **[UNCOVERED]** - Fixed auto-compact never triggering for Claude Opus 4.8 on Bedrock and `/compact` failing once over the limit
- **[UNCOVERED]** - Fixed corporate mTLS, TLS-verify, OAuth scope, and proxy settings being ignored in Claude Desktop sessions
- **[UNCOVERED]** - Fixed screen reader mode's startup announcement being cut off by the first prompt render, and the thinking status row re-rendering every few seconds to update elapsed time and token counts
- **[UNCOVERED]** - Fixed managed settings that set `OTEL_EXPORTER_OTLP_ENDPOINT` not governing all signals — lower-scope signal-specific overrides no longer redirect telemetry away from the managed endpoint
- **[UNCOVERED]** - Fixed `--resume`/`--continue` and `/resume` failing with a TypeError when a transcript has a malformed attachment entry
- **[UNCOVERED]** - Fixed Remote Control sessions not showing a pending permission prompt or dialog to viewers that connected after it appeared
- **[UNCOVERED]** - Fixed background shells sometimes becoming impossible to stop after a session is sent to the background (`/background` or `←`) or when the session exits on a heavily loaded machine, most visible on Windows
- **[UNCOVERED]** - Fixed a `CLAUDE.md` or `SKILL.md` paths frontmatter value with many brace groups OOM-killing or stalling the CLI at startup — brace expansion is now budget-bounded
- **[UNCOVERED]** - Fixed the transcript preview sitting flush against the input area when attaching to a starting background session; it now leaves the same one-line gap as the live layout, so the transcript no longer shifts when the session takes over
- **[UNCOVERED]** - Improved footer PR badge links to be clickable hyperlinks even when terminal support can't be detected (e.g. over ssh/tmux); set `FORCE_HYPERLINK=0` to opt out
- **[UNCOVERED]** - Changed the login-expiry warning to appear 3 days before expiry instead of 5
- **[UNCOVERED]** - Capped the frontend-design plugin suggestion tip at 3 lifetime impressions instead of repeating indefinitely
- **[UNCOVERED]** - Added a cap on concurrently-running subagents (default 20, override with `CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS`) so one message can't fan out unbounded background agents
- **[UNCOVERED]** - Changed subagents to no longer spawn nested subagents by default; set `CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH` to allow deeper nesting
- **[UNCOVERED]** - Fixed `--max-budget-usd` not stopping background subagents: once the cap is reached, new spawns are denied and running background agents are halted

#### v2.1.216

- **[UNCOVERED]** - Added `sandbox.filesystem.disabled` setting to skip filesystem isolation while keeping network egress control
- **[UNCOVERED]** - Fixed a slowdown in long sessions where message normalization cost grew quadratically with the number of turns, causing multi-second stalls and slow resumes
- **[UNCOVERED]** - Fixed auto mode denying commands with "HTTP 401" classifier errors after the OAuth token expired or rotated mid-session
- **[UNCOVERED]** - Fixed AskUserQuestion telling Claude to continue even when your answer asked it to wait or explain first — free-text answers now get neutral wording
- **[UNCOVERED]** - Fixed Claude Code on the web re-asking the same question and dropping your answer after the session sat idle for a few minutes
- **[UNCOVERED]** - Fixed @-mentions silently attaching nothing after file-modifying hooks, vim dot-repeat of `c`-operators and paste, statusline running twice on resume, and resume-picker hangs on failure
- **[UNCOVERED]** - Fixed resumed background agent sessions reverting to the default agent: the agent's prompt and tool restrictions are now restored
- **[UNCOVERED]** - Fixed worktree-isolated subagents redirecting git into the shared checkout via `git -C`, `--git-dir`, or `GIT_DIR`/`GIT_WORK_TREE`
- **[UNCOVERED]** - Fixed worktree sessions landing in another project's leftover worktree when the working directory did not match the selected project
- **[UNCOVERED]** - Fixed background sessions whose worktree has no git repository being undeletable
- **[UNCOVERED]** - Fixed `claude daemon stop --any` potentially terminating an unrelated process via a stale legacy daemon lockfile
- **[UNCOVERED]** - Fixed Esc-Esc at an idle prompt not opening the rewind picker in long-running sessions with background tasks
- **[UNCOVERED]** - Fixed Bash command permission checking for compound statements with redirects inside `&&` lists or negations
- **[UNCOVERED]** - Fixed pressing Ctrl+X twice in the agent list failing to delete a session, and deleted sessions reappearing when their background worker had died
- **[UNCOVERED]** - Fixed background subagents getting cancelled when a high-priority message arrives during their startup window
- **[UNCOVERED]** - Fixed mouse and focus garbage in the terminal while a GUI editor from `/memory`, `/plan`, `/keybindings`, or Ctrl+G is open; `/memory` no longer waits for the editor to close
- **[UNCOVERED]** - Fixed Claude-in-Chrome 403-looping on reconnect when the session's OAuth token lacks a required scope
- **[UNCOVERED]** - Fixed workflow saves and scheduled-task writes following a symlink at `.claude`, which could redirect writes outside the project
- **[UNCOVERED]** - Fixed MCP re-authenticate revoking working credentials before the new sign-in succeeds, and the reconnect needs-auth message in background sessions pointing at an unusable command
- **[UNCOVERED]** - Fixed read-only commands on Windows accessing network paths without a permission prompt
- **[UNCOVERED]** - Fixed Bash command parsing of non-ASCII characters to match real shell word boundaries
- **[UNCOVERED]** - Fixed PowerShell tool permission validation of commands containing invisible Unicode characters
- **[UNCOVERED]** - Fixed dialogs in fullscreen mode stretching past the right-hand edge of their panel
- **[UNCOVERED]** - Fixed the `/config` settings list in fullscreen mode clipping its keyboard-hint footer
- **[UNCOVERED]** - Fixed the transcript-mode (Ctrl+O) footer hint wrapping on terminals narrower than 104 columns
- **[UNCOVERED]** - Fixed the Prometheus metrics endpoint (`OTEL_METRICS_EXPORTER=prometheus`) emitting invalid `# UNIT` lines
- **[UNCOVERED]** - Fixed skills and commands changed during a session not appearing in the slash menu until restart
- **[UNCOVERED]** - Fixed plugin skills with a `name` frontmatter field losing their plugin prefix in slash-command autocomplete
- **[UNCOVERED]** - Fixed telemetry misreporting permission denials: failed permission-prompt requests no longer count as user rejections, and user interrupts are now reported as user aborts instead of rejections
- **[UNCOVERED]** - Improved the `/fork` confirmation to one line with the new session's name, `claude attach` id, and a note when the copy shares your checkout
- **[UNCOVERED]** - Improved validation of `git` and `gh` command arguments in the PowerShell tool
- **[UNCOVERED]** - Improved the `/ultrareview` diff-too-large error to show configured limits, measured diff size, and largest contributing files
- **[UNCOVERED]** - Improved `/code-review ultra` empty-diff message to name the exact base ref and suggest passing an explicit base
- **[UNCOVERED]** - Improved the spend limit adjustment prompt to show the server's reason when a spend limit change is rejected
- **[UNCOVERED]** - `/context` now shows an explicit warning when the conversation exceeds the context window, and a failed `/compact` displays as an error
- **[UNCOVERED]** - `/rewind` no longer restores or deletes files through symlinks or hard links at tracked paths and reports how many paths it skipped
- **[UNCOVERED]** - Background sessions: `/mcp` and `/install-github-app` now park a "needs input" request in the agent view when no client is attached
- **[UNCOVERED]** - Updated the bundled dataviz skill: reordered the default chart palette and fixed guidance that suggested direct labels for four-series charts
- **[UNCOVERED]** - [VSCode] Fixed right-to-left text (Arabic, Hebrew, Persian) rendering in the wrong order when mixed with English or code
- **[UNCOVERED]** - Fixed cloud sessions dropping the in-flight message when the session's container restarts mid-turn — the interrupted turn now re-runs on resume instead of leaving the session unresponsive

---
_Generated by `.github/scripts/changelog-compare.py`_
## Native Sources Monitor Report

Sources checked: **3**

### anthropic-blog

- Source: Anthropic Blog — announcements and product updates
- Entries fetched: 13
- New uncovered: 2

| Entry | Section | Description |
|-------|---------|-------------|
| Aug 4, 2026AnnouncementsMariano-Florentino (Tino) Cuéllar to | Anthropic Blog | Aug 4, 2026AnnouncementsMariano-Florentino (Tino) Cuéllar to join Anthropic as C |
| Jul 22, 2026Economic ResearchA research agenda for the Econo | Anthropic Blog | Jul 22, 2026Economic ResearchA research agenda for the Economic Futures Research |

### cc-issues-enhancement

- Source: CC GitHub Issues labeled 'enhancement'
- Entries fetched: 300
- New uncovered: 3

| Entry | Section | Description |
|-------|---------|-------------|
| [Feature Request] Add built-in security vulnerability scanni | GitHub Issues (enhancement) | **Bug Description** Esoy testeando mi producto localmente, tengo que validar si  |
| [FEATURE] Disable honking, sussing, cogitating, spelunking,  | GitHub Issues (enhancement) | ### Preflight Checklist - [x] I have searched [existing requests]( and this feat |
| Aviso de "archivo modificado externamente" expone contenido  | GitHub Issues (enhancement) | Al trabajar en un proyecto interno con múltiples módulos (cada uno con su propio |

### cc-discussions-feature-request

- Source: CC GitHub Discussions in feature-request category
- Entries fetched: 0
- New uncovered: 0

---
Total new uncovered entries: **5**

_Generated by `.github/scripts/native-sources-monitor.py`_
