# Example data from step to step 

```
name: stepscheck

on: 
  push:
 
jobs:
  job1:
    runs-on: ubuntu-latest
    steps:
    
      - name: Set color
        id: color-selector
        run: |
          echo $GITHUB_OUTPUT # test
          echo "SELECTED_COLOR=green" >> "$GITHUB_OUTPUT"
      - name: Get color
        env:
          SELECTED_COLOR: ${{ steps.color-selector.outputs.SELECTED_COLOR }}
        run: echo "The selected color is $SELECTED_COLOR"
```
         
