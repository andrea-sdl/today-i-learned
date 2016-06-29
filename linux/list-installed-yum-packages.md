# List installed yum packages #

This seems a trivial question but the goal is to have a list of packages to be installed elsewhere.
Used awk so I take only the package name and leave out the rest

```sh
yum list installed | grep php | awk '{ print $1 }'
```