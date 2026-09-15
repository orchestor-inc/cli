# Orchestor CLI

Use Orchestor from your terminal.

This repository hosts CLI releases, installation instructions, and the issue tracker. The CLI implementation is maintained separately.

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

## Update

For installations made with the macOS/Linux installer:

```sh
orc update
```

For a manually downloaded Windows executable, replace it with the executable from the latest release.

## Release files

Each release contains binaries for macOS (Apple silicon and Intel), Linux (x64 and arm64, glibc and musl), and Windows (x64 and arm64), plus `install.sh` and `checksums.txt`.

Verify an archive against the SHA-256 digest in `checksums.txt` before extracting it. macOS binaries have ad-hoc signatures and are not notarized. Windows binaries are unsigned.

## Documentation and support

- [CLI documentation](https://orchestor.io/docs/cli)
- [Report a bug](https://github.com/orchestor-inc/cli/issues/new?template=bug_report.yml)
- [Report a security vulnerability](SECURITY.md)
