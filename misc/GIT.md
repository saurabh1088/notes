#  GIT

## git merge : fast-forward vs no fast-forward

Example :

We have a main branch, from which feature branches are created and merged back to
main branch. Suppose we create a feature branch from main and add few changes and
stage+commit+push those to feature branch.

main
feature_a
    - commit 1
    - commit 2
    - commit 3

Now our changes for feature_a are complete and we want to merge these back to main
branch. There are two ways to do this

- git merge using fast-forward (DEFAULT)
- git merge with no fast-forward

If merged from terminal the usual process is :

1. git checkout main
2. git pull (to make sure we have all changes from main)
3. git merge feature_a

The command (git merge feature_a) used in step no 3 will proceed with merge using
default strategy as fast-forward.

Below screenshot shows how branch revision history appears in Fork when fast forward
strategy is used. Here fast forward simply shows revisions added to main branch.
Nowhere it can be figured out where feature began and where it ended and where merge
was done. It also will be difficult if one were to revert the feature. Only way to
revert the feature would be to figure out all commits and revert those.

![git merge using fast forward](/resources/git-merge-fast-forward.png "git merge using fast forward")


Below screenshot shows how branch revision history appears in Fork when fast forward
strategy is NOT used. In this case it's clearly visualised that a branch was created,
then some commits were added and finally it was merged. There is a merge commit as
well. This merge commmit can be reverted to revert the feature from main branch.

![git merge not using fast forward](/resources/git-merge-no-ff.png "git merge not using fast forward")
