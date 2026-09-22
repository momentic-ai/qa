# qa

Run Momentic's Mo agent from your terminal.

## Install

Install the CLI globally:

```bash
npm install -g qa
qa --help
```

Or run it without a global install:

```bash
npx qa --help
```

The npm package is `qa`. It installs a compiled `mo` binary for your system and
exposes both `qa` and `mo` commands. Both commands show `qa` in help when
installed through npm. The standalone installer uses `mo` in help.

The npm launcher requires Node.js 22.12 or later in the 22.x series, or Node.js
24 or later. Binaries are available for macOS ARM64/x64, Linux ARM64/x64 (glibc
and musl), and Windows x64. Linux musl requires `libstdc++`. Keep optional
dependencies enabled so npm can install your system's binary.

## Authentication

Sign in once to share credentials with the Momentic CLIs:

```bash
qa login
qa logout
```

Credentials are saved to `~/.momentic/auth.json`. Existing credentials from
`momentic login` or `momentic-wizard login` are reused automatically. You can
also provide `MOMENTIC_API_KEY` or `--api-key` for a single command.

## Update

Update a global npm installation with:

```bash
npm install -g qa@latest
```

For a project dependency, update `qa` with your project's package manager.
`qa upgrade` prints these instructions without replacing npm-managed files.

See the [Mo CLI reference](https://docs.momentic.ai/cli-reference/mo/overview)
for commands and examples. The reference's `mo` commands also work with `qa`.
