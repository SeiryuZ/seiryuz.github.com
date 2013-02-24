---
layout: post
---

Testing is a crucial part of building a good software which is often overlooked. It's sometimes cumbersome and take an extra effort to build. I learnt the hard way that I cannot let myself to push new functionalities before testing it, but I am digressing.

Our Django tests in one of our project reached the count of 162 tests (Which are still not completely testing the whole stacks). The time it took us to run the whole tests using PostgreSQL is `118s` which are really annoying when you need to tests for the changes you made. I know that you can run only some of the tests instead of the whole suites for quicker testing time, but I felt that tests should be quick so you can immediately knows what breaks from your changes.

So with speed in mind, I tried to read the Django documentations once again and some blogs for testing tips. Here I found two neat tricks that can easily speed up your tests. * Note that these tricks are tested with Django 1.4.3


---
#### 1. Use in memory SQLite for testing ####
---
From some blogs that I read, It is extremely good to have tests run on the exact same database as your production server, be it PostgreSQL, MySQL, or any other databases. It could catch errors that are specific to your choice of database. If speed are your main concern for developments, nothing could beat an in memory SQLite database for testing. It is **extremely fast**.

Here's how you would like to apply SQLite for your tests

{% highlight python linenos %}
import sys
if 'test' in sys.argv:
    DATABASES = {default': {'ENGINE': 'django.db.backends.sqlite3'}}
{% endhighlight %}

Note that this block of configuration will be run only if tests are the arguments for the manage script(./manage.py test). If you use different test runners change the conditions accordingly.

The result? `75s` on running the same tests on same machine.

Gotcha:

* It might not catch some problems when using other database. With my case,lots of error come up about the needs to roll back transactions.


---
#### 2. Use MD5 Hash only ####
---
Based on the [documentations](https://docs.djangoproject.com/en/dev/topics/testing/overview/#speeding-up-the-tests), Django uses a strong encryption that will take some time to compute, in order for a stronger protections to our data. On our tests, we used fixtures extensively and all of our user objects in the fixture has a password encrypted with Django's default encryption `pbkdf2_sha256`.

Our tests involve of using the fixtures data and loggin in as a user. This process is repeated on every single tests that require user login. In django's documentation, we are recommended to use weaker hash functions, since it will speed up the tests considerably.

{% highlight python linenos %}
import sys
if 'test' in sys.argv:
    DATABASES = {default': {'ENGINE': 'django.db.backends.sqlite3'}}
    PASSWORD_HASHERS = (
        'django.contrib.auth.hashers.MD5PasswordHasher',
    )
{% endhighlight %}

The result? `49s` on running same tests on same machine.

Gotcha:

* All of our fixtures, which originally use stronger encryptions, need to have their password to be rewritten in md5 hash

---
### Conclusion ###
---

Use in-memory SQLite and MD5 Hash on tests, it will speed up your tests considerably while needing minimal efforts. Now I can work on my changes even faster, since I can check back with the test results faster than before. Our tests' run duration come down from `118s` to `75s` using in-memory SQLite instead of PostgreSQL and even faster to `49s` when combined with weaker hashing.

