---
layout: post
title: "OS X: How to Access Email While Using a VPN"
location: "Southampton, England"
image: headers/quito_people.jpg
color: 268742
---

{{ page.title }}
================

If you're unable to send email while using a [VPN][], it's likely that your provider is blocking [SMTP][] services. That seems fair, they're doing it to prevent spam abuse. But you don't want to stop your connection every time you need to send email, right?

[VPN]: http://en.wikipedia.org/wiki/Virtual_private_network "You've more likely entered your password incorrectly ;-)"
[SMTP]: http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol

Here's a temporary workaround. Use the `route` [command][] to create a static route that redirects outgoing email traffic, bypassing the VPN. Packets destined for the SMTP server will now instead use the local gateway.

[command]: https://developer.apple.com/library/mac/documentation/Darwin/Reference/Manpages/man8/route.8.html

SMTP server: `62.24.157.35`  
Local gateway: `192.168.1.254`
  
{% highlight bash %}
$ sudo route add 62.24.157.35 192.168.1.254
{% endhighlight %}

**Remember** to replace the addresses with those of your own. This also works on Linux (CentOS).
