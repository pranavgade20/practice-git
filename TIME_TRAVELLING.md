# Time Travelling

One of the coolest features in git is the ability to time travel and make edits in the past. You can go to any commit and browse(*check out*) the state of the repository at that point in time. You can *reset* to a previous state if you want some of your commits to be deleted. You can also pick individual commits to undo, and only the changes made in that commit will be undone.

## Setup

To start, switch to the master branch(`git switch master`) and create a new branch called `time-travelling`(`git switch -c time-travelling`)

## Checkout

To go to a previous commit, we can `git checkout <commit>`. Before we do that, let us try to find a commit to checkout to. `git blame` is very handy in these cases. In particular, we'd like to find that commit that unchecked the following checkbox:

- [ ] git is cool

And undo it. `git blame TIME_TRAVELLING.md` will show the commit-id which changed the line. We can then copy that commit-id and `git checkout commit-id` to go to that commit. Try looking around to make sure that you have indeed travelled back in time!

Another handy feature git has is *tagging* commits. We can `git tag tag-name` to start referring to the commit by `tag-name` instead of an ugly hash. So, while you are in the past, tag the commit we want to remove with `git tag bad-commit`. We can then switch back to the present with `git switch -`.

## Revert

Now, we have a commit tagged with `bad-commit` that we'd like to undo without changing other modifications we have made in the future. `git revert` is perfect for this. Since we know the tag we'd like to revert, we can simply `git revert bad-commit`, which will undo that one commit. You will be asked for a commit message to describe this revert, and you are done.

Finally, push your branch and create a PR.

## Reset

If you have some commits you'd like to remove from the history completely, you can use `git reset`. There are two basic modes to git reset - hard reset, and soft reset.

### Hard reset

To completely delete your changes and restore the state to a previous commit, you can `git reset --hard <commit>`. This will delete all changes, and make the current state just like it was after `<commit>`.

### Soft reset

To erase git's memory of updates, but keep your changes in the files intact, you can `git reset --soft <commit>`. This will not delete the changes you have made, but leave them as *changes to be commited* as `git status` would put it.

## Next steps

See MISC.md



