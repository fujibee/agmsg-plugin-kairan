# kairan setup

Read this when `join <team> <name> ext-tool --tool kairan` stops because no
member config exists yet. kairan has no settings and no secrets, so there is
nothing to ask the user beyond the member name (`kairan` is a good default).

`<skill-root>` is the agmsg install this file sits under (it is in
`<skill-root>/plugins/sources/github/.../ext-tools/kairan/SETUP.md`);
`ext-tool.sh` and `join.sh` are in `<skill-root>/scripts/`.

1. Save the member config:

   ```
   bash <skill-root>/scripts/ext-tool.sh setup <team> <name> kairan save
   ```

2. Join:

   ```
   bash <skill-root>/scripts/join.sh <team> <name> ext-tool --tool kairan
   ```

The board is one file next to the member config,
`<skill-root>/ext-tools/<team>/<name>.kairan.json`, created by the first
message. It never touches the message database.
