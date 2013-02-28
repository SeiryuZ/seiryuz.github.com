---
layout: post
---

After knowing what happen to your working directory, you added one or more files to the staging area and you are sure that these are the files that you want to save. These are the revisions that you want to commit on. You now will use `git commit`

For example, let's continue from the last post. This is your current working directory:

{% highlight bash linenos %}
xxxxxxxxx:seiryuz.github.com steven$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
# new file:   readme.md
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
# readme_more.md
nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

When you use `git commit` you will be presented with your configured text editor. Usually it will be `vim`, `nano`, or `emacs`, but if you don't like this editors, you can changed it on your configuration. On the text editor you will be presented with these text.

{% highlight bash linenos %}
<Write your commit message here>
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       new file:   readme.md
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       readme_more.md
{% endhighlight %}

You will need to put your commit message, basically write down what has been changed on this commit. As a rule of thumb, make it concise, but meaningful so that you can know exactly what this commit is about without looking at the difference between files.

For this reason, you need to commit *often* and in logical steps. Don't put all your work into one big commit, for example after working a full day, you commit all your changes into one big commit. This practice is bad, because (1) you cannot revert back to some more smaller change, you need to revert your whole big commit, and (2) you will have a hard time to keep track of your changes.


### Handy shortcut on commit ###
* `git commit -m "Your commit message"` If you want to write your commit message in the command directly, instead of opening text editor
* `git commit -a` Commit everything that has changed. Basically `git add .` and `git commit` at the same time
* `git commit -am "your commit message"` Combination of above commands, handy but you need to be *REALLY* careful about this command


All in all, commit often! You will be thankful that you can screw up and revert back to your last changes without changing big chunk of your code. Talking about reverting to old commit, that will be my next post.