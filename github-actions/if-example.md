# If example (using special var)


```
steps:
 - name: Check for outdated packages
   id: vars
   run: |
     OUTDATED=$(npm outdated) || true
     
     echo "OUTDATED='$OUTDATED'" >> $GITHUB_OUTPUT
      
 - name: Upgrade
   if: ${{ steps.vars.outputs.OUTDATED != '' }}
   run: npm upgrade
```
