# git config

## List the result (last entry is being used) 

```
git config --list
```

## How to delete an entry from config 

```
# Important: Find exact level, where it was added --global, --system, --local 
# test before
# should contain this entry 
git config --global --list 

git config --unset --global alias.log
```

![image](https://github.com/user-attachments/assets/8c3270d0-12a1-4e41-ba85-21a145a2914c)
