<!--

author:  Elizabeth Drellich
email:    drelliche@chop.edu
version:  0.0.1
language: en
narrator: UK English Female
title: Exploring the History of your Git Repository
comment:  This module will teach you how to look at past versions of your work on Git, compare versions, and return to former versions.
long_description: You know that version control is important. You know how to save your work to your Git repository. Now you are ready to look at and compare different versions of your work. In this module you will you will learn how to navigate through the commits you have made to Git. You will also learn how to compare current code with past code, and, if necessary, revert to an earlier version of your work.

@learning_objectives  
After completion of this module, learners will be able to:

- Identify and use the HEAD of a repository.
- Identify and use Git commit numbers.
- Compare versions of tracked files.
- Restore old versions of files.

@end

link:  https://chop-dbhi-arcus-education-website-assets.s3.amazonaws.com/css/styles.css

script: https://kit.fontawesome.com/83b2343bd4.js

-->

# Exploring the History of your Git Repository


<div class = "overview">

## Overview
@comment

**Is this module right for me?** @long_description

**Estimated time to completion:**

**Pre-requisites**

This module is for you if:

* You know that version control is important. (See [module](module) to learn why version control is important.)
* You know how to save your work to your Git repository. (See [module](module) to learn how to create a Git repository and put your work into it.)
* You want to learn how to see and compare different versions of your work.


**Learning Objectives**

@learning_objectives

</div>

## Lesson Preparation

*We need some sort of emulator here, probably the best way (if possible) would be to have an emulator that can come preloaded with all of the commands from the previous module so that learners can explore the history without having to go through that entire module, especially if they did it a while back, or already know that stuff. Having something just checkout a particular head in the chain of the modules could then be used for later modules, by checking out later or earlier heads.*

If you are coming to this module directly from the [previous one](link) and still have that console open, you can continue using that console instead.

## Seeing prior commits

Keeping track of all versions and being able to see and compare them is the entire point of using version control on a project you are working on alone. It is also a huge part of working on a project with others, but we will get to that part in [module](module).

Each time you `commit` to Git, you are marking the current state of your project as a checkpoint that you can return to. You will hear these states referred to as *commits*.

<div class = "options">
You are going to learn about two ways to refer to past commits:

- Using HEAD to refer to the latest `commit`.
- Using the commit number assigned to a particular `commit`.

</div>

![The Commit Stack: a stack of 3 flat white boxes, stacked on top of each other with open air in between. The top box is labeled "last committed version of repository", the middle box is labeled "next to last version of repository" and the bottom is labeled "previous version of repository". There are three dots below the lowest box indicating that this pattern continues.](./fig/Commit_stack.svg)

### Using HEAD

The `HEAD` refers to the most recently commit to your repository. It won't include any changes that haven't been committed to the repository yet. You can see that most recent commit by entering `git show HEAD`.

The last thing that Dracula committed in the previous module was the `.gitignore` file in which he told Git not to track certain files:

```
$ git show HEAD
commit 65f447e949e53edc0db08b93670d2e2b35fa6c22 (HEAD -> main)
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Mon Feb 28 11:47:17 2022 -0500

    Ignore data files and the results folder.

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..f451386
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1,2 @@
+*.dat
+results/
```

<div class = "help">
Sometimes a command will output many lines of code that may not be relevant to you. For example the `show` command will output not just the commit message, but also every single change that you made in that commit. If the output of a command is longer than the number of lines your console displays, you can navigate that output using the down and up arrows on your keyboard, or press `q` to skip to the end of that output.
</div>

Maybe you want to look one step further back into your work. By using `HEAD~n` you can look back $n$ checkpoints in your repository. The `~` named "tilde" and pronounced "TIL-duh."

For example, to look back just one commit before the most recent checkpoint, use `git show HEAD~1`. If instead you wanted to look back three checkpoints (the most recent and then two before that) you would enter `git show HEAD~2`.

