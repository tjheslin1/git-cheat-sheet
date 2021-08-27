# git-cheat-sheet
No more `git commit -am`

## Resources
- [Git Book](https://git-scm.com/book)
- [Getting more with Git / Alice Bartlett / ffconf 2019](https://www.youtube.com/watch?v=FQ4IdcrOUz0)

## Katas
- [git-katas](https://github.com/eficode-academy/git-katas)

---

```sh
git log -p
```

Show the log with _"patch text"_. Shows the changes in the commits like `git show <sha>`.

---

```sh
git diff --cached
```

Show changes on the _Staging Index_.

```sh
git diff {branch-A} {branch-B}
```

Show changes between branch-A and branch-B.

```sh
git diff {branch-A} {branch-B} -- {file}
```

Show changes of a specific file between branch-A and branch-B.

---

```sh
git fetch --prune
```

Before fetching, remove any remote-tracking references that no longer exist on the remote.
Local branches still need deleting.

---

```sh
git show <sha>
```

Shows the changes in a commit (other objects can be 'shown').
Useful for reviewing the changes made in a _revert_ commit.

---

```sh
git branch -d <branch-name>
```

---

```sh
git add -p
```
Interactively step through changes in the _Working Directory_ to add to the _Staging Index_.

---

```sh
git commit --amend
```

Completely replace the last commit with a new one and it will commit everything that's currently staged.

---

```sh
git checkout -p
```

Interactively step through changes in the _Working Directory_ to discard.

```sh
git checkout {branch} -- {path/to/file}
```

Checkout the specified file from the specified branch.

_Useful for when you want to separate changes in a branch._

---

```sh
git reset
```

Calling `git reset` with no additional arguments moves any changes on the _Staging Index_ back to the _Working Directory_.

`git reset -p` behaves the same as `git add -p` allowing you to choose hunks to reset back to the _Working Directory_.
Nothing happens to the commit history.
`git reset` is the opposite of `git add`.

`git reset --soft <sha>` moves the HEAD to the specified commit. Preserving current changes.

```sh
git reset <sha>
```

Move all changes from any commit after the id you've given it back to the _Working Directory_.
Adding `--hard` will **delete** the contents of the _Working Directory_ and _Staging Index_.
Lost work is only recoverable from the ref log.

---

```sh
git revert <sha>
```

Create a new commit which reverts the changes made in the <sha> commit.

---

```sh
git rebase
```

```
     feature branch                             feature branch                                 feature branch
          |                                          |                                              |
          v                                          v                                              v
    *-*-*-*       after `rebase`               *-*-*-*           afer `merge`                 *-*-*-*
   /              ------------->              /                  ----------->                /      ^
--*-*-*-*-*                        --*-*-*-*-*                                    --*-*-*-*-*       |
          ^                                  ^                                                    master
          |                                  |
        master                             master
```

Rewrites history. Only do this on **local unpublished branches**.
"Rebasing" is changing the base of your branch from one commit to another, making it look as if you had created a branch from a different commit.

---

```sh
git cherry-pick <sha>
```

Apply the change of the specific commit on the top of this branch. Requires the _Working Tree_ to be clean.

---

```sh
git reflog
```

As you’re working, Git silently records what your HEAD is every time you change it.
Each time you commit or change branches, the reflog is updated.

`git log -g` will give the normal log output but for `reflog`.

A good way to recover work is to create a branch at the commit you want to recover.

```sh
git branch recover-branch <sha-to-recover>
```

---

```sh
git clean
```

Remove untracked files from the working tree.

`-n` for dry run.
`-f` to force. Required for default git settings.
`-d` to clear directories.

---

```sh
git push origin {A}:{B}
```

Push the state of of branch A to branch B. Useful for updating a deploy branch.

e.g: `git push origin main:dev`

