# Fast way to navigate through directory subfolders #

The newdirectorystream in java is and easy and very performant way to navigate the subfolders.

Also here it shows the filtering abilities together with automatic try/close

```java

final DirectoryStream.Filter<Path> filterCartelle = path -> !path.endsWith(".DS_Store")
        && !path.toString().equals("/full/path")
        && path.toFile().isDirectory();

try (DirectoryStream<Path> folders = Files.newDirectoryStream(cartellaProduttore, filterCartelle)) {
    for (Path subFolder : folders) {
        //do your work with the files
    }
}
```