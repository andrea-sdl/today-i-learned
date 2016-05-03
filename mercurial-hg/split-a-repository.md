# Split an HG repository in two and keeping the history #

## Activate the hg convert extension  ##

Add the convert extension to the .hgrc file
```
[extensions]
hgext.convert=
```

## Create the filemap ##

The filemap is needed because it tells hg convert which are the _interesting_ dirs/files that you want to move or rename.

```
# Comment
include path/to/file
exclude path/to/file
rename from/file to/file
```

Beware that filemap uses POSIX filenames and doesn't want a starting slash.
Also the rename is very useful because it allows you to have a new repo structure


## Convert ##

```bash
hg convert -s hg -d hg --filemap mymapfile oldRepo freshRepo
```

This will copy the new files into the new freshRepo while keeping the history.
It doesn't remove the files in the old repo.

## Update the repo ##

```bash
hg update 
```
