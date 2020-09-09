---
title: "Recent Reads"
---

Here's a few things I read recently.

## [Getting Things Done: The Art of Stress-Free Productivity](https://en.wikipedia.org/wiki/Getting_Things_Done)

You don't often find me lurking in the productivity section of the book store, but I see GTD mentioned often enough that I figured it's worth a gander. The author proposes a system that emphasizes small discrete actions rather than vague nebulous goals, and writing down all the various TODOs cycling through your brain for easy retrieval and review later. The methodology is compelling in its simplicity and ease of implementation --- I feared Gantt charts and the Conjoined Triangles of Success, but it turns out to closely resemble the bare-bones action-and-project-lists-on-index-cards system that I already use.

I'm unconvinced that 300 pages was necessary but it's not the slog I dreaded. I suspect that those with more management responsibilities get more out of it, but I picked up plenty of useful tips all the same. Worth the gander indeed.

## [Little Manual of API Design](https://github.com/papers-we-love/papers-we-love/blob/master/api_design/api-design.pdf)

This one's a quick and pleasant read. It's a pragmatic reminder of best practices when developing libraries (or any software really) from one of the developers of Qt. Much of it reads like common sense --- avoid abbreviations, prefer specific names over general ones, choose sensible defaults --- but, you know, "common sense is not so common" and all that.

I particularly like the advice to write use cases before implementing an API. Too often I find myself refactoring a function because I only partially thought through how it would be used in practice. Likewise, nothing beats early feedback from the poor saps who have to use your code.

## [The Rise of the Citizen Developer: Assessing the Security Impact of Online App Generators](https://saschafahl.de/papers/appgens2018.pdf)

What I find even more interesting than the security implications of this paper (which are no joke, don't get me wrong) is the sheer number of apps created using online app generators. The researchers found over 250k of them (!) on Google Play. It brings to mind the sudden availability of powerful-yet-approachable game engines like Unity that precipitated the past decade's explosion of quality indie games.

While making app development accessible to all is undoubtedly a good thing, this paper inspires little confidence about the competence of online app generators. Not even bothering with basics like SSL is pitiful. As the authors note, "a single error by an OAG potentially affects thousands of generated apps." C'mon troupe, we can do better than this.

*The Morning Paper* has [a nice writeup](https://blog.acolyer.org/2018/07/02/the-rise-of-the-citizen-developer-assessing-the-security-impact-of-online-app-generators/) that summarizes the paper and adds some insightful commentary. Speaking of which, *The Morning Paper*, which posts "an interesting / influential / important paper from the world of CS every weekday morning", is the bomb dot com.
