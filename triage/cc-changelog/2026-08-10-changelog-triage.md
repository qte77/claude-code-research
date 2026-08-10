# CC Changelog & Native Sources: New Uncovered Features Detected

## Changelog Monitor Report

Last scanned version: **2.1.215**
New versions detected: **11**

### New Versions Summary

| Version | Features | Covered | Uncovered |
|---------|----------|---------|-----------|
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
- New uncovered: 2

| Entry | Section | Description |
|-------|---------|-------------|
| Organizacao de trabalhos diversos | GitHub Issues (enhancement) | ### Preflight Checklist - [x] I have searched [existing requests]( and this feat |
| Configuración nativa de idioma en vez de depender de instruc | GitHub Issues (enhancement) | ### Preflight Checklist - [x] I have searched [existing requests]( and this feat |

### cc-discussions-feature-request

- Source: CC GitHub Discussions in feature-request category
- Entries fetched: 0
- New uncovered: 0

---
Total new uncovered entries: **4**

_Generated by `.github/scripts/native-sources-monitor.py`_
