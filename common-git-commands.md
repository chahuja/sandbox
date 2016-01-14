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

# TO TRY
* git diff
* git push
* git tag
* what to do before you start of working on your own branch
  * bring your local up to date before starting anything new
* revert back to old stuff
* delete a file out of the git repository, but keep it locally
* stashing
* how to manually merge?
* gitignore
* rebasing
* git mergetools
* --dry-run
