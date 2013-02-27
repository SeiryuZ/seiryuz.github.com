---
layout: post
---

Today, I'll write shortly about `git status` and `git add`. After yesterday's post, you already know how to initialize a project or clone other people's project. Now you might want to start working on your project or your contributions. Today's post will focus on how to track your changes (Not yet saving them) and stage them for a commit.

First thing first, to know what are the current conditions of your git and your local work. Try to use `git status` on your project root.

{% highlight bash linenos %}
xxxxxxxxx:~ steven$ cd projects/seiryuz.github.com/
xxxxxxxxx:seiryuz.github.com steven$ git status
# On branch master
nothing to commit (working directory clean)
{% endhighlight %}

This means nothing has changed from the last commit or your checkpoints on your branch `master`. If you add another file, then do another `git status` it will show the new file

{% highlight bash linenos %}
xxxxxxxxx:seiryuz.github.com steven$ touch readme.md
xxxxxxxxx:seiryuz.github.com steven$ git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
# readme.md
nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

`git status` will also shows if file has been removed since last commits and whether you have modified a file. This is really handy in checking the current status of your working directory. You can easily query and scan what has been changed and decide what to do with it.

---

After knowing what files have been changed, you want to move the file(s) into the staging area. This area is for file that you want to be tracked in your next commit / savepoints. To move file(s) into the staging area, you need to use `git add` command. Continuing from last example:

{% highlight bash linenos %}
xxxxxxxxx:seiryuz.github.com steven$ touch readme_more.md
xxxxxxxxx:seiryuz.github.com steven$ git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
# readme.md
# readme_more.md
nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}


Now, let say you have not finished modifying the readme_more.md and you just want to keep track readme.md in the next commit. You can use `git add [filename]` to move that particular filename into the staging area.

 {% highlight bash linenos %}
xxxxxxxxx:seiryuz.github.com steven$ git add readme.md
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

See the difference now? when you move file(s) to the staging area, it will be listed by `git status` to be under changes to be comitted. The untracked file will not be saved in the next commit. Maybe after you finish the modification on the file later on after the commit you want to make another commit just for readme_more.md.

### Handy shortcut on adding files ###
`git add .` will add EVERYTHING that has been changed on your current path and its childrens to the staging area.
`git add folder_name` will add EVERYTHING that has been changed on that particular folder.

These two commands are very useful, but use with care so that you don't put files that you don't want into the staging area.(I am guilty of this mistake so many times)

This two commands are the essentials of using git. Checking your status, and moving files to the staging area, in the next post we will talk about comitting changes in the staging area, or writing history so you can visit or base your experimental work on it.