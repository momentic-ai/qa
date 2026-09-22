# qa

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
