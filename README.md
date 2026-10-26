# agmsg-plugin-kairan

## What is a kairan?

A *kairanban* (回覧板, "circulating board") is how neighborhood associations in
Japan pass news around: a notice is clipped to a board that goes from house to
house, and each household stamps it with its seal (*hanko*) before handing it on.
Whoever sent it round can see at a glance who has read it. This plugin does the
same for a team: post a notice, everyone stamps it as seen, and you know who has
read it.

## About this plugin

An [agmsg](https://github.com/fujibee/agmsg) plugin with one ext-tool, `kairan`,
a circular board. An ext-tool is a program that joins a team as a
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
bash <skill>/scripts/send.sh <team> <you> kairan "post Release work on Friday"
```

The reply comes back to your inbox.

| command | what happens |
|---|---|
| `post <text>` | puts up a notice and replies with its number |
| `list` | open notices, who posted each, and who has seen it |
| `seen <n>` | stamps notice `<n>` as seen by you |
| `close <n>` | takes notice `<n>` down and archives it with its stamps; only whoever posted it can |
| `archive` | closed notices, newest first (the latest 10, and how many there are in all) |

Each command also has a Japanese word; see [USAGE.md](ext-tools/kairan/USAGE.md).

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
