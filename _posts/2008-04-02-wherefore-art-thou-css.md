---
layout: post
title: Wherefore Art Thou CSS?
---

> Stylesheets that won't render are more tragic than Romeo's inability to check a pulse.
> <small>R.B. Bennett</small>

Two months ago I designed a website for the company I'm currently employed at. The site was pretty basic fare --- four or five HTML pages, a few images, and a stylesheet to make it look sexy. The design was uploaded to the development server then uploaded to the live server once approved. All was well until the site was viewed in Firefox (I can't recall how Safari and Opera behaved). For a reason unknown to all of us fine employees, the styles in the CSS file weren't being applied. The .css file was most certainly *there*, and Internet Explorer displayed the site just peachy. Most perplexing was that the development server and live server are *supposed* to be identical, and no such wonkiness occurred on the dev side.

Luckily the problem was found quickly by one of my co-workers. Our live server is apparently powered by Netscape Enterprise Server, which came configured to serve .css files with the `application/x-pointplus` mime type (not good Netscape, not good at all). Some web browsers like Internet Explorer will ignore the server and treat the CSS file as `text/css` while others like Firefox will roll with `application/x-pointplus` and potentially show you a website that looks disastrously grotesque.

I'm not sure how popular Netscape Enterprise Server is, but if you happen to be using it and browsers are ignoring your stylesheets, make sure that your .css files are actually being served with the `text/css` mime type. Because that *just makes sense.*
