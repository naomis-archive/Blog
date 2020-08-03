## Git and GitHub

Okay, I know what you are thinking: *not another git tutorial...*  - but this one will be different! This time, you will be working on an actual existing repository to get familiar with what GitHub has to offer.

## What is git? What is GitHub?

`git` is a version control system (VCS) that allows you to make changes to your code and "commit" those changes. The VCS tracks those changes, keeping a history of the evolution of your code. This allows many powerful features, such as rolling back to a previous version (in case your current version is broken), testing changes on a development version before merging them into the production version, and many more. `git` commands are handled through a command-line interface (CLI) - this can be done in Windows PowerShell, MacOS terminal,  or another CLI application. For this tutorial, we will be using GitBash.

GitHub is an online interface for managing your git repositories, storing them in the cloud, and accessing them from any computer. GitHub is an excellent resource for open-source projects, as it allows contributors to make bug reports, propose feature requests, and even submit improvements to the code. In this tutorial, we will review how to use these features!

## Setting up your Environment

There are a few things you will need to prepare before we can move on to the tutorial. If you already have a local development environment set up, you can skip this section and move on to *Getting Started*. Otherwise, continue reading for more information!

### 1. Set up your integrated development environment. 

You will need some sort of code editor. Personally, I recommend [VSCode](https://code.visualstudio.com/) as it offers many features. [Atom](https://atom.io/) is a good alternative, as well. There are many more that you can choose from - it is even possible to write code in NotePad, though you miss out on the extra features an IDE provides.

### 2. Download git for Windows

Next, you will need to download [git](https://git-scm.com/downloads). This shell will handle our `git` CLI commands, and make the process for pushing our changes to GitHub easier.

### 3. Create a GitHub account

If you have not done so already, you will need to create a [GitHub account](https://github.com/join). Don't worry - it is totally free!

### Bonus: Set up integrated terminal

If you have chosen VSCode or Atom as your IDE, there is a setting available to configure an integrated terminal - this will make things significantly easier, and the tutorial will assume you have done this. VSCode should automatically identify your available terminal programs - we will be using the one named `bash` for this tutorial.

## Getting Started

Now that you have downloaded what you need, we can get started! We will be working off of [this repository](https://github.com/nhcarrigan/github-testing-playground), which I specifically created for this tutorial. 

The very first thing you need to do is create a "fork" of the repository. Forking a repository creates a copy of the code, turns that copy into a separate repository under your account, and connects it to the original repository so you can track the changes between the two (and update yours to match the original). To create the fork, navigate to the repository linked above. Then, in the upper right corner, click the "Fork" button - GitHub will handle the rest!

![fork.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596415808133/-cBmuIalm.png)

Next you need to get the link for *your* repository, so you can create a local version on your computer. From your repository screen, make sure you have selected the `code` tab. Then find the green button that says "Code ↓" and click it. You should see a window with a URL - select and copy that url.

![clone.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596416251542/qg7oLm9G1.png)

Now, open your IDE and navigate to the directory (folder) where you want to load this repository. Once you have done this, open the integrated terminal (which should now be pointed to that directory). Enter the `git clone <url>` command, where `<url>` is that link you copied above. Allow the terminal a minute or two to process the command, and you should see all of the repository files appear on your computer!

Now we will set that aside - time to go back to the tutorial repository!

## Creating an Issue

In case you have lost the link, navigate to the [tutorial repository](https://github.com/nhcarrigan/github-testing-playground) again. From here, locate the `issues` tab and click it. You will now see a list of currently open issues for this repository (if there are any). 

What is an issue? Issues are commonly used by repository owners to allow users and contributors to report a bug or suggest a new feature. For this tutorial, you are going to create a slightly different one! If you would like to browse any currently open or closed issues, feel free to do so before moving on. When you are ready, select the green "New issue" button to continue.

![new-issue.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596416532373/Q6SorIBsR.png)

Sometimes a project will offer issue templates, which will pre-fill the new issue with the format and information the project owners prefer. In this repository you will only see one issue template (creatively named "Issue Template") - click the "Get Started" button to continue.

![issue-template.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596416752211/F7ltPkJFo.png)

This will take you to a screen that allows you to edit the issue before posting it. There are a few things to do here. First, you will see the issue title box - it currently has "[TUTORIAL]" for the title. Change the title to "[TUTORIAL] - <name>", where `<name>` is your username. Then move on to the body of the issue (the larger text input below the title). Underneath the "place your name below" comment, add your name. The comment will be hidden from view when you submit the issue, and you will often see comments in issue templates to explain how you should fill out the information. Continue following the instructions in the issue template - when you feel you have completed it, click the green "Submit new issue" button.

Congratulations! You have submitted your first issue! It will now look something like this: 

![completed-issue.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596417111475/jjNbDuPvI.png)

See that number next to the title? Yours will be different - this number allows you to reference your issue in other issues, pull requests, or comments. You will need this number later in the tutorial, so make a note of it! 

## Making Changes

Okay, now we need to make some changes to the code! Switch back to your IDE, and open up the folder called "github-testing-playground" to load your local files for your repository. You should now see something similar to this (depending on the editor you chose, it may look slightly different):

![local-repository.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596417330735/w9eBOgrKZ.png)

Now we can start some very basic `git` commands! The first thing you should do is create a new branch on your repository. A branch is essentially a separate path - like a fork in the road. It allows you to make changes to the code without saving those changes directly to the main (or master) branch. In your terminal, enter the command `git checkout -b <branchname>`, where <branchname> is the name of the branch you'd like to create. But wait! What does this command do? `git checkout` tells the software to look at the code for a specific branch - essentially, it changes the branch you are looking at. The `-b` flag says "create a new branch", and that branch will be named `<branchname>`. So if I use `git checkout -b tutorial/test` the command will create a new branch called "tutorial/test" and switch to that branch. I *strongly* recommend making changes to your code on a new branch, instead of working on the master branch, as this allows you to keep a clean (and working) copy of the code.

![git-checkout.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596417618630/Izg-n8k49.png)

Now that you are working on a new branch, let's make a change! In the `tutorial` folder, create a new file called `username.md` - but replace username with *your* username! An `.md` file is a markdown file, and supports [markdown formatting](https://www.markdownguide.org/basic-syntax/). For the content of this file, feel free to write whatever you wish! This is a good opportunity to practise your markdown formatting. (Please keep the content appropriate - inappropriate content will be rejected and the contributor will be blocked from the repository). Once you are happy with the content of the file, make sure you save it!

Next, you need to get those changes from your local files to the repository you created. There are three commands you will need to enter in the terminal to do this, and they will need to be entered separately and in order.
1. `git add ./` - `git add` stages files, preparing them to be added to the next commit. The `./` path adds *all* changed files in the project directory to the staging area.
2. `git commit -m "My first commit!"` - `git commit` creates a new commit (set of changes). The `-m` flag adds a commit message, and "My first commit!" is that message.
3. `git push` - Pushes the changes from the local repository to the remote repository (in this case, the fork you created on GitHub). 

If everything is configured correctly,  you should see a message like this:

![git-add-commit-push.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596418040032/cF473nT-N.png)
 
If you get an error, you will need to double check that you have followed the steps in this tutorial correctly. You may need to do some Google research for your specific error!

## Creating a Pull Request

Now you have updated your forked repository on GitHub, and you need to propose those changes to be added to the [tutorial repository](https://github.com/nhcarrigan/github-testing-playground)! If you head to the tutorial repository (or your own repository) you should see a yellow notice that says "<branchname> had recent pushes" and a button that says "Compare and pull request". 

![compare-and-pull.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596418311969/-OIR-xS6PT.png)

Click the "Compare and pull request" button to get to the next screen. Now you will have the option to select a `base` and a `head` repository. The `base` repository should be the tutorial repository (nhcarrigan), and the `base` branch should be `master`. The `head` repository should be YOUR repository, and the `head` branch should be the <branchname> you created earlier. NOTE: You may see a warning that says "Can't automatically merge" - this means there are changes to the tutorial repository that are not reflected in your repository - for this tutorial, you can safely ignore this and continue with the instructions.

![base-and-head.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596418475443/keCEUFfiR.png)

Once you have done this, you should see the Pull Request inputs load below. The smaller Title box should be pre-filled with your commit message (if you made more than one commit, it should take the most recent one). You can change this if you'd like, or leave it as is. The larger box will be pre-filled with a Pull Request template. Like an issue template, the pull request template may be used by a project owner to contain the format or information they prefer. Like you did with the issue template, follow the comment instructions in the pull request template. When you have completed this, click the "Create Pull Request" to finish the process!

![completed-pull-request.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1596418773517/AZWaD-D39.png)

## What's next

Sometimes, when you create a pull request, a project may require a certain number of reviews from project members. These reviews will either approve your proposed changes, or request that you modify or change the code you have written. Keep an eye on the pull requests you submit! 

If you would like to continue experimenting with `git` and GitHub, you are welcome to create issues and pull requests on this tutorial repository until you feel comfortable. Sometimes, as mentioned before, you may run into pull requests that cannot be automatically merged because changes occurred on the main repository that were not in your forked repository. These are called "merge conflicts", and GitHub allows you to resolve them directly in the GitHub editor! The option will appear if your pull request has a merge conflict. You can avoid merge conflicts by creating a pull request in the opposite direction before making changes. Make the pull request from the tutorial repository (as `head`) to your repository (as `base`) to get the changes updated in your repository. Then, you can use `git pull` on your local repository to bring those changes to your local files, before making your own changes. 

Now that you have completed this tutorial, try creating your own repository! Or contribute to an open-source project! The only limit is your willingness to learn

If you run into any issues with this tutorial, or have feedback, feel free to leave a comment or contact me directly! Contact links are available at the top of the blog.