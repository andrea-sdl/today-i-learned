#Maximum call stack exceeded when installing node modules in homestead on a win10#

The first install of node modules might fail on windows because they can't symlink correctly

To fix it I executed these commands (yes, one is executed twice because the first will crash)

```
npm install --no-bin-links
npm install --no-bin-links
npm rebuild node-sass --no-bin-links
```

