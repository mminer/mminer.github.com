---
layout: post
title: "What Is My IP Address LaunchBar Action"
---

Often I need to find my external IP address, warranting a trip to whatismyip.com. To speed this up I created a [LaunchBar](https://obdev.at/products/launchbar/index.html) action that fetches the info for me. It's a simple wrapper around a one-liner that requests and parses the IP address reported by Dyn.

```shell
curl --silent http://checkip.dyndns.org/ | grep --extended-regexp --only-matching '\d+\.\d+\.\d+\.\d+'
```

This is useful on its own as a shell command, but when available as part of your LaunchBar workflow it becomes even handier.<sup><a href="#fn1" id="r1">[1]</a></sup>

<img alt="What Is My IP Address? LaunchBar Action" src="/images/what-is-my-ip-address.gif">

Download a signed version of the action [here](https://github.com/mminer/launchbar/raw/master/Signed/What%20Is%20My%20IP%20Address%3F.lbaction). Money back guaranteed.


---

<ol class="footnotes">
    <li id="fn1">No foolin&rsquo;, LaunchBar is a damn fine piece of software that has saved me countless hours over the years and keeps improving as I find actions like <a href="https://github.com/prenagha/launchbar">these</a> and write my own. I&rsquo;m such a fan.<a href="#r1" class="return"></a></li>
</ol>
