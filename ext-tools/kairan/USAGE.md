# kairan

In Japan a *kairanban* is a notice board passed from house to house, where each
reader stamps it before handing it on; a kairan member does that for the team.
Send it a command; it replies.

| command | what happens |
|---|---|
| `post <text>` | puts up a notice and replies with its number |
| `list` | open notices, who posted each, and who has seen it |
| `seen <n>` | stamps notice `<n>` as seen by you |
| `close <n>` | takes notice `<n>` down and archives it with its stamps; only whoever posted it can |
| `archive` | closed notices, newest first (the latest 10, and how many there are in all) |

Anything else gets the usage line back. The board is per member and per team.
A notice stays up until its poster closes it; a closed notice leaves `list` but
is kept, stamps and all, for `archive`. Numbers are never reused.

Each command also has a Japanese word, and the reply comes in the language of
the word you used; see [USAGE.ja.md](USAGE.ja.md). The words and replies for
each language are in [messages/](messages/).
