Common GIT commands
===================

Pulling vs Fetching
-------------------


Retrieves the changes pushed on the remote repository (i.e. `origin/branch_name`) and keeps it locally without changing the local directory. The branches can be merged by using the merge command.

```sh
git fetch
```

If you want to pull changes on chahuja from `orgin/master`

```sh
git fetch
git checkout chahuja
git merge origin/master
```

Pulling fetches the changes and merges them onto the local branches. There maybe conflicts, and one may have to manually sort them out.

```sh
git pull
```

**Note:** Currently `pull` fetches and merges all the branches. In future version, `pull` will just merge the current branch.

Merging
-------

```sh
git checkout master
git merge origin/branch-to-merged
```

There might be conflicts while merging. Use **merge tool** (my favourite is `meld`) to resolve the disputes.

```sh
git mergetool --tool=your-choice-of-mergetool
```

After merging the `master` branch needs a commit.

```sh
git commit -m 'Merged branch-to-be-merged to master'
```

**Note:** The changes will occur in the `master` branch.

Tagging
-------

Tag is basically a human friendly pointer to commit in any branch.

To see all the tags

```sh
git tag
```

To tag the current commit

```sh
git tag -a <tag-name> -m "annotation"
```

Information about a given tag

```sh
git show <tag-name>
```

Lightweight tag (does not store any information apart from the commit checksum)

```sh
git tag <tag-name>
```

Tag a commit which exists in history

```sh
git tag -a <tag-name> <commit-address>
```

Pushing the tags to remote

```sh
git push origin --tags
```

Checking out a tag in a new branch

```sh
git checkout -b <new-branch> <tag-name>
```

Stashing
--------

Let say you are working on some files and want to `checkout` previous versions of the project or any other `branch`. One way is to `commit` the current changes and then `checkout` whatever part of the repository you want to. If you don't want to commit these changes, you can `stash` them. `Stashes` are basically local changes which are generally not ready for commit.

To stash the local changes

```sh
git stash
```
Then you can checkout other branches and even work on them.

You can check the list of local stashes using
```sh
$ git stash list
stash@{0}: WIP on master: 049d078 added the index file
stash@{1}: WIP on master: c264051 Revert "added file_size"
stash@{2}: WIP on master: 21d80a5 added number to log 
```

To revert back to the latest stash, use
```sh
git stash pop
```

To revert back to a particular stash number, use
```sh
git stash apply [stash@{1}]
```

Generally the `stash` is reapplied to the `branch/commit` where it was originally stashed, but it may be applied to another `branch`. There maybe `merge` conflicts, which can be resolved using any `mergetool`.

If you would like to create a `branch` out of a given `stash`, use
```sh
git stash branch <branch-name>
```

To `drop` (remove a `stash`) use
```sh
git stash drop <stash-name>
```

To un-apply **(stash -> do-some-work -> remove the changes caused by applying stash)** a stash, use

```sh
git stash show -p <stash-name> | git apply -R
```

**Note:** If you don't specify a stash, git assumes the latest stash.

# TO TRY
* git diff
* git push
* git tag
* what to do before you start of working on your own branch
  * bring your local up to date before starting anything new
* revert back to old stuff
* delete a file out of the git repository, but keep it locally
* how to manually merge?
* gitignore
* rebasing
* git mergetools
* --dry-run
