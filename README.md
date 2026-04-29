# pyck CLI

Official binaries for the [pyck](https://pyck.cloud) warehouse management
platform CLI.

This repository hosts release artifacts only. Source is not public.

## Install

### Homebrew (macOS, Linux)

```sh
brew install pyck-ai/tap/pyck
```

### Direct download

Latest release: <https://github.com/pyck-ai/pyck-cli/releases/latest>

| OS      | Arch          | Archive                            |
| ------- | ------------- | ---------------------------------- |
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

- This is **not** a `go install`-able package. The Go module path
  `github.com/pyck-ai/pyck-cli` resolves to this repo, which contains
  no source. Use Homebrew or the binary downloads above.
- macOS users will see a Gatekeeper warning on first run because the
  binary is unsigned. To allow it:

  ```sh
  xattr -d com.apple.quarantine $(which pyck)
  ```

## Bug reports

File issues against this repository.
