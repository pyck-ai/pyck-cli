# pyck CLI

Official binaries for the [pyck](https://pyck.cloud) warehouse management
platform CLI.

This repository hosts release artifacts only. Source is not public.

## Install

### macOS / Linux (Homebrew)

```sh
brew install pyck-ai/tap/pyck
```

### Linux

```sh
VERSION=$(curl -s https://api.github.com/repos/pyck-ai/pyck-cli/releases/latest \
  | grep '"tag_name"' | sed -E 's/.*"v?([^"]+)".*/\1/')
ARCH=$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/')
curl -L "https://github.com/pyck-ai/pyck-cli/releases/download/v${VERSION}/pyck_${VERSION}_linux_${ARCH}.tar.gz" \
  | tar -xz pyck
sudo install -m 755 pyck /usr/local/bin/
rm pyck
pyck version
```

### Windows (PowerShell)

```powershell
$version = (Invoke-RestMethod https://api.github.com/repos/pyck-ai/pyck-cli/releases/latest).tag_name -replace '^v',''
$arch    = if ($env:PROCESSOR_ARCHITECTURE -eq 'ARM64') { 'arm64' } else { 'amd64' }
$url     = "https://github.com/pyck-ai/pyck-cli/releases/download/v$version/pyck_${version}_windows_$arch.zip"
Invoke-WebRequest -Uri $url -OutFile pyck.zip
Expand-Archive -Force pyck.zip -DestinationPath .
# Move pyck.exe to a directory on your PATH, e.g.:
# Move-Item -Force .\pyck.exe "$env:USERPROFILE\bin\pyck.exe"
.\pyck.exe version
```

### Direct download

Latest release: <https://github.com/pyck-ai/pyck-cli/releases/latest>

| OS      | Arch          | Archive                              |
| ------- | ------------- | ------------------------------------ |
| macOS   | Apple Silicon | `pyck_<version>_darwin_arm64.tar.gz` |
| macOS   | Intel         | `pyck_<version>_darwin_amd64.tar.gz` |
| Linux   | arm64         | `pyck_<version>_linux_arm64.tar.gz`  |
| Linux   | amd64         | `pyck_<version>_linux_amd64.tar.gz`  |
| Windows | amd64         | `pyck_<version>_windows_amd64.zip`   |
| Windows | arm64         | `pyck_<version>_windows_arm64.zip`   |

Each release also publishes `checksums.txt` for SHA-256 verification.

## Verify

```sh
pyck version
```

## Auto-update

`pyck` checks for new releases at most once every 24 hours and prints a
notice if one is available. Disable the check with
`PYCK_NO_UPDATE_CHECK=1`.

To upgrade with Homebrew:

```sh
brew upgrade pyck
```

## Notes

- macOS users will see a Gatekeeper warning on first run because the
  binary is unsigned. To allow it:

  ```sh
  xattr -d com.apple.quarantine $(which pyck)
  ```

## Bug reports

File issues against this repository.
