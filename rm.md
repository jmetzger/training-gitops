# git rm

## Delete file in working directory, staging and repo 

```
git rm filename.txt 
```

## Deleting files only from repo (not locally) 

```
git rm --cached filename.txt
# Please be sure to commit the change afterwards
# to reflect the changes in repo 
git commit -am "my filename.txt was deleted"

```
