# General 

## Komponenten 

  * actions 
  * workflows 
  * jobs
  * steps
  * events 

## Actions 

  * What can we do ? 
  * i.d.R läuft jede Action in einem docker-container (aber auch möglich: node-js (12), combined)

## Workflows 

  * ENV (Umgebungsvariablen, Variablen) 
  * Jobs -> Steps 
  * Events

## Events 

  * Events sind Ereignisse die stattfinden (man könnte auch sagen -> Trigger)
  * Ref: https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows

### Beispiele für Typen 

  * pull_request
    * if no activity types are specified, the workflow runs when a pull request is opened or reopened or when the head branch of the pull request is updated
   