![IMAGE: The same stack of 3 white flat boxes, now the top box is labeled `HEAD`, the middle box `HEAD~1` and the bottom `HEAD~2`](./fig/Commit_stack_HEAD.svg)

Using `HEAD` to refer to your commits can be great for looking at recent versions of your repository. But be careful, each time you commit to the repository, you are creating a new most-recent-version that is now the `HEAD` and every older version moves one layer down in the stack.

![IMAGE: On the left, the same stack of 3 flat white boxes are labeled `HEAD`, `HEAD~1`,  and `HEAD~2`. An arrow points to a stack on the right made of the same stack of 3 flat white boxes with a 4th red box on top. This red box is labeled `HEAD` and the boxes below it are labeled, in order from top to bottom, `HEAD~1`, `HEAD~2`, `HEAD~3`](./fig/Commit_stack_HEAD2.svg)

### Using the commit number

If there is a particular commit you want to look back on and are not sure how far back it was, having to refer to it as `HEAD~n` could get extremely frustrating, especially since $n$ will continue to change as you work more on your project and make more commits. Luckily there is another way to refer to a particular commit, using its commit number.

When you enter `git commit -m "short descriptive message"` no output appears, but Git gives that commit a unique identifier, its commit number. By typing `git log` we can see ALL of the previous commits. Since that might be a lot of output to deal with, we will just ask for the last 3 commits using `git log -n 3`. The number after `-n` is how many commits you want displayed from the log.

Let's see what that output looks like for Dracula:

```
$ git log -n 3
commit 65f447e949e53edc0db08b93670d2e2b35fa6c22 (HEAD -> main)
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Mon Feb 28 11:47:17 2022 -0500

    Ignore data files and the results folder.

commit 0d4b23c688dbbf87cff3cfa9425a7dfd9a6e6280
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Mon Feb 28 11:42:41 2022 -0500

    Add concerns about effects of Mars' moons of Wolfman

commit 7cd0f422d373516d968c8fe4b90401dfee4d52a6
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Mon Feb 28 11:39:24 2022 -0500

    Start notes on Mars as a base
```

If you forget to include the `-n 3` flag and just type `git log` you can always jump to the end by pressing `q`. If you have been working on this project for a while, using the arrow keys to scroll down may take a prohibitively long time.

The first thing to notice is that **all** of your commit messages are here. This is a good reminder to write clear and concise messages because future you may be very grateful when trying to figure out where exactly past you introduced a particular issue.

The second thing to notice is the structure of each entry in the log: commit, Author, Date, message.
When you identify which commit you want to look at, the commit number is the unique 40 digit string of letters and numbers above it after the word "commit". In Dracula's repository, the unique identifier for the commit in which he "add[ed] concerns about effects of Mars' moons on Wolfman" is `0d4b23c688dbbf87cff3cfa9425a7dfd9a6e6280`.

Now that we have found the unique identifier of the commit we want to examine, we can use it with `git show`. Don't worry, you won't need to type all 40 digits, the first six will suffice.

```
$git show 0d4b23
commit 0d4b23c688dbbf87cff3cfa9425a7dfd9a6e6280
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Mon Feb 28 11:42:41 2022 -0500

    Add concerns about effects of Mars' moons of Wolfman

diff --git a/mars.txt b/mars.txt
index df0654a..315bf3a 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,2 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
```

The commit number doesn't change as you update your repository.

![IMAGE: On the left, the same stack of 3 white boxes but now each is labeled with its six digit commit number. An arrow points from this stack to the stack On the right where the three white boxes have a new red box on top. The red box also has a commit number, but the commit numbers on the white boxes have not changed from the picture on the left.](./fig/Commit_number.svg)

### Knowledge Check 1

The output from `git log -n 2`is:

```
$ git log -n 2
commit 65f447e949e53edc0db08b93670d2e2b35fa6c22 (HEAD -> main)
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Mon Feb 28 11:47:17 2022 -0500

    Ignore data files and the results folder.

commit 0d4b23c688dbbf87cff3cfa9425a7dfd9a6e6280
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Mon Feb 28 11:42:41 2022 -0500

    Add concerns about effects of Mars' moons of Wolfman
```

