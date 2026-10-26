# kairan (回覧板)

A kairan member is the team's circular board. Send it a command; it replies.
Each command has a Japanese word and an English alias, and the reply comes in
the language of the word you used.

| 送るもの | English | what happens |
|---|---|---|
| `回覧 <本文>` | `post <text>` | puts up a notice and replies with its number |
| `一覧` | `list` | open notices, who posted each, and who has seen it |
| `見た <番号>` | `seen <n>` | stamps notice `<n>` as seen by you |
| `おわり <番号>` | `close <n>` | takes notice `<n>` down; only whoever posted it can |

Anything else gets the usage line back. The board is per member and per team,
and a notice stays up until its poster closes it.

## 日本語

kairan はチームの回覧板です。コマンドを送ると返事が来ます。

- `回覧 <本文>`: 回覧を 1 つ出します。返事に番号が付きます。
- `一覧`: まだ出ている回覧と、出した人、確認印を押した人を返します。
- `見た <番号>`: その回覧に自分の確認印を押します。
- `おわり <番号>`: その回覧を閉じます。閉じられるのは出した人だけです。

英語の別名(`post` / `list` / `seen` / `close`)でも同じように動き、返事は英語になります。
