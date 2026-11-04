# qa

## 0.31.1

### Patch Changes

- ecc4f0f: When HTTPS traffic is intercepted during sign-in, the error now explains how to trust your corporate certificate with --use-system-ca or NODE_EXTRA_CA_CERTS.
- 7252ef0: Improve inference speed by scaling screenshots appropriately
- 6ba8002: Explain missing inputs and filesystem access failures without internal crash reports. Return a 400 response for malformed JSON requests to the local editor and MCP servers, and keep local project settings when organization settings cannot be reached.

## 0.31.0

### Minor Changes

- fe3eb56: Add pull request and commit references to bug fix and reopen commands.
- 37de26a: Each CLI's pointer block lists only its own skills, and each command rewrites only its own block. The new `devin` target installs skills to `.devin/skills` and writes its pointer in `AGENTS.md`. `qa skills` installs only `mo-qa`. Reinstalling removes skills that this CLI generated earlier and no longer ships, unless another Momentic CLI's pointer in the repository lists the same skills directory.

### Patch Changes

- 193b9f6: Fix send waits timing out after Mo starts a new turn.
- b351774: Mo's Human interaction speed now types at about 120 words per minute.
- 89d309b: Mo's setup actions are less likely to change the wrong item on a crowded page.
- 651e036: A retest you request in Mo now finishes even after the session's time budget is spent.

## 0.30.1

### Patch Changes

- 35b21db: Omit `completed` from `qa send` JSON while preserving its other response fields, and update its help, documentation, and skill guidance. Hide internal Mo wakeups from public read output and latest-message previews while preserving persisted history and stream bookkeeping.
- 756ff1f: Simplify the Mo skill and documentation for sending follow-up messages.

## 0.30.0

### Minor Changes

- d1b3166: Add accept, review, dismiss, fix, and reopen commands for finding triage. Bug
  output includes lifecycle status and dismissal reason. Legacy set-status values
  keep their meaning; ambiguous short bug IDs require the exact finding name.
- 4be9109: Add `qa start --no-test-cases` to skip Mo's observed test cases, which are recorded in the background from agent activity.
- ef1d07f: Improve browser session reliability and cleanup.

### Patch Changes

- 7c4720c: Fix `qa tunnel start`, `list`, and `stop` in the standalone binary, which reported running tunnels as unreachable and failed detached starts.

## 0.29.0

### Minor Changes

- 207d019: Remove test-case data from CLI reports and status output.

  Expose the root agent's explicit completion flag in status, read, wait, and
  report JSON, independently of session lifecycle and agent verdicts.

- 0d3da20: Give each bug a shell-safe `id` next to its name in `qa status --full`, `qa bugs`
  output, and reports. Add `qa bugs describe <session-id> <bug>` for one bug's
  full details; it and `qa bugs set-status` accept the id or the exact name.

  `qa status --full` now lists bugs (id, name, kind, summary) with counts, the
  latest message, and the blocker reason, and omits verdicts. Add `--output <file>`
  to `qa status`, `qa bugs list`, and `qa bugs describe`.

- 0d3da20: `qa report` always exports and always includes Mo finding links. When Mo is not
  done, it warns on stderr that the report may be partial and lists the warning in
  `report.json` `warnings`. `--require-idle` is no longer needed; it is accepted
  and ignored so existing scripts keep running.
- 0d3da20: CLI JSON now reports the session's state as one `status` field, the word the web
  UI shows (`running`, `needs_you`, `findings`, `ready`, …). It replaces
  `displayState`, `sessionState`, and the legacy `state` in `qa status`,
  `qa read --json`, `qa wait --json`, `qa send`, and the `report.json` summary.
  The API is unchanged, so older `qa` versions keep working; scripts that parse
  this CLI's JSON should read `.status`.
- 6e974f3: Show session progress in `qa status`: test case outcomes, suspected bugs, active sub-agents and testing-clock minutes. `--full` also lists each sub-agent.

