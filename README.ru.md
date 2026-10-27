# Пакеты Chistore

Репозиторий заархивирован. Он доступен только для чтения и больше не обновляется.

Для новых установок есть [Chistore-go](https://gitgud.io/name-cho/Chistore-go) и
его основной репозиторий
[chistore-repo](https://gitgud.io/name-cho/chistore-repo). Этот оставлен для
старого Bash-менеджера и для тех, у кого эти пакеты уже стоят.

- GitGud: <https://gitgud.io/name-cho/Chistore>
- GitHub: <https://github.com/name-cho/Chistore>

[English](README.md)

## Chistore-go

Установка менеджера:

```bash
curl -fsSL https://raw.githubusercontent.com/name-cho/Chistore-go/main/scripts/install.sh -o /tmp/chistore-install.sh
bash /tmp/chistore-install.sh
```

На Windows используйте `scripts/install.ps1` из репозитория Chistore-go.

Репозиторий по умолчанию это `chistore-repo`. Чтобы добавить этот:

```bash
chistore repo add legacy https://gitgud.io/name-cho/Chistore/-/raw/main --priority 30
chistore repo refresh
```

## Пакеты

| Пакет | Описание |
| --- | --- |
| `deskgen` | создание и редактирование `.desktop`-файлов |
| `envsnap` | снимки состояния системы и окружения, сравнение |
| `netdiag` | проверка IP, ping, DNS, портов и скорости |
| `pystat` | монитор системы с TUI |

## Структура

```text
Chistore/
├── index.json          # метаданные пакетов и SHA-256
├── INDEX               # старый индекс, один пакет на строку
├── VERSION
├── chistore            # старый Bash-менеджер
└── <пакет>/
    ├── info.md
    └── <файл>
```

`index.json` создаёт `chistore pkg index`. `INDEX` нужен старым клиентам.
Chistore-go умеет читать репозитории без `index.json`.

## Как добавить пакет

```bash
chistore pkg init hello
# заполнить hello/info.md, заменить файл пакета
chistore pkg validate
chistore pkg index
```

Держите `.gitattributes` с `* text=auto eol=lf`. `pkg index` хеширует байты,
которые отдаёт Git, и CRLF в рабочей копии на Windows дал бы хеши, которые не
сходятся при установке.

Сначала пуш в GitGud, потом в GitHub.

## Bash-менеджер

Скрипт `chistore` и `VERSION` лежат здесь для тех, кто ещё пользуется Bash-версией.
Новым пользователям нужен Chistore-go.
