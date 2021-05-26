

git it together: earlybird hurdles
===

## Oh, No!, I really don't want git copying irrelevant OS files to my repo. How can I prevent that?

```bash
> cat .gitignore

# ref: https://gist.github.com/octocat/9257657 #

.gitignore

my-secret-credentials/*

tide/*

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip
 
# Logs and databases #
######################
*.log
*.sql
*.sqlite
 
# OS generated files #
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

```


A .gitignore text file in the repo root directory tells git which files not to publish to github. See also https://docs.github.com/en/github/getting-started-with-github/getting-started-with-git/ignoring-files#configuring-ignored-files-for-all-repositories-on-your-computer 


## Oh No! I staged a file that I don't want associated with the pending commit. How can I undo that?

```bash


$ git reset HEAD -- <file>


```

Its a good idea to try and collect changes associated with specific improvements or bug fixes into discrete commits. Its a housekeeping thing. Please ref: https://stackoverflow.com/questions/1505948/how-do-i-remove-a-single-file-from-the-staging-area-undo-git-add




## Oh No! The National Weather Service might be really mad that my API keys are being published in the clear. Pushing my secret credentials for a while now is not cool. I've updated my .gitignore , but how do I erase the record of the file completely from the repo?

This non-trivial exercise is best described here: https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository .

The sledgehammer approach would be to 1) update your .gitignore , 2) delete and re-create the github repo , 3) delete the local repo ( $ rm -r .git ) , 4) re-create the local repo and push it the empty github repo. This solution erases all record of previous commits (if you care).



## Bummer! I just changed the wrong local file. No way I'm going to push that to the repo, and I really want to recover the previous version.

```bash

# first, with your editor, 'close' the file

$ git restore myCode.R


```

Luckily, git can replace the local copy (that you mistakenly changed) with a copy of the file from the last commit. git recovers this from the *local* repo represented in the .git directory. It does not have to touch the remote github repo. Note that all changes made after the last commit will be lost! Please see: http://git-scm.com/book/en/v2/Git-Basics-Undoing-Things 