### Patch Changes

- 754e33f: A plain `qa send` now answers Mo's open question card, and `qa read`, `qa wait` and `qa send --wait` print how to answer a pending question.
- 3de8c28: Include culprit changes and source links in exported bug reports.
- 3441217: Retry uploads after temporary network and server failures.
- 4fb860c: Update validation security protections while preserving existing bulk request sizes.
- 15d99c9: `qa read`, `qa wait` and `qa send --wait` list every open Mo question card with its id. `--question-id` no longer fails for a card that is not open; the text is sent as a normal message.
- 21b628d: `qa status` no longer prints `attentionPending` (`status: "checking"` means the same), and help and the bundled `mo-qa` skill describe `checking` as an unknown outcome.
- 0d3da20: Show the JSON each command prints in its `--help`.
- 0d3da20: Fix `qa` output being cut off at 64 KB when stdout is a pipe, such as `qa status --full | jq`.
- 6e974f3: `qa report` prints each warning once and names the artifact type in download errors, the issue draft says "Not captured." when no page URL was recorded, and `qa stop --subagents` no longer implies exporting after stopping. `qa send` takes the session ID as its first argument, like the other session commands; `--session-id` still works.
- 0d3da20: Accept `--json` on commands that always print JSON, list each effort's testing time in `qa start --help`, note that sub-agents take time to shut down after `qa stop --subagents`, and say a stopped session's report covers work up to the stop.
- 0d3da20: `qa version` no longer suggests upgrading when the installed CLI is newer than
  the server's latest release.
- 52d6e82: Recover interrupted mobile sessions and give restarted device drivers time to become ready.

## 0.28.0

### Minor Changes

- 9b188e3: Let Mo ask questions while continuing work, and answer specific questions from the CLI.

### Patch Changes

- 360bd47: Recover more reliably from temporary recording upload failures.
- acdcad5: Include the connector enrollment log when qa tunnel start fails.

## 0.27.1

### Patch Changes

- 4ba58ae: Show the real Connector error when qa tunnel start fails on Windows, instead of a temporary directory cleanup error.
- 3847c4f: Make tunnel startup easier to read, with clear next steps and JSON output for scripts.

## 0.27.0

### Minor Changes

- e45b0f4: Add qa unarchive to restore archived Mo sessions and continue the conversation.

## 0.26.0

### Minor Changes

- 01fb23f: Add `qa start --effort low|medium|high|max` to choose testing effort. Effort sets the session's default concurrency and testing time; medium is the default.

### Patch Changes

- 2cd024b: Explain tunnel target mismatches with actionable diagnostics when starting a session or navigating.

## 0.25.0

### Minor Changes

- beb0def: Export complete bug reports with available videos, screenshots, browser logs, and structured evidence for coding agents.

## 0.24.0

### Minor Changes

- e39bbb2: Choose regular or large browsers with --size when starting Mo sessions.
- 9a26778: Added command to set bug statuses

### Patch Changes

- ab40d1d: Honor HTTP_PROXY, HTTPS_PROXY, and NO_PROXY for API requests.
- 7505bee: Let Mo finish reproducing bugs without a time limit.

## 0.23.0

### Minor Changes

- a6b1c24: Add configurable session-level budgets

### Patch Changes

- 5fcd66a: Fix `qa tunnel start` failing immediately on Windows, and let `qa upgrade` update the Windows release binary in place.

## 0.22.2

### Patch Changes

- fb8b9b4: Better support for public GitHub repositories.

## 0.22.1

### Patch Changes

- 8606f47: Show login and site protection requests in Mo CLI output and report when user input is needed to continue.

## 0.22.0

### Minor Changes

- 6ba389c: Enable WebGL when starting browser sessions with --webgl.

## 0.21.1

### Patch Changes

- 34dad77: Include pending attention status in compact session status output.

## 0.21.0

### Minor Changes

- 7658486: Updates to session startup and validation.

