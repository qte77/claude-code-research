# CC Changelog & Native Sources: New Uncovered Features Detected

## Changelog Monitor Report

Last scanned version: **2.1.215**
New versions detected: **5**

### New Versions Summary

| Version | Features | Covered | Uncovered |
|---------|----------|---------|-----------|
| 2.1.220 | 1 | 0 | 1 |
| 2.1.219 | 24 | 1 | 23 |
| 2.1.218 | 36 | 0 | 36 |
| 2.1.217 | 20 | 0 | 20 |
| 2.1.216 | 40 | 0 | 40 |

### Feature Coverage Details

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
- Entries fetched: 12
- New uncovered: 1

| Entry | Section | Description |
|-------|---------|-------------|
| Jul 22, 2026Economic ResearchA research agenda for the Econo | Anthropic Blog | Jul 22, 2026Economic ResearchA research agenda for the Economic Futures Research |

### cc-issues-enhancement

- Source: CC GitHub Issues labeled 'enhancement'
- Entries fetched: 300
- New uncovered: 1

| Entry | Section | Description |
|-------|---------|-------------|
| Configuración nativa de idioma en vez de depender de instruc | GitHub Issues (enhancement) | ### Preflight Checklist - [x] I have searched [existing requests]( and this feat |

### cc-discussions-feature-request

- Source: CC GitHub Discussions in feature-request category
- Entries fetched: 0
- New uncovered: 0

---
Total new uncovered entries: **2**

_Generated by `.github/scripts/native-sources-monitor.py`_
