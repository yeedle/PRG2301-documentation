# git & GitHub

`git` is a tool that enables code version management. That is when you want to track changes to your code, you want to add features or fix bugs in a safe way, and you want to work with a team on the same codebase. Git will track all "changes" to the codebase (a change can be adding or removing files, or adding, removing, or changing lines of code).\
\
The basic concept of `git` is that by default a change is not tracked. If you want to start tracking a change, you use the `git add file.js` command (or `git add .` to add all the files and subfolders in a repository). Once you're ready to create a new version of all the tracked changes you've made since the last version, you run the `git commit -m 'commit message'` command.&#x20;

Once a file is being tracked, you can also add and commit changes in one step by using `git commit -am 'message'`

The GitHub website is a central place where you can store your code "repositories".

{% hint style="info" %}
A code **repository**, often called "repo", is a storage location for coding projects that facilitates version control and collaboration among developers. It acts like a digital library where code is stored, managed, and tracked. Repositories can contain not just code, but also documentation, configuration files, and other resources related to a project.
{% endhint %}

When you're done for the day, or as soon as you're ready to share your commits with other team members (or if you want to back them up), you use the `git push` command to upload the code.

When you want to pull in the code and the changes that is online, you use `git pull`.

The way git repositories are usually structured, is that you have a `main` branch (sometimes this branch is called `master` that is the "official" version of your code. When you want to add something to your code project, you create a branch (using `git switch -c 'name-of-the-new-branch'`) and you can commit changes to that branch without touching the main branch. Once you're happy with all the changes in your branch, you can open a Pull Request (commonly called a PR) to merge the code from the branch into the `main` branch.&#x20;

You can use `git branch` to see all the branches that you have and `git switch name-of-branch` to switch between them.

To create a brand new repository you can do it in two ways: Either you first create the repository on GitHub and you use the `git clone` command to copy it to your local computer, or you run the `git init` command in the folder where your code is, and then you use `git remote add origin <git url>` to register the GitHub repository.\
\
Most of this functionality is also available as a GUI (graphical user interface, as opposed to a CLI - command line interface) in VS Code in the "Source Control" tab (with this icon: <img src="../.gitbook/assets/Screenshot 2024-04-01 at 12.32.24 PM.jpg" alt="" data-size="line">).
