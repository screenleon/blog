# Sync Folder
================================

**Author**: Lien Chen  **Date**: 2020-09-28

* To easy sync two folders with command line, use command below.

Put A folder into b folder
```bash
rsync -avu --delete "/home/user/A" "/home/user/B"
```

Put A folder's files into b folder
```bash
rsync -avu --delete "/home/user/A/" "/home/user/B"
```

Put A folder into b folder exclude nameA folder and nameB folder
```bash
rsync -avu --exclude "nameA" --exclude "nameB" --delete "/home/user/A" "/home/user/B"
```

[reference](https://unix.stackexchange.com/questions/203846/how-to-sync-two-folders-with-command-line-tools)