Which of the following commands would show you the *most recent* commit you made?

- [[X]] `git show HEAD`
- [[ ]] `git show HEAD~1`
- [[X]] `git show 65f447`
- [[ ]] `git show fa6c22`
***
<div class ="answer">
The *most recent* commit is the current `HEAD` and its commit number is `65f447`. Either of these commands will give the same output. The command `git show HEAD~1` will show you one checkpoint earlier in your work, while `git show fa6c22` may not show you anything since it is not the first six digits of a known commit number (and likely not the first six digits of any commit number).
</div>
***

<div class = "help">
The error you get from entering a non-existent commit number starts with the word "fatal."  The word may be scary, but, in this case, all it is saying is that it could not execute the command. You did not harm anything!
</div>

### Technical details for the intrigued

When you commit code to Git, it doesn't create a brand new copy of your files from scratch. Instead it records the differences between the version of each file that it already has stored, and the new version. You can think of it as the instructions for transforming the previous version of your repository into the new version.

![The three white boxes are shown with a large green arrow pointing from each box to the box above it. The top box is labeled "Last committed version of repository" and the arrow pointing to it from the middle box is labeled "HEAD." The second box is labeled "Next to last version of repository" and the arrow pointing to it from the box below is labeled "HEAD~1." The bottom box is labeled "Previous version of repository" and the arrow pointing to it is labeled "HEAD~2." There are three dots under the boxes, and another three dots under the arrows indicating that this pattern continues.](./fig/Commits_are_pointers.svg)

You could think of each commit not as a checkpoint, but the instructions on how to get to the next checkpoint. The entire repository can be built by following a series of instructions (commits) in order. Similarly you can determine the precise state of an earlier version by following the instructions backwards.

## Comparing files to prior commits

In order to have some more commits to compare, let's add a few more lines to our notes about Mars, and start a file of notes about Venus.

First add a line to `mars.txt` so that it reads:

```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
```
Let's add and commit this change:

```
$ git add mars.txt
$ git commit -m "Discuss concerns about Mars' climate for Mummy"
```

Next let's add one more line to `mars.txt` so that it reads:
```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
An ill-considered change
```

You might have noticed that `diff` was the first word after your commit message when you entered `git show HEAD`. The lines after that are **all** the changes that you made with that commit. When comparing earlier versions with the current version, you are usually only going to want to look at one file at  a time. By typing `git diff HEAD`.... **work through behavior here, there will be a big divergence  (haha `diff`) in this behavior between command line git and github desktop**
*Or maybe we don't want to introduce github desktop at all, or just skip this section entirely for the github desktop module?*

Using `diff` command to compare current version of `mars.txt` and earlier versions.

### Knowledge Check 2

compare a file at two different times

## Undoing changes with Git

One big reason we save older versions of our work is so that we can go back to an earlier version if something we did doesn't work out.

### Changes not yet committed

Using the git checkout command, big warnings about including the file name so you don't lose things you didn't want to lose.

### Revert to an earlier version

Big warnings around this part!!

### Knowledge Check 3

quiz!

## Additional Resources

The last section of the module content should be a list of additional resources, both ours and outside sources, including links to other modules that build on this content or are otherwise related.

## Feedback

In the beginning, we stated some goals.

**Learning Objectives:**

@learning_objectives

We ask you to fill out a brief (5 minutes or less) survey to let us know:

* If we achieved the learning objectives
* If the module difficulty was appropriate
* If we gave you the experience you expected

We gather this information in order to iteratively improve our work.  Thank you in advance for filling out [our brief survey](https://redcap.chop.edu/surveys/?s=KHTXCXJJ93&module_name=%22Module+Template%22)!

Remember to change the redcap link so that the module name is correct for this module!