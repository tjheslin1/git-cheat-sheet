# git-cheat-sheet
No more git commit -am

## Resources
- [Getting more with Git / Alice Bartlett / ffconf 2019](https://www.youtube.com/watch?v=FQ4IdcrOUz0)

## Katas
- [git-katas](https://github.com/eficode-academy/git-katas)

```sh
git log -p
```

Show the log with _"patch text"_. Shows the changes in the commits like `git show <sha>`.

```sh
git fetch --prune
```

Before fetching, remove any remote-tracking references that no longer exist on the remote.
Local branches still need deleting.

```sh
git show <sha>
```

Shows the changes in a commit (other objects can be 'shown').
Useful for reviewing the changes made in a _revert_ commit.

```sh
git branch -d <branch-name>
```

```sh
git add --patch
```

```sh
git commit --amend
```

Completely replace the last commit with a new one and it will commit everything that's currently staged.

```sh
git reset
```

Calling `git reset` wih no additional arguments moves any changes on the _Staging Index_ back to the _Working Directory_.
Nothing happens to the commit history.
`git reset` is the opposite of `git add`.

```sh
git reset <sha>
```

Move all changes from any commit after the id you've given it back to the _Working Directory_.
Adding `--hard` will **delete** the contents of the _Working Directory_ and _Staging Index_.
Lost work is only recoverable from the ref log.

```sh
git revert <sha>
```

Create a new commit which reverts the changes made in the <sha> commit.

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
