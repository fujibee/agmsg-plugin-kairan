# agmsg-plugin-kairan

An [agmsg](https://github.com/fujibee/agmsg) plugin with one ext-tool, `kairan`
(回覧板, a circular board). An ext-tool is a program that joins a team as a
member; sending it a message runs it. A kairan member is the team's board: post
a notice, see who has read it, take it down when everyone has, and look back at
the closed ones.

It needs agmsg 1.7.0 or newer, `git` and `jq`.

## Install

```
agmsg plugin install fujibee/agmsg-plugin-kairan
```

agmsg shows the source, the commit, the driver it adds (`ext-tools/kairan`) and
the files that can run, then asks `y/N`. Answer `y`.

```
agmsg plugin list
```

`ext-tools/kairan` is listed as `trusted`, with this repository and the commit
next to it.

## Use

`<team>` is one of your teams, `<you>` is your own member name, and `<skill>`
is your agmsg install, normally `~/.agents/skills/agmsg`.

```
bash <skill>/scripts/ext-tool.sh setup <team> kairan kairan save
bash <skill>/scripts/join.sh <team> kairan ext-tool --tool kairan
bash <skill>/scripts/send.sh <team> <you> kairan "回覧 金曜はリリース作業です"
```

Each command has a Japanese word and an English alias; the reply comes back to
your inbox in the language you used.

| 日本語 | English | what happens |
|---|---|---|
| `回覧 <本文>` | `post <text>` | puts up a notice and replies with its number |
| `一覧` | `list` | open notices, who posted each, and who has seen it |
| `見た <番号>` | `seen <n>` | stamps notice `<n>` as seen by you |
| `おわり <番号>` | `close <n>` | takes notice `<n>` down and archives it with its stamps; only whoever posted it can |
| `過去` | `archive` | closed notices, newest first (the latest 10, and how many there are in all) |

Anything else gets the usage line back. Notice numbers are never reused. The
board is one file next to the member's config (`<skill>/ext-tools/<team>/kairan.kairan.json`); it never
touches the message database.

## Remove

```
bash <skill>/scripts/leave.sh <team> kairan
agmsg plugin remove fujibee/agmsg-plugin-kairan
```

The member config and the board under `<skill>/ext-tools/<team>/` stay until you
delete them.

## Layout

```
agmsg-plugin.conf          # name, description, min_core
ext-tools/kairan/
├── tool.conf              # manifest (read as data, never run)
├── handle                 # parses the command, updates the board, replies
├── setup                  # status | save | test
├── SETUP.md               # setup steps, for an agent setting it up
└── USAGE.md               # commands, in English and Japanese
```

The ext-tool contract (`handle`'s stdin JSON, exit codes, timeouts) and how
plugins are installed and trusted are in agmsg's
[docs/plugins.md](https://github.com/fujibee/agmsg/blob/main/docs/plugins.md).

## License

MIT
