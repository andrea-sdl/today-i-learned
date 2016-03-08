# Update the last modified date for each file in a folder#

To update the last modified date you can use "touch" on every file

```bash
find . -exec touch  {} \;
```