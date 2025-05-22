# gitops-Training  

## Agenda 

  1. Git - Grundlagen
     * [Grundlagen](https://schulung.t3isp.de/documents/pdfs/git/git-training.pdf)
 
  1. Git - Commands (with tipps & tricks) 
     * [git add + Tipps & Tricks](add.md)
     * [git commit](commit.md)
     * [git log](log.md)
     * [git config](config.md) 
     * [git show](show.md)
     * [Needed commands for starters](started-commands.md)
     * [git branch](branch.md)
     * [git checkout - used for branches and files](checkout.md)
     * [git merge](merge.md)
     * [git tag](tag.md)
     * [git rm](rm.md)

  1. Git - mergetool
     * [mergetool auf der Kommandozeile verwenden](mergetools.md)
      
  1. Git - Advanced Commands 
     * [git reset - Back in Time](reset.md)   

  1. Git - Tipps & tricks 
     * [Beautified log](beautify-log.md)
     * [Change already committed files and message](commit-amend.md) 
   
  1. Git - Exercises 
     * [merge feature/4712 - conflict](merge-conflict.md)

  1. Git - Snippets 
     * [publish lokal repo to server - bitbucket](local-public.md)
     * [failure-on-push-fix](failure-push.md)
     * [failure-on-push-with-conflict](failure-push-conflict.md)
        
  1. Git - Documentation 
     * [GIT Pdf](http://schulung.t3isp.de/documents/pdfs/git/git-training.pdf) 
     * [GIT Book EN](https://git-scm.com/book/en/v2)
     * [GIT Book DE](https://git-scm.com/book/de/v2)

  1. github actions - Einführung
     * [Was ist ci/cd ?](/ci-cd/overview.md)
     * [General overview](/github-actions/general.md)

  1. github actions - Praxis I
     * [Übung 1: Den 1. Workflow erstellen](/github-actions/simple-workflow.md)
     * [Übung 2: Das repo auschecken](/github-actions/examples/02-checkout-repo.md)

  1. github actions - Praxis II (Arbeiten mit Outputs)
     * [Outputs zwischen jobs](github-actions/examples/06-tag-auto-erstellung-und-setzen.md)

  1. github actions      
     * [Create dependant jobs](/github-actions/dependant-jobs.md)
     * [Create custom composite action](/github-actions/create-custom-action-composite.md)
     * [Create custom docker action](/github-actions/create-custom-action-docker.md)
     * [If example](/github-actions/if-example.md)
     * [Work with artefacts](/github-actions/work-with-artefacts.md)
     * [Create digitalocean-kubernetes.md](/github-actions/digitalocean-kubernetes.md) 
     * [Deploy to server with ssh](/github-actions/use-cases/deploy_ssh.md)

  1. github actions - passing data 
     * [passing data from step to step](github-actions/steps-data.md)

  1. github actions - events (IMHO trigger)
     * [Events](/github-actions/events.md)
     * [Required Status Checks](/github-actions/required-status-checks.md)
     
  1. github actions - examples 
     * [Simple Workflow Test](/github-actions/examples/01-workflow-test.md)
     * [Push to repo](/github-actions/examples/03-push-to-repo.md)
     * [Write secret to file and push to repo](github-actions/examples/04-secret-and-push-to-repo.md)
    
  1. github actions - use case
     * [Check lang-file before merging and disallow merging](github-actions/use-cases/check-langfile.md)
     * [Run script from repo](github-actions/use-cases/run-script-from-repo.sh)
     * [Deploy with ansbile using ssh](github-actions/use-cases/deploy-ansible.md)

  1. github - actions - docker
     * [Was darf in das Dockerfile rein](https://docs.github.com/de/actions/creating-actions/dockerfile-support-for-github-actions)
      
  1. github - actions GITHUB_OUTPUT - GITHUB_SUMMARY
     * [Write to summary page from within jobs](github-actions/write_to_summary.md) 

  1. github - actions - documentations
     * [github actions repo](https://github.com/actions/checkout)
     * [github actions marketplace](https://github.com/marketplace?category=&query=&type=actions&verification=)
     * [default environment variables](https://docs.github.com/en/actions/learn-github-actions/variables#default-environment-variables)
     * [Documentation github actions](https://docs.github.com/en/actions)

  1. Docker 
     * [Install docker on Ubuntu](/docker/install-ubuntu.md)
     * [Important commands](/docker/wichtigste-befehle.md)  
       
## Teilnenmerfragen 

  1. Git - Server
     * [Git-Server auf Synology NAS installieren](/git-server/git-server-auf-synology.md) 

## Extras - github actions 

  1. github - actions - runner 
     * [Add a self-host runner](/github-actions/add-runner.md)

## Extras - git 

  1. Git - Best practices 
     * [Die 5 goldenenen Regeln - nix kaputtmachen so gehts](5-goldene-regeln.md) 
     * [Best practices](bp.md)
  1. Git - Advanced Commands
      * [git reflog](reflog.md)
    
## Backlog  
     
  1. Git - Installation (GIT) 
     * [GIT auf Ubuntu/Debian installieren](installation-ubuntu-debian.md)
     * [GIT unter Windows installieren](https://git-scm.com/download/win)
  
  1. Git - Tipps & Tricks
     * [Best practice - Delete origin,tracking and local branch after pull request/merge request](best-practice-delete-branch.md)
     * [Change language to german - Linux](linux-english.md)
     * [Reference tree without sha-1](tree-no-sha.md)
     * [Always do pull --rebase for master branch](master-pull-rebase.md)

  1. Git - github pages
     * [Github Pages](/github/pages.md)
    
  1. Git - Documentation (Tools)
     * [Third Party Tools](tooling.md)   

  1. Kubernetes 
     * [Installation micro8ks (Ubuntu)](/kubernetes/installation-micro8ks-ubuntu.md)
    
