---
layout: post
title: Announcing Lumos Game Analytics
---

> Goodbye weird hackish Google Analytics solution!
> <small>John Graunt</small>

Recently myself and other suave folks have been building a game analytics service called Lumos. Frustrated by the lack of analytic tools geared specifically towards the needs of game developers, we took up the task of building one ourselves. The result of our efforts is now in public beta, and I encourage you to [take it for a spin](http://www.uselumos.com/). Currently we only offer support for the outrageously awesome Unity engine, but support for other game engines is coming soon. We love you regardless of your tool choice.

"Tell me good sir," you might demand, "what does Lumos offer an enterprising chap like myself?" First off, _remote debugging_. Lumos automatically records runtime errors and warnings thrown by your game and sends them to our servers for later perusal. When a player triggers a dastardly NullReferenceException in level three that you were unaware of, you'll see the problem immediately and be able to fix it. This is particularly useful in the beta testing phase of your game; errors happen, but unless you discover into them yourself while developing it can be difficult to know where they might occur.

Second feature: _system info recording_. When a player first fires up your game, specs such as their computer's RAM and operating system are sent to Lumos. This information is valuable when deciding what class of machine your game should target. If most of your players are rocking integrated graphics cards with 64 MB VRAM (don't laugh, that's what my old workhorse has), you might want to dial down the particle effects. It's also valuable when deciding what your next game should target.

Another feature we built was a _feedback system_. This allows players to report bugs or give suggestions, to which you can respond if desired. In the Unity package we supply there's an optional GUI that makes it a breeze to solicit feedback from your players, or you can write your own sexy interface to do the job.

Now, besides the features mentioned above there are many new ones currently in the works. As time goes on Lumos will be expanded to fulfill the needs of game developers large and small. If you have features you'd like to see that aren't currently offered, we'd love to hear them (you can use the form [here](http://www.uselumos.com/contact) or contact me <matthew@uselumos.com>). Many of us on the Lumos team are game developers ourselves, but obviously you'll desire features we haven't even thought of yet. We looked into hiring a telepath, but decent ones are few and far between.

The website for Lumos is [www.uselumos.com](http://www.uselumos.com/). Sign up, make an app, add the Lumos Unity package to your game and get those stats flowing! We've designed the service to operate as automatically as possible --- for most functionality you don't have to take any action at all. Simply drop the Lumos game object into your scene and you're ready to laugh at the days when game analytics was a far-off fantasy. If that's not the definition of the American Dream (or Canadian, in my case), I don't know what is.
