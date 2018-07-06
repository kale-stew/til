# Fixing Mistakes in Git

I've made too many mistakes to count using Git both at work and for my personal projects. Today, I finally learned how to rewrite history and save myself the shame of poorly-worded commits and embarrassing bug fixes.

### Undoing the last commit

Ever commit something and realize you're working on the wrong branch? You can still save yourself! The following command<sup>[1](#resource1)</sup> rolls back that commit and unstages your changes so you can modify them, create a new branch, and move on with your day.

```sh
git reset HEAD~
```

If you knew you never wanted to see your committed changes again, it's even easier:

```sh
git reset --hard

# go the extra mile and delete all untracked or ignored files
git clean -ndx
```

... but know this is risky and will get rid of a lot at once.

### Saving Uncommitted Changes

From one branch, it's easy to save uncommitted changes to a new one, given you want to pull _everything_ in progress from your current branch to the new one.

```sh
git checkout -b new-branch
git commit -m "Fixed the broken thing"
```

It's also easy to stash changes to be applied or dropped at a later time.

```sh
# stage & stash all working changes
git add .
git stash save "Message to future self"

# apply, commit, and clean up the latest stash
git stash apply
git commit -m "Updated the thing"
git stash drop
```

If you have a number of stashed commits to navigate, you can do it with ease

```sh
# check out all of your stashed commits on the current branch
git stash list

# apply a specific stash
git stash apply 0
```

### Fixing Specific Commits

It's easy to edit the message or add more files to the last commit on the current branch

```sh
git commit --amend
```

But what if you want to edit a commit further back in the git history?

```sh
# find the specific commit you want to edit using
git log

# copy the hash and paste it in place of $HASH
git rebase -i $HASH^
```

In the vim prompt that follows, navigate to the beginning of the line containing the commit you want to edit, type `i`, delete `pick`, replace with `e` (or the alternative action you would like to make to this commit), `ESC`, `:wq`.

Make your edits, and proceed with your rebase:

```sh
git add .
git commit --amend
```

`ESC` + `:wq` to exit the vim prompt once more.

```sh
git rebase --continue

# force the update to reset the branch HEAD
git push -u origin +current-branch
```

## In Conclusion

There are hundreds of other git commands worth knowing that will solve your problems and improve your workflow. These commands have done wonders for me, but nothing has done as much as bothering to [learn about git's interactive rebase](git/interactive-rebase.md).

**TL; DR:** It's easy to rewrite history!

---

#### Resources

<a name="resource1">1</a>: See [this reply](https://stackoverflow.com/a/927386/8761234) on StackOverflow for a thorough walk through what's going on and how to better tailor this command for a more specific need. The above one-liner takes care of most of my use cases, though.
