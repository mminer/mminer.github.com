---
layout: post
title: "Dark Mode CSS"
---

Just in time for Halloween but late for the 20<sup>th</sup> anniversary of The Smashing Pumpkins' *Adore*<sup><a href="#fn1" id="r1">[1]</a></sup>, Apple added support for dark mode on the web via the [`prefers-color-scheme`](https://drafts.csswg.org/mediaqueries-5/#prefers-color-scheme) media query in Safari Technology Preview. Lately I've noticed developer-centric sites like Docker and Microsoft's docs offer a dedicated switch to toggle between light and dark themes, but this CSS-only solution is way easier.

```css
@media (prefers-color-scheme: dark) {
    body {
        background: black; /* like my soul */
    }
}
```

Implementing dark mode support on this blog was a breeze thanks to its grand total of 13 colours. I took the lazy route and just inverted most of them using Sass' [`invert`](http://sass-lang.com/documentation/Sass/Script/Functions.html#invert-instance_method) function. The end result looks respectable given the minimal effort expended.

<img alt="Dark mode CSS comparison" srcset="/images/dark-mode-css-comparison.png 1x, /images/dark-mode-css-comparison@2x.png 2x" src="/images/dark-mode-css-comparison.png">

I doubt we'll see widespread adoption of `prefers-color-scheme` --- providing multiple themes would be a serious undertaking for many websites --- but it'll be useful for web apps that strive to honour the user's preferences. Because the customer is always right, power to the people, yadda yadda yadda.


---

<ol class="footnotes">
    <li id="fn1">This was the best goth reference I could think up. I'm not even sure it counts. I missed the goth boat in my youth.<a href="#r1" class="return"></a></li>
</ol>
