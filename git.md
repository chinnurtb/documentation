General
=======

Undo last commit                git reset HEAD^
remove file from stage          git reset HEAD FILE
Gitolite View all repos         ssh server info
Show all authors                git log --format='%aN' | sort -u
Show all deleted files          git log --diff-filter=D --summary
Restore deleted file            git checkout <deleting-commit>^ -- <file-path>


Submodules
==========

add submodule                   git submodule add <repo> <path>
update all submodules           git submodule foreach git pull

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

push local branch to server     git push origin newbranch
Delete remote branch            git push origin :oldbranch

History
=======

show history of a file          git log -p filename
checkout specific file only     git checkout hash file/to/restore
