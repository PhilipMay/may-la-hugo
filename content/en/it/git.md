---
title: GIT
---

## Links
- Pro Git book: <https://git-scm.com/book/en/>
- Ry’s Git Tutorial: <https://www.smashwords.com/books/view/498426>

## Basics
- show log
  - `git log`
  - show only `n` messages: `git log -n`
  - one line format: `git log --pretty=oneline`
  - one line format and show only `n` messages: `git log --pretty=oneline -n`
- initial checkout: `git clone <remote_repo_url>`
- clone a specific branch: `git clone -b <branch_name> <remote_repo_url>`
- rename local master branch to main: `git branch -m master main`

## Ignore Things
- put directory or file into `.gitignore`
- for private ignore put it into `.git/info/exclude`
- good Python ignore temnplate: https://github.com/github/gitignore/blob/main/Python.gitignore

## Branch handling
- create and change Branch: `git checkout -b <new_branch_name>`
- show all branches: `git branch -a`
- delete branch
  - delete a local branch: `git branch -d <local_branch>`
  - delete a remote branch `git push origin --delete <remote_branch>`

## Advanced
- change upstream url: `git remote set-url origin new.git.url/here` - see [here](https://stackoverflow.com/a/2432799)
- add remote after `git init`
  - add remote: `git remote add origin <git_url>`
  - set upstream: `git branch --set-upstream-to=origin/main main`

## Empty Commit to trigger CI
``` bash
git commit --allow-empty -m "empty commit to trigger CI"
git push
```

## Stash Usage
- stash changes: `git stash`
- list stashed changes: `git stash list`
  - example:
``` bash
git stash list
# output:
stash@{0}: WIP on master: 049d078 Create index file
stash@{1}: WIP on master: c264051 Revert "Add file_size"
stash@{2}: WIP on master: 21d80a5 Add number to log
```
- reapply stash
  - apply newest (last) stash: `git stash apply`
  - apply selected stash: `git stash apply <number>`


## Special Commands
- show history of last ref updates: `git reflog`
- list tracked repositories: `git remote -v`
- signoff last (5) commits: `git rebase --signoff HEAD~5` - see https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---signoff

## Undo things
- unstage files staged with git add: `git reset`
- revert local uncommitted changes
  - should be executed in repo root: `git checkout .`
  - longer to type, but works from any subdirectory: `git reset --hard HEAD`
- revert pushed commit:
```bash
git reset --hard '<commit_id>'
git clean -f -d
git push -f
```
- change last commit message: `git commit --amend`

## Work with a forked Repository
- add original repository (has to be done once): `git remote add upstream <original_repository_url>`
- fetch changes form forked repository:
```bash
# fetch changes
git fetch upstream

# change to locale branch
git checkout master
# or
git checkout main

# merge upstream
git merge upstream/master
# or
git merge upstream/main

# push changes
git push
```

Rebase changes from forked repository into development branch:
```bash
git checkout <dev_branch>
git rebase upstream/master
# or
git rebase upstream/main
```

Rebase into development branch:
```bash
git checkout <dev_branch>
git rebase master
# or
git rebase main

# abort
git rebase --abort
```

Conflicts look like this:
```text
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
```

## Squash: Clean dirty commit History
To clean a dirty commit history (before doing a pull request) you can do
a squash.

Warning: Do not rebase commits that exist outside of your repository. At
least do not rebase branches where others are working on.

Lets say you want to fix up the last 5 commits you do this:
```bash
git rebase -i HEAD~5
```

Change first commit:
```bash
git rebase -i --root
```

Then you get an editor window where you have to do the changes. Here you
can rename the top commit by writing "r" (for reword) and change the
commit text. If you want to discard all other commits you write "f" (for
fixup) infront of them. Now you save the file and the GIT magic is
happening.

Here is an overview of all options:
```text
- p, pick = use commit
- r, reword = use commit, but edit the commit message
- e, edit = use commit, but stop for amending
- s, squash = use commit, but meld into previous commit
- f, fixup = like “squash”, but discard this commit’s log message
- x, exec = run command (the rest of the line) using shell
- d, drop = remove commit
```

If something bad happens after saving where you have to fix up something
first, you can continue the rebase with: `git rebase --continue`

When everyhing is ok you have to do a forced push: `git push -f`

If you have already done a pull request (on GitHub) this squash still
works afterwards. The “dirty” commit history of the PR will also be
changed.

## Configuration
- always rebase on pull (is is best practice): ` git config --global pull.rebase true `
- remember username and password: `git config --global credential.helper store`
- set username
  - local (for single repository): `git config user.name "<username>"`
  - global: `git config --global user.name "<username>"`
- set mail
  - local: `git config user.email "<mail>"`
  - global: `git config --global user.email "<mail>"`
- change editor to nano (global): `git config --global core.editor "nano"`
- global ignore Settings
  - create `~/.gitignore_global` file with ignore settings
  - execute `git config --global core.excludesfile ~/.gitignore_global`
  - also see: <https://jayeshkawli.ghost.io/using-global-gitignore-on-mac/>
- set VSCode as editor: `git config --global core.editor "code --wait"`

## Mac specific
- system config file is here: `/Library/Developer/CommandLineTools/usr/share/git-core/gitconfig`
- credentials helper `osxkeychain` is enabled by default (see system config)
- add `.DS_Store` to global ignore settings (see above)
