# git checkout (used for branches and files) 

## Checkout (change to) existing branch 

```
git checkout feature/4711
```

### Checkout and create branch 

```
# Only possible once 
git checkout -b feature/4712
```

### Recover deleted file 

```
rm todo.txt 
# get from last from last commit 
git checkout HEAD -- todo.txt 

```
