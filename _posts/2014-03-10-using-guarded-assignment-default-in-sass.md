---
layout: post
title: "Using Guarded Assignment or `!default` in Sass"
location: "Southampton, England"
image: headers/canoa_sunset.jpg
caption: "Canoa, Ecuador"
color: e6623c
---

{{ page.title }}
================

How does Sass' guarded assignment (`!default`) keyword work?

{% highlight sass %}
/* custom vars */
$module_height: 18px;

/* defaults */
$module_height: 20px !default;
$module_bgcolor: #ccc !default;

.module {
  height: $module_height; /* height: 18px; */
  background: $module_bgcolor; /* background: #ccc; */
}
{% endhighlight %}

`!default` will assign a value only if the variable does not already have one. In other words, it prevents a variable from being reassigned.

How is this useful? It allow us to create customisable modules with fallbacks. Let's say we've created a headings module that styles the page headers.

{% highlight sass %}
/* _headers.scss module */

h1 {
  font-size: 2em;
  color: #222;
}

h2 {
  font-size: 1.5em;
  color: #333;
}
{% endhighlight %}

That's fine but it's not not customisable. Here's where we introduce guarded assignment. Developers using the module can now customise the headers as they choose.

Here's the updated headers module:

{% highlight sass %}
/* _headers.scss module */

/* customisable vars */
$h1_font_size: 2em !default;
$h1_color: #222 !default;
$h2_font_size: 1.5em !default;
$h2_color: #333 !default;

h1 {
  font-size: $h1_font_size;
  color: $h1_color;
}

h2 {
  font-size: $h2_font_size;
  color: $h2_color;
}
{% endhighlight %}

Consuming and customising the module is now a trivial task. Note here the order of things. The variables are defined **before** importing the headers module.

{% highlight sass %}
/* app.scss */

$h1_font_size: 36px;
$h2_color: red;

@import "headers"
{% endhighlight %}

Here's the final css output.

{% highlight css %}
/* app.css */

h1 {
  font-size: 36px;
  color: #222
}

h2 {
  font-size: 1.5em;
  color: red;
}
{% endhighlight %}

