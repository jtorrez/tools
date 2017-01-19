# Git Daily Workflow
An example of the daily git workflow for the DSI class.

# tl;dr Version

## Morning

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
        * The name for your remote will be `origin` by default.

## Afternoon

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
        * The name for ***your*** remote will be `origin` by default.

### Second Driver
**Assumes you did all steps in Before Starting Work**

1. Pull your ***partner's*** work onto your local machine
    * `git pull <partner's remote alias> <partner's pair branch name>`
        * Merges your partner's changes onto your *currently checked out branch.*
2. Do work, follow ABC (Always Be Committing)
    * `git status` (check for your modifications)
    * `git add <file you changed>` (repeat for all files)
    * `git commit -m <commit message>`
3. Push the new changes/commits to ***your*** remote repo
    * `git push <your remote> <your local pair branch name>:<your remote pair branch name>`

### Repeat Second Driver Steps to infinity (or 'til you go home)

# All the Dirty Details Version

## Morning

1. Fork zipfian repo for the day
    * in browser
        * Forking is just a fancy way of saying "make a copy of this repo."
        * Necessary so you can push changes to your own remote repo, sorry we can't let you push to the Zipfian repos...
2. Clone repo onto local machine
    * `git clone <repo url>`
        * This copies the state of your remote repo onto your local machine and sets up a remote, `origin` by default, to pull or push changes.
3. Create individual and pair branches
    * `git checkout -b <individual branch name>`
    * `git checkout -b <pair branch name>`
        * We create both branches ***immdediately*** after cloning the repo onto our computer for a few reasons:
            1. Keep the `master` branch clean. The `master` branch will point to the commit that represents the same state as the original Zipfian repo.
            2. Keep *your* work completely separate from your partner's work to avoid merge conflicts. The `individual` branch will contain only your morning work. The `pair` branch will contain only partner work.
            3. Make the creation of the `pair` branch painless. If you wait to create the `pair` branch until the afternoon, you'll have to first `git checkout` to the commit that represents the clean Zipfian repo (if you're following the steps, this will be your `master` branch), then create the branch from that commit. Your partner will get your `individual` branch changes if you don't remember to do this and you'll have the joy of dealing with merge conflicts.
        * `git checkout -b <branch name>` is shorthand for two separate commands: `git branch <branch name>` followed by `git checkout <branch name>`
        * You can think of this command as saying "Make a new branch, then go point to it and track changes from there on."
        * `git checkout` tells your `HEAD` which commit it should point to. Usually you have it point to a branch, but you can technically have it point to any commit in your tree (or commits in remotes you are tracking).

4. Double check you are on individual branch before starting morning exercise
    * `git branch`
        * This will also display all the branches in your commit tree. The asterisk is next to the one you are currently checked out on.
    * (if not on individual branch) `git checkout <individual branch name>`
        * Remember, this is just telling git where it should point to track changes.
5. Do work, follow ABC (Always Be Committing)
    * `git status` (check for your modifications)
        * You should be running this before ***and*** after you add files to ensure you are staging the changes you think you are.
    * `git add <file you changed>` (repeat for all files)
        * `git add .` is the shorthand way to add all changes to your index for commit. It is best not to do this, especially if you haven't set up a proper `.gitignore` file, but it is especially poor form when you haven't run `git status` first.
    * `git commit -m <commit message>`
        * Make your commit message helpful. `changed some stuff` doesn't help anyone. Remember, be kind to future you, make your commits and docs useful.
6. Push morning work to remote repo
    * `git push <remote> <local individual branch name>:<remote individual branch name>`
        * The name for your remote will be `origin` by default.
        * The `<local branch>:<remote branch>` notation allows you to be explicit about where you are sending commits. If the `<remote branch>` doesn't exist, git will dynamically create it for you.

## Afternoon

### Before Starting Work (Both Partners Do This)

1. Check for local modifications that need to be committed, commit them
    * `git status` (check for your modifications)
    * `git add <file you changed>` (repeat for all files)
    * `git commit -m <commit message>`
2. Checkout to your pair branch
    * `git checkout <pair branch name>`
    * If you didn't create a `pair` branch in the morning, you have to do a few extra things.
        1. Checkout to the commit that represents the clean Zipfian repo, if you are following this guide that should be `git checkout master`
        2. Create your `pair` branch using `git checkout -b pair`
3. Double check you are on pair branch before starting pair exercise
    * `git branch`
    * (if not on pair branch) `git checkout <pair branch name>`
4. Add each other's remotes to your local repo
    * `git remote add <alias> <your partner's repo url>`
        * This step can be done at any time before your first pull, but it is easier to get all the set up out of the way at the beginning of the exercise.
        * You don't have to specify an alias, but if you choose not to, every time you want to pull from a remote you'll have to use the full remote url.


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

1. Pull your ***partner's*** work onto your local machine
    * `git pull <partner's remote alias> <partner's pair branch name>`
        * Merges your partner's changes onto your *currently checked out branch*
        * git pull is shorthand for two separate commands: `git fetch <alias> <branch>` followed by `git merge`
        * `git fetch` downloads all the commits from the remote repo to your local repo and updates where your remote branch points. It doesn't change anything about your local branches. Running `git fetch` instead of `git pull` gives you flexibility to choose how to incorporate those changes (`git rebase` or other fancy git things) instead of being forced to use `git merge`.
2. Do work, follow ABC (Always Be Committing)
    * `git status` (check for your modifications)
    * `git add <file you changed>` (repeat for all files)
    * `git commit -m <commit message>`
3. Push the new changes/commits to ***your*** remote repo
    * `git push <your remote> <your local pair branch name>:<your remote pair branch name>`

### Repeat Second Driver Steps to infinity (or 'til you go home)
