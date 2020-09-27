## Good Old git: A Few Tips and Tricks

Today I would like to share a few tips and tricks I've picked up that make my experience with `git` and GitHub both significantly smoother. I've run in to a few odd hiccups while using GitHub, and have been slowly putting together tricks to avoid those weird occurrences. 

## Updating your Fork

If, like me, you are regularly contributing to an open source project, you likely have to update your fork's primary branch to match the current state of the upstream repository. When I first started contributing, I was making a pull request from the upstream into my fork to bring the latest commits over. This worked well enough, but I was running in to the following mess: 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1601168260666/xaSz5ypE8.png)

At some point, this list would get so long that I ended up nuking my fork and re-forking it. Until, that is, I discovered this set of commands.

```bash
# get the current state of the upstream repo
git fetch upstream

# get the local instance of the fork caught up
git reset --hard upstream/master

# force the remote instance of the fork to match
git push --force
```

And now your fork matches the upstream exactly, with no extra commits from merging a PR!

## Renaming a Branch

I tend to make a lot of typos. And I type quickly. This means I often end up with a typo in my local branch. I *used* to simply deal with it, and work with a mis-named branch. Until I discovered how simple it was to change the branch name.

```bash
# switch to the branch you want to rename
git checkout <old_name>

# move the branch to the new name
git branch -m <new_name>

# optionally push the branch to the remote
git push -u origin <new_name>

# optionally delete the old remote branch
git push --delete origin <old_name>
```

Now the branch will have the correct name on both the local and remote instance of your repository.

## Bonus: Checking out PRs

PR reviews were tricky with GitHub. I either manually copied the code changes into my local repository's files, or I made a separate PR to bring the changes into a test branch and pulled them to my local repository. Either way, it felt like a lot of work to test a pull request. Enter the *GitHub CLI*. 

I discovered very quickly that the GitHub CLI offered a simple way to do this. 

```bash
gh pr checkout <pr_number>
```

This command creates a new branch on your local repository, and pulls down the code as it exists in the PR. Thus, you are able to test the changes and ensure everything works correctly. The best part: If you're working on a fork, this command will grab PRs that target the upstream so you can assist with the review process. (This made my life much easier when contributing to freeCodeCamp). 

Do you have any `git` tips to share? Drop a comment below! I'm always looking for new tricks!