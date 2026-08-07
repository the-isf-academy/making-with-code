---
title: 08. Version Control
draft: true
---
# Version Control Lab


In this mini-lab, we're going to learn two new tools, git and Github, to help us with version control.

## [0] Set up

You have already used git a few times. Remember typing `git clone
...`? Cloning means pulling a copy of a repository down from github onto your
own computer. Now we are going to take the next step, editing a repository and pushing it to the cloud. 


---

### Terminal

{{< code-action "Double-check that git is installed." >}} If you do not see a version number, it should automatically install `git`.
```shell
git --version
```

{{< code-action "Configure git">}} : Type each of these commands into Terminal. 

> Make sure to replace `your_name` and `your_school_email` with your information.

```shell
git config --global user.name your_name
```
```shell
git config --global user.email your_school_email
```

{{< code-action "Add a shortcut command to easily open Github" >}} 
```shell
echo 'alias remote="open \"\$(git remote get-url origin | sed \"s/\.git\$//\")\""' >> ~/.zshrc
```

{{< code-action "Close your Terminal and re-open it to activate the changes." >}} 

<!-- 
{{< code-action "Install a credential manager to store your Github credentials securely." >}} *Copy and paste the lines below one at a time. It may ask you for your computer password.*
```shell
brew tap microsoft/git
```
```shell
brew install --cask git-credential-manager-core
``` -->

---

### Command Line Tool
{{< code-action "Run the below command to install the Github CLI." >}}
```shell
brew install gh
```
{{< code-action "Run the below command to authorize." >}} This will take you through a few prompts to log in to your github account.
```shell
gh auth login
```

**You will be asked the following questions to finish the authorization process. You should accept all the default highlighted options, which are these:**

0. "What account do you want to log into?" - GitHub.com
0. "What is your preferred protocol for Git operations?" - HTTPS
0. "Authenticate Git with your GitHub credentials?" - Yes
0. "How would you like to authenticate GitHub CLI?" - Log in with a web browser

> **If you are asked for your computer password, you won't see any letters appear as you type.** This is normal--it's to keep the person standing behind you from seeing your password.

{{< code-action "When prompted, copy your code and press enter." >}} Then you can follow the prompts in your browser.

<br>

<!-- {{< expand "Github Auth Token" >}}


Github uses personal access tokens to ensure security when remotely accessing a repository. You will need your token when using git from the Terminal. 

