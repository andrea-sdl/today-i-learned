# How to search with find for a specific depth and excluding a folder #

```bash
find /srv/folder/ -maxdepth 3  -not -path "/srv/folder/FolderTOExclude/*" -name *.tgz
```