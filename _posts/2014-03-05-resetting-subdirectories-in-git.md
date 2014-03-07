---
layout: post
title: "Resetting Subdirectories in Git"
location: "Southampton, England"
image: headers/motorbike_yama.jpg
caption: "Jama, Ecuador"
color: b21913
---

{{ page.title }}
================

How do you hard reset a subdirectory of a Git repository? Simple.

{% highlight bash %}
$ git checkout HEAD -- subdirectory
{% endhighlight %}

A word of warning. This replaces the working tree ***and*** the index with the HEAD commit. 

Don't lose changes you might have already staged within the subdirectory. If this is the case and you wish to unstage those changes, use:

{% highlight bash %}
$ git reset -- subdirectory
{% endhighlight %}

Think of `git reset -- path` as the opposite of `git add`.
