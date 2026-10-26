# kairan (回覧板)

In Japan a *kairanban* is a notice board passed from house to house, where each
reader stamps it before handing it on; a kairan member does that for the team.
Send it a command; it replies.
Each command has a Japanese word and an English alias, and the reply comes in
the language of the word you used.

| 送るもの | English | what happens |
|---|---|---|
| `回覧 <本文>` | `post <text>` | puts up a notice and replies with its number |
| `一覧` | `list` | open notices, who posted each, and who has seen it |
| `見た <番号>` | `seen <n>` | stamps notice `<n>` as seen by you |
| `おわり <番号>` | `close <n>` | takes notice `<n>` down and archives it with its stamps; only whoever posted it can |
| `過去` | `archive` | closed notices, newest first (the latest 10, and how many there are in all) |

Anything else gets the usage line back. The board is per member and per team.
A notice stays up until its poster closes it; a closed notice leaves `list` but
is kept, stamps and all, for `archive`. Numbers are never reused.

## 日本語

kairan はチームの回覧板です。コマンドを送ると返事が来ます。

- `回覧 <本文>`: 回覧を 1 つ出します。返事に番号が付きます。
- `一覧`: まだ出ている回覧と、出した人、確認印を押した人を返します。
- `見た <番号>`: その回覧に自分の確認印を押します。
- `おわり <番号>`: その回覧を閉じます。閉じられるのは出した人だけです。閉じた回覧は確認印ごと残り、「一覧」には出なくなります。
- `過去`: 閉じた回覧を新しい順に返します(直近 10 件と、全部で何件あるか)。

回覧の番号は、閉じたあとも使い回しません。

英語の別名(`post` / `list` / `seen` / `close` / `archive`)でも同じように動き、返事は英語になります。
