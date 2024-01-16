# Events 

```
9. events 

9.1. Nur triggern, wenn bestimmte Dateien geändert wurden

on:
  pull_request:
    paths:
      - '**.js'


9.2 Branches ausschliessen

on:
  push:
    # Sequence of patterns matched against refs/heads
    branches-ignore:    
      - 'mona/octocat'
      - 'releases/**-alpha'
    # Sequence of patterns matched against refs/tags
    tags-ignore:        
      - v2
      - v1.*
```

## Refs:

  * https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#pull_request
  * https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#push
 
