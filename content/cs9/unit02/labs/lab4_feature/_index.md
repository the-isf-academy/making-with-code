---
title: 3. Feature Lab
draft: True
resources:
- name: branch
  src: images/courses/cs9/unit02/02_03_feature_branch.png
- name: merge
  src: images/courses/cs9/unit02/02_03_feature_merge.png
- name: pullrequest_0
  src: images/courses/cs9/unit02/02_03_feature_pullrequest_0.png
- name: pullrequest_1
  src: images/courses/cs9/unit02/02_03_feature_pullrequest_1.png
- name: pullrequest_2
  src: images/courses/cs9/unit02/02_03_feature_pullrequest_2.png
- name: pullrequest_3
  src: images/courses/cs9/unit02/02_03_feature_pullrequest_3.png
- name: pullrequest_4
  src: images/courses/cs9/unit02/02_03_feature_pullrequest_4.png
- name: pullrequest_5
  src: images/courses/cs9/unit02/02_03_feature_pullrequest_5.png
---
{{< devnote >}}
CS1/CS2 links
{{< /devnote >}}

# 3. Feature Lab

## Overview
In this lab, you will be contributing to the development of the [Quest software library](https://github.com/the-isf-academy/quest), the library you'll ultimately use to make your unit project game.

**You goal is simple: identify a feature you want for you game that the Quest framework currently doesn't support and build it.**

However, this task is more complicated than it seems. Since this is a real piece of software that you, your peers, and many others after you will use, you've got to make sure your contributions are effective. Specifically,

* your feature should work as you describe it
* your feature shouldn't break any other parts of the game -- older examples should still work without modification after your feature is done
* your feature should be well documented so others can use it (and continue to develop it!)

## [0] Setup

*Note: if you made changes to the code during the Quest lab that you would like to keep, clone the [Quest framework](https://github.com/the-isf-academy/quest) again into a different directory in your unit_02 folder and use the new copy for this lab.*

💻 **TODO:** First, make sure that you Quest repo is up-to-date. In the `quest_lab` repo:

```shell
    git stash
    git pull
```
💻 **TODO:** Make sure your packages are up to date: `pip install --upgrade --editable .`

## [1]  Working on your feature branch
In this lab, you will work on a branch of the main repository to implement your feature. Git branches are copies of a code base where you can work on a specific feature of the code without worrying about messing up the code in the main branch.

{{< figure src="images/courses/cs9/unit02/02_03_feature_branch.png" width="400px" >}}

Once your feature is done, we'll merge your branch into the main branch and add your feature to the main software package. Then, everyone will be able to use it!

{{< figure src="images/courses/cs9/unit02/02_03_feature_merge.png" width="400px" >}}

### Checking out your branch
To simplify things, we've already created a branch for your group.

💻 **TODO:** All you need to do is change to it:

```shell
    git checkout feature-TEAM_NAME
```
*Note: make sure to replace `TEAM_NAME` with your team name from the game [group sheet](https://docs.google.com/spreadsheets/d/18igzTD_URXydP3qj0P6kn1ExIAmTWcdMxn9phfgk-K8/edit?usp=sharing).*

## [2] Working on your branch and pushing the work to GitHub
You are now ready to start working on your feature branch!

**Note: Before every work session, you should make sure that you are on your feature branch by running `git checkout feature-TEAM_NAME`**

### Working on your branch
You are responsible for figuring out how to implement your feature. The planning document we made in class should be helpful.

💻 **TODO:** To start, make a new file in the `examples` repo. Make a simple class that extends one of the example games already created. You can use another example game as a template.

Make sure that at the end of your file, you include the code to run the game you've create:

```python
    if __name__ == '__main__':
        game = YOURGAMECLASSGame()
        game.run()
``` 
### Testing your feature
As you are developing your feature, it's important that you don't break any other functionalities of the Quest library. To make sure, you can run all of the examples in the `examples` repo.

💻 **TODO:** To test these games, `cd` to the `quest_lab` directory and run:

```shell
    python test_feature.py
```
*Note: this test will not test the actual functionality of your feature. You'll have to find a way to test that on your own 😁*

### Documenting your work
The Quest library is a public library that anyone can access. As such, we need to make sure that it is well documented so others know how it works.

For every class and function you write or edit, you need to make sure that it has a comment that accurately describes what it does. Comments for classes should be in the following format:

```python
    class MyGameClass(QuestGame):
    """ This is a comment describing what the class does.

    Attributes:
          INIT_ARG_0: description of the first argument in the class's __init__() function
          INIT_ARG_1: description of the second argument in the class's __init__() function
    """
```
Comments for functions should be in the following format:

```python
    def some_function(self, ARG_0, ARG_1):
    """ This is a comment describing what the function/class does. For functions, you also need the Args and Returns field below.

    Args:
          ARG_0 (ARG_TYPE): description of the first argument passed into the function
          ARG_1 (ARG_TYPE): description of the second argument passed into the function

    Returns:
          (RETURN_TYPE) Description of what the function returns.
    """
```
💻 **TODO:** Start by writing a comment for the new game class you just wrote.

### Pushing your work

After a class session or after you've reached a milestone, you can commit your code just like normal:

```shell
    git add EDITED_FILES
    git commit
    git push
```
💻 **TODO:** Commit the code you just wrote for the new example game.

*Note: since this is a group project, you will have to deal with merging your code and merge conflicts when another member of your team pushes their work. Checkout [this refersher on merge conflicts](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/resolving-a-merge-conflict-using-the-command-line) if you get stuck.*

## [3] Submitting your work
Finally, at the end of the lab when you have completed your feature, you can make a final push to GitHub just like normal.

To submit your work, you will need to make a pull request. This is a request to merge the code from your branch into the master branch.

To do this:

1. Go to the [GitHub page for the Quest repository](https://github.com/the-isf-academy/quest).
1. Below the number of commits, click on the "Branch" drop-down menu.<br>
{{< figure src="images/courses/cs9/unit02/02_03_feature_pullrequest_0.png" width="400px" >}}

1. Select your team's branch.<br>
{{< figure src="images/courses/cs9/unit02/02_03_feature_pullrequest_1.png" width="400px" >}}

1. Make sure the branch updated and click "New pull request".<br>
{{< figure src="images/courses/cs9/unit02/02_03_feature_pullrequest_2.png" width="400px" >}}

1. Write a title for your pull request. Optionally, you can add comments about your submission. Create your pull request.<br>
{{< figure src="images/courses/cs9/unit02/02_03_feature_pullrequest_3.png" width="400px" >}}

1. If you see this page, your pull request was created!<br>
{{< figure src="images/courses/cs9/unit02/02_03_feature_pullrequest_4.png" width="400px" >}}

*Note: GitHub will automatically run a few checks to make sure your code builds correctly. If you don't pass the check, make sure your code passes the `test_feature.py` file.*<br>
{{< figure src="images/courses/cs9/unit02/02_03_feature_pullrequest_5.png" width="400px" >}}
