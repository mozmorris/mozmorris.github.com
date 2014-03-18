---
layout: post
title: "Shell Brace Expansion"
location: "Southampton, England"
image: headers/cheriton_sunset.jpg
caption: "Cheriton, Hampshire"
color: 3376af
---

{{ page.title }}
================

I've only just discovered brace expansion in the shell. How had I not known about this before? Somehow I've never seen someone using this clever time saving trick on the command line.

I have a `subdirectory`. It contains `old-file.txt`. I need to copy it to `new-file.txt`. I've spent years typing:

{% highlight bash %}
$ cp /subdirectory/old-file.txt /subdirectory/new-file.txt
{% endhighlight %}

When instead I should have been using:

{% highlight bash %}
$ cp /subdirectory/{old-file.txt,new-file.txt}
{% endhighlight %}

Or even more succinct:

{% highlight bash %}
$ cp /subdirectory/{old,new}-file.txt
{% endhighlight %}

Syntax
------

    i.  [preamble]{comma,separated,strings}[postscript]
    ii. [preamble]{x..y[..incr]}[postscript]


The braces may contain a set of comma-separated strings ***or*** a sequence expression. `preamble` and `postscript` are optional. 

The comma-separated sequence `{aa,bb,cc}` becomes `aa bb cc`. While the sequence expression `{1..10}` becomes `1 2 3 4 5 6 7 8 9 10`. The sequence also takes an optional increment value. So, `{1..10..2}` expands to `1 3 5 7 9`

Examples
--------

How to create a backup of `file.txt`. Easy:

{% highlight bash %}
$ cp /subdirectory/file.txt{,.bak}
{% endhighlight %}

Create five new directories within subdirectory:

{% highlight bash %}
$ mkdir /subdirectory/dir_0{1..5}
{% endhighlight %}
