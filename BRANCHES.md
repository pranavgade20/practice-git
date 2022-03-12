# Branching and Merging

A very central feature of git is having *branches*, which allow you to work on multiple features independently, and then *merging* the features into the same codebase later. 

We usually use branches to allow multiple people to work on the same codebase and to test different new features without affecting other features. Then, when we are sure that our code works, we can *merge* it in the main branch.

## Branching

To figure out what branch you are currently on, use `git status`. This will show the branch name you are currently on, along with a bunch of other information about the status of the project.

To create a new branch and start working on it,

```bash
git branch branch_name # create a new branch called branch_name
git switch branch_name # switch to the branch called branch_name
# or, you can use the following shortcut which does the same thing as the lines above
git switch --create branch_name # create a new branch, and switch to it
```

Now, you can make any edits to your previous code, and commit it to this branch. And you can `git switch` to the previous branch to make the changes go away. When you switch back to this branch, the changes will be restored!

To begin, create a branch called `branching` and switch to it. This will be our principle branch for now.

Then, create a branch called `hello_world` and switch to it. Then, create a hello world program in any language, and save the file in a directory called `hellos`. Commit this change.

Now, switch to `branching` and create a branch called `hello_git`. Create a program that prints `Hello, git!` and commit it in `hellos` folder in this branch. Remember to give different names to both programs(for example, `hello_world.py` and `hello_git.py`)

## Merging

You should now have three branches: `branching`, `hello_world`, and `hello_git`. We will now merge the branches into `branching` so that all changes are reflected in the principle branch.

To start, make sure you are in the `branching` branch. Then, you can simply `git merge hello_world` to merge the branch into `branching`. Because the `branching` branch did not have any new changes, the update will be performed via a 'fast-forward', where the newer commits from `hello_world` are copied and pasted onto `master`(for efficiency, git actually just moves some pointers around, but we don't need to worry about that).

However, scenarios like merging `hello_git` into the new `branching` are far more common. Here, `branching` has newer commits(adding hello_world), and hello_git has newer commits(adding hello_git). So, we say that the branches have *diverged*. In this case, merging is slightly trickier.

After making sure that you are on `branching`, `git merge hello_git` to merge the branch into `branching`. Git is pretty smart, and will see that since you have modified different files, you can simply copy both in the same folder. Merging changes made in the same file is sometimes trickier, and we'll practice this more complicated scenario later.

You will have to specify a commit message to describe this merge, and you are done!

Push the changes and create a PR to the original repository. You will have to switch to the `branching` branch in the browser before you open the PR.

## Next steps

See SQUASH_AND_MERGE.md