## 0.20.2

### Patch Changes

- dd45470: Add a one-time Node.js compatibility build for Windows Server 2016.

## 0.20.1

### Patch Changes

- e114377: Keep failed checks visible in reports and distinguish sub-agent execution status from its last submitted result.

  Default new Momentic web sessions to Turbo while preserving organization and mobile restrictions.

## 0.20.0

### Minor Changes

- 203dad2: Start Mo sessions for GitHub pull requests from the CLI with focused testing, preview discovery, and code diagnoses in bug reports. Supply curated local patches from the PR checkout when pushing is disallowed; the CLI reads their base revision from local HEAD.

  The QA skill leaves flow selection, test cases, and delegation to Mo within the user's scope and budget, while coding agents handle access and host coordination.

## 0.19.3

### Patch Changes

- bd15974: Security fixes.
- 66c5f71: Show a clear, actionable error instead of a crash when the skills command can't write to a read-only instructions file or skills directory.
- 428b6d1: `qa start` now shows the API's validation message (for example, an unknown environment name) as a user-facing error instead of reporting it as an unexpected CLI failure.
- 7cd63a7: Remove the --granularity option from qa start. Describe the desired test depth in the session brief.
- e719941: Fix the Mo CLI crashing on startup on Windows, including GitHub Actions runners.

## 0.19.2

### Patch Changes

- 9f0cd97: Unify session state across `qa read`, `qa status`, and `qa report`: `displayState` now reports the same UI-visible session state on all three commands, `sessionState` and `state` carry the lifecycle state everywhere, and `status.state` switches from the display word to the lifecycle word.

## 0.19.1

### Patch Changes

- 9fcca29: Upgrade finishes the mo-to-qa rename automatically and qa doctor runs the same checks as momentic doctor.

## 0.19.0

### Minor Changes

- ede7955: Add `qa doctor` for install diagnostics, make the npm wrapper self-heal missing platform binaries (MO_BINARY_PATH override, on-demand install, package-manager-aware repair hints, Windows ARM64 to x64 fallback), and rename the command and installed binary to `qa` on every channel: the npm package drops its `mo` shim (npm removes it on update) and the standalone installer writes `qa` instead of `mo`. Releases keep publishing `mo-<target>` GCS aliases so installed `mo` binaries can still self-upgrade; an old `mo` file keeps its name after upgrading.

## 0.18.0

### Minor Changes

- 566b892: Add `mo start --interaction-speed` with `default` and `human` browser pacing options.

### Patch Changes

- f6e56d5: Update npm page copy and package metadata: descriptions, keywords, homepage, bugs, and README headers.
- 8cc3a5e: Start a Mo session with `qa <url>` (or `mo <url>`), e.g. `npx qa https://your-app.com`.

## 0.17.0

### Minor Changes

- 2698901: Add a `mo wait` command to wait for a session to finish or ask for input.
- 387a76c: Install the Mo CLI with `npm install -g qa`, including binaries for macOS, Linux, and Windows.
- 6110d03: Remove the deprecated --momentic-mode option; Mo always uses Momentic browser tools. Remove this option from existing commands.

### Patch Changes

- ca82255: Failed commands now print a machine-readable error line to stderr with a stable error code for scripts and CI, and every failure exits with a consistent code.
- e17599c: Add the `mo cost <session-id>` command for inspecting session costs.
- 2fab330: An API key that was copied incompletely (for example with a trailing "…") is now reported as an invalid key instead of a network error.

## 0.16.0

### Minor Changes

- 0aa1bc1: Add session environment variables from local files or selected process variables.

### Patch Changes

- 5f0027e: Update Mo's QA skill to include mo update.

## 0.15.0

### Minor Changes

- 4ce7658: Add `mo upgrade` to replace the installed binary with the latest checksum-verified release, and prompt to run it when a newer version is available.
- 7f0d459: Allow Mo sessions to start in a selected cloud environment.

## 0.14.0

