---
layout: post
title: "Update to Slim Skeleton App"
location: "Southampton, England"
image: headers/quito_mural.jpg
caption: "Quito, Ecuador"
color: 3376af
---

{{ page.title }}
================

I made some [updates][] to the [Slim][] skeleton app I put together last year. It still uses [my fork][] of Slim and I've pulled in all the latest changes from the original repository [(v2.4.2)][]. All tests passing. FWIW, I migrated an application this week without any breakages.

[updates]: https://github.com/MozMorris/slim-skeleton
[Slim]: https://github.com/codeguy/Slim
[my fork]: https://github.com/MozMorris/Slim/tree/webroot
[(v2.4.2)]: https://github.com/codeguy/Slim/tree/2.4.2

The skeleton itself now uses Slim's [Views][] repository, replacing the deprecated [Extras][].

Using Composer to generate an app is straightforward enough:

{% highlight bash %}
$ composer create-project moz-morris/slim-skeleton [app-name]
{% endhighlight %}

[Views]: https://github.com/codeguy/Slim-Views
[Extras]: https://github.com/codeguy/Slim-Extras
