---
layout: post
title: Get Down, Get Down (Unity Boogie)
---

> Please stop butchering our song. I'm begging you man, just quit doing it. Please.
> <small>Kool &amp; The Gang</small>

Recently I built a browser-based window system using the most excellent [MooTools](http://mootools.net/) JavaScript framework. It behaves similar to how your modern desktop windows work. That is, windows can be opened, closed, resized, and dragged around by their titlebar. When clicked on, a window will come to the front of the window stack. It's a lot like the [Mocha UI](http://greghoustondesign.com/demos/mocha/) project, just not as good (mad props to the creators of Mocha, it rocks hard).

Anyway, to the point of this post: in one of these windows I later embedded a Unity game. Much to my dismay I discovered that having a `div` hovering over an embedded Unity game doesn't work --- the `div` will appear *behind* it, despite having a higher `z-index`. This means that I can't have my windows properly overlapping each other, and any thought of decorating a Unity game (giving it rounded corners, perhaps) can be forgotten.

I'm told by intelligent people that this behaviour can be expected with *any* embedded object ([Flash excluded](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15523 "Information about displaying Flash content below other layers.")). So, what's the solution? Unfortunately there isn't one that I'm aware of. As nice as it would be to place wacky animated GIFs overtop a well-polished Unity game (bring back 90's web design!), you're simply out of luck. Or I'm simply out of luck. Somebody is simply out of luck.
