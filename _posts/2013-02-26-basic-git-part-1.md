---
layout: post
---

So this will be a short post about git basic. In one sentence, Git is a distributed version control system. Basically, it will keep track all of your project revisions(In git, it is called `commit`), just like how you have revisions / versions on your important documents.

Few of the advantage of using git are that you can roll back to previous versions if you screw up on your latest versions, You can easily collaborate with others since git will enable you to manage changes easily when compared to managing changes by hand, and many more. Basically, if you still use dropbox or any other manual approach for your repository(I am looking at you Binus International students), please, by all means learn git! It will amke your life easier.

Please note that this will not be the most comprehensive guide about git, so apologize in advance for being slow or explaining too much. For more advanced user, you can go to more advance blog / website. I recommend [git-scm's website](http://git-scm.com/), [git-ready](http://gitready.com/), and [try.github.com](try.github.com). Also, this might not work on windows machine, since I have not used or tried git on windows yet.


So you are ready to start learning git. Now what?

---
### Create initial git repository ###
---

You can do this by going to the command prompt and changing directory to your project's root location and use command `git init`. In my example, I use my blog's location.

{% highlight bash linenos %}
xxxxxxxxx:~ steven$ cd projects/seiryuz.github.com/
xxxxxxxxx:seiryuz.github.com steven$ git init
Initialized empty Git repository in /Users/steven/projects/seiryuz.github.com/.git
{% endhighlight %}

What this command does, is that it will create an initial folder called .git in your root folder, where all your revision histories, versioning, remote git, and etc are stored. This .git folder is specific to your folder, so you can have .git folder for each and every projects you have.

With that you can start to work on your project. Next, what if you want to continue / extends someone's project you found on github?


---
### Cloning git repository ###
---

This process is called cloning repository. Basically it will download all the source code from the referenced repository and all the revision histories available. You are cloning everything the project has and created a link in your .git folder towards the so called `origin`, the url / locations of your original cloned project.

To clone a repository simply use the command `git clone [target]`. (Remember it will create the project directory in the current working directory). For this example, I'll use [my blog](https://github.com/SeiryuZ/seiryuz.github.com) as the reference.


{% highlight bash linenos %}
xxxxxxxxx:dev steven$ git clone https://github.com/SeiryuZ/seiryuz.github.com.git
Cloning into seiryuz.github.com...
remote: Counting objects: 417, done.
remote: Compressing objects: 100% (233/233), done.
remote: Total 417 (delta 170), reused 367 (delta 120)
Receiving objects: 100% (417/417), 281.94 KiB | 113 KiB/s, done.
Resolving deltas: 100% (170/170), done.
xxxxxxxxx:dev steven$ ls
xxxxxx     xxxxxx    xxxxxx  xxxxxxx   seiryuz.github.com
xxxxxxxxx:dev steven$
{% endhighlight %}

From the above code, you can see that the command downloads the whole project and created a local folder and a local repository for you to work on.

---

This is part one of the basic git blog post series that I will be doing. I hope this can help people trying to understand git better.

