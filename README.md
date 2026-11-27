# Orchestor CLI

[![Latest release](https://img.shields.io/github/v/release/orchestor-inc/cli?label=release)](https://github.com/orchestor-inc/cli/releases/latest)
[![License](https://img.shields.io/github/license/orchestor-inc/cli)](LICENSE)

Generate images, video and speech from your terminal with `orc`, the command-line interface for [Orchestor](https://www.orchestor.io).

```sh
orc creative image generate --model gpt-image-2 --prompt "A red cube on a white background" --wait
```

This repository holds CLI releases, the install script and the issue tracker. The CLI source is maintained separately.

## Install

### macOS and Linux

```sh
curl -fsSL https://orchestor.io/install | sh
orc --version
```

Node.js is not required. On Alpine Linux, install `libstdc++` first:

```sh
apk add --no-cache libstdc++
```

### Windows

Download the archive for your architecture from [Releases](https://github.com/orchestor-inc/cli/releases/latest), extract `orc.exe`, and run it from PowerShell:

```powershell
.\orc.exe --version
```

## Quick start

```sh
orc auth login                # sign in through your browser
orc workspace use <id>        # pick a workspace from `orc workspaces list`
orc creative image generate --model gpt-image-2 --prompt "A red cube on a white background" --wait
```

For scripts and CI, set `ORCHESTOR_API_KEY` from your secret manager instead of `orc auth login`.

## Usage

Generate a video and print only its URL:

```sh
orc creative video generate --model seedance-2.5 --prompt "Slowly moving along a coast at dawn" \
  --wait --timeout 10m --field result.video_url --raw
```

Turn a script into narration:

```sh
printf '%s\n' '{"model":"qwen-audio-3.0-tts","transcript":"Hello.","voice":{"id":"Ono_Anna"}}' \
  | orc creative tts generate --stdin --wait --field result.audio_url --raw
```

Find voices with `orc creative tts voices list`.

Run a job in the background and check on it later:

```sh
orc creative image generate --model gpt-image-2 --prompt "A red cube" --json   # returns job.id
orc creative jobs status <job-id>
orc creative jobs result <job-id>
```

List models before you pick one:

```sh
orc creative image models list
orc creative video models list
```

Every command accepts `--json`, `--field`, `--raw` and `--help`.

## Update

For installations made with the macOS and Linux installer:

```sh
orc update
```

For a manually downloaded Windows executable, replace it with the executable from the latest release.

## Release files

Each release contains binaries for macOS (Apple silicon and Intel), Linux (x64 and arm64, glibc and musl), and Windows (x64 and arm64), plus `install.sh` and `checksums.txt`.

Verify an archive against the SHA-256 digest in `checksums.txt` before extracting it. macOS binaries have ad-hoc signatures and are not notarized. Windows binaries are unsigned.

## Use it from an agent

Coding agents can call `orc` directly. To connect an agent without the CLI, use the hosted [MCP server](https://www.orchestor.io/docs/en/mcp) or install the [Orchestor plugin](https://github.com/orchestor-inc/orchestor-plugin).

## Documentation and support

- [CLI documentation](https://www.orchestor.io/docs/en/cli)
- [Release notes](https://github.com/orchestor-inc/cli/releases)
- [Report a bug](https://github.com/orchestor-inc/cli/issues/new?template=bug_report.yml)
- [Report a security vulnerability](SECURITY.md)

## License

See [LICENSE](LICENSE).
