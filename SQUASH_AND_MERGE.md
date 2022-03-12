# Conflicts and Squashing

Usually, when multiple people work on the same file, managing everyone's contributions becomes quite tricky. When multiple versions of the same file are changed, we usually see places where different branches have different contents. This causes a *merge conflict* when we try to merge those branches. Let's see how git handles these scenarios, and how to effectively deal with merge conflicts. 

## Setup

- Create a branch called `squashing`
- In your `squashing` branch, add a program to print `Hello, World` and save it in a file called `hello`(for example, `hello.py`). Add it to git and commit it.
- Switch back to `master`, and create a new branch called `hello-git`. In `hello-git`, add a program to print `Hello, git` and save it in a file called `hello`(for example, `hello.py`. This name has to be the same as the name above). Add it to git and commit it.

Notice that we have modified/created the same file with the same path in the repository. What do you think will happen when we try to merge these branches?

## Merging

In your `squashing` branch, `git merge --squash hello-git` to merge the `hello-git` branch into `squashing`.  You will probably see a scary message like this:

```
Auto-merging hello.py
CONFLICT (add/add): Merge conflict in hello.py
Automatic merge failed; fix conflicts and then commit the result.
```

However, this is nothing to worry about! Git tells us that `hello.py` has a problem in it. So, let us look at the file and see what's wrong:

```python
<<<<<<< HEAD
print("Hello, World")
=======
print("Hello, git")
>>>>>>> hello-git
```

- Here, the first line tells us that the following content is what was found in the current version(commonly referred to as `HEAD`), which is the `squashing` branch in our case.
- The second line is the contents in the current version.
- The next line(=======) separates this section from the next section.
- The fourth line contains the contents in the `hello-git` branch.
- The last line tells us that the contents of the preceeding section are from the `hello-git` branch we are trying to merge into the current branch.

We would like to keep both of these lines. So, we can simply delete the lines git added to end up with something like:

```python
print("Hello, World")
print("Hello, git")
```

You have now resolved the merge conflict! Now, `git add hello.py` and `git commit` to finish the merge.

Push the changes and create a PR.

## Squashing

You should now have two commits in the `squashing` branch, one adding hello world, and one about the merge. When you contribute to a large project, you usually *squash* all new commits into a single commit for brevity. So, one feature gets one commit.

To *squash* the multiple commits into one, we can do an *interactive rebase*. To start, run `git rebase --interactive HEAD~2`. Replace the `pick` on the second line with `s` to squash the commit. Save the file and exit the editor. You will then be prompted to enter a new commit message for the combination of the two commits.

After you are done squashing the commits, push the changes. Since you are pushing to the same branch, the previous PR will be updated automatically. You will need to force the push with `git push --force` because you will be overwriting previous commits.

## Next steps

See TIME_TRAVELLING.md
