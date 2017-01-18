# Git Daily Workflow
An example of the daily git workflow for the DSI class.

## Morning

tl;dr version

1. Fork zipfian repo for the day
    * in browser
2. Clone repo onto local machine
    * `git clone <repo url>`
3. Create individual and pair branches
    * `git checkout -b <individual branch name>`
    * `git checkout -b <pair branch name>`
4. Double check you are on individual branch before starting morning exercise
    * `git branch`
    * (if not on individual branch) `git checkout <individual branch name>`
5. Do work, follow ABC (Always Be Committing)
    * `git status` (check for your modifications)
    * `git add <file you changed>` (repeat for all files)
    * `git commit -m <commit message>`
6. Push morning work to remote repo
    * `git push <remote> <local individual branch name>:<remote individual branch name>`
        * The name for your remote will be `origin` by default

## Afternoon

tl;dr version

### Before Starting Work (Both Partners Do This)
1. Check for local modifications that need to be committed, commit them
    * `git status` (check for your modifications)
    * `git add <file you changed>` (repeat for all files)
    * `git commit -m <commit message>`
2. Checkout to your pair branch
    * `git checkout <pair branch name>`
3. Double check you are on pair branch before starting pair exercise
    * `git branch`
    * (if not on pair branch) `git checkout <pair branch name>`
4. Add each other's remotes to your local repo
    * `git remote add <alias> <your partner's repo url>`

### First Driver
**Assumes you did all steps in Before Starting Work**

1. Do work, follow ABC (Always Be Committing)
    * `git status` (check for your modifications)
    * `git add <file you changed>` (repeat for all files)
    * `git commit -m <commit message>`
2. Push initial work to ***your*** remote repo
    * `git push <your remote> <your local pair branch name>:<your remote pair branch name>`
        * The name for ***your*** remote will be `origin` by default

### Second Driver
**Assumes you did all steps in Before Starting Work**

1. Pull your ***partners*** work onto your local machine
    * `git pull <partners remote alias> <partners pair branch name>`
    * Merges your partners changes onto your *currently checked out branch*
2. Do work, follow ABC (Always Be Committing)
    * `git status` (check for your modifications)
    * `git add <file you changed>` (repeat for all files)
    * `git commit -m <commit message>`
3. Push the new changes/commits to ***your*** remote repo
    * `git push <your remote> <your local pair branch name>:<your remote pair branch name>`

### Repeat Second Driver Steps to infinity (or 'til you go home)
