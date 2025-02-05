<!--

author:   Rose Hartman
email:    hartmanr1@chop.edu
version:  0.0.1
module_template_version: 2.0.0
language: en
narrator: UK English Female
title: Setting Up Git

comment: This module provides recommendations and examples to help new users configure git on their computer for the first time.

long_description: If you're ready to start using the Git version control system, this lesson will walk you through how to get set up. This lesson should be a good fit for people who already have an idea of what version control is (although may not have any experience using it yet), and know how to open the command line interface (CLI) on their computer. No previous experience with Git is expected.

estimated_time: 20 min

@learning_objectives  

After completion of this module, learners will be able to:

- Configure `git` the first time it is used on a computer
- Understand the meaning of the `--global` configuration flag

@end

link:  https://chop-dbhi-arcus-education-website-assets.s3.amazonaws.com/css/styles.css

script: https://kit.fontawesome.com/83b2343bd4.js

-->

# Setting Up Git

<div class = "overview">

## Overview
@comment

**Is this module right for me?** @long_description

**Estimated time to completion:** @estimated_time

**Pre-requisites**

This module assumes that you...

- Have used the command line interface (CLI) on your computer before
- Have Git installed on your computer (note that it is probably installed already even if you've never used it)
- Have an account on github.com (you can [sign up now](https://github.com/signup) if you haven't yet --- it's free)
- Have at least a rough idea of what version control is, even if you've never used it before


**Learning Objectives**

@learning_objectives

</div>

## Global configurations

When we use Git on a new computer for the first time, we need to configure a few things.
Below are a few examples of configurations we will set as we get started with Git:

*   our name and email address,
*   what our preferred text editor is,
*   and that we want to use these settings globally (i.e. for every project).

<div class = "important">
We will use `git config` with the `--global` option to configure a user name, email address, editor, and other preferences. This only needs to be done once per machine.
</div>

### Setting up your username and email

On a command line, Git commands are written as `git verb options`,
where `verb` is what we actually want to do and `options` is additional optional information which may be needed for the `verb`. So here is how
Dracula sets up his new laptop:

```bash
git config --global user.name "Vlad Dracula"
git config --global user.email "vlad@tran.sylvan.ia"
```
<div class = "warning">
Please use your own name and email address instead of Dracula's.

You should use the same email you used to set up your account on [github.com](https://github.com/).
</div>

<div class = "help">
**Help! I'm getting errors already!**

Although git comes already installed on many machines, it may not be installed on yours yet. To check, try running `git --version`. If that returns an error, you likely need to install git before continuing: here are installation insructions for Windows, Mac, and Linux from the [git website](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git), and from [Software Carpentries](https://carpentries.github.io/workshop-template/#git). Either set of instructions should work fine, but if you have trouble with one then try the other.
</div>

This user name and email will be associated with your subsequent Git activity,
which means that any changes pushed to
[GitHub](https://github.com/),
[BitBucket](https://bitbucket.org/),
[GitLab](https://gitlab.com/) or
another Git host server
after this lesson will include this information.

For this lesson, we will be interacting with [GitHub](https://github.com/) and so the email address used should be the same as the one used when setting up your GitHub account.

<div class = "options">
If you are concerned about privacy, please review [GitHub's instructions for keeping your email address private](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-user-account/managing-email-preferences/setting-your-commit-email-address).

If you elect to use a private email address with GitHub, then use that same email address for the `user.email` value, e.g. `username@users.noreply.github.com` replacing `username` with your GitHub one.
</div>

### Handling line endings

As with other keys, when you hit `Enter` or `↵` or on Macs, `Return` on your keyboard,
your computer encodes this input as a character.
Different operating systems use different character(s) to represent the end of a line.
(You may also hear these referred to as newlines or line breaks.)
Because Git uses these characters to compare files,
it may cause unexpected issues when editing a file on different machines.

<div class = "learnmore">
Though it is beyond the scope of this lesson, you can read more about this issue
[in the Pro Git book](https://www.git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#_core_autocrlf).
</div>

You can change the way Git recognizes and encodes line endings using the `core.autocrlf` command to `git config`.
The following settings are recommended:

On macOS and Linux:

```bash
git config --global core.autocrlf input
```

And on Windows:

```bash
git config --global core.autocrlf true
```

### Setting your text editor

Dracula also has to set his favorite text editor, following the table below.

<div class = "options">
If you have a text editor you're already familiar with, choose that.

If you don't recognize any of the editors in the table below, we recommend setting your default editor for git to `nano`, using the following command: `git config --global core.editor "nano -w"`.
</div>

It is possible to reconfigure the text editor for Git whenever you want to change it.

<div class = "help">
**Exiting Vim**

Note that Vim is the default editor for many programs, including git.

If you haven't used Vim before and wish to exit a session without saving your changes, press `Esc` then type `:q!` and hit `Enter` or `↵` or on Macs, `Return`.
If you want to save your changes and quit, press `Esc` then type `:wq` and hit `Enter` or `↵` or on Macs, `Return`.

This is [a common problem that has frustrated many a new git user](https://stackoverflow.blog/2017/05/23/stack-overflow-helping-one-million-developers-exit-vim/)! You are not alone.
</div>


| Editor             | Configuration command                            |
|:-------------------|:-------------------------------------------------|
| Atom | `git config --global core.editor "atom --wait"`|
| nano               | `git config --global core.editor "nano -w"`    |
| BBEdit (Mac, with command line tools) | `git config --global core.editor "bbedit -w"`    |
| Sublime Text (Mac) | `git config --global core.editor "/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl -n -w"` |
| Sublime Text (Win, 32-bit install) | `git config --global core.editor "'c:/program files (x86)/sublime text 3/sublime_text.exe' -w"` |
| Sublime Text (Win, 64-bit install) | `git config --global core.editor "'c:/program files/sublime text 3/sublime_text.exe' -w"` |
| Notepad (Win)    | `git config --global core.editor "c:/Windows/System32/notepad.exe"`|
| Notepad++ (Win, 32-bit install)    | `git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`|
| Notepad++ (Win, 64-bit install)    | `git config --global core.editor "'c:/program files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`|
| Kate (Linux)       | `git config --global core.editor "kate"`       |
| Gedit (Linux)      | `git config --global core.editor "gedit --wait --new-window"`   |
| Scratch (Linux)       | `git config --global core.editor "scratch-text-editor"`  |
| Emacs              | `git config --global core.editor "emacs"`   |
| Vim                | `git config --global core.editor "vim"`   |
| VS Code                | `git config --global core.editor "code --wait"`   |


### Default branch naming

Git (2.28+) allows configuration of the name of the branch created when you initialize any new repository.  Dracula decides to use that feature to set it to `main` so
it matches GitHub, which is the cloud service he will eventually use.

```bash
git config --global init.defaultBranch main
```

Source file changes are associated with a "branch."
For new learners in this lesson, it's enough to know that branches exist, and this lesson uses one branch.
By default, Git will create a branch called `master`
when you create a new repository with `git init` (as explained in the next lesson in this series). This term evokes the racist practice of human slavery and the
[software development community](https://github.com/github/renaming)  has moved to adopt
more inclusive language.

In 2020, most Git code hosting services transitioned to using `main` as the default branch. As an example, any new repository that is opened in GitHub and GitLab defaults to `main`.  
However, Git has not yet made the same change.  As a result, local repositories must be manually configured have the same main branch name as most cloud services.

<div class = "help">
For versions of Git prior to 2.28, the change can be made on an individual repository level using `git branch -M main` if there are currently commits in the repository, or `git checkout -b main` if there are no commits/the repository is completely empty.
</div>

Note that if this value is unset in your local Git configuration, the `init.defaultBranch` value defaults to `master`.

### Check your global configurations

The commands we just ran in the sections above only need to be run once: the flag `--global` tells Git to use the settings for every project, in your user account, on this computer.

You can check your settings at any time:

```bash
git config --list
```

You can change your configuration as many times as you want: use the same commands to choose another editor or update your email address.

<div class = "help">
**Proxy**

In some networks you need to use a
[proxy](https://en.wikipedia.org/wiki/Proxy_server). If this is the case, you may also need to tell Git about the proxy:

```bash
git config --global http.proxy proxy-url
git config --global https.proxy proxy-url
```

To disable the proxy, use

```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```
</div>

## Git Help and Manual

Always remember that if you forget the subcommands or options of a `git` command, you can access the relevant list of options typing `git <command> -h` or access the corresponding Git manual by typing
`git <command> --help`, e.g.:

```bash
git config -h
git config --help
```

<div class = "options">
** -h vs --help**

The `-h` flag returns a list of options for that command. It's most useful when you already know what a command does and you want a reminder of how to use it. The `--help` flag pulls up the full git documentation for a command, so it's a better choice if you want to learn more about what the command does.
</div>

More generally, you can get the list of available `git` commands and further resources of the Git manual typing:

```bash
git help
```

<div class = "important">
While viewing the manual, remember the `:` is a prompt waiting for commands and you can press `Q` to exit the manual.
</div>

## Quiz

Without looking it up, what can you say about the following command? `git config --global alias.ci commit` Select all that apply.

[[X]] It will change something in the global settings, meaning it will apply to all the projects in your user account on this computer
[[ ]] You'll need to run this command each time you start a new git repository if you want it to take effect
[[ ]] It will affect your settings on GitHub.com as well as on your local computer
***
<div class = "answer">
This command begins with `git config --global`, like most of the commands we ran during this lesson. The `--global` flag tells us this setting will be applied for all of the git projects on this user account on this computer (for a review of this topic, see [Check your global configurations](#check-your-global-configurations)).

Global configurations for git only need to be run once and then they will continue to apply until you undo them or replace them with new settings.

Importantly, 'global' only refers to within your account on your machine; if you use git on multiple machines, or when you use it in the cloud (for example, on GitHub.com), your global configuration settings from your personal machine won't apply.
</div>
***

If you wanted to learn more about the command above, which of the following would be good places to start? Select all that apply.

[[ ]] `git config -h`
[[X]] `git config --help`
[[X]] Google it
[[X]] Ask a friend, or post a question in an online community forum
***
<div class = "answer">
Remember that `git config -h` will show you a list of the options you can use for `config`, whereas `git config --help` will bring up the full documentation for `config`, not just a list of options. In this case, we need information about what the command does, so a list of options won't be helpful; the documentation might provide an answer, though!

In this particular case, `git config --help` won't tell you what you want to know about the global settings for aliases, so that will be a dead end here. But sometimes the git help files will have exactly what you need, so it's never a bad idea to check!

Googling it is also never a bad idea. There are tons of great git resources available online, and for common problems you're likely to find a useable answer quickly. Keep in mind that there are lots of very advanced git users posting things online as well, though, and if you get unlucky you could end up with search results that are not at all user-friendly for beginners. When that happens, remind yourself that kind of gatekeeping is a failure on the part of the writer, not something wrong with you as a learner, and keep searching to find a good answer to your question somewhere else.

Asking a peer (in person, or via an online community of practice) is probably the best strategy in a lot of situations, especially if the first two strategies don't yield useful results right away. If you feel embarrassed to ask a question, remind yourself that everyone is a beginner at some point and [asking for help is a great skill to practice](https://www.linkedin.com/pulse/20141027152039-95387062-why-you-should-never-feel-embarrassed-to-ask-questions)!
</div>
***

<details>

<summary>**Curious about this `alias` option?**</summary>

<div class = "learnmore">
This command is an example of [how to set aliases in git](https://www.atlassian.com/git/tutorials/git-alias), something we didn't cover in this lesson.

Basically, aliases are shortcuts you can write for yourself so you don't have to type out full git commands every time. We won't be using aliases in the lessons here, but you may like to set some up on your own computer if that sounds attractive to you!
</div>
</details>

## Additional Resources

This module is based closely on the [Setting up Git](https://swcarpentry.github.io/git-novice/02-setup/index.html) lesson published by [Software Carpentry](https://software-carpentry.org/). Much appreciation to Carpentries for developing the content and sharing it under a creative commons license!

If you're new to the command line (or want a refresher), you may like to read through [Command Line 101](https://liascript.github.io/course/?https://raw.githubusercontent.com/arcus/education_modules/main/bash_scripting_101/bash_scripting_101.md), a general resource on using the command line with no specific focus on git.

Although the content here focuses on command line git, you may prefer to use the GitHub Desktop program instead. See the instructions posted on GitHub.com for how to [install and configure GitHub Desktop](https://docs.github.com/en/desktop/installing-and-configuring-github-desktop).

## Feedback

In the beginning, we stated some goals.

**Learning Objectives:**

@learning_objectives

We ask you to fill out a brief (5 minutes or less) survey to let us know:

* If we achieved the learning objectives
* If the module difficulty was appropriate
* If we gave you the experience you expected

We gather this information in order to iteratively improve our work.  Thank you in advance for filling out [our brief survey](https://redcap.chop.edu/surveys/?s=KHTXCXJJ93&module_name=%22Setting+up+Git%22)!
