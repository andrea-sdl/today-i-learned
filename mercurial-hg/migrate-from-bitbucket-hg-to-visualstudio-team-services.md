# Migrate a mercurial HG repo from Bitbucket to VisualStudio TeamService

This is a super-easy script that helps with the repeating task of migration of the repo.
It uses fast-export.


## Setup
```bash
git clone https://github.com/frej/fast-export.git
```

## Quick & Dirty script

This scripts acce

```bash
hg clone https://bitbucket.org/$1

mkdir $1.git
cd $1.git
git init
../fast-export/hg-fast-export.sh -r ../$1/
git remote add origin $2
git push -u origin --all

cd..
rm -rf $1
rm -rf $1.git
```

## usage
```bash
sh migrate-hg-repo.sh hg-repo-name http://xxx.visualstudio.com/_git/ProjectName
```
