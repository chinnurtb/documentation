General
=======

Push local branch to another remove branch

    git push origin local_branch:remote_branch

### Undo last commit

    git reset HEAD^

### remove file from stage

    git reset HEAD FILE

### Gitolite View all repos

    ssh server info
### Show all authors

    git log --format='%aN' | sort -u

### Show all deleted files

    git log --diff-filter=D --summary

### Restore deleted file

    git checkout <deleting-commit>^ -- <file-path>
    
### Find unreachable commits with commit message

    git fsck --full --no-reflogs --unreachable --lost-found | awk '{print $3}' | xargs -n 1 git log -n 1 --pretty=oneline
    
Source [Recover deleted branch from git](https://stackoverflow.com/questions/16793637/recover-deleted-branch-git)


Submodules
==========

### add submodule

    git submodule add <repo> <path>

### update all submodules

    git submodule foreach git pull

Remove submodule
----------------

- Delete the relevant line from the .gitmodules file.
- Delete the relevant section from .git/config.
- Run git rm --cached path_to_submodule (no trailing slash).
- Commit and delete the now untracked submodule files.

synchronize svn with git
========================

    git svn
    git svn clone <svn-repo> dir-name


Remote Branches
===============

### push local branch to server

    git push origin newbranch

### Delete remote branch

    git push origin :oldbranch

History
=======

### show history of a file

    git log -p filename

### checkout specific file only

    git checkout hash file/to/restore


# Delete merged branches

http://devblog.springest.com/a-script-to-remove-old-git-branches

locally

```
git branch --merged master | grep -v 'master$' | xargs git branch -d
```

remote

```
git branch -r --merged master | sed 's/ *origin\///' | grep -v 'master$' | xargs -I% git push origin :%
```
