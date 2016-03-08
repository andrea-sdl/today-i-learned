# Rename files in a directory by replacing a text in the filename #

This version of the command replace the "TEXT_TO_SEARCH" with "TEXT_TO_REPLACE" in the file names in the actual folder.
It's nice because it also works on mac/mingw64(windows)

```bash
for f in *; do mv "$f" "${f//TEXT_TO_SEARCH/TEXT_TO_REPLACE}"; done
```