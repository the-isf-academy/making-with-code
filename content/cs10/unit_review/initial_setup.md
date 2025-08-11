---
title: "Check Setup"
weight: 1
---

# Check setup

**Welcome back to CS! These instructions will help you get your computer set up for the class.**
If you get stuck or are unsure what to do, first check out the debugging section at the bottom of the page. If you are still encountering an error, please send a screenshot of your error to Ms. Brown.


---
 
## Ensure Xcode is Updated

{{< code-action "Copy and paste the command below into your Terminal to install Xcode." >}} Then press `Enter/Return`. Make sure you have a strong internet connection, this may take up to 2 hours to complete. Don't worry, you can still use your computer and have it running in the background. 

```shell
xcode-select --install
```


{{< code-action "Enter your password when prompted." >}} You won't see any letters appearing as you enter the password. This is a security feature.

{{< aside >}}
If you already have this installed, you will see the following message instead:
```shell
xcode-select: error: command line tools are already installed, use "Software Update" to install updates
```
{{</ aside >}}

---

## Install Latest Version of Python

(0) **Start by installing the latest version of Python.** [Open this link](https://www.python.org/downloads/), click "Download Python," and follow the installation instructions.


(1) **Once the installation finishes, you will see a Finder window showing what was installed**.
(If you closed the window, open Finder, click on "Applications," and then "Python 3.13" (or whatever version of Python you just installed).


(2) **Check Python installed successfully by typing `python3 --version` into the Terminal.** You should see the version number `3.13`.

(3) **Double-click on "Install Certificates.command".** This will will open a Terminal window and run a bunch of commands. Once you see `[Process completed]`, you may close the window.

(4) **Double-click on "Update Shell Profile.command".** Each of these will open a Terminal window and run a bunch of commands. Once you see `[Process completed]`, you may close the window.

[Here is a video that walks you through the steps.](https://youtu.be/OiCiOgeyaWA)


{{< aside >}}
**If you see a red "Permission denied" error message when running "Install Certificates.command"**:
- open a Terminal window and run **`sudo "/Applications/Python 3.13/Install Certificates.command"`**
- You will be asked for an administrator password; you won't see any letters appearing as you enter the password. This is a security feature.
{{</ aside >}}

<!-- {{< youtube "OiCiOgeyaWA" >}} -->

---

## Update Homebrew
*Homebrew helps you install different libraries and packages*

{{< code-action "Update Homebrew" >}} 

```shell
brew update
```

{{< code-action "It may ask you to upgrade" >}} 

```shell
brew upgrade
```

---


## Upgrade Poetry

{{< code-action "Upgrade Poetry " >}} 
```shell
brew upgrade poetry
```

{{< code-action "Add the poetry shell plugin" >}} 
```shell
poetry self add poetry-plugin-shell
```

---

## Github Setup 

{{< code-action "Add a shortcut command to easily open Github" >}} 
```shell
echo 'alias remote="open \"\$(git remote get-url origin | sed \"s/\.git\$//\")\""' >> ~/.zshrc
```

{{< code-action "Upgrade gh " >}} 
```shell
brew upgrade gh
```

{{< code-action "Ensure you are logged into Github." >}} Follow the instructions. 
```shell
gh auth login
```

---

## Testing your Setup

💻 **Run each of the following checks one at a time to check your setup.** If you do not see an `version number`, there was an error with the install.


✔️ *Checks `Xcode`*

```shell
xcode-select --version
```

✔️ *Checks `Python`*

```shell
python3 --version
```

✔️ *Checks `Homebrew`*

```shell
brew --version
```

✔️ *Checks `Poetry`*

```shell
poetry --version
```



{{< deliverables "Fill out the Install Form" >}}

✅ **Fill out this form to notify your teachers if your install was successfull:** [forms.gle/uHZ2xGhuhhYFnCkXA](https://forms.gle/uHZ2xGhuhhYFnCkXA)


{{< /deliverables >}}

---

## Debugging 

**If `code --version` showes `EACCES: permission denied, unlink '/usr/local/bin/code'`**
1.  First double check `VS Code` is in your “Applications” folder
2.  In the top menu click `View > Comannd Palette...`
3.  Type `uninstall code`, click the option 
4.  Type `install code`, click the option
5.  In Terminal, try `code --version`.
6.  If you do not see a version number, run this command: `sudo chown -R your_user_name /usr/local/bin`
7.  In Terminal, try `code --version`.
3. If still does not show a verison number, ask a teacher.

---

**If `poetry --version` does NOT show a version number.** 
1. Copy & Paste this command into the Terminal: `pipx ensurepath`
2. Try `poetry --version` again. 
3. If still does not show a verison number, ask a teacher.

---

**If `brew --version` does NOT show a version number.** 
1. Copy & Paste the commands below into the Terminal.  Be sure to paste them one at a time. Each time, pressing `return` to run the command.
    1. `echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile`
    2. `eval "$(/opt/homebrew/bin/brew shellenv)"`
2. Try `brew --version` again.
3. If still does not show a verison number, ask a teacher.