### Minor Changes

- 2ba4e90: Bundle the Momentic coding agent skills with the CLIs. Install them with momentic skills, momentic-mobile skills, or mo skills. The CLI asks once when an upgrade ships newer skills, and init and the wizard offer skills and MCP setup.

### Patch Changes

- 1690ce3: Installed `SKILL.md` files end with a footer that names the CLI version and skills version that generated them.

## 0.13.0

### Minor Changes

- 5049de0: Add the mo report command to export findings and reproduction videos.

### Patch Changes

- b1b545c: Update bundled dependencies to address a security advisory.
- a1efdc8: Keep mo status polling focused on root test cases, bugs, and signed-off verdicts.

## 0.12.0

### Minor Changes

- a492973: Keep Mo CLI responses compatible with new server states and message roles.
- 816be7d: Make mo status compact by default and use --full for the latest message and complete findings.

## 0.11.2

### Patch Changes

- b9f51c8: Remove the obsolete repository option now that GitHub access follows the organization's app installation.
- 055f67a: Add `mo stop --subagents` to stop running and queued sub-agents without closing their conversations.

## 0.11.1

### Patch Changes

- 6b86c95: Correct CLI sign-in hints for each published command.

## 0.11.0

### Minor Changes

- 5b5ea0e: Add a version command that checks for the latest available Mo functionality.

## 0.10.1

### Patch Changes

- e1be0d8: Allow Mo sessions to set a maximum sub-agent concurrency.

## 0.10.0

### Minor Changes

- 2d52f12: Add login and logout commands that share credentials with the other Momentic CLIs.

## 0.9.0

### Minor Changes

- b571f95: Allow Mo sessions to opt into read-only context from a connected GitHub repository.
- 9805314: Add managed Connector tunnels for exposing local applications to Mo, with background lifecycle and explicit list and stop commands.

## 0.8.0

### Minor Changes

- fd52af5: Add Connector tunnel support to mo start.

## 0.7.0

### Minor Changes

- a40f83c: Add a Mo session granularity setting for explore-agent coverage.

## 0.6.0

### Minor Changes

- d2a930c: Allow Mo sessions to start with configurable session settings.
- 3998eba: Add the mo archive command for stopping and archiving a session.

### Patch Changes

- 79c5615: Reject messages sent to archived Mo sessions.

## 0.5.0

### Minor Changes

- 4e89896: Add `mo send --wait <duration>` to return session output at the next attention boundary.

## 0.4.0

### Minor Changes

- f8e8ff6: mo send now steers a live Mo turn: mid-turn messages are injected at the next tool-step boundary instead of waiting for the turn to end, and CLI messages show a "Sent from the CLI" label in the web transcript

### Patch Changes

- 73d0e4e: Show files attached to Mo messages in `mo read`/`mo status` output, and refuse symlinked sources in `mo download`.
- 7add1ae: mo send now stops an active turn before it sends the new message, and Mo continues from saved history.

## 0.3.0

### Minor Changes

- 6160bdc: Add `mo read` with realtime waiting, timeout handling, history replay, and structured output.

## 0.2.0

### Minor Changes

- bf7edf3: Add a send command for messaging existing Mo sessions.
- c14fb32: Add `mo upload` to copy a local file onto a Mo session machine.
- e4abf6a: Add file downloads from Mo session machines to the Mo CLI.

### Patch Changes

- 4c7d62d: Remove the `why-is-node-running` dependency so that CLI installs no longer fail when the package manager blocks it as an untrusted release

## 0.1.0

### Minor Changes

- 6b3140c: Add `mo start` to start a Mo session from the CLI.
- 6b3140c: Add `mo stop` to stop a running Mo session from the CLI.

## 0.0.2

### Patch Changes

- eef26e4: Support Alpine and other musl-based Linux distributions.

## 0.0.1

### Patch Changes

- 46b7f18: Publish standalone mo binaries for macOS, Linux, and Windows.
