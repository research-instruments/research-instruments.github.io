# Делись опытом

## 1.**Fork the repo of interest**

[Create a Fork](https://docs.gitlab.com/ee/user/project/repository/forking_workflow.html){:target="_blank"} by clicking the *Fork* button.

## 2. **Clone your forked copy to your local machine**

Using a suitable command line interface, change from the current working directory to the location where you desire the cloned directory to be housed. Run:

``` sh
git clone <URL_of_your_forked_copy>
```

When you fork a project in order to propose changes to the original repository, you can configure Git to pull changes from the original or upstream repository into the local clone of your fork. This can be achieved on the command by typing in:

``` sh
git remote add upstream <URL_of_original_repo>
```

## 3. **Start working in a different branch**

Checkout and create a new branch with the name you want (for example, [develop](https://docs.gitlab.com/ee/topics/gitlab_flow.html/){:target="_blank"}):

``` sh
git checkout -b <your_desired_branch_name>
```

## 4. **Add locally created or modified files**

The git add command adds new or changed files in your working directory to the Git staging area.

``` sh
git add <file_name>
```
This step will ensure that the modified files will be included in the next commit. 

## 5. **Commit all the necessary changes to source code**

Create a commit, describing the changes you've done, with:

``` sh
git commit -m "your commit message"
```

## 6. **Sync with the remote repo**

In case someone made changes to the origin repository, type:

``` sh
git pull
```
It downloads the content from a remote repository and immediately updates your local copy to match the content.

## 7. **Commit your changes to the remote repo**

This command will update the remote repository with the modifications performed in your local environment. On the command line, run:

``` sh
git push origin <remote_branch_name>
```

## **Congratulations!**

You've made your first contribution on [git2.oecd-nea.org](https://git2.oecd-nea.org/){:target="_blank"}🏁!

You may now also create a merge request which will have to be approved by the code maintainers. 


&nbsp;
# Using the VS Code Working Environment

## Configuring your work environment

We recommend using [GitLab Workflow Visual Studio Code Extension](https://about.gitlab.com/blog/2018/03/01/gitlab-vscode-extension/){:target="_blank"} for seamless working with the NEA git instance. To configure it properly, please follow these steps:

* On [git2.oecd-nea.org](https://git2.oecd-nea.org/){:target="_blank"} go to *Settings* (top-right corner of the homepage) and select *Access Tokens* on the left navigation menu;
* When at the *Add a personal access token* form:
    * Give a name to your token;
    * Select *api* at the *Scopes:*;
    * Select *Create personal access token*;
    * Copy the token under the *Your new personal access token*;
    
* Go to your VS Code editor:
    * Open Command Palette by pressing ++ctrl+shift+p++;
    * Search for "GitLab: Set GitLab Personal Access Token" and hit ++enter++;
    * Enter the URL *https://git2.oecd-nea.org* of the NEA GitLab instance and hit ++enter++;
    * Paste your token and hit ++enter++.

That's it! Now you have user-friendly built-in VS Code source control. 🏁

## Work using the VS Environment

Start using it with typing in Command Palette:
``` sh
Git: Clone
```
to see the list of repositories available to you.


To make changes to the projects cloned into your local machine, create new branch by typing in Command Palette:

``` sh
Git: Checkout to
```

To update your local version of code by syncing it with the origin (in case someone is simultaneously making changes to the source code), in Command Palette type:

``` sh
Git: Pull 
```

To make changes to your version of code on the branch you've created, edit the sourcefiles by going to *Source Control* (on the left panel), type *your commit message* describing the commit and hit the *Commit* button. Push your commits to the git2 remote repository by clicking *Synchronize Changes* at the bottom left corner.

To merge changes into the main branch, with:

``` sh
Git: Checkout to 
```

go to master branch, and then, pick a branch to include with a command:

``` sh
Git: Merge Branch 
```

&nbsp;
# More on Git Workflow

[Learn more on how to use GitLab with VS Code](https://about.gitlab.com/blog/2018/03/01/gitlab-vscode-extension/){:target="_blank"}

You could find useful lessons on [software-carpentry.org](https://software-carpentry.org/){:target="_blank"}, with tutorials on:

* [Git VCS](https://swcarpentry.github.io/git-novice/){:target="_blank"}
* [Unix Command Shell](https://swcarpentry.github.io/shell-novice/){:target="_blank"}
* [Automation with Makefiles](http://swcarpentry.github.io/make-novice/){:target="_blank"}