{{< code-action "Go to your github settings:">}}  [https://github.com/settings/tokens](https://github.com/settings/tokens).

> 0. **Select** `Generate new token (Classic)`.
> 0. **Type** `CS9` in the `Note` box.
> 0. **Set** the `Expiration` to `Custom` and choose a date after the last day of school.
> 0. **Check** the `repo` box.
> 0. **Select** `Generate token` at the bottom of the page. 

{{< code-action "Copy your token to your Notes application.">}} 

{{< /expand >}} -->

---

## [1] Your First Repo

**From now on, all code for this class will be stored as individual git repositories.** We are going to start now, by setting up your repository for the next lab. 

### Cloning Your Module Repository

We have set up repositories for each student to populate with their do now files.

{{< code-action "Go to your" >}} `unit00_drawing` **folder.**

```shell
cd ~/desktop/making_with_code/unit00_drawing/
```

{{< code-action "Clone your repo. This will copy it onto your computer." >}}  

> Below you'll see that the `git clone` command has a `yourgithubusername`. 
>
> **You need to replace this with your username**
>
> *e.g. `https://github.com/the-isf-academy/lab_modules_emmaqbrown`*


```shell
git clone https://github.com/the-isf-academy/lab_modules_yourgithubusername
```

If successful, you should see something like this in your Terminal:
```shell
Cloning into 'lab_modules_emmaqbrown'...
remote: Enumerating objects: 33, done.
remote: Counting objects: 100% (33/33), done.
remote: Compressing objects: 100% (22/22), done.
remote: Total 33 (delta 13), reused 22 (delta 8), pack-reused 0
Receiving objects: 100% (33/33), 7.51 KiB | 7.51 MiB/s, done.
Resolving deltas: 100% (13/13), done.
```

{{< code-action "Now that you have the lab, go into its folder." >}}
```shell
cd lab_modules_yourgithubusername
```

---

## [2] Working with Git

Whenever you are working on a project, you will go through four steps:

- **Edit files**: Work on all the files in this project just like normal.
- **Review Changes**: Look at your changes and make sure you are happy with
  them.
- **Commit**: Save your changes to the repository.
- **Push**: Push your copy of the repository up to github.

Let's practice.

---

### Step 0: Edit the README

Today we are going to practice commiting files to Github. Let's start by editing the `README.md` file. 

{{< code-action "Open the" >}}  `README.md` **file using VS Code:**

```shell
code README.md
```

As you've seen before, `README` files are like a guide to what's contained inside
a repository and how to use it. 

Right now the `README` is pretty bare. 

{{< code-action "Add your name as the Author." >}} Be sure to save.

Your final markdown file should look something like this:
```md
# Modules Lab
## Author: Ms. Brown
```


{{< aside "Markdown" >}}
The `README.md` file is written in a simple language called Markdown that
allows you to format text. 

[Here's a quick guide to
markdown](https://www.markdownguide.org/cheat-sheet). 

When you have a `.md` file
open in VS Code, you can preview the rendered version by pressing ⌘+Shift+V.
{{< /aside >}}

--- 

### Step 1: Review changes

Once you have made some changes to `README.md`, save your work in VS Code and go
back to the Terminal. 

{{< code-action "Let's use git to see what changes you have made." >}}

```shell
git status
```

You will see the following message:

```shell
On branch master
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git checkout -- <file>..." to discard changes in working directory)

    modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

👀 **Read the whole message.** It is telling you that only file that you have changed is `README.md`. 


{{< expand "To see specific changes" >}}

{{< code-action "Use another command to get details about what changes were made:" >}}
```shell
git diff
```

Now you will see a description of what you have added and what you have removed
from `README.md`:

```shell
diff --git a/README.md b/README.md
index 2c637ca..00ca290 100644
--- a/README.md
+++ b/README.md
@@ -1,9 +1,4 @@
 # Do Nows
-### Author: YOUR NAME GOES HERE
+### Author: Ms. Brown
 
-
-> INCLUDE THE FOLLOWING:
-> - A description of this repository
-> - A link to the `do now` page of the website.
->
-> *You may delete this section when complete.*
\ No newline at end of file
+This repository holds the do now exercises. The exercises can be found (here)[http://localhost:1313/courses/cs9/unit00/do_now/].
```

> To get out of `git diff`, type `q` then `return`.



**You should always run at a minimum run `git status` before you add changes to your repository.** To make sure you're adding the changes you meant to add, run  `git diff`. 

If you noticed any typos, or want to add something, edit `README.md` in Atom again, and then run `git status` and `git diff` again.

{{< /expand >}}

---

### Step 2: Commit

Now it's time to add these changes to your repository. 

**A *commit* is a collection of one or more changes that belong together.** 

For example, if you wanted to add a photo to your README document, you would need to 

0. edit `README.md`, telling it to include the photo
0. add the image file itself to the repo. 

These two changes belong together, so they should be part of the same commit.

**You will prepare a commit by adding all the files that have changes.**

{{< code-action "Let's add your" >}} `README.md` **to a new commit:**

```shell
git add README.md
```

{{< code-action "Run" >}} `git status` **again.** You will see that `README.md` has gone from red to green because it has been added to a new commit.

```shell
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
(use "git reset HEAD <file>..." to unstage)

    modified:   README.md
```

Now we are ready to finalize the commit. 

{{< code-action "Describe what you did, using a commit message." >}}
```shell
git commit -m "added name to readme"
```
> Every time you commit code, you need to write a message explaining what you have done. 
>
> Anybody reading your code (teachers, peers, a future version of you) will read the  log of your changes to understand what has been happening on the project. 


---

### Step 3: Push

Now it's time to sync the copy of your repo with the copy on github.

{{< code-action "Push your code:" >}}  
```shell
git push
```
> **A dialog box should pop up, select "Sign in with your browser, then follow the instructions"**
>
> If you do not see this, notify a teacher.


If all is successful with the login, you should see something below in Terminal. 
```shell
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 302 bytes | 302.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/the-isf-academy/lab_modules/emmaqbrown
   67838f1..4742ecf  main -> main
```

{{< code-action "Go to your repository page on Github.com." >}} You should see your updated version of your `README.md` at the bottom of the page.
> https://github.com/the-isf-academy/lab_modules_yourgithubusername
> 
> *Be sure to change, 'yourgithubusername' to your actual username.*

**🎉 Congratulations! You have successfully made your fist push to Github! 🎉**

---

## [3] Github Commands

**Summary of Github Steps:**

0. `git status`
0. `git add file.py`
0. `git status`
0. `git commit -m "describe changes here"` 
0. `git push`


| Command          | What it does                               |
|------------------|--------------------------------------------|
| `git status`     | displays the state of the repo             |
| `git add file.py` | adds a file to the commit                  |
| `git commit -m ""`     | records changes to the repo                |
| `git push`       | updates remote repo with your local repo   |


