---
layout: post
title: "Git Interactive Rebase: A Newbie's Guide"
date: 2016-05-30T12:52:20-05:00
---

Proper git hygiene is an important skill for developers. A key element of this is maintaining a readable commit history for a file. The use of interactive rebase through the `git rebase -i` command is an important tool for this. For a beginner developer this can be an intimidating tool, so I decided to write a brief overview of the process.

Interactive rebase allows you to rewrite the commit history of a branch. This can be useful to combine (or "squash") small, non-substantive commit. For example if you implemented a feature in a commit and the four subsequent commits were minor refactoring or bug fixes for that new feature, you might want to combine all of these into one commit for merging into the main codebase. This is commonly requested when contributing to open source projects and is just good development practice overall.

A detailed overview of the process is available at the [Git website](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) - I'll focus on the aspects I found most confusing.

Assuming you want to rebase your branch against master, you'd begin the process like you would a normal rebase but with the `-i` flag added: `git rebase -i master`. This indicates to git that you wish to interactively rebase the branch. After entering this command Git will open a list of the branch's commits with the following text below the list. The default option for each commit will be `pick` but you can change the options as desired.

~~~
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
~~~

It is important to understand that *your changes in this file serve as a roadmap for the rebase; no modifications are made at this point*.

Once you complete and close this file, you will receive a series of commit messages to edit. For those not familiar with the process these messages may be confusing. If you opted to *squash* commits, you will be asked to update the commit message for the combined commits. Similarly, if you opted to *reword* a previous commit message, you will be asked to complete the edit of that commit message, and so on. *(Note: Rewritten commit messages in the initial file created by git rebase -i are not recognized by git, so wait until this step before rewriting.)* Once these messages are all edited, your rebase is finished.

Now you are ready to push your branch to origin. Great! Since you rewrote your commit history, though, doing a standard `git push origin` will lead to merge conflicts. You'll need to use the `--force` flag to overwrite the existing history with your rewritten history, so `git push origin --force` is the way to go.

Even with this guide, the whole process can still be confusing. Let's say you realized that you messed up your rebase and want a do-over. No worries! The whole thing can easily be reverted by accessing your `git reflog` and then doing a `git reset --hard` to the appropriate commit prior to your rebase. (This has never happened to me, no way...)

If you want more information about all of Git's history rewriting tools, the [Rewriting History article on the Git website](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) is your friend.
