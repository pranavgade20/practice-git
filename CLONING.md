# Cloning and Pushing

Cloning downloads a repository to your computer, where you can work on it using your favorite tools. After you have made the necessary changes, you can commit and push the changes to the *remote*(i.e., github servers) from your *local*(i.e., your computer).

## Setup

After you have created an account on github, I suggest you set up your local as described [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh), as it will make subsequent steps easier. After you have set this up, you should be able to run `ssh git@github.com` and see the following message:

```
$ ssh git@github.com
PTY allocation request failed on channel 0
Hi pranavgade20! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

If you see this, you are good to go!

## Cloning

To clone your repository, use `git clone git@github.com:username/repo_name.git`. Then, change directory to `repo_name` with `cd repo_name`. You can now use any editor to make changes to the files.

We will create a new directory called images and add an image to the directory. Go to `repo_name` and create a new folder called `images`. Then, take a screenshot of the output `ssh git@github.com` gives you, and add it to the directory.

## Committing

Add the files to the *staging area* by running  `git add images/`. Then, you can commit them with `git commit -m 'commit message'`. You can replace the commit message with a line describing what this commit is.

If you'd like to see the current status of the repository, you can `git status`.

To see the changes you will be committing, you can run `git diff` and/or `git diff --staged`. The first command shows the changes if the file isn't added to the staging area with `git add`. The second shows the difference in the staging area.

## Pushing
(cloned and pushed)
Finally, `git push` to push the changes to the remote. Assuming you have completed the setup properly, this step should be seamless.

After the changes are pushed, you can create a PR to the original repository, just like the last time.

## Next steps

Next steps are in BRANCHES.md



