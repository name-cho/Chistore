# Chistore packages

This repository is archived. It is read-only and gets no updates.

For new installs use [Chistore-go](https://gitgud.io/name-cho/Chistore-go) and its
default repository, [chistore-repo](https://gitgud.io/name-cho/chistore-repo). This
one stays online for the old Bash manager and for existing installations.

- GitGud: <https://gitgud.io/name-cho/Chistore>
- GitHub: <https://github.com/name-cho/Chistore>

[Русская версия](README.ru.md)

## Chistore-go

Install the manager:

```bash
curl -fsSL https://raw.githubusercontent.com/name-cho/Chistore-go/main/scripts/install.sh -o /tmp/chistore-install.sh
bash /tmp/chistore-install.sh
```

On Windows, use `scripts/install.ps1` from the Chistore-go repository.

The default repository is `chistore-repo`. To add this one:

```bash
chistore repo add legacy https://gitgud.io/name-cho/Chistore/-/raw/main --priority 30
chistore repo refresh
```

## Packages

| Package | Description |
| --- | --- |
| `deskgen` | create and edit `.desktop` files |
| `envsnap` | save system and environment state, compare snapshots |
| `netdiag` | check IP, ping, DNS, ports and speed |
| `pystat` | system monitor with a TUI |

## Layout

```text
Chistore/
├── index.json          # package metadata and SHA-256
├── INDEX               # old index, one package per line
├── VERSION
├── chistore            # old Bash manager
└── <package>/
    ├── info.md
    └── <payload>
```

`index.json` is written by `chistore pkg index`. `INDEX` is kept for older clients.
Chistore-go can read repositories without `index.json`.

## Adding a package

```bash
chistore pkg init hello
# edit hello/info.md, replace the payload
chistore pkg validate
chistore pkg index
```

Keep `.gitattributes` with `* text=auto eol=lf`. `pkg index` hashes the bytes Git
serves, and a CRLF checkout on Windows would produce hashes that fail on install.

Push to GitGud first, then to GitHub.

## Bash manager

The `chistore` script and `VERSION` are here for people who still use the Bash
version. New installations should use Chistore-go.
